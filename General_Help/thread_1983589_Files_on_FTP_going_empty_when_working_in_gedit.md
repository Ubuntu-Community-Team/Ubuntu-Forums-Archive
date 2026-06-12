---
title: "Files on FTP going empty when working in gedit"
date: 2012-05-20
forum: General Help
---

### Post by DrLaunch on 2012-05-20
**My setup**
Domain and hosting services from one.com
Ubuntu 12.04 32-bit
gedit 3.4.1
nautilus 3.4.2

**My workflow**
I've added my FTP directory at ftp.knutremi.com to my network folders in Nautilus. I'm working on my own website written in PHP, and I'm using gedit as my editor. I some times browse the FTP directory for my website through Nautilus, and double click the files to edit them directly in gedit. And sometimes, I open them by browsing my FTP directory through the "Open file" dialog in gedit. I always save my files using Ctrl + S. This causes gedit to save the files directly to the FTP directory where I opened them.

**My problem**
My workflow works without problems most of the time. But on some occasions, I discover that some of the files I've been saving to my FTP directory through gedit are empty. This only happens to some of the files. And it happens seemingly at random. My hunch was that some scripts at one.com are removing file contents. I contacted one.com chat support and explained my problem. Even though I don't know what caused them to come to the conclusion, they concluded that there's a problem with gedit, causing the FTP transfer upon save to fail. This sounds weird, as I seem to remember gedit not saving empty files.

**The answer I need**
I need to find out if this is actually an issue with gedit. Or if it's an issue with Nautilus. Or if it's an issue with the built in FTP support in Ubuntu. I need to know this so I can file a bug report, if it's either of the things I mentioned. That way, it can hopefully be fixed in the future. I'd also be happy to know if it's my hosting provider's fault. That way I can report back to them with the information, so they can solve the problem on their end. I'd also be happy to know if it's my own fault, so I can solve the problem my self.

---

### Post by dcstar on 2012-05-21
FTP is a lousy way to access files. FTP is basic method to transfer files from one location to another (**F**ile **T**ransfer **P**rotocol, get it?)

When you "edit" using FTP the entire file is transferred to your node, edited and then the entire changed file is transferred back.

Gedit is a Linux application that expects to be used on fully supported Linux filesystems, and does things like creating hidden backup files using the Linux convention of a filename starting with a ".", which is probably illegal and unsupported in FTP.

The answer is not to use Gedit but only basic text editors (or a web site editor like Kompozer that uses FTP), or manually copy files locally for editing.

---

