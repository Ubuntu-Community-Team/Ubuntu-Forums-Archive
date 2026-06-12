---
title: "Command Line Only Environment"
date: 2009-07-27
forum: General Help
---

### Post by CrusaderAD on 2009-07-27
Is it possible to do a command line only mode with no GUI and still do things like open pictures, play music, use instant messengers and whatnot? I take it there wouldn't really be a way to browse the web since you need a gui browser, don't you?

---

### Post by philcamlin on 2009-07-27
ctrl alt f2 i think is what you want

---

### Post by Stunts on 2009-07-27
All that you say can be done in a pure cli environment.
you can try running "links" for web browsing in a terminal, for instance.
You can even use links2, and if you have framebuffer activated, you can even browse the web with pictures.
Likewise, there is cli software to look at pictures (Can't remember then name right now), play music (MPD), instant messaging (finch), etc...

---

### Post by Stunts on 2009-07-27
It's Imagemagick for viewing images from the cli.

---

### Post by jonobr on 2009-07-27
using the cntrol alt suggestion will bring you to the command line as pointed out.

If you wanted to browse websites, your limited to display only in text only mode , so you could use a browser which is text based like w3m.

so when you hit say ctril-alt-f1 
login and type w3m google.

Im sure you willb e very disappointed with the result.

AS for the pics and music, Im not so sure

---

### Post by CrusaderAD on 2009-07-27
Cool, thanks for the replies. I'll do some more research. If anyone knows of any programs that runs this kinda stuff from the command line, can you post them please? Thanks!

---

### Post by sisco311 on 2009-07-27
[thread=1215406]possible to do all your regular computing in terminal ?[/thread]

---

### Post by Stunts on 2009-07-27
I think finch is bundled with pidgin.
As for the MPD just install mplayer-daemon.
For links2 just install links2 - not sure how to activate the framebuffer kernel module, but I'm sure you can find that info on google.
Imagemagick is also in synaptic. It runs a "display command, just type ```
 user@computer$ display image.png
or
user@computer$ display ~/Pictures/*

```

Have fun in the CLI!

---

### Post by CrusaderAD on 2009-07-27
> **Stunts said:**
> Have fun in the CLI!

Will do, thanks for all the great help everyone!

---

### Post by hrod beraht on 2009-07-27
When you say 'command line only', do you mean without X? If so, then check out [dvtm](http://brain-dump.org/projects/dvtm/) (dynamic virtual terminal manager). It's like a tiling window manager for the console.

However, if you mean that you just want to have a window manager without all of the eye-candy bloat but still using X, then sure, that's easy. I do it every day, using programs that I run in an X-term.

The first step is to find a non-gui type of X window manager. My favorites are Evilwm (floating windows), or Ratpoison (tiling windows). Both, by default have no icons, no window decorations, no panels, no file managers or other built-in apps, etc. Essentially they make a window in which you can run your x-term, and that's about it.

So once you have your X-term up and running, there are lots of non-gui programs you can run. For example, qiv and feh for looking at pictures, moc and mplayer (command line) for listening to music and watching movies, bash itself as a great file manager, and even programs like finch for instant messaging, which is a text version of Pidgin.

But be careful with the minimal window managers if you're coming from Gnome or KDE. Their speed is so addictive you may never be able to go back to a big, bloated gui desktop environment :D

Bob

---

### Post by CrusaderAD on 2009-07-28
> **hrod beraht said:**
> But be careful with the minimal window managers if you're coming from Gnome or KDE. Their speed is so addictive you may never be able to go back to a big, bloated gui desktop environment :D

Bob

That's cool! Are you strictly limited to the keyboard with this x-term or does it have mouse capabilities? Good stuff, thanks for the info.

---

### Post by hessiess on 2009-07-28
> **raptormanad said:**
> That's cool! Are you strictly limited to the keyboard with this x-term or does it have mouse capabilities? Good stuff, thanks for the info.

As long as you are running X, you can use the mouse if you want to, however with DWM/Xmonad, Vim, Vimperator, Cmus, LaTeX and your other faverate CLI apps, you will start to notice that mouse driven computing is extremely inefecent.

---

### Post by Anzan on 2009-07-28
Try out INX:

[http://inx.maincontent.net/]("http://inx.maincontent.net/")

> Some Info...
Briefly, INX is a Live CD currently based on Ubuntu 8.04
It has no GNOME, KDE, XFCE... or any other desktop or window manager for that matter.

It is console-only - the idea is to give you a tool to learn more about the command line, while having some fun. You might be surprised how much can be done with such a system. 

---

### Post by CrusaderAD on 2009-07-28
I don't suppose anyone knows of a pen drive version? Something like [http://www.pendrivelinux.com]("http://www.pendrivelinux.com") but command line only?

---

### Post by Slim Odds on 2009-07-28
Just to be pedantic, you can't "view" pictures without a GUI (unless you really like ASCII art that much).

There are ways to "surf the web" in text only mode (lynx), but you won't get the "pictures" part (obviously).

Anything that actually requires images needs a GUI.

---

### Post by marshag63 on 2009-07-28
raptormanad, INX is in the process of testing a script to make a USB install of INX -it worked for me.

[http://inx.maincontent.net/](http://inx.maincontent.net/)

see the link to questions and reports on this page and feel free to come to the IRC channel.

MarshaG.

---

### Post by lswb on 2009-07-28
With a working frame buffer, you can play movies, view pictures and images, surf the web, play music, even use the mouse without X or a gui. Depending on what version & kernel you are running, enabling a framebuffer may as easy as adding an option to your grub menu; you may also need to add a couple modules to your initrd.img

The links2 and w3m browsers can display web pages including images. the fbi package has programs to display a few different image formats. mplayer (and some other programs) can play movies (and of course audio) directly in a framebuffer console. The gpm package will enable some limited use of a mouse in a console.

One caveat about web browsing, none of these framebuffer browsers (that I know of anyway) support many modern html practices, such as use of css, scripts, and other features, it's kind of like the looking at web sites from 1996.

---

### Post by finite9 on 2009-08-03
> **Slim Odds said:**
> Just to be pedantic, you can't "view" pictures without a GUI (unless you really like ASCII art that much).


I want to view ascii art in my terminal.  I found a solution on linuxquestions for using libjpeg-progs and netpbm but the ascii is too large for a standard terminal.

I want to be able to view an image that i do not know the contents of by looking at the filename, and I do not want to download a folder full of images remotely over the net just to see what the image is.  I want to ssh into my server and just output the image as ascii on the command line to get a rough idea of what the picture is.

this works:

```
/usr/bin/djpeg <file> | /usr/bin/ppmtopgm | /usr/bin/pgmtopbm | /usr/bin/pbmtoascii -2x4
```


but the image is too big.

Does anyone else have other suggestions?

---

### Post by dreamsR4living on 2009-08-03
My favorite commandline only apps:

1. mp3blaster    (the name says it all)
2. nano          (.txt editing)
3. less          (for reading .txt files)
4. antiword      (for reading .doc files)
5. lynx          (text webbrowser as mentioned before)
6. mutt          (e-mail client, didn't use it but I like the idea)
7. mc            (Midnight Commander, advanced file management)

I hope this will give some inspiration

---

### Post by slakkie on 2009-08-03
Don't be like this guy, please: [http://seanrtilley.blogspot.com/search?updated-min=2008-06-01T00%3A00%3A00-07%3A00&updated-max=2008-07-01T00%3A00%3A00-07%3A00&max-results=10](http://seanrtilley.blogspot.com/search?updated-min=2008-06-01T00%3A00%3A00-07%3A00&updated-max=2008-07-01T00%3A00%3A00-07%3A00&max-results=10)

---

