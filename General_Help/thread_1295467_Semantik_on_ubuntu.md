---
title: "Semantik on ubuntu"
date: 2009-10-19
forum: General Help
---

### Post by Trinaxia on 2009-10-19
Hi,
I am very beginner with ubuntu. It runs well. 
I tried to download semantik. The problem is that semantik seemed to be downloaded properly (in directory : /home/salvatore/Data Salva/semantik) but I don't know how to run it. There is no button, nothing that indicates how to launch the program. And I can't find any exe in the directory.

Could anyone tell me what to do ?

Thanks a lot in advance

Best Regards

Sal

---

### Post by Giblet5 on 2009-10-19
Downloaded it from where? How?

Why not just install it?

```
sudo apt-get install semantik
```

---

### Post by Trinaxia on 2009-10-22
Hi Giblet5,
Thanks a lot for your help.

Well actually I just needed to install it and the first thing I did was to look for it on the web. As it was available on the web on : [http://www.brothersoft.com/semantik-download-283875.html](http://www.brothersoft.com/semantik-download-283875.html)

I just downloaded it. If there is a simpler way please let me know.

It seems that all semantik files are on my computer but to the program itself....no idea.

I think I must do some kind of command on ubuntu but don't know what.

Because I also wanted to install wordpress and again all files are on my computer but I cannot launch wordress somehow.

Thanks a lot for your help

Sal

---

### Post by P4man on 2009-10-22
To install software in ubuntu, the default way is to go to applications > add/remove. (make sure you enable all available apps in the drop down)

then search for semantik or any keyword and have a look at a few thousand free apps to be installed safely with just one click. Welcome to ubuntu :)

edit: btw, semantik is a KDE app. It works with ubuntu (though it will require you to download a lot) but its really optimized for Kubuntu (which uses KDE). Id try some other tools first that do not rely on KDE.

---

### Post by nikkkko on 2009-10-22
> btw, semantik is a KDE app. It works with ubuntu (though it will require you to download a lot) but its really optimized for Kubuntu (which uses KDE). Id try some other tools first that do not rely on KDE.

AFAIK, Semantik is the only application of it's type, (mindmap), which integrates nicely, (ok, well just integrates), with OpenOffice.  I use Semantik all the time and it's one of Kubuntu's hidden gems.  Worth downloading the KDE elements for this application alone, IMHO, and once installed it works really well under Ubuntu.

Use Synaptic to install it if you are not familiar with the command line. (System>Administration>Synaptic). In the search box type 'Semantik', select it for installation and Synaptic will do the rest, adding all the KDE parts you need to make it work.

---

### Post by Trinaxia on 2009-10-23
Thanks a lot guy for your help..
Sounds a bit too complicated and time consuming for me. I just give up...
But again I really appreciate your help on that....

Big thanks to the ubuntu community

Sal

---

### Post by P4man on 2009-10-23
> **Trinaxia said:**
> Thanks a lot guy for your help..
Sounds a bit too complicated and time consuming for me. I just give up...
But again I really appreciate your help on that....

Big thanks to the ubuntu community

Sal

Surely you misread us?  Installing it is as easy as checking a checkbox in the add/remove applications. You were actually trying it the (very) hard way.

As for the KDE stuff, ignore it for now. It will not prevent Semantik or any app from working, it still installs the same way.

---

### Post by Trinaxia on 2009-10-23
When I go to add/remove menu in applications I get the below error message : 

"Could not launch menu item. Failed to execute child process "/sudo" (No such file or directory)"

---

### Post by P4man on 2009-10-23
> **Trinaxia said:**
> When I go to add/remove menu in applications I get the below error message : 

"Could not launch menu item. Failed to execute child process "/sudo" (No such file or directory)"

wow? Never seen or heard that one. That sounds bad. I think you have been removing stuff you shouldnt have. Either that or your disk is full perhaps? Is the rest still working normally?

Try this:

```
sudo apt-get install menu
```

Also what is the output of:

```
df -h
```

Both commands should be entered in a terminal, which you can start from applications > accessories

---

### Post by Trinaxia on 2009-10-23
yes everything is working fine for more than 6 months now....
May be should I reinstall ubuntu a second time?

---

### Post by P4man on 2009-10-23
that sounds a bit drastic. It could be something trivial. Or perhaps you just dont have the permissions (though that would give another error normally)

What happens when you open a terminal and type

```
gnome-app-install
```

?

---

### Post by Trinaxia on 2009-10-23
this is what I get with df -h

salvatore@Jensen:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G  4.3G   64G   7% /
varrun                629M  112K  629M   1% /var/run
varlock               629M     0  629M   0% /var/lock
udev                  629M   52K  629M   1% /dev
devshm                629M   12K  629M   1% /dev/shm
lrm                   629M   40M  590M   7% /lib/modules/2.6.24-24-generic/volatile
gvfs-fuse-daemon       71G  4.3G   64G   7% /home/salvatore/.gvfs
salvatore@Jensen:~$ 


