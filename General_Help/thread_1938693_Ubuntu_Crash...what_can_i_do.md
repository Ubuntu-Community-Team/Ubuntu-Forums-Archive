---
title: "Ubuntu Crash...what can i do?"
date: 2012-03-10
forum: General Help
---

### Post by gg41r on 2012-03-10
Hi all. My unbuntu 11.10 OS has crashed. All i get now is the following screen with the following options...

GNU Grub Version 1.99 l2Ubuntu5

Ubuntu with Linux 3.0.0.0-15 generic
Ubuntu with Linux 3.0.0.0-15 generic (recovery mode)
Previous Linux versions
Memory Test (Memtest86+)
Memory Test (Memtest86+ serial Console 115200)

I have been thro ALL options with no sucsess and I even tried installing ubuntu NUMEROUS times, it gets so far,but it wont install now

Any ideas?

Cheers

---

### Post by gg41r on 2012-03-10
Would i be right in thinking that no one has a clue whats going on?

---

### Post by miasmablk on 2012-03-10
i think you would be correct in assuming nobody knows what you're talking about, could you be more specific as to what happened? error messages, crash after installing a certain package, after removing a certain package?

---

### Post by sudodus on 2012-03-10
Welcome to the Ubuntu Forums :-)

1. Can you run a live session 'testing Ubuntu' from a CD or USB install drive?

2. Have you ever been running Ubuntu as installed from an internal HDD? Or is this your first try?

---

### Post by Topsiho on 2012-03-10
Ubuntu (most versions) runs on a lot of hardware. If it doesn't run on specific hardware, maybe the hardware is at fault. How is the memory, how is your hard disk? Maybe you should try and test these first.

Then, there are minimum specifications for the harware, for Ubuntu to run, or run well. Enough disk space is one of them, and enough working memory (500 MB or more).

Topsiho

---

### Post by gg41r on 2012-03-10
> **miasmablk said:**
> i think you would be correct in assuming nobody knows what you're talking about, could you be more specific as to what happened? error messages, crash after installing a certain package, after removing a certain package?

Thank you for the replies. Any help Much appreciated

Its actually my sons laptop that this happened on. As far as i am aware, he wasnt installing or uninstalling anything. he has been warned about doing this. The screen with the afforementioned message just appeared from nowhere when trying to boot one time. He basically only had Ubuntu installed on the machine and was using google chrome to surf the net and thats pretty much all that was done on the laptop.

I have tried installing Ubuntu again from the disc i installed it from the first time.  It goes for about 2 minutes then the whole process stops.

As for trying to run a live session for "testing ubuntu" from a CD or USB install drive.....well...id be lying if i sed i knew what you meant. Im not really up to speed with all the tech jargon 

Ubuntu was installed about 3-4 weeks ago, and had been working fine till this happened.

---

### Post by sudodus on 2012-03-10
> **gg41r said:**
> ...
I have tried installing Ubuntu again from the disc i installed it from the first time.  It goes for about 2 minutes then the whole process stops.

As for trying to run a live session for "testing ubuntu" from a CD or USB install drive.....well...id be lying if i sed i knew what you meant. Im not really up to speed with all the tech jargon 

Ubuntu was installed about 3-4 weeks ago, and had been working fine till this happened.
Good, now we know more. Ubuntu has been running. But now it does not run, not even install. The first thing I would suggest is to try to use the install CD disk but not install, only run a 'live session'. This is to boot the whole Ubuntu system from that CD to test how it is running, but not try to install it to the hard drive. This is possible with the normal desktop install CD disk. 

But if you have an alternate install disk, you cannot do that, so then I would suggest that you download a new iso file for a desktop version and flavour of Ubuntu and burn a CD disk, so that you can test the computer without installing anything.

It might be a hardware crash, and you can test that trying to get the computer running 'live' from the CD drive.

---

### Post by gg41r on 2012-03-10
> **sudodus said:**
> Good, now we know more. Ubuntu has been running. But now it does not run, not even install. The first thing I would suggest is to try to use the install CD disk but not install, only run a 'live session'. This is to boot the whole Ubuntu system from that CD to test how it is running, but not try to install it to the hard drive. This is possible with the normal desktop install CD disk. 

But if you have an alternate install disk, you cannot do that, so then I would suggest that you download a new iso file for a desktop version and flavour of Ubuntu and burn a CD disk, so that you can test the computer without installing anything.

It might be a hardware crash, and you can test that trying to get the computer running 'live' from the CD drive.

Thanx for the reply.

I did try running ubuntu without installing it....but the same thing happened as when trying to install it....ie: hit a brick wall. Im not pretending to be an expert, but i would have thought if the Disc managed to install Ubuntu a few weeks ago, it should be able to do it now, without the need to re download Ubuntu and burn to disc again? 
Funny you should mention a hardware crash, the laptop suffered the same fate a few weeks ago with Windows 7 OS, thats what lead to me sticking on ubuntu, as no system restore discs were made when the laptop was new....so i had no discs to try and get out of the mess with.

---

### Post by sudodus on 2012-03-10
> **gg41r said:**
> Thanx for the reply.

I did try running ubuntu without installing it....but the same thing happened as when trying to install it....ie: hit a brick wall. Im not pretending to be an expert, but i would have thought if the Disc managed to install Ubuntu a few weeks ago, it should be able to do it now, without the need to re download Ubuntu and burn to disc again? 
Funny you should mention a hardware crash, the laptop suffered the same fate a few weeks ago with Windows 7 OS, thats what lead to me sticking on ubuntu, as no system restore discs were made when the laptop was new....so i had no discs to try and get out of the mess with.
Then we can be rather convinced that there is something wrong with the hardware, something that happened when Windows broke and again when Ubuntu broke. It could be many types of errors. The computer is not dead, since it reaches the grub menu. I suggest that you try

1. the memory test
2. recovery mode (try text mode, try help ..., and later maybe graphics mode)

If these seem to work, it might be something wrong with the graphics. Maybe you can try an external monitor (it might work, depending on where something goes wrong).

---

### Post by gg41r on 2012-03-10
> **sudodus said:**
> Then we can be rather convinced that there is something wrong with the hardware, something that happened when Windows broke and again when Ubuntu broke. It could be many types of errors. The computer is not dead, since it reaches the grub menu. I suggest that you try

1. the memory test
2. recovery mode (try text mode, try help ..., and later maybe graphics mode)

If these seem to work, it might be something wrong with the graphics. Maybe you can try an external monitor (it might work, depending on where something goes wrong).

I ran the memory test option. No faults were found.

I ran the Recovery mode, let it run thro and it just takes me back to the same screen

I had to hook it up my desktop monitor, as a new screen was fitted, which has since packed in too. But it makes no difference

---

### Post by sudodus on 2012-03-10
I think a hardware guy should have a look at your computer.

Or browse the internet and find links like this one
[[COLOR="Red"]_http://club.myce.com/f7/hardware-problems-how-check-75387/_[/COLOR]]("http://club.myce.com/f7/hardware-problems-how-check-75387/")

---

### Post by miasmablk on 2012-03-10
at the grub bootloader menu when you startup your computer if you select previous linux versions are you able to boot into one of your older installations? if so try this.

[http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/](http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/)

---

### Post by gg41r on 2012-03-11
> **miasmablk said:**
> at the grub bootloader menu when you startup your computer if you select previous linux versions are you able to boot into one of your older installations? if so try this.

[http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/](http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/)

hi,

i have no previous versions of linux on the laptop, but did select the option and gave it a go, just incase. But again, just takes me back to the same screen

---

