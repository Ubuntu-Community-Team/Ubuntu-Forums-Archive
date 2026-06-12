---
title: "2nd Graphics Card Not Detected"
date: 2012-07-19
forum: General Help
---

### Post by flossy12 on 2012-07-19
Fresh Ubuntu 12.04 Install.

I have three monitors connected through Sapphire Radeon HD 6870 x 2.

Now, I can use two of my monitors fine from the first graphics card, but the second graphics card is not accesible through the AMD Catalyst Control Centre.

It merely says [unknown adapter].

It works fine when I boot into Windows. Any suggestions?


Really really enjoying Linux but not being able to use my main monitor or have triple monitor set up is going to force me back to windows! :( 

Thanks.

---

### Post by QIII on 2012-07-19
After installing the driver, did you do

```
sudo aticonfig --adapter=all --initial
```

before restarting?

---

### Post by flossy12 on 2012-07-19
> **QIII said:**
> After installing the driver, did you do

```
sudo aticonfig --adapter=all --initial
```

before restarting?

No I did not, this is my first ever Linux installation sorry.

Shall I do it now and re-start?

---

### Post by QIII on 2012-07-19
First, how did you install the driver?

---

### Post by flossy12 on 2012-07-19
> **QIII said:**
> First, how did you install the driver?

I used this:

[http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers)

until I got to:

```
nstalling the lastest 12.6 ATI/AMD driver
Download the appropriate driver for your machine here from the AMD/ATI Website and then enter the following into the terminal (replace the astrix "*" in the string below to the driver name e.g. 12-6-x86_64 and remember to navigate to where you downloaded the driver to):
```

But the AMD website was playing up so I couldn't download it.

So I didn't go any further with the tutorial.


At least ... I think it was that one. I used so many in a desperate ditch attempt to get it to work I may not have. 

Sorry to be completely unhelpful!

Thanks for your help so far.

---

### Post by QIII on 2012-07-19
The 12.4 driver is in the Ubuntu repo and it is much easier to do that way than to try to install the very latest and greatest in that tutorial.

So, if that tutorial didn't work, how did you finally get it installed?

---

### Post by flossy12 on 2012-07-19
> **QIII said:**
> The 12.4 driver is in the Ubuntu repo and it is much easier to do that way than to try to install the very latest and greatest in that tutorial.

So, if that tutorial didn't work, how did you finally get it installed?

I ... uh.

Don't really know come to think of it, I ended up bombarding my computer with so many commands copied off the Internet...


How do I completely eradicate it from my computer so I can start again with you?

---

### Post by QIII on 2012-07-19
We can try the general method that will remove the driver if it was installed via an aptitude/apt/additional driver/synaptic method.

It will require a reboot, which should get you back to the default open source driver.

If it will not reboot, can you be near another machine so I can talk you through getting back in?

---

### Post by flossy12 on 2012-07-19
> **QIII said:**
> We can try the general method that will remove the driver if it was installed via an aptitude/apt/additional driver/synaptic method.

It will require a reboot, which should get you back to the default open source driver.

If it will not reboot, can you be near another machine so I can talk you through getting back in?

Yes that's fine I am on my Laptop now.

Fire away with instructions.

Thanks!

---

### Post by QIII on 2012-07-19
OK.  First, this needn't have been this hard for you, and I am sorry.  Sometimes the tutorials one finds on the web can get you in trouble.

The AskUbuntu answer was fine -- if you really want the latest 12.6 driver.  However, the 12.4 driver is in the repo and unless the shiniest new driver has something far and away better than that one, 12.4 will do.

Even the open source drivers will generally work and should be used if they suit your needs.  I can't honestly say how well they would work with two cards, but we might just find out.

Do the following in the terminal and post back the results (click the # sign above to create code tags and copy the text back in to your post.)  To get the info out of the terminal, highlight it and press Cntl+Shift+C.

```
sudo apt-get remove --purge fglrx fglrx-amdcccle
```

Don't reboot just yet.  Let me know what happens.

---

### Post by flossy12 on 2012-07-19
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package fglrx-amdcccle is not installed, so not removed
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  fglrx*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 175076 files and directories currently installed.)
Removing fglrx ...
Purging configuration files for fglrx ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-26-generic
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot

```

Done.

---

### Post by QIII on 2012-07-19
OK.  The next step is to reboot and make sure you get back to your desktop.  You should be running the default open source driver just as you were using when you first installed.

When you get there, see if the normal display configuration tools will let you configure all three monitors.

If you have trouble with the reboot, let me know and I'll talk you through how to get back to your desktop.

Again, sorry this is going so hard for you.  There was no need for it to have been so.

---

### Post by flossy12 on 2012-07-19
> **QIII said:**
> OK.  The next step is to reboot and make sure you get back to your desktop.  You should be running the default open source driver just as you were using when you first installed.

When you get there, see if the normal display configuration tools will let you configure all three monitors.

If you have trouble with the reboot, let me know and I'll talk you through how to get back to your desktop.

Again, sorry this is going so hard for you.  There was no need for it to have been so.

Re-Booted fine.

Still, only 2/3 of my monitors are available from System Settings > Display

---

### Post by QIII on 2012-07-19
Well, we have you back to a clean start.

OK.  The next step is to go to the ATI wiki in my signature.  I wrote the part I am going to direct you to, so if you have any questions you are talking to the right guy.

In the table of contents, click the entry that says "Using the Ubuntu repositories (alternate command line method, including hardware acceleration)"

We are NOT going to deal with acceleration yet, so don't go in to that.  Just follow steps 1 - 6.

You've already removed the fglrx driver, but follow all of the steps in order so nothing is missed.

When you get to the part that says

```
sudo aticonfig --initial
```

use

```
sudo aticonfig --adapter=all --initial
```

(I need to update the wiki to add that line for multiple cards, so I'll do that when we're done.)

---

### Post by flossy12 on 2012-07-19
Completed 1-6 and used the command you told me.


When I re-booted I got this:

[IMG]http://i.imgur.com/qlgei.png[/IMG]

---

### Post by QIII on 2012-07-19
OK.  Can you see at least a workable screen?  This is where the Catalyst Control Center will come in.  That's how we'll make the adjustments you want.

---

### Post by flossy12 on 2012-07-19
> **QIII said:**
> OK.  Can you see at least a workable screen?  This is where the Catalyst Control Center will come in.  That's how we'll make the adjustments you want.

In the CCC! And my monitor attatched to the 2nd graphics card is alive! :D


Sadly, all I get is a white screen and cannot drag windows on to it.

I alligned them appropriately

[20"][22" (2nd gfx card][19"]

and enabled Xinerama

Where do I go from here?

Thanks so much for your help! So glad I can switch to Linux now!

---

### Post by QIII on 2012-07-19
I'm going to have to do a bit of research.  I think I've encountered this before, but I'll have to look through some old notes.

Unfortunately, at the moment I have a dinner date and a play to go to with Mrs. QIII.  (Well, fortunate for ME!)

Can you work with what you have until tomorrow?  Alternately, start a new thread -- with a descriptive subject line.  That will get more attention than the tail end of this one.

I'll try to find the post tomorrow.  I can look up your posts by clicking on your nickname, so I should be able to find anything new.

Edit:  Oh, wait.  Try disabling Xinerama.

---

### Post by flossy12 on 2012-07-19
It works!

OMG! Haha, thank you SO SO SO much! Is there any way to only have the launch bar on my main screen and no where else?


Additionally, where should I start learning more about Ubuntu? There's such a wealth of knowledge I dont know where to begin!


Really appreciate your help!


P.S I am going to be coding in C++, any experience with Linux && C++?

---

### Post by QIII on 2012-07-19
For keeping it only on one screen only, yes.  You'll have to go to the settings manager -- but, dude, I gotta run!

(And yes, I do have a tiny bit of experience with C++ and Linux. ;)  However, there is a Programming subforum that I don't often frequent.  There are plenty of people who hang out there and would be willing to help you out.)

---

### Post by z3nhakr on 2012-07-19
sorry to intrude but does your graphics card show up when you run the command "lspci"?
just thought I'd ask because it's a good first check

---

### Post by SteveHillier on 2012-08-13
> **QIII said:**
> I'll try to find the post tomorrow.  I can look up your posts by clicking on your nickname, so I should be able to find anything new.

Edit:  Oh, wait.  Try disabling Xinerama.

Sorry to jump on your thread but...

Have just been able to get my two graphics cards to show more then one monitor and like the OP I got a white screen on the second monitor after all the drivers installed and configured.

However, rather than disabling Xinerama I had to enable it to get the screens to work alongside each other.

The trouble is that with Xinerama enabled you cannot see the display monitors pages in Catalyst Centre.  Two switch Xinerama on or off required a reboot.

I also had an issue.  On my test bed I put both monitors on one card and they configured OK.  When I moved one of those monitors to the second graphics card Catalyst Centre did not configure the resolution properly.  Diving into xorg.conf allowed me to sort that out.  So I think I am now ready to put all 4 screens onto my system and get to work.

One issue I have is that the inbuilt display utility, which should allow me to place the monitors in a suitable arrangement for me is throwing and RandR extension missing problem.  I shall be searching this later.

Thanks guys


I am hoping that this will allow me to remove the program launcher bar from all but one screen.

---

