---
title: "control mouse position from command line...?"
date: 2010-05-17
forum: General Help
---

### Post by Jamesss on 2010-05-17
Is it possible to control the mouse position from the command line? I want to centre the pointer in the middle of the screen.

thanks

James

---

### Post by dv3500ea on 2010-05-17
I doubt it.

---

### Post by Thangalin on 2010-06-06
sudo apt-get install xdotool
xdotool mousemove 500 500

---

### Post by Jamesss on 2010-06-15
that's great, thanks! exactly what I needed

---

### Post by hubertofliege on 2010-06-18
I don't want to ask this, but I can't figure it out.

How do I make a script in gedit which, when clicked on, will just run as if typed in the terminal?  Is it a file extension I add?  I don't want it to open in gedit, I want it to run.

---

### Post by drewsus on 2010-06-19
> 
How do I make a script in gedit which, when clicked on, will just run as if typed in the terminal? Is it a file extension I add? I don't want it to open in gedit, I want it to run. 

You need to make it executable. 
I will tell you two ways...
1) Right-click on the file and go to Permissions.
[INDENT]-Check the "Allow executing file as Program"[/INDENT]
[INDENT]-Click "Close"[/INDENT]
2) Go to the folder the file is in in terminal and run the command:
```
chmod +x <file>
```
(replace <file> with the file name...)

The file needs to be in your $PATH as well. But, you can make the 'current' folder be in the path. 

With gedit, open the file ".bashrc" from your home folder.
Add the following line at the end of the file:
```
PATH='$PATH:./'
```

And one time only, open terminal and run this command (or restart your session...):
```
. ${HOME}/.bashrc
```
**[COLOR="Red"](note the dot at the beginning of that command)[/COLOR]**

---

### Post by drewsus on 2010-06-19
And to follow up on the actual subject of the post... is there a way to get the mouse coordinates from terminal? (kind of the opposite of what the OP was asking)

Drew

---

### Post by Jamesss on 2010-07-03
xdotool getmouselocation

:D

---

### Post by drewsus on 2010-07-07
> **Jamesss said:**
> xdotool getmouselocation

:D

Wow that solved my issue AND more. Many solutions to other things I have been pondering. Excellent!

---

