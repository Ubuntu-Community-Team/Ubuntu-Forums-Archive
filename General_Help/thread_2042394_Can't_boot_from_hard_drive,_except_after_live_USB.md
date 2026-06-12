---
title: "Can't boot from hard drive, except after live USB"
date: 2012-08-14
forum: General Help
---

### Post by Dan Pat on 2012-08-14
Two days ago, I attempted to boot my laptop and was greeted with the awful news that it didn't seem to think I had an operating system installed. The hard drive test utility that I'm presented with then simply returns "HARD DRIVE NOT EXIST", which is a hilariously frustrating piece of grammar. I confirmed that my hd does in fact exist, then removed and reattached it with no results. After some troubleshooting, I found that I could boot from a live USB drive and still access and backup my files on the hard drive.

But here's the weird part. After some goofing around, I found that after running the FIle Integrity Check when booting from the live USB, *my computer restarts and then boots completely normally.* I'm thinking that there's something weird going on with my bootloader. Usually, GRUB is the first thing I see and I can pick between Windows or Linux. Maybe something updated and broke it. 

Any and all help is greatly appreciated! I'm running Kubuntu 12.04 and Win7 on an HP Envy 14.

---

### Post by C.S.Cameron on 2012-08-14
So if you can boot into the Kubuntu on the HP?
Remove the flash drive and run update-grub.

---

