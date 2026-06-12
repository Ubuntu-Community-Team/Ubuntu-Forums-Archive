---
title: "I want my desktop back!"
date: 2010-10-13
forum: General Help
---

### Post by compmom on 2010-10-13
I installed 10.10 and two things are driving me crazy.  I can't fix which is telling me it is something so easy and obvious it is over my head!

1.   I want the desktop that was installed with 10.04 where there was a colorful side bar which you clicked on and it went to all the icons in that category, real nice and smooth.  Now all I can get is something more like a traditional Windows set up with the bar panels.  This is messing with my head bad.

2.  My bookmarks on Firefox doesn't show the icon specific to sites but instead has a standard "page" pic that sometimes does and sometimes does not take on the sites logo when I click on it.

Yeah, minor things but I am a creature of habit.  Thank you.

---

### Post by Refalm on 2010-10-13
> **compmom said:**
> 1.   I want the desktop that was installed with 10.04 where there was a colorful side bar which you clicked on and it went to all the icons in that category, real nice and smooth.  Now all I can get is something more like a traditional Windows set up with the bar panels.  This is messing with my head bad.
By "colourful sidebar", do you mean the left panel in the file-browser?
If so, just hit F9.

---

### Post by Quackers on 2010-10-13
Welcome to ubuntuforums :-)
Did your "colorful side bar which you clicked on and it went to all the icons in that category" look like the one in the screenshot?
If so you need to install cairo dock. There are others similar as well.

---

### Post by JackNocturne on 2010-10-13
hello,

I'm not so sure but i can offer 2 cents. I think your configuration file was overwritten when you upgraded. 

Open **terminal** from accessories and type the following

```
ls -a ./.gconf

```Print the output here

---

### Post by roggenschrotbrot on 2010-10-13
[http://media.cdn.ubuntu-de.org/wiki/attachments/42/44/37332264.png]("http://media.cdn.ubuntu-de.org/wiki/attachments/42/44/37332264.png")
is this what you mean?

---

### Post by marl30 on 2010-10-13
To get all your bookmark icons showing,  install Ubuntu Tweak:[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)  - then go to Gnome Menu option in Ubuntu Tweak and tick: Show icons in menus and show icons in buttons.

---

### Post by compmom on 2010-10-13
> **Quackers said:**
> Welcome to ubuntuforums :-)
Did your "colorful side bar which you clicked on and it went to all the icons in that category" look like the one in the screenshot?
If so you need to install cairo dock. There are others similar as well.

no, it was like this:

[http://opentechblog.com/2010/04/a-look-at-ubuntu-10-04-netbook-remix/](http://opentechblog.com/2010/04/a-look-at-ubuntu-10-04-netbook-remix/)

---

### Post by compmom on 2010-10-13
Yes!!!!!!

---

### Post by compmom on 2010-10-13
.  ..  apps  desktop  system

---

### Post by compmom on 2010-10-13
> **JackNocturne said:**
> hello,

I'm not so sure but i can offer 2 cents. I think your configuration file was overwritten when you upgraded. 

Open **terminal** from accessories and type the following

```
ls -a ./.gconf

```Print the output here


.  ..  apps  desktop  system

---

### Post by compmom on 2010-10-13
> **roggenschrotbrot said:**
> [http://media.cdn.ubuntu-de.org/wiki/attachments/42/44/37332264.png](http://media.cdn.ubuntu-de.org/wiki/attachments/42/44/37332264.png)
is this what you mean?

yes!!

---

### Post by compmom on 2010-10-13
> **marl30 said:**
> To get all your bookmark icons showing,  install Ubuntu Tweak:[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)  - then go to Gnome Menu option in Ubuntu Tweak and tick: Show icons in menus and show icons in buttons.

Cannot find a :Gnome Menu option......

---

### Post by roggenschrotbrot on 2010-10-13
[http://ubuntuforums.org/showthread.php?t=1592796&highlight=netbook]("http://ubuntuforums.org/showthread.php?t=1592796&highlight=netbook")
this should help you.

---

### Post by compmom on 2010-10-13
> **roggenschrotbrot said:**
> [http://ubuntuforums.org/showthread.php?t=1592796&highlight=netbook](http://ubuntuforums.org/showthread.php?t=1592796&highlight=netbook)
this should help you.

Thank you.  I am not sure I under stand what to do with the following from that discussion.  I have figured out in is netbook lucid interface?  Now why would anybody get rid of such linux efficiency and go, on the latest version, to a Microsoft Windows type thingy?   Any more-to-a-novice steps on how to achieve:

 				 				**Re: Maverick with old netbook interface - how?** 			
 			 			 		   		 		 		I got a passable imitation of Lucid's interface going in maverick using EFL.

1: I installed netbook-remix-efl, maximus, go-home-applet and window-picker applet
2:When installed, log out and start an ubuntu netbook 2D session
3: Remove the bottom panel, remove the main menu and window list applets from the top panel
4: Add go-home-applet and window-picker-applet to the top panel.
5: Make sure you start add maximus to your startup applications

Login and logout and you're good!

---

### Post by roggenschrotbrot on 2010-10-13
it's never been installed with the desktop edition. either you had installed the netbook-edition of lucid or you installed the netbook interface later on. the lucid netbook interface has been replaced with the new unity interface: [http://www.webupd8.org/2010/05/taking-ubuntu-unity-interface-for-test.html]("http://www.webupd8.org/2010/05/taking-ubuntu-unity-interface-for-test.html"). from the sounds of it you are runing standard gnome atm.

> 1: I installed netbook-launcher-efl, maximus, go-home-applet and window-picker applet
search for and install the above packages in synaptic / softwarecenter or type
```
sudo apt-get install netbook-launcher-efl maximus go-home-applet window-picker-applet
```
in terminal
> 2:When installed, log out and start an ubuntu netbook 2D session
in your login screen you can select you session somewhere in the bottom panel.
> 3: Remove the bottom panel, remove the main menu and window list applets from the top panel
you can remove panels and panel-applets by right-clicking them and selecting the option (can't remember what its called, im not runing gnome atm)
> 4: Add go-home-applet and window-picker-applet to the top panel.
panel applets can be added by rightclicking a panel, selecting "add to panel" and either selection a applet in the now opening dialog window or drag and drop it to where you want it
> 5: Make sure you start add maximus to your startup applications
you can set which applications to start in "system->settings->startup-applications". if you add maximus there you'll get the default behavior of the prior netbook editions: windows will always be maximized, on a desktop this is most likely not what you want, so just skip this step.

you can also try the unity interface by installing the package "ubuntu-netbook" as mentioned above. this will ad a new session entry to your login screen.

---

### Post by Refalm on 2010-10-13
[Please remove]

---

### Post by marl30 on 2010-10-13
> **compmom said:**
> Cannot find a :Gnome Menu option......

Ok, sorry about not being clear enough. It's under the desktop menu/Gnome Settings in Ubuntu Tweak.

---

