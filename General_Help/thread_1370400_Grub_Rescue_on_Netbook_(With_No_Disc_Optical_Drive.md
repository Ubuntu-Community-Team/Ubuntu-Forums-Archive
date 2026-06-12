---
title: "Grub Rescue on Netbook (With No Disc Optical Drive)"
date: 2010-01-02
forum: General Help
---

### Post by foresthill on 2010-01-02
OK, here's what happened. My girlfriend has a dual boot netbook I set up for her with Vista + 9.10. Her internet service went down yesterday temporarily and she was messing around with the computer to get back online and somehow booted into the Windows Rescue Partition and began the Windows Restore process, then turned the computer off during the middle of the restore process.

It's her only computer and she lives 1800 miles away. And since it's a netbook there's no optical drive.

When she boots up now, the netbook goes straight into Grub Rescue mode. I got her to try most of the commands for Grub Rescue, but most of them come back as "Unknown Command". The "LS" command works though, and she was able to get a list of partitions displayed.

QUESTION: Does anyone know of some commands she could use try to boot back into 9.10 (assuming it's still there)? Or even boot into Windows? Specifically, is there a simple command that could be combined with "LS" to specify a partition and try to boot into it? 

Thanks very much in advance.

Failing that, is it possible to reinstall or repair 9.10 with a bootable USB thumb drive I could send her in the mail?

---

### Post by drs305 on 2010-01-02
This section of the Grub 2 community doc discusses how to get back into Ubuntu via the Grub 2 command line. There are a few ways to try, starting with the simplest and progressing to entering more commands.

If she goes through the section slowly she should be able to get back into Ubuntu.

[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode")

If you or she has questions about the process ask them here.

---

### Post by foresthill on 2010-01-02
She can't view the site, as the netbook is her only computer. Any commands I get her to try will have to be given over the phone. And all the commands I had her try so far have returned as "unknown command" except for the "LS" command.

I guess I will try to get her to hold down the shift key to get the menu to come up, and also control-x. Anything else I might try?

---

### Post by Leppie on 2010-01-02
> **foresthill said:**
> I guess I will try to get her to hold down the shift key to get the menu to come up, and also control-x. Anything else I might try?

with the rescue prompt appearing, she won't be able to get to the menu (otherwise the system would've shown the menu).
what output did she get from the ls command?

---

### Post by Torrilin on 2010-01-02
Unless she got very lucky, she won't be able to repair Grub2 via the rescue prompt. She needs about 4-6 of the commands available, and IME ls is the one most likely to survive an accident. There are about 20 total commands, and if "help" doesn't work, odds are something else critical is missing.

If Grub2 is hosed enough that you have a rescue prompt, your best bet is a LiveUSB. Most versions of the instructions will have the user try to do a mount --bind via the command line to get each partition mounted. It's usually better to use the GUI for mounting your devices, since most command line instructions do not give a novice user enough background to figure out the correct mount points for their devices in /dev. Once you have all partitions mounted, it's safe to use the command line instructions.

Not all flash drives will boot all machines. Sometimes it might be due to software provided by the manufacturer, but other times there are no obvious reasons for the problem. So even if you've got a netbook that boots off the drive, it may happen that hers can't. I've got a Kingston USB stick that's failed on every machine I've tried it on, but an identical size Kingston microSD card that will boot almost anything. Several freebie USB sticks will boot some machines, but not others... and I have one that will cheerfully boot off an Ubuntu image, but if you try to put a different distro on the stick, it won't boot.

Since your girlfriend is clearly not very tech aware, you'll need to go over these weak points with her *carefully*. Odds are the Grub issues are only the surface problem right now.

---

### Post by drs305 on 2010-01-02
> **foresthill said:**
> She can't view the site, as the netbook is her only computer. Any commands I get her to try will have to be given over the phone. And all the commands I had her try so far have returned as "unknown command" except for the "LS" command.

I guess I will try to get her to hold down the shift key to get the menu to come up, and also control-x. Anything else I might try?

If G2 can't find it's commands, she may have to set the prefix first, with the correct device (hd0,1), etc. The setting she uses should have been one of the returns from the "ls" command.

She will know she is looking in the correct place when the following displays the boot files such as "vmlinuz-<her_version>" and "initrd.img-<her_version>"  such as vmlinuz-2.6.31-16-generic.
```
ls (hdX,Y)/boot
```
Example: ls (hd0,1)/boot

Once she has found the boot files, run the following with the correct X,Y values:
```
set prefix=(hdX,Y)/boot/grub
```
and then resume the commands in the Grub 2 doc. The "Express boot to the most recent kernel" section would be the easiest to convey over the telephone, after she has run the "set prefix" command.

I hope you have cheap long distance rates.  ;-)

---

### Post by foresthill on 2010-01-02
> **Leppie said:**
> with the rescue prompt appearing, she won't be able to get to the menu (otherwise the system would've shown the menu).
what output did she get from the ls command?

