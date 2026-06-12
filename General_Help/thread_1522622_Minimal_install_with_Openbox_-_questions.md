---
title: "Minimal install with Openbox - questions"
date: 2010-07-02
forum: General Help
---

### Post by buddyd16 on 2010-07-02
I am trying to go through a minimal install of Ubuntu and add openbox on my netbook but am unsure of where to go after getting the main items that I know about installed.

Here is where I am at:

I installed xorg openbox menu tint2 thunar xterm with the no install recommends option

From here I am a little lost on where to go next I like not having the graphical login and do not mind having to type startx to begin the openbox session. I know how to configure openbox and tint2. What I would like to get up and going is:

1. wireless connection (wpa encryption) - I assume wireless-tools and network-manager are the packages needed for this??
2. system update program from standard desktop install
3. Not sure what else I would need

Also what items will I need in the openbox autostart script so that wireless, update service, etc startup automatically or do these items even get placed in the openbox autostart script.

thanks for any help

---

### Post by Zill on 2010-07-02
You might like to take a look at [CrunchBang Linux]("http://crunchbanglinux.org/").

---

### Post by 4Orbs on 2010-07-02
You might be interested in [THIS OPENBOX GUIDE.]("http://urukrama.wordpress.com/openbox-guide/#Gtkthemes")

---

### Post by buddyd16 on 2010-07-02
Zill: thanks for the suggestion however I am looking to go through the setup on my own rather than a preconfigured set up. 

40rbs: your link is more on the setup of openbox itself rather than the whole system.

I am more looking to find out want other essential packages I need if any above the standard minimal install and the packages I indicated in my initial post.

My system runs now but it feels like I am missing something.

---

### Post by 4Orbs on 2010-07-02
Assuming tint2 has a tray, if you want the network manager applet to show in the tint2 tray add this to your openbox autostart.sh:
```
nm-applet &
```
or, if you're using wicd instead of network manager add this:
```
wicd-client &
```
Neither of these applets will appear until after you reboot.

Openbox already includes a dock that will function as a tray separate from the tint2 tray, but you will need to install docker for it to work as a tray.
```
sudo apt-get install docker
```

I also suggest installing Synaptic Package Manager unless you prefer just using apt-get from the terminal.

You can find the necessary update-manager packages in synaptic.

I recommend: for using gtk2 themes in openbox install lxappearance, for wallpapers install nitrogen, for easily changing or adding entries in your openbox menu install obmenu. For menu's to automatically update when new applications are installed- install openbox-xdgmenu which also requires libxml2-dev to work correctly. To easily change your openbox themes and settings install obconf.

---

### Post by urukrama on 2010-07-03
> **buddyd16 said:**
> 1. wireless connection (wpa encryption) - I assume wireless-tools and network-manager are the packages needed for this??

Though I rarely use wireless, I prefer wicd over nm-applet. I find it more user friendly, it has fewer dependencies and has a neat command line interface (*wicd-curses*).

> **buddyd16 said:**
> 2. system update program from standard desktop install

That will be the same as on a full ubuntu install. You can do it all from the command line (with apt-get or aptitude). If you prefer to use a GUI, you can use Synaptic, though you would have to install this first with apt-get. You will also need gksudo to be able to run Synaptic as root.

```
sudo apt-get install synaptic gksudo
```

Then run Synaptic with the following command: *gksudo synaptic*. Add this to your Openbox menu or assign a keybinding to it and you will be able to install and update packages as you could in Ubuntu.

I am not sure if the [update-notifier]("http://packages.ubuntu.com/lucid/update-notifier") works outside of Gnome, as I don't use it. In case it does not work, you can update with *sudo apt-get update && sudo apt-get upgrade * or *sudo aptitude update && sudo aptitude safe-upgrade* or through Synaptic.

> **buddyd16 said:**
> 3. Not sure what else I would need

That depends on your preferences. ;)

> **buddyd16 said:**
> Also what items will I need in the openbox autostart script so that wireless, update service, etc startup automatically or do these items even get placed in the openbox autostart script.

You can add something like this to your autostart file:

```
(sleep 2 && wicd-client) &
(sleep 3 && update-notifier) &
```

Some applications need to be launched after Openbox (or other applications in the autostart file) have started. That is why the *sleep* command is used. The number after *sleep* is the number of seconds it waits to execute the command that follows the *sleep* command. Adjust the times if these applications do not start. See [here]("http://crunchbanglinux.org/wiki/howto/autostart_programs") for more info.

---

### Post by nothingspecial on 2010-07-03
You can use wicd-curses to set up your network from the terminal. It`s an ncurses "gui" for wicd, kind of like cmus or mc but for your network.

First thing I install after a minimal istalation.

---

### Post by Zill on 2010-07-03
> **buddyd16 said:**
> Zill: thanks for the suggestion however I am looking to go through the setup on my own rather than a preconfigured set up...
Understood but my suggestion was based on the fact that CrunchBang is (of course!) open source and you are therefore free to examine the scripts and source code to see how problems have been resolved.

If you find better ways of doing things then, as long as they are also released under the GPL, they could in turn end up in other distros, such as CrunchBang.  Such is the wonder of FOSS. :-)

---

### Post by nothingspecial on 2010-07-03
My rc.xml is a heavily edited default crunchbang one.

You`ll find it alot easier to add and remove stuff to and from that than to start from scratch.

I use it with a ubuntu minimal install rather than Crunchbang itself.

It`s not cheating, I promise :-\"

---

### Post by buddyd16 on 2010-07-03
Zill: ah good call I didn't even think about going through the scripts used by crunchbang.

40rb and Urukrama: Thank you very much for your walkthroughs

---

### Post by philthyfill on 2010-07-26
Sorry to thread jack. I also did a minimal install of Ubuntu with Openbox. I'm still in the process of setting it up, but I see a lot of errors when I exit my Openbox session. Is there a way to view those errors in a log file?

---

