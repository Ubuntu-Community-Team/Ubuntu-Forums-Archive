---
title: "How to copy a URL with links2 -g ?"
date: 2012-05-04
forum: General Help
---

### Post by rapper97 on 2012-05-04
I am running [FONT="monospace"]links2[/FONT] in graphics mode but cannot copy addresses to X Windows' clipboard. There is an option to "_C_opy link location  c" when right-clicking a link, but this does not work, and neither can I copy the current URL because Links 2 won't let me click and drag, or it's part of the status window, and cannot be selected.

Am I missing something, or does anybody have an idea on how to copy the address of either the page you're on or of a link to be pasted into an xorg program?

---

### Post by El Potro on 2012-05-05
Hello **rapper97**

I'm currently investigating about this, and I know something that may help you.

Did you try installing **glipper**? To install it, simply open synaptic and search for it, and install it, or you can do it from a terminal with the following command:

```
sudo apt-get install glipper

```
Once the package is installed, right-click the gnome-panel and press "Add to panel", then select Clipboard manager.

You will see a small clipboard icon that appears there, that is glipper, the clipboard manager. 

Now, try once again to copy an URL with links2 -g, and afterwards, check if it is shown in the glipper drop-down menu. If it is shown, simply select it, and now will be the clipboard's active object, meaning that you can paste it with ctrl+v.

I hope that helps!:popcorn:

I'm not an expert on clipboard issues, but I think this inconvenient might happen due to some incompatibilities of links2 (or terminal-based apps in general) and the X clipboard.

---

### Post by rapper97 on 2012-05-06
That **** *totally worked!*
Once again, I think links2 -g is my favourite browser!

¡Gracias, Potro!

---

### Post by El Potro on 2012-05-07
I'm glad to help!

Did you try elinks? It has color support, unicode support, multi-tabbed browsing, and so on. I specially recommend  it if you are going to use it in a virtual terminal.

Please mark this thread as solved editing the first post!

All the best

---

### Post by rapper97 on 2012-05-15
I feel like a fuckin' idiot dumbtard. Was it there before? But I can't believe I missed xlinks2's File menu option to _C_opy current URL location.

**But**, I still would've needed glipper to use it for anything. So thanks again, Potrito!

As for elinks, between lynx in the terminal and Links 2 for graphical use, there's really no room for a niche that elinks fills. Maybe I'm missing something, but if you haven't tried links2 in graphical mode I'd recommend it.

Also, PowerUsers' Tip, if you hit Ctrl-C in xlinks2 it will END YOUR SESSION duh, so don't do that unless you want to see your browser window instantaneously disappear.

---

### Post by twogeo on 2012-09-14
> **rapper97 said:**
> xlinks2's File menu option to _C_opy current URL location.



Just to make that a little clearer for folk:  there is *no access at  all* out to the default Gnome clipboard (at least for Unity2D and Unity that I  tested) in the Precise install of Links2 V2.6   Even if you use the Links2  file menu (contextual or drop-down) after selecting any text, including a  well-formed link, there is zero communication out of Links2 graphical  mode.  The listed keys don't have access either.  CTRL B, CTRL X, CTRLV.  

Neither is text selection available in the terminal mode... at least from the quick look I took at it just now.   There may be a setting that isn't quickly discoverable, but as it stands, the browser gets you around links very nicely, but is buggy on text selection.

I've reported the bug to the dev.  I have an idea that it's a regression after JavaScript was removed from Links2.

So, many thanks to El Potro for the missing utility!
glipper has a history and management console that makes it a welcome addition to all Gnome sessions, not just with Links2.

I prefer using Links2 over elinks for graphical sessions because of the very nice display configuration access.   Clarity and brightness are important when you're mainly searching text and text within graphics.   A lot of sci web publications these days throw graphics into precis articles, rather than make them available as pdfs.  *grumble*

---

### Post by twogeo on 2012-09-17
> **twogeo said:**
> 
  I have an idea that it's a regression after JavaScript was
removed from Links2. 

Nope, I couldn't be more wrong.  Plus I had a very basic grasp of how the clipboard is accessed.
The dev communicates that there are 2 clipboards available to
Xwindow applications.  And Links2 uses only one of them.  He
confirms that you can
>  copy the selected text to xterm, firefox or
openoffice by clicking the middle mouse button in the target
window (I tried that). You can try to paste by clicking the
middle mouse button in other programs.and I've confirmed gedit, sylpheed and a couple of graphics utilities also
use the middle mouse clipboard.
This makes Links2 super to use in my system.  All you have to do to get any text onto the clipboard from Links2 is to select it!  Not being a linux hardcore user, this particular efficiency had passed me by until today :-)

glipper is a good enough workaround because it must copy from one clipboard to the other for us dummies.   However after a couple of days of glipper use, I'm more attracted to using the middle mouse clipboard for its efficiency - plus glipper crashes a bit in Unity2D.

The dev says he may change Links to use both clipboards if there's a majority of
Xwindow programs that use the second clipboard.

---

