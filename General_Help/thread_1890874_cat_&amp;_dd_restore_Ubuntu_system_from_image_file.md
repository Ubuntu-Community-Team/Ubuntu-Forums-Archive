---
title: "cat &amp; dd restore Ubuntu system from image file"
date: 2011-12-04
forum: General Help
---

### Post by makkuro on 2011-12-04
Hi,
I have created a image file using the dd command:[FONT=monospace]
"[/FONT]dd if=/dev/sda1 | split -d -b 3500M - ~/image_sda1.img. " 
so about 4 files have been created img.00 01 02 03 .
now if I try to restore those files in a different ws on a partition called sdb6 
I've started the ws with a ubuntu live cd, then
ubuntu@ubuntu:~/sdc1/Images$ sudo mkdir ~/sdb6
ubuntu@ubuntu:~/sdc1/Images$ sudo mount /dev/sdb6 ~/sdb6
when I try to start the copy with the command
"cat image_sda6.img.* | dd of=~/sdb6"
I get an error message 
"dd: öffne „/dev/sdb6“: Keine Berechtigung (means I got no rights)
then I try
"sudo cat image_sda6.img.* | dd of=~/sdb6"
"dd: öffne „/home/ubuntu/sdb6“: Ist ein Verzeichnis" (means sdb6 is a directoy!)

what is wrong with this restore command?
Thanks a lot for your reply

---

### Post by TeoBigusGeekus on 2011-12-04
I think, someone correct me if I'm wrong, you have to use dd on a whole partition, not a directory.
First join the split image together,
```
cat part1 part2 part3 part4 > wholeimage
```
and then extract it to a partition
```
dd if=wholeimage of=/dev/partition
```

---

### Post by makkuro on 2011-12-04
good idea!
Many Thanks

---

### Post by The Cog on 2011-12-04
Your problem is that the dd part of your command is not running under sudo - only the cat part is running under sudo.
This might work: > 
sudo ls
cat image_sda6.img.* | sudo dd of=~/sdb6 where the ls makes sure that the second sudo doesn't try to ask for a password.

It might be easier to become root for a short while: > sudo su
cat image_sda6.img.* | dd of=~/sdb6
exit

---