and this is what I get with the other command

salvatore@Jensen:~$ sudo apt-get install menu
sudo: unable to resolve host Jensen
[sudo] password for salvatore: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
menu is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
salvatore@Jensen:~$

---

### Post by Trinaxia on 2009-10-23
This is herebelow what I get plus a pop up new screen inviting for new applications to install


** (gnome-app-install:26056): WARNING **: return value of custom widget handler was not a GtkWidget
/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py:1255: GtkWarning: gtk_tree_model_sort_sort: assertion `tree_model_sort->default_sort_func != NULL' failed
  item.applications.set_default_sort_func(None)
salvatore@Jensen:~$

---

### Post by P4man on 2009-10-23
> **Trinaxia said:**
> This is herebelow what I get plus a pop up new screen inviting for new applications to install


** (gnome-app-install:26056): WARNING **: return value of custom widget handler was not a GtkWidget
/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py:1255: GtkWarning: gtk_tree_model_sort_sort: assertion `tree_model_sort->default_sort_func != NULL' failed
  item.applications.set_default_sort_func(None)
salvatore@Jensen:~$

aha. So its just a problem with the menu somehow. Did you ever try changing those menu's by yourself?

Anyway, what you see now is what you should get when clicking add/remove programs. You can use that to install semantik (or any other app) easily.

To fix the menu entry for that, right click on Applications (main menu) and select "edit menu".
Then youll see something like this:

[IMG]http://img132.imageshack.us/img132/7227/screenshot008v.png[/IMG]

Then click on Applications on the left pane, and in the right scroll down to the end.

Select "add remove applications" click on Properties 
[IMG]http://img190.imageshack.us/img190/9513/screenshot006r.png[/IMG]
and make sure the Command box has this in it:
```
/usr/bin/gnome-app-install
```

---

### Post by Trinaxia on 2009-10-23
i think we are almost there....

When I type now semantik it appears indeed in the right box but already with the tick marked box. So it is like it is there but I can't find it in the application menu or anywhere else.

If I release the tick mark I might uninstall it so I dont change anything

Thanks a thoushands time

---

### Post by P4man on 2009-10-23
Ok so I lied. Its not one click, its two or three :D
Check the box, then click on "apply changes". Type your password when prompted and agree to install the dependencies. Then when its finished you'll find it in the menus somewhere.

---

### Post by P4man on 2009-10-23
Oh wait its already installed.. I may have misunderstood.
Well.. in that case, it could be that you have more weirdness in your menu. Use the same procedure I gave to fix the add/remove menu item to see if its not deselected in the menu.(deselected there means hidden in the menu)

Alternatively you could test if it really is installed by running semantik from a terminal or by pressing alt+F2 and typing semantik.

---

### Post by Trinaxia on 2009-10-23
when typing in the search box of :application / add-remove menu then semantik appears indeed but the problem is precisely that I cannot apply changes because the button is grey highlighted....so don't know again what to do....

Alternatively typing "semantik" in terminal returns the message "commande not found"

Thanks again for your devotion

---

### Post by P4man on 2009-10-23
something odd going on there...
Oh well, terminal to the rescue i guess. Try this:

```
sudo apt-get install --reinstall semantik
```

Keep in mind everything in ubuntu (linux) is case sensitive. So **s**emantik is not the same as **S**emantik.

---

### Post by Trinaxia on 2009-10-23
something run indeed with this command but still can't find it in applications and the button to apply changes is still grey highlighted and the box is ticked.

Terminal gives :

salvatore@Jensen:~$ semantik
bash: semantik: command not found
salvatore@Jensen:~$ 

yes i pay attention to the case

thank you.....again  :(

---

### Post by P4man on 2009-10-23
**Perhaps any of the semantik users can help out here?**
 Im not sure how to start it from a command line nor where in the menu its supposed to be. Id rather not install all the KDE dependencies on my system to find out.

---

### Post by marcoftheknight on 2010-06-05
Creating a launcher for Semantik

--> GO to Synaptic package manager search for semantik download.
once downloaded go to system--> preferences--> main menu --> new item 

Name; semantik
command: gksu semantik
Description : excellent mind mapping tool

BooM ! launch well and you can save files butI havent figured out how to open those files except with semantik itself for some reason I can see the files on my desktop even though Semantik does it could be that GNome doesnt recognize that type of file but anyways you can open them when you have semantik open so thats good enough and if word office works with it ( havent tried Yeat But I willl THen WAHOO)

Thanks everyone keep up the ubuntu legacy

---

