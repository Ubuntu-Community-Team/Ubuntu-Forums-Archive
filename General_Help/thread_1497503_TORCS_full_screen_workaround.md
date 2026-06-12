---
title: "TORCS full screen workaround"
date: 2010-05-30
forum: General Help
---

### Post by srcsantos on 2010-05-30
This is how i got torcs to run full screen on my pc.

**The story**:
While my vga is able to handle 1280x768 as a desktop resolution, 800x600 is its best resolution for torcs.

**The problem**:
Setting torcs to 800x600 resolution and full screen mode, results in a frameless 800x600 window at the upper-left corner of my 1280x768 desktop.

**My solution**:
Create a simple script that changes the desktop resolution to 800x600 before running torcs and restores it to 1280x768 afterwards.

**My Procedure**:
**Step "0":** If you're inexperienced in Linux, please open a browser with your favorite search engine - you'll probably need it. :)
**Step 1**: Check if you have xrandr installed by running "xrandr" in a terminal. If you don't, please install the "x11-xserver-utils" package.
**Step 2**: If you haven't done so already, run torcs and set it to full screen mode and your desired resolution.
**Step 3:** Create an empty file where you would like the script to be placed (the desktop would be a good idea) and open it with a text editor.
**Step 4:** Add the following lines to the file, replacing "tocs_resolution" and "desktop_resolution" with the ones you want, and then close the file:
[INDENT]xrandr -s torcs_resolution > /dev/null 2>&1
torcs  > /dev/null 2>&1
xrandr -s desktop_resolution > /dev/null 2>&1
[/INDENT]Please note that "> /dev/null 2>&1" is not really necessary, and you can remove this from every line if you'd like to see the output of the applications.
**Step 5:** Set permissions to allow execution of the file.

And that's it! Just run the file in a terminal and you'll be able to play torcs in full screen. This isn't much of a solution, i know, but it's better than playing at 6fps... :P

---

### Post by kcode on 2012-11-11
I tried your solution, but somehow, it didn't work.

I have nvidia's graphic card and its resolution is set to 1366x768.
Making torcs resolution to 1366x768 did the job.

For that,
1. Start *torcs*
2. Goto *options*
3. Goto *display*
4. Adjustment the s*creen resolution* accordingly.

---

