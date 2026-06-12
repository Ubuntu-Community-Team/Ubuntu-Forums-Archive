---
title: "Unity issues with WINE and moving icons"
date: 2011-07-13
forum: General Help
---

### Post by jjb2011 on 2011-07-13
[I posted this at a SOLVED post but they didn't address these two issues]:

My first reaction when I heard of Unity is Great! Finally an object dock  where you simply drag and drop, right-click for settings, move icons  around. 

Ouch. I hope this is only a set of bugs:

1. Wine programs won't "stick" to the object dock. Mac will let you  stick whatever (ditto object dock for Windows). You can "search for  applications, click again to see all, find Microsoft Word - or whatever)  and then it will appear on the launcher ONLY WHEN YOU HAVE THE PROGRAM  OPEN!!). It appears as a Wine symbol (not Word which can attach to  Docky, BTW). Then it disappears when you shut down. 

2. Can't move icons/shortcuts up and down. They just won't move. 

The work arounds defeat Ubuntu's efforts to get something working "out  of the box" for the "mainstream." How many people are going to do this:

[http://askubuntu.com/questions/29553/how-can-i-configure-unity](http://askubuntu.com/questions/29553/how-can-i-configure-unity)

I realize this is a project in the making but if it isn't as good as  docky, I hope we can just pin the thing away and still use Docky. 

If there is a solution that doesn't require all the hacking of above  (and no mention of Wine programs?) then I'll just stick with 11.04 for a  while and then ditch Ubuntu for something else. It's a shame:  "snatching defeat from the jaws of victory," as they say. 
Not many! Docky is easier to configure, much easier. 

But I would like an easy way to do #1 (not mentioned in Ubuntu help) or  #2 (says you can move but I can't on my 64-bit machine and OS). 

I really, really like how Ubuntu just works now and PlayonLinux runs the few programs I need (Office, specialty educational stuff).

---

### Post by flipper T on 2011-07-13
to make wine apps stick in launcher bar, save the shortcut some here (documents perhaps) and then drag this shortcut to the launcher bar.

**_do not_** delete the shortcut you have saved.

---

### Post by jjb2011 on 2011-07-14
That worked! 

Now my problem is that the Unity Launcher icon is blank. I changed the icon for the Link but that still didn't do the trick.

---

### Post by grahammechanical on 2011-07-14
My answer to the icon of a program running under not fixing to the launcher, was to install the program in Ubuntu Classic so that it put an icon on the desktop. Then load into Unity and drag the icon from the desktop.

Regards,

---

### Post by jjb2011 on 2011-07-14
Thanks. I'll try that tomorrow. I like Docky and really this side bar is driving me nuts. I've hated Auto Hide on all platforms: Windows, Mac, Ubuntu. But, hey, if Mac is successful by not giving people choices, then Ubuntu will be for the masses too. Sigh.

---

### Post by flipper T on 2011-07-14
jjb my icons show up the same as i have saved. so cannot be of more help

perhaps try again ?


:)

---

### Post by flipper T on 2011-07-14
if it helps, see attached screenshot

also, this is the shortcut command info, in thus case for the game "around the world ..."

> env WINEPREFIX="/home/jason/.wine" wine C:\\Program Files\\GameTop.com\\Around the World in 80 Days\\Around the World in 80 Days.exe 

---

