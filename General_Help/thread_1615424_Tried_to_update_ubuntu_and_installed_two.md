---
title: "Tried to update ubuntu and installed two"
date: 2010-11-07
forum: General Help
---

### Post by antturley on 2010-11-07
Hi

I know I know I'm new...1 bean maybe...I had an older version of ubuntu on a disk and intalled it from that one. I finally decided to update it and get to the "Advanced Partition" menu and...yea I know a little but not that much. So I just made the older partition as small as it could go and left it at that. How do I get ride of the other partition of linux? I also have a partition of vista that I want to keep while I learn linux but will delete later. I just want to give this partition of linux the rest of the older one. Later I will just wipe the entire hard drive and install ubuntu over it all. I think its a good learning experience. :grin:

---

### Post by garvinrick4 on 2010-11-07
Open gparted and make a screen shot and attach it in this post.
gparted is System to Administration to gparted: if not there run this in terminal:
```
sudo apt-get install gparted
```
Tell me which one go's and which one stays by sdaX numbers in gparted.

---

### Post by antturley on 2010-11-07
Hi, 

Thanks for the help. Here is the screen shot.

---

### Post by garvinrick4 on 2010-11-07
I imagine you want to get rid of sda5 and move sda7 over to use that space also.
and you also have 2 swaps. How much ram you have? If this is what you want to
do let me know I will tell you the instructions in gparted. Not that hard but always
do backups of Home  when you start to do any disk management. Let me know.

---

### Post by antturley on 2010-11-08
> **garvinrick4 said:**
> I imagine you want to get rid of sda5 and move sda7 over to use that space also.
and you also have 2 swaps. How much ram you have? If this is what you want to
do let me know I will tell you the instructions in gparted. Not that hard but always
do backups of Home  when you start to do any disk management. Let me know.

Yes that's what I want to do everything is backed up on my external. So no problems. Sda5 is ubuntu 9.something and a safe boot.

---

### Post by garvinrick4 on 2010-11-08
Must use a Live Cd (ubuntu install Cd using Try Ubuntu) then go to gparted and open:
Right click on sda5 and delete then hit green apply arrow on top.
#must use live cd to work on system maintinance no mounted partition can be worked on.
## always hit green apply arrow to apply changes in gparted.
Now right click on sda7 and resize to take up sda5's deleted space on drive. (Will take a while because you are moving left, which means the whole system has got to move itself.)
Hit apply arrow. 
 Now when that is done figure out which swap to use. If over 2 gigs or more of RAM just delete them both. (Swap is a scratch disk on drive for use as Ram when you run out of installed RAM.) If not find which swap was with sda7 when installed. (Most likely sda5 and sda6 together) and sda7 and 8 together  Like 99.9 % chance but good for you to look at grub config.
```
gedit /boot/grub/grub.cfg
```When you are through with deleting and moving items. Go into ubuntu install and open terminal:
```
sudo update-grub
```Makes new grub config file and boot menu:

If gparted changes sda7's number to new sda number then we will have to replace grub in mbr
so it looks in right place for grub. User did this same procedure a few days ago and no change.
But one never knows. Not a big procedure.

---

### Post by antturley on 2010-11-10
Thanks for the help! I will give this a shot and let you know how it goes.

---

