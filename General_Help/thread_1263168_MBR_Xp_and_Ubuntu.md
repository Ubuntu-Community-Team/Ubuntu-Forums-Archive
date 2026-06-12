---
title: "MBR Xp and Ubuntu"
date: 2009-09-10
forum: General Help
---

### Post by Soapy.Illusions on 2009-09-10
I borrowed a netbook from a friend for university, and well he uses XP (for his office work) I decided to set up UNR on a second partition of the EEE pc's drive

Now I need to give it back to the person, although they are not huge linux fans and will be extremely angry to see GRUB come up on their work computer

My thought was too simply format the UNR partition from XP, although people seem to say that will simply ruin the boot-loader and nothing will boot, or GRUB will remain and the UNR will simply not boot but XP will.

I know I need to somehow fix the MBR for XP, and I have a windows XP cd lying around, but this has no cd drive and I have no idea how to easily boot XP recovery from a USB to fix the MBR

Any ideas how to completely remove UNR from the box while leaving his XP partition untouched, and have a good working bootloader?



P.S. If their is no better way I will have it boot straight to XP in GRUB and put the GRUB countdown timer to 0 seconds, but I guess that would be a last resort

P.P.S. Please don't turn this into a XP vs. UNR thread, his business needs him to have XP, don't blame me for not trying to change this

---

### Post by chriskin on 2009-09-10
google gets this for me

> Obtain a bootable Windows XP CD, and use it to boot.
Wait through all the Bill-messages until you get the first prompt. Choose R to repair an existing installation.
It will search and prompt the Windows installation, showing :
1) C:\WINDOWS
choose 1, and it will ask for the Admin password. If you have one enter it or just press Enter.
C:\WINDOWS>
Now, type
C:\WINDOWS> CD ..
C:\> FIXBOOT C:
C:\> FIXMBR
C:\> BOOTCFG /rebuild

After the BOOTCFG, it will ask if you want to add the Installation it found, and to be safe answer &#8220;Y&#8221;.

---

### Post by Soapy.Illusions on 2009-09-10
Ya I found that too, the only problem is making a bootable XP cd, seems to be far from easy... very far, unless someone has a solution

---

### Post by chriskin on 2009-09-10
consider this a non-truly good advice, but downloading an illegal version just for this job, i'm sure that even bill gates himself would say that it's ok

---

### Post by Soapy.Illusions on 2009-09-10
> **chriskin said:**
> consider this a non-truly good advice, but downloading an illegal version just for this job, i'm sure that even bill gates himself would say that it's ok

Ya I'm way ahead of you on that, I have an .iso although don't know how to make it bootable for my netbook, which has no CD drive

---

### Post by chriskin on 2009-09-10
oh that's that as well :S
can't you use the same commands from inside windows?

there got to be something terminal-like on windows, isn't there?

---

### Post by Soapy.Illusions on 2009-09-10
There is the command prompt in Windows but you can only run the 

```
fixmbr
```

command when you are in recovery mode, which is only obtainable with a cd

---

### Post by egalvan on 2009-09-10
The ONLY thing that GRUB touches in an existing Windows XP install is the MBR (Master Boot Record)

So the ONLY thing that needs "fixing" is to re-do the Microsft-specific MBR.

SuperGRUB is excellent for this, and it has Flash/Thumb drive options. Repairing a borked MS MBR is one of it's options.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)


Or you can try going to a command prompt in XP,
and typing 

```
fdisk /mbr
```

It's been far too long since I mucked around with XP command-line,
so I may be mistaken on this.

But SuperGRUB is definitely workable.

---

