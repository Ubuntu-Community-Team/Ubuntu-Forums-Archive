---
title: "problems with ushare install"
date: 2011-02-22
forum: General Help
---

### Post by Ditchdoc7893 on 2011-02-22
I posted this in the absolute beginner section hoping to get a response (since I happen to be an absolute beginner and complete newbie at all things linux), and hope I'm not vehemently flogged for reposting this under general help, but I've got a problem that so far I've gotten absolutely no help on.  So please help me.  I want to learn, I've been searching all day for some way to make this work.  Either I'm a dumbass or I can't find anything helpful.  This was copied and pasted from my original cry for help.  Thanks guys.

So in trying to install ushare to be able to play my music  and videos on my xbox 360, I have apparently screwed something up and  now I can't get ushare to work.  I can't even get it uninstall and do a  fresh install.  I used the instructions found here: [https://help.ubuntu.com/community/Xbox360Media](https://help.ubuntu.com/community/Xbox360Media).   I got down to the basic configuration tool.  I entered the name of the  media server, which I called Ubuntu_Media_Server.  Then I identified my  network interface, which was my wireless connection (wlan0).  Then I  told it what directory to share, which was /home/ryan/music and hit  enter.  It did exactly what it was supposed to do which was to restart  ushare.  And then, oops, I forgot, I wanted to be able to see my videos  as well as my music, so I went back and ran the same command that I had  to start the configuration tool which was $ sudo dpkg-reconfigure ushare  and voila, I went back and added in the directory for the video folder  that I wanted to share and hit enter.  Again, it restarted as expected  then it said permission was denied to the video folder.  So I went to  the video folder and gave permission for it to be shared.  So then in  all my illustrious wisdom (which apparently equates to dumbass), I  decided to completely uninstall ushare and do a fresh install.  Then it  wouldn't reinstall, same problem permission denied for the video file.  I  have no idea what to do.  Can someone give me some step by step help on  what to do to just start from scratch and not even include the video  folder.  All I really care about is being able to play my music on the  xbox 360.  Please help, thanks!

---

### Post by Ditchdoc7893 on 2011-02-22
An addendum, when I reinstalled it and then tried to run the basic configuration tool:

sudo dpkg-reconfigure ushare

I get this:

/usr/sbin/dpkg-reconfigure: ushare is broken or not fully installed

I need a step by step from someone who knows more than I do.  Thanks!

---

### Post by nubias on 2011-02-22
[http://www.n00bsonubuntu.net/content/how-to-share-your-pc-files-with-ps3xbox360-ushare/](http://www.n00bsonubuntu.net/content/how-to-share-your-pc-files-with-ps3xbox360-ushare/)

Use the terminal and gedit to configure your ushare server.

---

### Post by Ditchdoc7893 on 2011-02-22
Thanks nubias.  When I start the process listed on the page you gave me, here is what returned in terminal.

ryan@ryan-1005HA:~$ sudo apt-get install ushare
[sudo] password for ryan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ushare
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/51.6kB of archives.
After this operation, 238kB of additional disk space will be used.
Preconfiguring packages ...
/etc/ushare.conf: 22: /home/ryan/Videos: not found
ushare failed to preconfigure, with exit status 2
Selecting previously deselected package ushare.
(Reading database ... 142999 files and directories currently installed.)
Unpacking ushare (from .../ushare_1.1a-0ubuntu5_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up ushare (1.1a-0ubuntu5) ...
/etc/ushare.conf: 22: /home/ryan/Videos: not found
dpkg: error processing ushare (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 ushare
E: Sub-process /usr/bin/dpkg returned an error code (1)
ryan@ryan-1005HA:~$ 


Any ideas how to fix the errors when it is attempting to install?  Thanks!

---

### Post by Ditchdoc7893 on 2011-02-22
Making progress, used the command sudo gedit /etc/ushare.conf and was able to remove the videos folder and so far am working on the install.  Will post if more problems.  I'm sure I'll still run into something.

---

### Post by Ditchdoc7893 on 2011-02-22
And... as promised, problems.  Got ushare to load up finally.  Even got the xbox and ps3 to recognize ushare.  Only problem now is that I can't get the xbox or ps3 to pull up any of the contents of my music folder at all.  No artists, no songs, no nothing.  Any suggestions?  Thanks!

---

### Post by nubias on 2011-02-23
Do you have multiple shares in your ushare.conf?  

Can you post a copy of it here so I can see it.

---

### Post by PratterFak on 2011-02-23
> **Ditchdoc7893 said:**
> And... as promised, problems.  Got ushare to load up finally. ** Even got the xbox and ps3 to recognize ushare.  Only problem now is that I can't get the xbox or ps3 to pull up any of the contents of my music folder at all.  No artists, no songs, no nothing.**  Any suggestions?  Thanks!

I've had this exact problem since 10.04 and nobody seems to have any answers. It was working perfectly on 9.10, but 10.04 and 10.10 not at all.

One thread I made in the past regarding this:
[http://ubuntuforums.org/showthread.php?t=1475635](http://ubuntuforums.org/showthread.php?t=1475635)

Note: Only way I was able to get it to work on 10.04 was install 9.10 with uShare up and working, then update to 10.04 within the OS. However, if you do a fresh install of 10.04 or 10.10, you will not be able to access the files from the Xbox 360 as described above.

---

### Post by Ditchdoc7893 on 2011-02-23
Nubias, hopefully this is what you're needing to see.


# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=uShare

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=wlan0

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=~/Music1

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=

# Enable Web interface (yes/no)
USHARE_ENABLE_WEB=yes

# Enable Telnet control interface (yes/no)
USHARE_ENABLE_TELNET=no

# Use XboX 360 compatibility mode (yes/no)
USHARE_ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
USHARE_ENABLE_DLNA=yes

---

### Post by Ditchdoc7893 on 2011-02-23
I had a brain storm (it might be a brain fart though).  In my music folder, my music is organized into subfolders of each artist.  Could having all the files in separate subfolders be causing a problem with sharing?  Should I maybe try making another folder separate from the music folder and moving all the individual mp3, etc files into another folder and configuring ushare to share that folder?  

Also, another thought, I read on another post that xbox may be trying to get the files using SMB protocol where linux uses NFS to transfer files (found this thread here [http://ubuntuforums.org/showthread.php?t=1689761&highlight=ushare+xbox+360](http://ubuntuforums.org/showthread.php?t=1689761&highlight=ushare+xbox+360)).  Could this be the problem? I don't know about the PS3 and what protocol it uses, but the same problem plagues it also, it can see ushare, but it doesn't see anything else.  Surely there's a fix to this somewhere.

---

### Post by nubias on 2011-02-23
I'm thinking your music directory is wrong, it should be "/home/username/Music1" not "~/Music1"

---

### Post by Ditchdoc7893 on 2011-02-24
Absolutely fabulous nubias!!!  That worked like a charm!  What do you know, I came home from work this morning and saw the post, gave it a shot, and there it was, it worked!  Thanks so much for your help!

---

