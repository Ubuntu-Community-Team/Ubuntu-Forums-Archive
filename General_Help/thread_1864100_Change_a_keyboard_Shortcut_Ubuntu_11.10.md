---
title: "Change a keyboard Shortcut Ubuntu 11.10"
date: 2011-10-18
forum: General Help
---

### Post by YankeeFan on 2011-10-18
Greetings all,
Before upgrading to Ubuntu 11.10, I had my printscreen key pointing to ksnapshot.  After my upgrade my printscreen key is firing up a different snapshot program.  How do I change this to start up ksapshot?

Ksnapshot allows me to draw a retangle of different sizes to create a snapshot.  This is easier than editing a snapshot of the entire screen.

I went into the system >> keyboard >> Shortcuts >> Screenshots, but I cannot change what program is triggered by the clicking of the Printscreen key.

Appreciate any help, thanks...

---

### Post by mbmccurdy on 2011-10-24
Hallo!

I have the same problem also. Some keys can be reassigned properly but others cannot -- "Print Screen" and "Insert" in particular cannot be remapped to anything, although, say, "Pause/Break" can. It is very frustrating! I have had custom keybindings for several years and relearning is very painful.

---

### Post by wkrekik on 2011-11-13
The answer is here 
[http://joesteiger.com/2011/11/06/enable-alt-f2-keyboard-shortcut-ubuntu-11-10/](http://joesteiger.com/2011/11/06/enable-alt-f2-keyboard-shortcut-ubuntu-11-10/)

---

### Post by frodowiz on 2011-12-08
> **wkrekik said:**
> The answer is here 
[http://joesteiger.com/2011/11/06/enable-alt-f2-keyboard-shortcut-ubuntu-11-10/](http://joesteiger.com/2011/11/06/enable-alt-f2-keyboard-shortcut-ubuntu-11-10/)

not the answer for me :)  i want to reassign what program is launched, not the key combination..any thoughts?

---

### Post by snowguy on 2012-02-15
Hi YankeeFan, mbmccurdy, frodowiz and others who are affected,

I opened this bug [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/932990](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/932990)
related to this very problem. If it affects you please go there and say it affects you to give it some priority for fixing.

thanks.

---

### Post by bitpicker on 2012-02-26
The keybindings setting in Ubuntu 11.10 is weird, but you can set a different screenshot program for the print key in gconf. Provided you have installed gconf, go to apps -> metacity -> keybinding_commands - the last two in the list are the commands for making a full screenshot and a window shot respectively, and here you can simply set what you want.

I am using Shutter, and that program actually seems to be able to change these two settings by itself once you enable the keys in its settings -> keyboard tab.

---

### Post by lazyalex92 on 2012-12-27
The solution for this problem is by replacing "Window Manager" with "Metacity" (that you should have already installed on your ubuntu), so what you have to do is write this sequence of commands:
code:

#!/bin/bash 
metacity --replace & 
disown

save it as bash file in a directory you prefer, than go to prefrences -> Startup application -> add, so browse your saved file and add it. 
Restart and you'll see metacity working.
Hope that my resolution will be usefull for you and hope you'll understand my english cause i'm italian.. =)

---

