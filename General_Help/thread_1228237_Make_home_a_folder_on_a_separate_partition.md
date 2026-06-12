---
title: "Make /home a folder on a separate partition?"
date: 2009-07-31
forum: General Help
---

### Post by SoftwareExplorer on 2009-07-31
Is there a way to mount a partition automatically at startup and then mount a folder in that partition to /home? That way I could have a data partition with out cluttering the virtual /home and the partition wouldn't be cluttered because all you would see is a /home folder in the partition. If you don't get what I'm asking, I'm happy to clarify.

Thanks so much.

---

### Post by styxcoverbnd on 2009-07-31
> **SoftwareExplorer said:**
> Is there a way to mount a partition automatically at startup and then mount a folder in that partition to /home? That way I could have a data partition with out cluttering the virtual /home and the partition wouldn't be cluttered because all you would see is a /home folder in the partition. If you don't get what I'm asking, I'm happy to clarify.

Thanks so much.

I am slightly confused. When you say: "mount a partition automatically at startup" what partition are you talking about? /home?

---

### Post by michy99 on 2009-07-31
Is this what your looking for?

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by SoftwareExplorer on 2009-07-31
I want something like this: 

Partition 1: 8 GB has folders like /boot /bin /etc, but /home data is not on this partition
Partition 2: 500 GB has folders like /home /UbuntuCDimages /DvdRips /Music

I want my computer to, at startup, to look in partition 2's /home for the data to make 'appear' in partition 1's /home folder.  However if I made partition 2 mount in the partition 1's /home, wouldn't partition 2 have folders like /user1 /user2 etc? Instead, I would want those folders to be on partition 2 but in /home/user1 and /home/user2

---

### Post by SoftwareExplorer on 2009-07-31
To put it in more geeky terms:

I want something like this: 

Partition 1, sda7: 8 GB has folders like /boot /bin /etc--basically an ubuntu install, but /home data is not on this partition
Partition 2, label "Data-500", sdb2: 500 GB has folders like /home /UbuntuCDimages /DvdRips /Music

I want my computer to, at startup, to look in sdb2's /home for the data to make 'appear' in sda7's /home folder.  However if I made sdb2 mount in the sda7's /home, wouldn't sdb2 have folders like /user1 /user2 etc? Instead, I would want those folders to be on sdb2 but in /home/user1 and /home/user2

Also, if it makes it more clear, I think that it would mean that sdb2 would be automatically mounted on something like sda7's /media/Data-500

---

### Post by Post Monkeh on 2009-07-31
follow the link posted above - it explains how to set up a seperate /home partition.

---

### Post by michy99 on 2009-07-31
You mount the partition at /home, everything in the partition will be in /home. If you have folders named bob mark and joe, they will appear as /home/bob, /home/mark, and /home/joe.

---

### Post by SoftwareExplorer on 2009-07-31
> **Post Monkeh said:**
> follow the link posted above - it explains how to set up a seperate /home partition.

I don't think it does quite what I want though I could possibly use it to get something to mount at startup. Then maybe linking the two homes together? Would that be safe?

---

### Post by SoftwareExplorer on 2009-07-31
> **michy99 said:**
> You mount the partition at /home, everything in the partition will be in /home. If you have folders named bob mark and joe, they will appear as /home/bob, /home/mark, and /home/joe.

Thats what I thought, but I don't want that, because then other folders like that are in sdb2 like UbuntuCDimages, music, and DVDrips have folders like they are a user or something. Instead of mounting sdb2 in sda7's /home, I would actually be mounted somewhere like /media/Data-500. Then could I make the /home folder on sda7 a symbolic link to /media/Data-500/home/ ? Would that work?

---

### Post by michy99 on 2009-07-31
I think you are making this more complicated than it needs to be. This is how my system is set up: I have the main system on one partition. I have another partition that mounts at /home. I am the only user, so the only folder in that partition is named 'mike' and appears in the filesystem as /home/mike. I have another drive that I mount at /media/storage and use for pictures, documents, movies, music, etc. It has many different folders which all appear under /media/storage. If I wanted, I could mount the storage disk inside my home folder instead, and it would appear at /home/mike/storage.

---

### Post by merlinus on 2009-07-31
You can make another partition for those folders/directories and their contents.

---

### Post by michy99 on 2009-07-31
> **SoftwareExplorer said:**
> Thats what I thought, but I don't want that, because then other folders like that are in sdb2 like UbuntuCDimages, music, and DVDrips have folders like they are a user or something. Instead of mounting sdb2 in sda7's /home, I would actually be mounted somewhere like /media/Data-500. Then could I make the /home folder on sda7 a symbolic link to /media/Data-500/home/ ? Would that work?

It would probably work, just seems a bit convoluted to me.

---

### Post by SoftwareExplorer on 2009-07-31
I got it to work the way I wanted. The rest of this post is a note to myself as much as anyone else.

