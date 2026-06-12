---
title: "Ubuntu will not start - freez at splash screen"
date: 2010-02-04
forum: General Help
---

### Post by abh83 on 2010-02-04
Something happened last night after I installed banshee (I think). I can no longer login to Ubuntu 9.10.

When I start up my laptop and after the grub, Ubuntu freezes at the brown spotlight wallpaper right after the Ubuntu splash screen.

Usually, after the splash screen I have to login with my password but before that comes up Ubuntu freezes.

I've updated to Ubuntu 9.10 since it first came out without any issues until now.

Help is greatly appreciated!

---

### Post by abh83 on 2010-02-04
It might be the gdm which is broken.

I went into recovery mode to fix dpkg and xserver but that didn't help!

Is it possible to fix the gdm or reinstall it?

Anything else I should try?

THX

---

### Post by abh83 on 2010-02-08
*bump*

---

### Post by poet_imp on 2010-02-08
Not a solution to the problem but try this:

- Press "ESC" during grub boot to get the grub menu
- cursor to the vmlinux... line and press "e" to edit
- Remove the "splash" keyword at the end of the line
- Press "b" to boot

If that bypasses the problem you can edit your grub configuration to remove the splash permanenetly.

---

### Post by eaglemystic69 on 2010-02-08
Well I have had a similar issue this past week . . . likely after some app/repo additions.  I found this Howto helpful 
[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)

The advice allows me to access my desktop, though the issue repeats during each reboot, and wake up from sleep mode.  

I even reinstalled grub, then upgraded to grub2 through synaptic.  Still no success for a smooth boot, but the best part is I can still access and work on docs and apps until resolved.

---

### Post by abh83 on 2010-02-12
I tried reinstalling twice last night as I did not want to go through the headache of fixing the problem. However, I was quite surprised to see the issue reoccur on a fresh clean install.

As soon as I'm done installing ubuntu and after the first restart, it will crash right before loading the gdm.

I'm quite surprised as I've had ubuntu since the dapper days and I've even had 9.10 since it was first released.

Could it have anything to do with the fact that I'm dual booting with Win7 in x64 and Ubuntu 9.10 in x32?

Thx

---

### Post by abh83 on 2010-02-12
Okay, so I reinstalled Ubuntu 9.10, only this time I went for the x64 version.

It turns out gdm loads eventually! It just takes a very long time. Could this have anything to do with linux-swap, the boot sectors or my nvidia graphics card?

I'm dual booting with Win 7 x64.

sda:

sda1: linux swap
sda2: ntfs win 7 x64
sda3: ext 4 ubuntu 9.10 x64

Also, starting application like gimp or power management (from the preferences menu) need a very long time to load. 

NOTE: Screenshots attached. It takes about 2-5mins just for the gdm to load fully (meaning to the point where I enter my password to login)

Like I mentioned earlier, this issue just suddenly occurred (either via updates or when installing banshee). But for some reason it's also happening on a fresh install of Ubuntu.

Help is greatly appreciated!

---

### Post by eaglemystic69 on 2010-02-12
From what I have read in other threads, this is a persistant issue for Karmic (amoungst other challenges. . . funny karma huh?).  My HPG71 laptop is a dual boot with Windows7 too.

Im no code tech though I have spent many hours doing recommended terminal fixes with limited success (reinstall from LiveCD, adding wubilr to C drive, editing the grub at boot "e", etc.  The problem seems to be intermittant and progressive in my case.  Now I cannot use the Ubuntu OS, although I can access everything via W7 and live CD when needed.  I prefer a well tuned Ubu either way.

I was ready to do a reinstall on my OS partition until I saw your post with the issue reoccurring.  So I will be patient . . . and let you, though this thread know of any success.

---

### Post by abh83 on 2010-02-12
What confuses me most is why it's happening after a fresh clean install?

IMO something must have happened in Windows 7. I'm wondering if maybe running disk clean up in windows might have done something to the boot sectors?

---

### Post by eaglemystic69 on 2010-02-14
Any luck?

If not, I'ld go back to 9.04 which works well and is still supported (I'ld rather not loose all the custom apps Ive loaded.  I am reminded to stay behind the "newest version" and let the brave geeks battle with the bugs.

I can reach my desktop using this 1-9 process:
[https://help.ubuntu.com/community/Grub2#Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Rescue%20Mode)

---

### Post by sandyd on 2010-02-14
> **abh83 said:**
> Okay, so I reinstalled Ubuntu 9.10, only this time I went for the x64 version.

It turns out gdm loads eventually! It just takes a very long time. Could this have anything to do with linux-swap, the boot sectors or my nvidia graphics card?

I'm dual booting with Win 7 x64.

sda:

sda1: linux swap
sda2: ntfs win 7 x64
sda3: ext 4 ubuntu 9.10 x64

Also, starting application like gimp or power management (from the preferences menu) need a very long time to load. 

NOTE: Screenshots attached. It takes about 2-5mins just for the gdm to load fully (meaning to the point where I enter my password to login)

Like I mentioned earlier, this issue just suddenly occurred (either via updates or when installing banshee). But for some reason it's also happening on a fresh install of Ubuntu.

Help is greatly appreciated!

does it boot faster if you flip to a virtual terminal, login, and type in
```

sudo killall gdm-binary
sudo startx

```This bypasses GDM. you can also do this in recovery mode (select resume)

---

### Post by eaglemystic69 on 2010-02-14
Hmmm, you probably want to read this site info.  My ubu partition also acts as my swap cause I have lots of room to give it a 30gig space.  After days and reinstalls, this process worked well for me until this Karmic glitch many people are having issue with.

[http://lifehacker.com/search/window7%20ubuntu%20dual%20boot/](http://lifehacker.com/search/window7%20ubuntu%20dual%20boot/)

Also, I tend to be conservative with adding x64 apps and OS.  I think it adds an extra system load.  My HPG71 is good and humble, so I allow it to blaze at 32bit instead of bogging at 64bit . . . as you seem to be experiencing.

---

### Post by abh83 on 2010-02-21
Where are the boot logs stored?

I've reformatted and reinstalled several time (x64 & x32) but the problem persists.

Recap:

1) After splash-screen (white ubuntu logo) I am presented with a blank gdm screen for about 1-2 minutes.

2) Then the box appears where I select my user account and type in my password.

3) Desktop needs another 1-2 minutes to load.

