---
title: "How does one go about removing the recent documents?"
date: 2010-05-14
forum: General Help
---

### Post by argedion on 2010-05-14
I'm using Ubuntu 9.10 (Gnome) 

I cannot remember how to remove the Recent Documents option from the places bar. I thought it was to open GConf-editor and then desktop/gnome/lockdown in there should have been an option of file types that had 12345 as a value i remember removing the 3 (document history) and my problem was solved. Now this seems to be gone. How do I go about removing this now? I did a search and really couldn't find a solution to my problem.

---

### Post by scouser73 on 2010-05-14
To stop recent documents from showing please enter these commands into the terminal.

**1st** > **rm ~/.recently-used.xbel**

**2nd** > **touch ~/.recently-used.xbel**

**3rd** > **sudo chattr +i ~/.recently-used.xbel**


Alternatively, if you have Ubuntu Tweak installed then you can disable the recent documents list be going to **Gnome Settings** & uncheck **Enable System-wide "Recent Documents" List**

---

### Post by obscurant1st on 2010-05-14
thx for this tip. Now only i recognize that how useless this recent documents  for me. I am removing it.
:)))
btw what si this [B].recently-used.xbel ?
is it a conf file or something? :o
also from where you got this info? :o
[/B]

---

### Post by wojox on 2010-05-14
There's also

```
gedit .gtkrc-2,0
```

Then add this to it:

```
gtk-recent-files-max-age = 0
```

---

### Post by obscurant1st on 2010-05-14
the second command is not working in my system..
:(

---

### Post by crichard on 2010-05-14
> **obscurant1st said:**
> the second command is not working in my system..
:(

FYI, the second line is not the command to execute. You've to copy that line in the .gtkrc-2.0 file & save it. [wojox]("http://ubuntuforums.org/member.php?u=802919") is correct. :)

---

### Post by argedion on 2010-05-14
Thanks for all the help guys 

scouser73 that worked for me it doesnt remove the recent documents but it does disable it

wojox 
yours did not work for me (tried it first) maybe i'm not using gtk? dont know just did a basic install.

again thanx for the help you guys rock
:guitar:

---

### Post by no0ne on 2010-06-28
The **KDE** way;

Remove all recent documents.
 
```
rm ~/.kde/share/apps/RecentDocuments/*.*
```

(You might want to go trough the directory above per item if you wish to be surgical.)

and to disable simply make it read only.

```
chmod 400 ~/.kde/share/apps/RecentDocuments
```

PS Wasn't showing up clearly and separately on any decent search, decided to post. (Once you know the location, it gives a few results, but the other way around.)

---

### Post by highfructose327 on 2010-11-18
This worked perfect, in the places menu, Recent Documents are grayed out. Thanks wojox

> **wojox said:**
> There's also

```
gedit .gtkrc-2.0
```

Then add this to it:

```
gtk-recent-files-max-age = 0
```

---

