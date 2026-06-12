---
title: "Lubuntu conky start-up clearification help"
date: 2011-11-13
forum: General Help
---

### Post by ajobim on 2011-11-13
Hello all, 

After a few weeks of trying out multiple live cds from a few different distributions, I have finally made the leap to Linux.  I settled on a Lubuntu version for my aging desktop, an old Dell p4.  Thanks to Lubuntu its running better than it did a decade ago, when it was brand new.  

While exploring the world of Linux, I came across a wonderful little program named Conky, and instantly became quite fond of it.  I spent the better part of this weekend learning how to configure it and finally settled on a layout that, one- I'm happy with and, two- I look forward to adding to and increasing it's functionality.  

My only stumbling block comes with trying to have it start automatically on login.  I have read a ton of posts regarding start-up methods and it seems almost none of them deal with my set up.  I am running Lubuntu 11.10 in the default session, openbox-lxde.  

I got as far as creating the following file and saving it as: /home/ajobim/.conky_start.sh

```
#! /bin/bash
sleep 20 && conky -c /home/ajobim/Conky/conky03
```I made sure it is excutable by all users using:

```
chmod +x .conky_start.sh
```I am hoping what I have done this far is correct.  I came across this thread:

[http://http://ubuntuforums.org/showthread.php?t=1799956&highlight=conky+on+start+up]("http://http//ubuntuforums.org/showthread.php?t=1799956&highlight=conky+on+start+up")

But being very new to the Linux world, it makes very little sense to me and I was hoping someone here could help me out a bit.  Mostly I need clearification with the last part:

                                                                             > Got it.  With  LXDE, you first have to make a .desktop file in /usr/share/applications  then copy that file into home/username/.config/autostart  The system  seems to be picky about these two files so it takes a lot of messing  around to get it right.  Thanks for the help timgoodI guess I'm not real clear on what a .desktop file is.  Is it just a blank file named .desktop? Or is there something a file I should have and save it as .desktop? Also in the thread, the poster has the following code as his auto start config file:

[```
Desktop Entry]
Encoding=UTF-8
Type=Application
Name=Conky
Exec=/home/zachleigh/Scripts/conkystart.sh
StartupNotify=true
```Is that supposed to be my .desktop file?  Or do I need to create this file or any others somewhere else along the way?
Mostly, I'm pretty lost right now, but I am hopeful that I am on the right track.  I appreciate any assistance in clearing this up.

As I said, I am very new to Linux and only got as far as file types, permissions, and basic command line interface, beginner's shell scripting tutorials and installation guides so far, so for any one that has any advice for me, type slowly and use small words please=)

Thx much

---

### Post by bluexrider on 2011-11-13
OMG! You really want to get into the deep part of the pool don't you?

Ignore anything and everything you might have been told about conky. This is the authority and possibility GOD when it comes to conky. Do not invoke or and try to appease any other script. YOU WILL fail.

That said I think I would follow what ever "sector 11" has to say 

This is a start [http://ubuntuforums.org/showthread.php?t=281865&highlight=sector11](http://ubuntuforums.org/showthread.php?t=281865&highlight=sector11)

Good luck on your journey

---

### Post by ajobim on 2011-11-13
If your going to learn how to swim you might as well jump in and get it over with=)

I have two weeks off from work and figured now was as good a time as ever to try and learn as much as I could.

Thanks for the link.  1100+ pages..... looks like I have my work cut out for me.

---

### Post by ajobim on 2011-11-14
Yay me!!!!

After a few more Google attempts I found a work around.  Not sure if this is correct or not, I'm just ecstatic it works.

***This is for Lubuntu 11.10 using the default "openbox-lxde" session.***

As anyone who is using this particular Desktop environment/Window manager combo knows, when you select Preferences, Desktop Session Settings, Automatically Started Applications, you are given a list of applications with no option of adding any.  This is a way I found to manually add applications to this list.  

Example for Conky-

Step one:
Create a file named: conky.desktop.  Use your favorite text editor, I used leafpad.  Place the following code in the file:

```
[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=Conky
Exec=conky -c <location of your conky file>
StartupNotify=false
```My Exec line looked like this: 
Exec=conky -c /home/ajobim/Conky/conky03, ('conky03' being my conky setup.)

You do not have to make this file executable.  I saved it in my /home/ajobim/Conky folder, just to keep things orderly.  You can save it where ever you'd like, because your going to copy and paste it somewhere else anyways.

Step two:
Copy and paste 'conky.desktop' into /etc/xdg/autostart.

You'll notice a few other applications in this folder.  Now open Desktop Session Settings again from the menu and you will see Conky on the list=).

For kicks and grins I also copied a niffty little application I like to use called Quicksynergy and added it to the list in the same manner and it also started automatically upon logion.  Just remember to copy the .desktop file of the application you want to add to the list.  

Hope this helps anyone having issues auto starting applications with Lubuntu.

Cheers

---

### Post by Ego-X on 2012-10-25
> **ajobim said:**
> Yay me!!!!

After a few more Google attempts I found a work around.  Not sure if this is correct or not, I'm just ecstatic it works.

***This is for Lubuntu 11.10 using the default "openbox-lxde" session.***

As anyone who is using this particular Desktop environment/Window manager combo knows, when you select Preferences, Desktop Session Settings, Automatically Started Applications, you are given a list of applications with no option of adding any.  This is a way I found to manually add applications to this list.  

Example for Conky-

Step one:
Create a file named: conky.desktop.  Use your favorite text editor, I used leafpad.  Place the following code in the file:

```
[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=Conky
Exec=conky -c <location of your conky file>
StartupNotify=false
```My Exec line looked like this: 
Exec=conky -c /home/ajobim/Conky/conky03, ('conky03' being my conky setup.)

You do not have to make this file executable.  I saved it in my /home/ajobim/Conky folder, just to keep things orderly.  You can save it where ever you'd like, because your going to copy and paste it somewhere else anyways.

Step two:
Copy and paste 'conky.desktop' into /etc/xdg/autostart.

You'll notice a few other applications in this folder.  Now open Desktop Session Settings again from the menu and you will see Conky on the list=).

For kicks and grins I also copied a niffty little application I like to use called Quicksynergy and added it to the list in the same manner and it also started automatically upon logion.  Just remember to copy the .desktop file of the application you want to add to the list.  

Hope this helps anyone having issues auto starting applications with Lubuntu.

Cheers

I realise that this is an old post but just wanted to say thanks anyway

---

