---
title: "SCP question"
date: 2011-05-22
forum: General Help
---

### Post by NR1224 on 2011-05-22
I'm trying to scp a file to a server, from my directory Downloads, the the directory on the server /home/media/xxx/audio. When I tried
 
scp test.torrent [email]xxx@xxxxx.com[/email]:/home/media/xxx/audio, 

I get a permission denied message. When I tried 

scp test.torrent [email]xxx@xxxx.com[/email]:./home, 

which I did to experiment, it apparently copied over, but I can't find it on the server, so...what did I do different, why did it copy, where did it end up, etc...I don't understand scp yet, sorry

---

### Post by tasaif09 on 2011-05-22
scp test.torrent user@host:/home/media/xxx/audio

this likely failed because user does not have permission to write to the /home/media/xxx/audio directory. Check the read/write permissions on the directory, and which user owns it.

scp test.torrent user@host:./home

this scp'd test.torrent onto the host into the user's home directory (.), and named the file home. If you look in "user"'s home directory, you should find a file named home. That home file is actually the torrent file you scp'd, you renamed it along the way.

---

### Post by NR1224 on 2011-05-22
Ok, that was it, thank you!

---

