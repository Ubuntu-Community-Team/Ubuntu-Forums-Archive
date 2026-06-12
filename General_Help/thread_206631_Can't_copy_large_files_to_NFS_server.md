---
title: "Can't copy large files to NFS server"
date: 2006-06-30
forum: General Help
---

### Post by Keith_Beef on 2006-06-30
I've got some quite large files (around 600MB to 850MB) that I want to offload from my everyday computer to my NFS server, over a wireless link.

Whether I do this by dragging and dropping in Gnome, or by using the command line, only about 100MB gets copied, before stalling...

I noticed since upgrading to Ubuntu 6.06 that NFS volumes are by default mounted with the "sync" option set (where "async" was the default in the previous release). Could this be the problem?

Which logs should I be looking in to see what's happening? I see nothing in /var/log/messages nor /var/log/syslog.


Beef.

---

### Post by pestilence4hr on 2006-06-30
[QUOTE=Keith_Beef]I've got some quite large files (around 600MB to 850MB) that I want to offload from my everyday computer to my NFS server, **over a wireless link.**
[/QUOTE]

Are you sure it's an nfs issue and not a wireless issue?

---

### Post by Keith_Beef on 2006-06-30
[QUOTE=pestilence4hr]Are you sure it's an nfs issue and not a wireless issue?[/QUOTE]

No, I'm not, which is why I asked which logs I should be looking at.

At the same time as copying, I logged in over ssh to look at the file size and there was no problem that I could see (ssh connection was established promptly, no lag between issuing a command and getting the response).

```
# netstat -in
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
lo    16436 0       411      0      0      0      411      0      0      0 LRU
wlan0  1500 0    113989      0      0      0    87758      0      0      0 BMRU

```

Looks OK to me.


Beef.

---

### Post by pestilence4hr on 2006-06-30
I don't know, and if you are able to connect over ssh that certainly puzzles me.  Try using scp?

---

### Post by Keith_Beef on 2006-06-30
[QUOTE=pestilence4hr]I don't know, and if you are able to connect over ssh that certainly puzzles me.  Try using scp?[/QUOTE]


Good idea, thanks!

Using scp copied the file perfectly well.

So that pretty much rules out any problems with the wireless networking.

Plain old cp and Gnome drag and drop failed, though. I'd like to know why.


Beef.

---

### Post by reclusivemonkey on 2006-06-30
[QUOTE=Keith_Beef]
Using scp copied the file perfectly well.

So that pretty much rules out any problems with the wireless networking.

Plain old cp and Gnome drag and drop failed, though. I'd like to know why.
[/QUOTE]

If scp worked, trying mounting the remote server via SSH in Gnome. I am not entirely sure, but I would assume (always dangerous!) that it will use scp to copy, in which case you may get drag and drop working. Just use "Places --> Connect to Server"

---

