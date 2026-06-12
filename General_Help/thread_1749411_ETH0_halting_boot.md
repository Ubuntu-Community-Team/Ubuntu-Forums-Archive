---
title: "ETH0 halting boot"
date: 2011-05-04
forum: General Help
---

### Post by .Aaron on 2011-05-04
So I have been wanting to dable more into Linux since helping a friend at church install Ubuntu 10.10 on his netbook.  It looks sweet. So I saw that Ubuntu has WUBI.  So I went and downloaded it today.  I did the install and gave it 17GB of disk space, put in a username, password and clicked install. I sat back and let it roll.  The installer rebooted and I selected Ubuntu from the boot menu.  It loaded but then halted right after detecting my Logitech receiver.  I tried again, samething. I pressed Escape and selected ACPI startup (or something like that).  It installed and rebooted.  Now it will load to Grub and I select Ubuntu Linux and it loads, but as soon as it gets to ETH0, it stops. And I have let it sit there for OVER AN HOUR!!!

So here is what is on the screen:
r8169 0000:02:03.0: eth0: link down
ADDRCONF(NET.DEV_UP): eth0: link is not ready
r8169 0000:02:03.0: eth0: link up
ADDRCONF(NET.DEV_CHANGE): eth0: link becomes ready
eth0 : no IPv6 routers present

And it stops and does nothing.

My PC Specs:
Intel P4 2.8 HT
2gb ram
Realtek PCI gigabit network card

Please help, I will to learn.

---

### Post by bcbc on 2011-05-04
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

The acpi workarounds (see post #8 in the above thread for what the workarounds are) only last for the installation. You will need to apply them each time you boot or make the change permanent as described above. Usually, by searching on your computer brand/model you can find information others have posted to get Ubuntu working without requiring acpi workarounds (which can disable other things)

---

### Post by .Aaron on 2011-05-04
I had to use this option to get Ubuntu to install:

ACPI workarounds (uses 'acpi=off noapic nolapic')

---

### Post by bcbc on 2011-05-04
> **bcbc said:**
> [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)


> **.Aaron said:**
> I had to use this option to get Ubuntu to install:

ACPI workarounds (uses 'acpi=off noapic nolapic')
So you would use the technique in post #1 of the thread I showed above, to override the grub menu with the same kernel boot options to get it to boot again.

What computer brand/model do you have?

EDIT: ok I see you provided a spec... but that's a bit generic. You need something to search on to figure out what workarounds you need.

---

### Post by .Aaron on 2011-05-04
Umm..Its a self built machine.  Its running an Intel 865P board with P4 2.8. I am using a add-on nic card.  Sound is Audigy and Video is Nvidia Geforce 6800 XT.

---

### Post by bcbc on 2011-05-04
For nvidia I'd normally recommend nomodeset (but it sounds like that part is not the problem).

What you can do is try booting and change the boot options each time to see what works - try them one at a time. And remove quiet nosplash and see if you get some diagnostics when it fails.

Failing that you could search on "ubuntu Intel 865P kernel boot" and see if you get anything meaningful. I saw a few hits but nothing that stood out. Maybe add in some of your other hardware too.

---

