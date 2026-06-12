---
title: "Video problem preventing ANY access to gnome and flashing slow command prompt"
date: 2009-11-12
forum: General Help
---

### Post by Irishpolyglot on 2009-11-12
What a frustratIng upgrade :( After some tweaks, I solved sound etc. problems but now nothing is working!
I've been in Karmic since it was released, with some boot up issues, but since the last time I tried to reboot I haven't been able to access the GUI. I'm writing this on my iPhone :'(

When I boot up, I see the Dell screen, then the grub message and then the white Ubuntu logo. When it was working before there was a bar animation or something under the white logo, but this is no longer true and it's just still. After a few seconds all I see is the command line FLASHING for me to log in. It's hard to do this because the flashing is slowing the computer down somehow and it only registers letters if I hold them down or press them at the right time.
Every second time, I see the following above the log in (flashing with everything else):
> Warning: 2.6.31+ kernel detected. Most likely the harware performance counter framework which can generate NMIs is active. You have to prevent the usage of hardware performance counters by 
echo 2 > /proc/sys/kernel/perf_counter_paranoid
(This is spread over several lines)


If I select recovery mode from grub and then 'resume normal boot' the annoying flashing isn't there (I still see the NMIs is active message) and I can log in by the command line. Is it possible to activate gnome from here? If not, then what should I do?? 
This may have something to do with my nvidia driver that has caused me problems in the past, although I've installed the latest stable one (190) and rebooted the comp since then without this problem. Also, before the reboot the computer started being randomly slow.
I am on a Dell XPS M1730.
Thanks for any help!!

---

### Post by Irishpolyglot on 2009-11-12
no ideas? I've been trying to get simple GUI abilities from the command line in recovery mode with no joy. The outputs from that may be useful in solving the problem: [http://ubuntuforums.org/showthread.php?t=1324438]("http://ubuntuforums.org/showthread.php?t=1324438")

---

### Post by Giblet5 on 2009-11-12
Did you install a custom kernel?

If so, use the grub menu to select the previous kernel and remove the custom one.

If not, then boot into a recovery shell and look at /var/log/Xorg.0.log and see if you can find out why X is dying at boot time (hosed xorg.conf maybe, missing driver maybe).

Did you powerfail?

---

### Post by Irishpolyglot on 2009-11-13
Thanks for your reply. I didn't install a custom kernel; just the one from 9.04 and the new one from 9.10. I tried to access 9.04 from grub but it doesn't even make it to the command line and stops half way through checks.

There was no power fail.

As I say in the parallel thread, I tried just starting over with a fresh installation (of 9.04, since I only have that CD at the moment). I can't run xfix!! I did some searching and others are having the same issue in Karmic - there is no longer an xfix option for some people. A bug has already been filed.

In the mean time I definitely need to scan and fix my hard drive. I dug out my old 9.04 installation CD and was reinstalling it, and in the last stage of installation it said that there was a problem with the CD or hard drive. I tried another CD (always have two... haven't burned 9.10 yet, not sure if that would make any difference) and it did the same thing. When I selected "scan disk for errors" option on the boot up CD list, it confirmed that there was an error.

That's all great, but how do I get rid of it?? xfix no longer exists and when I tried fsck it very sharply says "WARNING!!! Running e2fsck on a mounted filesystem may cause SEVERE filesystem damage" so I select no. How can I run this without mounting the filesystem?

What I really need to do now is run xfix or fsck with error correction enabled. How can I do this? I am accessing the system fine through my boot up CD. It seems that whatever this error is, it is what is causing the problem. Thanks for any tips!!

---

### Post by Giblet5 on 2009-11-13
Ah.

The xfix option isn't required.

Boot into recovery mode shell. Enter the following command.

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.091113
```

(You just ran xfix...)

Now, exit the shell and continue the normal boot.

Did this fix the problem?

---

### Post by Irishpolyglot on 2009-11-13
haha thanks so much!! :D :D I was so worried that I would have to format my comp or that there may be a hardware issue. I'm back in Ubuntu now!! The nvidia drivers have been disabled - I think I'm going to install 32 bit Ubuntu and use that instead of 64 bit; there are too many problems in 64 bit (flash etc.) and I think the drivers issue is one of them.
Is it a simple case of just installing the 32 bit from the CD, or do I have to play around with any libraries etc.?
Thanks again for your help!! You are my hero :D

---

### Post by Giblet5 on 2009-11-13
> **Irishpolyglot said:**
> haha thanks so much!! :D :D I was so worried that I would have to format my comp or that there may be a hardware issue. I'm back in Ubuntu now!! The nvidia drivers have been disabled - I think I'm going to install 32 bit Ubuntu and use that instead of 64 bit; there are too many problems in 64 bit (flash etc.) and I think the drivers issue is one of them.
Is it a simple case of just installing the 32 bit from the CD, or do I have to play around with any libraries etc.?
Thanks again for your help!! You are my hero :D

I can fix your flash problem too... But if you really want 32-bit, go for it.

---

### Post by Irishpolyglot on 2009-11-18
There is no escaping the issues that I'm getting!! I got back into the system and used it with no drivers enabled for a few days. I finally decide that pixelly movies is not good enough and in the hardware drivers, I selected the latest nvidia driver 190 that was working for me previously and "Activate" and get this error:
> SystemError: E:Unable to correct problems, you have held broken packages.
I ran both ```
sudo apt-get install -f
```
and
```
sudo dpkg --configure -a
```
But this doesn't help.

Oddly enough, flash is working fine now.

---

### Post by Irishpolyglot on 2009-11-21
Final problem solved [on this thread]("http://ubuntuforums.org/showthread.php?t=1331701")

---

