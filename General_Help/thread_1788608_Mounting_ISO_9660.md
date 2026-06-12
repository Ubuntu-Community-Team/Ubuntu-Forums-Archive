---
title: "Mounting ISO 9660"
date: 2011-06-22
forum: General Help
---

### Post by warmnscsi on 2011-06-22
Hello, I have been googling and troubleshooting this issue for a couple hours and I think it's time to ask for help. I have a dvd that was made as a back up using ISO 9660 and  windows reports that the disc isnt formatted and is empty but linux will report the it's an ISO and has 0mb free.

Can someone help me access the files on this disc? Thanks.

---

### Post by mistyautom on 2011-06-22
I would try:
1. Boot into Ubuntu.
2. Put the DVD into the DVD Rom.
3. Right click on the Iso image and click "Open with archive mounter"

or try:

1. Boot to Ubuntu.
2. Put the DVD into the DVD Rom.
3. Right click on the Iso image and select "Copy"
4. Right click on the desktop and Select "Paste"
5. Once the Iso file has finished transfering to your desktop, right click the Iso file on your Desktop and Select "Open with archive Mounter"
6. A Disk icon should appear on your desktop.  Double click on this to acces your files.

----------------
[http://www.dotdeb.com](http://www.dotdeb.com) is a great place to find deb packages.

---

### Post by warmnscsi on 2011-06-22
Thanks for trying but ubuntu is not recognizing this as a mountable source.

sudo mount /dev/sdr0 doesn't work.

---

### Post by Gyokuro on 2011-06-23
sudo mount -t iso9660 /dev/sdr0 /media

---

### Post by life in color on 2011-06-23
Did you try booting it at startup?

---

### Post by warmnscsi on 2011-06-24
> **Gyokuro said:**
> sudo mount -t iso9660 /devsdr0 /media

Thanks I'll try that when I get home. I'm assuming I would replace "media" with the name of what's on the disc, correct? Unfortunately I don't have any way to even look at the file directory of the disk. I'll try sudo mount -t iso9660 /devsdr0 

The disc doesn't even show up on the desktop or in the computer directory so it acts like I don't even have a disc in the drive. It's not until I open disk utility and click on the disc drive that it gives me some details.

> **life in color said:**
> Did you try booting it at startup?

Um, I was told that it's just a backup of some microsoft .pst files that was made with magicISO. I don't know why he saved it is an ISO. I don't think there's anything in the file structure for it to boot off of but I will give it a shot when I get home.

---

### Post by life in color on 2011-06-25
Well I wonder if GParted could recognize it. Open GParted inside Ubuntu or run the GPartedLiveCD and see if it picks up the DVD.

---

### Post by ClientAlive on 2011-06-25
> **warmnscsi said:**
> Thanks I'll try that when I get home. I'm assuming I would replace "media" with the name of what's on the disc, correct? Unfortunately I don't have any way to even look at the file directory of the disk. I'll try sudo mount -t iso9660 /devsdr0 



> **Gyokuro said:**
> sudo mount -t iso9660 /devsdr0 /media


If I'm not mistaken, that "/media" part is telling it where you want to mount too. I think there are actually three things going on there - each separated by a space. The syntax is commmand -option <type> <source> <mount point>.

Check out the man page for the mount command.

```
man mount
```

Here's a resource that talks about using the mount command too.

[http://linux.about.com/od/commands/l/blcmdl8_mount.htm](http://linux.about.com/od/commands/l/blcmdl8_mount.htm)

But also it says the following so maybe the -t option should not even be necessary. That link (above) seems to say quite a bit about that command though. Might be useful.

> The type iso9660 is the default. If no -t option is given, or if the auto type is specified, the superblock is probed for the filesystem type (adfs, bfs, cramfs, ext, ext2, ext3, hfs, hpfs, iso9660, jfs, minix, ntfs, qnx4, reiserfs, romfs, udf, ufs, vxfs, xfs, xiafs are supported). If this probe fails, mount will try to read the file /etc/filesystems, or, if that does not exist, /proc/filesystems. All of the filesystem types listed there will be tried, except for those that are labeled "nodev"
--------------------

Edit:

Oh, I forgot something. The thing about /media is that it actually is a mount point. I run Ubuntu 10.04 and when I plug any usb device (my 230 gig external for example) it mounts to /media. If you look in root you can see that there really is a /media

```

cd /; ls

```
---------------------

Edit II:

I'm curious - could there be something to do with permissions, or even encryption going on? Just thought I'd mention it.

Here's an excerpt from the wikipedia article on Personal Storage Table

> Password protection can be used to protect the content of the .pst files.[4] However, Microsoft admits that the password adds very little protection, due to the existence of commonly available tools which can remove or simply bypass the password protection.[5] The password to access the table is stored without the first and last XOR CRC-32 integer representation of itself in the .pst file. Outlook checks to make sure that it matches the user-specified password and refuses to operate if there is no match. The data is readable by the libpst project code.

Microsoft (MS) offers three values for the encryption setting: none, compressible, and high.
None the .pst data is stored as plain text.
Compressible the .pst data is encrypted with a byte-substitution cipher with a fixed substitution table.
High (sometimes called "better") encryption is similar to a WWII German Enigma cipher with three fixed rotors.

Note that neither of the two encryption modes uses the user-specified password as any part of the key for the encryption.

[http://en.wikipedia.org/wiki/Personal_Storage_Table#Data_access](http://en.wikipedia.org/wiki/Personal_Storage_Table#Data_access)

---

### Post by Gyokuro on 2011-06-25
ClientAlive: your assumption about the command is correct; please not I have edited my original post due to a missing /; correct syntax should be: sudo mount -t iso9660 /dev/sdr0 /media 	


warmnscsi: I thought about your problem and could it be possible that you have not finished the DVD yet?? It will be good to know which application you used to burn the DVD

---

### Post by ClientAlive on 2011-06-25
> **warmnscsi said:**
> 
. . . I was told that it's just a backup of some microsoft .pst files that was made with magicISO. I don't know why he . . .


Just happened to notice that in the guys post.
------------------------------

Edit:

Funny thing, I thought magicISO was a Windows only program. That would make sense I guess since he's talking about Windows file types being on the disc. Just has me curious what's going on. Someone else who is running Windows burned the disc but he runs Linux?
------------------------------

Edit 2:

If you look at the original post it looks like he's running Windows. Here were telling the guy to run Linux commands? I'm confused now.

---

