---
title: "grid in CompizConfig Settings Manager 10.04rc"
date: 2010-04-29
forum: General Help
---

### Post by rcragun on 2010-04-29
I just installed 10.04 fresh on two computers, a laptop and desktop.  In 9.10 I had set the Grid option in CompizConfig Settings Manager to allow me to manipulate windows with key combinations.  Grid (in Windows Management section) is no longer showing up in 10.04.  Is this true for anyone else?  The "put" function is still working for moving windows around my dual monitor setup, but I'd sure like "grid" back.  Thoughts, anyone?

---

### Post by dmacdougall on 2010-04-30
I have the same problem in the official 10.04 release.  It looks like [this site]("http://wiki.compiz.org/Plugins/Grid") ([http://wiki.compiz.org/Plugins/Grid]("http://wiki.compiz.org/Plugins/Grid")) has instructions on how to clone the git repository for the grid plugin, compile it, and install it manually.

I haven't tried this yet, has anyone else come across a better solution?

---

### Post by rcragun on 2010-04-30
dmacdougall, I'm trying the manual install now.  Will let you know how it turns out.

---

### Post by dmacdougall on 2010-04-30
I found a workaround that very nearly emulates the functionality of Grid.

First it requires you install wmctrl, a program that lets you move windows from the command line.

```
sudo apt-get install wmctrl
```

Then, in the CompizConfig Settings Manager, you can use the Commands plugin to define the following:

```
wmctrl -r :ACTIVE: -e 0,<x>,<y>,<width>,<height>
```

Define x,y,width,height to be whatever you want, and bind each of these commands to the key combo of your choice.

It does not emulate the "click the button multiple times to toggle between 1/2, 1/3, 2/3 size of the screen" functionality that Grid has, but other than that it seems to work decently.

Source here: [http://ubuntuforums.org/archive/index.php/t-601186.html](http://ubuntuforums.org/archive/index.php/t-601186.html)

Any luck on compiling and installing Grid manually?

---

### Post by rcragun on 2010-04-30
Sorry, I had to actually go to work today and am just getting back to this.  The directions on [http://wiki.compiz.org/Plugins/Grid](http://wiki.compiz.org/Plugins/Grid)  worked, with one modification.  On the line where it says "git-checkout", remove the "-" so it reads "git checkout".  Et voila, it installed and it works.  Here are the instructions I followed:

In the terminal:

```
sudo gedit /etc/apt/sources.list
```Uncomment the "intrepid-backports main restricted universe multiverse" and "intrepid partner" repositories in your sources.list

In the terminal:

```

sudo aptitude update
sudo aptitude install git-core libtool compiz-dev compiz-fusion-bcop compizconfig-settings-manager
mkdir tmp
cd tmp
git clone git://anongit.compiz-fusion.org/compiz/plugins/grid
cd grid
git checkout 1281082ba678033e515a19419ca8ffe8641d744b
make
make install
ccsm

```
The last command opens the CompizConfig Settings Manager where you can enable and configure "grid".
I'm not 100% sure what I just did, but I think I just compiled something in Linux!  I'm feeling pretty impressed with myself at the moment!  :guitar:

---

### Post by dmacdougall on 2010-04-30
Great, it worked perfectly for me too.  Issue resolved.

---

### Post by NearlyALaugh on 2010-05-02
install **compiz-fusion-plugins-extra** to bring back "grid"

---

### Post by rcragun on 2010-05-02
> **NearlyALaugh said:**
> install **compiz-fusion-plugins-extra** to bring back "grid"

Much easier than how I did it.  Thank you!

---

### Post by jtheoof on 2010-05-05
> **NearlyALaugh said:**
> install **compiz-fusion-plugins-extra** to bring back "grid"

Waw that was easy, thanks!

---

### Post by grindboy on 2010-06-13
Perfect thanks :-)

---

### Post by Kurtosis on 2010-07-10
Thanks Nearly, I came here looking for that too.

---

### Post by falkaholic on 2010-07-12
I have had the same issue.

I installed compiz-fusion-plugins-extra and got the plug back.

My problem is that is just doesnt work at all. No errors, no nothing. This plugin used to work perfectly. I am on a fresh install of 10.04. 

I haven't installed it from git/source, I think its the same version anyway.

Got any ideas on how to fix this?

EDIT: Strangely Alt-Tab (switching windows) didnt work, but Shift-Alt-Tab (switch reverse order) does. I have managed to fix those issues by turning off and on the Visual Effects in Appearance prefs. 

Now if I can only fix this [this issue]("http://ubuntuforums.org/showthread.php?t=1371815")

---

### Post by SabreWolfy on 2011-06-21
> **NearlyALaugh said:**
> install **compiz-fusion-plugins-extra** to bring back "grid"

Thanks :)

---

