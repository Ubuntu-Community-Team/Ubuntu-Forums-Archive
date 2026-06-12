---
title: "ubuntu seems to hog bandwidth..."
date: 2010-02-01
forum: General Help
---

### Post by rhynes on 2010-02-01
ubuntu 9.10 desktop running as a server basically... I don't know if it's ubuntu or my firewall but whenever I upload/download anything with the ubuntu server, I can't surf the net with my laptop. 

It seems like its hogging all the bandwidth but it doesn't make sense that a single computer could do that. 

my internet connection is 15 megs down but only 1 meg up.

Any ideas?

Thanks.

---

### Post by t4thfavor on 2010-02-01
without QoS rules a machine will take whatever it can get, and you are probably saturating  your upload.

You need a QoS device, or a method to limit dl speed on your linux box.

I would guess a Windows box would do the same.

---

### Post by rhynes on 2010-02-01
I understand that... but for example, i'm doing an upload right now and it's running on average of 60kb/s but I can barely surf on my laptop... 

Going to have to recheck the firewall. this shouldn't be happening.

---

### Post by t4thfavor on 2010-02-01
KB or kb, both are different. Some people don't know that.

60kb is like 6.0KB whereas 60KB is 600kb which is close to your 1024kb upload cap.

---

### Post by LMB on 2010-02-01
[QUOTE=rhynes;8760692]I understand that... but for example, i'm doing an upload right now and it's running on average of 60kb/s but I can barely surf on my laptop... 

Are you sure this is not the very known problem of ADSL and cable modems being incapable of uploading and downloading at the some time?

---

### Post by Vaphell on 2010-02-01
what do you upload? torrent by any chance? do you use a router? That would explain a lot. Saturating upload is not the only thing that can kill the connection, having too many sockets open can do that too - many routers can't handle that and reducing the number of concurrent connections of torrent client is the way to go.

---

