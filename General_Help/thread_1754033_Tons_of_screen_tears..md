---
title: "Tons of screen tears."
date: 2011-05-09
forum: General Help
---

### Post by ThePhysician on 2011-05-09
I'm running 11.04 with an HD 5870 that should seriously just fly. But instead (in Unity or Ubuntu Classic) there are tears from almost everything. Sometimes when I open a window, everytime I scroll, sometimes if I just move the mouse around enough.

I turned on proprietary drivers, and tried turning them off. No matter what 11.04 is just abysmally slow in the graphics department.

---

### Post by jerome1232 on 2011-05-09
In ccsm is Sync to Vblank checked (I believe that should reduce tearing) Under OpenGL

What driver do you have installed, From my quick google search 11.4 Catalyst is the latest, I have very little experience with ATI but I did come across this how to for installing the 11.4 drivers.

[http://www.downloadatoz.com/driver/articles/how-to-install-amd-catalyst-11-4-graphics-driver-for-linux-in-ubuntu-11-04.html](http://www.downloadatoz.com/driver/articles/how-to-install-amd-catalyst-11-4-graphics-driver-for-linux-in-ubuntu-11-04.html)

Please note that this how to is untested by me and I only quickly glanced it over, let me know if your issue is more specifc than that.

---

### Post by jeremy1138 on 2011-05-09
Go into the Catalyst control center and enable the tear free desktop.  Then install the compiz settings manager and disable sync to v-blank.

That's how I got my computer working smoothly.  Hope that helps.

(edit)
See this:

[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

for instructions on how to disable sync to vblank.  It also has some other cool stuff you may wish to try.

---

### Post by ThePhysician on 2011-05-09
Whenever I click on "ati-driver-installer-11-4-x86.x86_64.run" that it downloaded it says it could not open it. I'm guessing because I don't want to open it in gedit. What do I want to try to launch that with? >.>

---

### Post by jerome1232 on 2011-05-09
> **ThePhysician said:**
> Whenever I click on "ati-driver-installer-11-4-x86.x86_64.run" that it downloaded it says it could not open it. I'm guessing because I don't want to open it in gedit. What do I want to try to launch that with? >.>

If I was you, I'd ignore me and listen to jeremy1138, I was merely trying to help, he seems to have experience with ATI, I do not.

---

### Post by ThePhysician on 2011-05-09
Well, I actually don't even have 11.4 CCC installed because Ubuntu thinks 11.2 is the most recent one. So if either of you can assist me in getting 11.4 first that'd be great. Because hopefully it finally provides Eyefinity support. 

Blah. So much stuff wrong with my video drivers right now that screen tearing was just the top on my list.

---

### Post by jeremy1138 on 2011-05-09
I think you should use the drivers that the hardware manager in Ubuntu gives you but you may wish to ignore me and go ahead and install the latest ones.

In that case, you will need to right click on the .run file that you've downloaded, select properties and then permissions, and check the box to make it executable.  Then double click on it and it should run for you.

See this:

[https://help.ubuntu.com/community/InstallingRunPackage](https://help.ubuntu.com/community/InstallingRunPackage)

for more instructions on installing a .run file.

Let us know how it turns out for you.

---

