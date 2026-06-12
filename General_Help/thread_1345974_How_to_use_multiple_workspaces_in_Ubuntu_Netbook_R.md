---
title: "How to use multiple workspaces in Ubuntu Netbook Remix 9.10"
date: 2009-12-04
forum: General Help
---

### Post by ohiomoto on 2009-12-04
First of all, let me say that I love UNR.  It just works for me because everything you need to navigate in and between applications is right at the top of the screen.

The only thing I didn't like was that by default, UNR limited you to only one workspace or desktop.  I like to keep my projects and applications on separate workspaces.  I might have a music player and a web browser open on one workspace, a IDE and a terminal on another.  This way I can quickly find the applications I need without having my "personal" stuff getting in the way of my "project" or visa versa.

It's not difficult to work with multiple workspaces in UNR.  I recently did a fresh install on one of my laptops so I decided to make the guide that explains how to configure and use workspaces in Remix.  

It only takes a few clicks and about 10 minutes....

---

### Post by ohiomoto on 2009-12-04
Launch Pad user jfmchivall suggested an even easier way to accomplish the first 5 steps of this guide.  If you use the  alternative method,  go directly to post #3.

**Alternative Method**
[QUOTE=jfmchivall proposed the following answer:]
You can more simply change the number of workspaces by launching gconf-
editor and going to apps->metacity->general and changing the value for
num_workspaces.

Or, even quicker, in a terminal type:
gconftool-2 -s /apps/metacity/general/num_workspaces 4 --type int

change 4 above to however many workspaces you want.
[/QUOTE] 

 
**Original Method**
1)  Go to the top left corner. Right click the divider that is located just to the left of the Go Home icon.
[ATTACH]138544[/ATTACH]

2)  Unlock and move the divider slightly to the right.  Now lock it to the panel.  This makes enough space to right click the panel.  
[ATTACH]138545[/ATTACH]

3)  Right click the panel > Add to panel.. > Workspace Switcher 
[ATTACH]138546[/ATTACH]

4)  Right click the switcher > Preferences > Number of workspaces > 4 (or whatever you want.)  
[ATTACH]138547[/ATTACH]
[ATTACH]138549[/ATTACH]

5)  Right click the switcher > Remove from panel (unless you actually like the switcher up there.)

Continued...

---

### Post by ohiomoto on 2009-12-04
Now your screen should look like this.  You can Ctr + Alt > right/left arrows to navigate between the workspaces.
[ATTACH]138553[/ATTACH]

Notice that there are two icons shown in the Window Picker at the top left of the screen.  Now look at the Workspace Switcher in the center of the screen.  Notice that the icons are being pulled from multiple workspaces.  The problem with this is that every application is displayed in the picker regardless of the workspace it belongs to.  This can be a real issue if you regularly keep multiple instances of the same application open at the same time.  For example, I often have multiple instances of Firefox and terminals open in multiple workspaces plus additional programs.  It gets a little tough to keep track of them after a while. This is why I prefer my Window Picker to show only the windows that belong to the workspace I'm using at that time.  This is easy to change.

6)  Minimize all windows > right click the Window Picker (center of top panel) > Preferences >  un-check "Show windows form all workspaces"
[ATTACH]138554[/ATTACH] 

Now when you switch between workspaces, you will only see the windows from the current workspace in the window picker.
[ATTACH]138555[/ATTACH]

---

### Post by paul pom on 2009-12-05
Hey man !
You made my day ! 

That was a nice mouse using trick.

Actually I found out how to add workspace using command line but not how to organize them in 2 lines.

link to command line method :
[http://library.gnome.org/admin/system-admin-guide/stable/gconf-8.html.en#gconf-12](http://library.gnome.org/admin/system-admin-guide/stable/gconf-8.html.en#gconf-12)

thanks for sharing,

Paul

---

### Post by ohiomoto on 2009-12-05
Thanks for the link Paul.

---

### Post by Torrilin on 2009-12-05
Very useful tutorial. Not because I wanted multiple desktops, but because it showed me how to access the gnome-applets. I've seen references to them in a lot of places, but never any instructions for how to USE them.

Now I can set up a CPU frequency adjuster like the EEEpc SuperHybrid Engine in Windows. And I can have a system load monitor. Most of the other stuff isn't useful to me... but this opens up a lot of tools that most users would really find handy.

---

### Post by ohiomoto on 2009-12-11
I added an alternative method to post #2.

---

### Post by slash3s on 2009-12-28
you rlz men D: im so thank you : )

---

### Post by Gemnoc on 2010-02-24
Well it'd be great if I was actually able to move the #$%?!!! separator. I right-click on it like a madman and nothing happens.

I'm getting sick to death of UNR. The touchpad and its buttons are often unresponsive, but only in the UNR interface. Once I'm in an app or Nautilus, no problem whatsoever.

Sorry ohiomoto to barge in on your thread like that, I'm just so pissed that I couldn't use your tip. ](*,)

---

### Post by ohiomoto on 2010-02-24
Gemnoc,

As for the divider, it can be tricky to get unlocked.  You might want to use the alternative method.  It's actually easier.

As for the problems with the netbook interface, I actually had the same problem on one of my computers.  (The other one still works great.)  You can use alt + F1 to use the menu or do what I did and add the "main menu" to the top panel and enable "Show Desktop" in the gconf-editor.  

