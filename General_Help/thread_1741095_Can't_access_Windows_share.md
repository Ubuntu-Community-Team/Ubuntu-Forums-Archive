---
title: "Can't access Windows share"
date: 2011-04-27
forum: General Help
---

### Post by alech on 2011-04-27
Hi
 new to Ubuntu so be patient please :-)
 [B]
Overview[/B]
 I have a couple of Pc's that I have installed Ubuntu 10.10 on, standard installs.  No install issues
 I have a FreeNAS box set up with a windows share for various things pictures, videos, music
 
The files are located in a directory Media, i.e.,  
 \media My Pictures
 \media\My Videos
 \media\My Music
 
 each folder has lots of files and directories, specifically \My Music has >2000 files/top level directories
 
I connect to the FreeNAS share with no issue and can browse all the files, EXCEPT....
 [B]
The issue[/B]
 I cannot access the My Music directory.  Can access Media, see all directories but when I click My Music I get  
 >>The contents could not be displayed.... Sorry, could not display all the contents of "My Music": Invalid argument<<
 
 Any thoughts?
 [B]
What I've found[/B]
 came across bug #217137 and 304345.  No solutions though.  Is this a problem with nautilus (the file manager?) reading SAMBA directories that are too large?
 
 Anyway thoughts greatly appreciated.

---

### Post by bobwyajnr on 2011-05-01
> **alech said:**
> 
What I've found[/B]
 came across bug #217137 and 304345.  No solutions though.  Is this a problem with nautilus (the file manager?) reading SAMBA directories that are too large?
 
 Anyway thoughts greatly appreciated.

I am going to start sounding like a broken record on these forums :) But you can't debug Samba issues with nautilus (in fact it probably introduces quite a few problems itself).

I would recommend trying to mount the music share in terminal using the **mount.cifs** command (it's part of the smbfs package - which you should have installed by default):
```
$ sudo mkdir "/media/My Music"
$ sudo mount.cifs "//FreeNAS(IP or NetBIOS name)/My Music" "/media/My Music" --verbose -o user=????,password=????,domain=WORKGROUP
```
That should probably work (obviously replace the ???? with your sharename user and password -as setup on the FreeNAS box). If that mount command doesn't work - at least you will get some feedback on what is going wrong (verbose flag)!!

Another commandline love winner as far as I am concerned is **smbclient**, try:
```
$ smbclient "//FREENAS IP or NETBOIS NAME/My Music" -U????
```
Enter your FreeNAS share user in place of ???? - you will then be prompted for the share password (just press return if it setup for anonymous login). If this command works you should get commandline FTP-like access to the FreeNAS shared folder and be able to **ls** all the files, etc.

Sorry I'm not too familar with FreeNAS (having not used it myself) - that's FreeBSD based - right? Hopefully that won't be an issue!

Bob

---

### Post by alech on 2011-05-02
Bob

thanks for the reply, I'll give this a whirl tonight

A

---

### Post by alech on 2011-05-02
Bob,

failing on syntax for option 1 (will get there), however option 2 produces the following:

> smb: \> cd Media
smb: \Media\> ls
  .                                   D        0  Thu Mar 24 00:27:52 2011
  ..                                  D        0  Fri Apr 22 11:09:03 2011
  My Videos                           D        0  Sun Apr 24 09:13:01 2011
  My Music                            D        0  Thu Mar 24 08:26:25 2011
  My Pictures                         D        0  Sun Oct 24 21:35:22 2010
  database                            D        0  Mon Apr 11 22:06:57 2011
  MusicBackup                         D        0  Tue Apr 26 00:49:40 2011

        57741 blocks of size 16777216. 11460 blocks available
smb: \Media\> cd "My Music"
smb: \Media\My Music\> ls
Invalid packet length! (65580 bytes).
Receiving SMB: Server stopped responding
Read error: Success listing \Media\My Music\*
Error in dskattr: Read error: Success
smb: \Media\My Music\> 
Any thoughts?

If I try and access this for a Windows machine I can see the files?

Sorry - should have said I can access the other folders in the Media directory

A

---

### Post by alech on 2011-05-02
p { margin-bottom: 0.21cm; }  Bob
 

 an update on option 1 you gave me, sorry this syntax of network naming is still not clear to me, however I did manage a mount using this command:
 

 alec@TopOfStairs-L:~$ sudo mount -t cifs "//192.168.1.94/BackupRoot" "/media/My Music" --verbose -o user=XXXX,password=XXXX,domain=YYYY  
 

 'BackupRoot' is a share that contains Media\My Music
 

 doing this  mount created a My Music icon on the desktop, and using the gui I COULD navigate to My Music and it did bring up the files: 2,468 directories.  So … I think I'm solved  - I can access this from XBMC (which was the aim)
 

 But – any ideas what the issue is?  Also if I could extend the question (Unix 101 I'm sure) what is the name of my freenas server, its  a bit base to use //192.168.1.2 and //freenas does not work
 

 cheers
 A

---

### Post by bobwyajnr on 2011-05-02
> **alech said:**
> Bob,

failing on syntax for option 1 (will get there), however option 2 produces the following:

Any thoughts?

If I try and access this for a Windows machine I can see the files?

Sorry - should have said I can access the other folders in the Media directory

A

@ **alech**

I have been corrected! Accessing Samba shares via nautilus (smb://) and smbclient both use a userspace [GVFS]("http://en.wikipedia.org/wiki/GVFS") mount. **mount.cifs** uses a different mechanism. I always (personally) prefer to use mount.cifs - it's been more reliable for me!

Hmmm. So the directory listing is > 65535/64Kbytes and that's causing the Smbclient to fall over. That's obviously why you don't see anything in Nautilus for that folder...

Perhaps it's an issue with the FreeNAS box sending out a packet larger than Smbclient allows... Perhaps fiddling with these variables (from the **smbclient** man page) might help:
```

       iosize <bytes>
           When sending or receiving files, smbclient uses an internal memory buffer by default of size 64512 bytes. This command allows this size to be
           set to any range between 16384 (0x4000) bytes and 16776960 (0xFFFF00) bytes. Larger sizes may mean more efficient data transfer as smbclient
           will try and use the most efficient read and write calls for the connected server.
```
```
-b|--send-buffer buffersize
           This option changes the transmit/send buffer size when getting or putting a file from/to the server. The default is 65520 bytes. Setting this
           value smaller (to 1200 bytes) has been observed to speed up file transfers to and from a Win9x server.

```
I tried the latter one (which has no specified limit) and I was able to specify 102400 when hooking into my flatmate's Samba server...

One really useful bit of info to help you solve this puzzle would be to install **Wireshark** (a highly educational tool!!) from the Ubuntu repositories. This lets you snoop on LAN/network traffic. Its got a great interface and is real easy to use... Run it as root and set the network card (on your client machine), filter on **smb** traffic. I bet you will find that the really big (TOO BIG!!) packet simply contains a plain listing of the Music directory...

I tend to use static IP addresses for all my gear (doled out by MAC address). NetBIOS name resolution is pretty crap at the best of times... (Do you want stuff to look 'neat' or to actually work :P )

Bob

---

