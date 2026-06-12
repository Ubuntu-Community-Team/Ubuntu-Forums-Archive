---
title: "Best filesystem for USB harddrive"
date: 2010-02-04
forum: General Help
---

### Post by prince.buster on 2010-02-04
A minor success story that I thought I'd share with you all.

I recently bought a Western Digital 640GB external USB hard drive. It was ****-house, had all these extra security features and windows programs hard coded onto a non-writable flash chip that can't be deleted ...

So I returned the WD and got a Seagate 500GB external hard-drive. Perfect.

I was then faced with the perennial problem of choosing a filesystem. Preferably one that works well in Linux, but still portable. FAT32 isn't much good for anything these days, with size limits and all. NTFS is proprietary and unreadable on Mac OSX. Compatibility problems exist for most other proprietary filesystems, and a whole bunch of the free ones as well.

In the end I chose ext3. "ext3?" I hear you say - you might be surprised. Here are my reasons: For a start, ext3 is certainly the most well supported filesystem in Linux. That goes without saying. Secondly, and not everyone knows this: *there exists open source ext2/3 drivers for both Windows and Mac*. Ext3 is, in fact, just as portable as NTFS - and it is open source (read: free from bull-shite).

My setup is as follows:
[LIST]
[*]One 499GB partition formatted as EXT3
[*]One 1GB partition formatted as FAT32, containing drivers:
[LIST]
[*][MacFUSE]("http://code.google.com/p/macfuse/") + [fuse-ext2]("http://alperakcan.org/?open=projects&project=fuse-ext2") for Mac OSX, and
[*][Ex2Fsd]("http://www.ext2fsd.com/") for Windows.
[/LIST]
[/LIST]
Problem solved!

---

### Post by switch10 on 2010-02-05
Awesome!  Thanks for the info.  I did not know that there were ext3 drivers for mac and windows.  I'm going to reformat my external NTFS hard drive.

---

### Post by HermanAB on 2010-02-05
Howdy,

That setup is good, but your precious data is still not secured.  I use LUKS with NTFS-3g on Linux and FreeOTFE on Windows.

---

### Post by chowder on 2010-05-06
Thanks, been trying to figure out how to format my USB drive so that it can be read by all OS's too!

---

### Post by mstargard on 2011-02-10
The only problem with using ext3 is when you are sharing the drives between systems that have different users, file ownership is maintained.  For example, if I get an external USB drive formated ext3 from a friend, then when I plug it in, the ownership is maintained, and I have no rights to read or write to the drive.

Maintaining ownership is simply annoying on removable media and is standing in the way for me to ditch NTFS.  This is probably a straightforward fix in gnome/kde/devmapper/whatever, but it's not "out of the box" this way.

---

