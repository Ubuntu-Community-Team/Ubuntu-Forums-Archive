---
title: "Send Email from the command line (mutt?)"
date: 2010-07-28
forum: General Help
---

### Post by marcolondonuk on 2010-07-28
I think this one is for expert Linux users. I use Ubuntu 10 and I am looking for a way to send email with a zip attachment to a distribution list containing a few email addresses of recipients. As I would like to keep the confidentiality of the recipients, I would like to use the bcc option to mail the zip file. The zip file can be unzipped later into a single pdf file document.

Because it is a boring process I have to go through once a day, I would like to use the bash shell to automate the sending of the email, hence would very much love to use the command line.

I have looked at a command line utility called mutt, but it seemed to give me an error when I tried to use it. May be I did not set up the correct settings when I first installed mutt...

I am using my gmail.com account to email the recipients. If I do it every day within gmail, as I do now, I have to waste quite a bit of time clicking here and there. Long live the command line!

Thank you very much for any help on this, marco

---

### Post by jobix on 2010-07-28
Try the "mail" command. 
man mail

---

### Post by davidmohammed on 2010-07-28
google was my friend on this...

try this [blog]("http://www.amirwatad.com/blog/archives/2009/03/21/send-email-from-the-command-line-using-gmail-account/") - could be the sort of thing you are looking for.

---

### Post by interval1066 on 2010-07-28
For this method you need to have zmail installed;

cat $TXTFILE | zmail.small -subject "$SUBJECT" -attach \
application/octet-stream:${ATTFILE} $MAILTO

If you can handle perl (the new/old python, according to some) you can try this:

#!/usr/local/bin/perl -w
# Send message with attachments

use MIME::Lite;

$TXTFILE="/tmp/textfile";
$ATTFILE="/tmp/binary_file";
$SUBJECT="Your attachment";
$MAILTO="user\@where.ever";

# Create a new multipart message:
$msg = new MIME::Lite 
   From    => "$ENV{LOGNAME}",
   To      => "$MAILTO",
   Subject => "$SUBJECT",
   Type    => 'multipart/mixed';
        
# Add parts (each "attach" has same arguments as "new"):
attach $msg 
   Type     => 'text/plain',   
   Path     => "$TXTFILE";
attach $msg 
   Type     => 'application/octet-stream',
   Encoding => 'base64',
   Path     => "/tmp/$ATTFILE",
   Filename => "$ATTFILE";

# Output the message to sendmail

open (SENDMAIL, "| /usr/lib/sendmail -t -oi");
$msg->print(\*SENDMAIL);
close(SENDMAIL);

make sure you cpan the mime library, forget if its in the default library collection or not.

---

