---
title: "Any analogous to Window's Snipping Tool?"
date: 2009-11-18
forum: General Help
---

### Post by Saurabhdua on 2009-11-18
Hello There!

Iam om Ubuntu 9.04, latest release. I wish to seek details that if there is any option available within Ubuntu that works in the same way to that of Window's "Snipping Tool"?!

I wish to extract a particular portion of the Screen & have to take the "Entire Screenshot"....Please help!

---

### Post by stinkeye on 2009-11-18
> **Saurabhdua said:**
> Hello There!

Iam om Ubuntu 9.04, latest release. I wish to seek details that if there is any option available within Ubuntu that works in the same way to that of Window's "Snipping Tool"?!

I wish to extract a particular portion of the Screen & have to take the "Entire Screenshot"....Please help!
Use shutter. Takes screenshots of windows or sections.

---

### Post by Saurabhdua on 2009-11-20
How to get it? OR from where can it be accessed?

---

### Post by redmk2 on 2009-11-20
> **Saurabhdua said:**
> How to get it? OR from where can it be accessed?

See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://www.ubuntugeek.com/shutter-featureful-screenshot-tool.html").

---

### Post by stinkeye on 2009-11-20
Open synaptic package manager.
Settings > repositories > other software
click add button .
paste in```
deb http://ppa.launchpad.net/shutter/ppa/ubuntu [COLOR="DarkRed"]jaunty[/COLOR] main
```Change to [COLOR="DarkRed"]your release[/COLOR] if necessary.
Keep synaptic open
add the signing key.....in terminal
```
wget -q http://shutter-project.org/shutter-ppa.key -O- | sudo apt-key add -
```
Now click reload in synaptic and then search for shutter.
Shutter will be installed in the menu under accessories.

---

### Post by Saurabhdua on 2009-11-21
Hello There..again!

Firstly, there is nothing like 'Other Software'! Tabs are associated with Ubuntu & Third Party Software.

Secondly, after following your steps...the search to Shutter in the Synaptic Package Manager yields to setpwc & jhead(I wonder if the latter is derived from JEHAD propagated by Bin Laden!?)

Iam not able to find the "Shutter" entry in specific & moreover couldn't follow the objective of the command typed in the Terminal window?

---

### Post by llamabr on 2009-11-21
I'm not sure quite what snipping does, but the gimp will take screenshots of the entire screen, or just of particular windows.

It's a great big program, but it'll do what you want.  From the cli, I also use scrot.

---

### Post by totheleft on 2009-11-21
is  the take screenshot app in 9.04 not the same as 9.10 as that allows you to grab an area of screen or full screen which is the same as snipping tool in windows

---

### Post by 3rdalbum on 2009-11-21
The Gimp can take full screenshots, windowshots, or partial screenshots based on an area.

Open Gimp and go to File > Create > Screenshot.

---

### Post by stinkeye on 2009-11-21
> **Saurabhdua said:**
> Hello There..again!

Firstly, there is nothing like 'Other Software'! Tabs are associated with Ubuntu & Third Party Software.

Secondly, after following your steps...the search to Shutter in the Synaptic Package Manager yields to setpwc & jhead(I wonder if the latter is derived from JEHAD propagated by Bin Laden!?)

Iam not able to find the "Shutter" entry in specific & moreover couldn't follow the objective of the command typed in the Terminal window?

Well ,pardon me!?
In karmic the "third party software" has been renamed to "other software".
The objective of the command typed in the Terminal window is stated before the code box....ie."add the signing key...." for the shutter ppa.
When I give an answer to someone's question I look at how long they've been registered on the forums for and put in as much detail as I think necessary.
For the complete nooobs guide see redmk2 post.
or
just download the .deb file from here [_[COLOR="DarkRed"]http://shutter-project.org/downloads/[/COLOR]_]("http://shutter-project.org/downloads/")
under Ubuntu packages.

---

