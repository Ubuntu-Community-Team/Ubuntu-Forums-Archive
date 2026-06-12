---
title: "new to ubuntu - lost all free disk space last night - dont know why!?"
date: 2012-01-08
forum: General Help
---

### Post by infinitegeometry on 2012-01-08
hey all. so ive been pretty new to ubuntu. my friend gave me this 'loaner' computer when my other one crashed so im still learning as i go and havent had any problems up until last night. I have an Asus EEE PC. It normally doesnt have much free disk space as it is, around 2.5gb when its clean, so I move all of my stuff to an external. But last night randomly when i was deleting things from the computer, it wouldnt change the disk space. I tried doing a nautilus trash dump, and it seemed to free up a gb, but when i checked it again today, im down to 0 free bytes. Please help me out. this is my only computer and its something i need to continue to use for my artwork.

---

### Post by snowpine on 2012-01-08
Welcome to the forums! How large is your hard drive? (15gb is the recommended minimum for Ubuntu.)

Ubuntu includes a Disk Usage Analyzer utility that will show you which files/folders are using the most space. That's a good place to start, good luck! :)

---

### Post by infinitegeometry on 2012-01-08
how do i check that?! (sorry im really new to the linux platform)

---

### Post by snowpine on 2012-01-08
Assuming you're using the current 11.10 Ubuntu release, all you have to do is press the Super (or Windows) key, then you can search through the applications installed on your system. 

Two really useful applications in your situation are the System Monitor (gnome-system-monitor) and Disk Usage Analyzer (baobab).

If you aren't using Ubuntu 11.10 then tell us what you are using.

---

### Post by infinitegeometry on 2012-01-08
i checked disk utility (idk if thats it) -- 4.0 GB Hard Disk (ATA ASUS-Phison SSD) & a 16 GB Hard Disk (ATA ASUS-Phison SSD)

and than my 1 TB external hard drive

---

### Post by infinitegeometry on 2012-01-08
ubuntu 10.04

---

### Post by snowpine on 2012-01-08
> **infinitegeometry said:**
> i checked disk utility (idk if thats it) -- 4.0 GB Hard Disk (ATA ASUS-Phison SSD) & a 16 GB Hard Disk (ATA ASUS-Phison SSD)

and than my 1 TB external hard drive

If you installed Ubuntu to the 4gb drive, that would explain why it's full. :)

---

### Post by infinitegeometry on 2012-01-08
see... i didnt install it though. I got this computer given to me as a loaner, so i have no clue where he installed it. Is there a way I can check!? thanks so much for helping too btw...

---

### Post by snowpine on 2012-01-08
You can use the System Monitor and Disk Usage Analyzer, as I suggested above.

If it's not your computer, then obviously you should get on board with the computer's owner before you make any changes. :)

---

### Post by infinitegeometry on 2012-01-08
see thats another problem, he went MIA.. and i havent been able to reach him since. so idk...

ok so i checked system monitor -- my system status says i have 11.4 GB free of available disk space

but when i check the file systems in system monitor -- the /dev/sda2 (the 3.7 GB drive) shows 0 bytes free


??? im so confused...arghhh

---

### Post by snowpine on 2012-01-08
My interpretation of those number is that your 4gb is full and your 16gb has plenty of space; do you agree?

My suggestion is to move as many files/documents as you can from the 4gb to the 16gb. (The 16gb should appear under your Places menu).

---

### Post by infinitegeometry on 2012-01-08
its not shown. when i open 'places' there is only 'computer' and my external... the other drive isnt shown there -- i open computer and file system shows 0 bytes free

---

### Post by infinitegeometry on 2012-01-08
the other drive (the one showing 11.4 gb free) is a /usr directory... idk if that makes a difference

---

### Post by snowpine on 2012-01-08
> **infinitegeometry said:**
> its not shown. when i open 'places' there is only 'computer' and my external... the other drive isnt shown there -- i open computer and file system shows 0 bytes free

Then try moving some files to your external. You are going to have to move or delete some files no matter what. :)

---

### Post by snowpine on 2012-01-08
> **infinitegeometry said:**
> the other drive (the one showing 11.4 gb free) is a /usr directory... idk if that makes a difference

That's an unusual, but smart, way to do it. It sounds like your friend is pretty good with Linux. :)

---

### Post by JRV on 2012-01-08
Try this:
```

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

```

