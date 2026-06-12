---
title: "Jaunty lockup -"
date: 2009-08-12
forum: General Help
---

### Post by stans on 2009-08-12
I've had random lockups since upgrading to Jaunty.

My message log revealed something interesting; most lockups occur after this message: 

*eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.*

I understand the concept of Full Duplex but am not sure how it could be responsible for the lockup of an entire system.

---

### Post by P4man on 2009-08-12
can it be that that is just the last message in dmesg, but it occurs long before the lockup ?

Check:

```
cat /var/log/messages
```

see if you find something in there to give a clue as the causes of the lockups.

---

### Post by stans on 2009-08-12
Perhaps I'm missing something obvious, but this display appears to be identical to the one provided by the Log File Viewer.

As I was watching the lines scrolling, got to the bottom with that same message then it stopped. Locked up again.

In a way I'm excited to have narrowed down this mystery, but frustrated in that this can happen. 

BTW, that message appears nowhere else in the log other than right before the boot that is forced by the lock up.

---

### Post by P4man on 2009-08-12
can't say I have any good idea's in that case.. perhaps try loading a previous kernel?

---

### Post by stans on 2009-08-12
That would be a bit drastic. I'll wait a bit to see if anyone has any ideas.

I'd rather see a fix for this.

---

### Post by P4man on 2009-08-13
no its not drastic at all, if have more than one kernel in the grub menu, just select a previous one. Which one are you running ? 2.6.28-14-generic ?

If in doubt type:
```
uname -r
```

To see which other ones you have installed, type

```
ls /boot
```

---

### Post by stans on 2009-08-13
I can see the previous versions... and thanks for the suggestion to return to the previous one.

Is 2.6.28-14-generic unstable ?  These lockups are getting very tiring.

---

### Post by P4man on 2009-08-13
I wouldn't call it "unstable" in general. It works flawlessly on the machine im typing on, it hasnt needed a reboot since I upgraded to it, but im troubleshooting another machine right now that constantly locked up using that kernel. Now I also replaced an IDE cable, and im not yet sure which of both cured it, but I suspect its the new kernel that doesnt get along with that particular machine. Either way, its easy to find out. Just boot the 2.6.28-11 kernel.

edit: actually. thinking about it, the machine almost always locked up when there was significant network activity.. so.. hmm. I'll test later today.

---

### Post by stans on 2009-08-13
In general vs. the machine you are trying to work on... it's all relative. 

I've booted 2.6.28-13-generic and will hope to not lock up. 

Thanks for your input - it is appreciated...

Just checked the log and see the *eth0: Setting full-duplex based on MII#1 link partner capability of 45e1 message*... but no lockup.

---

### Post by P4man on 2009-08-13
Im seeing some reports of ppl having the same issue who cured it getting the 2.6.30 proposed kernel (and getting better performance to boot). If you feel like trying,:

[http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/](http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/)

---

### Post by stans on 2009-08-13
Thanks, but think I will wait for the automatic update to provide it.

I'd like to revert to 'user' mode and start using this machine more instead of having to put energy into fixing things.

Still no lockup, btw.

---

### Post by stans on 2009-08-13
Followup: Just had the same lockup and see that I have booted with the 2.6.28-14-generic kernel. How do I make the change to another kernel permanent ?

---

### Post by P4man on 2009-08-13
edit:ignore

---

### Post by P4man on 2009-08-13
You can modify grub menu. 

```
gksudo gedit /boot/grub/menu.lst
```

Remove the latest kernel entry there. 

If you want it gone completely:

```
apt-get remove kernel-image-2.6.xxxx (press tab for automcomplete)
```

But then next time you update your machine, it will propose it again...

---

### Post by stans on 2009-08-13
I don't see anything when editing the member... it is empty. Perhaps it is in another location ?

---

### Post by P4man on 2009-08-13
I mistyped. Its menu.lst not menu.list.
I even made 2 typo's, I wrote gub rather then grub lol.. here is is again:

gksudo gedit /boot/grub/menu.lst

---

### Post by P4man on 2009-08-13
it will look something like:

