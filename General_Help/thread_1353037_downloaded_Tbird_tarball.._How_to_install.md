---
title: "downloaded Tbird tarball.. How to install?"
date: 2009-12-12
forum: General Help
---

### Post by mahela007 on 2009-12-12
I have downloaded the tar.gz file for thunderbird 3.0. However, I don't have a clue how to install it because it doesn't contain source code which I can 'build'. What should I do?

---

### Post by scouser73 on 2009-12-12
Download the **.tar/bz2** file from

[[COLOR="Red"]**Mozilla Messaging: Thunderbird 3**[/COLOR]]("http://en-gb.www.mozillamessaging.com/en-GB/thunderbird/")

**1** - Extract the **.tar/bz2** file

**2** - Enter **gksudo nautilus** in terminal

**3** - Go to the folder **/opt**

**4** - Copy & paste the Thunderbird file that you extracted to **/opt**

**5 -** Enter these commands into **Terminal** > **sudo -i**

*Enter your password if asked.*

> **cd /opt**
> **chown -R username filename**

[COLOR="Red"]**Obviously the username refers to you, and the filename to the file**[/COLOR]

**6** - Go to **System > Preferences > Main Menu**

**7** - In Main Menu, click on **New Item**

**8** - In the **Name** field enter **Mozilla Thunderbird Mail/News**

**9** - In the **Command** field enter **/opt/thunderbird/thunderbird**

**10** - In the **Comment** field enter **Mozilla Thunderbird Mail/News**

[[IMG]http://img121.imageshack.us/img121/7329/screenshot2c.png[/IMG]](http://img121.imageshack.us/img121/7329/screenshot2c.png/)

---

### Post by mahela007 on 2009-12-12
Thanks for the quick reply. Isn't there a way of automatically adding the start menu entries?

---

### Post by scouser73 on 2009-12-12
Not that I know of, sorry.

---

### Post by mahela007 on 2009-12-12
by the way, what the -i argument do in sudo?

---

### Post by HomoGleek on 2009-12-12
Take a look at this thread [http://ubuntuforums.org/showthread.php?t=1350306](http://ubuntuforums.org/showthread.php?t=1350306)

That explains how to install it in a more easy fashion

---

### Post by mahela007 on 2009-12-12
I should have mentioned this before. I don't want to add PPAs. I want to try my hand at installing a tarball.

---

### Post by scouser73 on 2009-12-12
> **mahela007 said:**
> by the way, what the -i argument do in sudo?

Well the command I gave you sudo -i is recursive ownership, meaning that you unlock everything inside the folder.

I got the instructions from here and I have used them myself and they work perfectly: [[COLOR="Red"]**How To Change Ownership Of Files & Directories**[/COLOR]]("http://www.unixtutorial.org/2009/02/how-to-change-ownership-of-files-and-directories-in-unix/")

---

### Post by wojox on 2009-12-12
> **mahela007 said:**
> by the way, what the -i argument do in sudo?

Drops you into root.

---

### Post by wojox on 2009-12-12
> **mahela007 said:**
> Thanks for the quick reply. Isn't there a way of automatically adding the start menu entries?

You mean adding to Applications > Internet?

---

### Post by wojox on 2009-12-12
> **scouser73 said:**
> Well the command I gave you sudo -i is recursive ownership, meaning that you unlock everything inside the folder.

I got the instructions from here and I have used them myself and they work perfectly: [[COLOR="Red"]**How To Change Ownership Of Files & Directories**[/COLOR]]("http://www.unixtutorial.org/2009/02/how-to-change-ownership-of-files-and-directories-in-unix/")

Nice site scouser73 Thanks for the link ;)

---

### Post by scouser73 on 2009-12-12
Yeah, that sites helped me out loads.

---

### Post by mahela007 on 2009-12-12
> **wojox said:**
> You mean adding to Applications > Internet?
Yes..
This may seem dumb but what file am I supposed to change the ownership of ? the main folder that I've extracted from the tar file?

---

### Post by praveenthivari on 2009-12-12
> **mahela007 said:**
> I have downloaded the tar.gz file for thunderbird 3.0. However, I don't have a clue how to install it because it doesn't contain source code which I can 'build'. What should I do?
Go to softpedia.com. Download the latest thunderbird in .deb format. So easy.

---

### Post by wojox on 2009-12-12
Go into System > Preferences > Main Menu 

Click on Internet on right side and select New Item from top left and follow scouser73 directions for launcher.

---

### Post by scouser73 on 2009-12-12
> **mahela007 said:**
> Yes..
This may seem dumb but what file am I supposed to change the ownership of ? the main folder that I've extracted from the tar file?

Yes.

---

### Post by mahela007 on 2009-12-12
> **praveenthivari said:**
> Go to softpedia.com. Download the latest thunderbird in .deb format. So easy.
look, I obviously want to know how to install from the tar ball. I've said so in a previous post.

---

### Post by mahela007 on 2009-12-12
> **wojox said:**
> Drops you into root.
Well , why not just use sudo instead of sudo -i?

---

### Post by mahela007 on 2009-12-12
> **scouser73 said:**
> Well the command I gave you sudo -i is recursive ownership, meaning that you unlock everything inside the folder.

I though chown -R gave recursive ownership.

---

### Post by mahela007 on 2009-12-12
Finally installed it. How should I get the Tbird icon to put on the menu? I don't like the ugly defualt icon.

---

### Post by wojox on 2009-12-12
Click on the program icon from System > Preferences > Main Menu > Internet Thunderbird and open opt/thunderbird/icons

---

### Post by mahela007 on 2009-12-12
There's only one icon in that folder and I don't think ubuntu can use it an an icon. It's a png file.
and it's not the proper Tbird icon with the bird and envelope.

---

