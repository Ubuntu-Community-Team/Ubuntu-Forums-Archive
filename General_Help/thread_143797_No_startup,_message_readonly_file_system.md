---
title: "No startup, message readonly file system"
date: 2006-03-13
forum: General Help
---

### Post by Madrid on 2006-03-13
i work for the passed three months with kubuntu 5.1 modified for two display etc. works well. 

Now i have a big problem, i can not start any more, boots says network fail says no sync with ubuntu clock no random generation and stop at starting the log deamons and goes to text mode. There i see read only file system so the system can not start any more because it can not modify itself.

How can i repair this.

background: this happend after i wanted to format a hd greater than 32GB as a fat32 hd, i could'nt get it formated(on the usb connection), made a mistake to set the mount to "/". i logged out and rebooted and now a can not work any more.

someone an idea to repair or is all lost and have i to install overnew, was a big work to have the system as it was, i did not document what i installed and how to setup the two displays. so answers with repair option are welcome.

---

### Post by totallylost on 2006-03-13
I had a similiar problem i believe-- You can log in still correct? But its only text. no graphics?

If that is the case you can go to the Grub bootloader and select the kubuntu 5.1 listing (should be at the top) and then hit enter and it should boot up normally.

Dont select kubuntu 5.1 troubleshooting (i think thats what its called)

It should work from there.

---

### Post by Madrid on 2006-03-14
at grub i only can select the image of the present kernel de recover mode of the present kernel and this also for the previous kernels and memtest thats al.

The problem is that i can log in as su in the recover image but can not modify nothing it always says read only system so i can not modify the /etc/fstab file.

i tried to start up of a knoppix 4 live, but how to mount from knoppix live the hard disk to modify it it always asks for the su password which i do not have.

how further????

---

