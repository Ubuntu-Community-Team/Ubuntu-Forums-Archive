---
title: "Cannot boot - Bash error 18"
date: 2009-07-19
forum: General Help
---

### Post by Xzenome on 2009-07-19
Hello there,

I've been using Ubuntu since Dapper now, so I'm not really new to Ubuntu, but I've come across a pretty 'fatal' problem that I can't solve.

I recently bought a computer that came with Ubuntu preinstalled along with Windows XP (I won't say who from right now because I don't want this to hurt their reputation, other purchases from them have been very good). Everything was going fine until yesterday when it seemed to get a bit temperamental about booting. I'd get this whole cylinder out of range (bash error 18) and I think I got an error 17 too or whatever it was error, but it'd sort itself out after a restart or two. Then today, it did it again but it never corrected itself. None of the partitions would boot, they all gave the same error.

I modified the BIOS settings to allow me to boot from a CD and booted a 9.04 CD that I had on my desk. It booted up fine.

```
ubuntu@ubuntu:~$ ls -l /dev/sd*
brw-rw----  1 root disk 8,  0 2009-07-19 15:50 /dev/sda
brw-rw----+ 1 root disk 8, 32 2009-07-19 16:02 /dev/sdc
brw-rw----+ 1 root disk 8, 48 2009-07-19 16:02 /dev/sdd
```

I believe sdc and sdd to be for empty card reader slots. sda is my hard disk.

Then I tried fdisk

```
ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda

```

No joy there.

Then I tried GPartEd (both from the Ubuntu live cd and the specific gparted live CD).

```
ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 1.8.8
======================
Input/output error during read on /dev/sda
ubuntu@ubuntu:~$ sudo gparted /dev/sda
======================
libparted : 1.8.8
======================
/dev/sda: unrecognised disk label


```
When I ran it the first time, /dev/sda didn't show up in its list of drives. When I ran it the second time, it showed the entire hard drive as unallocated.

I should point out that I wasn't at all fiddling around with partitions when this happened, I was playing tremulous. The system froze up and I rebooted and then the problems started.

I'm not that knowledgeable in this area, but my first thought was that the partition table might be damaged or destroyed for that matter.

If the worst comes to the worst I can reinstall or send it back to the manufacturer, but that's a lot of hassle and I'd quite like some files that I've created since my last weekly backup.

Help! :)

P.S. I was running linux-generic on an AMD 64.

---

### Post by louieb on 2009-07-19
Sometimes even new hardware has problems. I am having to return a wireless card I just bought. - won't connect to my network.

Sounds like the hard drive or its controller. I say that because **sudo fdisk -l **should have returned something. It just displays what is there. 

Use the live CD and follow [Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3") and put the results.txt file in your next post.

---

### Post by Xzenome on 2009-07-19
Ok, strange turn of events. I turned the computer off because I was bored, came back, booted into the live CD again, suddenly, it could see my partitions. So I took out the live CD, rebooted and GRUB and Ubuntu were working again. Just in case it wasn't going to last, I updated my backup.

I ran the boot info script and have attached the results.

I'm not sure whether it's relevant, but before the temporary problems (that sort themselves out after a few reboots) and before the more permanent one that I had earlier, I got a lot of errors in the console (something like ata: ext4 I/O error maybe, I may have mixed 2 errors together in my head or something) and I assume that caused the freezing or programmes to not execute that then made me decide to reboot.

I just want to find out what the cause is, because if it looks like a hardware issue, then I want resolve this before my warranty ends.

---

### Post by louieb on 2009-07-19
All looks normal in the results.txt file.  

If the errors come back think your getting a waring your computer about to die. 

Just be sure take good notes if it acts up again. I'm sure whoever you got it from will want to know.

---

