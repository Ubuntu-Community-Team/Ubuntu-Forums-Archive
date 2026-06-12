---
title: "can't resume or boot to system after hibernating"
date: 2011-03-22
forum: General Help
---

### Post by doron387 on 2011-03-22
[COLOR="Blue"][solved] solution was to reformat the swap partition back to linux-swap, it was done using ubuntu liveusb and geparted.[/COLOR]

hi guys,
ubuntu 10.10 on asus 1201n, i have it for 2 months, works flawlesly, including hibernate and suspend.
until today.
after hibernating, when i power on the machine i get a black screen, with white letters.
this is all the text that is written on the screen : 

[COLOR="Blue"]resume: libgcrypt version: 1.4.5
looking for splash system... none
resume: compressed image
loading image data pages (96463 pages)... wrote 376.8 mb in 12.4 seconds (30.5 mb/s)
read 376.8 mb in 0.0 seconds 3425568.2 mb/s)

the system snapshot image could not be read.

this might be a result of booting a wrong kernel
or typing in a wong passphrase.

you can continue to boot the system and lose the saved state or reboot and try again.

[notice that you may mount any filesystem between now and succesfull resume. that would badly damage affected filesystems.]

do you want to continue boot (Y/n)?[/COLOR]

the problem is that it does not respond to Y or N or ENTER .
it only responds to ESC, which sends it to the boot screen (the one with the orange dots channging to white and then again to orange.

i don't have a clue what to do.

pls help.

thanks 
doron387

---

### Post by doron387 on 2011-03-24
bump
anybody ???
i can't boot to my ubuntu install.......

---

### Post by Peter09 on 2011-03-24
Are you using a capital Y, I have noticed some conversations do require the right case.

---

### Post by doron387 on 2011-03-24
it does not respond to y or Y ,
just ESC brings the boot screen, that goes on and on until i get tired of it.
then, ESC brings me back to the screen shown above.
alt+f2 brings black screen with blinking cursor on left upper corner.
and nothing else happens....
can i fix it using ubuntu live flashdrive ?

---

### Post by Peter09 on 2011-03-24
Have you tried holding shift during startup to get to the menu, then selecting recovery mode?
 
If you can get there do
 
shutdown -r now
 
to restart

---

### Post by matt_symes on 2011-03-24
Hi

Not sure if i can help with this one. I have never come across it but lets check the basics.

You are booting using the correct kernel ?

You have checked your fstab on your hard drive drive to make sure the swap UUID is the correct UUID for your swap partition and it has not become corrupted ? This can be checked from the LiveUSB.

If you need help with this boot into  the LiveUSB and type

```
sudo swapoff
cat /etc/fstab
sudo blkid
```

Post the results of the last two commands here.

I would also like to check the UUID used by initramfs for resume but i can't remember the name of the file at the moment. I will check for you.

I believe your swap may have become corrupted some how.

It may be possible to format your swap and update your initramfs image but i am not sure of the consequences of doing this due to the potential of unflushed buffers etc. I will have to read up on this. It may totally bork your system.

In the first instance, i _would_ backup your drive.

Thinking about it maybe we could look inside your initramfs file on your hard drive and check the resume UUID. I will get back to you about that.

Kind regards

---

### Post by QLee on 2011-03-25
[QUOTE=matt_symes]...
I would also like to check the UUID used by initramfs for resume but i can't remember the name of the file at the moment. I will check for you.

I believe your swap may have become corrupted some how.

It may be possible to format your swap and update your initramfs image but i am not sure of the consequences of doing this due to the potential of unflushed buffers etc. I will have to read up on this. It may totally bork your system.
...[/QUOTE]
Just want to step in here and say that your troubleshooting sounds reasonable, something corrupted about the resume partition (swap) is what occurred to me too.

Probably the file you want to look at is /etc/initramfs-tools/conf.d/resume for what the system uses to configure the initrd image.

I would expect formatting the swap and generating a new initrd.img to work (you could even give it the same UUID if you chose to do that, not needing the initramfs update). The "new" swap would not have a resume file on it and I would expect it to continue with a normal boot just as if it hadn't been hibernated. Disclaimer: Your caution is both reasonable and appropriate. I can't guarantee anything, I believe I did something like that once but I can't be sure the conditions were exactly the same as in this case.

---

### Post by matt_symes on 2011-03-25
Hi

> **QLee said:**
> Just want to step in here and say that your troubleshooting sounds reasonable, something corrupted about the resume partition (swap) is what occurred to me too.

Probably the file you want to look at is /etc/initramfs-tools/conf.d/resume for what the system uses to configure the initrd image.

I would expect formatting the swap and generating a new initrd.img to work (you could even give it the same UUID if you chose to do that, not needing the initramfs update). The "new" swap would not have a resume file on it and I would expect it to continue with a normal boot just as if it hadn't been hibernated. Disclaimer: Your caution is both reasonable and appropriate. I can't guarantee anything, I believe I did something like that once but I can't be sure the conditions were exactly the same as in this case.

Yes. I was also thinking about looking inside his latest initramfs using something along the lines of 

```
gzip -dc /boot/initrd.img-XXXXX-generic | cpio -idv  conf/conf.d/resume
```

and checking the resume UUID is correct in there.

If not i was going to suggest reformating the swap partition and the rebuilding the initramfs. Again something along the lines of

```
sudo swapoff /dev/sda1
sudo mkswap /dev/sda1
sudo update-initramfs -u
```

and then reboot and cross fingers. But first the OP must backup the hard drive. 

@OP. Don't use these command yet. They are more of an explanation and feedback for other posters here.

Thanks for your feedback QLee. :)

Kind regards

---

### Post by doron387 on 2011-03-26
thanks guys,
there were some things that i did not understand in your posts, like the UUID stuff....
but i did understand that if i format the swap partition it might work and boot normally as i hadn't hibernated at all, suits me.
can i do it in the simple way ? e.g. using ubuntu live usb and gparted to format the swap partition ? this will be the simplest for me.
just to clarify : it is an asus 1201n netbook, dualboot win7 & ubuntu 10.10,  
partition 1-win7
partition 2-ubuntu /
partition 3-data
partition 4-swap

waiting for your answers

doron387

EDIT :  i have tried recently to boot from ubuntu live usb, in gparted on sda i saw few partitions, but non of them is listed is swap so i can't do anything until i know exactly which partition is the swap partition.
i also tried in terminal : fdsik -l but it showed me just the ubuntu live usb (sdb) and the sda.

does it help somehow ?

doron387

EDIT : 
S O L V E D !!!
well, you know how it is, no patience....
i gave a bet which partition in my sda is the swap one (4 gb partition, marked in gparted as unknown fs)
i reformatted it as linux-swap and rebooted easily back to my beautifull beloved UBUNTU os.
thanks guys.
doron387

---

