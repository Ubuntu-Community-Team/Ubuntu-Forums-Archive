---
title: "Add applications to Startup"
date: 2012-06-25
forum: General Help
---

### Post by omiazad on 2012-06-25
Hi,
Adding applications on startup looks easy. But to add an application on the startup settings, we have to know the location to the application's executable. For example I want to add TeamViewer to startup, but I don't know the location of it's executable.

Please suggest me how I can find that?

Regards
Omi on Ubuntu 12.04

---

### Post by nipunshakya on 2012-06-25
Go to start up applications
Click &#8220;Add&#8221;
Now you will see a box called Add Startup Program box
Now In Name place Type Start Team viewer
In Command place type /usr/bin/teamviewer
And now press Add button
And press close button.

Goodluck

---

### Post by deathadder on 2012-06-25
If you open up a terminal you can find it's absolute path by using the "which" command, for example looking for geany (a text editor) I'd type:
```
$ which geany
/usr/bin/geany
```
If it can not find the executable in your PATH then it won't return anything. 

I'm not tried teamviewer before but a quick Google suggests the executable is called 'teamviewer' located in /usr/bin, just open a terminal to double check :)

---

### Post by papibe on 2012-06-25
Hi omiazad.

Let's say you want to run 'ls'.

To find out where 'ls' is located take a look at this commands:
```
which ls

whereis ls

```
Hope it helps, and tell us how it goes.
Regards.

---

### Post by HiImTye on 2012-06-25
to find an executable you can use this:
```
find / -type f -executable 2>/dev/null | grep <name>
```replace <name> with the filename of the program you are looking for

---

### Post by dcsoldschool53 on 2012-06-25
You can also type in a terminal```
alacarte &
```When it opens, click on the Applications Menu. You are looking for the program's location. In the Show Items menu, click on the name of the program that you want. The list on the far right will become UN-grayed. Click on the Properties button, and a create launcher window will pop up. Look on the command line to see what command you will need to use.

Now if you want to know the exact location of the command you found in alacarte, you can type in the terminal```
whereis gpaint
```It will tell you all of the locations gpaint is found under.

---

### Post by omiazad on 2012-06-25
Thanks folks. **which whereis** worked nice.

**alacarte** is not a built it application, have to install that first if I'm not wrong.

---

### Post by dcsoldschool53 on 2012-06-25
On 12.04 classic, it is built-in

---

### Post by omiazad on 2012-06-25
> **dcsoldschool53 said:**
> On 12.04 classic, it is built-in

I'm using x64, that is not in-built. I'll give it a try as _whereis/which didn't work for me. _

---

### Post by ausrick on 2012-09-21
I'm having this trouble too.  I will let you know what I found out though.

In /usr/bin/ There is a teamviewer which is a link to /usr/bin/teamviewer7 which is a link which takes you to a shell script in the /opt directory. that location is /opt/teamviewer/teamviewer/7/bin/teamviewer

Now "that" script basically runs Wine and opens up c:\program files\teamviewer\version7\teamviewer.exe :p

```
#!/bin/bash

TV_script_dir="$(dirname "$(readlink -f "$0")")"
"$TV_script_dir/wrapper" wine "c:\Program Files\TeamViewer\Version7\TeamViewer.exe" "$@"

true

```

Here's the stupid problem that because I'm new at this I keep messing up.  When I execute it this way, It creates a separate icon for it with a questionmark picture in my Unity launcher, and Unity doesn't seem to recognize or treat it in the same way as if I launched it from the panel on the left or as an application in Dash Home.

Sooooo I thought I was being cleaver and made my startup point to /usr/share/applications/teamviewer-teamviewer7.desktop because when I run that file it acts as expected...

Evidently you can't do that.  I didn't get any error messages, but when I logged off and logged back on again, it didn't start anything. :confused::mad:

---

### Post by ausrick on 2012-10-01
I just wanted to add an update so any future souls that stumble in here can maybe find an answer to their questions...

This is how I got Team Viewer 7 to be added to the startup applications and thus run when my account is logged into the computer. (this doesn't cover auto-running at startup with no one logged in.  That evidently involves daemon conjuring. ;)   )

1.) navigate to applications folder (/usr/share/applications/) in unity on ubuntu 12.04, making sure the file browser (a la explorer, finder in other OS's) you are using is not full screen (maximized).

2.) open up startup applications in it's own window (from the gear in the upper right is easiest)

3.) drag and drop the "Team Viewer 7" icon from the applications folder to the blank white space where startup applications are listed in the startup applications window.

What Doesn't work: dragging and dropping from the Dash Home, at least for me, on the server I set up here running Unity 2d... It asploded. :( 

What this process actually does:  Creates an entry in the startup applications window for "TeamViewer 7", with the TV Icon, with a Command of "/opt/teamviewer/teamviewer/7/bin/teamviewer" and a comment "TeamViewer Remote Control Application"

Side-Effects: When you log in you will have the TeamViewer application open and front and center.  Some people may want it to minimize to the tray upon start... outside of my knowledge-scope, sorry.

Side-Effects: I had already drug the TeamViewer icon over from Dash Home to add it to the Launcher (which did work sans asplosions) and doing it this way effectively creates another, unpinned version of the TeamViewer application in the Launcher. So I have the "TeamViewer 7" icon that I had put in the Launcher, and a "TeamViewer" icon below that that actually has the white arrow indicators for the open windows it has and weather it is on top or not.  I could just remove the one I had made, but for instance when I duplicate this process with something like Chromium it doesn't act that way. (e.g. Cromium launches as the icon I already have in the launcher when I make it a startup application, not creating a separate Icon to run under.)

Conclusion:  I hope this helps anyone reading through here trying to get TeamViewer 7 to run from the Startup Applications in Unity on ubuntu 12.04  If you find this helpful please send me a message and say "Hey!"  I hope I'm not typing purely for finger exercise and manual dexterity. ;)

---

### Post by Venem on 2012-11-28
Ausrick, thanx a lot for your contribution! It worked for me. Im gonna try to find a similar app that runs instead in the tweak bar waitn at all times

---

