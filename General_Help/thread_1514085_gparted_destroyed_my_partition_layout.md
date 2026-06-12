---
title: "gparted destroyed my partition layout"
date: 2010-06-20
forum: General Help
---

### Post by macstar on 2010-06-20
i have a BIG problem with gparted. all i wanted to do is to extend one  partition (dev/sda1 - sucess), move several others and create another  one. it was a procedure of 6 steps, the first 2 went smoothly on the 3rd  one gparted just hang up and i had to turn off the notebook. now  gparted wont boot anymore (it will hang up again)

and now the big problem. my data partition is GONE! (according to  gparted its still there but i cant see it on ubuntu)

[img]http://i.imgur.com/OENKl.png[/img]

does anyone know how to fix it?  i havent touched anything after the  failure and im not sure if i should still continue trying it with the  faulty gparted or use some quality software instead (is partition-magic  still arround?) 

please help!!! i need my data back and i need a new partition layout:

it should be like the following:

the dev/sda3 should be accessible again (i have no clue why its not)
and then i just want to create a new partition (extended) 50GB where i  will do my backup on.

if it helps the 50.06GiB non-allocated space was before in front of the  /dev/sda3 partition and i moved it behind it with gparted to get it from  primary into extended area.


i clicked on the partiton and info says the following:

[img]http://i.imgur.com/UNKZk.png[/img]

now, i dont have windows installed anymore. can i run the chdsk command  on ubuntu as well? or simply checking the partition with gparted? 							 							





so any ideas? hope some1 is able to help me out on this.

---

### Post by pbrane on 2010-06-20
Did you happen to save a printout of your original partition table? If you did you can use fdisk to retore the original layout. If you don't have windows anymore you may need to delete the ntfs partition, recreate it and format it to the file system you need. You should try checking the partitions with fdisk to see if that matches gparted.

---

### Post by macstar on 2010-06-20
i didnt save printout. and i dont want to delete that ntfs partition either cause all my data is stored there! 

i just booted windows setup with dvd and it can see that 117GB partition too, says 115GB used, 1.x GB free. so its still there i think.


i guess i have the following option now:

1.moving the 50GB unallocated disk-space to extended area, then creating a new partition there.
2.booting clonezilla live and creating full backup of /dev/sda1 (thats where my ubuntu install is located)
3.starting windows setup from dvd, deleting /dev/sda1, creating new ntfs partition, installing windows on it, booting windows. 
4. run chkdsk /f for that 117.19GiB partition in windows and rebooting twice was gparted suggested.
5. now my dada partition should be fixed.


after that i want to get ubuntu back and remove windows. how to best do that? 
can i just use gparted to delete the ntfs partition and then creating a new ext4 one, then launching clonezilla and restore it there? 

will ubuntu boot then like before?


i think with these steps i can keep all my data. i just hope gparted wont fail again. it doesnt look very stable program to me.

---

### Post by pbrane on 2010-06-20
Before you do all of that try running ***ntfsfix***. It may fix the inconsistencies. YOu can do a *man ntfsfix* and see what you think.

---

### Post by macstar on 2010-06-20
> **pbrane said:**
> Before you do all of that try running ***ntfsfix***. It may fix the inconsistencies. YOu can do a *man ntfsfix* and see what you think.

doesnt work :(

> 
ntfsfix /dev/sda3
Mounting volume... Error opening partition device: Permission denied.
Failed to startup volume: Permission denied.
FAILED
Attempting to correct errors... Error opening partition device: Permission denied.
FAILED
Failed to startup volume: Permission denied.
Volume is corrupt. You should run chkdsk.


---

### Post by yetiman64 on 2010-06-20
> Mounting volume... Error opening partition device: Permission denied
Indicates to me you need to "sudo" the command.

---

### Post by Joe of loath on 2010-06-20
Always back up before resizing/moving partitions. If you don't have windows, you may have to take the disc to a friend who has to be able to repair it.

---

### Post by macstar on 2010-06-20
posting this from my iphone.
installed windows and ... the partition is there :)))) 
that went just as expected. 
now im gonna delete windows partition and restore ubuntu.
hehe i hope that will work too.

---

### Post by macstar on 2010-06-20
bad news here :(

i had to install ubuntu again, as clonezilla did not what i wanted to do, meaning cloning my old ubuntu partition. 
it was doing something, working and pretending to clone the partition for about 17 mins and finished without any obvious error messages, but i just have an empty partition. restore not possible. :(
what a **** poor app :(

and my old ubuntu install is gone :( i hope i can get it that perfect as it was before again. lots of config will be needed. oh well.

after that i wanna DO a backup ofc. but not with clonezilla, that app is just not doing its job properly. 

can someone recommand me any good alternatives?

---

### Post by macstar on 2010-06-20
damn now i cant find the emerald theme anymore i was using before. (you can see it on the screenshots above) how is it called? anyone knows?

---

### Post by macstar on 2010-06-20
nevermind. found it.

---

### Post by megamandos on 2010-06-20
ok i know this isnt helping at all, but what theme are you using? thats really neat looking!

---

### Post by macstar on 2010-06-20
@[megamandos]("http://ubuntuforums.org/member.php?u=1098442")
im using:

- black white 2 neon icons: [http://browse.deviantart.com/?qh=&section=&global=1&q=black+white+neon#/d17mjtu](http://browse.deviantart.com/?qh=&section=&global=1&q=black+white+neon#/d17mjtu)
- 45402-scaled black mod for emerald themer: [http://gnome-look.org/content/show.php/Scaled+Black+Mod?content=45402](http://gnome-look.org/content/show.php/Scaled+Black+Mod?content=45402)
- slickness: [http://browse.deviantart.com/?qh=&section=&global=1&q=slickness#/d1dhhsz](http://browse.deviantart.com/?qh=&section=&global=1&q=slickness#/d1dhhsz)

i hope this helps. if you need any advice installing it, feel free to ask.
i finally managed to reinstall everything as it was before and im very happy now. :lolflag:):P:guitar::popcorn:

---

