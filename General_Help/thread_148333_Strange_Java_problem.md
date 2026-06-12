---
title: "Strange Java problem"
date: 2006-03-21
forum: General Help
---

### Post by ncappel1 on 2006-03-21
Hi everyone,

I have the latest version of Java (1.5.06 as of Mar 21, 2006) installed on my computer, I verified it with Sun's website. At my school there is an online java applet that we have to use to register for new classes, for some reason it just doesn't work. There is an error in the Firefox java console that reads like this: 

>  WARNING: Deprecated parameter: "language". Please use "interfaceLanguage" instead.
NavigWeb: Server version: 20020904, Protocol version: 38
The World Wide Web Degree Navigator Version 4.0.1.0 (37)
java.lang.NullPointerException
	at sun.awt.X11.XMenuPeer.repaintMenuItem(Unknown Source)
	at sun.awt.X11.XMenuItemPeer.setEnabled(Unknown Source)
	at sun.awt.X11.XMenuItemPeer.disable(Unknown Source)
	at java.awt.MenuItem.disable(Unknown Source)
	at java.awt.MenuItem.enable(Unknown Source)
	at java.awt.MenuItem.setEnabled(Unknown Source)
	at com.dagsoft.common.degree.WindowDegreeCybernautWithDegree.organizeWindow(WindowDegreeCybernautWithDegree.java:349)
	at com.dagsoft.cybernaut.InteractiveWindowDegreeCybernaut.organizeWindow(InteractiveWindowDegreeCybernaut.java:1327)
	at com.dagsoft.registration.RegisWinDegCyb.organizeWindow(RegisWinDegCyb.java:1399)
	at com.dagsoft.common.misc.WindowDegreeCybernaut.startUp(WindowDegreeCybernaut.java:2028)
	at com.dagsoft.cybernaut.DegreeCybernaut.startCybernaut(DegreeCybernaut.java:144)
	at com.dagsoft.common.misc.DegreeCybernautBase.init(DegreeCybernautBase.java:122)
	at com.dagsoft.cybernaut.DegreeCybernaut.init(DegreeCybernaut.java:34)
	at sun.applet.AppletPanel.run(Unknown Source)
	at java.lang.Thread.run(Unknown Source)
