---
title: "Monitor goes into permanent sleep upon boot"
date: 2010-05-23
forum: General Help
---

### Post by xXSVx Phantom XS on 2010-05-23
Whenever I boot into ubuntu 10.04, my monitor just automatically goes into sleep mode. As soon as I select to boot into ubuntu, the monitor just sleeps. There's no getting out of it. Booting into windows works fine though, so the problem has to be ubuntu. Any thoughts of how I could fix it?

---

### Post by xXSVx Phantom XS on 2010-05-24
also, the keyboard and mouse lose signal. i have to manually shutdown the computer every time i try to fix the problem.

---

### Post by DOSIX on 2010-05-26
I was the one helping him install it on his computer, so i'm posting here so i can get the answer too. here's some more info

ubuntu 10.04 64-bit
installed with wubi
dual boot with vista on same hdd

---

### Post by glopso on 2010-05-26
I used to have this problem, it would do this sometimes, and not some other times. I don't have it now, and I never figured out the problem. If it does this to you, press you power button then "enter" to shutdown (of course, your power button has to be compatible with this feature).

---

### Post by Catharsis on 2010-05-27
Hold down Shift while booting to get to grub. Hit 'e' and replace "quiet splash" with "nomodeset". Ctrl+x to boot.

---

### Post by xXSVx Phantom XS on 2010-05-28
it helped a little bit, but now after the purple splash screen with the five dots shows up it still goes to sleep.

---

### Post by Catharsis on 2010-05-28
Try replacing "quiet splash" with "xforcevesa noapic noapci nosplash irqpoll" instead.

---

### Post by xXSVx Phantom XS on 2010-05-28
i've managed to figure out the problem. basically the process you described earlier does work, but i have to re do it every single time i boot up. i've already tried editing the entry in /etc/default/grub that said

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```

to 

```

GRUB_CMDLINE_LINUX_DEFAULT="nomodeset noplymouth"

```

but it didn't do anything.
i still have to change the line you mentioned in grub every time i boot. is there a way to make it permanent?

---

### Post by Catharsis on 2010-05-28
```
gksudo gedit /etc/default/grub
```
Add "nomodeset" to that line. I don't think you need to remove "quiet splash" or add "noplymouth". But do what you want.
Save and exit, then run
```
sudo update-grub
```

---

### Post by IkimashoZ on 2010-06-19
I am trying to install Ubuntu 10.04 to some kind of desktop Mac.  I don't have any specs for this thing.  All I know is it's fairly new.  It is **not** the kind that comes with the monitor and and CPU all as one unit.  It's some kind of tower.  Maybe a G4?  I don't know.

Anyway, I had lots of trouble trying to install (monitor falls asleep immediately after the blinking line disappears) until I found the advice to add "nomodeset xforcevesa" to the startup directive in the installer.  After this, installation went completely smoothly.

Of course, once I went to boot up again, same problem.  After doing some searching, I found this thread.  I used my LiveCD so I can boot into the system.  Using the terminal I changed my /etc/default/grub to contain this:

```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset xforcevesa quiet splash"
```

This is the line that gets me into the installer and the live session.  But, I went to run sudo update-grub and no go.  I get an error about not being able to find a device attached to /.  I assume this is because the live session is mounting my main drive in /media and the root file system is just a temporary session.

In my case, when I attempt to boot from my hard drive, holding down shift on boot has no effect.  I cannot seem to reach the grub menu.  I have also tried holding down the escape key, and hitting ctrl+option+f1 many times and after waiting quite awhile.  None of these has any effect.

---

### Post by IkimashoZ on 2010-06-19
My graphics card is an ATI Radeon 2600XT, if that helps.

---

### Post by KzoneDD on 2010-11-13
Hi there,

I had simmilar issues. When I installed Ubuntu on a G4 PPC, the monitor would go into sleep mode right after booting. I tried several incarnations.

Installing the server edition did work, but obviously I had no GUI. Installing ubuntu-desktop immediately brought the problem back.

None of the solutions mentioned in this thread worked. But I reinstalled the serrver edition, then installed X and Gnome (NOT Ubuntu desktop) and I could boot into a working GUI, albeit only 800x600-60. (The system should be able to do far better.)

Maybe this info helps someone more of an expert than me figure out where this issue comes from.

Greetz.
DD.

---

### Post by Gerald here on 2010-11-15
I had the same problem as described in this thread using 10.10 (64-bit, ATI). Doing the nomodeset thing solved the problem (till now at least). Thanks !

Update: No, nomodeset didn't solve it. This threat is accurately describing my problem: [http://ubuntuforums.org/showthread.php?t=1518789&page=2](http://ubuntuforums.org/showthread.php?t=1518789&page=2) .
Update 2: Changing the splash screen as described in this thread solved it: [http://ubuntuforums.org/showthread.php?t=1503509&page=2](http://ubuntuforums.org/showthread.php?t=1503509&page=2)

---

