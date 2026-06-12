---
title: "How to install Thunderbird 3 (tar.bz2)"
date: 2010-01-13
forum: General Help
---

### Post by chrislionheart on 2010-01-13
I just download Thunderbird 3 and a file named as thunderbird-3.0.tar.bz2 got downloaded.
But I do not know how to install this file. I am very new to Ubuntu and recently migrated from Windows Vista to Ubuntu 9.10.

I know how to install the .deb files but how do I install the source code files.
Please help!


I already got some answers from various websites... but they are too confusing, since I am very new to Linux and do not know much about it. But I am trying to learn.
So please suggest me a simple solution.
Thanks in advance.

---

### Post by bug67 on 2010-01-13
A few things helped me figure this out:

1:  [http://ubuntuforums.org/showthread.php?t=1349889](http://ubuntuforums.org/showthread.php?t=1349889)

2:  [http://digitizor.com/2009/12/10/how-to-install-thunderbird-3-shredder-in-ubuntu-9-10/](http://digitizor.com/2009/12/10/how-to-install-thunderbird-3-shredder-in-ubuntu-9-10/)

3:  [http://www.google.com/#hl=en&source=hp&q=upgrade+thunderbird+3+ubuntu&aq=2&aqi=g9g-m1&oq=upgrade+thunderbird&fp=df82d86320cf60e9](http://www.google.com/#hl=en&source=hp&q=upgrade+thunderbird+3+ubuntu&aq=2&aqi=g9g-m1&oq=upgrade+thunderbird&fp=df82d86320cf60e9)

Definitely worth the effort.

---

### Post by Surkow on 2010-01-13
The file you downloaded probably did not contain source code. You can decompress the file in your home directory and start the thunderbird binary (maybe you need to make it executable first). After starting it, it will try to load your original settings if you had installed thunderbird 2 previously.

---

### Post by chrislionheart on 2010-01-13
@bug67
Bro, thanks for the help! The links are really helpful...

Just wanted to ask, in the second link there's a tutorial on installing Thunderbird 3 shredder.
Is shredder the same as the normal thunderbird for windows and Mac.

But anyways, thanks a lot for your help :)

---

### Post by scouser73 on 2010-01-13
Shredder was the pre-release of Thunderbird.

Download the **.tar.bz2** file from

[[COLOR="Red"]**Mozilla Messaging: Thunderbird 3**[/COLOR]]("http://en-gb.www.mozillamessaging.com/en-GB/thunderbird/")

**1** - Extract the **.tar.bz2** file

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

### Post by Cheesemill on 2010-01-13
If you're using a 32-bit Ubuntu then your best bet is to use [UbuntuZilla]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page"), this way your Thunderbird will stay up to date.

---

### Post by KingYaba on 2010-01-15
> **scouser73 said:**
> .

Thanks!

---

### Post by cforput on 2010-02-17
> **scouser73 said:**
> Shredder was the pre-release of Thunderbird.

Download the **.tar.bz2** file from

[[COLOR="Red"]**Mozilla Messaging: Thunderbird 3**[/COLOR]]("http://en-gb.www.mozillamessaging.com/en-GB/thunderbird/")

**1** - Extract the **.tar.bz2** file

**2** - Enter **gksudo nautilus** in terminal

**3** - Go to the folder **/opt**

**4** - Copy & paste the Thunderbird file that you extracted to **/opt**

**5 -** Enter these commands into **Terminal** 

*Enter your password if asked.*




[COLOR="Red"]**Obviously the username refers to you, and the filename to the file**[/COLOR]

**6** - Go to **System > Preferences > Main Menu**

**7** - In Main Menu, click on **New Item**

**8** - In the **Name** field enter **Mozilla Thunderbird Mail/News**

**9** - In the **Command** field enter **/opt/thunderbird/thunderbird**

**10** - In the **Comment** field enter **Mozilla Thunderbird Mail/News**

[[IMG]http://img121.imageshack.us/img121/7329/screenshot2c.png[/IMG]](http://img121.imageshack.us/img121/7329/screenshot2c.png/)

I need a little more clarification on step 4. It says to copy and past "the thunderbird file" that you extracted....

What is the exact file we are referring to here? When I extract the tar.bz2 file, I get tons for files.

Help!!!

---

### Post by wojox on 2010-02-17
Copy and paste the whole folder into /opt

You could also install the nightly builds from the repo's: [http://wojox.homelinux.net/?p=20](http://wojox.homelinux.net/?p=20)

---

