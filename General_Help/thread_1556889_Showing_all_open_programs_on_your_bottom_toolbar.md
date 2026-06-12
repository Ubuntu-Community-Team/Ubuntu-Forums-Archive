---
title: "Showing all open programs on your bottom toolbar"
date: 2010-08-20
forum: General Help
---

### Post by COKEDUDE on 2010-08-20
[IMG]http://i255.photobucket.com/albums/hh133/COKEDUDEUSF/toolbar.jpg[/IMG]

Take a look at my picture to understand what I'm talking about. I have a bunch of programs open right now and I can't see the name of the programs on my toolbar. Is there hopefully a way to see all open programs on your toolbar when this happens? 

In windows OS's when you have multiple windows from the same program open they group themselves together, and on MAC OS's they have a toolbar that you can easily scroll through. So I hope there is a similar way to do this in Linux

---

### Post by bobcollard on 2010-08-20
Right click the Panel>Add New Items>Window List will group the open applications and windows together.  Might want to remove Icon Box which it looks like you have running now.

---

### Post by COKEDUDE on 2010-08-21
> **bobcollard said:**
> Right click the Panel>Add New Items>Window List will group the open applications and windows together.  Might want to remove Icon Box which it looks like you have running now.


[IMG]http://i255.photobucket.com/albums/hh133/COKEDUDEUSF/split.jpg[/IMG]

Ok this looks better, but it also created a new problem. Now all of my program icons are showing up twice on my toolbar. What do I do to stop that from happening? 

What is icon box and how do I remove it? I'm not familiar with this.

---

### Post by Frogs Hair on 2010-08-21
.

---

### Post by borth92 on 2010-08-21
there is an applet that uses just icons to display open programs on the toolbar...it works a lot like the wndows 7 superbar. you could give that a go.

1. Navigate to system>administration>software sources
2. add this to the list on the "other" tab: ppa:dockbar-main/ppa
3. open terminal and type: sudo apt-get update
4. then type this in terminal: sudo apt-get install dockbarx
5. Right click panel and select add...then select dockbarx

---

### Post by bobcollard on 2010-08-21
> **COKEDUDE said:**
> 
Ok this looks better, but it also created a new problem. Now all of my program icons are showing up twice on my toolbar. What do I do to stop that from happening? 

What is icon box and how do I remove it? I'm not familiar with this.
Icon Box is in the same menu you found Window List.  You will probably have to close most of your windows to get to the Panel, then right click an open area of the Panel and Remove Icon box. Or if it could be Task List.  Not sure what you had at first.

---

