---
title: "truecrypt 6.3a creating hidden partition."
date: 2010-06-13
forum: General Help
---

### Post by alfonz19 on 2010-06-13
Hi,

I'm having some difficulities with truecrypt and cannot figure out what's wrong since this is my first attempt to create hidden encrypted partition.

I'm using ubuntu 9.10 64b with latest 6.3a truecrypt.

After using truecrypt gui (just command truecrypt) I've tried: create volume-->create volumne within a partition/drive-->hidden trucrypt volume --> select some /dev/sdX by my choice --> select aes & sha512 --> password --> and format it.

when formating finished message "wrong ss, swith or wrong superblock of /dev/loop0" appeared. I've got no idea what could I do with it neither know whats program trying to do! Ok formating's done, then if you're trying to mount that partition then I would expect prompt for password, but that did not happen ...

any ideas what could be wrong and why?

EDIT:
ok, sudo mount /dev/loop0 /media/tmp/ also complaint about wrong superblock, but that does not ring any bell since i've got no idea what /dev/loop0 is or is for... Can you help me with that?

EDIT2: 
I've tried another approach also:
sudo truecrypt -t -c
sudo truecrypt -t /dev/sda3 --filesystem=none
but the first command finished creating 100G drive in 1 sec (nonsense) and latter one prints: 
Error: device-mapper: reload ioctl failed: Invalid argument
Command failed

---

### Post by alfonz19 on 2010-06-13
am I getting crazy or is it true that certain tasks cannot be done under linux? I mean whole documentation is written for windows and certain menus are completely missing in gui, and documentation of command-line command is quite poor.

---

### Post by MooPi on 2010-06-13
I don't use truecrypt but this looks to be a good man page:[http://www.irongeek.com/i.php?page=backtrack-3-man/truecrypt]("http://www.irongeek.com/i.php?page=backtrack-3-man/truecrypt")
[http://www.howtoforge.com/truecrypt_data_encryption]("http://www.howtoforge.com/truecrypt_data_encryption")

---

### Post by alfonz19 on 2010-06-14
yes it does and no, it does not.

for example documentation of truecrypt mentions need of creation rescuedisc (and I would like to do so not to have to install truecrypt bootloader). While windows gui allows to create one, linux gui does not and neither does the command line command. Or I just can't see the option listed there.

---

