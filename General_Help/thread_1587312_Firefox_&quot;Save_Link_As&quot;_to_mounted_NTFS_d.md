---
title: "Firefox &quot;Save Link As&quot; to mounted NTFS drive fails"
date: 2010-10-03
forum: General Help
---

### Post by transporter_ii on 2010-10-03
Didn't find anything on google on this. Windows machine is encoding movie files. I'm using HFS (HTTP File Server) to download to my Ubuntu machine (10.04LTS), which doubles as a UPnP media server running twonkymedia.

Firefox click and save = works.
Firefox click and "save link as" (to my home folder) = works
Firefox click and "save link as" (to an NTFS mounted 1.5 TB HD) = A file saves immediately, with the right file name, that is 0k in size and that's it. Game over man.

So I'm having to save it to my home folder and then move it from within Linux.

Just wondering if this is a known limitation in Linux of some sort or I have stumbled on a bug.

This is not a huge deal, but more of just wondering what is up.

Thanks,

---

### Post by andrewthomas on 2010-10-03
Do you have ntfs-3g installed?

Is the partition mounted as read-only?

---

### Post by lovinglinux on 2010-10-03
Have you tried a different browser to see if it is a Firefox issue or not?

Also check [this thread]("http://ubuntuforums.org/showthread.php?t=1553837") about some issues with Apparmor.

---

### Post by transporter_ii on 2010-10-03
Drive is not mounted Read Only. My install was pretty much default. Is ntfs-3g used by default? I've been using linux for a while now, but I'll admit that question threw me.

Not sure why I didn't think of testing using Chrome. Here are my test results:

Tested Firefox and Google Chrome using the same .mp4 file.

Firefox = fail
Chrome = works

I must have stumbled upon some bug with Firefox.

But if chrome works, I can download the file right where I want it and save the time of moving it to the mounted drive.

Thanks guys.

---

