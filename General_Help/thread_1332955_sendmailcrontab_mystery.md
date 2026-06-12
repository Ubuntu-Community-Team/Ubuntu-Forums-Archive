---
title: "sendmail/crontab mystery"
date: 2009-11-20
forum: General Help
---

### Post by ufarmer on 2009-11-20
Hi,

I have saved the following script as grapes.pl:

#!/usr/bin/perl

use warnings;
use strict;

my $email = "name\@domain";
my $subject = "Subject Line";
my $body = "Message body\n";

open (OUT, "|/usr/sbin/sendmail -t");
print (OUT "From: $email\n"); ## don't forget to escape the @
print(OUT "To: $email\n");
print(OUT "Subject: $subject\n");
print(OUT "\n");
print(OUT "$body\n");
close(OUT);
exit(0);

When I run it from the command line the email is not sent and I get a blinking cursor on the command line -- as if it's hanging or something.  If I alter this line:

open (OUT, "|/usr/sbin/sendmail -t") of die "Unable to open pipe: $!\n";

the script doesn't die -- implying that the pipe is open and should be working.

Mysteriously, this script is running as a cron job and sending emails.  So how is it running as a cron job but not from the command line.

Any advice is appreciated.

---

### Post by ufarmer on 2009-11-20
In fact, I am definitely having an issue with sendmail on the command line.  Neither a line containing only a "." nor Ctrl-d signals the end of input.  For example:

/usr/sbin/sendmail [email]person@domain.com[/email]
This is a test.
.

and

/usr/sbin/sendmail [email]person@domain.com[/email]
This is a test.
Ctrl-d

both fail to send "This is a test." to [email]person@domnain.com[/email].  In fact the cursor just blinks on the command line apparently still waiting for input to sendmail.

By the way, this fails as well:

/usr/sbin/sendmail [email]person@domain.com[/email] < email.txt

---

