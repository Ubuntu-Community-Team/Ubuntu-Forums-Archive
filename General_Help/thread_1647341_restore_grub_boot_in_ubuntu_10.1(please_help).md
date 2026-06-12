---
title: "restore grub boot in ubuntu 10.1(please help)"
date: 2010-12-17
forum: General Help
---

### Post by masoudshr on 2010-12-17
[I][FONT=Arial Black]Hi to all friends

sorry for this post but i search my problem in all threads and i can't solve it

my problem:
i lost my boot grub in my notebook (dell vostro 1320) , also i installed ubuntu along windows 7 , now today when i turn on my notebook it can't boot and restarted . 
then i search in google i found softwares such as :super boot grub and i used it but while i use it has an error "files no found"
also i tried to restore it from live dvd in manual mode 
i used this mode but it didn't work too .
please help me 
I realy confused 
(sorry for my bad english language)

[/FONT][/I]

---

### Post by ryu kun on 2010-12-17
You can follow the instructions explained [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") in Ubuntu Documentation.

If "fdisk -l" command in the instructions does not return any Ubuntu partition, you can try to recover your partitions by using Testdisk. Boot with your Live CD, open Terminal and then use following commands:

1. sudo apt-get install testdisk
2. testdisk

---

