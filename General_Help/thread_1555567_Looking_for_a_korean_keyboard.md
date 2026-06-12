---
title: "Looking for a korean keyboard"
date: 2010-08-18
forum: General Help
---

### Post by jodonald on 2010-08-18
n00b here looking to see if there's a way to get a Korean keyboard on my machine.  I know system > preferences > keyboard will get me options for other languages, but for some reason there is no Korean.  Or i guess there is, but it's not Korean, just plain ol' English.  Is there a way to acquire this?

---

### Post by praveenkovvuri on 2010-08-18
[SIZE=5]Follow the following steps.U may get it[/SIZE]


I found a [post in ubuntuforums.org]("http://ubuntuforums.org/showthread.php?t=1498411") that explained how to enable Korean input.
 1. Enable Korean language support by going to System>  Administration> Language Support. Click on Install / Remove  Languages, select Korean from the list and Apply Changes. Select scim as  the Keyboard input method system.
 [IMG]http://newtoubuntu.files.wordpress.com/2010/07/korean1.png?w=700&h=268[/IMG]
 2. Go to Applications> Ubuntu Software Center and search for scim-hangul and install Hangul Input Method Engine for SCIM.
 [IMG]http://newtoubuntu.files.wordpress.com/2010/07/korean2.png?w=700&h=154[/IMG]
 3. On my computer [SCIM]("http://www.scim-im.org/") was  installed by default, but if not you can install it in the Ubuntu  Software Center. It is called SCIM Input Method Setup. After it is  installed you can find it under System> Preferences> SCIM Input  Method Setup.
 4. Restart your computer.
 5. Activate SCIM by inputting ctrl + space bar. You should see a  floating menu on the bottom right corner and/or a keyboard icon in the  upper right corner. Both allow you to switch between Korean and English.
 [IMG]http://newtoubuntu.files.wordpress.com/2010/07/korean3.png?w=334&h=122[/IMG]
 [IMG]http://newtoubuntu.files.wordpress.com/2010/07/korean4.png?w=233&h=118[/IMG]
 My preferred font for reading Korean text is Baekmuk Dotum and  Baekmuk Gulim which are nicely legible. These can be installed through  the Ubuntu Software Center by searching for Baekmuk series TrueType  fonts. Then in Firefox, you can enable them by going to Edit>  Preferences. Select the Content tab and select Advanced and then you can  choose the fonts for Korean.
 [IMG]http://newtoubuntu.files.wordpress.com/2010/07/korean5.png?w=700&h=526[/IMG]

---

### Post by jodonald on 2010-08-18
Great easy instructions, it worked perfectly.  Thanks praveenkovvuri!

---

### Post by simosx on 2010-08-18
> **jodonald said:**
> Great easy instructions, it worked perfectly.  Thanks praveenkovvuri!

The proper instructions for Ubuntu 10.04 is to use IBus instead.
IBus replaces SCIM.

You install the Korean language support and then you logout. You select the Korean locale and you login again. You should be able to type Korean.

Alternatively, you can keep the English interface; you install Korean from the Language Support and configure IBus to type Korean.

---

