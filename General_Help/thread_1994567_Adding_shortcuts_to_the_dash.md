---
title: "Adding shortcuts to the dash?"
date: 2012-06-02
forum: General Help
---

### Post by Straemer on 2012-06-02
So I have a bunch of games that weren't installed via the software center. Currently I just have a bunch of launchers on my desktop, as well as a couple bash scripts. Is it possible to manually put these shortcuts into the dash? I would like to be able to have them show up under the "games" filter in the applications lens as well. How would I go about doing this?

---

### Post by Paddy Landau on 2012-06-03
To simply add a shortcut to the launcher, start your program. When the icon appears in the launcher, right-click and select *Lock to Launcher*.

However, if you want to add your icon to the main menu, install [alacarte]("apt:alacarte"). Then run Main Menu and make your changes there. Sometimes, you have to log out and in again before the changes are recognised, but not always.

---

### Post by Vaphell on 2012-06-03
if you want them to be recognized by the system you need to create .desktop files for them
[https://linuxcritic.wordpress.com/2010/04/07/anatomy-of-a-desktop-file/](https://linuxcritic.wordpress.com/2010/04/07/anatomy-of-a-desktop-file/)

---

### Post by Paddy Landau on 2012-06-03
> **Vaphell said:**
> if you want them to be recognized by the system you need to create .desktop files for them
[https://linuxcritic.wordpress.com/2010/04/07/anatomy-of-a-desktop-file/](https://linuxcritic.wordpress.com/2010/04/07/anatomy-of-a-desktop-file/)
Main Menu (alacarte) will do that for you.

---

### Post by Cavsfan on 2012-06-03
> **Paddy Landau said:**
> To simply add a shortcut to the launcher, start your program. When the icon appears in the launcher, right-click and select *Lock to Launcher*.

However, if you want to add your icon to the main menu, install [alacarte]("apt:alacarte"). Then run Main Menu and make your changes there. Sometimes, you have to log out and in again before the changes are recognised, but not always.

Interesting! What if you add more than what can show on the screen? Would the Launcher then scroll?

---

### Post by Paddy Landau on 2012-06-03
> **Cavsfan said:**
> Interesting! What if you add more than what can show on the screen? Would the Launcher then scroll?
There is a "See 10 more results" type of message with the option to scroll.

---

### Post by Cavsfan on 2012-06-03
> **Paddy Landau said:**
> There is a "See 10 more results" type of message with the option to scroll.
Good to know! Thanks! I am still on lucid but, also learning Precise.
I guess alacarte was installed when I installed Gnome Classic. I am learning both with Unity and Gnome Classic.

---

### Post by Paddy Landau on 2012-06-03
> **Cavsfan said:**
> I guess alacarte was installed when I installed Gnome Classic.
:confused: Gnome Classic comes by default with Ubuntu 12.04; you don't have to install it. You simply select it when logging on if you don't want Ubuntu 3D.

---

### Post by Cavsfan on 2012-06-03
> **Paddy Landau said:**
> :confused: Gnome Classic comes by default with Ubuntu 12.04; you don't have to install it. You simply select it when logging on if you don't want Ubuntu 3D.

It did not come on my install and I download the ISO on April 26 when the RC was released. I had to sudo apt-get install it.

I got it off of this sticky and I only did what is on post 4.

[http://ubuntuforums.org/showthread.php?t=1859961](http://ubuntuforums.org/showthread.php?t=1859961)

I am pretty sure it only had 2 options after I installed it: Ubuntu and Ubuntu 2D.
Then when I installed Compiz and Cairo Dock other options showed up.
 After taking the above step, Gnome Classic showed up.

---

### Post by Straemer on 2012-06-03
Thanks! I just added the .desktop files in manually, easy enough.

---

### Post by chocklet on 2012-06-04
"Interesting! What if you add more than what can show on the screen?"

Another option... You can put several games in one .desktop file.

Choices (menu items) can be added to the right click of an icon on the laucher bar.  For example, You can add new "Actions" to one .desktop file so that the action line looks like this:

```
Actions=NewAna;NewBog;NewBri;NewFif;NewGal;NewGue;NewGwe;NewIne;NewLig;NewMin;NewNet;NewOY;NewPys;NewRec;NewSam;NewUnt;

```and then include actions paragraphs that look like like this:

```
[Desktop Action NewPys]
Name=PySol Fan Club Edition
Exec=pysolfc
```Then lock the game laucher to the launcher bar.

Now, when the game launcher is right-clicked, there are 16 games to choose from.

---

### Post by Paddy Landau on 2012-06-04
> **Cavsfan said:**
> It did not come on my install and I download the ISO on April 26 when the RC was released. I had to sudo apt-get install it.
That is so weird. With me, it came included.

> **Straemer said:**
> Thanks! I just added the .desktop files in manually, easy enough.
Excellent, I'm glad your problem is solved. Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by nicolasforum89 on 2012-06-04
With me as well.

---

