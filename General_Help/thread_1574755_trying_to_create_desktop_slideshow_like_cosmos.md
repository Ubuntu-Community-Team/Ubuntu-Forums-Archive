---
title: "trying to create desktop slideshow like cosmos"
date: 2010-09-14
forum: General Help
---

### Post by boarder428 on 2010-09-14
I am trying to create a slideshow like cosmos, did not quite understand how to fill in the missing blanks with the scripts I found on the forum so I got this bright idea to edit the original cosmos xml file.  I put all my images in a folder called "surreal" inside the usr/share/backgrounds folder, edited the cosmos file with my image info in gedit and saved it as background-1.xml inside the surreal folder. ```
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
    <file>/usr/share/backgrounds/surreal/mountain1.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/surreal/mountain1.jpg</from>
    <to>/usr/share/backgrounds/surreal/mountain2.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/surreal/mountain2.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/surreal/mountain2.jpg</from>
    <to>/usr/share/backgrounds/surreal/park1.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/surreal/park1.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/surreal/park1.jpg</from>
    <to>/usr/share/backgrounds/surreal/park2.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/surreal/park2.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/surreal/park2.jpg</from>
    <to>/usr/share/backgrounds/surreal/water1.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/surreal/water1.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/surreal/water1.jpg</from>
    <to>/usr/share/backgrounds/surreal/water2.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/surreal/water2.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/surreal/water2.jpg</from>
    <to>/usr/share/backgrounds/surreal/mountain1.jpg</to>
  </transition>
 </background>

```
Does'nt seem to show up in the choose background list.  Do I need to make the file executable or is this just not an exceptable way to go about doing this?

---

### Post by pbrane on 2010-09-14
You could try this
[http://code.google.com/p/gnome-wallpaper-slideshow/]("http://code.google.com/p/gnome-wallpaper-slideshow/")
I haven't used it myself though.

---

### Post by robsoles on 2010-09-14
I copied the whole folder that comprises the 'cosmos' slideshow from where the backgrounds are kept in /usr/share/backgrounds to my home folder and then I renamed it, ditched the existing pics, put my pics in place and edited the filenames given in the xml file.

I copied my new copy back to /usr/share/backgrounds and made it belong to root. Then when I changed backgrounds I had to click the 'add' button in bottom right corner of background dialog box and select my new background - worked a beauty.

I will be trying the code linked by pbrane some time soon because it will be more convenient than manually re-writing (or writing from scratch) the xml control file.

---

### Post by boarder428 on 2010-09-14
I downloaded the software pbrane refferenced, I'll have to try it out tomorrow.  I don't think I made my file root if that could be the problem.  I seem to have done everything else robsoles stated, I did have to use gksudo nautilus to move the file to the backgrounds folder if that qualifies as making the file root. I also tried the add button but it would only let me pick one image out of the folder as the background and you could'nt shuffle thru the photos with the arrows like the cosmos file.

---

### Post by robsoles on 2010-09-14
to change ownership of the files to root open terminal
```
sudo 'chown -R root:root /usr/share/backgrounds/*your-slideshow-background-directory*'
```
of course you need to change *your-slideshow-background-directory* to the one you used - then when 'adding' the background you may have to change 'file-type' to any and then select the xml file instead of one of the pictures (can't remember for sure and can't access right now - am at work.).

---

### Post by boarder428 on 2010-09-15
thanks robsoles on the lesson of changing to root.  I'll have to play around with that a little more.  I tried the program pbrane recommended and it works great, even add's it to the backgrounds list.  Thanks pbrane for the link!

---

### Post by robsoles on 2010-09-16
no probs, sounds like the python script pbrane linked to must be getting root permission at some point of execution.

If this thread is solved then please consider using [COLOR="Red"]thread tools[/COLOR] above to mark it so.

---

### Post by robsoles on 2010-09-16
<snip>I hate it when it looks like I've double posted due connection fluctuation or simile</snip>

---

### Post by Vrroom on 2010-09-16
You can use a simple alternative without the need of editing xml files. Go here: [http://www.ubuntuvibes.com/2010/09/easily-create-picture-slideshows-and.html](http://www.ubuntuvibes.com/2010/09/easily-create-picture-slideshows-and.html)

---

### Post by robsoles on 2010-09-16
> **Vrroom said:**
> You can use a simple alternative without the need of editing xml files. Go here: [http://www.ubuntuvibes.com/2010/09/easily-create-picture-slideshows-and.html](http://www.ubuntuvibes.com/2010/09/easily-create-picture-slideshows-and.html)

Not as good (to me at least) as the python script that pbrane linked to. Some of us aren't as keen for java as others...

---

### Post by ngrieb on 2010-09-16
When looking for the background you just have to change the search option in the chooser window from image files to all files. Then you can see the XML files. Other than that just make sure your paths to the images in the stack are good. I had trouble with the slide shows working with an ATI card, but they seem to work fine otherwise...especially with desktop effects enabled.

---

### Post by boarder428 on 2010-09-26
You can also us "Drapes" if your looking for an application based way to do it.  I forgot about it until I was browsing an older Ubuntu book this morning.  It available in synaptic.  I'm trying it on my "Mint" desktop

---

