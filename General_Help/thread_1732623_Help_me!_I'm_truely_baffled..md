---
title: "Help me! I'm truely baffled."
date: 2011-04-18
forum: General Help
---

### Post by AaronDaycentChild on 2011-04-18
Hello.. Excuse me, I'm new here.

I have a problem with my computer. I'm running "Ubuntu 10.10" and have been running it for about a month now without any problems, until now.

The problem started yesterday. I left my laptop on stand-by and I left the house for a while. I came back and my laptop was out of power. I connected the power cable and started it up again, but instead of my computer booting up normally I got this other thing on my screen. 

(This is what shows up when I start the computer)
[IMG]http://img25.imageshack.us/img25/7750/dscf3743f.jpg[/IMG] 

Then, when I click the highlighted option, it gives me this...
 [IMG]http://img845.imageshack.us/img845/4895/dscf3744.jpg[/IMG]

I really don't know what to do... Can someone please help?

---

### Post by Spyderkid on 2011-04-18
try the second non-recovery mode one.

if that doesn't work try recovery mode second down.

google some of the key phrases from the pictures you've taken to find out if other peoploe have had the same problem.




If in doubt Google it!

---

### Post by TBABill on 2011-04-18
Looks like you received a kernel update, which is why it pushes you to the Grub screen. It offers you the chance to select either kernel or safe mode or Windows. Can you boot into the older kernel? Or is Grub not getting you to a desktop with either? If you cannot, it's possible you just need to boot from the liveCD and reinstall Grub.

---

### Post by nothingspecial on 2011-04-18
I would suggest booting a live cd and trying to mount the drive from that.

If that doesn't work you will have to run e2fsck on it, but see if you can get at it from the live cd first.

---

### Post by 3Miro on 2011-04-18
There is a problem with Grub and the HDD. Grub is unable to mount your HDD.

Boot from a LiveCD and check to see if you can properly mount your hard drive partitions form it (particularly the root partition).

---

### Post by WorMzy on 2011-04-18
> **TBABill said:**
> Looks like you received a kernel update, which is why it pushes you to the Grub screen. It offers you the chance to select either kernel or safe mode or Windows. Can you boot into the older kernel? Or is Grub not getting you to a desktop with either? _If you cannot, it's possible you just need to boot from the liveCD and reinstall Grub._

The screenshots show that grub is working fine. Reinstalling it won't make any difference.

OP: you need to boot a LiveCD and run fsck on your root partition. You're getting the second screen because your filesystem is partially corrupted, probably due to the unclean shutdown caused by the battery dying.

Simply boot the LiveCD (or LiveUSB), and run
```
sudo fsck /dev/sda1
```

(Assuming your root partition is sda1)

---

### Post by AaronDaycentChild on 2011-04-18
> **WorMzy said:**
> The screenshots show that grub is working fine. Reinstalling it won't make any difference.

OP: you need to boot a LiveCD and run fsck on your root partition. You're getting the second screen because your filesystem is partially corrupted, probably due to the unclean shutdown caused by the battery dying.

Simply boot the LiveCD (or LiveUSB), and run
```
sudo fsck /dev/sda1
```(Assuming your root partition is sda1)

Awesome, thank you, that has helped me! :KS

So I have now got the live CD in my computer and I'm going through the installation proccess (I hope I'm correct in doing that). I'm just wondering where do I run "sudo fsck /dev/sda1"?

---

### Post by nothingspecial on 2011-04-18
> **AaronDaycentChild said:**
> 

So I have now got the live CD in my computer and I'm going through the installation proccess (I hope I'm correct in doing that). 

If you are reinstalling your system will be fixed but you will loose all your saved data.

I meant for you to boot from the live cd not reinstall Ubuntu.

---

### Post by WorMzy on 2011-04-18
Yes, there's no need to reinstall your system, you just need to run that command in a terminal (Applications -> Accessories -> Terminal).

---

### Post by AaronDaycentChild on 2011-04-18
> **nothingspecial said:**
> If you are reinstalling your system will be fixed but you will loose all your saved data.

I meant for you to boot from the live cd not reinstall Ubuntu.

Oh.. Right. lol

So then you go into the terminal and then type "sudo fsck /dev/sda1"?

---

### Post by nothingspecial on 2011-04-18
If /dev/sda1 is the right partition, what does it say if you type ```
sudo fdisk -l
```

---

### Post by AaronDaycentChild on 2011-04-18
> **WorMzy said:**
> Yes, there's no need to reinstall your system, you just need to run that command in a terminal (Applications -> Accessories -> Terminal).

Okay, all the problems have been solved.

Thank you for your help, I am very very greatful. :-)

---

### Post by AaronDaycentChild on 2011-04-18
> **nothingspecial said:**
> If /dev/sda1 is the right partition, what does it say if you type ```
sudo fdisk -l
```

Don't worry man, all my problems have been solved.

Really, thank you for your help! I could have never gotten this kind of help if I was still using a Windows OS.

---

