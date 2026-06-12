---
title: "how do you make a slide show background"
date: 2011-05-25
forum: General Help
---

### Post by lance23dillon on 2011-05-25
Is there a way to create your own slide show for the desktop background for Ubuntu 11.04?

---

### Post by linuxinstalledfromhdd on 2011-05-25
**Gnome Wallpaper Slideshow**


**[http://cinderbox.net/2011/02/23/video-tutorial-perfect-ubuntu-10-10-desktop/](http://cinderbox.net/2011/02/23/video-tutorial-perfect-ubuntu-10-10-desktop/)**


[B]It's about half way down the list of add-ons.
[/B]

---

### Post by lance23dillon on 2011-05-25
cool, thanks for the help.

---

### Post by hwttdz on 2011-05-25
You could also do it yourself by copying the contents of one of the xml files contained in /usr/share/backgrounds/
example
```
<background>
  <starttime>
    <year>2009</year>
    <month>08</month>
    <day>04</day>
    <hour>00</hour>
    <minute>00</minute>
    <second>00</second>
  </starttime>
<!-- This animation will start at midnight. -->
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Arboreal_ballet_by_Bob_Farrell.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Arboreal_ballet_by_Bob_Farrell.jpg</from>
    <to>/usr/share/backgrounds/Berries_by_Orb9220.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Berries_by_Orb9220.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Berries_by_Orb9220.jpg</from>
    <to>/usr/share/backgrounds/Bird_by_Magnus.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Bird_by_Magnus.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Bird_by_Magnus.jpg</from>
    <to>/usr/share/backgrounds/Fabric_by_Just_Jeanette.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Fabric_by_Just_Jeanette.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Fabric_by_Just_Jeanette.jpg</from>
    <to>/usr/share/backgrounds/Green_by_Alan_Mattila.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Green_by_Alan_Mattila.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Green_by_Alan_Mattila.jpg</from>
    <to>/usr/share/backgrounds/Grey_day_by_Drew__.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Grey_day_by_Drew__.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Grey_day_by_Drew__.jpg</from>
    <to>/usr/share/backgrounds/Holes_by_FireCobold.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Holes_by_FireCobold.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Holes_by_FireCobold.jpg</from>
    <to>/usr/share/backgrounds/Ilunabarra_Azkainetik_by_Garuna_bor-bor.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Ilunabarra_Azkainetik_by_Garuna_bor-bor.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Ilunabarra_Azkainetik_by_Garuna_bor-bor.jpg</from>
    <to>/usr/share/backgrounds/La_no_alto_by_Allyson_Souza.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/La_no_alto_by_Allyson_Souza.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/La_no_alto_by_Allyson_Souza.jpg</from>
    <to>/usr/share/backgrounds/Quandro_by_Tomas_Vasconcelo.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Quandro_by_Tomas_Vasconcelo.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Quandro_by_Tomas_Vasconcelo.jpg</from>
    <to>/usr/share/backgrounds/Signpost_by_maroubal2.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Signpost_by_maroubal2.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Signpost_by_maroubal2.jpg</from>
    <to>/usr/share/backgrounds/Tiny_Worlds_by_matthileo.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Tiny_Worlds_by_matthileo.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Tiny_Worlds_by_matthileo.jpg</from>
    <to>/usr/share/backgrounds/Touch_the_light_by_Matt_Katzenberger.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Touch_the_light_by_Matt_Katzenberger.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Touch_the_light_by_Matt_Katzenberger.jpg</from>
    <to>/usr/share/backgrounds/Variations-On-Natty-Narwhal-1_by_madeinkobaia.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Variations-On-Natty-Narwhal-1_by_madeinkobaia.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Variations-On-Natty-Narwhal-1_by_madeinkobaia.jpg</from>
    <to>/usr/share/backgrounds/White_flowers_by_Garuna_bor-bor.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/White_flowers_by_Garuna_bor-bor.jpg</file>
  </static>
</background>

```
The syntax should be pretty clear.  I did this for a family member with some photos and they loved it.

---

### Post by wsamh on 2011-05-25
Install drapes from syanptic package manager. The program is easy to use.

---

### Post by J^3 on 2011-07-11
Thanks hwttdz!  I think yours was the best idea!  As a tip, to actually add the slideshow to your background list once you've completed it, when you click on "Add," you'll need to change from just "Images" to "All Files."    Then again, you could all probably figure that out, if you were able to figure out the (relatively simple) XML code =P.  Anyway, great solution!

---

### Post by malspa on 2011-07-13
Anyone know if Wally will work with Unity?

---

### Post by Gawains Green Knight on 2011-07-13
I can confirm Desktop Nova works great with Unity. You specify the folder with your images and how often you want it to change and you get a continually changing background.... very cool!

---

### Post by malspa on 2011-07-13
Cool, that's good to know about Desktop Nova!

Wally works, too. Tried it here. Had to follow some instructions from this page, though: [http://ubuntuincident.wordpress.com/2011/01/10/wallpaper-changer/](http://ubuntuincident.wordpress.com/2011/01/10/wallpaper-changer/)


> Update (20110509) [Unity patch]

Wally exists in the system tray. However, Ubuntu 11.04 introduced Unity that comes with a new top panel and applications are not allowed to be there by default. You need to enable explications explicitly. If you want to continue using wally, here is what to do:

First, get your current settings for systray-whitelist:


gsettings get com.canonical.Unity.Panel systray-whitelist


Then, add your application to the above list with this command:


gsettings set com.canonical.Unity.Panel systray-whitelist "[ your_previous_list_here, 'wally']"

---

