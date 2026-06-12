---
title: "creating a short-cut to run an app"
date: 2012-08-14
forum: General Help
---

### Post by p3aul on 2012-08-14
I use a component of the program Calibre quite a lot. This component is called ebook-convert that I use on the commandline. I would like to shorten this work to something like "ebk" to make for less typing. I tried renaming the link I find in /usr/bin/ and even as root it won't let me. How do I do this?
Thanks,
Paul

---

### Post by GWBouge on 2012-08-14
You can create an alias in your ~/.bashrc or ~/.bash_aliases file.  Just open it up in gedit or whatever you prefer, scroll down a bit and you should see some aliases already set up.  Just add one in there like:

```
alias ebk='ebook-convert'
```

Note, you have to re-open the terminal before you can use the alias.

---

### Post by TheFu on 2012-08-14
> **p3aul said:**
> I use a component of the program Calibre quite a lot. This component is called ebook-convert that I use on the commandline. I would like to shorten this work to something like "ebk" to make for less typing. I tried renaming the link I find in /usr/bin/ and even as root it won't let me. How do I do this?


There are many, many different ways to solve this issue. I'll suggest 2 below.

Renaming files installed by a package manager is a terrible idea, but there is an alternative, use a softlink and put that into someplace in your PATH.

A common place to put personal programs, scripts and just more convenient names is in your $HOME/bin/ directory.  In fact, putting this first in your PATH will mean that you can override programs of the same names for yourself, but not break system tools.

Add this to your ~/.bashrc file:
```
export PATH=$HOME/bin:$PATH
```Now create a softlink for that program inside your ~/bin/ folder - name it anything you like.
```
mkdir ~/bin
cd ~/bin
ln -s /usr/bin/ebook-convert ebk 
```Just source your ~/.bashrc for the PATH changes to take effect.

Ok, that's the hard way, but it will work and there are lots of times when a more complex script or even a full program that you wrote will be desired. Put that into your ~/bin/.

You can also **use an "alias". This is much easier. **Edit your ~/.bashrc file and add:
alias ekb='/usr/bin/ebook-convert'
Now just source your ~/.bashrc to make it active in any window.  It might be easier to logout and back in to make every window _know about _ the new aliases.

Aliases are fantastic. There is an entire subculture of people making really great aliases.  Here's one of my favorites:
```
alias psg='ps -eaf | grep $*'
```

---

### Post by p3aul on 2012-08-14
Thank you all! I'm saving this excellent advise. I used the first suggestion , it worked fine
Paul

---

### Post by p3aul on 2012-08-14
TheFu: Thank you for your suggestions. I am confused though. How do you "source" the .bashrc file I hope you meant save, utherwise I havn't a clue!
thanks

---

### Post by slooksterpsv on 2012-08-14
You can open the .bashrc file with gedit or another text editing program (not LibreOffice though).

e.g.
gedit ~/.bashrc

---

### Post by efflandt on 2012-08-15
Besides **gedit** in X, a simple terminal text editor is **nano**.

If you create a **bin** directory in your home directory (mkdir ~/bin) it that should automatically be in your $PATH once you log out of X and back in.  That would be an ideal place for personal scripts or binaries.

To see what is in your path:

```
$ **echo $PATH**
/home/efflandt/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```If you create an alias in .bashrc, all you have to do is close any existing terminal and open a new terminal for it to take effect.

---

### Post by TheFu on 2012-08-15
> **p3aul said:**
> TheFu: Thank you for your suggestions. I am confused though. How do you "source" the .bashrc file I hope you meant save, utherwise I havn't a clue!
thanks

No, you "source it". There are 2 ways:
```
source ~/.bashrc
```or 
```
.  ~/.bashrc
```Sourcing runs the commands in the file, but doesn't start a new sub-shell. Very handy.  It lets any aliases or exported environment variables be applied to the current shell.

Starting a new terminal will do the same thing, but any other terminal sessions will not get the new settings.  Logging off and back on will also read all the new settings from the ~/.bashrc file.  Which is easier is up to you.  As you gain more experience, you'll probably make the change and use the  ```
.  ~/.bashrc
``` version. Trust me.

---

