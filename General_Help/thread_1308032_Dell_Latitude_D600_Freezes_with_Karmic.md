---
title: "Dell Latitude D600 Freezes with Karmic"
date: 2009-10-31
forum: General Help
---

### Post by ennoil on 2009-10-31
I installed Karmic on my son's Latitude D600 yesterday. 
I had to do a straight install from the outset since while using the Live CD install would also freeze.
(my son did the initial install with my direction since he is almost 9 years old and I am not home).
After he did the initial install and installed openssh-server I ssh'd in and install ubuntu-restricted-extras, kubuntu-desktop (he and I prefer KDE), as well as a few other packages. Now when he logs on he can play around for a bit then after 2-3 minutes the laptop just freezes. He has left it to sit for an hour and still no joy. Eventually he has to use the power button to force the machine off.
The system freezes on both GNOME and KDE desktops.
Is anyone else having problems with this?
John

---

### Post by P4man on 2009-10-31
not a great idea to install if the livecd already freezes. One of the points of a livecd is testing hardware compatibility before you install.

Anyway, go have a look in the log files. Run dmesg and check out /var/log/messages and post anything that looks relevant. Most causes of freezin in linux are caused by bios problems. You could try booting your kernel with ```
noapic
``` and/or ```
nolapic
```. If you dont know how, have a look here:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Contains instructions for trying it on a live cd, or your installed ubuntu

---

### Post by ennoil on 2009-10-31
I was mostly just hoping tat the problems with the live CD would not carry over.

I can't find menu.lst to put the noapic and other options into. There are no other OS's on this machine. Shouldn't menu.lst still exist? Or, should I edit grub.cfg to add them?

Thanks

---

### Post by P4man on 2009-10-31
> **ennoil said:**
> I was mostly just hoping tat the problems with the live CD would not carry over.

I can't find menu.lst to put the noapic and other options into.

Thats right, karmic uses grub2 which no longer has a menu.lst. But try a[dding those parameters from the grub boot menu,]("https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation") its slightly different from grub 1 but the how to still applies. Basically just pay attention to the lines wrapping around the screen in grub 2 whereas grub 1 didnt do that, so basically you have to edit one line higher than you might think, then use right arrow key to go to the end of the line, which is wrapped on the next line. If you dont understand this now, you probably will once you are editing the grub entry.

If it solves the issue, Ill talk you through making those changes permanent in grub 2

Oh and you may have to press escape to view the grub menu...

---

### Post by ennoil on 2009-10-31
I am guessing that would be to edit /etc/default/grub to make sure:
GRUB_CMDLINE_LINUX=""
reads
GRUB_CMDLINE_LINUX="noapic nolapic"
Then run update-grub2.
Forgot that Karmic uses grub2
Explaining to an almost 9 year old how to add kernel parameters at boot time is not something I would look forward to so I am skipping that step and hoping it works (I should have thought of noapic myself but my mind has not been focused the last couple of months). I will not have physical access to the laptop until January and I think that would not make him a happy boy which will make the wife not happy which, in turn, will not make me happy...

---

### Post by P4man on 2009-10-31
> **ennoil said:**
> I am guessing that would be to edit /etc/default/grub to make sure:
GRUB_CMDLINE_LINUX=""
reads
GRUB_CMDLINE_LINUX="noapic nolapic"
Then run update-grub2.
Forgot that Karmic uses grub2
Explaining to an almost 9 year old how to add kernel parameters at boot time is not something I would look forward to so I am skipping that step and hoping it works (I should have thought of noapic myself but my mind has not been focused the last couple of months). I will not have physical access to the laptop until January and I think that would not make him a happy boy which will make the wife not happy which, in turn, will not make me happy...

Ah I see. You have ssh access to the machine or something. 
Im not quite sure what the difference is between
GRUB_CMDLINE_LINUX_DEFAULT
and
GRUB_CMDLINE_LINUX

but other than that you'd be right. noapic and nolapic will not render the machine unbootable, at least Ive never seen that. It may cause a tiny performance hit under certain loads but thats way better than freezing. Assuming it helps, but its worth a try.

---

### Post by choman on 2009-11-01
I have the same issue.  I've tried all the recommended solutions here and none appear to work.  Limited the test to 
the non-DEFAULT GRUB_CMDLINE_LINUX variable. me too, not sure what the difference is.

simple test for me to replicate the issue is to open a terminal and resize the window with the mouse.

My real deal is I have a production laptop D600 that I want to upgrade.  This system is already converted to ext4.

so here's whats weird about this:  

* if I install my test D600 fresh with karmic, I freeze with the above test

* if I install my test D600 fresh with jaunty and migrate to ext4, I freeze with the above text

* if I install my test D600 fresh with jaunty and leave ext3, all seems well.

These test were with pre-final (say alpha 6).  but I am currently running through them again.  It's just time consuming.   Down side is I am on the road starting tomorrow til thursday, so I won't be able to test this week much.

Anyways, I too would like to see a resolution to this issue

---

### Post by kevanj on 2009-11-02
I've run into the same problems on a D600, however running a LiveCD in Safe Graphics Mode works fine....so I checked the xorg.conf file on my installation (upgraded from Jaunty) and modified it to look like the xorg.conf used by the LiveCD by adding the Driver  "vesa" parameter in the "Device" section

My /etc/X11/xorg.conf now looks like this:

```
Section "Device"
    Option "AccelMethod" "XAA"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```This appears to be working, however I am a bit of a n00b with Linux/Ubuntu so I am not really sure what the disadvantages of using a vesa driver is...but if I can provide any info to try to get things working 'properly' let me know...

---

### Post by P4man on 2009-11-02
> **kevanj said:**
> On a D600 running a LiveCD in Safe Graphics Mode works fine....so I checked the xorg.conf file on my installation (upgraded from Jaunty) and modified it to look like the xorg.conf used by the LiveCD.

My /etc/X11/xorg.conf now looks like this:

```
Section "Device"
    Option "AccelMethod" "XAA"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```
This appears to be working, however I am a bit of a n00b with Linux/Ubuntu so I am not really sure what the disadvantages of using a vesa driver is...but if I can provide any info to try to get things working 'properly' let me know...


I think you want to post this in a separate thread..
that said, there is no advantage to using vesa. Vesa is pure and simple an emergency way to get something on your screen, its horribly slow. If the nvidia or ati drivers are not working, post in a new thread.

---

### Post by kevanj on 2009-11-02
Already addressed in [this thread]("http://www.uluga.ubuntuforums.org/showthread.php?t=1305349")....and the solution seems to work.

---

### Post by choman on 2009-11-04
So I tried this xorg.conf idea and it does resolve the issue according to my test case of resizing the terminal window by dragging the mouse.

The interesting thing is that my D600 did not have an xorg.conf.  Then I remembered that this file is going away.  Anyways, I copied exactly what was posted and rebooted my D600 and everything is fine. 

So now we need to get the big boys involved.  I agree with the comment that the vesa drivers blow.  but obviously the ati drivers are not correct in karmic to keep the window manager from freezing.

---

