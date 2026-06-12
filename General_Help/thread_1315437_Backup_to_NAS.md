---
title: "Backup to NAS"
date: 2009-11-05
forum: General Help
---

### Post by grumpyoldgit on 2009-11-05
I have to admit that I am new to Ubuntu so this may be blindingly obvious.

I have set up 9.10 on a clean disk. There is no data on it at all.
I have an external drive on a USB cable where I keep my docs and pics.
I also have a NAS which consists of Freenas on an old Dell where I keep all my MP3s.
I can see the NAS under Places and Rhythymbox can happily see the NAS and can play my mp3s. I can manually pick up files and drop them into a directory on the NAS with no problems.
However, none of the backup programs I have installed can see the NAS at all.
I have tried Luckybackup and Back in Time.
Mounting the NAS also does not make it visible.
I am not sure what to do next.

---

### Post by tdoyle on 2010-03-13
Not sure 'cus I'm a newbie too, but this might help:

1)  Open terminal window

2)  sudo gedit  /etc/nsswitch.conf

3)  Find line beginning "hosts:"

4)  After "files" but before "dns" phrase, add "wins"

With someone's help I did this because the Ubuntu system could not see my NAS if I referenced it by host name.  I could only reference it by IP address on my local network.  After adding the "wins" parameter as described, it causes Ubuntu to check the windows file system to find a host name before it requests it from a domain name server.  (If it requests from the dns, it doesn't know anything about your local hosts, so it fails.)

Good luck, hope it helps.

---

### Post by joberly on 2010-03-13
Are you trying to use LuckyBackup with the Remote Connections feature? That requires rsync to be running in daemon mode on the server. If this is over local network, I would just mount the share normally, and backup your files as if they were going to the locally mounted directory. IE, normal source -> destination and not the Remote tab.

---

