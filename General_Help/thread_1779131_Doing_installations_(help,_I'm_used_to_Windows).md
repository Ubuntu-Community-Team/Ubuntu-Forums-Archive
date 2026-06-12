---
title: "Doing installations (help, I'm used to Windows)"
date: 2011-06-10
forum: General Help
---

### Post by Scott M on 2011-06-10
I have Ubuntu up and running; now I want to install Eclipse and start porting some C++ code. (I should clarify - I already know I hate Eclipse, because I use it at work, and every chance I get I crawl back to friendly, helpful and quick Visual Studio. But I need to get better at Eclipse, so I'm trying to force myself to use it at home.)

I know how to install on Windows - you double click an installer, magic happens, and your new tool appears in your program list. Given how shiny Ubuntu is (my last unix experience was decades ago, back when X windows was pretty hot), I expected installation would be more or less the same - download Eclipse, click it, and done.

That's not working. I got Eclipse to install - in my Downloads directory, where I don't want it. When I try to run it, it complains I don't have a JRE. (This stunned me; what system doesn't have at least some version of Java installed out of the box?) I fetched one of those, bumbled around until I got the .bin file to run, and tried Eclipse again. Still no JRE. At least, no JRE in my path.

Clearly, I'm missing the concept of "how do I get applications to install in the appropriate place", with some additional lossage in the area of "how do I know what the appropriate place really is."

I think I need a pointer to a basic how-to. What can folk here recommend? (Yes, I know Windows has spoiled me, you don't need to point this out.) And is there some way to do all this with apt-get, instead of bumbling around with .gz and .bin files? TIA.

---

### Post by Shea6892 on 2011-06-10
Did you use the download manager to install the packages and check all the ones you wanted?

---

### Post by mastablasta on 2011-06-10
well you install first by searchign Software center for application and synaptic as well. if it''s there you just click it and run install.
 
JRE is never on a system out of the box. Windows doesn't have it out of the box (at least XP doesn't have it). Linux on the other hand has the opensource Icetea preinstalled. you can also install the javasun. how? again go to ubutnu software center select it and click install.
 
for the magic you describe from windows to work in Ubuntu and outside fo synaptic or software center you need to have a .deb file. if it's not a .deb file then there is going to be a readme file giving instructions on how to install it.
 
you can also do a search for PPA if someone prepared a package archive of newer version to install.
 
[https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)

---

### Post by polki@mac.com on 2011-06-10
I found this: [http://ubuntuforums.org/showthread.php?t=1744625](http://ubuntuforums.org/showthread.php?t=1744625)

Hope that helps, and welcome to the forums.

---

