---
title: "Unused space"
date: 2011-06-07
forum: General Help
---

### Post by shamz_71 on 2011-06-07
I ve been using windows all my life . One fine day i decided to boycott windows and instead use linux. So i googled and found , Ubuntu 11.04 natty narwhal is the latest version so i installed UBuntu 11.04 formating everything.

While installing it asked for partitions , i had no idea what to do.

But in the end ,  i did this

15gb "/"
90 gb home
4 gp swap
and some 80 gb unused.
i thought maybe i  need to make new drive later on so i better leave the some space .
now i realized i cant have 2 home partitions . Now i want to add this unused space to my home partition , without deleting / formating anything. 

Took me days to install this package / that package , install amsn, skype and other general purpose apps in ubuntu. 
So now , i have no plans to repeat wht i did

---

### Post by nothingspecial on 2011-06-07
Why not format it ext4 with gparted label it data and mount it to your home directory. If you have no idea what I'm talking about post back.

---

### Post by wildmanne39 on 2011-06-07
> **shamz_71 said:**
> I ve been using windows all my life . One fine day i decided to boycott windows and instead use linux. So i googled and found , Ubuntu 11.04 natty narwhal is the latest version so i installed UBuntu 11.04 formating everything.

While installing it asked for partitions , i had no idea what to do.

But in the end ,  i did this

15gb "/"
90 gb home
4 gp swap
and some 80 gb unused.
i thought maybe i  need to make new drive later on so i better leave the some space .
now i realized i cant have 2 home partitions . Now i want to add this unused space to my home partition , without deleting / formating anything. 

Took me days to install this package / that package , install amsn, skype and other general purpose apps in ubuntu. 
So now , i have no plans to repeat wht i did
Hi, here is a great guide for resizing partitions.
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html) Make sure you make a copy of your home folder so just in case something goes wrong you will be able to just copy your home folder back. You need to boot from the livecd and use gparted from it, you will need to unmount the partitions that you ae going to resize, it is possible that you will have to reinstall grub after you do this.

---

### Post by Bucky Ball on 2011-06-07
Simple. Boot from a LiveCD (the install disk) and that way all partitions will be unmounted so you can stretch and shrink. Open Gparted from the desktop (while booting from the LiveCD) and away you go. You can delete the /swap if that is between you current /home and the free space and leave 4Gb at the end of the disk for it. Just expand the /home to whatever size you like. 

Incidentally, good planning in the first instance. Well done and welcome. ;)

PS: This won't effect / (root partition) or any of your setup as you are only working with /home and possibly /swap. Good luck. Should be a cinch if you've gotten this far.

---

### Post by shamz_71 on 2011-06-07
> **nothingspecial said:**
> Why not format it ext4 with gparted label it data and mount it to your home directory. If you have no idea what I'm talking about post back.
no idea , but ur advice sounds good

---

### Post by shamz_71 on 2011-06-07
> **Bucky Ball said:**
> Simple. Boot from a LiveCD (the install disk) and that way all partitions will be unmounted so you can stretch and shrink. Open Gparted from the desktop (while booting from the LiveCD) and away you go. You can delete the /swap if that is between you current /home and the free space and leave 4Gb at the end of the disk for it. Just expand the /home to whatever size you like. 

Incidentally, good planning in the first instance. Well done and welcome. ;)

PS: This won't effect / (root partition) or any of your setup as you are only working with /home and possibly /swap. Good luck. Should be a cinch if you've gotten this far.

sounds good , but i dont ve CD. i installed with USB and now its formatted

---

### Post by shamz_71 on 2011-06-07
no problem if the space cant be added to home . 
if it creates another drive , still okay . but no problems.

llike in windows if i had this problem and i cudnt add the space to D drive i wud create another drive E and store all multimedia data there ...but here i cant ve 2 home

---

### Post by shamz_71 on 2011-06-07
> **Bucky Ball said:**
> Simple. Boot from a LiveCD (the install disk) and that way all partitions will be unmounted so you can stretch and shrink. Open Gparted from the desktop (while booting from the LiveCD) and away you go. You can delete the /swap if that is between you current /home and the free space and leave 4Gb at the end of the disk for it. Just expand the /home to whatever size you like. 

