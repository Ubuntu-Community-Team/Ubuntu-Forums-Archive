---
title: "i tunes program?"
date: 2006-05-27
forum: General Help
---

### Post by LORD_PoLvO on 2006-05-27
hello does any 1 here know if there is an itunes program for ubuntu ( im using kde) or if there is an equivilent of an itunes program, ne help would be appreciated

---

### Post by caldevil on 2006-05-27
use amarok. Its the best music player there

---

### Post by LORD_PoLvO on 2006-05-27
i allready use amarok as a music player i need itunes to use my ipod properly..... ne1 know of a program or how i can get itunes windows install to work using wine?

---

### Post by Neo Ex on 2006-05-27
You can try gtkpod, it does a lot of things.

---

### Post by MaleqAlhaq on 2006-05-27
I think amaroK has a build in iPod Support, ....
According to this article ( [http://www.desktoplinux.com/articles/AT7150747782.html](http://www.desktoplinux.com/articles/AT7150747782.html) ) Banshee is a good iTunes Alternative for Linux.

//Edit: It does have iPod Support. In the main window go to Media Device, and hit Connect. I dont have an iPod, so I can't test this...

---

### Post by skymt on 2006-05-27
If you need to use the iTunes Music Store, or manage songs you bought from the Music Store, you need to use iTunes proper. The good news is, it's supported under [Crossover Office](http://www.codeweavers.com/). The bad news is, Crossover Office isn't free. I wouldn't recommend trying to use vanilla Wine for iTunes, it's more trouble than it's worth.

If you just use plain MP3s on your iPod, one of the open-source players like Banshee, amaroK, or (under Dapper) Rhythmbox.

---

### Post by adamkane on 2006-05-27
amaroK 1.4 has very good ipod support, and 1.4 is now available for breezy.

[http://amarok.kde.org/amarokwiki/index.php/1.4_for_Kubuntu_5.10]("http://amarok.kde.org/amarokwiki/index.php/1.4_for_Kubuntu_5.10")

```

sudo gedit /etc/apt/sources.list

``` 
Add this line to the file:

> 
deb [http://archive.czessi.net/ubuntu]("http://archive.czessi.net/ubuntu") breezy main universe
 

Save and close the file. Continue:

```

cd ~/Desktop
wget http://www.czessi.net/kczessi.gpg
sudo apt-key add kczessi.gpg
sudo apt-get update 

``` 

If amarok is already installed:

```

sudo apt-get dist-upgrade

``` 
  
If amarok isn't already installed:

```

sudo apt-get dist-upgrade[FONT=monospace]
[/FONT]sudo apt-get install amarok amarok-xine

``` 

Be aware that amarok-gstreamer is not available for amarok 1.4. You will be using amarok-xine.

---

### Post by jimarko on 2006-05-28
Just to put in my 2 cents:

Amarok 1.4 is a HUGE step up from 1.3 in respect to iPod/m4a support. Amarok can now actually read the song tags!

GTKpod is a good plan B, but at the moment, KDE/Amarok work GREAT for me, so give it a punt and let us know how it goes!! 


*excited*

---

### Post by ed_agamemnon on 2006-05-28
rhythmbox

edit: oh, for kde. ooops. sorry.
what's 'listen'? gtk aswell?

---

