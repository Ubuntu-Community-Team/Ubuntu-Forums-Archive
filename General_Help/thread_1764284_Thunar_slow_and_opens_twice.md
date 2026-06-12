---
title: "Thunar slow and opens twice"
date: 2011-05-21
forum: General Help
---

### Post by James_the_dude on 2011-05-21
So I have never seen this behavior before in thunar, but I am using xubuntu 11.04 freshly installed on my netbook, and when I open a folder for the first time in a session, it can take as much as 30 seconds to open, even if it is a very tiny folder. Then, after it has opened, maybe 15 seconds later, it opens again in a new window. Anyone know why?

---

### Post by GoodPanos on 2011-06-19
I get the same behavior.  Do you get an error message too?

The very first folder I double-click on, takes about 5-10 secs to open and then I get an error message:
"Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

Then after that, opening folders works normal.

---

### Post by Marote on 2011-06-28
I got the same problem too.

Saludos

---

### Post by tigerdog on 2011-07-04
Same trouble here, but only on 11.04.  10.10 and 10.04 worked perfectly.  I also note, after the first open the "Network" entry is not shown in the left-side menu.  If I close Thunar and reopen, "Network" shows up along with the local drives and folders.

Anyone found a cure?  It's pretty annoying.

---

### Post by minktoast on 2011-07-11
Same problem here - has anyone filed a bug?

---

### Post by Toz on 2011-07-11
I believe this is the one: [https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/775117]("https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/775117")

---

### Post by GoodPanos on 2011-10-14
I believe the latest update takes care of this issue.  The one with the latest kernel update, sorry could not remember the version.

After this upgrade, did not experience this behavior any more.

---

### Post by videodrome on 2012-05-28
This bug is still very much alive.

Xubuntu 64 bit 12.04.

I removed gvfs-backends (nothing seemed to depend on it) and Thunar seems to now be working...

---

### Post by lightning slinger on 2012-05-28
> **videodrome said:**
> This bug is still very much alive.

Xubuntu 64 bit 12.04.

I removed gvfs-backends (nothing seemed to depend on it) and Thunar seems to now be working...

Samba uses gvfs-backends but see item #2 on the xubuntu FAQ for a workaround

[http://xubuntu.org/news/faq-1204-precise/](http://xubuntu.org/news/faq-1204-precise/)

Both fixes work just fine!

---

### Post by videodrome on 2012-11-14
Come on please coders here we are again, Xubuntu 12.10 fresh install, had a couple kernel updates come down and now the error is back again!

This bug's being going on for YEARS, then it's fixed, then you guys break it again. 

Frustration.

---

