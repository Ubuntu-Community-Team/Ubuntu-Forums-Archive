---
title: "Can't boot from cd, and have no os"
date: 2012-02-11
forum: General Help
---

### Post by chuning on 2012-02-11
hello - 

slight emergency - today i tried to re-install windows to run alongside ubuntu 11.04 which i use as a matter of course, to do a couple of things that i haven't found a way of doing in ubuntu.  neither my acer recovery discs nor an unused xp disc would work, which a bit of googling indicated was probably something to do with the MBR.  a bit more googling pointed me towards lilo - i followed some instructions, and was then unable to boot into anything.  i tried booting from cds that i already had, and went into a black screen.  tried making a new live cd, same result.

can anyone help?

thank you

chris

---

### Post by 3Miro on 2012-02-11
When a computer boots, it first goes to the MBR and then into a boot-loader and the boot-loader boots an OS. Linux has two boot-loaders, Grub and Lilo. Ubuntu uses Grub (in fact Grub seems overwhelmingly more popular), there is no reason to mess around with Lilo.

You should note that a windows recovery CD would probably erase Ubuntu and anything with it.

A windows install CD will install Windows (assuming you have a free partition), however, windows will overwrite MBR with its own boot-loader. Unlike Linux boot-loaders, Windows can boot only Windows and hence you will lose the ability to boot Ubuntu. However, unless you mess up the partitioning, Ubuntu will still be there. You will simply need to restore Ubuntu's Grub.

If your computer is currently messed up and doesn't boot anything, then you should get an Ubuntu CD and boot from that (select "Try Ubuntu" as opposed to "Install"). Then you need to reinstall Grub 2 to get back to Ubuntu:

[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

Once you have Grub restored, you should get your Ubuntu back. As for installing Windows, I cannot help. Someone else might, if you describe the problems in more detail.

---

### Post by chuning on 2012-02-11
thank you for your swift reply.

i tried going to the 'try' option, but still the same problem, it goes to a black screen.  i know something was going on, because the thumb drive light was flashing (tried that instead of a cd), and i also heard the ubuntu start-up jingle, but the screen is black, so can't do anything

chris

---

### Post by 3Miro on 2012-02-11
> **chuning said:**
> thank you for your swift reply.

i tried going to the 'try' option, but still the same problem, it goes to a black screen.  i know something was going on, because the thumb drive light was flashing (tried that instead of a cd), and i also heard the ubuntu start-up jingle, but the screen is black, so can't do anything

chris

The CD doesn't boot from MBR and it doesn't touch anything on your hard-drive. You should always be able to boot from a liveCD.

Are you using the right version of Ubuntu and are you sure the CD isn't broken? Have you changed your hardware since you last installed Ubuntu? What is your video card? How long did you wait? LiveCD takes considerably longer to boot, maybe as much as 5 minutes on a slow machine.

---

### Post by bluexrider on 2012-02-11
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

This may help [RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=fullsearch&context=180&value=linkto%3A%22RecoveringUbuntuAfterInstallingWindows%22")

---

### Post by chuning on 2012-02-11
hello - 

i'm trying to boot from a just-downloaded 11.10 - i've tried  burning 2 cds, and 2 downloads onto usb stick.  i've left it for longer than 10 minutes each time.  after a few minutes of making the usual booting up noises, it just goes quiet, but the trouble is, each time, after the first bit of purple screen, the display just goes black.  it's a relatively new and fast laptop, i can't tell you what the video card is, because i can't boot into anything (or at least, i can't see anything if it does boot up)

chris

---

### Post by wolfen69 on 2012-02-11
Are you running hybrid graphics? Can you post the specs of the computer?

---

### Post by 3Miro on 2012-02-11
If you originally had 11.04, you should try with the 11.04 CD. You can get it from here:

[http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/)

It is strange that 11.10 doesn't boot, there must be some bug between your hardware and Ubuntu, I wouldn't know about it.

Another thing that you can try is to get Xubuntu. It is virtually identical in terms of booting and Grub, however, the desktop environment requires much lower resources and it is much better for live CD (boots faster and it works better).

[http://cdimage.ubuntu.com/xubuntu/releases/11.04/release/](http://cdimage.ubuntu.com/xubuntu/releases/11.04/release/)

In either case, you want the desktop .iso file for either i386 or amd64 bit, depending on which one you had before. If you had just downloaded the .iso from the Ubuntu main page, you probably have the i386 version.

---

### Post by ajgreeny on 2012-02-11
Try using the various boot options available if you use F6 (I think) when you see the menu which offers "Try ubuntu" and "Install ubuntu".

There are several available ones, but try **nomodeset** first, and if nthat is no good try the others.

---

### Post by chuning on 2012-02-11
Thank you!

I found my way to the install - F6 - nomodoset, and it's now installing

Thanks again

Chris

---

### Post by 3Miro on 2012-02-11
> **chuning said:**
> Thank you!

I found my way to the install - F6 - nomodoset, and it's now installing

Thanks again

Chris

Are you installing Ubuntu or the boot loader?

If you want to reinstall Ubuntu, that's fine, but installing Ubuntu after you install windows is usually easier. If you are just going to make a new install, then install windows first.

Also, you can always use a liveCD to backup files from a broken computer.

---

### Post by chuning on 2012-02-11
i was trying to re-install ubuntu.  however, it installed apparently ok, but then when i had to restart, it went straight to the black screen.  i could hear the startup sounds etc., but just black screen. so back to square one

---

### Post by chuning on 2012-02-11
and i've just tried installing windows, and it won't let me

---

### Post by 3Miro on 2012-02-11
Maybe Ubuntu needs nomodset to boot from the HDD as well. After installing Ubuntu, you should get two options (hold shift while booting if you don't see the options). You should be able to boot in recovery mod and then run all of the updates. This will hopefully fix the issue, if not, here is how to set nomodset permanently:

[http://ubuntuforums.org/showthread.php?t=1761252](http://ubuntuforums.org/showthread.php?t=1761252)

I don't know about windows. There is nothing in Ubuntu that can in any way prevent you from doing a clean install of Windows on your machine.

---