Incidentally, good planning in the first instance. Well done and welcome. ;)

PS: This won't effect / (root partition) or any of your setup as you are only working with /home and possibly /swap. Good luck. Should be a cinch if you've gotten this far.
  
thanks for welcoming , btw are you the same famous bucky of youtube?
i dont remember , but i ve heard/seen someone called bucky on youtube

---

### Post by nothingspecial on 2011-06-07
> **shamz_71 said:**
> no idea , but ur advice sounds good

Install gparted from the software center and run it.

Select your unused space and choose to format it ext4.

Give it a lable, this can be anything you like "data" is just a suggestion.

When it's done (don't worry if you don't understand this), do this

Open a terminal and type

```
mkdir ~/data
```

That will make a folder for your new partition in your home.

```
sudo cp /etc/fstab /etc/fstab_bak
```

That just backs up a system file you are about to change just incase you make a mistake.

Then type ```
gksudo gedit /etc/fstab
```

That will open the file so you can change it

At the bottom of the file put this (with changes I'll explain after)

```
LABEL=[COLOR="Red"]data[/COLOR]  /home/[COLOR="Red"]shamz[/COLOR]/data  ext4 defaults 0 0
```

You will have to change data for whatever lable you gave the partition with gparted.

Also change shamz for whatever your username on that computer is.

Save the file and close it.

Then type ```
sudo mount -a
```

Your 80gig partition should now be available in your home folder in a folder called data.

You can lable it whatever you want and call the folder what ever you want.

If you don't understand, just post back.

You only have to do this once, it will be in your home folder every time you restart your computer.

---

### Post by shamz_71 on 2011-06-07
gparted ==  gnomepartitionedition right?

---

### Post by sanderd17 on 2011-06-07
> **shamz_71 said:**
> sounds good , but i dont ve CD. i installed with USB and now its formatted

Any partition changes have to be done from a live CD (or USB, that's the same) to be safe. It's also always best to have some live CD around, just in case something goes wrong.

For the unused space, it depends where it is. You can shrink partitions, enlarge them, delete them, create them or move them.

Deleting, enlarging and creating partitions isn't a lot of work and isn't very dangerous. 

Moving and shrinking is a lot of work because there are a lot of files that have to be moved around. And because of the long time, it can also be dangerous. If something causes the process to interrupt (power problems, you're not patient enough ...) you lose all data on the partitions you are editing.

So if your unallocated space is next to your home (when you look at it from Gparted), I would simply enlarge your home. When an important partition is between your home and your unallocated space (e.g. your root), I would create a new partition on that unallocated space and use that for a dedicated type of files like music or backups. You can mount the partition to any directory (if it contains music, it might be logical to mount it as /home/username/music) so that won't be a big usability problem.

To know how to mount a partition somewhere, there are already good tips given, and you just need to edit your /etc/fstab file. google for it.

EDIT: nothingspecial gave a good tutorian on how to mount a new partition somewhere. Maybe you should know that the editing of the fstab file should be done fro the installed ubuntu, and not anymore from the live CD.

---

### Post by nothingspecial on 2011-06-07
> **shamz_71 said:**
> gparted ==  gnomepartitionedition right?
Might be, I hate it when they rename stuff.

One thing I forgot, after you've done all that, you will find that you don't own the data folder, root will.

To change it, in a terminal type this

```
sudo chown -R shamz:shamz /home/shamz/data
```

Change all three instances of shamz in that command to your username on that computer......

......and change data for whatever you ended up calling the folder/partition.

---

### Post by shamz_71 on 2011-06-07
this is what i get 

farooq@KhalidTank:~$ sudo mount -a
mount: special device LABEL=Multimedia does not exist


my username is : farooq
instead of data i wrote multimedia

---

### Post by shamz_71 on 2011-06-07
oh i am confused now ,
when to write the last commands you posted ?
can u rearange everything?

---

### Post by nothingspecial on 2011-06-07
> **sanderd17 said:**
> Any partition changes have to be done from a live CD (or USB, that's the same) to be safe.

You can format an unmounted partition without the live cd and in this case it would be safer anyway because you will not be able to wipe / and /home which will be mounted.

---

### Post by nothingspecial on 2011-06-07
multimedia or Multimedia

big M or little m

This is important, linux is case sensitive.

The last command is after everything else.

---

### Post by shamz_71 on 2011-06-07
farooq@KhalidTank:~$ gksudo gedit /etc/fstab

(gedit:2222): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.DOPHWV': No such file or directory

(gedit:2222): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

farooq@KhalidTank:~$ sudo mount -a
mount: special device LABEL=Multimedia does not exist


M thingy is fine , ive used Multimedia 
I can see the folder , inmy home.

---

### Post by shamz_71 on 2011-06-07
and also 
in gparted 
sequence is like this

/
home
mutlimedia
swap

can i delete multimedia and enlarge home like what one brother said above

---

### Post by nothingspecial on 2011-06-07
> **shamz_71 said:**
> farooq@KhalidTank:~$ gksudo gedit /etc/fstab

(gedit:2222): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.DOPHWV': No such file or directory

(gedit:2222): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

farooq@KhalidTank:~$ sudo mount -a
mount: special device LABEL=Multimedia does not exist


M thingy is fine , ive used Multimedia 
I can see the folder , inmy home.

Don't worry about the error, that's gedit

Did you label the partition with gparted when you formatted it, you have to right click and choose "add label".

What does the terminal say when you type ```
sudo blkid
```

---

### Post by shamz_71 on 2011-06-07
farooq@KhalidTank:~$ sudo blkid
/dev/sda1: UUID="0f3e4263-5993-4183-b7f2-e960330e2cac" TYPE="ext4" 
/dev/sda5: UUID="5699f05d-b5cc-4521-a252-5c4538b5dcec" TYPE="swap" 
/dev/sda6: UUID="712790d7-756f-4ecc-baac-a1cda3e43423" TYPE="ext4"

---

### Post by nothingspecial on 2011-06-07
Have you formatted the unused space? It doesn't look like you have.

---

### Post by shamz_71 on 2011-06-07
formatted to ext4

---

### Post by nothingspecial on 2011-06-07
Did you label it?

You have a seperate / and /home partitions, right? Because (forgetting swap) I only see 2

---

### Post by sanderd17 on 2011-06-07
> **shamz_71 said:**
> and also 
in gparted 
sequence is like this

/
home
mutlimedia
swap

can i delete multimedia and enlarge home like what one brother said above

yes you can, but you will have to revert the fstab file to the previous and because this time you do edit your home partition, you need to do it from a CD.

But if you already made a partition, it's not worth the trouble.  I would proceed with the hints that nothingspecial gives.

---

### Post by shamz_71 on 2011-06-07
/dev/sda1       ext4            /       14gb        boot(flag)
/dev/sda2      extended              135 gb
    /dev/sda6  ext4            /home  94gb
    NewPartition #1 ext4                 39 gb
    /dev/sda5     linnux-swap          2 gb


this is from gparted

---

### Post by sanderd17 on 2011-06-07
> **shamz_71 said:**
> /dev/sda1       ext4            /       14gb        boot(flag)
/dev/sda2      extended              135 gb
    /dev/sda6  ext4            /home  94gb
    NewPartition #1 ext4                 39 gb
    /dev/sda5     linnux-swap          2 gb


this is from gparted

you have to apply your changes first, otherwise nothing happens

---

### Post by shamz_71 on 2011-06-07
what changes , dont talk at expert level.
wth is changes?

---

### Post by nothingspecial on 2011-06-07
You have to click the big green tick.

In gparted that says apply changes.

---

### Post by nothingspecial on 2011-06-07
Also, I'm still worried about the letter cases.

If you labeled your drive multimedia (with a small m)

and made a folder called Multimedia (with a big M)

the line in fstab _has_ to look like this

```
LABEL=multimedia  /home/farooq/Multimedia  ext4 defaults 0 0
```

the first multimedia in the fstab line is the label, the second is the folder in your home.

---

### Post by shamz_71 on 2011-06-07
OMG , this is the reason i hate troubleshooting.

Its done now , i entered the last comand also.

now i ve folder called lost+found , i want to hide this , its irritating.

can u explain now what has actualy happened?  the space in /home has not increased.
try to make a scenario in windows.

And i say u thank u from botom of my heart for the help.

---

### Post by shamz_71 on 2011-06-07
> **nothingspecial said:**
> Also, I'm still worried about the letter cases.

If you labeled your drive multimedia (with a small m)

and made a folder called Multimedia (with a big M)

the line in fstab _has_ to look like this

```
LABEL=multimedia  /home/farooq/Multimedia  ext4 defaults 0 0
```the first multimedia in the fstab line is the label, the second is the folder in your home.
i used Multimedia whereever multimedia/Multimedia/MULTIMEDIA was required

---

### Post by nothingspecial on 2011-06-07
> **shamz_71 said:**
> OMG , this is the reason i hate troubleshooting.

Its done now , i entered the last comand also.

now i ve folder called lost+found , i want to hide this , its irritating.

can u explain now what has actualy happened?  the space in /home has not increased.
try to make a scenario in windows.

And i say u thank u from botom of my heart for the help.

You can either rename lost and found and put a . infront of it which I would recommend

That will hide it.

Or you can delete it (nothing bad will happen but you might need it one day)

I can't make a scenario for windows because I've never used it but.......

You haven't increased the space in your home partition because the folder Multimedia is a different partition. The extra space (for now) is only available in that folder even though it is in your home.

We can have fun with making links to other folders in your home another time (I think this is enough for today :) )

It is like you have a drive within a drive. All your extra space is in Multimedia, which is both a partition and a folder in your home.

In my music folder I have 8 folders, but only 6 of them are on my internal hard drive. 

```
audio-books  BBC_Proms_2010  Compilations  flac  Grateful Dead  mp3  radio  rips
```

flac and mp3 are both on different external drives mounted just like I showed you

```
LABEL=flac  /home/ns/music/flac ext3 defaults 0 0
LABEL=mp3  /home/ns/music/mp3  ext4 defaults 0 0
```

I have to go get my kids from school now, but I'm glad you got it sorted.

---

### Post by shamz_71 on 2011-06-07
Thanks a ton again , n yea its ENOUGH for today.
i wish/pray your kids dont become a noob like me , instead follow your steps ;)

---

### Post by sanderd17 on 2011-06-07
> **shamz_71 said:**
> 
i wish/pray your kids dont become a noob like me


you don't become a noob, everyone starts as a noob and once you get here, the chance is big that you end as a power user or a master :D

---

### Post by shamz_71 on 2011-06-07
thats the reason i switched to Ubuntu , One day i will be Trained UBuntu user. :)

---

### Post by nothingspecial on 2011-06-07
If you knew my first problem you would LOL :lolflag:

Luckily for me, I think you can only search my last 500 posts. :P

---

### Post by shamz_71 on 2011-06-07
what was your first problem ? 
C'mon lets have a laugh ... maybe lateron i can come with a more silly problem

---

### Post by nothingspecial on 2011-06-07
When I got my first computer, it came with linux on it, but I couldn't get the sound to work.

So I searched the internet and I asked here.

I learned a whole load of commands and really tricky linux stuff but even after 3 weeks, nothing would work.

In the end, it turned out, you have to plug the speakers into the green hole.

:oops::oops::oops:

---

### Post by Bucky Ball on 2011-06-07
Nothingspecial, that's something special! lol.

---

### Post by shamz_71 on 2011-06-07
> **nothingspecial said:**
> When I got my first computer, it came with linux on it, but I couldn't get the sound to work.

So I searched the internet and I asked here.

I learned a whole load of commands and really tricky linux stuff but even after 3 weeks, nothing would work.

In the end, it turned out, you have to plug the speakers into the green hole.

:oops::oops::oops:

lol ! 
Unforunately for me , im on laptop , built in speakers :(
or else i would ve somehow learnt quite a few things

---

### Post by shamz_71 on 2011-07-18
hey guys , i am back with a new problem.
The reason i am posting in this thread is because i think information here on this thread about my partitions will help you all.

I want to install a new OS , Backtrack5. I have only 1 partition and one other partition called 'Multimedia' (see top posts)

---

### Post by Bucky Ball on 2011-07-19
Post a new thread. This post is #41 deep and doesn't have anything to do with your thread title. ;)

You will greatly increase your chances of getting help. Include the relevant info from here. Also, your new problem should be in the 'Other Distros' forum.

---

