---
title: "Lost Desktop"
date: 2010-01-14
forum: General Help
---

### Post by sellewe on 2010-01-14
I am running ubunto 8.4 but when I boot up it goes to command lines and not to the usual desktop.  I have tried to boot from a CD but I do not know how to make this run.  This is a machine with only ubunto installed, I am a newbe to lynux so any help would be appreciated.

---

### Post by staf0048 on 2010-01-14
When you get to the command line, try running:

```
sudo /etc/init.d/gdm start
```

That should get you to the login (gdm) screen with any luck.

Question though:  What were you doing before this happened?  Were you editing configuration files?  If so, what were you editing/trying to accomplish?

---

### Post by sellewe on 2010-01-14
Thanks, it did get me to the log in but it will not accept my password.  Is there any to force the CD to run?

---

### Post by sellewe on 2010-01-14
Sorry I did not answer you question.  I was trying to update the OS, which seemed to work ok but the next time I booted up I had the problem.  I have tried searching the fourms reading all the newbe stuff I can find but as the computer will not boot from the CD I am at a loss to know what to try next.

---

### Post by staf0048 on 2010-01-14
Is your BIOS set to start up from the CD first?

Whatever settings you may have on your current OS should not matter when it comes to booting from the CD.  But, if your BIOS is set to boot from the HDD first, you will never get to the cd (unless you disconnect your HDD).  

When your computer starts up and the initial boot screen appears, hit esc, F10, F12, (or whatever is tells you to use) to get to the BIOS setup or boot setup.  Make sure your CD ROM is 1st in the boot order, restart, and see if that helps.

---

### Post by sellewe on 2010-01-14
The boot sequence is set as C,A,SCAI and it will not allow me in to change it.  I hate to be defeated but I think Lynux  might manage this.  Unless you can suggest another step I will call it quits for now.
Thanks for your help,

---

