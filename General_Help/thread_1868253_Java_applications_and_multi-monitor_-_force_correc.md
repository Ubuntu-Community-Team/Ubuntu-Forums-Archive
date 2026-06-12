---
title: "Java applications and multi-monitor - force correct window size and placement?"
date: 2011-10-24
forum: General Help
---

### Post by Aesso on 2011-10-24
I have a Java application that I have to use ([TN5250J]("http://tn5250j.sourceforge.net/")) since I haven't found a user-friendly native Linux equivalent. Since I have three monitors, the JRE thinks I have one huge screen that's 5040x1050 rather than three separate 1680x1050 screens, so when the app starts, it creates an unmaximized window that spans all three screens. How do I get Java apps to NOT do this?

On that note, who knows of any native 3270/5250 emulators for Linux that use GTK/Qt? Every emulator I've found is old and lacking in features.

---

### Post by Aesso on 2011-10-25
After doing some digging, apparently you can pass on "width" and "height" parameters to a Java applet -- when you start one from a webpage with an <applet> tag. 

[_Oracle - Using JAR files: The Basics_]("http://download.oracle.com/javase/tutorial/deployment/jar/basicsindex.html")
[html]<applet code=AppletClassName.class
archive="JarFileName.jar"
width=width height=height>
</applet>[/html]Unfortunately, these Oracle help pages make no mention (that I could find) of how to do this when you're executing a [FONT=Lucida Console].jar[/FONT] file from the command line. In my case I'm running 

```
java -jar /opt/tn5250j/lib/tn5250j.jar
```Surely there must be a way to do this from the command line???? :confused: Seems silly to have to create an html file just to get this thing to load  right.

---

### Post by Aesso on 2011-10-29
Semi-solved and now usable.

I ended up creating a window rule in ccsm ([Compiz Configuration Settings Manager]("apt:compizconfig-settings-manager")). I was hoping to do this with the launcher rather than through Compiz, though I think I've made the rule specific enough to this applet that I won't get weird results with other Java windows (like overstretched windows that were intended to be rendered at 320x240, as an example). Also, a ccsm rule would be of no use to somebody who's not using Compiz. 

Of course, _[ccsm]("apt:compizconfig-settings-manager")_ needs to be installed:
```
sudo apt-get install compizconfig-settings-manager
```I made two rules, one in the "Place Windows" plugin and another in  "Window Rules":

**Place Windows:**[INDENT] **Fixed Window Placement**

Windows with fixed placement mode:[INDENT] Windows: [FONT=Courier New](name=sun-awt-X11-XFramePeer) & (class=org-tn5250j-My5250)[/FONT]
Mode:    Smart

*(The [FONT=Courier New](class=org-tn5250j-My5250)[/FONT] makes it specific to the applet I'm using, _[tn5250j]("http://tn5250j.sourceforge.net")_.)*

[/INDENT][/INDENT]**Window Rules:**[INDENT]**Size Rules**:[INDENT]Sized windows: [FONT=Courier New](name=sun-awt-X11-XFramePeer) & (class=org-tn5250j-My5250)[/FONT]
Width/Height: *  set dimensions appropriate to your screen*

[I](I did 1600x900, slightly smaller than a full screen on one of my monitors. 
In my case, the applet maximizes anyway, so it's probably moot,but at least it doesn't span all three screens!) [/I]

[/INDENT][/INDENT]The result?  The window will come up on one screen, maximized though (not a preferred option), and it appears on the left-most monitor.

If there is a way to set a window size or state in a launcher file (.desktop), that would be my preference. Anyone who if this can be done?

---

