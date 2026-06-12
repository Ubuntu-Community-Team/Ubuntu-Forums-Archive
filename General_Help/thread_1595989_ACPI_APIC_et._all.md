---
title: "ACPI APIC et. all"
date: 2010-10-13
forum: General Help
---

### Post by petrasflorin on 2010-10-13
So after random freezes of Ubuntu I found this solution of disabling things in BIOS.

I have an Asus P5LD2-VM DH motherboard and I went there and did the following:

Suspend Mode:	 S1 Only
Repost Video on S3 Resume:	No
ACPI 2.0 Support:	 No
ACPI APIC Support:	 Disabled

Under APM I did the following:

I Enabled PCI and PCIE to apparently wake-up the computer.

After doing these I currently experienced no freeze-ups AND I solved the infamous modprobe error (check here: [http://ubuntuforums.org/showthread.php?t=1592062](http://ubuntuforums.org/showthread.php?t=1592062) ).

So apparently this is a good thing, no fatal errors, no freezes (until now).

However, two things: I have no idea what I've done in BIOS - is it ok ? Is it wrong ? Anyone care to explain ?

and

conky won't start, apparently I now only have one CPU (I have a Dual Core).

pif@pif-asus:~$ conky
Conky: forked to background, pid is 3116
pif@pif-asus:~$ 
Conky: desktop window (1a000aa) is subwindow of root window (15a)
Conky: window type - normal
Conky: drawing to created window (0x4600001)
Conky: drawing to double buffer
Conky: obj->data.i 2 info.cpu_count 1
Conky: attempting to use more CPUs than you have!

---

### Post by petrasflorin on 2010-10-13
I've enabled ACPI APIC once again, conky is back and my two processors but so is the infamous modeprobe error.

Hei at least I've narrowed the modprobe error to ACPI APIC related. Although I have no idea what this means.

Also this means my random freeze-ups will be back. Too bad, I don't like them but I also don't like running with only one core of my CPU.

---

### Post by petrasflorin on 2010-10-13
OK besides the random freezes (which occur randomly and pretty rare) I can reproduce a freeze by inserting a DVD/CD into my CD/DVD drive and letting it SPIN DOWN. The second it spins down (i.e not hearing it anymore, LED not on) the computer freezes.

And I mean freeze: no CTRL+ALT+DEL, no CTRL+ALT+F1, no CTRL+ALT+BACKSPACE, conky stops update, clock stops update, nothing works, mouse not moving, nothing. TOTAL LOCKDOWN.

---

### Post by coffee412 on 2010-10-13
> **petrasflorin said:**
> So after random freezes of Ubuntu I found this solution of disabling things in BIOS.

I have an Asus P5LD2-VM DH motherboard and I went there and did the following:

Suspend Mode:     S1 Only
Repost Video on S3 Resume:    No
ACPI 2.0 Support:     No
ACPI APIC Support:     Disabled

Under APM I did the following:

I Enabled PCI and PCIE to apparently wake-up the computer.

After doing these I currently experienced no freeze-ups AND I solved the infamous modprobe error (check here: [http://ubuntuforums.org/showthread.php?t=1592062](http://ubuntuforums.org/showthread.php?t=1592062) ).

So apparently this is a good thing, no fatal errors, no freezes (until now).

However, two things: I have no idea what I've done in BIOS - is it ok ? Is it wrong ? Anyone care to explain ?

and

conky won't start, apparently I now only have one CPU (I have a Dual Core).

pif@pif-asus:~$ conky
Conky: forked to background, pid is 3116
pif@pif-asus:~$ 
Conky: desktop window (1a000aa) is subwindow of root window (15a)
Conky: window type - normal
Conky: drawing to created window (0x4600001)
Conky: drawing to double buffer
Conky: obj->data.i 2 info.cpu_count 1
Conky: attempting to use more CPUs than you have!


> cat /sys/devices/system/clocksource/clocksource0/current_clocksource

cat /sys/devices/system/clocksource/clocksource0/available_clocksource*Pick a different clock source, Edit your /etc/default/grub file and then run grub update and see if your freezing stops. 

Worked on a system I had freezing problems on. Make sure ACPI is on also in BIOs.

---

### Post by petrasflorin on 2010-10-14
clocksource: tsc
available clocksource: tsc acpi_pm

How do I pick acpi_pm ?

GRUB... what exactly should I edit here?

---

### Post by coffee412 on 2010-10-14
Ok. Here are the steps and hope this helps. As I said, I did this on a box and it fixed the freezing problem. Your mileage may differ.

1.Open a term window and edit the grub file

> Sudo gedit /etc/default/grub
2. Find the line that starts --> > GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
3. Change the line to read 

> GRUB_CMDLINE_LINUX_DEFAULT="ACPI=acpi_pm quiet splash"
4. Save and then run the grub update

> sudo update-grubReboot and test to see if freezing stops.

:)

---

### Post by Quackers on 2010-10-14
Is this line correct Coffee?
GRUB_CMDLINE_LINUX_DEFAULT="APCI=acpi_pm quiet splash" 
(Not ACPI (or APIC) =acpi_pm quiet splash)? 
Just for clarification, you understand :-)

---

### Post by coffee412 on 2010-10-14
> **Quackers said:**
> Is this line correct Coffee?
GRUB_CMDLINE_LINUX_DEFAULT="APCI=acpi_pm quiet splash" 
(Not ACPI (or APIC) =acpi_pm quiet splash)? 
Just for clarification, you understand :-)

Sorry! Only on my first cup of coffee:

Line should read "ACPI=acpi_pm"

---

### Post by Quackers on 2010-10-14
Lol, I know what you mean :-)
Can you edit the original post so the OP and others following don't jump the gun?

