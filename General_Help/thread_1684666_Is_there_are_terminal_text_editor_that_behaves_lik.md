---
title: "Is there are terminal text editor that behaves like gedit?"
date: 2011-02-09
forum: General Help
---

### Post by Cloudform on 2011-02-09
I have been spending the last hour and a half looking for terminal text editors with modern keybindings (NOT vi or nano).  All I want is something that is normal (i.e. Shift + keypad direction will highlight, Ctrl+X cuts, Ctrl+V pastes, etc.)  Something that behaves like gedit in the terminal.  

Something VERY close to this was fte, but fte behaves very strangely in other ways and I can't figure out their configuration file (I don't want to spend 5 hours configuring something to behave like a standard text editor!)

If anyone knows of anything, thanks a ton.

(or is there a way to actually open gedit inside of a terminal...?)

---

### Post by edhplus2 on 2011-02-09
You can always open a terminal and type *gedit* to start the program. Or type *gedit filename.txt* to edit a specific file. Or just *gedit fi* <tab> and bash will complete the file name or give you a list of all that match the few starting letters that you supplied. You then tab through the choices as they change on the command line until you get the one you want.

When you exit gedit you will be back at the command line in the terminal.

(You can run a lot of applications from the command line. Or from <alt-F2>. )

I'm not sure this answered the question, but this is what I think you are asking.

---

### Post by Cloudform on 2011-02-09
> **edhplus2 said:**
> You can always open a terminal and type *gedit* to start the program. Or type *gedit filename.txt* to edit a specific file. Or just *gedit fi* <tab> and bash will complete the file name or give you a list of all that match the few starting letters that you supplied. You then tab through the choices as they change on the command line until you get the one you want.

When you exit gedit you will be back at the command line in the terminal.

(You can run a lot of applications from the command line. Or from <alt-F2>. )

I'm not sure this answered the question, but this is what I think you are asking.

Sorry, I guess I didn't say it clear enough.  I want something that opens IN the terminal, just like nano and vi does (but I want it's hotkeys to behave like gedit).  I know that gedit filename will open filename :D

Thanks for the quick response though!

---

### Post by randiroo76073 on 2011-02-09
Open a Terminal:
```
gksu gedit
```

---

### Post by davidmohammed on 2011-02-09
vim and emacs come to mind

---

### Post by Cloudform on 2011-02-09
> **randiroo76073 said:**
> Open a Terminal:
```
gksu gedit
```

That opens up the gedit gui, which is not what I want.  I want a terminal text editor that behaves like gedit... (there must be something about this language that is VERY confusing)

I don't want a separate window to open up.  fte editor ALMOST does this.  In fact, I can get it to do it when I play around with the configurations--but then there is no way to save the configurations from inside the terminal!  When I try to create and compile a configuration file, it seems to change other settings.  I am at a loss.

---

### Post by Cloudform on 2011-02-09
> **davidmohammed said:**
> vim and emacs come to mind

from my understanding joe is an emacs terminal emulator and you cannot use shift to highlight, ctrl+c to copy, etc.

And vim is practically the complete opposite of what I am asking (other than that it stays in the terminal).  It comes with its own plethora of hotkeys that I would have to learn to use it.  I want something that works just like gedit -- something with no learning curve for someone who has grown up working with microsoft/open office.

---

### Post by davidmohammed on 2011-02-09
yes you can - as per [here]("http://www.med.nyu.edu/rcr/rcr/course/unix8.html").

you can also redefine the keyboard strokes to do what you want - simple google search revealed [this]("http://xahlee.org/emacs/reclaim_keybindings.html").

however - no terminal editor will behave just like gedit - just use gedit!

You'll probably need to put in the effort to customise the editor to your needs.

---

### Post by Cloudform on 2011-02-09
I just installed it.  

to get it to run in the terminal I typed:

emacs -nw

I guess to get it to behave like gedit/notepad/every other gui text editor in existance one has to figure out how to configure the damned thing.  cntrl+c does not copy, cntrl+x does not paste.  You can use shift to highlight stuff... but only downwards.

If only gedit had a -nw option (it doesn't seem to)

I'm beginning to think that there is no such thing as a normal (modern keymapped) terminal text editor.

---

### Post by Cloudform on 2011-02-09
I guess I should say why I want this...

I got a background embedded terminal working on this machine (which means a terminal is embedded in my background and carries across workspaces)  This is really neat and I love it, and it would be great to have a text editor I can use in it as well.  But it doesn't seem like they don't exist (which is kind of silly in my opinion)

Also, if my desktop crashes (because I screw something up) it would be nice to be able to do some stuff in a standard terminal text editor.

Oh well, thanks for all the help.

---

### Post by HermanAB on 2011-02-09
Try 'joe'.

It comes with various preconfigured bindings.  The default works like Wordstar, but it can be configured easily.

Name
       joe - Joe's Own Editor

Syntax
       joe [global-options] [ [local-options] filename ]...

       jstar [global-options] [ [local-options] filename ]...

       jmacs [global-options] [ [local-options] filename ]...

       rjoe [global-options] [ [local-options] filename ]...

       jpico [global-options] [ [local-options] filename ]...

Description
       JOE  is a powerful ASCII-text screen editor.  It has a "mode-less" user
       interface which is similar to many user-friendly PC editors.  Users  of
       Micro-Pro's  WordStar or Borland's "Turbo" languages will feel at home.
       JOE is a full featured UNIX screen-editor though, and has many features
       for editing programs and text.

---

### Post by nothingspecial on 2011-02-09
Yep , joe

It has one of the most easily understandable man pages of any app. (with the exception of feh which has nothing to do with your question).

Try joe

---

### Post by zabsv on 2011-02-09
I think your best option is to learn how to use emacs (or zile). I'm  afraid that's the closest you will get to normal in a terminal.
It's a pain to get started with but after a while it's at least usable, and after a few years you might even start to like it...
Here's a page with some basic emacs commands to get you started, [http://www.engr.uvic.ca/~dastone/emacs-keys.html]("http://www.engr.uvic.ca/%7Edastone/emacs-keys.html")

---

### Post by Cloudform on 2011-02-09
alright, joe seems pretty good... maybe I will configure it when I have 5 hours to kill.

On that note, does anyone have a config file that configure it to be a more "standard" modern text editor?  :D  Maybe there is a forum I can request this on...

---

### Post by Cloudform on 2011-02-09
> **zabsv said:**
> I think your best option is to learn how to use emacs (or zile). I'm  afraid that's the closest you will get to normal in a terminal.
It's a pain to get started with but after a while it's at least usable, and after a few years you might even start to like it...
Here's a page with some basic emacs commands to get you started, [http://www.engr.uvic.ca/~dastone/emacs-keys.html]("http://www.engr.uvic.ca/%7Edastone/emacs-keys.html")

That is really unbelievable to me, but it seems to be true.  The other option would be to write a terminal clone of a simplified version of gedit.  (I have no idea how difficult this would be)

---

### Post by Cloudform on 2011-02-09
doublepost

---

