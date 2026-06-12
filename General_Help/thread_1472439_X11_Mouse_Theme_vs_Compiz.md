---
title: "X11 Mouse Theme vs Compiz"
date: 2010-05-04
forum: General Help
---

### Post by revslaughter on 2010-05-04
Hi there,

When I try to change my mouse cursor theme through gnome-appearance-properties, my cursor only changes to the selected themes in only certain situations, but is the default most of the time. Due to some vision problems, it is hard for me to see the default cursor, and would prefer a size 24 DMZ-Black theme for the pointer.

I've been searching for some solutions, and it looks like Compiz has taken over some duties regarding the mouse cursor and how it looks. That's fine, I love Compiz, I use the screen magnifier and zoom all the time - so turning Compiz off is not an option.

Most solutions I've found call for changing the mouse theme in compiz. However, most of those posts are at least 2 years old, and my current version of ccsm doesn't have an option to change the mouse theme. I found 'cursor_size' and 'cursor_theme' in gconf-editor (apps > compiz > general > allscreens > options), but making those keys match those found in (desktop > gnome > peripherals > mouse) has brought me no success.

I'm using Lucid Lynx with all updated packages, upgraded from Karmic. Any help from you would be tremendously appreciated.

---

### Post by revslaughter on 2010-05-14
Bump after a week? I have still not found a solution :(

---

### Post by hyperman on 2010-05-15
same over here
and there isn't any mouse configuration option in Compiz too
=\

---

### Post by revslaughter on 2010-05-16
OK - found an awesome post from Redditor aperson pertaining to this issue, the .debs for compiz-core are immediate fixes to the problem. [The link to the reddit thread is here.](http://www.reddit.com/r/Ubuntu/comments/c3s1e/using_1004_compiz_and_find_you_cant_completely/)

It appears that the problem is upstream, according to [this bug report filed by the redditor who figured out the problem](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/459647/comments/44).

Anyway, now I can help myself and a mostly-blind relative see our mouses!! :guitar:

---

### Post by a person on 2010-05-16
Glad I could be of some help.  I have a couple of other .debs in my /deb folder if anyone cares to poke around.

Just to recap what I had in the post:

I have the fixed [i386](http://dl.dropbox.com/u/64866/compiz-core_0.8.4-0ubuntu15_i386.deb) and [amd64](http://nosrepa.ath.cx/deb/compiz/compiz-core_0.8.4-0ubuntu15_amd64.deb) packages of 0.8.4 compiz-core.  I have a mirror on my home box [here](http://nosrepa.ath.cx/deb/compiz/).

To prevent the packages from being upgraded with the versions from the repositories (it will every time regardless if there's a newer version or not), open up a terminal and do a:

```

sudo aptitude hold compiz-core

```

When this is fixed in the repos, you can just unhold the package.

I followed instructions from [this](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/459647/comments/44) comment from [this](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/459647/) bug report.

Oh, and if you feel this is resolved, please mark the thread [solved].

---

### Post by granny6989 on 2010-06-08
That worked for me as well, to get my pointer theme to stay put (Lucid Lynx).
Just install the .deb, and log out/in, and I finally have one cursor. Thanks.
S*

---

### Post by s1mple_M4N on 2010-07-07
Awesome! Works for me too.

Thanks to everyone who helped out with this issue.

RoyJ

---

### Post by trusktr on 2010-08-08
Any idea how to apply this fix for Arch Linux? We don't use debs over here, and i don't have that mentioned file where the bug exists, but i indeed have the same problem.

---

### Post by rozen on 2010-08-18
Thanks for the corrected deb; it seems to work for me.

My question now is about the command:

      sudo aptitude hold compiz-core

I did that but then the update manager still wants to update compiz-core as does 
   
      sudo apt-get upgrade.

I have heard negative things about aptitude and generally use apt-get or synaptic.  Is there a way to do a "hold-like" function in the apt-get environment.  Am I off base about aptitude?

Thanks in Advance,
Don

---

### Post by revslaughter on 2010-08-18
I think that the command you want is

```
sudo echo "compiz-core hold" | sudo dpkg --set-selections
```

it's what works for me, anyhow. I think ```
aptitude hold
``` only works if you use aptitude to update. Since aptitude, apt, and the GUI programs all use dpkg at some point it makes most sense to do this.

To unhold compiz-core, 

```
sudo echo "compiz-core install" | sudo dpkg --set-selections
```

will set it back to install.

---

### Post by dyess002 on 2011-06-30
These links won't load for me. I am using 11.04 so it may not work.

---

