---
title: "setting up home server (newb)"
date: 2010-12-13
forum: General Help
---

### Post by lancevo3 on 2010-12-13
Hi,

I am wanting to turn an old desktop to a small file server, just the usual movies, music, pictures, etc. I want to be able to access this not only on my home network I want to be able to access it online so there is a way to get to my files remotely if needed. I was wondering if ubuntu server is what I must use or would the desktop edition do the trick? Any suggestions would be great.

Thanks

---

### Post by katykat on 2010-12-13
Take a look at wzdftpd and pure-ftpd. 

You will probably have to store your files in their directories as typically FTP servers are chrooted and unable to access the main system or Home files.

---

### Post by msandoy on 2010-12-14
Since you are a beginner, I'm assuming you have little or no experience with CLI. So, use the ordinary desktop version, and after install, open a terminal and write:
```

sudo tasksel

```
choose the type of server tasks you want to install. There are many good configuration howto's both here and elsewhere on the internet. Try searching for SAMBA config howto or something simmilar.
For sharing files with windows clients, go for SAMBA sharing. (SMB)

For remote access to files, you should go for OpenSSH server, and with windows client, it is possible to transfer with a program called putty.exe (Free download.) With Linux clients, you can use any program that supports fish, ssh, scp or SSHFS. 

You would think that you can do anything in GUI, but just to tweak your interest a bit, read up on those four last commands. In combination with Nautilus they make secure file transfer childsplay. 

When opening your computer to the world, make sure you have read the stickies in the security section.

---

