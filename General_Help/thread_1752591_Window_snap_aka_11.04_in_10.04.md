---
title: "Window snap aka 11.04 in 10.04"
date: 2011-05-08
forum: General Help
---

### Post by InTheNameOfDelicious on 2011-05-08
Good time of the day fellow Ubuntu users. I'm wondering if there's any way to get the "window snap" feature in 10.04, i.e. so that windows resize to half-width-full-height when you touch the edge of the screen with the cursor while dragging a window (but not just when you do the latter)? It doesn't seem like that's a Unity specific feature in 11.04. I was messing with it earlier today and snap still worked in gnome when I installed it. Is there a separate package for snap I can install in 10.04?
Thank you.

---

### Post by wilee-nilee on 2011-05-08
> **InTheNameOfDelicious said:**
> Good time of the day fellow Ubuntu users. I'm wondering if there's any way to get the "window snap" feature in 10.04, i.e. so that windows resize to half-width-full-height when you touch the edge of the screen with the cursor while dragging a window (but not just when you do the latter)? It doesn't seem like that's a Unity specific feature in 11.04. I was messing with it earlier today and snap still worked in gnome when I installed it. Is there a separate package for snap I can install in 10.04?
Thank you.

Argh captain here yee be.
[http://www.omgubuntu.co.uk/2009/11/get-aero-snap-in-ubuntu/](http://www.omgubuntu.co.uk/2009/11/get-aero-snap-in-ubuntu/)

---

### Post by InTheNameOfDelicious on 2011-05-08
Sorry, this doesn't earn you a peace of mein cake.
That's just a work around with ccsm. I tried it, and only the maximization part worked; the 1/2 width doesn't. Also, with this it would run the command on the active window every time I hold the cursor near the edge. What I'm wondering about is what they use in 11.04. That works even without ccsm installed. I thought that may be a stand alone program.

---

### Post by yetiman64 on 2011-05-08
> **InTheNameOfDelicious said:**
> Sorry, this doesn't earn you a peace of mein cake.
That's just a work around with ccsm. I tried it, and only the maximization part worked; the 1/2 width doesn't. Also, with this it would run the command on the active window every time I hold the cursor near the edge. What I'm wondering about is what they use in 11.04. That works even without ccsm installed. I thought that may be a stand alone program.

Even without ccsm installed compiz itself is used in 11.04, ccsm is only a settings manager for compiz. 

The grid plug-in is used in 11.04, you can enable it in 10.04 as well, but you are restricted to using the keypad controls only as there is no edges tab in 10.04.

From the same source as linked by wilee-nilee, I had to work on the commands, copying from the webpage apparently changes some of the symbols. Using the comments at the bottom of the page, I adjusted them to get the 2 commands working you are having problems with. I posted the commands in a code box [[COLOR=Blue]--here--[/COLOR]]("http://ubuntuforums.org/showpost.php?p=10730463&postcount=3") , the code box should keep the symbols correct for you to compare them with. Actually I think I may have copied the commands from one of the commenters there, not the code posted at the top.

You are correct about the active window and the edge running the command when you don't mean to. Also if you get that working, try clicking the desktop to take the focus off any window then try out both the edges, you can get some mighty strange effects running with the desktop cube in use as well :). Check out the attached screenshot for one of the weird effects it causes. The second screenshot is what it should be like without an edge activated.

Not a real good solution, but it seems to be that or keypad only use with the grid plugin for 10.04.

**Edit:** one extra idea I use with the link from wilee-nilee, is rather than using the edges and the top, I use the four corners instead (I needed an extra "edge" for the fourth command I added to the other UF post above for returning a maximized window to its previous state). Also I don't mention the edges in that link as the OP there only asked about key combinations. This may help a bit with the accidental edge activation you note.

---

### Post by excetara2 on 2011-05-08
Assuming you have grid installed. Then just sudo apt-get install xautomation.

Put commands in ccsm commands section (preferred) or keyboard shortcuts like:

xte 'keydown Control_L' 'key Left' 'keyup Control_L'

For this I have window resize to left half in grid as key combination of ctrl + left.

xte is in xautomation package and allows automatic imitation of keypresses. [http://manpages.ubuntu.com/manpages/hardy/man1/xte.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/xte.1.html)

What I love about this is you can also still have dragging windows between workspaces still set.

Cheers

---

### Post by excetara2 on 2011-05-08
If you don't have grid installed just install package:

compiz-fusion-plugins-extra

---

### Post by yetiman64 on 2011-05-08
> **excetara2 said:**
> If you don't have grid installed just install package:

compiz-fusion-plugins-extra
Actually I forgot the grid plugin is in the extra package, thanks excetara2. I have that installed here and by activating the grid plugin I already have  CTRL + ALT + <KP#> control of the active window. 

ctrl+alt+kp4 sends the active window to the left half screen.
ctrl+alt+kp6 sends the active window to the right half screen. and so on down the list.

What I am wondering is what does the xautomation package actually do? Is it to reassign the key combination to a simpler one only, or does it have some other use ?

You are right, you can use both the grid and the commands plugins for this together.

---

### Post by excetara2 on 2011-05-08
xautomation installs a package for automation of controlling X. In laymen terms, basically xte simulates the keypress even though your not actually doing it. Through the commands this keypress that causes grid to resize the screen can be binded to an edge binding. I find this a lot more stable or I like the way it works better than the wmctrl option. Both work. Here is a more advanced description of xautomation:

Control X from the command line for scripts, and do "visual scraping" to
 find things on the screen. The control interface allows mouse movement,
 clicking, button up/down, key up/down, etc, and uses the XTest extension so
 you don't have the annoying problems that xse has when apps ignore sent
 events. The visgrep program find images inside of images and reports the
 coordinates, allowing programs to find buttons, etc, on the screen to click
 on.

---

### Post by yetiman64 on 2011-05-08
> **excetara2 said:**
> xautomation installs a package for automation of controlling X. In laymen terms, basically xte simulates the keypress even though your not actually doing it. Through the commands this keypress that causes grid to resize the screen can be binded to an edge binding. I find this a lot more stable or I like the way it works better than the wmctrl option. Both work. Here is a more advanced description of xautomation:

Control X from the command line for scripts, and do "visual scraping" to
 find things on the screen. The control interface allows mouse movement,
 clicking, button up/down, key up/down, etc, and uses the XTest extension so
 you don't have the annoying problems that xse has when apps ignore sent
 events. The visgrep program find images inside of images and reports the
 coordinates, allowing programs to find buttons, etc, on the screen to click
 on.
Ok, thanks, I will try this out and experiment a bit. :)

---

### Post by excetara2 on 2011-05-08
To answer the other part. With the Grid plug-in installed, you can change the key bindings within the Grid plug-in. You don't need an external plug-in to do this. I just preferred the Ctrl+left and Ctrl+right. This is one of my most used commands because I have dual screens. Obvi edge bindings don't work on the inside edges.

Side Note:
If you keep doing the command in grid, it resizes 1/2 then 1/4 then 3/4. If I'm coding python or something where want access to terminal to run scripts. I'll do a 1/4 terminal and 3/4 program often.

---

### Post by excetara2 on 2011-05-08
Let me know how it goes :)! Where you at in Qld?

