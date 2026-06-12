---
title: "GTK2 install path?"
date: 2006-06-08
forum: General Help
---

### Post by strider1551 on 2006-06-08
Hello all,

I'm trying to install something called [im-classical greek]("http://sourceforge.net/project/showfiles.php?group_id=78185").  I'm a classical language major, and it's incredibly helpful to be able to write ancient greek, accents and everything.  im-classicalgreek makes this really easy in GTK2 application.

I downloaded the files and got ready to install.  The README warned that > However, by default im-classicalgreek installs to /usr/local.  If your GTK2 installation is under /usr, as it is for many systems, be sure to specify it:
$ ./configure --prefix=/usr

I went with the default hoping it would work using:
```
sudo auto-apt run ./configure
```

Of course, it hits an error, the last two lines being:
> checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.2.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

I tried a few different locations with the --prefix option to no avail.  Anyone know the right prefix (or has noticed some other mistake on my part)?

---

### Post by givré on 2006-06-08
Install the -dev package of gtk2 (search in synaptic)
pkg-config will always search for .pc file and those files are in the -dev packages.

---

### Post by strider1551 on 2006-06-08
Many thanks.  I now have im-classicalgreek installed (as far as I can tell), but I'm tripping up on the last part of the installation.
> Once the package has been installed, update GTK2's knowledge
of input methods by entering as root:

gtk-query-immodules > /etc/gtk-2.0/gtk.immodules

The first problem was that "gtk-query-immodules" doesn't exist.  I did some searching and changed it to "gtk-query-immodules-2.0", which does exist

Here's my current problem:
```
$ sudo gtk-query-immodules-2.0 > sudo /etc/gtk-2.0/gtk.immodules
```
and the result:
> Cannot load module /etc/gtk-2.0/gtk.immodules: /etc/gtk-2.0/gtk.immodules: invalid ELF header
/etc/gtk-2.0/gtk.immodules does not export GTK+ IM module API: /etc/gtk-2.0/gtk.immodules: invalid ELF header

---

### Post by givré on 2006-06-08
[QUOTE=strider1551]Many thanks.  I now have im-classicalgreek installed (as far as I can tell), but I'm tripping up on the last part of the installation.


The first problem was that "gtk-query-immodules" doesn't exist.  I did some searching and changed it to "gtk-query-immodules-2.0", which does exist

Here's my current problem:
```
$ sudo gtk-query-immodules-2.0 > sudo /etc/gtk-2.0/gtk.immodules
```
and the result:[/QUOTE]
gtk-query-immodules-2.0 will "collects information about loadable input method modules for GTK+ and writes it to stdout" (see man for more man gtk-query-immodules-2.0 for more information)
Stdout, means that you will have the information directly in the terminal (standart output)

You have to update /etc/gtk-2.0/gtk.immodules which is the configuration file use by gtk about the input methode, so you have to write the result of  gtk-query-immodules-2.0 into this file.
In unix to do that kind of thing, you have a great tool : >
it will redirect the output to the file specify in right(to know more, there is a lot of great webpage about unix command)
it's why you have to execute EXACTLY
```
sudo gtk-query-immodules-2.0 [COLOR="Red"]>[/COLOR] /etc/gtk-2.0/gtk.immodules
```

Say me if it is ok

---

### Post by strider1551 on 2006-06-08
I follow what you're saying.  I tried "sudo gtk-query-immodules-2.0 > /etc/gtk-2.0/gtk.immodules", but it returns
> bash: /etc/gtk-2.0/gtk.immodules: Permission denied
hence, why I had tried putting "sudo" after the open carrot.

Solved: I thought about it for a while, and figured out what to do.  I went to a tty terminal and actually logged in as root.  The command worked perfectly.

Unfortunately, im-classicalgreek doesn't work.  In a moment I'm going to restart gnome to see if that fixes it.  I don't think it will, though.  I looked at the output of gtk-query-immodules-2.0 and it doesn't list an entry for im-classicalgreek.  I'm thinking that the issue is with that --prefix command, but I'll see what the reset does.

[Edit] No luck.  I really think it's that prefix.  I tried --prefix=/usr/lib, but that install things to /usr/lib/lib/gtk-2.0/2.2.0 . Obviously, I need to change the prefix to /usr, but I wonder about the 2.2.0 - the folder in my gtk-2.0 is 2.4.0

---

### Post by givré on 2006-06-08
[QUOTE=strider1551]Obviously, I need to change the prefix to /usr, but I wonder about the 2.2.0 - the folder in my gtk-2.0 is 2.4.0[/QUOTE]
Try it, you will so if it is seen by gtk-query-immodules or note

---

