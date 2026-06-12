---
title: "Please teach me how to install vegastrike-linux-0.5.0.rar"
date: 2009-11-01
forum: General Help
---

### Post by szaemon on 2009-11-01
Hi All,
Thanks for reading my help request.

I just downloaded this game from [http://vegastrike.sourceforge.net/getfiles/](http://vegastrike.sourceforge.net/getfiles/)  the Archive Manager says,"Could not open "vegastrike-linux-0.5.0.rar"

Archive type not supported.". 

Could someone please tell me how to install this game?
Thanks,
szaemon

---

### Post by P4man on 2009-11-01
Is there any reason why you dont install vegastrike through add/remove programs (or ubuntu software center if you use karmic) ? Its in the repositories

If you must do it the hard way start by installing rar from that same add/remove programs.

---

### Post by 6205 on 2009-11-01
You must install unrar package with command [COLOR="DarkRed"]sudo apt-get install unrar[/COLOR] through terminal, or search for it in Synaptic package manager

---

### Post by Waappu on 2009-11-01
Hi,

You can also download tar
[http://downloads.sourceforge.net/vegastrike/vegastrike-linux-0.5.0.tar.bz2?use_mirror=osdn](http://downloads.sourceforge.net/vegastrike/vegastrike-linux-0.5.0.tar.bz2?use_mirror=osdn)

But it seems you do not have unrar installed ?
If you like install rar
```
sudo aptitude install rar unrar
```

And Vega Strike seems to be also in 8.04 and 9.04 repor
So just type to terminal
```
sudo aptitude install vegastrike
```

---

### Post by szaemon on 2009-11-01
Hi folks, 
Thanks for the quick response.

I read on the Vega Strike Home Page that the Ubuntu Repo version was old, so I downloaded this one. 

Thanks for the help. I'll get the unrar thing and then try again.
szaemon

---

### Post by szaemon on 2009-11-01
How strange. I just tried installing from the Ubuntu Software Center and the installation refused to go through. It said "requires installation from an unauthorized source" there was no option to say "yes that's what I wanna do". So it just didn't install.
..hmmm.....

---

### Post by P4man on 2009-11-01
Not sure about jaunty, but in karmic the repo's seem to offer the latest stable version (0.5).

---

### Post by P4man on 2009-11-01
> **szaemon said:**
> How strange. I just tried installing from the Ubuntu Software Center and the installation refused to go through. It said "requires installation from an unauthorized source" there was no option to say "yes that's what I wanna do". So it just didn't install.
..hmmm.....

Hmm. Maybe you have to enable multiverse. Try isntalling it from add/remove programs in system > adminstration. Make sure to enable "all available software" in the drop down.

---

### Post by szaemon on 2009-11-01
I don't know what's goin' on with this stuff. But the rar file I got, I was able to open and extract. Thanks for that bit of information folks. However, it didn't install properly and won't start up. I enabled all the software sources, but the Ubuntu Software Center still says the same thing. Then I checked the repos... and it shows version 0.5 available...
so I guess that's my answer.
...Now I just have to find and edit the default game startup cause I hate starting with no cash. It makes game play long and dull...

---

### Post by szaemon on 2009-11-01
Well, that didn't work. The Repo downloaded the game, but when I try to play it, the screen blips out for a second then comes back showing my desktop...but not game starts up.
hmmm...

---

### Post by P4man on 2009-11-01
try starting it from a terminal (apps > accessories> terminal) so you can see any errors it produces. Not sure what the command is to launch that game, I suspect just 

```
vegastrike
```

If not,  you can see it by editing the menu and check the properties of the game launcher there. 

What videocard and drivers do you have?

---

### Post by rCXer on 2009-11-01
> **P4man said:**
> Not sure about jaunty, but in karmic the repo's seem to offer the latest stable version (0.5).

The vegastrke in the repository is broken as reported in [this bug](https://bugs.launchpad.net/ubuntu/+source/vegastrike-data/+bug/403698). Don't use it and save yourself from misery :cry:  Although the actual program is version 0.5. In karmic, the vegastrike-data is still [version 0.4.3](http://packages.ubuntu.com/karmic/vegastrike-data).  If you already installed it from the repos, just uninstall it.

To install from the tar.gz unpack the it into a your home directory (/home/username/vegastrike-0.5.0).  In the terminal just type...
```

cd /home/username/vegastrike-0.5.0
sudo ./vsinstall.sh

```

---

### Post by szaemon on 2009-11-02
Thanks for the help folks.

I completely removed vegastrike through Synaptic. Now as for the installation of a working version, I don't have a .tar.gz file. I have only a .rar file : vegastrike-linux-0.5.0.rar and I'm downloading a .tar.bz2 now. Should I treat that the same as a .tar.gz file?
Thanks again for the help!

---

### Post by rCXer on 2009-11-02
If you're extracting the file from the terminal it's slightly different. But if you are doing it graphically it's the same process. For example, if you downloaded the file to your desktop, in the terminal type something like...

```

tar -xvjf "/home/YourName/Desktop/vegastrike-linux-0.5.0.tar.bz2" -C "/home/YourName/"
cd /home/YourName/vegastrike-0.5.0/
sudo ./vsinstall.sh

```
Just follow the on-screen instructions after that.  If there are any any more problems, you can get help at the [vegastrike forums](http://vegastrike.sourceforge.net/forums/).

---

### Post by szaemon on 2009-11-03
Thanks. Do I need to go into the computer and remove pieces of the failed install attempts? Is it possible that the terminal command to start vegastrike may look into the broken files of the failed attempt and try to start from them instead of the freshly installed files?

---

### Post by rCXer on 2009-11-03
I don't think so (and I hope not ;)).  Does vegastrike run?

---

### Post by szaemon on 2009-11-10
Thanks. It took a while to figure it out, but I got it now.
I appreciate the help.

---

