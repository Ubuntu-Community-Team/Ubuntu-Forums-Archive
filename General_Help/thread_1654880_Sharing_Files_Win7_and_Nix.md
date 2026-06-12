---
title: "Sharing Files Win7 and Nix"
date: 2010-12-29
forum: General Help
---

### Post by iball8888 on 2010-12-29
I know that I can use Samba to share files between a Linux computer with a Windows computer, I have found a lot of tutorials of how to set it up.  But what I need help with is how to set up my WINDOWS computer so that I can use samba with it.

What are the steps that I need to follow on my Windows comp?

---

### Post by noah++ on 2010-12-29
The SMB protocol is native to Windows. Samba was first written almost twenty years ago for UNIX-like systems to operate in a Windows world. (But perhaps you already knew that.)

So there's not much configuration on the Windows side. Visit Properties of any Windows folder you want to share, and share it. If you can't see the folder in Linux by then, I believe you have to make sure your computer is in the same workgroup that is named in your Linux **smb.conf**. I am more familiar with Windows XP, and I am writing this without access to Windows 7, but I think the steps are the same.

---

### Post by iball8888 on 2010-12-29
I am going to a new college that is quite far away from my house.  Can I use samba to access my files from my PC Box while at my college with my Nix Laptop?

---

### Post by noah++ on 2010-12-29
SMB is for sharing files over the same LAN. So to access SMB shares remotely, you'd have to establish a VPN at home and log into it from school. Seems overly complicated.

What's more common, and what I've done, is either to

1. manually transfer my school files to my personal disk space on the school server,
2. log into my home machine via SFTP, or
3. keep my school files directory synched via [Dropbox]("http://www.dropbox.com"), which I can access from the web at school. (But you can also autosync with the Dropbox client on your laptop. It's cross-platform software.)

Now I don't do any of those things, except to make backups, because I got a very powerful, very portable laptop I can carry with me, which I use exclusively.

---

### Post by iball8888 on 2010-12-29
I use and love dropbox, I have it on all of my computers, laptops, phones, etc.  My Girlfriend and I share a dropbox so that we can pass stuff like pictures we found, art she has drawn, and links and other files that are vital.  Their non-free accounts are quite expensive for me, but do seem useful.

SFTP does sound like a good idea, I'll look into that.  Any idea where to start on that?

---

### Post by noah++ on 2010-12-29
You just have to have an SSH service running on the server side. I think the popular free Windows one is called Winsshd. So look into starting that at boot time if desired. Also research port forwarding if you are using a home router and you are not familiar with it. In a default setup, port 22 needs to be forwarded.

On the remote client side, use an SFTP client like Filezilla or lftp. You log in with your normal (server) desktop credentials, probably, but I'm not sure how it works with a Windows server. Another, neat client-side option is sshfs, which lets you mount any remote directory via SSH.

---

