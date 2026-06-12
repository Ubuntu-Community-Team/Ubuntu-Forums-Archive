---
title: "Two-way synchronisation"
date: 2011-08-28
forum: General Help
---

### Post by andypi on 2011-08-28
I've been looking at trying to synchronise various folders between my laptop and netbook over wifi. I suspect I can use rsync for this, but I'm not quite sure how.

I've seen two guides which seem to have fairly straightforward instructions for doing backups:

[http://a1979shakedown.wordpress.com/2009/01/19/set-up-an-rsync-server-in-ubuntu-for-file-syncing-between-machines/](http://a1979shakedown.wordpress.com/2009/01/19/set-up-an-rsync-server-in-ubuntu-for-file-syncing-between-machines/)

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

But these appear to be unidirectional, however, what I want is to reflect changes in both directions. That means that when I do backups, I need to keep only the newest version of each file. Also I suspect deleting files could be problematic. Is this possible with rsync?

---

### Post by NLinTKO on 2011-08-28
I read that rsync is not able to synchronize between two computers who are visible to each other via a network. I am trying to backup folders from a laptop running Windows to my desktop which runs Ubuntu. I would very much like to hear a solution for this.

---

### Post by papibe on 2011-08-28
> **andypi said:**
> But these appear to be unidirectional...
That's correct. In order to sync you would need to execute two rsync commandas:

To get the lastest changes from the server:
```
$ rsync -av -e ssh server:/path/to/dir/ /local/path/
```
And this to push your changes to the server:
```
$ rsync -av -e ssh /local/path/ server:/path/to/dir/ 
```
If you want exact copies also add the option --delete to erase files in the destination that are not in the source.

BTW, you would need to install OpenSSH in at least one machine (here's is called server).

Hope it helps,
Regards.

---

### Post by dcstar on 2011-08-29
> **andypi said:**
> I've been looking at trying to synchronise various folders between my laptop and netbook over wifi. I suspect I can use rsync for this, but I'm not quite sure how.
........

Install and use the **unison** package, it uses rsync in the backend but simplifies things with a GUI interface.

---

### Post by andypi on 2011-08-29
> **papibe said:**
> That's correct. In order to sync you would need to execute two rsync commandas:

To get the lastest changes from the server:
```
$ rsync -av -e ssh server:/path/to/dir/ /local/path/
```
And this to push your changes to the server:
```
$ rsync -av -e ssh /local/path/ server:/path/to/dir/ 
```
If you want exact copies also add the option --delete to erase files in the destination that are not in the source.


Thanks. Would this not have the problem that if I do a sync from machine A to machine B, if a newer version of file x exists on machine B, then that would be overwritten by the old version on machine A? In addition, if I've erased a file from machine B, would it not then be replaced with the version on machine A, even though I wanted it to be permanently deleted?

> **dcstar said:**
> Install and use the **unison** package, it uses rsync in the backend but simplifies things with a GUI interface.

Thanks, this may do the trick. Just a couple of questions:

1) Can this be scheduled do automatically sync e.g. every night?
2) Is there any way of running this which does not require me to know the IP address of each machine? If IP addresses are dynamically allocated, or the computers are connected to a new network, is there any way they can be configured such that they'll still be able to find each other?

---

### Post by papibe on 2011-08-29
> **andypi said:**
> Thanks. Would this not have the problem that if I do a sync from machine A to machine B, if a newer version of file x exists on machine B, then that would be overwritten by the old version on machine A?
As I wrote the example, yes. But there's more options available. For example this would take care of that concern (running from A):
```
rsync -av --update /local/path/ B:/path/to/dir/
```
> **andypi said:**
> In addition, if I've erased a file from machine B, would it not then be replaced with the version on machine A, even though I wanted it to be permanently deleted?
Using the option --delete would help, but not solve that problem. That is a downfall of rsync, you would have to change the order of the commands to achieve the desired behavior. In other words, after changes, you would have to manually sync first in the correct direction.

For a perfect sync between to working environments, Unison is a much better solution.

Hope it helps.

---

### Post by dcstar on 2011-08-30
> **andypi said:**
> 
.........
1) Can this be scheduled do automatically sync e.g. every night?
2) Is there any way of running this which does not require me to know the IP address of each machine? If IP addresses are dynamically allocated, or the computers are connected to a new network, is there any way they can be configured such that they'll still be able to find each other?

[LIST=1]
[*]Unison has command line functionality, so it should be possible to run it from a cron job.
[*]Finding things with Dynamic IP addresses requires a DNS server to resolve such issues.
[/LIST]

---

### Post by Wayne_V on 2011-08-30
or, just use dropbox: [https://www.dropbox.com/](https://www.dropbox.com/)

It's not suitable for *every* situation but it is, for the most part, idiot proof.

---

### Post by NLinTKO on 2011-08-30
> **andypi said:**
> 1) Can this be scheduled do automatically sync e.g. every night?
Unison does not have a built-in scheduler. If you want a tool with a scheduler you could investigate **luckyBackup**.

---

### Post by andypi on 2011-08-30
Thanks everyone for the suggestions. Unison works a treat. I just need to set up sshkeys (I think) so it can all be done without me knowing about it and I'll be happy.

> **andypi said:**
> 
2) Is there any way of running this which does not require me to know the IP address of each machine? If IP addresses are dynamically allocated, or the computers are connected to a new network, is there any way they can be configured such that they'll still be able to find each other?

This naive question was because I didn't realise I could simply use the hostname to contact a computer on the LAN.

> **Wayne_V said:**
> or, just use dropbox: [https://www.dropbox.com/](https://www.dropbox.com/)

It's not suitable for *every* situation but it is, for the most part, idiot proof.

I already use dropbox, and it is very useful, but I don't want to/can't use it for everything.

Oh and one more thing... there isn't by any chance a project to get Unison running on Android is there? I couldn't find anything. That would be ideal.

Edit: Or is it possible to use Unison when only one of the sync'd computers has Unison installed? I have installed QuickSSHd on my Android phone, which is allowing me to access the SD card from my Ubuntu laptop (but only using ports from 1025 and up), however when I try to run a Unison profile to it, it fails...

Edit2: Hooray! It is very possible to mount the SD card of my (unrooted) phone using sshfs, as long as the SSH server is running on the phone. I can then use Unison to keep everything the way I want it.

---

### Post by hardyfan on 2011-09-09
I use Luckybackup great gui very easy to use with an option of two types of back up or synchronise.

---

