---
title: "background slideshow"
date: 2010-10-19
forum: General Help
---

### Post by Legeril on 2010-10-19
I would like to to create a slide show of background images, is there an easy way to do this? I would like the image to change roughly every 12hrs to 1 day

---

### Post by chessnerd on 2010-10-19
Well, as a bit of shameless self-promotion, you could use this one that I made myself. :D

I think it works pretty well. It is written in Java and I hereby release it under the MIT license (so it is now open-source, source files are in the jar). You can run it with -
```
java -jar DesktopSlideshowMaker.jar
```

Or you can set it as executable with -
```
chmod +X DesktopSlideshowMaker.jar
```
And from that point on you can just double-click to run it.

If not, the XML files themselves are not too complicated to create and edit. I can explain it briefly if you would like to do it yourself...

EDIT: Sorry, it didn't add the archive for some reason. The file is now added...

---

### Post by Tamlynmac on 2010-10-19
I believe there's another alternative [here]("http://gbackground.sourceforge.net/"). 

It's available in the synaptic package manager for download. Trying different apps. may help you decide which one you prefer.

Good Luck

---

### Post by Legeril on 2010-10-19
I'd prefer to be able to write them myself to be honest, a big part of the reason I moved to Linux was to force myself to stop being so lazy and reliant of applications to do everything for me :P I'd very much appreciate it if you could give me a run down of how it works please

---

### Post by chessnerd on 2010-10-19
> **Legeril said:**
> I'd prefer to be able to write them myself to be honest, a big part of the reason I moved to Linux was to force myself to stop being so lazy and reliant of applications to do everything for me :P I'd very much appreciate it if you could give me a run down of how it works please
Fair enough. I shall educate you! :)

Here is how it works:

You start with a basic header, this will set the starting time of the animation to midnight, you can set the hour to anything from 0 to 23 (11 pm), minutes and seconds as 0-60:
```
<background>
  <starttime>
    <hour>00</hour>
    <minute>00</minute>
    <second>00</second>
  </starttime>
<!-- Start time for the animation (midnight) -->
```
Next, you add the images in two parts, the "static" part and the "transition" part:
The static part has two parts, duration and file. The duration is how long the image will be stationary and is done in seconds. The file is the file that will be stationary.
```
  <static>
    <duration>180.0</duration>
    <file>/home/jason/Pictures/DontTouchTheQueen.jpeg</file>
  </static>
```
The transition part has three parts, duration, from, and to. The duration is how long the transition (fading) will take. The "from" is what the current image is (the one from the earlier static) and the "to" image is the next one in the slideshow.
```
  <transition>
    <duration>5.0</duration>
    <from>/home/jason/Pictures/DontTouchTheQueen.jpeg</from>
    <to>/home/jason/Pictures/lfire-red.jpg</to>
  </transition>
```
Repeat this, going from static to transition until you get to the end. Then, your last one should go back "to" the first image.
Close the file with this:
```
</background>
```
And you are done! Save it as (name).xml and then add it under System > Preferences > Appearance > Background to your desktop background list.

If you have any questions, feel free to ask!

Below, I have an example file.

---

### Post by Legeril on 2010-10-19
Thanks a lot I will give this a try, I'll send you a PM if I have an issue

---