Here is a link to a post that explains how to do it: [http://ubuntuforums.org/showpost.php?p=8313100&postcount=16](http://ubuntuforums.org/showpost.php?p=8313100&postcount=16)

Now I have a classic desktop look with multiple workspaces, a top panel that has a classic menu, and UNR functionality.  So while I was disappointed with the slow Remix desktop, I'm very pleased with the final result.
[ATTACH]148112[/ATTACH]

---

### Post by Ubunthree on 2010-02-24
I had trouble moving the separator too (meaning the little grab-handle thing I assume) until I tried dragging it WAY over next to the tray as far as it would go; it finally moved then. Then I was able to add the workspace switcher and move the window picker back to where I wanted it after that.

THANK YOU for this. I've been wanting two workspaces, but never bothered asking the question, because I just assumed that UNR didn't have that ability...

---

### Post by Gemnoc on 2010-02-24
Hi,

Thanks for answering.
> **ohiomoto said:**
> Gemnoc,

As for the divider, it can be tricky to get unlocked.  You might want to use the alternative method.  It's actually easier.
I've changed the number of workspaces in gconf-editor as per the alternate method. Still, it doesn't show any change in the panel, since I guess I need to add the workspace switcher applet, or do I?

> As for the problems with the netbook interface, I actually had the same problem on one of my computers.  (The other one still works great.)  You can use alt + F1 to use the menu or do what I did and add the "main menu" to the top panel and enable "Show Desktop" in the gconf-editor.  

Here is a link to a post that explains how to do it: [http://ubuntuforums.org/showpost.php?p=8313100&postcount=16](http://ubuntuforums.org/showpost.php?p=8313100&postcount=16)

Now I have a classic desktop look with multiple workspaces, a top panel that has a classic menu, and UNR functionality.  So while I was disappointed with the slow Remix desktop, I'm very pleased with the final result.

Thanks, didn't know that keyboard shortcut. I'll look at your other post too. But with that mod, what exactly is left of UNR functionality?

---

### Post by Gemnoc on 2010-02-24
tried to delete this post since I combined my answers into the last one, but could't find a way...

---

### Post by Gemnoc on 2010-02-24
> **Ubunthree said:**
> I had trouble moving the separator too (meaning the little grab-handle thing I assume)
Ok, thanks to Ubunthree, I managed to understand what was going on. :oops:

There is actually no separator: the three dots to the right of the go-home-applet (Ubuntu icon) are actually the "handle" for the window-picker-applet. Right-clicking next to it to unlock then move it to the far right like Ubunthree suggested did the trick.

Thanks for you help guys.

Kind of a reminder, in cases like this, to heed the advice from the weird boy dressed as a tibetan monk in the Matrix: there is no spoon! ;-)

---

### Post by ohiomoto on 2010-02-24
> **Gemnoc said:**
> 
I've changed the number of workspaces in gconf-editor as per the alternate method. Still, it doesn't show any change in the panel, since I guess I need to add the workspace switcher applet, or do I?You could, but you don't have to.  I didn't add the switcher because I use the keyboard shortcut: CTRL+ALT plus left or right arrows. 

> **Gemnoc said:**
> 
Thanks, didn't know that keyboard shortcut. I'll look at your other post too. But with that mod, what exactly is left of UNR functionality?The window picker at the top left is still there.  When I'm using the mouse pointer, I prefer to keep everything in one panel at the top.  This leaves more room for my applications (one panel) and makes navigation easier (everything is in the top panel).
[ATTACH]148122[/ATTACH]

EDIT:  Of course, once giving up on UNR's main interface you could achieve the same results from the Standard Desktop package with a little tweaking.  I still like the Remix interface when it's working properly, but the main attraction for me is how it uses the top panel.

---

### Post by Gemnoc on 2010-02-24
Well I made the mod and got rid of the UNR home screen. I'll see if I like it better in the long run. One good side effect is that my desktop background image is now clearly visible.

Thanks for the tips, ohiomoto, I'll try to remember the keyboard shortcut to switch between workspaces. It'll save space on the top panel not using the applet.

BTW, from the looks of your screencap in #10 post, I gather you have an Aspire 1410 11.6"LCD laptop. Mine is a Gateway EC1803h (with single-core Intel Core2 CPU) which was briefly sold in Canada last Fall. It's a clone of the 1410. They replaced it with the EC14 series with C2D which duplicates the Aspire 14xx line. Pretty good little machine, although I get 4h30 at most out of the 4400mAh battery in UNR. Battery life is about 6h in Vista...

---

### Post by ohiomoto on 2010-02-24
Yes, I have Acer version of your Gateway.  I'm real happy with it.  I don't use Windows much but my battery life matches yours. You might be interested in the link below.  It's a great resource for us Acer/Gateway 11.6" owners using Linux. 

[http://forum.notebookreview.com/showthread.php?t=434638](http://forum.notebookreview.com/showthread.php?t=434638)

---

### Post by Gemnoc on 2010-02-24
Thanks for the link! :)

I subscribed to that forum after I bought my Gateway but hadn't visited it for some time. I was unaware there was a Linux thread.

---

### Post by dancmd on 2010-10-06
How about 10.04? The method above seems not to work...

---

### Post by ledmonk on 2010-10-11
Hey OP, thanks a lot! I've been really bugged that UNR didn't have this feature like the standard distro... turns out I just wasn't looking hard enough.

---

