---
title: "New System Build Help"
date: 2009-12-31
forum: General Help
---

### Post by pgp_protector on 2009-12-31
I'm doing a New System Build with ubuntu (From the Live CD Install)

What I'm looking at doing is the following


1) Graphical Interface (Not required if I've got #6, but desired )
2) Apache, MySQL, PHP
3) SAMBA? 
   I want to share attached Hard drives that are already full of Windows NTFS Data
4) Web Development Platform (I'd Like to use it for Developing / testing Web code, primarly PHP / SQL)
5) Subversion Support for backing up / archiving a Real World Subversion server.
6) Remote Management (Non CLI Preferred )

I'll be running on a Celleron System with 1 Gig Ram and a 250G IDE Harddrive as the boot Drive.
I've got a second Full IDE HD and a few other SATA Drives that are also full of data that I'd like to keep for file sharing so I can access them from on the Home Network (Audio, Video, Documents, ect)

If possible I'd also like to be able to manage / check status of the server from the Web (I can open any required port in the Hardware Firewall if required)

So for this project would it be best to start with a Desktop or Server Install ?

---

### Post by VastOne on 2009-12-31
> **pgp_protector said:**
> I'm doing a New System Build with ubuntu (From the Live CD Install)

What I'm looking at doing is the following


1) Graphical Interface (Not required if I've got #6, but desired )
2) Apache, MySQL, PHP
3) SAMBA? 
   I want to share attached Hard drives that are already full of Windows NTFS Data
4) Web Development Platform (I'd Like to use it for Developing / testing Web code, primarly PHP / SQL)
5) Subversion Support for backing up / archiving a Real World Subversion server.
6) Remote Management (Non CLI Preferred )

I'll be running on a Celleron System with 1 Gig Ram and a 250G IDE Harddrive as the boot Drive.
I've got a second Full IDE HD and a few other SATA Drives that are also full of data that I'd like to keep for file sharing so I can access them from on the Home Network (Audio, Video, Documents, ect)

If possible I'd also like to be able to manage / check status of the server from the Web (I can open any required port in the Hardware Firewall if required)

So for this project would it be best to start with a Desktop or Server Install ?

It's the chicken or the egg question

Either install server which gives you most if not all of the parts you are seeking and if you need the desktop UI then install it. Or

Install the desktop and add the parts and packages that you want

---

### Post by Jive Turkey on 2009-12-31
if you download and run the server version installer on your system and choose the "LAMP" option, that will give you #2 in a very painless way.  Once installed you will need to use the cli to either install the desktop gui or you could install any number of web based admin tools ie: webmin, phpmyadmin.  Webmin will likely cover all of your gui needs.  

I think you're better off using ssh(CLI) and sftp to manage things but that's just my opinion.  Once you get the hang of it you will likely prefer it too.

I would not use webmin on a production box, based mainly on paranoia.

---

### Post by pgp_protector on 2010-01-04
Well I went with the Server Install, Added the desktop, and upgraded everything.

So for so good.

I've got SSH enabled (No root login / change default port number) 
I've also got WebMin running (tell I find something better)

Samba is isn't working the way I thought it would, I've got a second Hard Drive that was pulled from a windows system's secondary drive, so it's full of data that I don't want to loose.

I can see the drive but not access it from windows.
(Not at my home now, so I can't test it from the home network :( )

When I try to access my hardware firewall from webmin's http proxy, it doesn't load though, so I can't add / change open ports in my firewall right now.


Is their a way to setup a remote desktop through the ssh port that is open ?

---

