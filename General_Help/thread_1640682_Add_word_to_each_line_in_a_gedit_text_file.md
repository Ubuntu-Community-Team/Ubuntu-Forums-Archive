---
title: "Add word to each line in a gedit text file?"
date: 2010-12-08
forum: General Help
---

### Post by webcabbie on 2010-12-08
Using the latest version of Ubuntu desktop on an emachine t5062 if it matters. 

I have a text file of keywords that is one-three words line after line for like 5000 lines. 

How would I go about adding a word to each line. Aside from typing it in or copying and pasting. 

If it can`t be done with Gedit I am all for using another program. Willing to listen to any and all suggestions.

---

### Post by anglican on 2010-12-08
> **webcabbie said:**
> Using the latest version of Ubuntu desktop on an emachine t5062 if it matters. 

I have a text file of keywords that is one-three words line after line for like 5000 lines. 

How would I go about adding a word to each line. Aside from typing it in or copying and pasting. 

If it can`t be done with Gedit I am all for using another program. Willing to listen to any and all suggestions.I'd use "vi", one of the command line editors, to do something like that. Open a terminal then:
```
vi filename_to_edit[ENTER]
```once the file is open type:
```
:%s/$/text/g[ENTER]
```where "text" is the text you want to go at the end of every line, then:
```
:wq[ENTER]
```and that's it, job done. To do the same at the start of every line you would use:
```
:%s/^/text/g[ENTER]
```H

---

### Post by Rizwanm on 2010-12-08
Hi every one now i am using ubuntu software its cool yar i like this service and thanks for u r suggestions also ..... :o

---

### Post by webcabbie on 2010-12-08
> **anglican said:**
> I'd use "vi", one of the command line editors, to do something like that. Open a terminal then:
```
vi filename_to_edit[ENTER]
```once the file is open type:
```
:%s/$/text/g[ENTER]
```where "text" is the text you want to go at the end of every line, then:
```
:wq[ENTER]
```and that's it, job done. To do the same at the start of every line you would use:
```
:%s/^/text/g[ENTER]
```H

There is no other way with using a desktop application you can think of? 

I have been using Ubuntu about 2 years now and I never open the terminal or play with that stuff... I is scared of it.

---

### Post by anglican on 2010-12-08
> **webcabbie said:**
> There is no other way with using a desktop application you can think of? 

I have been using Ubuntu about 2 years now and I never open the terminal or play with that stuff... I is scared of it.Sure, install the graphical version of vi which is in a package called vim-gtk. Then from your menus choose Accessories->Gvim and open your file then type :%s/$/text/g save your file and it's done. There may well be another way other than a variation of vi - but since vi (and gvim) do everything I need from an editor I've never needed to investigate alternatives.;) You shouldn't be frightened of opening terminals and typing commands in them, it's one of the joys of linux IMO.

H

---

### Post by SeijiSensei on 2010-12-08
> **webcabbie said:**
> There is no other way with using a desktop application you can think of? 

I have been using Ubuntu about 2 years now and I never open the terminal or play with that stuff... I is scared of it.

Now's a good time to become less scared.  Go ahead, open a terminal and try typing this at the dollar-sign prompt:

```

cd /path/to/directory/where/oldfile/is/stored
sed 's/$/ wordtoadd/g' < oldfile > newfile

```

sed is a simple line editor.  Here I'm using the "**s**ubstitute" command.  The dollar-sign represents the end of the line using something called a "[regular expression]("http://en.wikipedia.org/wiki/Regular_expressions")." Sed thus replaces the end of each line with a space followed by "wordtoadd".  The < means read from the next item, oldfile in this case, and the > means write to newfile.

So if oldfile is in your home directory, you'd use "cd /home/webcabbie" then run the sed command.  The newfile will be written in that directory as well.

---

### Post by Lordluen on 2010-12-08
Please note that while things like vi and sed are tough to learn and understand, they are extremely powerful. I exclusively use vi for all my programming needs. You can install highlighting packages to make it easier to read different programming languages, etc. So if you ever need to do a lot of programming on a linux machine, learning something like vi would be a very powerful tool! Even if you don't program, if you need an even spaced text editor, these programs are still super useful, for the exact reasons you saw throughout this thread.

Also don't be afraid of the terminal! It will open a world of possibilities! If you break something, someone in this forum will always be there to help! You only learn by tinkering (and inevitably breaking and fixing).

---

### Post by dcstar on 2010-12-08
> **webcabbie said:**
> There is no other way with using a desktop application you can think of? 

I have been using Ubuntu about 2 years now and I never open the terminal or play with that stuff... I is scared of it.

This Gedit plugin may have something that could work:

[https://code.google.com/p/advanced-find/](https://code.google.com/p/advanced-find/)

Download, extract and then install it with:
```
sudo ./install.sh
```
and then enable the Plugin in Gedit, it will then be available in the Search menu and you can then use Regular Expressions in the Search and Replace strings (as outlined in the other posts).

---

### Post by SeijiSensei on 2010-12-11
> **Lordluen said:**
> I exclusively use vi for all my programming needs.

The only editor I'd recommend to someone new to the terminal like webcabbie is **nano**.  It has helpful menus at the bottom of the screen.  It's also installed by default in Ubuntu and some other distributions as well.  Personally I use jed, a stripped down version of emacs, but that's only because I needed to learn emacs at one point in my life and didn't want to learn another editor.  vi has always seemed especially obtuse to me.  Since I'm already quite content using jed, and have been for fifteen years now, I doubt I'll ever change.

I'd rather use jed than most GUI editors, too.  I run KDE and occasionally use Kate.  It's a decent editor with syntax highlighting.  But the GUI itself just seems like an unnecessary layer between me and the file I want to edit.  Since I've done nearly all my work via SSH connections, I'm just a text kinda guy.

---

