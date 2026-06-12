---
title: "Grub Security?"
date: 2010-09-14
forum: General Help
---

### Post by Vigh on 2010-09-14
Hi was just wondering how necessary it is to assign a password to the grub-boot loader? and how I go about doing it to make the system more secure.

---

### Post by WorMzy on 2010-09-14
How necessary is it to put a padlock on a shed door?

It all depends on the environment and the contents.

If you want to use a password, look here: [Grub 2 Password Protection]("http://ubuntuforums.org/showthread.php?t=1369019")

Be aware that grub protection can be easily gotten around with the aid of a LiveCD/USB, so you may want to prevent users booting from CD and such, and password protect your BIOS. Of course, a BIOS password can be reset by removing the CMOS battery, so you may want to put a lock on your PC's chassis.

Of course, as someone else said on these forums recently: A locked door is better than pretty much any technological protection.

---

### Post by Vigh on 2010-09-14
LOL! So true! I'm not worried about securing it from other people in the household. And i'm not that concerned about security. I am however getting a record number of kernel breaches on my internet router, and was wondering if putting a password on grub loader could be beneficial for this.

---

### Post by QLee on 2010-09-14
[QUOTE=Vigh]LOL! So true! I'm not worried about securing it from other people in the household. And i'm not that concerned about security. I am however getting a record number of kernel breaches on my internet router, and was wondering if putting a password on grub loader could be beneficial for this.[/QUOTE]
Post a few examples of those kernel breaches on your Internet router.

The password on GRUB only applies during booting, doesn't affect permissions on the loader.

---

### Post by Vigh on 2010-09-14
user - alert
kernel: Intrusion

i have done whois look ups

they are from china, japan, africa and the netherlands

i am in australia

have updated to latest version firmware

---

### Post by QLee on 2010-09-15
[QUOTE=Vigh]user - alert
kernel: Intrusion[/QUOTE]
Well, you didn't post any examples like I asked for but..., chances are good that what you are writing about are just "hits" on your firewall, blocked attempts to connect, an indication that the firewall is doing it's job. 

[QUOTE=Vigh]i have done whois look ups

they are from china, japan, africa and the netherlands

i am in australia
...[/QUOTE]
Yes, well if they had a nefarious purpose, chances are that they have spoofed the IP address and the one you are looking up is probably not where a malicious connection attempt originated. And many of the "hits" we get are harmless. These days on the 'Net it must almost drive you crazy if you monitor all that activity.

---

### Post by DrMelon on 2010-09-15
The fact you are getting alerts should be reassuring. That means they haven't gotten through your firewall. If it all went quiet, then you should be worried.

---

### Post by Vigh on 2010-09-16
Cheers!!! I did actually put an example up, but thought it best not to post it due to my IP address being in the router log-file.

---

