---
title: "Xubuntu 11.10 won't get past GRUB after 2-3 boots"
date: 2011-11-29
forum: General Help
---

### Post by sideshowme on 2011-11-29
This is a strange problem.  I installed Xubuntu 11.10 from CD onto a laptop partition (dual-booting with WinXP), and everything seemed to be fine.  However, after shutting down the machine and restarting a couple of times, the system now does not get very far beyond GRUB.  I am generally faced with either a black screen, or a blinking cursor, or a few lines of text (usually something different each time).

The first time this happened, I put the CD back in again and performed an 'upgrade' from 11.10 to 11.10 as the only way possibly to preserve the programs I'd spent a good few hours setting up.  This seemed to work, and I spent another few hours using the system, and installing more of the programs I need.

Then today, once again after 2-3 shutdown-restart cycles, I am back to the same point: from GRUB I get a blank screen, or a blinking cursor, or a few lines of text.  Recovery mode does not provide any help, and getting to a desktop is impossible.

I'm fairly confident that Xubuntu was not designed with the need to reinstall every two days in mind, so can anyone offer any help please?

---

### Post by cottfcfan on 2011-11-29
The only thing I can suggest as a temporary measure is boot back into the live CD, open a terminal then:
```
sudo mount /dev/sdaX /mnt
```
then:
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```
Change X in sdaX to the partion your Xubuntu is installed on.
eg sda1. This will also install grub into the MBR, not to a partition.
That should get you back into your system, why it keeps failing though I don't know.

---

### Post by sideshowme on 2011-11-29
thanks for the reply.  as far as i remember, GRUB is already on the MBR.  when i switch on i get to see GRUB, have the choice of XP or Xubuntu (or recovery mode) but the only option from within GRUB that gets anywhere is XP, which boots perfectly (I'm using it now).  the linux options stop with a few seconds of the xubuntu splash screen followed by a blank scree/flashing cursor/few lines of text (never the same thing).

---

### Post by sideshowme on 2011-11-30
well, another day, another reinstall.  this time i managed to install, shut down from the live CD, boot up, shut down, boot up, standby, resume and then shut down.  now i'm back to the black screen.  

the xubuntu installation lasted approximately 4 hours of use.

earlier today, a colleague was commenting disparagingly about how he has to reinstall MS Windows every six months or so.  i had to laugh.

---

### Post by sideshowme on 2011-12-13
does anyone have any suggestions about this yet?  it's bewildering.  i really want to use xubuntu, it seems a very sensibly laid out operating system, and it's the only one i've tried that gets wireless working on this laptop.  but i can't possibly reinstall every 4 hours, so i'm calling out for help and advice from the famed ubuntu community.

anyone?  please?

---

### Post by cottfcfan on 2011-12-14
Never seen anything like this. A fresh install usually either boots or it doesn't.
Something must be triggering it.
Are you fully updating after the install?
Is it only after updating the kernel it happens?
Are you booting back into windows at all?
Does it happen after you've used XP?
Please give us some more info to work with.

---

### Post by sideshowme on 2011-12-17
> **cottfcfan said:**
> Never seen anything like this. A fresh install usually either boots or it doesn't.
Something must be triggering it.
Are you fully updating after the install?
Is it only after updating the kernel it happens?
Are you booting back into windows at all?
Does it happen after you've used XP?
Please give us some more info to work with.

thanks for the reply.  in response to your questions:

i always allow the install updates when i first setup and connect to the net.  however after that i can usually reboot fine a couple of times before it goes wrong.  i must admit it hadn't occurred to me to try not installing the updates.

i'm not sure about updating the kernel.  how would i check?

i have booted into windows on occasion, but on at least one of the installs i was solely booting into linux while i was trying to get some work done (i had to reinstall xubuntu about four times in three days or something just to have the chance to get the work done).  as it happens when i do boot into windows as well as when i don't, i don't think it's connected to that.

any advice much appreciated.  i will try reinstalling again when i get a minute, and this time not installing the updates presented by update manager to see if that makes a difference.

thanks!

---

### Post by cottfcfan on 2011-12-17
First thing to try is the kernel.
If you've fully updated you will be booting into the 3.0.0-14 kernel.
Try booting into the original which I think is 3.0.0-12.
When you get to the grub screen, go to, (other Linux Kernels) or something like that its just below the one you're booting into. And choose the 3.0.0-12 kernel.
See if that helps.

---

### Post by koepked on 2011-12-20
I have exactly the same problem. I tried using the 3.0.0-12 kernel as cottfcfan suggested, but I still got the same. A couple notes:

I don't have to reinstall to get it to boot again. If I boot into recovery mode from grub, drop to root prompt, exit, then select remount from the recovery menu, it hangs, but if I hit Ctrl+C it presses on and boots. When I log in, graphics are fairly hosed, but I can open a terminal and shutdown -r, after which everything boots fine.

I've looked through syslog and dmesg, but nothing has jumped out at me. Are there other logs I should look at? 

These may or may not matter, but they are more or less abnormal things I'm doing which may be helpful:
- I have nfs mounts
- I'm running bind9 as a caching server
- I have dual monitors setup
- I'm running compiz, emerald, and cairo-dock in my desktop. They are all started after lightdm login.

I just switched to Xubuntu from arch. Prior to this issue I had been very excited about it, and badly want it to work!

---

### Post by koepked on 2011-12-20
After some more digging, this is what I've found:

If i reboot from the desktop, I have the same issue as sideshowme. If I shutdown instead, everything works as it should. After a reboot, I edited my grub entry from the grub menu and removed *quiet splash* so I could watch the boot. It hangs at *Checking battery state*.

I'm on a desktop, so there is no battery, and maybe it doesn't handle that properly, idk.

sideshowme, if you try these, do you get the same? If not, I think I'll start a new thread so you don't get hijacked. If so, I'll keep on posting here what I can find.

---

