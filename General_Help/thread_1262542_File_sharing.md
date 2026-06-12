---
title: "File sharing"
date: 2009-09-10
forum: General Help
---

### Post by doctorbighands on 2009-09-10
I have a home server running XFCE on top of ubuntu server edition. I'm trying to make it a file server, but I can't seem to figure out how to do that.

In Ubuntu (on my laptop, for instance), when I right-click on a folder, I can select "Sharing Options" in order to make this happen. On my server, I have no such option in my right-click menu. Other than the right-click option, I have no idea how to get this job done.

I'm sorry if this is unclear. All I want is to get my server running as a file server using Samba.

Any help is appreciated. Thank you!

---

### Post by doctorbighands on 2009-09-10
...bump

---

### Post by jondkent on 2009-09-10
search and you will find :

[https://help.ubuntu.com/8.04/serverguide/C/configuring-samba.html](https://help.ubuntu.com/8.04/serverguide/C/configuring-samba.html)

Setup samba server before, fairly easy to do.  Have fun

---

### Post by StuartN on 2009-09-10
> **doctorbighands said:**
> ...bump

Have you installed samba-common? It seems to be the only requirement for SMB shares. There is an Ubuntu server-specific guide at [https://help.ubuntu.com/8.10/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/8.10/serverguide/C/samba-fileserver.html)

---

### Post by doctorbighands on 2009-09-10
The issue I'm having isn't to do with configuring Samba. It's already installed and configured.

The issue is that I can't figure out how to share an actual folder on the network. In Ubuntu, it's as simple as right-clicking on the folder you want to share. On my server, I don't have the option in the right-click menu like I do on every other Ubuntu machine I've ever used.

So, without the right-click option, how do I tell my server to share a specific folder?

---

### Post by jondkent on 2009-09-10
You might be able to do such a thing via webmin, never used it but sounds like the kinda thing it would do.  Obviously you'd have to install that.

You're expecting desktop behaviour on a server, but servers never usually run GUIs so AFAIK you won't find what you are looking for with GNOME/KDE.

The easiest way is to configure this via the samba config files as outlined the guides linked previously

---

### Post by StuartN on 2009-09-10
> **doctorbighands said:**
> So, without the right-click option, how do I tell my server to share a specific folder?

I think you need to edit /etc/samba/smb.conf, and I think this is what Nautilus does behind the scenes when you share a folder. There is a long (long) guide at [http://samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html)

In the case of a single folder it is something like adding just:
```
[sharelabel]
path = /home/me/shared_folder
comment = Popup comment about shared_folder
```

The simplest way to set this up might be to save smb.conf on a computer that currently does share, then add one more share, then "diff smb.conf smb.old" and copy the difference to your Ubuntu server.

---

