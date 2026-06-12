---
title: "Problem with Application tab"
date: 2010-04-04
forum: General Help
---

### Post by amite on 2010-04-04
when i click on Places or Systems in my ubuntu karmic then drop down box comes but when i click on Application tab it just highlighted but no dropdown box comes.Due to this to open any application i hv to go through "Run Application",but when i need to open some app. which exact name is not known(some games) to me then i can't do anything.

it worked right for last 2 month but i don't know how this happened!

---

### Post by warfacegod on 2010-04-04
Right click the menu and select Edit Menus. In the Window that opens, in left hand pane, highlight Applications. Then in the right hand pane, make sure there are checks next to all of the sub-menus that you wish to have in the main menu. Then, back in the left hand pane, one at a time, highlight each sub-menu that you selected and, again to the right, make sure there are checks next to the apps that you would like in the menu.

It sounds complex on "paper" but it isn't.

---

### Post by amite on 2010-04-04
On clicking the "edit menus"(Application) nothing happens.Although drop down box for Places and System comes but clicking "edit menu" here also doesn't work.

also System>>Preferences>>Main Menu not responding.although other application in System>>Preferences work well...........

---

### Post by warfacegod on 2010-04-04
You'll need a Terminal so hit Alt+F2 and type: gnome-terminal

Then, in Terminal, do this:

```
sudo apt-get purge alacarte
```

Then:

```
sudo apt-get install alacarte
```

That will remove the Menu Editor and its config file and then install it again.

---

### Post by warfacegod on 2010-04-04
Try adding another Menu Bar to your panel, see if that one works. Right click the panel> select Add to Panel... well, you can figure out the rest.

You might try a Main Menu as well to see if you can get to your apps through that. It's basically a condensed version of the Menu Bar.

---

### Post by amite on 2010-04-05
> **warfacegod said:**
> You'll need a Terminal so hit Alt+F2 and type: gnome-terminal

```
sudo apt-get purge alacarte
```Then:

```
sudo apt-get install alacarte
```That will remove the Menu Editor and its config file and then install it again.


i did it but it's not working...........here is screenshot it may help.....
> 
amitesh@ami:~$ sudo apt-get install alacarte
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnet-ssleay-perl libxml-namespacesupport-perl
  libhttp-response-encoding-perl libxml-sax-expat-perl libxml-sax-perl
  libhttp-server-simple-perl libio-socket-ssl-perl libnet-libidn-perl
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  alacarte
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/57.8kB of archives.
After this operation, 1,364kB of additional disk space will be used.
Selecting previously deselected package alacarte.
(Reading database ... 198937 files and directories currently installed.)
Unpacking alacarte (from .../alacarte_0.12.4-0ubuntu2_all.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Setting up alacarte (0.12.4-0ubuntu2) ...


  it's after applying sudo apt-get purge alacarte:mad:

---

### Post by amite on 2010-04-05
> **warfacegod said:**
> Try adding another Menu Bar to your panel, see if that one works. Right click the panel> select Add to Panel... well, you can figure out the rest.

You might try a Main Menu as well to see if you can get to your apps through that. It's basically a condensed version of the Menu Bar.


i created new panel and then add to panel i added Menu Bar.............but there too i am facing the same problem!:sad:

---

### Post by warfacegod on 2010-04-05
What about the Main Menu applet, did you try that?

Go into Synaptic> under Edit (top left)> select Fix Broken Packages.

---

### Post by amite on 2010-04-05
i don't really want to configure my system from zero............so please any one help me!!
how to short out this tiny problem which has given me a lot of tension?????

---

### Post by stoneage on 2010-04-05
Did you try running ```
alacarte
``` in a terminal ? Post up the errors if any.

You could also try adding a new user:-
[http://ubuntuforums.org/showthread.php?t=1362825](http://ubuntuforums.org/showthread.php?t=1362825)

---

