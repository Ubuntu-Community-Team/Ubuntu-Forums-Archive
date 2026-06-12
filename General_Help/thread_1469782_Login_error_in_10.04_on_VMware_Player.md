---
title: "Login error in 10.04 on VMware Player"
date: 2010-05-02
forum: General Help
---

### Post by multimolti2 on 2010-05-02
Hi!

I downloaded and installed Ubuntu 10.04 on VMware Player today. Installation was fine (and really nice, congrats developers!), although there seemed to be a problem with the VMware tools (at first startup, I got some random error), but this shouldn't be the topic here.

I went away for a few hours, came back and Ubuntu locked itself. Then I tried to "unlock" it by entering the password and pressing enter, but nothing happened. Pressing unlock told me that the password is incorrect. One thing I noticed is that no stars * or black circles appeared when I was typing, but I thought that's normal like in the Linux shell.

Or is there some problem with my keyboard? At least I couldn't log in which sucks quite a lot.

One more question: Is there any possibility to permanently disable the password? I know that nobody will ever use my ubuntu, so where's the sense in creating a password I may forget or that won't be accepted?

Thanks!

---

### Post by multimolti2 on 2010-05-03
I updated VMware Player and still have the same problem. This is the error I get when starting up Ubuntu:

> Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10706000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

---

### Post by P4man on 2010-05-03
some googling suggests you try this:

```
sudo aptitude reinstall xkb-data
```

But are you sure there is no problem either with the iso you used to install ubuntu (did you run an md5 check?) or your vm setup? I dont know vmware or vmplayer (I use virtualbox) but these are rather weird errors to get.

As for the password thing. You can enable login without password in system > administration > login screen. You can set a blank password on the keyring and google around to find how to disable password prompts for specific apps (like adding programs).

But no, afaik you can not just have no password. Then again if you forget your password, its rather trivial to reset it. And it seems like a rather poor solution to work around the problem of having a non working keyboard. I do suspect you need the keyboard for more than just entering passwords :)

---

### Post by multimolti2 on 2010-05-03
Thanks for your reply!

I did some testing now and installed Ubuntu again, this time without the VMware Tools. This time I can't even log in because I can't type my password, so I don't know whether there is this error again.
So it seems to be a problem between Ubuntu, VMware and my keyboard. The weird thing is that once I start typing letters, the cursor in the password input field will stop blinking, as it usually does. But I still see no letters (or stars).
Any suggestions? I can download a new iso image if you think it would help, I used this one so far: [http://isohunt.com/torrent_details/184616109/ubuntu+10.04?tab=summary](http://isohunt.com/torrent_details/184616109/ubuntu+10.04?tab=summary)
(using torrent and not the official download links because they are too slow and can't continue).

---

### Post by P4man on 2010-05-03
wouldnt hurt to run an md5 checksum:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

although I dont think thats the problem. Think its more related to this:
[http://communities.vmware.com/message/1508704#1508704](http://communities.vmware.com/message/1508704#1508704)

Have you tried virtualbox yet? Its pretty awesome and free :)

---

### Post by multimolti2 on 2010-05-03
Yeah, I also use VirtualBox sometimes but prefer VMware due to its support for 3D graphics (VirtualBox can do it as well, but the performance is far worse).

I will try to install it in VirtualBox now.

EDIT:
The keyboard is working in VirtualBox, but as I thought the graphics acceleration sucks. I can't even increase the screen resolution, only 800x600 and 640x480 is possible. Installing the tools didn't help either, after a restart I just got a crash telling me that something is wrong with the graphics configuration and it suggested to run in some safe mode.

---

### Post by kaplaa on 2010-05-05
I have the same problem after upgrading Ubuntu in a VMWare virtual machine running on VMWare Player Vista 64 bit.  This is clearly a bug.  There is a workaround, however.  You can use the on screen keyboard to enter your password.  Once in, you can type normally -- as I am doing now.

---

### Post by P4man on 2010-05-06
> **multimolti2 said:**
> Yeah, I also use VirtualBox sometimes but prefer VMware due to its support for 3D graphics (VirtualBox can do it as well, but the performance is far worse).

I will try to install it in VirtualBox now.

EDIT:
The keyboard is working in VirtualBox, but as I thought the graphics acceleration sucks. I can't even increase the screen resolution, only 800x600 and 640x480 is possible. Installing the tools didn't help either, after a restart I just got a crash telling me that something is wrong with the graphics configuration and it suggested to run in some safe mode.

Installing the tools? You mean the guest additions? Thats what you need for better graphics and resolutions. Works fine here..?

Anyway did you see the second link I gave?
[http://communities.vmware.com/message/1508704#1508704](http://communities.vmware.com/message/1508704#1508704)

---

### Post by dcstar on 2010-05-06
This issue has already been address in the Virualization forum, (where all VM issues should be) and a simple search there would have provided an answer to the OP in a few minutes.

---

### Post by multimolti2 on 2010-05-06
> **dcstar said:**
> This issue has already been address in the Virualization forum, (where all VM issues should be) and a simple search there would have provided an answer to the OP in a few minutes.

Well, I wasn't sure whether its a problem from VMware or from Ubuntu, that's why I posted it here.

---

### Post by dcstar on 2010-05-07
> **multimolti2 said:**
> Well, I wasn't sure whether its a problem from VMware or from Ubuntu, that's why I posted it here.

So the Ubuntu Virtualization forum's existing questions don't make that forum's purpose clear?

---

### Post by multimolti2 on 2010-05-07
> **dcstar said:**
> So the Ubuntu Virtualization forum's existing questions don't make that forum's purpose clear?

What's the matter with you? E.g. when your computer just crashes all the time and you don't know whether its a software or hardware related problem, where would you post it? In a hardware or software forum? Or in both? Or would you go on and mob other people for posting in the wrong section because they DIDN'T know what the problem was related to?

---

### Post by P4man on 2010-05-07
dcstar probably meant you should have looked (and if needed, posted) in the ubuntu virtualization subforum here:
[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

---

### Post by multimolti2 on 2010-05-07
Yeah, he told me that before.

> **dcstar said:**
> This issue has already been address in the Virualization forum, (where all VM issues should be) and a simple search there would have provided an answer to the OP in a few minutes.

---

