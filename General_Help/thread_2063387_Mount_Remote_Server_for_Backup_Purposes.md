---
title: "Mount Remote Server for Backup Purposes"
date: 2012-09-26
forum: General Help
---

### Post by ndstate on 2012-09-26
Hello,

I have a remote Ubuntu server.  I would like my Ubuntu laptop to be able to mount that locally.  This was my backup systems that run on my laptop would also be able to backup the remote Ubuntu server (whenever I have it mounted).

What would be the best approach to doing something like this, FUSE?  It would be great to be able to see the remote server in nautilius so the backup programs on my computer would be able to see the server.

Perhaps there is a better way?  Either way, when I searched for a solution I have not seen anything that can help me.

Thanks!
Brian

---

### Post by Rexilion on 2012-09-27
I always try to avoid mounting as the plague under Linux (especially FUSE!). Since mounts get indefinitly stuck when the network goes down. Causing your backups to stall/fail/hang indefinitly.

If you want to reliably backup to remote servers, I suggest you use rsync. Install it as a server daemon on your server and let the client use it as a client (maybe trough grsync?).

You can also use it over SSH, in that way you don't have to configure an rsync server at all! Since you are using openssh as a server and the ssh shell as a client.

And finally, use cron to run the rsync client. If anything goes wrong, it will just try an hour (or day, or week) later.

---

### Post by ndstate on 2012-10-12
Thanks for the suggestion!

Brian

---

### Post by gregintexas on 2012-10-13
I wouldn't be afraid of fuse mounting. I've used it for years. My laptop has Ubuntu and my servers, all over the world, run whatever Linux the customer uses. All I have to do is "Connect to Server" from the menu (and bookmark it if I'm gonna go to it a lot). Fill in the IP, authentication credentials and Nautilus uses it as a local drive. You can edit or do whatever. It's one of the best things about Linux on the desktop.

That said, I wouldn't do backups that way either. Rsync is the way to go on that. It's like having your own Carbonite or something. Great utility.

He's also right about the network going down ... that's why you'd use rsync for unattended stuff. But when you are there ... nothing wrong with fuse mounting!

IMHO, of course.

G

---

### Post by Rexilion on 2012-10-13
You are right about FUSE boing ok for mounting. But I stumbled on issue's which are apparently related to the limitations of implementing SMB in FUSE. E.g. when moving large files and I also had it SIGABRT on my many times.

Furthermore, rsync uses a delta sync method which is not possible with SMB (only under very specific circumstances though...).

---

### Post by gregintexas on 2012-10-13
Yea, I'd have to say I almost always try to avoid moving large files. The reason is that it's mostly not practical, though. I've never had the abort problem. I almost always attempt to do a "wget" from the server or something similar to move a large file. Recently, I had to get VMWare server onto a server. VMWare will simply not allow you to get the file from the server (at least not an Ubuntu server with no desktop environment). I even attempted with Lynx, to no avail. I had to upload it via fuse and it took forever! Most ISP's restrict the speed of your uploads to the point where it's impractical, so that's probably why I never ran into that particular problem. I never EVEN thought to upload the file with rsync ... you can bet I'll be more "thoughtful" next time. Thanks, man!

---

