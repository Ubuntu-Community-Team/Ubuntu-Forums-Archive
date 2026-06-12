---
title: "Could someone explain this to me?"
date: 2010-06-13
forum: General Help
---

### Post by .Daniel on 2010-06-13
Hi all - I recently signed up for Sky Songs thinking that the whole process of download the music was web-based but it turns out that you need to download an app. It's written in Java so this guy has written a blog post that outlines how to get it working in Linux:

[http://blog.beplacid.net/2009/12/15/sky-songs-and-linux/](http://blog.beplacid.net/2009/12/15/sky-songs-and-linux/)

I'm relatively new to Ubuntu - could someone please give me a step-by-step walkthrough of this?

Thanks in advance,
Daniel

---

### Post by .Daniel on 2010-06-13
Bump

---

### Post by .Daniel on 2010-06-13
Bump? :(

---

### Post by ddrichardson on 2010-06-13
Bumping after 3 hours just means most of us think you've had a reply and don't look.

Which part of his guide are you having difficulty with?

---

### Post by .Daniel on 2010-06-13
> **ddrichardson said:**
> Bumping after 3 hours just means most of us think you've had a reply and don't look.

Which part of his guide are you having difficulty with?

Oh right, sorry... I don't understand when he says:

'chmod a+x it'...

---

### Post by ddrichardson on 2010-06-13
It means to add execute permission to everyone, once you've created the file "skysongs" then type:
```
chmod a+x skysongs
```
From a terminal in the same folder as the file.

---

### Post by benerivo on 2010-06-13
The chmod bit is a command that changes its permissions so that users can run it. The whole guide looks like the "skysongs.exe" can be installed on linux with wine, and then ran when a java runtime environment (jre) is installed. It says that you should create a file inside your home directory, and that this is the file that you should chmod (i think). To chmod it, just try

chmod a+x /home/dan/bin/skysongs

or i think you can make any file executable by right clicking and going to 'properties' where you can make it executable.

---

### Post by .Daniel on 2010-06-13
[http://www.winehq.org/search?cx=partner-pub-0971840239976722:w9sqbcsxtyf&cof=FORID:10&ie=UTF-8&q=sky+songs&siteurl=appdb.winehq.org/](http://www.winehq.org/search?cx=partner-pub-0971840239976722:w9sqbcsxtyf&cof=FORID:10&ie=UTF-8&q=sky+songs&siteurl=appdb.winehq.org/)

Nothing's showing for SkySongs in the Wine database search - any ideas? Looks like I might have to VM Win7 or something...

---

### Post by benerivo on 2010-06-13
The wine database won't be comprehensive. I think i would install wine then see if wine can be used to install the skysongs.exe downloaded file. From there, i would install a jre and then create that very small script file from that user guide. VM will definitely work.

---

### Post by .Daniel on 2010-06-13
Thanks for your help - I'm going to VM Windows 7 and run it through there when I want to download files. I also needed a way to test some sites on IE so it's all good :)

---

