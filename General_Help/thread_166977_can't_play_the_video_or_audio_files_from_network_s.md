---
title: "can't play the video or audio files from network servers!"
date: 2006-04-27
forum: General Help
---

### Post by minhaz4u on 2006-04-27
Hi...
My prob is ...im not able to play any video or audio files located on the network servers...To play it through a player,there is no option to browse network computers...I read somewhere about mounting the files and playing them..But Im verrrry new to this Linux field and have no idea how to do that...
Is there any particular software for this OR do I have to mount the files everytime I want to use?
could someone please help me out... ;)

---

### Post by echo $USER on 2006-04-27
You need to install Samba.  You can find very detailed [instructions here]("http://easylinux.info/wiki/Ubuntu#Samba_Server").

Once you have that running you need to make a mount point for the media you wish to access.  Something like this:
> sudo mkdir /mnt/media
Then change the permission for that folder like this:
> sudo chmod 777 -R /mnt/media
Then mount the share onto your ubuntu filesystem like this:
> sudo mount //192.168.X.X/share /mnt/media

Hope that helps

---

### Post by minhaz4u on 2006-04-27
Thanks a heap for replying this fast...
I tried to install samba like you said..but i get the following error message...
how can I solve it??? ](*,) 

```
scorpio@badboyz:~$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree... Done
samba is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up msttcorefonts (1.2ubuntu2) ...
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--22:20:12--  http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... 193.190.198.97
Connecting to belnet.dl.sourceforge.net|193.190.198.97|:80... connected.
HTTP request sent, awaiting response... 403 Access Denied
22:20:19 ERROR 403: Access Denied.

--22:20:19--  http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Connection timed out.
--22:20:30--  http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving twtelecom.dl.sourceforge.net... failed: Connection timed out.
--22:20:40--  http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving aleron.dl.sourceforge.net... 204.157.3.229
Connecting to aleron.dl.sourceforge.net|204.157.3.229|:80... connected.
HTTP request sent, awaiting response... 403 Access Denied
22:20:47 ERROR 403: Access Denied.

--22:20:47--  http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving cesnet.dl.sourceforge.net... failed: Connection timed out.
--22:20:57--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... 130.59.138.20, 2001:620:0:1b::20
Connecting to switch.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 403 Access Denied
22:21:00 ERROR 403: Access Denied.

andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by echo $USER on 2006-04-27
> samba is already the newest version

Looks like you already have it installed.  Just follow the rest of the directions and post any other errors you get.

---

### Post by echo $USER on 2006-04-27
Look at this [thread]("http://ubuntuforums.org/showthread.php?t=166990") posted a few minutes ago.  They are getting the same error messages as you about connections timing out.  Looks like one of the repo servers is down for maintenance.  You might have to wait awhile before they are back up.

---

### Post by Evlhomer on 2008-04-21
hello,

I am VERY VERY new to this linux game so i appologise in advance for my probably simple question....

I have followed the instructions above and i get this message after typing in...

sudo mkdir /mnt/media

i get....

mkdir: cannot create directory `mnt/media': No such file or directory

Any thoughts would be happily recieved!

---

### Post by sujoy on 2008-04-21
> mkdir: cannot create directory `mnt/media': No such file or directory

that my friend would be /mnt/media, as given in the instruction, you missed the starting "/"

---

