---
title: "Background Transitions"
date: 2011-01-30
forum: General Help
---

### Post by Deersindal on 2011-01-30
I've just used crebs to set up a background slideshow as my wallpaper. The slideshow is present as a background and works fine, until the time comes for it to change slides.

If you were to change your background from background 0 to background 1 under the appearances and preferences window, your desktop would have a graceful fade effect between the two backgrounds. In my slideshow background, however, the slides don't fade; they just suddenly go from one to another.

So with that in mind, my question is: why aren't my slideshow slides fading? It isn't really a *huge* inconvenience, but this is my ubuntu we are talking about -- everything must be perfect :rolleyes:

---

### Post by JOHNNYG713 on 2011-01-30
It's been awhile since I used CREBS I use gnome-wallpaper-slideshow, But you should have two settings, picture duration= how long the selected image is shown and picture transition= how long the fade between images will last. I have included GWS if you want to check it out.
To install
 download and untar, open home folder, press Cntrl+h to open hidden files, 
 open .gnome2/nautilus scripts and place the gnome-wallpaper-slideshow.py, and close. right on your desktop open "scripts" click on gnome-wallpaper-slideshow and navigate to the folder containing your images, and set the duration and transition times, no need to name or adjust anything other than that ! :D

---

### Post by Deersindal on 2011-01-31
Hi, Johnny

I am not sure if the problem is with crebs... it seems to have created the .xml correctly in ~/.crebs.

Here is the contents of the file. Is it possible the .xml is in the wrong location? Thanks

-Deersindal

