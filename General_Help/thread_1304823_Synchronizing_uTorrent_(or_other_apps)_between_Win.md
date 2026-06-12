---
title: "Synchronizing uTorrent (or other apps) between Windows and Ubuntu dual-boots"
date: 2009-10-29
forum: General Help
---

### Post by cbstryker on 2009-10-29
So I set this up last night and thought it was pretty ingenious, so I thought I'd share what I did.

Here is the scenario: I essentially have Win7 and Ubuntu dual booted (they are on separate HDDs and I don't use GRUB for Windows but that's another matter). What I needed/wanted to do is to synchronize the settings so that I can boot into either OS and have all my settings, new torrents, deleted torrent, etc., to be the same without having to manually copy the uTorrent settings files between each OS drive.

So I use CrossOver Games but the process should be the same in plain Wine or other Wine management programs.

This is what I did:
1. First thing you want to do is set up all your hard drives to automount when Ubuntu starts, this isn't necessary, it just makes you life much easier.
2. Next I created a new "bottle" in CrossOver called uTorrent (call it whatever you want) and install uTorrent.
3. Then go into the configuration for the "uTorrent" bottle or your general Wine settings and and set the Wine drives that you need (the ones uTorrent uses for torrent files and download directories) to be equal to what the drive letters are in Windows. For example I set H: to use the mount point ```
/media/1TB-NTFS
```
that's where my torrents download to.
4. Now run uTorrent inside Wine (this is also assuming you have already ran uTorrent in Windows before).
5. Now goto the settings directory in your windows drive. In vista and Win7 it'll be ```
C:\users\#username#\AppData\Roaming\uTorrent
```
and create a link to the "uTorrent" directory inside the "Roaming" directory.
6. Now copy the link you just created to the same spot but on the "drive_c" of your wine drive, ie:
```
/home/#username#/.cxgames/uTorrent/drive_c/users/crossover/AppData/
```
7. Now you can either delete the existing "uTorrent" directory or just rename it, but after you do, rename the "Link to uTorrent" to just "uTorrent".

That's it!.. I think, I'll double check my system when I get home and post any changes. If anyone is having any troubles, just ask here and I'll try to help.

Also if anyone else has anything to add, I'll plug it in to the first post.

Hope this helps.

---

### Post by krige on 2010-04-25
Thanks for sharing!

Another way to do it, which doesn't require the installation of Crossover, is the following:
[http://www.techenclave.com/guides-and-tutorials/sharing-utorrent-settings-between-windows-linux-130383.html](http://www.techenclave.com/guides-and-tutorials/sharing-utorrent-settings-between-windows-linux-130383.html)

---

