---
title: "I did something dumb, can't log in"
date: 2010-04-01
forum: General Help
---

### Post by drfox on 2010-04-01
Instead of using gedit, I copied the script below into a terminal, and now I can't log in to X with any user credentials. I go from login screen to black screen to login screen. I assume I have changed a startup script, but I have no idea which one. I can log in as root in terminal mode, so whatever I need to edit or delete I will be able to do. HELP, Please

#!/usr/bin/perl -w
use strict;
use FindBin '$Bin';

##################################################
# Hamachi Keep Alive (for hamachi-lnx-0.9.9.9-20)
# Written by Dimitri Stamatis <www.eflamenco.com>
#
# Detects and tries to correct connectivity problems with
# Hamachi on Linux. Such problems are logged to a file
# called hamachi-keep-alive.log, located in the same folder
# as the perl script.
#
# This software is offered without warranty. You acknowledge
# and agree to hold the author completely harmless, in the
# event of any harm, loss, damage, or consequences relating
# to the use of any part of this software, or instructions.
#
# Ubuntu Installation Instructions:
# 1) Copy this file to a location with read, write access.
# 2) Make it executable, right-click file and click Properties,
#    Permissions, "Allow executing file as program".
# 3) Open a terminal and type: crontab -e
#    (Do *NOT* use sudo!)
# 4) Type: * * * * * perl /PATH/TO/hamachi-keep-alive.pl
#    (Make sure it's 5 asterisks.)
# 5) Press CTRL-X
# 6) Press Y
# 7) Press ENTER
#
# Done! The script will run automatically, once per minute,
# even after reboot. To stop it, remove entry from crontab.
##################################################

my $log_file = $Bin . "/hamachi-keep-alive.log";
my $results;
my $command;

# initialize hamachi
foreach $command (("start","login","list")) {
	$results = `hamachi $command`;
	if ($? && $command eq 'list') {
		log_it("failed to initialize");
    	die;
	}
}

# get list of computers on hamachi network
my @computers = split(/\n/, $results);

# find first active computer and ping it
foreach my $computer (@computers) {
	if ($computer =~ /\* (5\.\d{1,3}\.\d{1,3}\.\d{1,3})/) { # found active computer
		my $IP = $1;
		`ping -c 1 $IP`;

		if ($?) { # ping failed
			my $message .= "couldn't ping $IP - restarting hamachi... ";

    		$results = `hamachi stop`;
			$message .= ($? ? "couldn't stop hamachi (already stopped?)... " : "");

    		$results = `hamachi start`;
			$message .= ($? ? "failed." : "done.");

			log_it($message);
		}

		last;
	}
}

sub log_it {
	my($message) = @_;
	my $log_entry = "[" . localtime() . "] $message";

	if (-e $log_file) {
		my $log_file_size = -s "$log_file";
		if ($log_file_size >= (1024 * 1024)) { # getting too big - delete log
			unlink($log_file);
		}
	}

	open my $FILE, ">>$log_file" or die "cannot open file $log_file: $!";
	print $FILE $log_entry, "\n";
	close $FILE;

	return;
}

Thanks..Larry

---

### Post by drfox on 2010-04-01
Bump
Isn't there anyone who can tell me what startup script I have created or corrupted? 
I have what caused my problem narrowed down to the bottom half of the code:

# initialize hamachi
foreach $command (("start","login","list")) {
$results = `hamachi $command`;
if ($? && $command eq 'list') {
log_it("failed to initialize");
die;
}
}

# get list of computers on hamachi network
my @computers = split(/\n/, $results);

# find first active computer and ping it
foreach my $computer (@computers) {
if ($computer =~ /\* (5\.\d{1,3}\.\d{1,3}\.\d{1,3})/) { # found active computer
my $IP = $1;
`ping -c 1 $IP`;

if ($?) { # ping failed
my $message .= "couldn't ping $IP - restarting hamachi... ";

$results = `hamachi stop`;
$message .= ($? ? "couldn't stop hamachi (already stopped?)... " : "");

$results = `hamachi start`;
$message .= ($? ? "failed." : "done.");

log_it($message);
}

last;
}
}

sub log_it {
my($message) = @_;
my $log_entry = "[" . localtime() . "] $message";

if (-e $log_file) {
my $log_file_size = -s "$log_file";
if ($log_file_size >= (1024 * 1024)) { # getting too big - delete log
unlink($log_file);
}
}

open my $FILE, ">>$log_file" or die "cannot open file $log_file: $!";
print $FILE $log_entry, "\n";
close $FILE;

return;
}

---

