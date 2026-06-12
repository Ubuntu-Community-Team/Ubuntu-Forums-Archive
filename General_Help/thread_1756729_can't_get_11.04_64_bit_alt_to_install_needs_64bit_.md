---
title: "can't get 11.04 64 bit alt to install needs 64bit cd (i think)"
date: 2011-05-12
forum: General Help
---

### Post by foodmonkey on 2011-05-12
install alt 64 bit 11.04 off cd - get through partioning and then asks for another cd - in this case "Ubuntu 11.04+Natty Narwhal_=Release amd64 (20110426)

i'm assuming the alt 64 bit cd requires some sort of vanilla 11.04 64bit cd - where can i download the vanilla version that will work with my alt version.

somebody please help.

love the os and features but getting beaten down like this - maybe the evil empire will win after all

---

### Post by plucky on 2011-05-12
> **foodmonkey said:**
> install alt 64 bit 11.04 off cd - get through partioning and then asks for another cd - in this case "Ubuntu 11.04+Natty Narwhal_=Release amd64 (20110426)

i'm assuming the alt 64 bit cd requires some sort of vanilla 11.04 64bit cd - where can i download the vanilla version that will work with my alt version.

somebody please help.

love the os and features but getting beaten down like this - maybe the evil empire will win after all

The alternative Cd should not need the Live Cd to install the operating system.It just uses a text based installer.

Did you check the MD5SUM of the downloaded iso?

Burn the iso image as slow as possible to CD

Did you run the CD integrity check from the menu list after you booted the CD?

---

### Post by foodmonkey on 2011-05-13
ok - did m5sum on dowload - all good

burned cd a s slow as possible - all good

ls -l on the file so i knew how many blocks

dd if=/dev/cdrom bs=1 count=xxxxxxxx | md5sum

compared with the ubuntu hash site - all good

installed and patitioned sda - /boot 2g /swap 2g raid partition 246g
sdb /swap 4g raid partition 246g

made md0 software raid mount point /

base install went until dialog box asked for media change insert ubuntu-11.04-alternate-amd64_-Release(20110426)

got me scratching my head

any thoughts?

---

