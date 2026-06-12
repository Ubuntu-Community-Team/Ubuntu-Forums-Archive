---
title: "Need Help Installing Scizzor Plugin"
date: 2006-04-12
forum: General Help
---

### Post by OffHand on 2006-04-12
Hi 
I need help installing Scizzor. Scizzor is a Beep Media Player and XMMS effect plugin for pitch\speed control. [http://scizzor.sourceforge.net/](http://scizzor.sourceforge.net/)
I have downloaded the plugin and extracted it with:
```
tar -xvzf scizzor-1.3.3.tar.gz

```
I don't know how to install it though. Is there anyone who can help me?
Thanks in advance,
Subsonic

---

### Post by OffHand on 2006-04-12
admin@linux:~$ tar xvfz scizzor-1.3.3.tar.gz
scizzor/
scizzor/Makefile
scizzor/scizzor.c
scizzor/scizzor_snd.c
scizzor/scizzor_snd.h
scizzor/scizzor.h
scizzor/scizzor_icon.xpm
scizzor/install.pl
scizzor/COPYING
admin@linux:~$ cd ~/scizzor
admin@linux:~/scizzor$ ./configure
bash: ./configure: No such file or directory
admin@linux:~/scizzor$


Anyone?

---

### Post by OffHand on 2006-04-13
I really would like to install this plugin so help is greatly appreciated  :confused:

---

### Post by vicarious on 2007-02-15
This is really old but I needed this so I'll post how I got it working. I only installed it for beep-media-player but you should be able to figure out how to get it working for xmms, also. (Who uses xmms anymore?!)

I also have a little rant, too, so bear with me.

> **OffHand said:**
> admin@linux:~$ tar xvfz scizzor-1.3.3.tar.gz
scizzor/
scizzor/Makefile
scizzor/scizzor.c
scizzor/scizzor_snd.c
scizzor/scizzor_snd.h
scizzor/scizzor.h
scizzor/scizzor_icon.xpm
scizzor/install.pl
scizzor/COPYING
admin@linux:~$ cd ~/scizzor
admin@linux:~/scizzor$ ./configure
bash: ./configure: No such file or directory
admin@linux:~/scizzor$

Ok. I know a lot of new linux users are used to copying and pasting commands but you need to learn what something does before you type it into a terminal (ask someone, google it, manpages,  whatever). The "./" characters are used to run an executable that is in the current directory since "." is not in your path (`echo $PATH` to see your current path). As you can tell from the 'ls' output, there is no file named 'configure' which is why it doesn't work.

The 'configure' script is 99% of the time from the GNU Autoconf package. This is not usually used for small projects (like a audio plugin) since it is overkill and it is sometimes not used for larger packages either because it is a huge pain in the ***.

There is a Makefile there, however. Usually you can just run 'make' and it will build the package or tell you what to do. When you run 'make' here it tells you to run 'make bmp' (among other choices) to build the bmp plugin. If you try this it will spit out a bazillion errors.

Next, I looked inside the Makefile to see what the problem might be. Luckily, this was a very simple Makefile and I was able to see the problem right away. Some of the C compiler flags used are pulled by the beep-config program, which I don't have. I check the repositories real quick and did not find it there either, though I didn't really expect to.

So, I searched google. Sure enough, the first entry was the beep-config script I needed.

Here we go:

Get the beep-config script and the scizzor plugin:
```
wget http://www.zugaina.org/gentoo/portage/media-sound/beep-media-player-cvs/files/beep-config
wget http://prdownloads.sourceforge.net/scizzor/scizzor-1.3.3.tar.gz?download
```

Make the beep-config script executable:
```
chmod +x beep-config
```
And then move it to a directory in your path or modify the Makefile to point to the file directly.

Extract the files:
```
tar xzf scizzor-1.3.3.tar.gz
cd scizzor
```

Then build the beep-media-player plugin:
```
make bmp
```

And move it to your bmp plugins directory:
```
mv *.so ~/.bmp/Plugins/
```

Restart beep-media-player and it should be in your plugins list. The plugin works fine for me but the GTK+ buttons are drawn halfway off the dialog. :?

---

