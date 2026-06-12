---
title: "Fix path to /home directory"
date: 2010-02-03
forum: General Help
---

### Post by elektros75 on 2010-02-03
ok, so like many noobs, i thought i'd set up the partitions correctly when i installed ubuntu, with a 15 gig "/" partision and a 45 gig "/home" and a 3.8gig "swap"

i was wrong i somehow misplaced the /home partition, and therefore didn't install it

i found this out about 4 days ago as i was running though  video tutorial and realized i didnt have it setup correctly afterall

so... i did some research and found this site...
[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/#comment-146981](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/#comment-146981)
and in a hurry and very happy that i found something that seemed to work for various people, i deleted the 'now' windows partition and so i had this

sda1 ntfs windows 7
sda2 ntfs data 1
sda3 extended linux with  root and swap
sda4 (was ntfs data 2) ext4 /newhome

however i unmounted the /home folder following the instructions without realizing that i didnt have permissions to mount the /new home partition as it is not in the extended ubuntu 9.04 linux partition and i have no rights to it

so my question is, how do i fix the path to the /home folder (original) in ubuntu so that i can start over and do this correctly (ie; resize the extended partition and add the /newhoe directory/patition to ubuntu)

 i realize that i can use a sudo command before lines to run su commands that are blocked in ubuntu, which is how i screwed up =\

i'm new to this terminal, but i'm not super dumb XD  so i can catch on quick, 

i'd appreciate the help

Patrick

ps.  i cannot use anything in the menu as all links to programs are dead, i can run the add app, but it cannot install as the install folders are "not there"...  i can see them in the terminal so i know my data is there and i can run the live disc to salvage it, but i cannot see it while ubuntu is loaded
note;
i have not restarted the computer and i don't know if this will block ubuntu from restarting either, so i need to fix via terminal, before i can do anything else, like letting the laptop rest :[

once again

HHEELLPPP!!!!!!

---

### Post by warfacegod on 2010-02-03
I asume you used Gparted. You will need to make yourself the owner of the partition. Open a Terminal.

```
sudo chown -R username:usergroup /media/drivename
```

Change username to your username and do the same with usergroup. change drivename to whatever it is listed as in the /media folder. You will probably need to mount the partition first using gparted.

---

### Post by elektros75 on 2010-02-04
thank you!!!

---

### Post by warfacegod on 2010-02-04
Then, I take it, it worked? If so, glad to help and please mark as Sloved under thread tools.

---

### Post by elektros75 on 2010-02-08
well i actually was happy that you replied, unfortunately i deleted that partition (sda4), and resized the ext ubuntu partition to fit the new "newhome" partition there (sda7)

i'm still having problems with it though, i actually posted a new thread, i guess i shoulda posted it here :\

---

### Post by warfacegod on 2010-02-08
Umm.. huh?

---

