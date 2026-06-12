---
title: "Language per user"
date: 2005-03-11
forum: General Help
---

### Post by nocturn on 2005-03-11
How can I set the language for Gnome for one user only?

The system in question is that of my parents, it is running Warty.

The DM is KDM (they where used to it in Mandrake and I wanted to make the switch somewhat gradual).
My mother is running KDE (in Dutch).  My father is running Gnome, but it defaults to english (which is set in the system-wide locale).
All other users should have english.

How can I change it just for him?

---

### Post by an.echte.trilingue on 2006-05-12
I also find the fact that KDM does not have the language selection button that GDM has annoying.  Many people need/like to work in a multicultural environment and KDE doesn't do it.  But you need KDM if you are going to be in KDE and want all the options on the logout/switch user menu.  Believe me, I spent hours on google and as far as I can tell KDE has not even thought about supporting this.  :( 

I am using Kubuntu 6.06 and I do not have gnome installed, so I do not know for sure if this will work for you, but it should. :-k  Just replace "startkde" with whatever launches Gnome.  For this example, I will set up French language logins on a computer located in Germany.  It is more sloppy than I would like, but it works.


1.  Open up the list of languages you have installed: 
```
kate /usr/share/language-selector/data/languagelist
```




2.  Check that you have your locales installed.  In my case the line I need looks like this:
```
French;1;fr;fr_FR.UTF-8;fr;FR;fr_FR:fr:en_GB:en;kbd=lat9u-16(utf8)
```
In your case, just look for Dutch and nl instead.




3.  Now, go to /usr/share/xsessions/ in konqueror or nautilus or whatever.  Copy the file kde.desktop (or whatever gnome is called in your case; it should be obvious) and paste it to your home folder (not your to desktop, it will disappear).




4.  Open up the file you just copied in your text editor.  It should look like this:
```

[Desktop Entry]
Encoding=UTF-8
Type=XSession
Exec=/usr/bin/startkde
TryExec=/usr/bin/startkde
Name=KDE
```
It will also have a bunch of lines after that starting with "Name[XX]" and "comment[XX]" that you can just erase. 




5.  Make that file look like this:
```
[Desktop Entry]
Encoding=UTF-8
Type=XSession
Exec=/usr/bin/kde-french.sh
TryExec=/usr/bin/startkde
Name=KDE_French
```
and rename it something like kde_fr.desktop.




6.  Now we write the shell script (be sure to call it the same thing that you called it in the Exec= line in step 5, kde-french.sh in my case):
```
#!/bin/bash
#
# This will set the language to French for a person living in Germany and then Launch KDE
#
#
#here we set the language we want to use 
LANG=fr_FR.UTF-8
#
#here we set the locale we want to use, by order of priority
LANGUAGE=fr_DE:fr_FR:fr
#
#here we set the character classes
LC_CTYPE="fr_FR.UTF-8"
#
#here we set how the time is displayed
LC_TIME="fr_FR.UTF-8"
#
#here we set how things are collated
#For example, in enlgish "A" comes before "a"
#but in French "a" comes before "A"
LC_COLLATE="fr_FR.UTF-8"
#
#here we set currency
LC_MONETARY="fr_FR.UTF-8"
#
#here we set paper types
LC_PAPER="de_DE.UTF-8"
#
#here we set how names are displayed
LC_NAME="fr_FR.UTF-8"
#
#here we set how addresses are displayed
LC_ADDRESS="de_DE.UTF-8"
#
#here we set how telephone numbers are displayed
LC_TELEPHONE="de_DE.UTF-8"
#
#here we set measurement units
LC_MEASUREMENT="de_DE.UTF-8"
#
#
#
#now we can start our Desktop:
startkde

```
You can probably leave out all the LC_* lines if the computer is in the Netherlands or Flanders or whatever.




7. Then do the following commands:
```
sudo cp kde_fr.desktop /usr/share/xsessions/
sudo chmod 644 /usr/share/xsessions/kde_fr.desktop
sudo cp kde-french.sh /usr/bin/
sudo chmod 755 /usr/bin/kde-french.sh
```




8.  Log out.  Under the menu or session button (depending on your kdm theme) you should now have an entry for KDE_French.  Select that, log in as your dad, and set that as the default session for him.



**HOPE THIS WORKS!!!**:) 

If anybody reads this and knows a better way I personally would love to know, too.

---

