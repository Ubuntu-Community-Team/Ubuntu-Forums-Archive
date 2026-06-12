---
title: "Can't get my email from LAN"
date: 2011-09-19
forum: General Help
---

### Post by AlexBooton on 2011-09-19
Hi,

Just upgraded to 11.04 and Dovecot is now installed along with Postfix.

So now, users on the LAN are unable to log into Postfix to get their mail (mostly from Outlook).

I found something about a change to /etc/dovecot/dovecot.conf to uncomment the line "disable_plaintext_auth = yes" and change the yes to no.

I did that, restarted postfix and dovecot but it still doesn't work.  In fact I did this multiple times and pulled out my hair between times.  :p

What am I missing?

I want to keep it as simple as possible.  Plaintext authentication is fine with me... if it works.

Thanks

---

### Post by AlexBooton on 2011-09-20
Things are really screwed up now.  

Checking the configuration with dovecot -n was yielding lots of errors; and there appeared to be lots of out-of-place lines in dovecot.conf.  I don't know how this happened but it seems I may have somehow messed up royally in trying to edit the file.

I thought I could correct the problem by reinstalling dovecot.  I removed dovecot.conf first assuming I'd get a new/clean copy.  

That didn't happen.  Dovecot was reinstalled but a new conf file was not installed.

So I copied the file from /usr/share/dovecot.  That files seems to be quite different from the one I was working on in /etc/dovecot; and dovecot -n yields lots of errors.  The last error was this:
Error: Error in configuration file /etc/dovecot/auth.d/01-mail-stack-delivery.auth line 1: Unknown setting: mechanisms

I NEVER touched that file!  So I am totally lost at sea.

I'd like to start over with a clean dovecot; but how?

Any help would be greatly appreciated.

---

### Post by SeijiSensei on 2011-09-20
sudo apt-get purge dovecot

removes the program and all associated files.

---

### Post by scarleo on 2011-09-20
"So now, users on the LAN are unable to log into Postfix to get their mail"

You mean Dovecot, right?

---

### Post by AlexBooton on 2011-09-20
> **SeijiSensei said:**
> sudo apt-get purge dovecot

removes the program and all associated files.

Thanks for the assistance.  Tried it but it didn't work.  I get:

# apt-get purge dovecot
Reading package lists... Done
Building dependency tree
Reading state information... Done
Virtual packages like 'dovecot' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.

Dovecot is a "virtual package"?  What does that mean?

Is there another way?

Thanks

---

### Post by AlexBooton on 2011-09-20
> **scarleo said:**
> "So now, users on the LAN are unable to log into Postfix to get their mail"

You mean Dovecot, right?

I guess.  I'm unclear as to what dovecot and postfix do in relation to each other.

Thanks

---

### Post by scarleo on 2011-09-20
> **AlexBooton said:**
> Thanks for the assistance.  Tried it but it didn't work.  I get:

# apt-get purge dovecot
Reading package lists... Done
Building dependency tree
Reading state information... Done
Virtual packages like 'dovecot' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.

Dovecot is a "virtual package"?  What does that mean?

Is there another way?

Thanks

You can try in synaptic, right click and choose remove completely. It should take care of dependencies. 

Dovecot is the POP/IMAP server to which people normally login to pull their mails, postfix delivers the mail to Dovecot. (Basically, but there's more to it ;))

---

### Post by AlexBooton on 2011-09-20
> **scarleo said:**
> You can try in synaptic, right click and choose remove completely. It should take care of dependencies. 

Dovecot is the POP/IMAP server to which people normally login to pull their mails, postfix delivers the mail to Dovecot. (Basically, but there's more to it ;))

Hi,

I used synaptic as you suggested but it didn't relaod the conf file.

At this point I desperately need that file.  

Since this thread has gone off on some side tracks I've posted a new thread with a plea for a copy of the file.  See the thread here:  [Desperately need dovecot.conf file!]("http://ubuntuforums.org/showthread.php?p=11269338#post11269338") 

Thanks!

---

### Post by AlexBooton on 2011-09-25
The problem was that dovecot.conf did NOT have the line:

   protocols = pop3

I had done quite a bit of googling and posting here but nowhere did I see this issue mentioned.

Hopefully this post will help the next guy.

BTW, I only found this problem via webmin's GUI for dovecot.  Once I checked the available options, I realized I had no selection for "Serve mail protocols".

Thanks to all the folks that offered suggestions.

---

