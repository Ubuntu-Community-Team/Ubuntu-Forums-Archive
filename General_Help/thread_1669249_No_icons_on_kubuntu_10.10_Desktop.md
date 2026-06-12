---
title: "No icons on kubuntu 10.10 Desktop"
date: 2011-01-17
forum: General Help
---

### Post by apollothethird on 2011-01-17
Can someone tell me how to enable the display of icons on the kubuntu desktop?  I've searched the internet and there are repeated references to setting the desktop to be a folder.  However I can't find this option in kutuntu 10.10.

Thanks in advance for anyone that can help.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by khamil8686 on 2011-01-17
I have trouble with that too when i do a clean install, how i set it to show the desktop folder is right-click the background, click folder view settings, click activity, set type to Folder View, and the name i usually set to the absolute path of the desktop folder but i just checked to see if i could set it to something else and it would still show the desktop folder and it does, so im not sure if the name is necesary or not, just changing the type to folder view seems to solve it for me :)

---

### Post by apollothethird on 2011-01-17
> **khamil8686 said:**
> I have trouble with that too when i do a clean install, how i set it to show the desktop folder is right-click the background, click folder view settings, click activity, set type to Folder View, and the name i usually set to the absolute path of the desktop folder but i just checked to see if i could set it to something else and it would still show the desktop folder and it does, so im not sure if the name is necesary or not, just changing the type to folder view seems to solve it for me :)

Thanks for the input.  I find it incredible that I can't find these steps in my new default install.  When I right click on the background (which is normally referred to as the desktop... in a space where there isn't a window or icons) I get these options:

Run Command
Add Widget
Add Panel
Activities
Lock Widget
Lock Screen
Leave
Desktop settings


In Desktop settings I have:

Wallpaper
Activity
Mouse Acctions

Under Wallpaper I have

Image
Scaled
Color

I can't find an option for setting Folder View.

This is a fresh install.  It's the second fresh install.  The first one as 64 bit.  This one is the 32 bit.  I can't find this feature in either.

Thanks in advance if you can help me to identify what I'm missing.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by apollothethird on 2011-01-17
After some experimenting the Desktop has started to behave like a normal Desktop (showing the desktop icons) and the folder view option that you mentioned.

I'll have to explore it more so that I can figure out an easy definable way to do this so that on the next install I might not have to spend 5 hours trying to figure it out.  Also, I'll be able to help the next person that has this problem.

Thanks!

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by khamil8686 on 2011-01-17
try activities, when I right click the desktop and select settings it takes me to where I can select from a list of those things you mentioned, try clicking activities and see what there is :)

---

### Post by khamil8686 on 2011-01-17
or desktop settings, just thought of that, posting this reply from my phone, I can look more in depth when I get home

---

### Post by aaaantoine on 2011-01-17
> **apollothethird said:**
> Thanks for the input.  I find it incredible that I can't find these steps in my new default install.  When I right click on the background (which is normally referred to as the desktop... in a space where there isn't a window or icons) I get these options:

Run Command
Add Widget
Add Panel
Activities
Lock Widget
Lock Screen
Leave
Desktop settings


In Desktop settings I have:

Wallpaper
Activity
Mouse Acctions

Under Wallpaper I have

Image
Scaled
Color

I can't find an option for setting Folder View.

I see you found the solution yourself, but I'm answering for the sake of others.

Folder View is an option under the "Activity" tab.

(Not to be confused with the *other* KDE Activities, which are getting some enhancements in KDE 4.6 and might actually be useful this go around.)

The quick way to set this is.

1. Right-click the desktop.
2. Select "Desktop Settings"
3. Go to the "Activity" tab.
4. Change the Activity to "Folder View".

It shouldn't take 5 hours going forward.  More like 30-45 seconds if you know where to find it.

The default "KDE Way" of handing desktop icons is to have a discrete "Folder View" Plasma widget which points to ~/Desktop.  This was the only option in earlier KDE 4 versions.  I kinda like it this way because it works better when you have other Plasma widgets on your desktop.

---

