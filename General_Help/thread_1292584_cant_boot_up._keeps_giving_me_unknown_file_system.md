---
title: "cant boot up. keeps giving me unknown file system"
date: 2009-10-16
forum: General Help
---

### Post by damnidunno on 2009-10-16
im alinux noob, and im tryin to give ubuntu a try, but i always have annoying problems that chase me away. hopefully i can get this resolved soon before i give up for a few more years/ or forever.

I am tryin to get ubuntu 9.10 beta to work, and i've gone through the normal install several times, and tell it to set up the boot and everything (default)

but for some reason now it wont boot up anything. It simple says something like:

grub error
reason: uknown filesystem
grub rescue 

(or something close to that).

And i formated the drive several times and reinstalled ubuntu and it keeps happening.

I had ubuntu working fine earlier when i had it installed alongside my windows, but it then this error started to happen.

is there a way to resolve it?

Right now im n the live cd.

---

### Post by mocoloco on 2009-10-16
Sorry to hear you're having problems. Remember though that this is a beta release, and a lot can and will change before the final release.
What kind of system is it (laptop/desktop, brand and model, etc)?  What specs (CPU, RAM, HD, etc)?

---

### Post by damnidunno on 2009-10-16
i have a dell studio xps. i7core. 4gb ram
radeon 4850 gfx card
two hard drives:
1)320 gb hard drive, which i install ubuntu to.
2) 650 gb hard drive, i place all my important files.

i cant get anything to work for me on this now. I reinstall and reinstall. try different mount methods, and nothing.

When i try to load grub in the terminal it tells me its not even installed. i dunno

---

### Post by mocoloco on 2009-10-16
When you reinstall are you selecting to use the entire drive?  By default it will resize existing partitions, leaving your previous "bad" install.  Have you tried with a 9.04 disc?  That would allow you to verify it's an issue only with 9.10, which is probably the case since 9.10 uses a newer version of grub.

---

### Post by damnidunno on 2009-10-16
yes i select entire drive. and i've even did the manual method where i delete alll the partitions on the drive and create a new one. still didnt help.

---

### Post by mocoloco on 2009-10-16
It's quite possible you have a bad disc. Boot from the CD and do the "check disc for defects" option.  Also get the exact error message and search for it.  See if there's a bug on launchpad that matches it, if not file a new bug.  Again, it's beta, which makes you an official "beta tester" by using it :P
This might get you started [https://launchpad.net/+search?field.text=grub2+uknown+filesystem&field.actions.search=Search]("https://launchpad.net/+search?field.text=grub2+uknown+filesystem&field.actions.search=Search")

And I still think trying to install 9.04 might rule out some things, like hardware issues.

---

### Post by arrange on 2009-10-16
If you're starting with Linux, please do not try to install a beta release. Opt for a more stable one :)

---

### Post by damnidunno on 2009-10-16
I got it to work again.

I have a second hard drive that used to be my main hard drive. (its my largest, so i decided to keep my files on it since i reformat and install windows alot) and it seemed to keep the windows boot loader on it. Even though i tried to delete all the extra partitions on it.

Some how it became corrupt with me tryin to get ubuntu to work. I gave up on ubuntu and tried to reinstall windows a bit ago, but it would never reload the installer when it restarted, it just wanted me to read from cd, or shows a blinking line. 
Turned out some how the boot loader partition on my second drive was corrupt. 

So i completely unpluged my second hard drive, and reinstalled ubuntu and it worked just fine. im on it now.

Some how i gotta figure out how to remove the windows boot loader from my second hard drive. hm.

but i got it working! yay! now i just have to figure out how to get my radeon drivers to work ha.

thanks everyone

---