/usr/share/themes/Human/gtk-2.0/gtkrc:7: Failed to parse property value " GTK_SHADOW_NONE " for `GtkMenuItem::shadow-type'
/usr/share/themes/Human/gtk-2.0/gtkrc:58: Engine "clearlooks" is unsupported, ignoring 

in the error console it says this:

> 
Error: Error in parsing value for property 'white-space'.  Declaration dropped.
Source file: [http://www.ubuntu.com/htdocs/ubuntuweb/css/common.css](http://www.ubuntu.com/htdocs/ubuntuweb/css/common.css)
Line: 103
 ----------
Error: Unknown property 'word-wrap'.  Declaration dropped.
Source file: [http://www.ubuntu.com/htdocs/ubuntuweb/css/common.css](http://www.ubuntu.com/htdocs/ubuntuweb/css/common.css)
Line: 104
 ----------
Error: Error in parsing value for property 'white-space'.  Declaration dropped.
Source file: [http://www.ubuntu.com/htdocs/ubuntuweb/css/common.css](http://www.ubuntu.com/htdocs/ubuntuweb/css/common.css)
Line: 106
 ----------
Error: Error in parsing value for property 'white-space'.  Declaration dropped.
Source file: [http://www.ubuntu.com/htdocs/ubuntuweb/css/common.css](http://www.ubuntu.com/htdocs/ubuntuweb/css/common.css)
Line: 107
 ----------
Error: Unknown property 'word-wrap'.  Declaration dropped.
Source file: [http://www.ubuntu.com/htdocs/ubuntuweb/css/skidoo_right-menu.css](http://www.ubuntu.com/htdocs/ubuntuweb/css/skidoo_right-menu.css)
Line: 18
 ----------
Error: document.getElementById("titlesearch") has no properties
Source file: [http://www.ubuntu.com/](http://www.ubuntu.com/)
Line: 30
 ----------
Error: a[i].getAttribute("href") has no properties
Source file: chrome://fasterfox/content/fasterfoxOverlay.js
Line: 186
 ----------
Error: stopIsValid is not defined
Source file: chrome://fasterfox/content/listener-fasterfox.js
Line: 60
 ----------
Error: Error in parsing value for property 'text-decoration'.  Declaration dropped.
Source file: [http://ubuntuforums.org/clientscript/vbulletin_css/style-257466ef-00001.css](http://ubuntuforums.org/clientscript/vbulletin_css/style-257466ef-00001.css)
Line: 58
 ----------
Error: Expected declaration but found '/'.  Skipped to next declaration.
Source file: [http://ubuntuforums.org/clientscript/vbulletin_css/style-257466ef-00001.css](http://ubuntuforums.org/clientscript/vbulletin_css/style-257466ef-00001.css)
Line: 344
 ----------
Error: a[i].getAttribute("href") has no properties
Source file: chrome://fasterfox/content/fasterfoxOverlay.js
Line: 186
 ----------
Error: Error in parsing value for property 'text-decoration'.  Declaration dropped.
Source file: [http://ubuntuforums.org/clientscript/vbulletin_css/style-257466ef-00001.css](http://ubuntuforums.org/clientscript/vbulletin_css/style-257466ef-00001.css)
Line: 58
 ----------
Error: Expected declaration but found '/'.  Skipped to next declaration.
Source file: [http://ubuntuforums.org/clientscript/vbulletin_css/style-257466ef-00001.css](http://ubuntuforums.org/clientscript/vbulletin_css/style-257466ef-00001.css)
Line: 344
 ----------
Error: a[i].getAttribute("href") has no properties
Source file: chrome://fasterfox/content/fasterfoxOverlay.js
Line: 186
 ----------
Error: Error in parsing value for property 'text-decoration'.  Declaration dropped.
Source file: [http://ubuntuforums.org/clientscript/vbulletin_css/style-257466ef-00001.css](http://ubuntuforums.org/clientscript/vbulletin_css/style-257466ef-00001.css)
Line: 58
 ----------
Error: Expected declaration but found '/'.  Skipped to next declaration.
Source file: [http://ubuntuforums.org/clientscript/vbulletin_css/style-257466ef-00001.css](http://ubuntuforums.org/clientscript/vbulletin_css/style-257466ef-00001.css)
Line: 344
 ----------
Error: a[i].getAttribute("href") has no properties
Source file: chrome://fasterfox/content/fasterfoxOverlay.js
Line: 186


I don't know if this is relevant, but it says that these are mostly "CSS" errors.

Here is a link to the page with the java applet [http://ottawa.ithaca.edu/sis-deg-nav-stu/]("http://ottawa.ithaca.edu/sis-deg-nav-stu/")

Is something not properly configured on my machine? Or is this a problem with my school only programming towards Windows and MacOS?

I hope someone can help me!

---

### Post by mustang on 2006-03-21
Don't know if it helps but here's what I get in the error popup java window:

```


WaitNamedPipe:
\\.\pipe\DegreeNavigatorServerPipeITHACA3
2: The
system cannot find the file specified.


```

---

### Post by spier on 2006-03-21
Same error poped up here. 

Seems like a server side problem, or a prior installation needed in the client...

---

### Post by ncappel1 on 2006-03-21
Does that mean the problem is on my side? or the school's network side?

---

### Post by mustang on 2006-03-22
Server side = their problem.

Oddly enough I'm not experiencing that problem anymore. Are you still getting the same errors?

---

### Post by ncappel1 on 2006-03-22
I asked at the technology lab desk and all they could tell me is that they don't know because they don't support linux, and that probably because the applet is not actually a pure java applet, but something else written onlywith support specific to windows and mac environments. is there no way to get around this problem? They suggested that I use a windows emulator like wine.

---

### Post by FIONEX on 2007-01-07
Although you might have Java 1.5.X installed, the wrong java interpreter is being used.  The link "java" is pointing to the earlier version that ships with ubuntu.  To switch to the newer version of java and javac, type the following in your console and select the approperiate path to the new java installation.

```

sudo update-alternatives --config java


sudo update-alternatives --config javac

```

My university uses the same applet and I had the same problem.  It worked on windows but gave me the same errors on linux.  I hope that helps you fix it.

---