### Post by strider1551 on 2006-06-08
With "--prefix=/usr", it did indeed install everything to "/usr/lib/gtk-2.0/2.2.0/immodules".  And, of course, it doesn't get added to "gtk-query-immodules".  I took the risky step of copying the files to 2.4.0, and so far everything seems to work fine.  Of course, one day I will be doing something important and my computer will crash and the hard drive will burst into flames.

I think from here I'm going to contact the creator of im-classicalgreek to see what he recommends.  Thanks a lot for your help.  By the way, supposing I resolve this last issue, what would be the best way to document the install for others?

---

### Post by andrew.46 on 2007-02-08
Hi,

 Read your post with great interest as I am also a Greek Undergraduate major trying to write Greek with Ubuntu:

> **strider1551 said:**
> I think from here I'm going to contact the creator of im-classicalgreek to see what he recommends.  Thanks a lot for your help.  By the way, supposing I resolve this last issue, what would be the best way to document the install for others?

 If you managed to resolve your issues I would love to know how you are going?

                               Andrew

---

### Post by strider1551 on 2007-02-09
I did send an email to the developer at his sourceforge address, but I never received a reply.  I assumed he abandoned the project, but he might have changed emails and forgotten to update his sourceforge account.

im-classical greek does indeed work.  The part that worries me is that I had to manually copy its files from /usr/lib/gtk-2.0/2.2.0/ into /usr/lib/gtk-2.0/2.4.0/.  I never encountered a problem, but there still might be a small change in 2.4 that could cause some miscellaneous error.

When I have some time this weekend, I'll post the steps to install it.  I have considerably more experience with linux now, so perhaps I'll notice something I didn't before.

As a side note, I've also wondered if it would be possible to set up an actual keyboard and be able to use classical greek in applications that are not gtk based.  I found [this]("http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11"), which might be the answer to learning what to do - I just wish I had the time!

---

### Post by andrew.46 on 2007-02-09
Hi,

 Well I installed the gtk -dev files and the installation went smoothly except I cannot see the Ancient Greek menu in AbiWord.  I could not, same problem that you faced, make the following command work, which I gather is the final step:


```
gtk-query-immodules > /etc/gtk-2.0/gtk.immodules
```

 I could not quite folow what you meant with manually moving files. Hmmm.... look forward to you posting full details. Which word processing software were / are you using for your Greek?

                     Andrew

---

### Post by strider1551 on 2007-02-11
> 
I could not, same problem that you faced, make the following command work... gtk-query-immodules > /etc/gtk-2.0/gtk.immodules


There are two problems with this command.  The first is that it is wrong.  The README does give this command, but it should be "gtk-query-immodules-2.0 > /etc/gtk-2.0/gtk.immodules" (note the addition of 2.0 to the first half.  Unfortunately, I do not remember how I figured that out.
The second is that the command needs to be executed as the root user, and for some reason sudo won't work.  Become the root user by using "su" instead, and the command will work.  At the time, I was shamefully unaware of su, and had to actually log in as root at a tty terminal (ctrl-alt-F1 goes to tty1, ctrl-alt-F7 goes back to gnome).  If your typical password doesn't work, it's because in edgy the root account is set with a random password (I believe).  Enter "sudo passwd root"  to set whatever password you want.

> 
I could not quite folow what you meant with manually moving files.


Once the above command is executed, files will be placed in /usr/lib/gtk-2.0/2.2.0/immodules.  However, the gtk version should be higher than 2.2.0, and so they need to be copied into the folder for whatever version is being installed.  At present, it will likely be /usr/lib/gtk-2.0/2.10.0/immodules.

---

### Post by strider1551 on 2007-02-11
Now for the bad news.  I reinstalled Ubuntu a while ago, and have normally been working with Arch Linux.  When I tried to install im-classicalgreek last night, it simply didn't work.  I had all the files in place, but the option for greek never came up on the input methods list.  Following will be the steps I used to install.  I encourage you to try it yourself and confirm/deny my results.  I also recommend rereading all instructions; I did this rather late at night and may have forgotten something.

I assume you extracted the source and moved into the proper directory
```

$ sudo ./configure --prefix=/usr
$ sudo make
$ sudo make install
$ su
# gtk-query-immodules-2.0 > /etc/gtk-2.0/gtk.immodules
# mv /usr/lib/gtk-2.0/2.2.0/immodules/im-class* /usr/lib/gtk-2.0/2.10.0/immodules

```

Sometime this week I plan to try installing it in Arch, just for the heck of it.  Ultimately, though, im-classicalgreek is a temporary solution.  Devolpment on it stopped about three years ago and it is listed as pre-alpha.  Sooner or later a version of gtk or its replacement will break it.  Unless a developer steps up and takes over the project, it is not a long term solution.  Unforutnately, the only programming language I know is python, so I am ill equipped to fix whatever might have happened.

If im-classicalgreek is indeed broken, I will certainly be looking into whether making a custom X11 keyboard map would work.  I may not really need greek composition *now*, but I will soon.

---

