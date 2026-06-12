---
title: "ntfs-3g hangs and corrupts svn working folder."
date: 2010-07-14
forum: General Help
---

### Post by BlessedGeek on 2010-07-14
This problem started after I moved from ubuntu 9.10 (64bit) dual core to 10.04 (64bit) quad core machine.

On both machines, I have svn working directories in an NTFS partition since I dual boot between Vista and Ubuntu - which gives me the opportunity to work on my projects whether I am on vista or ubuntu.

My fstab entry is very simple:
UUID=62B81CE6B81CBA8D    /media/ntfsdata    ntfs-3g    defaults    0    0

I use either RapidSVN or RabbitVCS.

Whenever I commit those folders to the SVN server(google code), the folders seem to get corrupted. After which a rebuild or a refresh on Eclipse would provoke a 100% use on one of my 4 cpus. It would just hang there and the ntfs partition would not be accessible at all until I killed ntfs-3g process.

Then I would have to boot on vista to repair that partition. The gparted repair utility is USELESS because it cannot spot any partition errors caused by the svn commit.

The dual cpu machine had occasional similar trouble but I never needed to repair it. SVN would not kill the ntfs-3g, but eclipse rebuild project after an svn operation would. I could prevent ntfs-3g hangup by checking off build automatically after a svn operation and close all projects and reopen one at a time to refresh.

A refresh would trigger a rebuild.

On the phenomenally faster quadcore machine, the speed of operations could be too quick for ntfs-3g to handle (may be??). It looks like ntfs-3g is unable to handle high number of files at high speed operations. I use the same ntfs partition to store high volume bulk copy and bulk downloads with no problems - apparently, it is not the problem with high volume of transfer but the high number of files being thrashed back and forth at high speed by eclipse and svn commit.

Does anyone else store their svn working directories on ntfs when developing with Eclipse on ubuntu 10.04?

Further addition:
I need to mention that partition is compressed under ntfs. Perhaps, ntfs-3g is not capable of handling compressed ntfs. I uncompressed them - and during uncompress operation, explorer hung at the folder where I had done the svn commit. I rebooted vista and made a fresh uncompressed copy of those svn working folders and deleted the old copy. I'll wait and see what happens on my next commit using rabbitcvs.

---

### Post by BlessedGeek on 2010-07-21
It is indeed confirmed that NTFS compression caused problems for both my ubuntu 9.10 (Dual core Intel P4) and ubuntu 10.04 (quad core intel) machines, when performing SVN commit operations.

When I used vista to uncompress those svn working directories, and then reboot on ubuntu to perform svn commits, I no longer faced any corruptions or having ntfs-3g pegged at 100% on one of the cpu cores.

Therefore, I conclude that ntfs-3g is not able to perform a completely safe/stable emulation of ntfs operations when operating on an ntfs compressed file/directory.

---