Look at my tutorial for localepurge here:
[http://ubuntuforums.org/showthread.php?t=1867813](http://ubuntuforums.org/showthread.php?t=1867813)

Next install ubuntu-tweak:
```

sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak

```
Run ubuntu-tweak and use the janitor to free up more space.

Search the forums for information on how to move your /home to the 16 gig drive.

---

### Post by snowpine on 2012-01-08
JRV has good suggestions above, if it is your computer.

Since it is not your computer I'm assuming you don't want to touch anything outside of your personal documents/files in your /home folder, is that correct?

---

### Post by infinitegeometry on 2012-01-08
im still really confused though... cuz i dont have any documents, photos, music on this computer... everything is already on my external... and idk what else i could potentially move to the /usr directory without messing up things

so confused :(

---

### Post by snowpine on 2012-01-08
> **infinitegeometry said:**
> im still really confused though... cuz i dont have any documents, photos, music on this computer... everything is already on my external... and idk what else i could potentially move to the /usr directory without messing up things

so confused :(

At the risk of sounding like a broken record, the Disk Usage Analyzer (baobab) will help you find the biggest files/folders, so you can delete them or move them to your external drive.

**Never** move anything to /usr (or delete/move/rename anything in /usr). The only folder you ever need to worry about is your /home folder. Everything else is a system file, don't touch it!

Do you have permission from the computer's owner to use "sudo" to perform system administration tasks as "root"? Do you have permission to install software, change the software sources, alter the partitioning scheme, reinstall the OS, etc.? Personally I would be very upset if I loaned a computer to someone and they did these things, but I don't know what deal you made with your friend.

---

### Post by infinitegeometry on 2012-01-08
i honestly dont think it matters if i were to delete anything from this. he gave it to me knowing i was going to use it. and the fact that he hasnt contacted me in the past 4 months about it, and ive tried to contact him says something i feel. 

i ran what JRV said up until the sudo apt-update and it completed, except it said this at the bottom

'GPG error: [http://deb.torproject.org](http://deb.torproject.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 74A941BA219EC810'

---

### Post by infinitegeometry on 2012-01-08
I'm also not allowed to run anything as a root, which i once was. I get this message 

'unable to copy the user's Xauthorization file'

---

### Post by snowpine on 2012-01-08
> **infinitegeometry said:**
> I'm also not allowed to run anything as a root, which i once was. I get this message 

'unable to copy the user's Xauthorization file'

That's because your 4gb drive is full and you need to delete some files; I can't think of a more plain way to say it. :)

---

### Post by infinitegeometry on 2012-01-08
ok so now that i think back --- last night i had a file that had a 'lock' emblem on it. I couldnt delete it so i had to sodu nautilus it to actually 'remove' it... after that is when problems started and i lost all the disk space

---

### Post by snowpine on 2012-01-08
> **infinitegeometry said:**
> ok so now that i think back --- last night i had a file that had a 'lock' emblem on it. I couldnt delete it so i had to sodu nautilus it to actually 'remove' it... after that is when problems started and i lost all the disk space

Maybe someday someone will invent a magical utility to Analyze your Disk Usage and help you locate the file(s) using up all your space... ;)

In the meantime, here's some further reading material:

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

### Post by infinitegeometry on 2012-01-08
and thats where this all begain... i should still have 2 gb free.. since everything WAS 'deleted' -- thats why im having this issue... idk where this 2 gb came from, and literally, as i said before, overnight it went from 1gb free to 0 bytes... out of thin air!

---

### Post by infinitegeometry on 2012-01-08
ok so check this out... this is what i just found out...

there IS files still in my root trash... how do i delete them!?

'111M	/root/.local/share/Trash/files/STS9 ~ 2007.03.17 - The Boulder Theater - Boulder, CO
128M	/root/.local/share/Trash/files/STS9 ~ 2007.03.15 - The Boulder Theater - Boulder, CO
12K	/media/Elements/.Trash-1000
131M	/root/.local/share/Trash/files/STS9 ~ 2007.03.13 - The Boulder Theater - Boulder, CO
131M	/root/.local/share/Trash/files/STS9 ~ 2007.03.14 - The Boulder Theater - Boulder, CO
133M	/root/.local/share/Trash/files/STS9 ~ 2007.03.16 - The Boulder Theater - Boulder, CO
1.6G	/root/.local/share/Trash
1.6G	/root/.local/share/Trash/files
16K	/home/ghost/.local/share/Trash
4.0K	/home/ghost/.local/share/Trash/expunged
4.0K	/home/ghost/.local/share/Trash/files
4.0K	/home/ghost/.local/share/Trash/info
4.0K	/media/Elements/.Trash-1000/expunged
4.0K	/media/Elements/.Trash-1000/files
4.0K	/media/Elements/.Trash-1000/info
4.0K	/root/.local/share/Trash/files/2007 Boulder Theater
56K	/root/.local/share/Trash/info
63M	/root/.local/share/Trash/files/Mount Kimbie - Crooks & Lovers
64M	/root/.local/share/Trash/files/The Notorious B.I.G. - Ready To Die
'

---

### Post by snowpine on 2012-01-08
I love STS9 so I'll give you good instructions. :)

1. Delete some files in your /home folder and empty the trash.

Now that your disk is not completely full you can (hopefully) use sudo again. :)

