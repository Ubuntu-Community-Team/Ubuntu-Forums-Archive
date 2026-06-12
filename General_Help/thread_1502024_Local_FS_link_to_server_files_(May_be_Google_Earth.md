---
title: "Local FS link to server files? (May be Google Earth related)"
date: 2010-06-05
forum: General Help
---

### Post by perryrt on 2010-06-05
This is one of those "I don't understand as much as I think I understand" things, I think.

In my house, I have several Ubuntu computers, one Windows computer and a Ubuntu server. (The Ubuntu computers are all running Karmic Koala). The server is primarily used for media/file serving, and it's been working well for that for almost a year now. Besides various media programs, for general file server/networked drive use, on the Windows side, I have samba running, and on the Ubuntu side, I've been using sftp.

Both work well.

Until this week.

My wife and I are in the market for a house. I've been collating our "possibles" in Google Earth, and what I'd like to do is put the shared kmz file on my server for access by both of us - that way we can both make comments, update it, cross out where we saw the one with the rats, etc, etc....

On the Windows side, the Windows Google earth client "sees" the network/samba share with no problem and this is easy. (I'm using the "Add" --> "Network link" option.)

However, on the Ubuntu side I can't get Google Earth to "see" anything but the local file system on the computer I'm accessing it on. I can't put in the sftp information that allows me to access my network files.

So... then my question becomes this. Is there a another way to get the networked files to appear on my local Ubuntu systems that will be seen by Google Earth?

Or is there a way (like the old command line symbolic link, which I VAGUELY remember being really really useful) to fool Google Earth into thinking it's accessing a local file when it's actually accessing a file on my network?

Or barring that, is there some sort of automated process/shell script that I could get to automatically copy the file from the server to the local drive for use as Google Earth opens, then copy it back to the server after it closes? This would be not as desired for the obvious data loss possibilities, but would work in a pinch, since there's just the two of us using it.

Anyway....your help would be appreciated, as this one's got me stumped.

---

### Post by perryrt on 2010-06-05
Bump - any thoughts?

---

### Post by perryrt on 2010-06-09
One last bump in case anyone has any ideas on this.

---

