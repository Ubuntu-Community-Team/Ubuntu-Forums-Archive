---
title: "lost my panels, how to get them back?"
date: 2010-12-15
forum: General Help
---

### Post by attilab on 2010-12-15
recent upgrade to 10.10
playing around with a NetworkManager (install/uninstall several), somewhere in between lost my lover panel completely, and the upper panel for apps won't take the mouse buttons anymore..........I just wanted to add the button for a network (tried the Wicd but just way too simple and got back to the NetworkManager) status ?! checked in the config editor, the panels are not locked. With 10.10 many features Im not confident, these panels, the workspace is allways running out, ect. 
I need the network list/status, driving around with my netbook, many times in library/starbucks free wifi, how could I select the available if I don't have a stat?

---

### Post by karthick87 on 2010-12-15
Type the following in your terminal,to reset your panel to the default one..

```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by Megaptera on 2010-12-15
Another option that's easy to use:
PanelRestore,allows you to quickly and easily restore the default Gnome panels in Ubuntu and to backup and restore your existing custom panel configurations.

More info here:[http://helpdeskgeek.com/linux-tips/easily-restore-the-default-gnome-panels-in-ubuntu/](http://helpdeskgeek.com/linux-tips/easily-restore-the-default-gnome-panels-in-ubuntu/)

---

### Post by attilab on 2010-12-15
> **karthick87 said:**
> Type the following in your terminal,to reset your panel to the default one..

```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

here is what its telling me:

attilab@attilab-netbook:~$ gconftool --recursive-unset /apps/panel && killall gnome-panel
gnome-panel: no process found

any other way?

---

### Post by Quackers on 2010-12-15
killall gnome-panel worked for me when I had a similar problem

---

### Post by attilab on 2010-12-15
I don't mind panel or no panel, 
I just want to make my NetworkManager be visible, in order to be able to chose from variety of wifi. Right now its not on the upper horisontal panel, but its working at home, not sure once Im on the road, how can I connect to a new wifi sources if I can't see or select the NM?

---

### Post by Quackers on 2010-12-15
I would imagine that the top panel needs to be present to show the applet.
If the top panel is there but the network manager applet is not try running nm-applet in the terminal. Is there any error message?

---

### Post by karmila on 2010-12-15
Hi attilab, do you still have the upper panel?
To start network-manager applet you can use this command:
```
nm-applet --sm-disable
```If you want the applet loaded up at start up you can add that command to your start-up applications.

Edit: Quackers told it first :D

---

### Post by attilab on 2010-12-16
ok guys, not that so fast, Im the ubuntu fan up to a level of web/email use. and here my knowledge pretty much stops.
yes, the upper panel is there, but won't take the 3rd mouse click. so can't find the network manager neither (at home is working auto), Im right now in the library, and writing this from W7 because in U10.10 I couldn't see and select any wifi.
will try further once I got home, thanks for this

---

### Post by attilab on 2010-12-17
> **Quackers said:**
> I would imagine that the top panel needs to be present to show the applet.
If the top panel is there but the network manager applet is not try running nm-applet in the terminal. Is there any error message?

how shall I interpret this :

attilab@attilab-netbook:~$ nm-applet
** Message: applet now removed from the notification area
** Message: applet now embedded in the notification area
** (nm-applet:1885): DEBUG: old state indicates that this was not a disconnect 0
^C** Message: Caught signal 2, shutting down...

---

### Post by attilab on 2010-12-17
> **karmila said:**
> Hi attilab, do you still have the upper panel?
To start network-manager applet you can use this command:
```
nm-applet --sm-disable
```If you want the applet loaded up at start up you can add that command to your start-up applications.

Edit: Quackers told it first :D

this one worked, the antenna is back to upper panel

attilab@attilab-netbook:~$ nm-applet --sm-disable
** Message: applet now removed from the notification area
** Message: applet now embedded in the notification area
** (nm-applet:1899): DEBUG: old state indicates that this was not a disconnect 0


actually not, the antenna was up at the upper panel until I shot down the terminal, but again disappeared...:( try it several times, once I close the terminal closes the running application :(

where is that NetworkManager apps located? Im browsing around to add it to the StartupApplicationPreferences, but can't find the thing...

---

### Post by astrobob.tk on 2010-12-17
> **attilab said:**
> recent upgrade to 10.10
playing around with a NetworkManager (install/uninstall several), somewhere in between lost my lover panel completely, and the upper panel for apps won't take the mouse buttons anymore..........I just wanted to add the button for a network (tried the Wicd but just way too simple and got back to the NetworkManager) status ?! checked in the config editor, the panels are not locked. With 10.10 many features Im not confident, these panels, the workspace is allways running out, ect. 
I need the network list/status, driving around with my netbook, many times in library/starbucks free wifi, how could I select the available if I don't have a stat?

Hello attilab,

I know a way that I personally haven't tested which I came across a couple of weeks ago on some website or blog on Ubuntu. here's is it as stated 
[[SIZE=4]_**Warning**_[/SIZE]: I haven't tested it + the forum & in general, using the command "rm" is not recommended specially if you don't know what you're doing. I post the commands below as is, with no guarantee. Its your sole responsibility]:

```
If you are new to ubuntu and for some reason if you accidently deleted top panel in ubuntu 10.04 don’t worry you can restore using the following procedure

Open the terminal and run the following commands

    gconftool-2 --shutdown

    rm -rf ~/.gconf/apps/panel

    pkill gnome-panel
```

---

### Post by attilab on 2010-12-18
I see more imput Im getting more Im trying, deepr I sink.......
(for me) this ubuntu will sooner or later become a real hobby, like a US Harley Davidson motorcycles (I don't have those any), 
you don't drive it but fixing all the time ?! That's why U buy European or Japanees.........:)

---

### Post by astrobob.tk on 2010-12-19
> **attilab said:**
> I see more imput Im getting more Im trying, deepr I sink.......
(for me) this ubuntu will sooner or later become a real hobby, like a US Harley Davidson motorcycles (I don't have those any), 
you don't drive it but fixing all the time ?! That's why U buy European or Japanees.........:)

well that's how you learn unix & linux. Personally, it took me a while to understand some basic stuff & get back to real day-2-day computing; but now I feel good about it coz I understand how bad & trashy windows is. Though I keep a dual boot system with Windows but I barely login. I more often login to windows to update it. Most of the time now I login to windows once every 6 months or so.

anyways this forum is your saviour, at least it is my saviour

---

### Post by attilab on 2010-12-19
> **astrobob.tk said:**
> ......I understand how bad & trashy windows is. ...
me2 just log to update the adaware and the antivirus, just in case....:)
btw, reinstalling right now 10.10 from scratch on my netbook, expecting better luck....:)

---

