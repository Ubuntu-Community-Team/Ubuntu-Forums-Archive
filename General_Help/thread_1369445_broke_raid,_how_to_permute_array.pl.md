---
title: "broke raid, how to permute_array.pl"
date: 2010-01-01
forum: General Help
---

### Post by darrenvick on 2010-01-01
Hello all,
I am stuck with my raid 5 array down. I used mdadm to create it but forgot the command I used and cant remember the order of my drives. I found this script to try all the combinations, but dont know how to plug in all my data in this script to make it work. if anyone is savy, please help.

script is here : [http://www.linuxfoundation.org/collaborate/workgroups/linux-raid/permute_array.pl](http://www.linuxfoundation.org/collaborate/workgroups/linux-raid/permute_array.pl)

I am running 9.10, 8 sata drives /dev/sd[a-h]3 on /dev/md2 raid 5 xfs format.

Bareword found where operator expected at ./permute_array.pl line 15, near "/dev/md2"
	(Missing operator before d2?)
Bareword found where operator expected at ./permute_array.pl line 25, near "# @_ looks like: ("/dev"
  (Might be a runaway multi-line // string starting on line 16)
	(Missing operator before dev?)
String found where operator expected at ./permute_array.pl line 25, near "sda3", ""
Bareword found where operator expected at ./permute_array.pl line 25, near "", "missing"
	(Missing operator before missing?)
String found where operator expected at ./permute_array.pl line 25, near "missing", ""
String found where operator expected at ./permute_array.pl line 25, near "sdb3", ""
String found where operator expected at ./permute_array.pl line 25, near "sdc3", ""
String found where operator expected at ./permute_array.pl line 25, near "sdd3", ""
String found where operator expected at ./permute_array.pl line 25, near "sde3", ""
String found where operator expected at ./permute_array.pl line 25, near "sdf3", ""
String found where operator expected at ./permute_array.pl line 26, near "my @device_list = @_;(""
  (Might be a runaway multi-line "" string starting on line 25)
	(Missing semicolon on previous line?)
String found where operator expected at ./permute_array.pl line 26, near "da3", ""
Bareword found where operator expected at ./permute_array.pl line 26, near "", "missing"
	(Missing operator before missing?)
String found where operator expected at ./permute_array.pl line 26, near "missing", ""
String found where operator expected at ./permute_array.pl line 26, near "sdb3", ""
String found where operator expected at ./permute_array.pl line 26, near "sdc3", ""
String found where operator expected at ./permute_array.pl line 26, near "sdd3", ""
String found where operator expected at ./permute_array.pl line 26, near "sde3", ""
String found where operator expected at ./permute_array.pl line 26, near "sdf3", ""
String found where operator expected at ./permute_array.pl line 30, near "my $create = ""
  (Might be a runaway multi-line "" string starting on line 26)
	(Missing semicolon on previous line?)
Bareword found where operator expected at ./permute_array.pl line 30, near "--create"
	(Missing operator before create?)
Bareword found where operator expected at ./permute_array.pl line 30, near "--level"
	(Missing operator before level?)
Scalar found where operator expected at ./permute_array.pl line 30, near "5 $MDADM_OPTS"
	(Missing operator before  $MDADM_OPTS?)
Array found where operator expected at ./permute_array.pl line 30, at end of line
	(Missing operator before ?)
Number found where operator expected at ./permute_array.pl line 30, near "@device_list 2"
	(Missing operator before 2?)
Backslash found where operator expected at ./permute_array.pl line 30, near "null\"
String found where operator expected at ./permute_array.pl line 32, near "my $mount =  ""
  (Might be a runaway multi-line "" string starting on line 30)
	(Missing semicolon on previous line?)
Number found where operator expected at ./permute_array.pl line 32, near "$MOUNTPOINT 2"
	(Missing operator before 2?)
String found where operator expected at ./permute_array.pl line 33, near "my $umount =  ""
  (Might be a runaway multi-line "" string starting on line 32)
	(Missing semicolon on previous line?)
String found where operator expected at ./permute_array.pl line 35, near "my $stop = ""
  (Might be a runaway multi-line "" string starting on line 33)
	(Missing semicolon on previous line?)
Bareword found where operator expected at ./permute_array.pl line 35, near "--stop"
	(Missing operator before stop?)
String found where operator expected at ./permute_array.pl line 42, near "die ""
  (Might be a runaway multi-line "" string starting on line 35)
	(Missing semicolon on previous line?)
Backslash found where operator expected at ./permute_array.pl line 42, near "$create\"
	(Missing operator before \?)
Backslash found where operator expected at ./permute_array.pl line 42, near "$err\"
	(Missing operator before \?)
Backslash found where operator expected at ./permute_array.pl line 42, near "n\"
String found where operator expected at ./permute_array.pl line 47, near "print ""
  (Might be a runaway multi-line "" string starting on line 42)
	(Missing semicolon on previous line?)
Backslash found where operator expected at ./permute_array.pl line 47, near "$create\"
	(Missing operator before \?)
String found where operator expected at ./permute_array.pl line 53, near "die ""
  (Might be a runaway multi-line "" string starting on line 47)
	(Missing semicolon on previous line?)
Backslash found where operator expected at ./permute_array.pl line 53, near "$stop\"
syntax error at ./permute_array.pl line 16, near "/dev/md2
"
Can't use global @_ in "my" at ./permute_array.pl line 16, near "@_"
syntax error at ./permute_array.pl line 25, near "# @_ looks like: ("/dev"
Global symbol "$num_devices" requires explicit package name at ./permute_array.pl line 30.
Global symbol "$MDADM_OPTS" requires explicit package name at ./permute_array.pl line 30.
Global symbol "@device_list" requires explicit package name at ./permute_array.pl line 30.
Global symbol "$create" requires explicit package name at ./permute_array.pl line 42.
Global symbol "$err" requires explicit package name at ./permute_array.pl line 42.
Global symbol "$create" requires explicit package name at ./permute_array.pl line 47.
Global symbol "$stop" requires explicit package name at ./permute_array.pl line 53.
./permute_array.pl has too many errors.

---

### Post by darrenvick on 2010-01-02
update:

after plugging away at this, I am close. just seems to be one line not working. I keep getting this error

./permute_array.pl needs at least two component devices
 
here is the filled in script i am using. Please help if you can!
---------------------------------------------------------------------

#!/usr/bin/perl -w

# If you forgot how you built an array and need to try various
# permutations then this is for you...

# based on Mark-Jason Dominus' mjd_permute: permute each word of input

use strict;
use Getopt::Long;

sub usage {
 return "syntax: permute_array --md <md_device> --mount <mountpoint> [--opts <mdadm options>] [--for_real] <all devices>\n";
}

my $MD_DEVICE="/dev/md2";
my $MOUNTPOINT="/share";
my $MDADM_OPTS="";
my $REAL;

################################################################
# This function is passed each permutation of component devices.
# This includes a 'missing' device.
# This is the place to hack command variations etc... 
sub try_array {
  # @_ looks like: 
  my @device_list = @_["/dev/sda3", "/dev/sdb3", "/dev/sdc3", "/dev/sdd3", "/dev/sde3", "/dev/sdf3", "/dev/sdg3", "missing"];
  my $num_devices = scalar $_ [8];

  # This may need a --force... <gulp>
  my $create = "yes | mdadm --create $MD_DEVICE --raid-devices=$num_devices --level=5 $MDADM_OPTS @device_list 2>/dev/null\n";
  # Don't forget to mount read-only
  my $mount =  "mount -oro $MD_DEVICE $MOUNTPOINT 2>/dev/null";
  my $umount =  "umount $MOUNTPOINT 2>/dev/null";
  # and stop the array...
  my $stop = "mdadm --stop $MD_DEVICE 2>/dev/null";

  # REAL == --for_real option
  if ($REAL) {
    # we expect this to succeed
    system $create;
    if (my $err = $?>>8) {
      die "command : $create\n   exited with status $err\n\n";
    }
    # we expect this to fail and are happy if it succeeds
    system $mount;
    if (!(my $err = $?>>8)) {
      print "Success. possible command : \n  $create\n";
      system $umount;
    }
    # we expect this to succeed
    system $stop;
    if (my $err = $?>>8) {
      die "command : $stop\n   exited with status $err\n\n";
    }
  } else {
    # Just show the create/mount/stop commands
    # If you want more control you could use this to write a script
    print "$create\n$mount\n$stop\n";
  }
}


################################################################
# Execution starts here...
#
sub factorial($);

GetOptions ('md=s'      => \$MD_DEVICE,
	    "mount=s"   => \$MOUNTPOINT,
	    "opts=s"    => \$MDADM_OPTS,
	    "for_real"  => \$REAL);

if (!defined($MD_DEVICE) or !defined($MOUNTPOINT)) {
  die &usage;
}

print "using device $MD_DEVICE and mounting on $MOUNTPOINT\n";

# we *always* assume a 'missing' device - not doing so will destroy
# the array...
my @devices = @ARGV;
# how many devices?
my $num_devices = scalar @devices;
if ($num_devices < 2) {
  die "$0 needs at least two component devices\n";
}
# how many base permutations...
my $num_permutations = factorial(scalar @devices);
# try all permutations, substituting 'missing' for each device in
# turn...
for (my $d=0; $d < $num_devices; $d++) {
  my $skip_device = $devices[$d];
  $devices[$d] = "missing";
  print "skipping $skip_device\n\n";
  for (my $i=0; $i < $num_permutations; $i++) {
    my @permutation = @devices[n2perm($i, $#devices)];
    try_array(@permutation);
  }
  $devices[$d] = $skip_device;
}

################################################################
# permutation code

# n2pat($N, $len) : produce the $N-th pattern of length $len
sub n2pat {
    my $i   = 1;
    my $N   = shift;
    my $len = shift;
    my @pat;
    while ($i <= $len + 1) {   # Should really be just while ($N) { ...
        push @pat, $N % $i;
        $N = int($N/$i);
        $i++;
    }
    return @pat;
}

# pat2perm(@pat) : turn pattern returned by n2pat() into
# permutation of integers.  XXX: splice is already O(N)
sub pat2perm {
    my @pat    = @_;
    my @source = (0 .. $#pat);
    my @perm;
    push @perm, splice(@source, (pop @pat), 1) while @pat;
    return @perm;
}

# n2perm($N, $len) : generate the Nth permutation of $len objects
sub n2perm {
    pat2perm(n2pat(@_));
}

# Utility function: factorial with memoizing
BEGIN {
  my @fact = (1);
  sub factorial($) {
    my $n = shift;
    return $fact[$n] if defined $fact[$n];
    $fact[$n] = $n * factorial($n - 1);
  }
}

---