She got a list of 4-5 partitions.

---

### Post by Leppie on 2010-01-02
> **Torrilin said:**
> Since your girlfriend is clearly not very tech aware, you'll need to go over these weak points with her *carefully*. Odds are the Grub issues are only the surface problem right now.

i agree, don't think windows will be accessible before running and finishing the windows restore.

---

### Post by foresthill on 2010-01-02
> **Leppie said:**
> i agree, don't think windows will be accessible before running and finishing the windows restore.

I'm willing to write off Windows, but if only we could get the machine to boot into Linux , she could reinstall Grub and could at least boot into 9.10.

---

### Post by foresthill on 2010-01-02
> **Torrilin said:**
> Unless she got very lucky, she won't be able to repair Grub2 via the rescue prompt. She needs about 4-6 of the commands available, and IME ls is the one most likely to survive an accident. There are about 20 total commands, and if "help" doesn't work, odds are something else critical is missing.

If Grub2 is hosed enough that you have a rescue prompt, your best bet is a LiveUSB. Most versions of the instructions will have the user try to do a mount --bind via the command line to get each partition mounted. It's usually better to use the GUI for mounting your devices, since most command line instructions do not give a novice user enough background to figure out the correct mount points for their devices in /dev. Once you have all partitions mounted, it's safe to use the command line instructions.

Not all flash drives will boot all machines. Sometimes it might be due to software provided by the manufacturer, but other times there are no obvious reasons for the problem. So even if you've got a netbook that boots off the drive, it may happen that hers can't. I've got a Kingston USB stick that's failed on every machine I've tried it on, but an identical size Kingston microSD card that will boot almost anything. Several freebie USB sticks will boot some machines, but not others... and I have one that will cheerfully boot off an Ubuntu image, but if you try to put a different distro on the stick, it won't boot.

Since your girlfriend is clearly not very tech aware, you'll need to go over these weak points with her *carefully*. Odds are the Grub issues are only the surface problem right now.

Thanks. I know the machine boots fine from my external USB DVD drive. Maybe she could buy one of those and I could mail her an Ubuntu disc.

I told her to start shopping for another laptop yesterday, and it's starting to look like this is going to be the easiest solution. At least if she can get online, she can read the GRUB tutorials and try out different commands. But I just don't think dictating endless 15-20 character long CLI commands to a Windows user over a scratchy cell phone connection is gonna work too well, unfortunately.

I was hoping there might be a simple command.

---

### Post by Cheesemill on 2010-01-02
Chances are if she started the Windows recovery partition then both OS's are gone.
The first thing these restore partitions usually do is repartion and reformat the drive.

---

### Post by foresthill on 2010-01-02
You are probably correct, unfortunately. But I'm thinking that maybe only the MBR was wiped or partially wiped. Isn't that usually the first thing that happens?

---

### Post by Leppie on 2010-01-02
> **foresthill said:**
> You are probably correct, unfortunately. But I'm thinking that maybe only the MBR was wiped or partially wiped. Isn't that usually the first thing that happens?
if that was correct, you wouldn't get to the grub rescue prompt but probably a windows bsod. it gets there because grub is still installed in the mbr.

---

### Post by foresthill on 2010-01-02
Does the DOS command fdisk/mbr still work to remove the linux bootloader from a system? 

I was thinking that this might at least allow her to boot back into Windows or Windows recovery.

---

