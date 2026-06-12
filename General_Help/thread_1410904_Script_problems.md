---
title: "Script problems"
date: 2010-02-19
forum: General Help
---

### Post by intermentals on 2010-02-19
I have this script:

"#!/bin/sh
echo "FAST, ROLLBACK, BACKUP or QUIT"
read myvar

if [[ $myvar = "BACKUP" ]]; then
    echo "About to backup (local backup)"
    sleep 5
    /srv/bin/backup.sh
fi

if [[ $myvar = "FAST" ]]; then
    echo "Fast backup (incremental)"
    sleep 2
    /srv/bin/incremental.pl && echo "Successfully completed incremental backup"
fi

if [[ $myvar = "ROLLBACK" ]]; then
    echo "Rollback (from incremental)"
    sleep 5
    /srv/bin/recover.pl
fi

if [[ $myvar = "SHELL" ]]; then
    echo "Going to shell..."
    sleep 2
    echo "But not any more"
    
else
    exit
fi"

my first question is how can I make it run when I login as "maint"?

my second question is how can I fix what has been changed after "if [[ $myvar = "SHELL" ]]; then" - it used to exit to the  shell but obviously now it just displays "But not any more"

thanks

---

### Post by intermentals on 2010-02-19
Also when I run this using ./maint.sh it returns these errors: 
./maint.sh: 9: [[: not found
./maint.sh: 15: [[: not found
./maint.sh: 21: [[: not found
./maint.sh: 30: [[: not found

I am confused - I used scripts from an OpenBSD setup, is there a change in syntax perhaps?

---

### Post by KeyserSoze93 on 2010-02-19
Create a file called ".bash_login", in the user "maint"'s home folder (it's a hidden file.)

Make it executable, and add the following:

```

bash /path/to/my/script

```

The file should begin "#!/bin/bash", instead of "#!/bin/sh". This is because Ubuntu doesn't use bash as the default shell, so some syntax doesn't work.

As for the SHELL option, just run the command "bash"

Note! This is assuming that you mean that you log in through a CTRL-ALT-F* console, if you log in graphically, you must add some terminal launching command to the GNOME session.

---

### Post by intermentals on 2010-02-19
thank you very much that's sorted that one - do you perhaps know why this next problem is occuring?

"#!/usr/bin/perl -w
# An incremental backup script for an access database core

use warnings;
use strict;

use File::Copy;

our $bakdir = '/srv/smb.bak';
our $corepath = '/srv/samba/core';
our $servercore = 'server';
our $logfile = '/srv/smb.bak/server.log';

sub main() {
    my $hour = sprintf('%0.2d', (localtime)[2]);
    my $min =  sprintf('%0.2d', (localtime)[1]);

    open(LOG,'>>',$logfile) or die "Fatal Error at $hour-$min: Couldn't open $logfile";

    unless ( -r "$corepath/$servercore" ) {
        print LOG "[FAIL-FS] $hour-$min Couldn't find $corepath/$servercore";
        close(LOG);
        die "Failed to find $corepath/$servercore at $hour-$min"
    }

    my $initCore = `md5 -q $corepath/$servercore`;    
    copy ( "$corepath/$servercore", "$bakdir/$servercore.$hour-$min" );
    my $newCore = `md5 -q $bakdir/$servercore.$hour-$min`;

    if ( $initCore eq $newCore ) {
        print LOG "[OK] $hour-$min $newCore";
    }
    else {
        print LOG "[MD5-FAIL] $hour-$min $newCore";
        die "MD5 checksum failure at $hour-$min: Do not rollback to this time"
    }

    close(LOG);
    exit 0;
}

main();"

it returns the errors:

Can't exec "md5": No such file or directory at ./incremental.pl line 26.
Can't exec "md5": No such file or directory at ./incremental.pl line 28.
Use of uninitialized value $initCore in string eq at ./incremental.pl line 30.
Use of uninitialized value $newCore in string eq at ./incremental.pl line 30.
Use of uninitialized value $newCore in concatenation (.) or string at ./incremental.pl line 31.

---

### Post by KeyserSoze93 on 2010-02-19
The command isn't md5, it's md5sum

See if that sorts the other issue (i.e. if it works, it may initialize the variable, thus preventing the issue.)

> **intermentals said:**
> thank you very much that's sorted that one - do you perhaps know why this next problem is occuring?

"#!/usr/bin/perl -w
# An incremental backup script for an access database core

use warnings;
use strict;

use File::Copy;

our $bakdir = '/srv/smb.bak';
our $corepath = '/srv/samba/core';
our $servercore = 'server';
our $logfile = '/srv/smb.bak/server.log';

sub main() {
    my $hour = sprintf('%0.2d', (localtime)[2]);
    my $min =  sprintf('%0.2d', (localtime)[1]);

    open(LOG,'>>',$logfile) or die "Fatal Error at $hour-$min: Couldn't open $logfile";

    unless ( -r "$corepath/$servercore" ) {
        print LOG "[FAIL-FS] $hour-$min Couldn't find $corepath/$servercore";
        close(LOG);
        die "Failed to find $corepath/$servercore at $hour-$min"
    }

    my $initCore = `md5 -q $corepath/$servercore`;    
    copy ( "$corepath/$servercore", "$bakdir/$servercore.$hour-$min" );
    my $newCore = `md5 -q $bakdir/$servercore.$hour-$min`;

    if ( $initCore eq $newCore ) {
        print LOG "[OK] $hour-$min $newCore";
    }
    else {
        print LOG "[MD5-FAIL] $hour-$min $newCore";
        die "MD5 checksum failure at $hour-$min: Do not rollback to this time"
    }

    close(LOG);
    exit 0;
}

main();"

it returns the errors:

Can't exec "md5": No such file or directory at ./incremental.pl line 26.
Can't exec "md5": No such file or directory at ./incremental.pl line 28.
Use of uninitialized value $initCore in string eq at ./incremental.pl line 30.
Use of uninitialized value $newCore in string eq at ./incremental.pl line 30.
Use of uninitialized value $newCore in concatenation (.) or string at ./incremental.pl line 31.

---

