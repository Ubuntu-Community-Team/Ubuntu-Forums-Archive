---
title: "Can not log in after upgrading Virtual box"
date: 2010-02-15
forum: General Help
---

### Post by steve723 on 2010-02-15
I just upgraded virtual box to the latest version.  Now I can't login to my virtual Ubuntu.  Even tty1 doesn't work. I forgot which version, jackalop I think.  I use Kubuntu Karmac on my ASUS Eee netbook and that works fine.  I use ubuntu on my laptop virtualized under Winblow$ vista64 BIT.  That worked great before I upgraded virtual box.

You need more emot icons ie... confused, mad, etc...

**solved**

---

### Post by jamesisin on 2010-02-15
I use a repository to keep VB up to date:

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

See the section beginning "Debian-based Linux distributions".

Once you add the repository and the associated key, note that each version will show separately in Synaptic.

---

### Post by steve723 on 2010-02-15
> **jamesisin said:**
> I use a repository to keep VB up to date:

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

See the section beginning "Debian-based Linux distributions".

Once you add the repository and the associated key, note that each version will show separately in Synaptic.

As I said above I run VB from Winblow$.  A linux repository is for linux programs not Winblow$ programs.  I can't login so it's pointless anyway.


Thanks for trying but that doesn't help.

---

### Post by jamesisin on 2010-02-15
Sorry, that wasn't entirely clear.

So you are running Windows with Ubuntu in VB and when you attempt to start up your virtual Ubu you run into some sort of problem.  What exactly happens?

---

### Post by steve723 on 2010-02-15
> **jamesisin said:**
> Sorry, that wasn't entirely clear.

So you are running Windows with Ubuntu in VB and when you attempt to start up your virtual Ubu you run into some sort of problem.  What exactly happens?

When I boot the VM, I get to the graphical login screen and It will not allow me to login.  It used to work before I upgraded to the latest version of Virtual box.  As I said above going into a tty1 login results in exactly the same problem.

---

### Post by jamesisin on 2010-02-15
So you get to the login screen.  You click to choose a user and type in a password.  Then what happens?

---

### Post by steve723 on 2010-02-16
[QUOTE=jamesisin;8833562]So you get to the login screen.  You click to choose a user and type in a password.  Then what happens?[

It doesn't let me choose the user name, I have to type It In.  after I enter the password it says wrong password even though It Is the same one that I have used I have used all the time!  I tried several times in case I made a typo and no, the caps lock key Is not a problem.  I am the only one that uses the computer, so unless the Virtual box upgrade did something then It should work.

---

### Post by jamesisin on 2010-02-16
Indeed that does seem odd.  The VM should not be effected by the update.  That file is not updated, as it were.  Are there any other accounts on that VM into which you might gain access?  Do you have ssh turned on for that VM?

---

### Post by steve723 on 2010-02-16
> **jamesisin said:**
> Indeed that does seem odd.  The VM should not be effected by the update.  That file is not updated, as it were.  Are there any other accounts on that VM into which you might gain access?  Do you have ssh turned on for that VM?

No other accounts.  I don't how to tell If SSH Is turned on for the VM.

---

### Post by jamesisin on 2010-02-16
By default ssh is off on new Ubuntu systems.  If you didn't enable it, it's probably disabled.

You can test it by opening the VM (just to the login screen is fine) and try to ssh into that VM using the IP address VB assigns to that machine.  You can confirm you are using the correct IP address using ping.  Since you are using a Windows machine as the host, you may want to add Cygwin to give you bash and of course ssh:

[http://www.cygwin.com/](http://www.cygwin.com/)

Very useful even if it doesn't work for this problem.

Assuming you can't gain access by ssh, let's take a look at your login to make sure you are doing everything correctly.

First, why do you have to type your username?  Did you change from the default 9.10 login screen?

Next, try typing your password into the username field to determine that your keyboard and the VM are interacting correctly (ie, make sure what you type at the keyboard is what appears in the username field).

Finally, we can try testing this VM in another VB (another machine, downgrade, &c) to see if that makes any difference.  I believe this is the wrong course, but we should test all possible avenues.

---

### Post by steve723 on 2010-02-16
OK so now I feel stupid.  I forgot on this VM I used my Winblow$ password.  I entered my Winblow$ password and logged in.  Sorry my bad.  :rolleyes:

---

### Post by jamesisin on 2010-02-16
These things happen.  Be sure to mark this thread as SOLVED in Thread Tools above.

---