```

title		Debian GNU/Linux, kernel 2.6.28-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=0e5317cf-1aa2-4b20-9ffa-f17c41f48f37 ro quiet splash
initrd		/boot/initrd.img-2.6.28-14-generic

title		Debian GNU/Linux, kernel 2.6.28-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=0e5317cf-1aa2-4b20-9ffa-f17c41f48f37 ro single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Debian GNU/Linux, kernel 2.6.28-13-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=0e5317cf-1aa2-4b20-9ffa-f17c41f48f37 ro quiet splash
initrd		/boot/initrd.img-2.6.28-13-generic

title		Debian GNU/Linux, kernel 2.6.28-13-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=0e5317cf-1aa2-4b20-9ffa-f17c41f48f37 ro single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Debian GNU/Linux, kernel 2.6.28-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0e5317cf-1aa2-4b20-9ffa-f17c41f48f37 ro quiet splash
initrd		/boot/initrd.img-2.6.28-11-generic

title		Debian GNU/Linux, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0e5317cf-1aa2-4b20-9ffa-f17c41f48f37 ro single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Debian GNU/Linux, kernel memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

```

just delete the two top entries with the 2.6.28.14 kernel so it looks like



```
title		Debian GNU/Linux, kernel 2.6.28-13-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=0e5317cf-1aa2-4b20-9ffa-f17c41f48f37 ro quiet splash
initrd		/boot/initrd.img-2.6.28-13-generic

title		Debian GNU/Linux, kernel 2.6.28-13-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=0e5317cf-1aa2-4b20-9ffa-f17c41f48f37 ro single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Debian GNU/Linux, kernel 2.6.28-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0e5317cf-1aa2-4b20-9ffa-f17c41f48f37 ro quiet splash
initrd		/boot/initrd.img-2.6.28-11-generic

title		Debian GNU/Linux, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0e5317cf-1aa2-4b20-9ffa-f17c41f48f37 ro single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Debian GNU/Linux, kernel memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

```

---

### Post by stans on 2009-08-13
Got it; the deed is done.

Now to reboot.

I do appreciate your assistance.

---

### Post by P4man on 2009-08-15
Im curious, are you still seeing any freezes with the old kernel?
For me it seems cured, and also the upcoming 2.6.30 is rocksolid.

---

### Post by stans on 2009-08-15
Nice of you to follow up.

I just had one... and I think there was one more the other day.

I'm not a heavy duty user but this is an improvement.

So do you suppose this is some kind of problem with the ethernet driver then ?

---

### Post by P4man on 2009-08-15
once a day is still hardly acceptable :s

you could try an older one, or 2.8.30.

As to what causes it.. I could guess, but it would be just that.
a guess;

---

### Post by stans on 2009-08-16
I think it is time to try another distro for awhile.

Thanks again for following up.

Bye.

---

### Post by Trapper on 2009-08-16
> **stans said:**
> I think it is time to try another distro for awhile.

Thanks again for following up.

Bye.

That's what we've done here. U-904 is currently labeled temporarily unreliable and not used. Fedora 11 was having the same basic freeze problems and also black screens popping up out of no where. They've managed to fix their issues apparently. Xorg's server was one of the main culprits over there and I believe kernel problems were involved too. They just pushed a new xorg-server package to testing a couple of days ago. Whatever they've done, the freeze ups and blank screens disappeared. Of course it took through their F11 alpha, beta, and well after their final release to resolve the issues.

I can understand your desire to try something else for a while. Having to hard reboot a number of times a day is quite reminiscent of Windows 95 and it creates the same frustration and exasperation Windows 95 did. The bad news is that almost all distro's using current kernels and xorg have been experiencing these types of  issues. Be careful with the distro you select.

---

### Post by lessgov2007 on 2009-08-16
I feel lucky then. I've had no such problems out of 9.04.

Although a while back I was running both Kubuntu 9.04 and Ubuntu 9.04 and having random lock-ups in both. I believe this was caused by using ext4. I reformatted and used ext3 and have not had any problems since.

---

### Post by stans on 2009-09-29
Well - I've roamed around a bit and find Ubuntu is worth returning to, lockups or not.

Just installed 9.04 and see the lockups are still here, although seemingly related to the usb mouse based on what I learned on openSUSE - the usb mouse was locking up. During my last lockup here I plugged the old ps/2 mouse into the motherboard port and the pointer moved a bit, then it locked.

I'm tired of roaming around the distros and want to settle down here... but need a stable system.

---

