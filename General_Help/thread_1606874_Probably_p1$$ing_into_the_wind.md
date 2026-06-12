---
title: "Probably p1$$ing into the wind?"
date: 2010-10-27
forum: General Help
---

### Post by TNT1 on 2010-10-27
I have a pc, was given to me. No monitor, no keyboard, nada. I powered it on, and it clearly makes all the right noises, and so on, but what can I do with it? As in, before I hook a monitor and stuff up to it, can I get it on my network and do anything?

---

### Post by Mark Phelps on 2010-10-27
Why on earth would you hook up an unknown PC to your network -- without first at least taking a look to see what's on it???

Suppose, worst case, it's a virus-infected mess of a Windows XP PC, and as soon as you hook it up to your network, it starts searching for other machine to turn into bots?

Yeah, I know that's a worst-case scenario -- but how do you know it's NOT true?

Do yourself a favor and at least hook up a monitor, keyboard, and mouse and boot up the machine -- BEFORE you hook it up to your network.

---

### Post by matt_symes on 2010-10-27
Hi

Good point Mark. What are you currently running on it??? (windows linux???). What do you _want_ to run on it??? 

Do the sensible thing and hook up a keyboard and monitor. You can remotley manage using SSH, VNC or PuTTY (Under windows), however we need more info

Kind regards

---

### Post by gradysghost on 2010-10-27
I agree with Mark here.  At the very least, just format the drive before doing anything else.  If you want to know what it currently does, give it a mouse, keyboard, and monitor and power it on with no network connection.  This at least will let you get some idea of what kind of hardware you're dealing with (or you could just crack the case).

What could you potentially do with it?

Make a headless TeamSpeak server or Apache server or something.  I don't know what you ordinarily do with your computers.

---

### Post by choochoousmc on 2010-10-27
with no monitor or keyboard on it, how would you know it is even working at all?
Hook those up to it, but do NOT connect it to the network or your ISP.
As above it could be infected.
Check it out make sure it works properly.
If it has a usb port, download or run form the usb, several different antivirus / adware programs. Provided it is a windows machine.
Find out what internal hardware there is. Barand name / model of network card/ adapter, modem, hard drive, cd/ dvd , motherboard, processor etc.
[CENTER][LEFT]
If in doubt download a hard drive wipe program that returns the drive to all 0's (zeroes).
Only way to ensure nothing is hidden in the FAT or MBR.
Now decide do you want windows or linux on it.


[/LEFT]
[/CENTER]

---

### Post by gradysghost on 2010-10-27
As choochoousmc mentions, you can nuke the drive with zeroes.  You can actually do this from an Ubuntu live CD and a terminal.  If you're comfortable finding out what device is the internal disk drive on it, you can run this command to zero it:

```
dd if=/dev/zero of=/dev/sda bs=1M
```

US Department of Defense says that a drive is fully zeroed (as in, all magnetic resonance is gone from the drive and the drive's former data is completely nonrecoverable) once you've zeroed the drive in this manner seven times, which you can automate like this:

```
for i in (1..7)
do
    echo "Beginning wipe number $i"
    dd if=/dev/zero of=/dev/sda bs=1M
done
```

In each of these cases, be absolutely sure that [tt]/dev/sda[/tt] is the actual device you want to zero.  These commands are designed to cause data loss.

---

### Post by matt_symes on 2010-10-27
Hi

dd, dban. I'm sorry guys, but that is overkill? Plug in a keyboard and monitor. See what you have. If you want, try Ubuntu from the live CD.

Kind regards

---

### Post by gradysghost on 2010-10-27
Please don't get me wrong.  Using dd at this point is absolutely overkill, especially doing it seven times in a row, but I thought it was with mentioning that it's easy to do without buying any more software.  I agree that the computer should be brought up without a network connection before doing anything, and also want to add that simply reinstalling the operating system should be sufficient to remove any infection that may exist.

---

### Post by matt_symes on 2010-10-27
Hi

[gradysghost]("http://ubuntuforums.org/member.php?u=563645") my sincere apologies. You are right.

Kind regards

---

### Post by gradysghost on 2010-10-27
No big deal, man.  Just a misunderstanding.

---

### Post by TNT1 on 2010-11-01
Ok, so went the monitor route, it was running win 95, with a 1.2Gb HDD... scrubbed that, had an old 40Gb hdd lying around, so popped that in, and installed Fedora. New firewall installed on network.

---

### Post by ubudog on 2010-11-01
Don't really understand your post, but you could try Light Ubuntu or Lubuntu.   

[http://lubuntu.net/](http://lubuntu.net/)

It is optimized for older PC's like that. :)

---