2. Read the chapter "trash folders not empty" in [the official Ubuntu.com help pages ]("https://help.ubuntu.com/community/RecoverLostDiskSpace#Trash_Folders_Not_Empty")that I linked to previously.

---

### Post by infinitegeometry on 2012-01-08
theres nothing in my /home folder though... everything HAS been 'deleted' which is what this issue is.... WTF! this is making me so mad... its like i cant access the root trash folder, which has the files which i need to delete to even access it... simply cuz root wont open because there is 0 bytes free

---

### Post by infinitegeometry on 2012-01-08
i ran 'gksudo nautilus' last night in which i thought i deleted the files... but it didnt happen, and no i cant even run that, since theres not enough bytes free to do so...

ahhhhh!!! im like freaking out! this is pissing me off! it contradicts itself :(:(:(:(:(

---

### Post by xyzzyman on 2012-01-08
When you deleted files using gksudo nautilus you just moved them to root's trash. Can you get to a terminal? Ctrl-Alt-F1? (Ctrl-alt-F7 will bring you back into your GUI)

---

### Post by snowpine on 2012-01-08
You have to delete some files from your /home to make space, there is really no other way to say it. :)

Use the Disk Usage Analyzer and choose the Scan Home option, hopefully you'll find some hidden files you can delete to make space. 

15gb is the [recommended minimum ]("https://help.ubuntu.com/community/Installation/SystemRequirements")disk size for Ubuntu, but your friend tried to install it in 4gb for some reason... this means you need to be incredibly careful with what you download/install/copy onto the drive to keep it from filling up; I really recommend using your external drive for music/videos/photos/documents.

---

### Post by infinitegeometry on 2012-01-08
ok i deleted some things.. now what... i have 36mb.. and can access root (or atleast potentially can) -- it no longer says i dont have enough bytes... how do i go into root with sudo and delete the trash???

---

### Post by infinitegeometry on 2012-01-08
ahhhhh WTF! i just checked it again, and im down to 8kb... wtf is going on!?

---

### Post by snowpine on 2012-01-08
> **infinitegeometry said:**
> ok i deleted some things.. now what... i have 36mb.. and can access root (or atleast potentially can) -- it no longer says i dont have enough bytes... how do i go into root with sudo and delete the trash???

I already told you how to delete root trash; it hurts my feelings that you do not read the advice I give you. :(

[For the third time]("https://help.ubuntu.com/community/RecoverLostDiskSpace#Trash_Folders_Not_Empty").

---

### Post by snowpine on 2012-01-08
> **infinitegeometry said:**
> ahhhhh WTF! i just checked it again, and im down to 8kb... wtf is going on!?

You have only 4gb and the recommended is 15gb...

---

### Post by infinitegeometry on 2012-01-08
is there a way i can just do a full system restore?!

---

### Post by infinitegeometry on 2012-01-08
NEVERMIND!!! problem was fixed... i restarted my computer.. and it gave me 1.1gb free, than i went into gksudo nautilus and got into /root/Trash and permanently deleted the files. THANK YOU SO MUCH!!! ahhh finally

seriously, thanks for bearing with me on this. so much appreciaton... also, you into sts9? i have the 5 night run from atlanta from this past NYE. I was at all 5 shows, so if you want them, let me know

blessings!

---

### Post by snowpine on 2012-01-08
YAY!

I saw sound tribe a couple of times when I lived in California, fun times. :)

---

