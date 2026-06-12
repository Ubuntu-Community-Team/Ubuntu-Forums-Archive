---
title: "Zombie infestation with 12.04.1"
date: 2012-08-30
forum: General Help
---

### Post by JKyleOKC on 2012-08-30
I've just installed Xubuntu 12.04.1 64-bit this past week, on a brand new box. It's been an adventure, as witness half a dozen help threads I've begun along the way. However it's now working acceptably, and I have time to deal with some annoying little loose ends.

The first I want to tackle is an infestation of zombie processes. Each time I run "top" to see what is going on, the number of zombies has increased. Finally this afternoon I ran "ps ax|grep Z" to see what they were -- and most of them are the LightDM display manager. Apparently, it goes zombie each time I log out! A few, though, were xfce-terminal, and I've not been able to determine what is creating those.

A possible companion to this problem is in another thread I posted here, at [http://ubuntuforums.org/showthread.php?t=2049501](http://ubuntuforums.org/showthread.php?t=2049501), about the CPU Graph panel applet losing its associated command. Since that vanishing command is "xterm -e top" there might be a connection to the zombie terminal process -- or this might be a red herring.

In [http://ubuntuforums.org/showthread.php?p=12206895?postcount=9](http://ubuntuforums.org/showthread.php?p=12206895?postcount=9) Toz suggested that using Xfce 4.10 from a PPA might solve another problem. Has anyone experimented with it to see if it might deal with the Zombies also, or the vanishing command?

It's all fun, and a great learning experience. However I could certainly do with a little less fun for the rest of this week at least...

---

### Post by pqwoerituytrueiwoq on 2012-08-30
i have been using xfce 4.10 for a while now on my laptop and on my desktop for a few days 
i have not noticed any zombie takeover of my system

as for the applet loosing it command try this 
[FONT=Courier New]xfce4-panel -s[/FONT]
This made my places applet keep its settings on xfce 4.10 for me should work on that applet also

---

### Post by vasa1 on 2012-08-31
4.10 here.
The only zombie I'm seeing is the xfce terminal one. And that's quite an old bug.
I don't use the CPU Graph applet and can't comment on that.

---

### Post by JKyleOKC on 2012-08-31
Well, I went to the xfce 4.10 web sites and discovered that it claims to have fixed the CPU Graph problem, so it looks as if going to 4.10 will deal with several of my annoyances.

However since it's taken me so long to get this new installation working to fill my needs, I'm a bit shy of just plunging into a change of the full window manager. Can one of you tell me in detail just how to go about making that change while retaining as much as possible of the customization I've done to Xubuntu (changed the panel contents, modified the lightdm login screen, added a few custom launchers to the desktop)? I'm no newbie to Linux or Xubuntu, just being (possibly overly) cautious. Can it be as simple as just adding the PPA and then installing the 4.10 version via Synaptic?

---

### Post by pqwoerituytrueiwoq on 2012-08-31
you may have to re-comstmize the login screen, but not sure been too busy working on the stiff after the login screen to mess with that
i only used xfce 4.8 10 min before upgrading to 4.10
upgrade in a single terminal line
```
sudo apt-add-repository ppa:xubuntu-dev/xfce-4.10 -y;sudo apt-get dist-upgrade -y;sudo reboot
```
edit:
my cpu applet is really stubborn i have to click it like 20 times to get a task manager, nrv i have to click the border around the graph

---

### Post by JKyleOKC on 2012-08-31
I didn't do a dist-upgrade because I was afraid it would mangle most of my customizations. Instead, I used Synaptic to upgrade just the xfwm4 package (to 4.10) initially, then did a reload in Synaptic to pick up all needed updates from that, which brought almost everything in. I finally did an upgrade to xubuntu-desktop, which got it all -- and did not mangle my customizations.

However, I had earlier been experimenting with saving settings at logout time, and the new xfce routines started refusing to let me log out (screen shot attached). I could, however, "switch users" to get out, and after clearing all of the checkboxes associated with saving sessions, clearing all saved sessions, stopping lightdm, and finally re-starting lightdm from TTY2, this problem seems to be gone now.

The CPU graph now retains its command, but it's not possible to click on the graph itself to launch it (I run "top" instead of "task manager" but this has nothing to do with it). I have to put the point of the arrow in the middle of that narrow margin below the graph to launch the command. I think we should report this as a serious bug, especially since it worked properly in xfce 4.6 shipped with Lucid.

The zombies from lightdm, unfortunately, seem to still be present...

---

### Post by pqwoerituytrueiwoq on 2012-08-31
without a dist upgrade you will have problems, it is either 4.10 or 4.8

---

### Post by JKyleOKC on 2012-09-01
> **JKyleOKC said:**
> The CPU graph now retains its command, but it's not possible to click on the graph itself to launch it (I run "top" instead of "task manager" but this has nothing to do with it). I have to put the point of the arrow in the middle of that narrow margin below the graph to launch the command. I think we should report this as a serious bug, especially since it worked properly in xfce 4.6 shipped with Lucid.

The zombies from lightdm, unfortunately, seem to still be present...Unfortunately I spoke too soon. The applet is now losing its command again, although it did work for a few sessions -- possibly because I was still working with automatic session saves enabled, and have since disabled them.

---

### Post by pqwoerituytrueiwoq on 2012-09-02
unable to reproduce your applet issue on xfce 4.10
i have to click the column pixles between the bars and the graph to get top to open with it

---

### Post by JKyleOKC on 2012-09-02
Take a look at post #5 in this thread: [http://ubuntuforums.org/showthread.php?p=12213139#post12213139](http://ubuntuforums.org/showthread.php?p=12213139#post12213139)

Is your installation retaining the associated command properly from one session to another?

Even if it is, I found that upgrading to the 1.0.5 applet from the Quetzal area solved the problem of having to click in the tiny border. It now works for me when clicking in the middle of the graph, just as it does in the original Lucid installation.

---

### Post by pqwoerituytrueiwoq on 2012-09-02
thanks for sharing the solution and i can confirm it works with xfce 4.10
edit:
someone removed the link...
64bit:
[http://launchpadlibrarian.net/112472471/xfce4-cpugraph-plugin_1.0.5-0ubuntu1_amd64.deb](http://launchpadlibrarian.net/112472471/xfce4-cpugraph-plugin_1.0.5-0ubuntu1_amd64.deb)
32bit:
[http://launchpadlibrarian.net/112472473/xfce4-cpugraph-plugin_1.0.5-0ubuntu1_i386.deb](http://launchpadlibrarian.net/112472473/xfce4-cpugraph-plugin_1.0.5-0ubuntu1_i386.deb)

---

### Post by JKyleOKC on 2012-09-23
The zombie invasion can apparently be cured, too, by grabbing the latest Quetzal build of the lightdm package and installing it via dpkg. See my thread at [http://ubuntuforums.org/showthread.php?t=2061889](http://ubuntuforums.org/showthread.php?t=2061889) post #4. I've not yet made the change on my production system but the test system seems to have survived without damage...

EDIT: The cause of the zombie attack, according to the bug filed on launchpad, was an authentication request when changing from one user to another. That's probably why so few folk see it; the one machine of mine that was infested is used both by me and my wife, with separate user names, which brought it to the surface.

---

