---
title: "HOWTO: Clean deleted files from F-Spot database"
date: 2009-10-19
forum: General Help
---

### Post by Darwin Award Winner on 2009-10-19
If you have ever moved your photos around before, you may have had problems with F-Spot keeping the old locations in its database. I wrote a perl script to solve this problem, because the existing scripts lying around the internet all had flaws, or were written for previous versions of F-Spot. 

One of the major problems with previous scripts was the potential for data loss when a photo has multiple versions and the default version was deleted. My script handles this case by detecting photos that have lost their default version, but still have others, and then picking another one at random to be the default.

Anyway here's the script. Just download it and run it. It won't make any changes at all unless you explicitly tell it to, and it always makes a timestamped backup of the database before making any changes, so there shouldn't be any danger in running it. 

Once your run the script, it should print out a list of files that should be removed from the database. If these file names all look like truly deleted files that no longer exist, then you can try running the program again with the --force option to make it modify the database for real. 

Do not run the script while F-Spot is running. The script will make an effort to abort if F-Spot is running, but no guarantees.

I have tested this script repeatedly on my F-Spot database, and it has been reliable so far.

Oh, and you may need to install some perl modules.

```
#!/usr/bin/perl

use v5.10;
use strict;
use warnings;
use Getopt::Long;
use List::Util qw(first);
use List::MoreUtils qw(uniq any);
use File::Spec;
use DBI;
use Set::Scalar;
use IPC::Run qw(run);
use URI::Escape;
use Carp;

sub fspot_running {
    system q{pgrep -u $(id -u) f-spot} == 0;
}

sub file_exists_uri {
    my $uri = shift;
    $uri =~ s{^file:(//)?}{}ixsm or croak "Invalid file: URI: $uri";
    return -e uri_unescape($uri);
}

sub make_timestamped_backup {
    my $filename = shift;
    chomp (my $timestamp = `date +-%F-%T.%N`);
    run ["cp", "--", $filename, $filename . $timestamp];
}

{
    # Initial list of possible paths
    my @db_paths;
    if ($ENV{XDG_CONFIG_DIR}) {
        push @db_paths, File::Spec->catfile($ENV{XDG_CONFIG_DIR},"f-spot","photos.db");
    }
    push(@db_paths,
         File::Spec->catfile($ENV{HOME},".config","f-spot","photos.db"),
         File::Spec->catfile($ENV{HOME},".gnome2","f-spot","photos.db"),
     );

    say "@db_paths";
    sub db_path {
        # Passing args adds them as possible locations
        unshift @db_paths, @_ if @_;
        return first { defined $_ and -f $_ } @db_paths;
    }
}

{
    my $db_handle;
    sub db_handle {
        return $db_handle if $db_handle;

        my $db_path = db_path(@_);
        $db_handle = DBI->connect("dbi:SQLite:dbname=$db_path","","");
        return $db_handle;
    }
}

main: {

    my ($force, $help);
    my $result = GetOptions("force" => \$force,
                             "help" => \$help,);

    if ($help) {
        say <<EOM;
fspot-cleaner: Removes nonexistent files from F-Spot's database.
Options:
	--help		Show this message
	--force		Without this option, only show orphaned database entries, but do nothing.
EOM
        exit 0;
    }

    if (!$force) {
        say "Running in no-op mode. Orphan database entries will only be listed. To actually clean the database, run this script again with --force.";
    }

    my $dbh = db_handle();

    print "Searching for nonexistent files in database... ";
    my @complete_file_list = @{$dbh->selectall_arrayref("select photo_id, version_id, base_uri, filename from photo_versions")};

    my @ok_file_list = map { if (file_exists_uri(File::Spec->catfile(@$_[2,3]))) { $_ } else { () } } @complete_file_list;
    my @deleted_file_list = map { if (not file_exists_uri(File::Spec->catfile(@$_[2,3]))) { $_ } else { () } } @complete_file_list;
    say "Done.";

    if (!$force) {
        say "The following filenames would be removed from the database:";
        say join("\n", map { File::Spec->catfile(@$_[2,3]) } @deleted_file_list);
        say "Exiting now. No changes have been made. To remove the above files, please re-run this script with the --force option.";
        exit 0;
    }

    if (fspot_running()) {
        say "The following filenames would be removed from the database:";
        say join("\n", map { File::Spec->catfile(@$_[2,3]) } @deleted_file_list);
        say "It appears that F-Spot is currently open, so no changes have been made. To remove the above files, please exit F-Spot before running this script.";
        exit 0;
    }


    print "Calculating necessary database operations... ";
    # Calculate list of deleted photos (photos that have zero
    # photo_versions associated with them) Note that this is NOT just
    # the list of photo_ids from @deleted_file_list, since we could
    # delete only one of several files for a given photo
    my @all_photo_ids = uniq map { $$_[0] } @complete_file_list;
    my @ok_photo_ids = uniq map { $$_[0] } @ok_file_list;
    my @deleted_photo_ids = (Set::Scalar->new(@all_photo_ids) - Set::Scalar->new(@ok_photo_ids))->members;

    # Calculate new default_version_id for each photo_id
    my @default_photo_versions = @{$dbh->selectall_arrayref("select id, default_version_id from photos")};

    # List of photo_ids and their new default_version_ids, if
    # modified. Unchanged defaults and deleted photos have been
    # filtered out.
    my @changed_default_photo_versions = grep { my $query = $_; not $$query[0] ~~ @deleted_photo_ids or
                                                    not any { @$query ~~ @$_[0,1] } @ok_file_list
                                                } @default_photo_versions;
    say "Done.";

    print "Making timestamped backup... ";
    make_timestamped_backup(db_path());
    say "Done.";

    print "Carrying out database operations... ";
    # Delete @deleted_file_list from table photo_versions
    {
        my $statement = "delete from photo_versions where photo_id=? and version_id=?";
        my @photo_ids = map { $$_[0] } @deleted_file_list;
        my @version_ids = map { $$_[1] } @deleted_file_list;

        my $sth = $dbh->prepare($statement);
        $sth->execute_array({}, \@photo_ids, \@version_ids);
    }

    # Delete @deleted_photo_ids from table photos
    {
        my $statement = "delete from photos where id=?";
        my @photo_ids = @deleted_photo_ids;

        my $sth = $dbh->prepare($statement);
        $sth->execute_array({}, \@photo_ids);
    }

    # Update default_photo_id and paths for
    # @changed_default_photo_versions in table photos
    {
        my $statement = "update photos set default_version_id=?, base_uri=?, filename=? where id=?";
        my @changed_defaults = map { my $query = $_; first { @$query ~~ @$_[0,1] } @ok_file_list } @changed_default_photo_versions;
        my @photo_ids = map { $$_[0] } @changed_defaults;
        my @version_ids = map { $$_[1] } @changed_defaults;
        my @base_uris = map { $$_[2] } @changed_defaults;
        my @filenames = map { $$_[3] } @changed_defaults;

        my $sth = $dbh->prepare($statement);
        $sth->execute_array({}, \@version_ids, \@base_uris, \@filenames, \@photo_ids);
    }
    say "Done.";
    say "Finished cleaning F-Spot database.";
}
```

---

### Post by almightybunghole on 2010-06-18
Hi there,

I could do with running this script, could you give me an idea of the perl modules required to run it?

Thanks!

George

---

### Post by Darwin Award Winner on 2010-06-18
I haven't used F-Spot in a long time, but you can look at the beginning of the script to see all the modules that it uses. If you just search for a package containing "perl" and the words that make up each module's name, you should be able to find a package for that module.

---

### Post by omegaFil on 2010-09-02
I'm aware that thread is inactive since 2007, but I've used the script and had an error with **fspot_running**: 
> 
Argument "pgrep -u $(id -u) f-spot" isn't numeric in numeric eq (==) at ./F-Spot_db_repair line 17.


so **I've changed sub** this way:

```

sub fspot_running {

    my $id = `id -u`; 
    chomp ($id);
    my $command = "pgrep -u ". $id . " f-spot";
   
    my $result = system ($command);
   
    return $result == 0;
}
```

I'm definitely not a Perl expert, so **use it carefully**, maybe check output before using it. 
Hope it helps

---

