---
title: "Uninstall WUBI"
date: 2011-09-22
forum: General Help
---

### Post by bobski60 on 2011-09-22
Hi bit of a problem here. I am new to ubutu....love it alot problem is:
Had xprpo and installed wubi, thought it great so I installed the full version from cd.
Lost xppro from boot but thought what the heck I only using 1104 thinking it great.
then all of a sudden after downloading all the updates for 1104. could not boot into anything so I installed again (not being able to find any info...)bad searching or pannic more like it)
Anyway still not being able to get into xppro clicked try ubuntu from the cd to see if I could fix the problem again...nope it just went through install and no chance to uninstall wubi so now I have the system I want and set up how I like on 1104 full, but the wubi x 2 versions are still there and unable to un in stall them.(my hard drive looks so untidy.

On disk utility I see winxpro partition my linux starage then there is a spare partition then a 15 gig ext4, then 1.1 gb swap, 33 gb ext4, 29gb ext4 1.1 gb swap and lastly 1.1 gb swap

all so confusing
winxp is on /dev/sda1
linux storage /dev/sda2
spare  /dev/sda10
15 gb /dev/sda11
1.1 gb    /dev/sda12
33 gb     /devsda6
29 gb     //dev/sda8      (thats where my all things running fav OS is) the one I use.
1.1 swap gb     /dev/sda9
1.1 swap         /dev/sda7

basically I want to get rid of everythibng apart from whats on sda8 as thats my current system.

maybe I was a fool for trying to go straght to Ubuntu and not trian but hey ho I did what I did...
can anyone help me out pls I haver tried to uninstall through Synaptic but it does not give me the choice to uninstall the wubi...
:twisted:     ;)

---

### Post by garvinrick4 on 2011-09-22
WUBI is a folder inside of Windows called Ubuntu it is in C: Drive right next to users. Can open that
folder and uninstall or go to ADD and Remove programs and remove Ubuntu from there.

If you want someone to help you clean up your drive.  Use the Ubuntu install CD and boot off it
and choose Try Ubuntu and when it boots go to a app called "gparted" and open it and take a screen
shot of it and add it to this thread thru the paper clip (attachments) in the Message box. You will
get some help in cleaning up your drive if someone can see it so as to give you proper instructions.

---

### Post by seawolf167 on 2011-09-22
Just to echo what garvinrick4 said; you can think of Wubi kind of like an installed program in running in Windows. You can remove it the same way; by going to Start -> Control Panel -> Programs and Features -> Select the Ubuntu Wubi entry and uninstall it. (In Windows XP and earlier it is Start -> Control Panel -> Add/Remove Programs)

---

### Post by Frogs Hair on 2011-09-22
Remove  Ubuntu from Programs & features in Windows and see the Guide if you have any problems .
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Mark Phelps on 2011-09-22
Just so you know ... Wubi doesn't create any actual partitions; instead, it creates a large file on an existing Windows partition.

So, while removing Wubi will erase the root.disk file and boot entries, it's not going to remove any of those "extra" partitions.

You will have to do that manually.

---

### Post by bobski60 on 2011-09-22
ooooooooooo ok thanks for that advise, I am off to work tonight working teaching English to an English teacher (never done that before but hey ho.....I gotta laugh though me teaching english....strong Derbyshire accent as well lol

So I will get to you tomorrow latish....thanks so far. although I cannot boot into Xppro even though it is there go figure lol

---

### Post by bobski60 on 2011-09-23
Ok here is a screen shot of gparted as it stands.sd1 is where xppro is although I cannot boot into it.sda5 is my storage drive that seems to have shrunk. and the ubuntu that I have configured and using is on sda8 along with another wubi (I think) as in the grub menu there are 2 versions of ubuntu 
sorry am still getting used to this OS so if you need any more please bare with me...(my brain is only so big lol)

---

### Post by garvinrick4 on 2011-09-23
You can delete 7 swap and 9 swap and then make 8 larger to fill up the extended.
sda 10 is at the front of the extended and just big enough for another install sometime.
Being in the front of the extended you do not want to move anything to the left to assume
that space has to move to much data for my taste. Other than that I did not see anything else.
You only need one swap in other words and sda10 is just stuck at the front put a 11.10 oneiric in there
when it is released or any version you choose. Put a Lubuntu in there that might be different for you.
Do not know what you use sda6 or sda11 for? Lot you could do just leave sda10 alone.

---

### Post by bobski60 on 2011-09-23
WELLLLLLLLLLLLLLL I did all that and now I cannotboot into anything. mmmmm
I had to re install xp just to get on line as Ubuntu tries to say I have no partitions and it need to format the whole drive 250GB to install.
Tried installing inside windows and when I log on it says that no root file is defined, please define in the partition something or other...............................
So I try a complete install and it tries to format the whole drive 250GB so I do the alternative meathod and again itsay define the root.
EEEEEEEEEk what to do.
I hate windows and want my Ubuntu  back                   ](*,)

