---
title: "Linking content of Windows Folders to Ubuntu Folders"
date: 2010-03-31
forum: General Help
---

### Post by gabreal2k on 2010-03-31
Hi, all. I recently tried going back to an old thread of mine (which I cant seem to find now) to post the solution to a problem I was having. 

The Problem was I wanted to open my /home/Pictures folder and have it display the contents of the My Pictures folder in my windows partition. This way I could have ubuntu and xp using the same set of music files, picture files, etc. 

I was having a very hard time understanding how to get from here to there because I'm such a newbie. 

However I have discovered how to do it and I wanted to post it, in hopes it will make things easier for other newbies. So without further ado:

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

*****yes I am aware that there is no /dev/sda4: I just don't know why...lol******

First off I opened a terminal and did: sudo -i, then I did: sudo mkdir /mnt/Media

next I edited /etc/fstab and added this line:

/dev/sda8 /mnt/Media ntfs-3g defaults,umask=022,locale=en_US.UTF-8 0 0

then I saved and closed fstab, and did: mount -a

Then I created links from the various folders in 'Media' to the various folders in '/home'

doing this from a terminal as user (not root):

ln -s /mnt/Media/"My Pictures"/* /home/username/Pictures

ln -s /mnt/Media/"My Music"/* /home/username/Music, etc,etc.

The '/*'  allows me to open [/home/username/Music] and see all the stuff

in [/mnt/Media/"My Music"], as opposed to seeing a link named "My Music"

inside the [/home/username/Music] folder.

The only exception to this was /home/username/Documents. For that I did:

ln -s /mnt/Media/*.*  /home/username/Documents

This allows me to see every TYPE of document in /dev/sda8/Media (windows My Documents folder) without having to see any of the folders (My Music, My Pictures, etc).

I hope this helps.

---

### Post by gabreal2k on 2010-03-31
I have subscribed to this thread so if you get confused/need help, give a shout and I'll try to help you as best I can.

---