---

### Post by yetiman64 on 2011-05-09
> **excetara2 said:**
> Let me know how it goes :)! Where you at in Qld?

Thanks excetara2, further to the PM, This is brilliant, I can get the effects now with no unusual side effects as I described earlier.

OP if you want to test out xte to see if it meets your needs [[COLOR=Blue]--here--[/COLOR]]("http://www.youtube.com/watch?v=XvlTlyEasD8") is a video to demonstrate how it works and is set up.  The video uses the standard keypad setup of the grid plug-in but adds xte commands to the command plug-in and sets edge bindings to them. You need only set up the movements you specifically want in the commands section.

The same problem will occur as you mentioned earlier with accidental active window movement when the cursor near the sides, but you could consider setting up custom keboard and/or mouse button combinations to do the window moving instead of using edges. I have it working like that here. **Edit**: have now reverted to using the four corners (edge binding) due to apparent clashes with existing bindings in other plugins. /edit

This method however won't move your desktop wallpaper or cut the faces of the desktop cube in two like wmctrl does. xte makes a massive performance improvement compared to my last setup. Cheers and thanks again to excetara2.

---

### Post by InTheNameOfDelicious on 2011-05-09
Thanks a lot excetara2 and yetiman64, this works great and even offers more functionality then I originally wanted to get. I ended up using key binding - Super+1,2,3,4 for corners and Super+z,x for sides.
One question though. Is there any way to give a window its original size after I snap it using Grid?

---

### Post by yetiman64 on 2011-05-09
> **InTheNameOfDelicious said:**
> Thanks a lot excetara2 and yetiman64, this works great and even offers more functionality then I originally wanted to get. I ended up using key binding - Super+1,2,3,4 for corners and Super+z,x for sides.
One question though. Is there any way to give a window its original size after I snap it using Grid?

Only way I have been able to work that so far is to use the functionality of the window title bar with a double click to go either down or up. There may be a way of doing it but it isn't included in the grid plugin that I'm aware of.

Also note with this plugin what happens when you tap the same edge more than once, I found using two taps of the edge to go to the bottom half of the screen will reduce the window to a small square, from there it makes double clicking the window title bar very easy to use.

---

### Post by excetara2 on 2011-05-09
In regards to active window movement,

You can change in the general settings of compiz the time you have to be near the edge time trigger. This isn't what it is called exactly. It is the time before the edge bindings will activate.

Secondly, conflicts are fine depending what they are. If it's the desktop wall plugin which is usually where the conflict occurs. You can leave both if your edge time is long enough. I have both. I think I have my edge time like .3 or .4 seconds. It is relatively quick but enough that when I drag between workspaces I don't have a problem. Then put the edge flipping to edge flip move. The other two unchecked. Then set the top, bottom, left, and right edges. They can be the same as the grid plug-in. Had this setup for ages and had no problems.

Third, should be able to do what you are saying by toggling a window with a keyboard command. It would require a little hacking I think because don't think there is a setting for it directly in compiz (at least as far as I know). It remembers the size of the previously drawn window as has been said if you double click the title bar or drag it away from its current position. It goes to the previously drawn size of your window.

---

### Post by InTheNameOfDelicious on 2011-05-10
Are you talking about how it remembers the size of the window when you maximize it and then restores it when you double-click on the title bar or move it? Yes, that would be an ideal solution if there was a way to make that code run with my keyboard shortcuts!

---

### Post by InTheNameOfDelicious on 2011-05-10
I'm thinking about writing two scripts. One that gets the active window size, stores it somewhere, then runs one of the snapping commands, and assigning that to the commands in compiz. Another that gets the current window id, gets the stored size, and applies it to the window. There probably isn't any way of assigning the latter script to dragging or double-clicking the window resized with the first one, but I could just set up another keyboard command to restore the original size - that should be good enough.

Anybody have any advice on how to get, store, and assign size to windows? I just found this thread [http://ubuntuforums.org/showthread.php?t=1244691](http://ubuntuforums.org/showthread.php?t=1244691) I'm more curious about a possible storing scheme. I'd imagine using a simple txt file is just awfully inefficient. Maybe creating environmental variables would be better?

---

