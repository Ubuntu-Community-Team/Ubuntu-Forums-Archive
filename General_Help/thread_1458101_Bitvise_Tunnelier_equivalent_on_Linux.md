---
title: "Bitvise Tunnelier equivalent on Linux?"
date: 2010-04-19
forum: General Help
---

### Post by x1a4 on 2010-04-19
Hi,

Is there a Linux equivalent of the [Bitvise Tunnelier]("http://www.bitvise.com/tunnelier")?

Thank you.

---

### Post by cdaringe on 2010-04-19
Possible good news.  Are you just trying to ftp to a remote directory and map it to a drive/location/etc so you don't need an additional app to facilitate file transfer?

in ubuntu, it's built into nautilus (nautilus is kind of like the explorer in windows).

when you have a file browser window open, such as your home folder, go to 'file, connect to server'. enter in your connection data, and hit ok.  once connected, go to 'bookmarks' and add it as a bookmark.  now you can just click the bookmark whenever you want to connect, and it will show up in the side pane/place panel.

is this what you're looking for?

---

### Post by x1a4 on 2010-04-19
> is this what you're looking for?
Actually no, but that's definitely useful information.  Thanks.  
I'm trying to bypass throttling by an unethical infrastructure-dictator by creating a SSH Tunnel directly to my internet service provider.

EDIT: 

I already tried : 
```
ssh -D 8022 user@tunnel.host
ssh -L 8022:tunnel.host:22 user@tunnel.host -N
```

I would like to configure SSH so I can set 127.0.0.1:8022 as proxy.  It being a tunnel to tunnel.host in the example above.

EDIT 2:
I'm using OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007 on Xubuntu Hardy.

---

### Post by MY0613 on 2011-02-17
> **x1a4 said:**
> Actually no, but that's definitely useful information.  Thanks.  
I'm trying to bypass throttling by an unethical infrastructure-dictator by creating a SSH Tunnel directly to my internet service provider.

EDIT: 

I already tried : 
```
ssh -D 8022 user@tunnel.host
ssh -L 8022:tunnel.host:22 user@tunnel.host -N
```

I would like to configure SSH so I can set 127.0.0.1:8022 as proxy.  It being a tunnel to tunnel.host in the example above.

EDIT 2:
I'm using OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007 on Xubuntu Hardy.

So, if I have to use cntlm to help authorize with MS ISA proxy server, how to setup ssh to connect tunnel.host?

Thanks for any help.

---

