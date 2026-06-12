---
title: "Acer Aspire One freezes on Kubuntu 12.04 boot"
date: 2012-08-23
forum: General Help
---

### Post by jesuisbenjamin on 2012-08-23
Issue also posted [on Launchpad]("https://bugs.launchpad.net/ubuntu/+bug/1039888").

According to the X Freeze Troubleshooting documentation "It's best to file a new bug report rather than joining onto someone else's", so here it goes:

I have installed Kubuntu 12.04 from USB on an Acer Aspire One. After installation, the computer freezes on boot after logging in the user.

The CD and USB are still with me, however at this moment the computer is remote (I installed it for someone who had to leave, please mind this while answering, as I will have to guide this person remotely, who knows little about operating systems etc.).

Since the computer is remote, I have not the possibility right now to "Reproduce the freeze, and with your system frozen ssh into it (over ethernet) and collect:
 * dmesg > dmesg.txt
 * /var/log/Xorg.0.log
 * /sys/kernel/debug/dri/0/i915_error_state [Intel graphics only]

Would you please instruct me on "ssh"-ing into the frozen system?

Q: Have I experienced just one lockup, or have you had a series of these lockups?
A: I have experienced a series of lockups.

Q: If you've had several, how often does it occur? Every few hours? Once or twice a day? Couple times a week?
A: At every single boot after logging in.

Q: When did you first notice it?
A: Right after installation.

Q: Under what conditions does it seem most likely to reproduce?
A: Only at boot time, I cannot pass the splash screen.

Do you need more information? Please help, I've messed up my friend's computer trying to promote Ubuntu. I hope I can fix this rapidly so this person can go back to work.

PS: thanks for all your work on Ubuntu / Kubuntu!

---

### Post by 2F4U on 2012-08-23
Can the person boot another Linux liveCD (not Kubuntu) to see if it is a problem with Kubuntu? If that is possible, can you have him run memtest from a liveCD to verify that the RAM is ok?

---

### Post by jesuisbenjamin on 2012-08-23
Acer Aspire One has no CD-drive. Can it be done with a USB?

---

### Post by mastablasta on 2012-08-23
> **jesuisbenjamin said:**
> Acer Aspire One has no CD-drive. Can it be done with a USB?
 
sure, USB is even better.
 
also on splash screen if you press esc it should throw you to command line (or at least it did). maybe you can notice where it stops.

---

### Post by jesuisbenjamin on 2012-08-23
> **mastablasta said:**
>  
also on splash screen if you press esc it should throw you to command line (or at least it did). maybe you can notice where it stops.

The user could not get command line with Esc, but the OS went beyond the splash screen few times, and froze once on the desktop. Is that a clue?

---

### Post by jesuisbenjamin on 2012-08-23
.

---

### Post by jesuisbenjamin on 2012-08-23
I realise now that Kubuntu was running fine after installation, and that it is only after the first re-boot that the freeze occured. I don't know if that can tells anything about the cause.

---

### Post by LewisTM on 2012-08-23
What model of Aspire One?
If it's the 522/722 model, you need to set the first boot device in BIOS to be Network boot (and have no wired connection at boot). The ethernet driver creates problems and lockups.
See this thread
[http://ubuntuforums.org/showthread.php?t=1811178](http://ubuntuforums.org/showthread.php?t=1811178)

Cheers!

---

### Post by cortman on 2012-08-23
> **LewisTM said:**
> 
If it's the 522/722 model, you need to set the first boot device in BIOS to be Network boot (and have not wired connection at boot). 

This. I tore my hair out for over a week with this problem- what a relief to find it was this simple.

---

### Post by jesuisbenjamin on 2012-08-25
Yes it worked! :)

I had read something about it before and I had tried to disable completely the network boot, but that didn't help at all.

---