Booted liveCD.
Opened both where Ubuntu is installed (sda7) and my Data partition (sdb2).
Alt+F2 and ran 'gksudo nautilus'.
Copied 'home' from sda7 to sdb2.
Went to sda7's /etc/fstab and made a backup copy.
Opened sda7's /etc/fstab and added '/dev/sdb2   /media/Data-500 auto   rw,nodev,nosuid  0   2'
Closed gedit.
Unmounted my data partition. Did 'sudo mkdir /media/Data-500' and 'sudo mount /dev/sdb2 /media/Data-500'.
Went back to the gksudoed nautilus and went to /media/Data-500 and right clicked on home -> make link.
Copied the link to sda7.
Renamed '/home' on sda7 to 'home_backup'
Renamed 'Link to home' to 'home'
Restarted into Ubuntu HDD install.
Ctrl + Alt + F2
Logged in.
Ran 'sudo chown -R username:username /home/username' for each user
Ran 'sudo chmod 644 /home/username/.ICEauthority' for each user
Ran 'sudo chmod 644 /home/username/.dmrc for each user
Ran exit
Logged in.

Why I did this: because I don't know how much /home will grow, and how much space my partition I use for storing big files will need in the future. I didn't want to just mount it at /home, because I didn't want folders like downloads in my /home directory.
What I learned:Symbolic Links are a good way to mount any folder inside another and have it available at both spots, as long as you can count on the partition it is on is going to be mounted.

---

### Post by Post Monkeh on 2009-08-01
i'm still quite confused. the link posted for mounting your home directory on its own partition does what you've just said.

or am i missing something and you want not only your home folder on the partition, but also the possibility of adding other folders to the partition to store files without them having to be in any particular users home folder?

---

### Post by SoftwareExplorer on 2009-08-01
> **Post Monkeh said:**
> or am i missing something and you want not only your home folder on the partition, but also the possibility of adding other folders to the partition to store files without them having to be in any particular users home folder?
You got it right there. Especially 'the possibility of adding other folders to the partition to store files without them having to be in any particular users home folder'. But in addition to that, I didn't want various folders  that didn't belong to a user to show up in /home on sda7.
The main reason I didn't want to use different partitions was they are space-inflexible.

---

### Post by Post Monkeh on 2009-08-01
> **SoftwareExplorer said:**
> 
The main reason I didn't want to use different partitions was they are space-inflexible.

while the idea of shareable data folders is good, i can't really say i agree with this last reason.

a seperate "home" partition is no more space inflexible than what you've done.

essentially, all you've done is followed a guide to give yourself a seperate home partition, but adjusted it slightly so that rather than the entire partition being mounted as your home folder, you've organised it so that there is a seperate folder within the partition for you "home" folder, leaving the top level of the partition useable for further folders.


you're still left with the same amount of overall useable space (in fact less when you start adding folders to your data partition), but i do like the idea of having the data folders accessible by everyone.
if you mean that you will be able to extend the partition you've made, you can increase the size of a partition used solely for the home folder just as easily as any other partition.  the guides above allow you to make one partition that solely houses the "home" folder, but using a live cd and gparted, this can be expanded (or indeed shrunk( just as easily as any other partition.

---

### Post by SoftwareExplorer on 2009-08-01
First, I should clarify what you quoted. I didn't want the standard / partition **plus** a /home **plus** an extra data partition. I did like the idea of 'user data' and 'system' separate though. > **Post Monkeh said:**
> while the idea of shareable data folders is good, i can't really say i agree with this last reason.

a seperate "home" partition is no more space inflexible than what you've done.
Unless you are in the habit of having a place where you can have data files that don't belong to anybody and therefore aren't in someone's home folder. Besides, my users folder is usually a lot of small clutter. Why? because stuff defaults to saving there. My shared data folder is usually well organized in contrast. Something like /home/myusername is the to be sorted and /media/Data-500 is the 'already sorted' area.
> **Post Monkeh said:**
> essentially, all you've done is followed a guide to give yourself a seperate home partition, but adjusted it slightly so that rather than the entire partition being mounted as your home folder, you've organised it so that there is a seperate folder within the partition for you "home" folder, leaving the top level of the partition useable for further folders.
Yep, except I used the guide just to know how to do fstab and set permissions. I figured the symlink and partitioning out myself.
> **Post Monkeh said:**
> you're still left with the same amount of overall useable space (in fact less when you start adding folders to your data partition), but i do like the idea of having the data folders accessible by everyone. Empty folders take a negligible amount of space. yes, i have the same amount of space, but it is more usable. Because of the wonders of file systems it is where I need it--automatically.
> **Post Monkeh said:**
> if you mean that you will be able to extend the partition you've made, you can increase the size of a partition used solely for the home folder just as easily as any other partition. The guides above allow you to make one partition that solely houses the "home" folder, but using a live cd and gparted, this can be expanded (or indeed shrunk( just as easily as any other partition.
I know about resizing partitions, it is just that I have heard in rare cases you can loose data, and resizing takes a fairly long time while you're stuck booted up in a liveCD. Instead, having it where you need it automatically and without restarting as a big plus for me. In case your wondering, I shunned My Documents on Windows, too, because of the clutter that builds up.

---

### Post by beast2k on 2009-08-02
I think I smell smoke...

---

### Post by SoftwareExplorer on 2009-08-02
> **beast2k said:**
> I think I smell smoke...

Where is it coming from? (If it's a joke I don't get it yet)

---

### Post by Post Monkeh on 2009-08-02
i never used the my documents folder on windows either, i like to have all my downloads seperate, i think i was just having trouble getting my head round your reasoning, but i get you now. you were going to have a seperate data partition anyway - might as well have "home" and the data on the same partition so you don't have to fanny about with partitions.

i've just been lazy and made a "shared" folder in the top level of "home", but your set up is probably a bit neater because you can make as many folders as you want

---

