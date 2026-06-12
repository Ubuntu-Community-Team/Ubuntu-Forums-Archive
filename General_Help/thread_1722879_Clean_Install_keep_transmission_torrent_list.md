---
title: "Clean Install keep transmission torrent list"
date: 2011-04-06
forum: General Help
---

### Post by Dr.Fritz on 2011-04-06
Hello, i would really like to install Natty from scratch (i always prefer clean installs than upgrade) , but i am seeding 1500 torrents in transmission most of them sorted in directories, and manually adding them again is a big big pain ... and will take alot of time.

is there a way i can keep the config file or whatever so i dont have to manually add them all? 
so that i just add it in the new transmission folder and all torrents appear?

i assume one way is to keep the /home folder?? but then what if i want a complete clean new install and this is the only thing i want to keep from the old installation??

Thanks in advance guys :)

---

### Post by VastOne on 2011-04-06
> **Dr.Fritz said:**
> Hello, i would really like to install Natty from scratch (i always prefer clean installs than upgrade) , but i am seeding 1500 torrents in transmission most of them sorted in directories, and manually adding them again is a big big pain ... and will take alot of time.

is there a way i can keep the config file or whatever so i dont have to manually add them all? 
so that i just add it in the new transmission folder and all torrents appear?


i assume one way is to keep the /home folder?? but then what if i want a complete clean new install and this is the only thing i want to keep from the old installation??

Thanks in advance guys :)

One of the most critical things a user can do to improve the Linux experience is to have the /home on a separate partition.  It is here that user specs and configs are kept all through out /home, most notably in .config of the /home dir...

Here is a link that shows you how to move /home to a separate partition...

[_[COLOR="Teal"]Check it out here[/COLOR]_]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by VastOne on 2011-04-06
When you have a separate /home area and within your new install in the Ubiquity Gparted process, you must tell the install of that /home area and make sure NOT to tell it to format it...

---

### Post by Dr.Fritz on 2011-04-06
thank you i will probably do that. 
but i dont know how much space should i leave for /home partition . all my music and movie libraries are in separate ntfs partitions of their own and applications and programs are installed in / partition right? so 5-10 GB i guess? 

(my home folder now is something less than 3 GB )

also, if i just copy my home folder to a new partition and go for a new install and point the /home folder to my new /home folder in the installation process will it not work? (i will check the "show hidden files option" copy them as well)  so that i can skip some steps of the guide

---

### Post by VastOne on 2011-04-06
> **Dr.Fritz said:**
> thank you i will probably do that. 
but i dont know how much space should i leave for /home partition . all my music and movie libraries are in separate ntfs partitions of their own and applications and programs are installed in / partition right? so 5-10 GB i guess? 

(my home folder now is something less than 3 GB )

For /home, I would go with 30-40 if you can.. These leaves a lot open for anything you may want to do.. You may never need it, but if you are resizing, now is the time to give yourself more...  When I first started I had a 10 gig, and had to resize after a lot of testing and working.. 

You do what you feel is right, but I would try to give more than you think...

---

### Post by Dr.Fritz on 2011-04-06
ok i will make it 20GB probably, but this question is far more important ;
if i just copy the folder named <username> (which is after the /home) to the new partition  and then point this as home folder in the installation wont it work?

thanks alot by the way :)

---

### Post by Dr.Fritz on 2011-04-06
ok, i copied my <username> folder in the other partition i made specifically for /home , all files seem to have been copied fine except 2 dropbox and acrobat synchronizer hidden files which are not that important. 
i am going to make a coffee download the new beta  and in 10 minutes or so start the installation process , hope everything will work fine..


praying for it to work.. :S

---

### Post by ezsit on 2011-04-06
Inside your /home folder are dot folders (folders that begin with a period . ) and these are hidden and contain settings used by the programs you use. To see them, there is a Show Hidden Files option in the View menu in Nautilus. Look for the ".transmission" folder and zip it up and save it to a removable flash drive. After you have installed your new OS, unzip the .transmission folder inside your /home, possibly overwriting the default one, and you should have all your transmission settings.

---

### Post by Dr.Fritz on 2011-04-06
thanks alot ! i already have done this to be sure, and also the home folder i copied has all the hidden files inside it ( i pressed "show hidden files" before copying) i am using Transmission 2.00b2 (10722),  btw and i hope the transmission version of natty will be ok with this one. anyways gonna try it now and see what happens :) ill let you know

---

### Post by Dr.Fritz on 2011-04-10
well, mostly everything went ok , but transmission wants to partially or completely download around 120 torrents ,why does this happen?


also , is there any fast way to migrate transmission torrent list in deluge?

---

