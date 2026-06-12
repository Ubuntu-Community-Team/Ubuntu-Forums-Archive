---
title: "Scripting help: extract data from email"
date: 2009-07-06
forum: General Help
---

### Post by t0p on 2009-07-06
Scenario: I send an email to a gmail address that my computer fetches new mail from periodically. The email has a certain subject line that procmail watches for and puts in a particular folder. The body of the email contains an ip address that a script will use to make a ssh connection. 

Can someone please tell me how I write the script to take the ip address from the email and call by a variable name that a script can use later

---

### Post by t0p on 2009-07-06
Okay, no one's rushed to help yet.  And this thread is rapidly falling into oblivion.

Well, I'll give it a discreet little *bump* while clarifying what I want to do.

I send an email to a certain address that my home computer polls regularly.  So the email gets downloaded to home machine.  The email has a special subject-line, which procmail is looking out for.  So, instead of going to the normal mailbox, this email goes to a special directory.

I know how to do the above, with procmail etc.  It's what follows that I need help with.

I need a script to take the email and strip away the headers etc, so all that's left is the body of the email.  We'll call this textfile text.txt.

The file text.txt consists of an ip address.  I am going to need the home computer to make a connection with the computer at this ip address - ssh I think.  So I need a script to take the ip address from text.txt, and store it in a form that it will be able to use to make that connection.

Is that all clear?  I hope so.

So, the questions I need answered are:

1. How do I get a script to take an email and strip away all the headers and whatever else to leave just the body of the email - in this case, leave just the ip address?

2. How do I get a script to take some text - the ip address in this case - and store it as a variable that it can later use in another command? I know the script could **'cat text.txt'**, which would print the contents of the file - basically, it would print the ip address.  But how do I then pipe that to a ssh command?

All help gratefully received.

---

### Post by spibou on 2009-07-06
> **t0p said:**
> Okay, no one's rushed to help yet.  And this thread is rapidly falling into oblivion.

Well, I'll give it a discreet little *bump* while clarifying what I want to do.
The more details you give the quicker and better answers you're going to get.
> 
I need a script to take the email and strip away the headers etc, so all that's left is the body of the email.  We'll call this textfile text.txt.

```
awk 'flag {print $0} $0 ~ /^[[:space:]]*$/ {flag=1}' email-file 
```
is promising for stripping the headers and printing the result to stdout.
> The file text.txt consists of an ip address.
Does this mean that the body of the email will have the IP address and nothing else ? If yes then
```
tail -n -1 email-file
```
will print this address. You don't need to strip the headers. You can do
```
ip=$( tail -n -1 email-file )
```to put the address in variable ip.

---

### Post by blueridgedog on 2009-07-06
If you are using procmail, you can try and get just the body into the text file with a recipe.  
```

:0 bc
* ^Subject:.*YourSpecialSubject
| formail -I -f "from"  >> /home/USER/folder/text.txt
```

Once you have that debugged, you can then tackle bash or Perl as a cron job to look at the folder, if it sees a file, open it and parse it for an ip address and initiate the ssh connection.

Something crude and untested in Perl:

```
#:!/usr/bin/perl

#

if (-e "/home/USER/folder/text.txt")
{
open (TEXTFILE, "/home/USER/folder/text.txt") ||

	die "Can not open file $file: $!";
while (<TEXTFILE>) {
	$IP =~ m/^\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}\$/;        
	`ssh $IP`;
	}
close (TEXTFILE);
} 
```

This could be called via cron every five minutes or so.

These are just "big strokes" and the devil will be in the details (and the debugging).

I recommend testing each step cleanly before trying to move on to the whole.

---

### Post by Celauran on 2009-07-06
> **t0p said:**
> 1. How do I get a script to take an email and strip away all the headers and whatever else to leave just the body of the email - in this case, leave just the ip address?

```
grep -o '[0-9]\{1,3\}\(\.[0-9]\{1,3\}\)\{3\}'
```

---

### Post by t0p on 2009-07-06
Thank you very much, **blueridgedog** and **spibou**!  I couldn't think for the life of me how to do this... but now your replies have got me on the right track.

When I get a chance later, I shall set to testing your scripts: hopefully I'm on the homeward stretch now.

Thanks again!  :)

---

### Post by blueridgedog on 2009-07-06
You may need to install formail (I can't find it on my default 8.10 system) and keep in mind that most of my code is more or less roughed out and you will have to tweak each.  Good luck.

---