---

### Post by coffee412 on 2010-10-14
> **Quackers said:**
> Lol, I know what you mean :-)
Can you edit the original post so the OP and others following don't jump the gun?

Got it.

I had this problem on a older emachine of a customers. Of course, In the logs it was giving an error of something like "TSC clocksource unstable". 

Sure would like to know if this helped you at all. If it does let me know.

---

### Post by petrasflorin on 2010-10-14
Ok did those steps, no freezes until now. Although they were rare so I won't really know too soon if it worked.

However my DVD/CD-rom is still freezing my system, and that can be reproduced, no probs just insert DVD and bam, 100% LOCKDOWN again. Dang.

Thanks, if this worked it should at least give me a degree of control on when my computer freezes, as in: not being random anymore.

---

### Post by coffee412 on 2010-10-14
> **petrasflorin said:**
> Ok did those steps, no freezes until now. Although they were rare so I won't really know too soon if it worked.

However my DVD/CD-rom is still freezing my system, and that can be reproduced, no probs just insert DVD and bam, 100% LOCKDOWN again. Dang.

Thanks, if this worked it should at least give me a degree of control on when my computer freezes, as in: not being random anymore.

Well, Then your problem lies else-where if sticking a dvd in locks the system up. Be interesting to see your log file (/var/log/messages). I bet its got a wealth of info about why your locking up. Can you post it or send it to me?

---

### Post by petrasflorin on 2010-10-14
Here it is: [http://rapidshare.com/files/425045789/messages](http://rapidshare.com/files/425045789/messages)

---

### Post by coffee412 on 2010-10-14
> **petrasflorin said:**
> Here it is: [http://rapidshare.com/files/425045789/messages](http://rapidshare.com/files/425045789/messages)

What are you running on? I dont see your dvd drive mentioned in the logs at all. Im used to seeing something about it when it is discovered on boot up atleast. 

If you dont load a dvd will it still lockup?

I did see this error: ata3.01: failed to IDENTIFY (I/O error, err_mask=0x5)

Nevermind, Found the dvd drive:

ata3.01: ATAPI: HL-DT-ST DVDRAM GSA-H10N, JL10, max UDMA/33

Looks to me that you are having a problem with either your dvd drive or a disk that is in it.

---

### Post by petrasflorin on 2010-10-15
No lock-ups if there's no disk in it. As soon as I insert a disk and it spins down, it locks.

---

### Post by coffee412 on 2010-10-15
> **petrasflorin said:**
> No lock-ups if there's no disk in it. As soon as I insert a disk and it spins down, it locks.

The model number of your dvd drive is : GSA-H10N

Have you checked the reviews online about this drive from retailers? Evidently this drive has problems when hooked up with sata controllers. I recommend you replace this dvd drive.

I had a LG drive bought from newegg. It was so bad that when I contacted Newegg about all the problems with it they just said "Keep it and we will credit your account". I tossed the thing in the garbage.

Really, DVD drives now are quite inexpensive. Go to Newegg and just order another (but not LG IMHO).

I qoute a amazon review from a buyer here running windows even:

> If you are using SATA local harddrives connected direct to the  motherboard, you risk getting a blue screen of death   "session3_initalization" error when you boot the machine up with this.   Has nothing to do with the OS.  This is strictly deep in the jungle of  hardware/firmware land. 
So, There you go. You can see that your system is having problems with it from my earlier post.

---

