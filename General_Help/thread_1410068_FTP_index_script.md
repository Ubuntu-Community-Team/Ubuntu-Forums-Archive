---
title: "FTP index script"
date: 2010-02-18
forum: General Help
---

### Post by tom.swartz07 on 2010-02-18
Hi all

I have a bit of a nagging question. 

Does anyone know a good script that would automatically generate an index.html file for an FTP server?

I just uploaded quite a bit of my music and files to my FTP server, and I really dont feel like having to go through and manually add links to a page so that I could browse them from anywhere. 

I was looking in to using a script originally written for dropbox- here: [http://www.webupd8.org/2010/02/share-entire-dropbox-folder-with.html](http://www.webupd8.org/2010/02/share-entire-dropbox-folder-with.html)

But it doesnt work on the remote server. I could only create the index for files residing on the drive here.


Any Ideas?

---

### Post by tom.swartz07 on 2010-02-18
Im not sure if it makes any difference, but its on a SFTP server and there are multiple subdirectories.

---

### Post by tom.swartz07 on 2010-02-19
Anyone have an idea?

---

### Post by tom.swartz07 on 2010-02-20
I guess Ill take this resounding silence as, "No-one knows"

---

### Post by amac777 on 2010-02-20
I might not be understanding what you want to do, but from your description it sounds like you want to be able to see a list of all the files on the ftp server in a web browser, and be able to click links in order to download said files. If that is all you want, try directly browsing the ftp server in your web browser:

[ftp://servername.com](ftp://servername.com)

If you need it work with a particular username / password, you can do this:

[ftp://username:password@servername.com](ftp://username:password@servername.com)

edit: for some reason the colon : p is coming up as a smiley... I'm trying to figure out a way to prevent the forum from doing that. Anyway, the above command should be: "username : password" but without the spaces. Ahh, found "disable smileys" in the advanced options.

---

### Post by tom.swartz07 on 2010-02-21
> **amac777 said:**
> I might not be understanding what you want to do, but from your description it sounds like you want to be able to see a list of all the files on the ftp server in a web browser, and be able to click links in order to download said files. If that is all you want, try directly browsing the ftp server in your web browser:

[ftp://servername.com](ftp://servername.com)

If you need it work with a particular username / password, you can do this:

[ftp://username:password@servername.com](ftp://username:password@servername.com)

edit: for some reason the colon : p is coming up as a smiley... I'm trying to figure out a way to prevent the forum from doing that. Anyway, the above command should be: "username : password" but without the spaces. Ahh, found "disable smileys" in the advanced options.

That makes sense, and I do use this method when Im on my other Linux boxes. The problem arises when Im out and about, Windows doesnt have, in my view, a decent FTP browser. 

I wanted to get it so that I could navigate to my ftp page (hosted by my University) and access my files from a menu like the one in the attachment

I was able to take the script i mentioned and edit it so that it gives the correct path to the files. If anyone wants, Ill post it.

---

