---
title: "Open or remove program (Cmaptools) installed to root"
date: 2012-05-24
forum: General Help
---

### Post by David_Colyer on 2012-05-24
Hello,

 I have just installed Cmap Tools on Ubuntu 10.10 / Mavrik 64bit

 The installer was a .bin.
 
 It&#8217;s default setting was to install in root, which I thought was odd, but I don&#8217;t really know that much about it, so decided to go with the default. Which I guess was probably a bad idea.
 
 So three questions:
 
 1. If it is possible to run the programme successfully from root, does anyone know how to open it. There&#8217;s no icons anywhere and I can&#8217;t open the root folder.
 
 2. How do I delete it from root, so I can reinstall?
 
 3. Where should I reinstall to? Home? etc?

Thanks
David

---

### Post by raja.genupula on 2012-05-24
its actually deals with what the terminal code you used to launch it . 

so to launch it by typing that in terminal and if you wanna remove it then 

```
sudo apt-get remove <app_name>
```

no need to delete from root . 

```
sudo apt-get remove --purge <app_name>
```

will make a clean removal for you .

and on how to use that tools can look from here 
[http://cmap.ihmc.us/support/help/](http://cmap.ihmc.us/support/help/)

---

### Post by David_Colyer on 2012-05-25
Thanks for that suggestion. Unfortunately I wasn't able to make that work, because I didn't know the exact name of application / folder and the various options I tried CMapTools, CMap etc didn't seem to work.

I was able to use the following command: 

"gksudo nautilus" in terminal

(as suggested here: [http://www.linuxforums.org/forum/mandriva-linux/112416-how-do-i-open-root-folder.html](http://www.linuxforums.org/forum/mandriva-linux/112416-how-do-i-open-root-folder.html))

to open the root directory, then in the CMap folder to run the installer. Hopefully this has worked without doing any damage to anything else.

(If I have any problems I will update this thread to warn people not to take that approach!)

PS How do mark this thread as "solved?"

---

### Post by raja.genupula on 2012-05-25
to solve the thread as solved , click at thread tools at your 1st post and there will be an option called mark the thread as solved .click that and that will do the job . 


Cheers

Raja

---

### Post by David_Colyer on 2012-05-25
Thanks.

As it happened that wasn't quite the end of the issue. Once CMap was installed I had the Java conflict others have mentioned.

The solution seems to be to delete or rename the jre file that comes with CMap. So far I haven't been able to do that...

But will update this when I figure it out.

---