4) notification applet in the top right gnome panel needs another 1 minute to load.

5) applications like power manager or update manager are slow and sluggish an need about 1-2 minutes to load too.

---

### Post by abh83 on 2010-02-21
> **carlee said:**
> does it boot faster if you flip to a virtual terminal, login, and type in
```

sudo killall gdm
sudo startx

```
This bypasses GDM. you can also do this in recovery mode (select resume)

After the spalsh screen (white ubuntu logo) when I hit ctrl + alt +f1 to get to tty1 I can login without any issue and it seem quick and responsive. when I hit ctrl + alt + f7 I am back to the blank gdm screen waiting for it to load.

The weird thing is, when I'm in tty1 and i sudo killall gdm, it give me the following message: gdm is not running.

?

---

### Post by abh83 on 2010-02-21
I just noticed that i installed ubuntu without the battery attached to my laptop. Furthermore, the battery tab seems to be missing in power manager.

I usually never take out my laptop battery. Could this be the issue?

---

### Post by eaglemystic69 on 2010-02-21
Hi ABH83,

Do you have 9.04 Jaunty? I tell ya, Karmic is the buggiest OS version Ive used in two years.  I reinstalled it on a compaq and the "bad blocks" error never returned.  Sound is more stable.  Video quality is better for many.  Im ready to go do this with my HPG71 if stupid stuff keep happening.  As I mentioned b4, hold off from an upgrade when they first come out, they are buggy for usually 3 months.  

Ive done my far share of reading threads and doing this and that on a number of issues.  Because you are already at the reinstall stage several times now, just forget karmic, and stay with stable Jaunty maybe x32 instead of x64, unless you need it for some major graphics, etc.  

Latest is rarely the greatest.

---

### Post by abh83 on 2010-02-21
Hey Eagle!

I think that's what I'll do. I just hate it when there's a problem I can't fix. I've had several issues with ubuntu in previous releases but nothing I couldn't solve.

> **eaglemystic69 said:**
> Hi ABH83,

Do you have 9.04 Jaunty? I tell ya, Karmic is the buggiest OS version Ive used in two years.  I reinstalled it on a compaq and the "bad blocks" error never returned.  Sound is more stable.  Video quality is better for many.  Im ready to go do this with my HPG71 if stupid stuff keep happening.  As I mentioned b4, hold off from an upgrade when they first come out, they are buggy for usually 3 months.  

Ive done my far share of reading threads and doing this and that on a number of issues.  Because you are already at the reinstall stage several times now, just forget karmic, and stay with stable Jaunty maybe x32 instead of x64, unless you need it for some major graphics, etc.  

Latest is rarely the greatest.

---

### Post by eaglemystic69 on 2010-02-22
Yup, surrendering to the obvious may be best here.  I truly hope it solves the issue.  I know the determination and challenges to attempt fixing things in the terminal . . . Im a Apple convert and prefer a GUI over a terminal any day.  My eyes get cross-eyed in code-land.  All in all Im happier with Ubuntu than Windows and OSX.  Funny enough, what I save in money sometimes it used in figuring out bugs in new upgrades.  

Lay it out best as possible.  This tutorial is clear and simple.  
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)


[]("http://lifehacker.com/search/window7%20ubuntu%20dual%20boot/")

---

### Post by abh83 on 2010-03-03
any updates here?

---

### Post by sandyd on 2010-03-03
> **abh83 said:**
> After the spalsh screen (white ubuntu logo) when I hit ctrl + alt +f1 to get to tty1 I can login without any issue and it seem quick and responsive. when I hit ctrl + alt + f7 I am back to the blank gdm screen waiting for it to load.

The weird thing is, when I'm in tty1 and i sudo killall gdm, it give me the following message: gdm is not running.

?
forgot that it has been renamed to **gdm-binary.** Post fixed.

---

