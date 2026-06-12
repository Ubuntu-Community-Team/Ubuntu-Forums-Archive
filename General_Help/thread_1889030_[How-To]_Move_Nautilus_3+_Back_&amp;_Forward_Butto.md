---
title: "[How-To] Move Nautilus 3+ Back &amp; Forward Buttons to the Left of the Location Bar"
date: 2011-11-30
forum: General Help
---

### Post by nyteryder79 on 2011-11-30
OK, so I'm no Linux developer or even an expert of Linux, but I like to tinker and hack.  Since upgrading to 11.10, I've been frustrated with new location of the back and forward buttons.  It just didn't make any sense and isn't uniform with any other interface for browsing.  I don't really care about the search button, because I've never used it in my life.  Any way, I decided to dabble with the source code and I think I fixed it.  I've been using Nautilus the past few days without a hiccup with the back and forward buttons on the left, before the location/path bar.

Example before:

[[IMG]http://i.imgur.com/3JwSO.png[/IMG]](http://imgur.com/3JwSO)

Example after:

[[IMG]http://i.imgur.com/6sc7w.png[/IMG]](http://imgur.com/6sc7w)

It's really easy to do, and I've got the easy Terminal instructions below.  BTW, the version of Nautilus current as of this post is 3.2.1.  You will probably need to do this any time Nautilus gets updated through Update Manager.  The exact line number of the code that needs to change may vary as well.  If this is the case, just use find as I instruct below.

*Warning: I am not a professional and am not responsible for anything going wrong.  These instructions are simply a guide for how I personally managed to fix this annoyance.  Use at your own risk.*

First off, you may need to enable the "Source code" repository.  To do this in Ubuntu, press the Super/Windows key and type "Source".  Open the "Software Sources" application from the results.  Check the box before "Source code", then click close.

From Terminal:

```
mkdir ~/Desktop/nautilus-mod

cd ~/Desktop/nautilus-mod

sudo apt-get update

apt-get source nautilus

sudo apt-get build-dep nautilus

cd ~/Desktop/nautilus-mod/nautilus-3*

gedit src/nautilus-toolbar.c
```

Now, scroll down to line 132 or do a "find" for "gtk_toolbar_insert (GTK_TOOLBAR (self->priv->toolbar), item, 0)" and change the "0" to a "2".  So change the original line from:

```
	gtk_toolbar_insert (GTK_TOOLBAR (self->priv->toolbar), item, 0);
```

To:

```
	gtk_toolbar_insert (GTK_TOOLBAR (self->priv->toolbar), item, 2);
```

When you're done, click save and close Gedit.

Back in Terminal, run the following:

```
./configure --prefix=/usr

make

sudo killall nautilus

sudo make install

nautilus &
```

At this point, I would actually recommend logging out and back in or just restarting.

To undo the changes and revert back to stock Nautilus, you can either change the "2" back to a "0", re-make and re-install, or you can simply run:

```
sudo apt-get --reinstall install nautilus
```

You might want to remove the required dev packages also, but be careful not to remove something that may have already been there and is needed.

---

### Post by gennatolls on 2011-11-30
Nice job! and thanks for sharing

---

### Post by nyteryder79 on 2011-11-30
> **gennatolls said:**
> Nice job! and thanks for sharing
No problem.  Hope it helps!  It drove me nuts enough to figure this out.  It's just funny that all you have to change is one single character in code.  It makes me wonder why this isn't something that could be changed with dconf editor or similar.

This could easily be made into a script that does it all for you, but I have no idea how to parse the C file, replace the one character, and re-write the file.  If anyone does, please let me know and I'll try to make a simple script to do this all in one step.

---

### Post by giowck on 2011-12-03
> **nyteryder79 said:**
> No problem.  Hope it helps!  It drove me nuts enough to figure this out.  It's just funny that all you have to change is one single character in code.  It makes me wonder why this isn't something that could be changed with dconf editor or similar.

This could easily be made into a script that does it all for you, but I have no idea how to parse the C file, replace the one character, and re-write the file.  If anyone does, please let me know and I'll try to make a simple script to do this all in one step.

use the **patch** utility

---

### Post by WindPower on 2011-12-03
> **nyteryder79 said:**
> No problem.  Hope it helps!  It drove me nuts enough to figure this out.  It's just funny that all you have to change is one single character in code.  It makes me wonder why this isn't something that could be changed with dconf editor or similar.

This could easily be made into a script that does it all for you, but I have no idea how to parse the C file, replace the one character, and re-write the file.  If anyone does, please let me know and I'll try to make a simple script to do this all in one step.

What you're looking for is [_creating a diff file_](http://jungels.net/articles/diff-patch-ten-minutes.html) with the [_diff_](http://manpages.ubuntu.com/manpages/precise/en/man1/diff.1posix.html) tool and apply it in a script with the [_patch_](http://manpages.ubuntu.com/manpages/precise/en/man1/patch.1.html) tool.

Edit: And giowck ninja'd me. But I have links, so I'll leave this post here.

---

### Post by chenxiaolong on 2011-12-03
Nice! But instead of running:

```
./configure --prefix=/usr
make
sudo make install
```

you can run:

```
dpkg-buildpackage -us -uc -b
```

which will compile and generate a proper DEB file in the parent directory.

EDIT: Also nautilus has a parameter '-q' that restarts itself:

```
nautilus -q
```

---

### Post by gennatolls on 2011-12-03
Cool you made omgubuntu s blog. Look forward to more "hacks" like this.

---

### Post by kylea on 2011-12-04
Nice - thanks - much better

---

### Post by iammuneeb on 2011-12-05
I have created a PPA for this if someone feels it's too much, just to get the navigation buttons on left side.

It's for Oneiric (Ubuntu 11.10) only!
```

$ sudo add-apt-repository ppa:iammuneeb/nautilus-leftnav
$ sudo apt-get update
$ sudo apt-get install nautilus
$ nautilus -q

```

To revert back:
```

$ sudo apt-get install ppa-purge
$ sudo ppa-purge ppa:iammuneeb/nautilus-leftnav
$ sudo apt-get update
$ sudo apt-get --reinstall install nautilus
$ nautilus -q

```

---

### Post by nyteryder79 on 2011-12-05
> **iammuneeb said:**
> I have created a PPA for this if someone feels it's too much, just to get the navigation buttons on left side.

It's for Oneiric (Ubuntu 11.10) only!
```

$ sudo add-apt-repository ppa:iammuneeb/nautilus-leftnav
$ sudo apt-get update
$ sudo apt-get install nautilus
$ nautilus -q

```

Very nice!  Thank you!  Will this work for both 32bit and 64bit?

---

### Post by iammuneeb on 2011-12-05
> **nyteryder79 said:**
> Very nice!  Thank you!  Will this work for both 32bit and 64bit?

Yes! The PPA has it for both 32bit and 64bit.

---

### Post by dasnk on 2011-12-09
I hope they make this optional for future versions 


Thanks for this patch.

---

### Post by jessy1 on 2011-12-16
Does this works in Linux Mint 12 too?
I hope so!

---

### Post by axiom613 on 2011-12-16
> **jessy1 said:**
> Does this works in Linux Mint 12 too?
I hope so!
Haha, exactly what i was wondering.  It should, since Lisa is based on Oneiric. I'm trying it out now =)

---

### Post by zoffix on 2012-04-01
Thanks. The fix worked, but I was still missing the "Up" arrow, and I didn't like the way the side panel went way too high up.

After searching around and combining several suggestions, I did this:

```
sudo apt-get install pcmanfm exo-utils;
exo-preferred-applications
```

Then I went to "Utilities" tab and changed the file manager to pcmanfm. So far, it seems to look and work a lot like the old Nautilus.

Cheers,
ZZ

---

