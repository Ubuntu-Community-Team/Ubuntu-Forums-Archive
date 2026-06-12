---
title: "Root"
date: 2012-04-03
forum: General Help
---

### Post by xworld on 2012-04-03
I am trying to make a separate user account with root privileges. I already know that you can give yourself temporary root privileges on your normal account. I am trying to create another user account with which I can login as root and am not sure how.  Thanks

---

### Post by QIII on 2012-04-03
My recommendation:  Don't.

Use sudo.  There is no root account by default in Ubuntu for your own good. ;)

---

### Post by xworld on 2012-04-03
I'm reading a pdf called How Linux Works What Every Superuser Should Know.  One of the requirements for doing the lessons properly is that I need a regular account and a root account. It's for learning purposes and my hand is being held. I'm not looking to start editing config files. Can someone give me this info please?  Thanks

---

### Post by Cheesemill on 2012-04-03
I'm afraid you won't get an answer here, see the following threads for details:
[http://ubuntuforums.org/showthread.php?t=716201]("http://ubuntuforums.org/showthread.php?t=1486138")
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

---

### Post by na5h on 2012-04-03
I agree with QIII...as the official Ubuntu help-pages state: 
"Enabling the Root account is rarely necessary. Almost everything you need to do as administrator of an Ubuntu system can be done via sudo or gksudo. If you really need a persistent Root login, the best alternative is to simulate a Root login shell using the following command..."

These are the help-pages. Please read through the instructions carefully:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by QIII on 2012-04-03
I suspect that you might achieve the objectives of the lessons by having one account in the sudoers file and one not.

For the times you need to sign in as "root", sign in with the account in the sudoers file and use sudo.

If that will not work, see the link provided for a link to the wiki on how to do this.

---

### Post by winh8r on 2012-04-03
You might find the info you need here:

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")


I would agree with QIII above and say that you should only do this on an experimental installation and not on an installation where you have any valuable data.

One wrong command or even a  typing error in a correct command can render your system unusable.

Good Luck with the learning.

---

### Post by CharlesA on 2012-04-03
> **QIII said:**
> I suspect that you might achieve the objectives of the lessons by having one account in the sudoers file and one not.

For the times you need to sign in as "root", sign in with the account in the sudoers file and use sudo.

If that will not work, see the link provided for a link to the wiki on how to do this.
Probably. If they do want to enable the root account, they might want to read the link winh8r posted.

EDIT: I just glanced thru the table of contents and I'm pretty sure you can do almost everything with sudo.

---

### Post by ajgreeny on 2012-04-03
There are plenty of websites which will give you this information, if you really feel you must do things that way.

However, I'm inclined to suggest that if you do not already know and understand how it is possible to enable the root account in Ubuntu, you are not ready to use it in that manner.  You will also find that it is impossible to get any useful information from this forum on using Ubuntu with the root account enabled, and most of the suggested ways to do things that you get from these forum sections will not work for you that way.

Why not try another distro that does use a root account in its normal usage?  There are many available, such as OpenSuse, Fedora, etc etc.  In fact most of the others.

---

### Post by CharlesA on 2012-04-03
+1 to Fedora from me.

---

### Post by QIII on 2012-04-03
It has been a long time since I bothered trying in Fedora, but I'm not sure you can log in from the login screen as "root" with your su password before you do a bit of work, either.

Can you?

I have found no more reason to want to be root in Fedora, OpenSUSE or CentOS than I have in Ubuntu.

---

### Post by CharlesA on 2012-04-03
> **QIII said:**
> It has been a long time since I bothered trying in Fedora, but I'm not sure you can log in from the login screen as "root" with your su password before you do a bit of work, either.

Can you?

I have found no more reason to want to be root in Fedora, OpenSUSE or CentOS than I have in Ubuntu.
The last time I used Fedora that wasn't possible.

I guess they want to login to the terminal as root, which is the only reason I can think of. There is really no reason to login to a GUI as root.

---

### Post by lisati on 2012-04-03
In the 5 years or so that I've been using Ubuntu, I've never had the need to enable "root", and have managed to do all I need using [sudo]("https://help.ubuntu.com/community/RootSudo").

---

### Post by QIII on 2012-04-03
But it seems the OP does need to differentiate between a superuser and a user to use his/her instructional materials.

I am frankly amazed that any recent materials would suggest root over sudoer.

---