---

### Post by garvinrick4 on 2011-09-23
Well, put in your Live Cd and open gparted and take a screenshot of it using paperclip in the message
box and upload it. Post it here so we can see exactly what you have done. Obviously more than remove 2 extra swaps I imagine.
Lets do it and see what the procedure should be.

---

### Post by bobski60 on 2011-09-23
I know for a fact the hard drive according to windows has 3 partitions one called Linux one called programme and the 3rd is called windowsxp.


BUT saying that according to boot record XP is on C, but according to windows XP is on E....even though I installed XP on C......

And this was nothing as I left it.....
I would give you an image as Disk utility sees it but it will not start up

---

### Post by garvinrick4 on 2011-09-23
> itsay define the root.
/

when you install it is in ext4
check mark the format
and at drop down menu is  / for defining the root.

/ is to linux like C: drive is to windows basically.

---

### Post by garvinrick4 on 2011-09-23
You got one big unallocated that needs a partition table. You can start over and make sda1 for your
windows a Primary partition in NTFS
Make sda2 extended all the way to end of drive.
Now in extended drive will be logical partitions they start at sda5. Gparted will assign partition numbers.
sda5 will be / in ext4
sda6 will be /home in ext4
sda7 will be swap
Make the size you want for windows and /home
sda5 should be about 15 gig tops can be 10 gig if want, I like 15 gig, takes about 4 to 5 gig for /
sda6 as big as you want for your /home
sda7 they say about twice the Ram, but if you have 4 gig of Ram or so I do not have a swap at all.
Do what you want there but do not get carried away with swap.
Here is link:
[HowToPartition - Community Ubuntu Documentation]("https://help.ubuntu.com/community/HowtoPartition")

---

### Post by bobski60 on 2011-09-23
Thanks for that I will try, I DONT care about windows or anything but I would not want to delete or fomat my programme drive as there is alot I want on there, I shall try and see where I get to lol thanks for being tthere, I shall see ya soon, if I am not back on here tommorrow send out the search parties lol

---

### Post by garvinrick4 on 2011-09-23
> **bobski60 said:**
> Thanks for that I will try, I DONT care about windows or anything but I would not want to delete or fomat my programme drive as there is alot I want on there, I shall try and see where I get to lol thanks for being tthere, I shall see ya soon, if I am not back on here tommorrow send out the search parties lol We will all be here and I certainly will. A new partition table is a nice thing,
like a new beginning for your machine. Enjoy working with you keep in touch on this thread so we know
how you are progressing, you are learning a skill set, that is a good thing.

---

### Post by bobski60 on 2011-09-25
OK here goes what I did...
I installed 3 x.
1st 2nd x I installed I did everything that you asked but it would never BOOT up.
3rd time I installed I put the boot from .... on dev/sda and got it booting, although I lost every download I ever made from that drive, only trouble is I could not connect to the internet, I had to put the CD in and get onto the net via the cd. .
everything works ok NOW AS i MANAGED TO SORT IT OUT SOME HOW...No idea how but there you go..... shhhhhhhhhhhhhh dont say anything (touch wood factor and dont say a word the pc is listening)
the only thing is I have an install on the main drive that I would like to get rid of but that can wait, Tanya is getting annoyed with me as I have spent the last 2 days working on this problem lol so will get back this eve.

---

### Post by bobski60 on 2011-09-25
Dont tell the pc anything and DO NOT shout this load lol its running pretty damn great. some slight tweeks needed like how to get into the BIG partition as I do not have permision lol me Its my stupid computer how do I not have permission lol NO seriously. it says in propertys that its the root disk (what!!!??? all 209 GB) 
is it ok to partition this drive via gparted OR? tried to get into lost and found but NO chance on that drive...
Gotta say at this point, this is tremendous learning upward curve, MUCH BETTER than windows innit.

---