```
<!-- Name: Background -->
<background>
  <starttime>
    <year>2009</year>
    <month>09</month>
    <day>06</day>
    <hour>00</hour>
    <minute>00</minute>
    <second>00</second>
  </starttime>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Aqua Lines.png</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Aqua Lines.png</from>
    <to>/home/jonathan/Pictures/Wallpaper/Beach.jpg</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Beach.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Beach.jpg</from>
    <to>/home/jonathan/Pictures/Wallpaper/Black Ubuntu.jpg</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Black Ubuntu.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Black Ubuntu.jpg</from>
    <to>/home/jonathan/Pictures/Wallpaper/Blue Lines.png</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Blue Lines.png</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Blue Lines.png</from>
    <to>/home/jonathan/Pictures/Wallpaper/Blue Tiles.png</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Blue Tiles.png</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Blue Tiles.png</from>
    <to>/home/jonathan/Pictures/Wallpaper/Blue Ubuntu.jpg</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Blue Ubuntu.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Blue Ubuntu.jpg</from>
    <to>/home/jonathan/Pictures/Wallpaper/Charcoal Ubuntu.jpg</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Charcoal Ubuntu.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Charcoal Ubuntu.jpg</from>
    <to>/home/jonathan/Pictures/Wallpaper/Color Bars.jpg</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Color Bars.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Color Bars.jpg</from>
    <to>/home/jonathan/Pictures/Wallpaper/Color Spectrum 0.png</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Color Spectrum 0.png</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Color Spectrum 0.png</from>
    <to>/home/jonathan/Pictures/Wallpaper/Color Spectrum 1.jpg</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Color Spectrum 1.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Color Spectrum 1.jpg</from>
    <to>/home/jonathan/Pictures/Wallpaper/Color Spokes.jpg</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Color Spokes.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Color Spokes.jpg</from>
    <to>/home/jonathan/Pictures/Wallpaper/Creeper.jpg</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Creeper.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Creeper.jpg</from>
    <to>/home/jonathan/Pictures/Wallpaper/Dark Ocean.png</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Dark Ocean.png</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Dark Ocean.png</from>
    <to>/home/jonathan/Pictures/Wallpaper/Dark Wood.png</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Dark Wood.png</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Dark Wood.png</from>
    <to>/home/jonathan/Pictures/Wallpaper/Firey Swirl.png</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Firey Swirl.png</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Firey Swirl.png</from>
    <to>/home/jonathan/Pictures/Wallpaper/Glowing Ubuntu.jpg</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Glowing Ubuntu.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Glowing Ubuntu.jpg</from>
    <to>/home/jonathan/Pictures/Wallpaper/Gray Pipes.jpg</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Gray Pipes.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Gray Pipes.jpg</from>
    <to>/home/jonathan/Pictures/Wallpaper/Gray Stripes.png</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Gray Stripes.png</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Gray Stripes.png</from>
    <to>/home/jonathan/Pictures/Wallpaper/Green and Lines.jpg</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Green and Lines.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Green and Lines.jpg</from>
    <to>/home/jonathan/Pictures/Wallpaper/Green Star.PNG</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Green Star.PNG</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Green Star.PNG</from>
    <to>/home/jonathan/Pictures/Wallpaper/Hawaii.jpg</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Hawaii.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Hawaii.jpg</from>
    <to>/home/jonathan/Pictures/Wallpaper/Hex Ubuntu.jpg</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Hex Ubuntu.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Hex Ubuntu.jpg</from>
    <to>/home/jonathan/Pictures/Wallpaper/Mountains.jpg</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Mountains.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Mountains.jpg</from>
    <to>/home/jonathan/Pictures/Wallpaper/Ocean.jpg</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Ocean.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Ocean.jpg</from>
    <to>/home/jonathan/Pictures/Wallpaper/Orange Ubuntu.jpg</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Orange Ubuntu.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Orange Ubuntu.jpg</from>
    <to>/home/jonathan/Pictures/Wallpaper/Paint Splatters.jpg</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Paint Splatters.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Paint Splatters.jpg</from>
    <to>/home/jonathan/Pictures/Wallpaper/Power Button.png</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Power Button.png</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Power Button.png</from>
    <to>/home/jonathan/Pictures/Wallpaper/Red Ubuntu.jpg</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Red Ubuntu.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Red Ubuntu.jpg</from>
    <to>/home/jonathan/Pictures/Wallpaper/Rusted Ubuntu.jpg</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Rusted Ubuntu.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Rusted Ubuntu.jpg</from>
    <to>/home/jonathan/Pictures/Wallpaper/Snowy Alps.jpg</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Snowy Alps.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Snowy Alps.jpg</from>
    <to>/home/jonathan/Pictures/Wallpaper/Snowy Branches.jpg</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Snowy Branches.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Snowy Branches.jpg</from>
    <to>/home/jonathan/Pictures/Wallpaper/Snowy Trees.jpg</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Snowy Trees.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Snowy Trees.jpg</from>
    <to>/home/jonathan/Pictures/Wallpaper/Speaker Ruins.jpg</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Speaker Ruins.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Speaker Ruins.jpg</from>
    <to>/home/jonathan/Pictures/Wallpaper/Virus.jpg</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Virus.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Virus.jpg</from>
    <to>/home/jonathan/Pictures/Wallpaper/Yin and Yang Explosion.jpg</to>
  </transition>

  <static>
    <duration>595.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Yin and Yang Explosion.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Yin and Yang Explosion.jpg</from>
    <to>/home/jonathan/Pictures/Wallpaper/Aqua Lines.png</to>
  </transition>

</background>
<!-- Created 2011-01-30 17:17:07 with Create Background Slideshow 0.9.8.5 -->
```

---

### Post by Deersindal on 2011-02-02
Does anyone have any ideas about what could be happening? I'm still having the same problems.

---

### Post by Deersindal on 2011-02-15
Problem solved to anyone else who is having this problem... Simply add the line in bold to your .xml file before each individual wallpaper. The default seems to be a sudden change, and you need to specify the transition type if you want something other than the default. :popcorn:

```
<?xml version="1.0" encoding="utf-8"?>
<background>
  <starttime>
    <year>2010</year>
    <month>01</month>
    <day>01</day>
    <hour>00</hour>
    <minute>00</minute>
    <second>00</second>
  </starttime>
  <static>
    <duration>300.0</duration>
    <file>/home/jonathan/Pictures/Wallpaper/Ancient Tree.jpg</file>
  </static>
  **<transition type="fade">**
    <duration>5.0</duration>
    <from>/home/jonathan/Pictures/Wallpaper/Ancient Tree.jpg</from>
    <to>/home/jonathan/Pictures/Wallpaper/Aqua Lines.png</to>
  **</transition>**
```

---