### Post by P4man on 2009-09-30
Id start suspecting the BIOS. Can you check if you can update it? Do you have options to play with for things like IRQ assigning ? Its a wild guess but maybe something (like USB) is sharing an interrupt (eg with video). Can you post the output of:

```
cat /proc/interrupts
```

You might also want to experiment with some kernel switches like "noapic" "nolapic" "acpi=noirq " which may help get around buggy bios's.

---

### Post by stans on 2009-09-30
stan@stan-desktop:~$ cat /proc/interrupts
           CPU0       CPU1       
  0:        122          0   IO-APIC-edge      timer
  1:          2          0   IO-APIC-edge      i8042
  4:          2          0   IO-APIC-edge    
  6:          5          0   IO-APIC-edge      floppy
  7:          1          0   IO-APIC-edge      parport0
  8:          0          0   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 12:      84618          0   IO-APIC-edge      i8042
 14:          0          0   IO-APIC-edge      pata_amd
 15:       7774          0   IO-APIC-edge      pata_amd
 16:      87451          0   IO-APIC-fasteoi   nvidia, eth0
 20:        429          0   IO-APIC-fasteoi   ohci_hcd:usb2
 21:          3          0   IO-APIC-fasteoi   ehci_hcd:usb1
 22:      69254          0   IO-APIC-fasteoi   sata_nv
 23:       9460          0   IO-APIC-fasteoi   sata_nv, HDA Intel
NMI:          0          0   Non-maskable interrupts
LOC:     114666     121847   Local timer interrupts
RES:       1972       3257   Rescheduling interrupts
CAL:        710       5527   Function call interrupts
TLB:       1780       4366   TLB shootdowns
SPU:          0          0   Spurious interrupts
ERR:          1
MIS:          0

To be honest, I found recovery for the lockup to consist of plugging the ps/2 mouse in. It is plugged in now, and both mice are working.

I researched updating the motherboard (ASUS P5NSLI) and it did appear to have a bit of a risk involved. Kernel switches ? No sure what you mean...

BTW  - Thanks for your reply.

---

### Post by P4man on 2009-09-30
Are you saying it doesn't lock up as long as there is a PS2 mouse connected? LOL?

Anyway, I can't see anything wrong with the interrupts, but I do see you're using apic, which may cause problems with buggy bioses. To experiment with kernel parameter (boot options), have a look here:

[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

In that example they give "vga=771" as option. Instead of that, try booting with "noapic", "nolapic" and "i8042.nomux=1".  Those changes only apply for 1 boot, but should you find one that works, further on that page they explain how to make the change permanent.

---

### Post by stans on 2009-09-30
Yes, it is definitely a 'LOL' as the problem appears to follow the distros and shows up on their forums. 

Matter of fact, I just read about someone leaving Ubuntu for that reason. 

I'm out of time for the morning session (must report to work unfortunately) but will definitely pursue your suggestion this evening.

Thanks again for your support.

---

### Post by stans on 2009-09-30
Following up - specified noapic and nolapic as per directions that you pointed me to. Interesting new boot message about 'forcing use of dummy apic emulator' (or something like that) but so far so good. Guess we will be going into monitor mode for a week or so, then will definitely report back for the benefit of others. 

Thanks again very much for your support P4man. 

I am looking forward to a stable system.

---

### Post by P4man on 2009-10-01
You booted with both noapic and nolapic switches? I should have been more clear, but I figured trying just one at a time initially, but if it works with both, and it seems stable then so much the better :). There is potentially a tiny performance hit from using them, but I doubt its measurable, let alone noticeable. 

 Keep in mind those changes only work until the next boot, unless you modify your grub to make them permanent. And even that "permanent" only lasts until the next time you update to a new kernel.

Anyway, I do hope its solved. If it is, write an angry mail to your OEM that they should fix their BIOS ;)

---

### Post by stans on 2009-10-01
Perhaps I should have tried just one, but it would be my luck to try the one that had no effect. 

You have no idea what frustration this has caused me... and I am VERY anxious to move on without having to deal with it.

I did have a lockup shortly thereafter, but it was npviewer providing some sort of fault. I've been trouble free now at least half an hour so far this morning. 

You mentioned performance - I see no degradation.

Guess I should seriously consider upgrading the bios of the motherboard - after all it is about three years old now.

---

### Post by stans on 2009-10-01
Update - three or four more lockups in the last hour and a half.

Sigh.

---

