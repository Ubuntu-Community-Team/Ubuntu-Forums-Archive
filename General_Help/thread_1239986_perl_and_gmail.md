---
title: "perl and gmail"
date: 2009-08-14
forum: General Help
---

### Post by dunryc on 2009-08-14
Hi Guys here's hoping some one can help !.

I have a perl script which i use to download messages from my gmail account once i have downloaded the messages and saved them in a text file format i need to delete the messages from my gmail account  below is the scipt i use to login and get the messgaes 

> #!/usr/bin/perl
#
############################################################################
#
#          Name: gmailpop.pl
#        Author: Pete Prodoehl
#  Author-Email: [email]pete@rasterweb.net[/email]
#
#  $Id: gmailpop.pl,v 1.2 2005/01/16 20:50:11 pete Exp pete $
#
############################################################################
#
# [http://gmail.google.com/support/bin/answer.py?answer=13287](http://gmail.google.com/support/bin/answer.py?answer=13287)
# Incoming Mail (POP3) Server requires SSL
#
# In gmail, go into 'Mail Settings' and then 'Forwarding and POP' 
# and under 'POP Download' set this setting: 
#   '2. When messages are accessed with POP'
# to 'archive Gmails's copy' that way after the scripts grabs the mail
# it'll be archived and it won't grab it next time...
#
############################################################################


############################################################################
# required modules

use Mail::POP3Client;
use IO::Socket::SSL;


# fill in your details here

$username  = 'pete.leads@gmail.com'; # edit this
$password  = 'delladog';        # edit this

$mailhost  = 'pop.gmail.com';
$port      = '995';


$pop = new Mail::POP3Client(	USER     => $username,
                               	PASSWORD => $password,
				HOST     => $mailhost,
				PORT	 => $port,
				USESSL   => 'true',
				DEBUG	 => 0,
                             );



# if no msgs just exit

if (($pop->Count()) < 1) {
	print "No messages...\n";
	exit;
}



# if msgs, tell how many

print $pop->Count() . " messages found!\n";



# loop over msgs

for($i = 1; $i <= $pop->Count(); $i++) {
	
	print $pop->Head($i) . "\n";
	print $pop->Body($i) . "\n";
	print "\n";
	
}


# close connection

$pop->Close();

exit;



__END__

=head1 NAME

gmailpop.pl

=head1 DESCRIPTION

This script checks a gmail account using POP/SSL

=head1 AUTHOR

Pete Prodoehl E<lt>pete@rasterweb.netE<gt>

=head1 LICENSE

This program is free software; you can redistribute it and/or modify it 
under the terms of the GNU General Public License as published by the Free 
Software Foundation.

=cut




any ideas on how I can delete archive the emails after reading would be really helpful 

Many thanks Pete

---

### Post by sdennie on 2009-08-14
This can be set server side by going to Settings->Forwarding and POP/IMAP.  You can set it to leave the message, delete or archive them after POP access.

---

