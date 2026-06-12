---
title: "Folders gone haywire after Ubuntu Tweak"
date: 2010-03-15
forum: General Help
---

### Post by skawars on 2010-03-15
I used ubuntu tweak to change where my default folders are (im dual booted with windows 7 and most of my data is still in them folders), but now after logging back in and going to my home folder ("dan"), all of the original folders have gone, and appeared strangely on the desktop.

I dont know if i accidently messed with some other settings but is there any way I can restore this all back to how it was then have another go at the "tweaking"?

Sorry for the bad description but its the best i can come up with!

---

### Post by wojox on 2010-03-15
Go to Places > Home Folder. Press Ctrl+H to show hidden files. Click on .config folder. Open user-dirs.dirs and make sure it looks like this:

```
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```

You'll need to create a new Dektop folder in Home Folder as well.

---

### Post by skawars on 2010-03-15
it seems as is the only way i can stop my desktop displaying everything in my home folder is disabling "show desktop icons" in ubuntu tweak.

also ive noticed the grub loader is shower more options than it used to. there are 3 different versions of ubuntu generic and recovery mode, as well as the windows 7 options.

i fear i may have fiddled with something i wasnt meant to when a bit drunk the other day, any ideas?

---

### Post by wojox on 2010-03-15
The three versions are probably different kernels.

---

### Post by gabreal2k on 2010-03-29
I'm having a similar problem.

 I deleted /home/g2k/Pictures/ to try and "remake" my Pictures folder as a link to /dev/sda8/My Pictures which failed miserably. (any advice on this???...lol)

However I was able to recreate a directory called Pictures in /home/g2k/ but it wont show up under "places" in the top panel.

I do have a /home/g2k/.config/user-dirs.dirs and it does look like what you posted.

I need to really be able to make /home/g2k/Pictures a link to D:\My Pictures but would like to be able to "see" Pictures folder under places and have it take me to D:\My Pictures without having my D:\ partition showing up on my desktop. (my D:\ partition is labeled Media which adds to the confusion)

If that isn't possible then I need to get the Pictures folder showing up under places again.

Any help with this will be greatly appreciated.

---

### Post by warfacegod on 2010-03-29
> **gabreal2k said:**
> I'm having a similar problem.

 I deleted /home/g2k/Pictures/ to try and "remake" my Pictures folder as a link to /dev/sda8/My Pictures which failed miserably. (any advice on this???...lol)

However I was able to recreate a directory called Pictures in /home/g2k/ but it wont show up under "places" in the top panel.

I do have a /home/g2k/.config/user-dirs.dirs and it does look like what you posted.

I need to really be able to make /home/g2k/Pictures a link to D:\My Pictures but would like to be able to "see" Pictures folder under places and have it take me to D:\My Pictures without having my D:\ partition showing up on my desktop. (my D:\ partition is labeled Media which adds to the confusion)

If that isn't possible then I need to get the Pictures folder showing up under places again.

Any help with this will be greatly appreciated.

Drag and drop the folder into the laeft hand pane in your file browser. You can also click Bookmarks on the top left and select Add Bookmark.

---

### Post by gabreal2k on 2010-03-29
> **warfacegod said:**
> Drag and drop the folder into the laeft hand pane in your file browser. You can also click Bookmarks on the top left and select Add Bookmark.

Ok, now I feel like a complete MORON.

 I've been looking for a way to get that folder back for 8 solid days. 

Ubuntu doesn't work for me because I'M AN IDIOT...lol. Thank you so much, I can't believe it was that simple. 

Maybe you can help with the problem that started it all:

I have (1) 160GB HDD. I am triple booting ubuntu, windows xp, puppy linux.

xp is set up as C:\ 10GB NTFS (labeled: System)  and D:\ 100GBB NTFS (labeled: Media). D:\ is called /dev/sda8 by ubuntu

the My Documents folder has been moved to D:\ along with everything in it: My Pictures, My Music, My Videos...etc etc.

In Ubuntu I want to have /home/g2k/Pictures/ open D:\My Pictures, /home/g2k/Videos open D:\My Videos...etc etc.

BUT.... I DONT WANT a drive called Media showing up on my desktop in ubuntu and i DO NEED read/write permissions for the various folders on said NTFS partition

I tried what c9-3Rror suggested in this thread:

[http://ubuntuforums.org/showthread.php?t=1400759](http://ubuntuforums.org/showthread.php?t=1400759)

but I get a permission denied error.

So what do you think? Am I asking for the impossible or ??????

---

### Post by DanGahan on 2010-03-29
> **gabreal2k said:**
> 
BUT.... I DONT WANT a drive called Media showing up on my desktop in ubuntu 

[http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/](http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/)

The above link should help you remove the HDD icon from the desktop.

---

### Post by gabreal2k on 2010-03-29
Thank you for that, I found that by "mounting" the partition in /mnt that it will allow access to the partition but will "hide" it from the desktop and the "places" tab in the top panel. 

I still haven't figured out how to make /home/username/Pictures open up /mnt/sda8/Media/My Pictures/ yet but maybe it's impossible??? 

Either way I'm sure to find out ;)

---

### Post by warfacegod on 2010-03-29
> **gabreal2k said:**
> Thank you for that, I found that by "mounting" the partition in /mnt that it will allow access to the partition but will "hide" it from the desktop and the "places" tab in the top panel. 

I still haven't figured out how to make /home/username/Pictures open up /mnt/sda8/Media/My Pictures/ yet but maybe it's impossible??? 

Either way I'm sure to find out ;)

Is it displaying an error message of some kind?

---

### Post by gabreal2k on 2010-03-30
No error message perse, but it will do things like create a shortcut called My Music inside /home/g2k/Music/. 

If I use terminal and type: mkdir /mnt/My Pictures= No such directory 'My' 

If: sudo mkdir "/mnt/My Pictures" then I get a empty folder called My Pictures.

so if I then: sudo mkdir /home/g2k/Pictures and then: ln -s "/mnt/My Pictures"  /home/g2k/Pictures/ I get a shortcut called My Pictures inside /home/g2k/Pictures/

If I: ln -s "/mnt/My Pictures/"  /home/g2k/Pictures I get the same thing but the link is broken

If I: ln -s "/mnt/My Pictures/"  /home/g2k/Pictures/ I get another broken link inside thePictures folder.

But I can: ln -s "/mnt/My Pictures"  /home/g2k/ and I will get a 'My Pictures' folder in /home/g2k/ that works perfectly. So all in all I dont know what is happening or why.

---

### Post by warfacegod on 2010-03-30
In the Terminal, there is no such thing as a Space. You need to use \ in place of it.

Example:

My\Documents

---

### Post by gabreal2k on 2010-03-30
The Quotes enable terminal to accept spaces in file names.

 The good news is that I got it working.

 I will post back a little later to spell out what I had to do. Hopefully it will save a noob from having to go through what I have been through...lol.

 I want to thank you for your help warfacegod. I would have NEVER thought of dragging/dropping a folder into the left pane to get it to show up under places. 

I am starting to realize more and more that Ubuntu has a lot of easy use features just like Windows does.

 I don't always need to look for some obscure technical way of doing EVERYTHING, sometimes a simple drag/drop will suffice :D.

One last question: when I post back do I mark my reply with SOLVED or no??

---

### Post by gabreal2k on 2010-03-31
Ok First the background: 1 HDD, 8 partitions.

/DEV/SDA1: NTFS, windows xp 'C:\' labeled System

/DEV/SDA2: FAT32, empty partition for ghost image of 'C:\'

/DEV/SDA3: EXTENDED PARTITION

in my extended partition I have the following sub partitions:

   /DEV/SDA5: EXT4 (Ubuntu root)
   
   /DEV/SDA6: LINUX SWAP

   /DEV/SDA7: EXT4 (Ubuntu home)

   /DEV/SDA8: NTFS, Windows XP 'D:\' labeled Media

   /DEV/SDA9: EXT3 (Puppy Linux)

 First off I opened a terminal and did sudo -i, then I did sudo mkdir /mnt/Media

next I edited /etc/fstab and added this line:

/dev/sda8 /mnt/Media ntfs-3g defaults,umask=022,locale=en_US.UTF-8 0 0

Then I created links from the various folders in 'Media' to the various folders in '/home'

by doing this from a terminal as user:

ln -s /mnt/Media/"My Pictures"/*  /home/username/Pictures

ln -s /mnt/Media/"My Music"/*  /home/username/Music, etc,etc.

The '*' after / allows me to open [/home/username/Music] and see all the stuff 

in[ /mnt/Media/"My Music"], as opposed to seeing a link to [/mnt/Media/"My Music"] 

inside the [/home/username/Music] folder. 

The only exception to this was /home/username/Documents. For that I did:

ln -s /mnt/Media/*.*  /home/username/Documents 

This allows me to see every TYPE of document in /dev/sda8/Media (windows My Documents folder) without having to see any of the folders (My Music, My Pictures, etc).

I'll repost this in my other thread so I can mark it SOLVED.

I hope this helps.

---

### Post by warfacegod on 2010-03-31
> **gabreal2k said:**
> The Quotes enable terminal to accept spaces in file names.

 The good news is that I got it working.

 I will post back a little later to spell out what I had to do. Hopefully it will save a noob from having to go through what I have been through...lol.

 I want to thank you for your help warfacegod. I would have NEVER thought of dragging/dropping a folder into the left pane to get it to show up under places. 

I am starting to realize more and more that Ubuntu has a lot of easy use features just like Windows does.

 I don't always need to look for some obscure technical way of doing EVERYTHING, sometimes a simple drag/drop will suffice :D.

One last question: when I post back do I mark my reply with SOLVED or no??

Glad I could help with something. I wouldn't bother typing solved here. ...Although you might want to apologize to skawars for boosting this thread.:biggrin:

---

### Post by gabreal2k on 2010-03-31
Yeah, my bad. 

My apologies, skawars. I didnt mean to hijack your thread. 

Out of curiosity, if you open /home/username/desktop/ are the missing folders in there?

---

