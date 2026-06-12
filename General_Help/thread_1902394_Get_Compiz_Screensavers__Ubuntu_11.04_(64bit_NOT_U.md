---
title: "Get Compiz Screensavers?  Ubuntu 11.04 (64bit NOT UNITY)"
date: 2011-12-30
forum: General Help
---

### Post by cbanakis on 2011-12-30
I'm trying to find the Compiz Screensaver Plug-in.

Running Gnome Desktop on 11.04 64bit

Every thread/post I find has outdated info, and broken links.

If someone can please point me in the right direction, and maybe some install instructions if theres more to it than installing a deb.

I did find a 32bit rpm that "I think" has the screen saver plug ins.
So if there is an easy way to convert that, I can use it.

I already tried converting with alien, but I guess its not that easy since it needs to be converted to 64bit too.

I really did not want to start yet another thread about this, because there appears to be several already.
But after months of searching and finding broken links, and outdated info, I finally broke down.

Thanks

---

### Post by JOHNNYG713 on 2011-12-30
**see this** !! [http://gnome-look.org/content/show.php/Compiz+Experimental+Plugins+UPDATED%21+%21?content=118511](http://gnome-look.org/content/show.php/Compiz+Experimental+Plugins+UPDATED%21+%21?content=118511)

---

### Post by cbanakis on 2011-12-30
> **JOHNNYG713 said:**
> **see this** !! [http://gnome-look.org/content/show.php/Compiz+Experimental+Plugins+UPDATED%21+%21?content=118511]("http://gnome-look.org/content/show.php/Compiz+Experimental+Plugins+UPDATED%21+%21?content=118511")


Looks like another broken link..



Thanks for the post though :(

---

### Post by cbanakis on 2011-12-30
I have spent several hours searching, and I'm honestly starting to wonder if these plug-ins were somehow erased from the internet?

Somebody has to have the files.  Right?

LOL

---

### Post by JOHNNYG713 on 2011-12-31
> **cbanakis said:**
> Looks like another broken link..



Thanks for the post though :(

Simply open terminal and follow the instructions on the page !!!! :P

```
**sudo apt-get install git**


``````
**cd ~/Downloads**


``````
[B]sudo apt-get install compiz-fusion-bcop compiz-dev \build-essential libtool \libglu1-mesa-dev libxss-dev \libcairo2-dev git-core
git clone git://anongit.compiz.org/users/soreau/scripts
[/B]


``````
**cd ~/scripts**


``````
[B]./compiz-addons install all
[/B]


``````
**nohup compiz --replace**


```[B]Note : you may have to reboot !
 

YOU INSTALL THESE EXPERIMENTAL COMPIZ PLUGINS AT YOUR OWN EXPENSE !

this git has new plugins !!! But lacks some others at this point I will keep you updated!

Enjoy !![/B]

---

### Post by cbanakis on 2012-01-03
After I run...

git clone git://anongit.compiz.org/users/soreau/scripts

I get the following error...

Cloning into scripts...
anongit.compiz.org[0: 195.114.19.35]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)

Is that basically just another broken link/repo?
Or am I doing something wrong?

Thanks for the post

> **JOHNNYG713 said:**
> Simply open terminal and follow the instructions on the page !!!! :P

```
**sudo apt-get install git**


``````
**cd ~/Downloads**


``````
[B]sudo apt-get install compiz-fusion-bcop compiz-dev \build-essential libtool \libglu1-mesa-dev libxss-dev \libcairo2-dev git-core
git clone git://anongit.compiz.org/users/soreau/scripts
[/B]


``````
**cd ~/scripts**


``````
[B]./compiz-addons install all
[/B]


``````
**nohup compiz --replace**


```[B]Note : you may have to reboot !
 

YOU INSTALL THESE EXPERIMENTAL COMPIZ PLUGINS AT YOUR OWN EXPENSE !

this git has new plugins !!! But lacks some others at this point I will keep you updated!

Enjoy !![/B]

---

### Post by cbanakis on 2012-01-06
*Bump

---

### Post by JOHNNYG713 on 2012-01-11
Try this ! Untar and run in terminal !

---

### Post by cbanakis on 2012-01-11
Seemed to work up to a certain point.

Looks like everything beyond installing anaglyph errors out?

```
i = Install s = Skip u = Uninstall a = Install all remaining without prompting q = Quit
What would you like to do for anaglyph? i/s/u/a/q: a
Installing all remaining without prompting..
Cloning into anaglyph...
anongit.compiz.org[0: 195.114.19.35]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
Error occured. Please see http://forum.compiz.org/viewtopic.php?f=114&t=12012 and report any problems.
Cloning into animationjc...
anongit.compiz.org[0: 195.114.19.35]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
Error occured. Please see http://forum.compiz.org/viewtopic.php?f=114&t=12012 and report any problems.
Cloning into atlantis...
anongit.compiz.org[0: 195.114.19.35]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
Error occured. Please see http://forum.compiz.org/viewtopic.php?f=114&t=12012 and report any problems.
Cloning into cubemodel...
anongit.compiz.org[0: 195.114.19.35]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
Error occured. Please see http://forum.compiz.org/viewtopic.php?f=114&t=12012 and report any problems.
Cloning into dialog...
anongit.compiz.org[0: 195.114.19.35]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
Error occured. Please see http://forum.compiz.org/viewtopic.php?f=114&t=12012 and report any problems.
Cloning into extra-animations...
anongit.compiz.org[0: 195.114.19.35]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
Error occured. Please see http://forum.compiz.org/viewtopic.php?f=114&t=12012 and report any problems.
Cloning into fakeargb...
anongit.compiz.org[0: 195.114.19.35]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
Error occured. Please see http://forum.compiz.org/viewtopic.php?f=114&t=12012 and report any problems.
Cloning into freewins...
anongit.compiz.org[0: 195.114.19.35]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
Error occured. Please see http://forum.compiz.org/viewtopic.php?f=114&t=12012 and report any problems.
Cloning into ghost...
anongit.compiz.org[0: 195.114.19.35]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
Error occured. Please see http://forum.compiz.org/viewtopic.php?f=114&t=12012 and report any problems.
Cloning into photowheel...
anongit.compiz.org[0: 195.114.19.35]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
Error occured. Please see http://forum.compiz.org/viewtopic.php?f=114&t=12012 and report any problems.
Cloning into screensaver...
anongit.compiz.org[0: 195.114.19.35]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
Error occured. Please see http://forum.compiz.org/viewtopic.php?f=114&t=12012 and report any problems.
Cloning into showrepaint...
anongit.compiz.org[0: 195.114.19.35]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
Error occured. Please see http://forum.compiz.org/viewtopic.php?f=114&t=12012 and report any problems.
Cloning into simple-animations...
anongit.compiz.org[0: 195.114.19.35]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
Error occured. Please see http://forum.compiz.org/viewtopic.php?f=114&t=12012 and report any problems.
Cloning into snowglobe...
anongit.compiz.org[0: 195.114.19.35]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
Error occured. Please see http://forum.compiz.org/viewtopic.php?f=114&t=12012 and report any problems.
Cloning into sound...
anongit.compiz.org[0: 195.114.19.35]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
Error occured. Please see http://forum.compiz.org/viewtopic.php?f=114&t=12012 and report any problems.
Cloning into stackswitch...
anongit.compiz.org[0: 195.114.19.35]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
Error occured. Please see http://forum.compiz.org/viewtopic.php?f=114&t=12012 and report any problems.
Cloning into startup...
anongit.compiz.org[0: 195.114.19.35]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
Error occured. Please see http://forum.compiz.org/viewtopic.php?f=114&t=12012 and report any problems.
Cloning into static...
anongit.compiz.org[0: 195.114.19.35]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
Error occured. Please see http://forum.compiz.org/viewtopic.php?f=114&t=12012 and report any problems.
Cloning into swap...
anongit.compiz.org[0: 195.114.19.35]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
Error occured. Please see http://forum.compiz.org/viewtopic.php?f=114&t=12012 and report any problems.
Cloning into throw...
anongit.compiz.org[0: 195.114.19.35]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
Error occured. Please see http://forum.compiz.org/viewtopic.php?f=114&t=12012 and report any problems.
Cloning into tile...
anongit.compiz.org[0: 195.114.19.35]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
Error occured. Please see http://forum.compiz.org/viewtopic.php?f=114&t=12012 and report any problems.
Cloning into toggle-decoration...
anongit.compiz.org[0: 195.114.19.35]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
Error occured. Please see http://forum.compiz.org/viewtopic.php?f=114&t=12012 and report any problems.
Cloning into trip...
anongit.compiz.org[0: 195.114.19.35]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
Error occured. Please see http://forum.compiz.org/viewtopic.php?f=114&t=12012 and report any problems.
Cloning into vidcap...
anongit.compiz-fusion.org[0: 195.114.19.35]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
Error occured. Please see http://forum.compiz.org/viewtopic.php?f=114&t=12012 and report any problems.
Cloning into vignetting...
anongit.compiz.org[0: 195.114.19.35]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
Error occured. Please see http://forum.compiz.org/viewtopic.php?f=114&t=12012 and report any problems.
Cloning into winreflect...
anongit.compiz.org[0: 195.114.19.35]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
Error occured. Please see http://forum.compiz.org/viewtopic.php?f=114&t=12012 and report any problems.
Cloning into wizard...
anongit.compiz-fusion.org[0: 195.114.19.35]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
Error occured. Please see http://forum.compiz.org/viewtopic.php?f=114&t=12012 and report any problems.
Cloning into workspacenames...
anongit.compiz.org[0: 195.114.19.35]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
Error occured. Please see http://forum.compiz.org/viewtopic.php?f=114&t=12012 and report any problems.
Done.
Don't forget to restart compiz and ccsm after installing or removing any plugin. Enjoy! :-)

```

> **JOHNNYG713 said:**
> Try this ! Untar and run in terminal !

---

### Post by cbanakis on 2012-01-12
HOLY CRAP!!!

Words cannot express how sorry I am for wasting everyones time.

I tried to add the experimental plugins at home this morning, and it worked fine.

Then when I got to work, I tried again with the same failed results.

Then I started thinking...

"Maybe our work internet is blocking the plugin source???"

A coworker lent me his cell phone which was setup as a wifi hot-spot.

And everything worked perfectly.

WTF!?!?!?!

Thank you all for your patience, and your help.

I have to stop typing now, so I can see my shiny new screensaver.

Thanks again.

---

