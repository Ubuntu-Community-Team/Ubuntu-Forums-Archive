---
title: "What are the steps to set up doubleclick on a *.txt file to open with &quot;/usr/bin/vi&quot;"
date: 2010-09-01
forum: General Help
---

### Post by rocksockdoc on 2010-09-01
What are the steps to set up doubleclick on a *.txt file to open with "/usr/bin/vi" ?

I'm new to Linux. In Windows, to open a text file in, say, C:\bin\vim, one would merely "associate" the *.txt extension with the path to "c:\bin\vim\vim.exe".

But how do we accomplish this simple task in Ubuntu 10.04?

When I doubleclick on a file, foo.txt, the contents of the file come up in gedit.
But I want the contents of the file to come up in vi.

When I right-click on the file, foo.txt and select "Open With->vi", nothing happens.
When I right-click on the file, foo.txt, and select "Properties->Open With->vi", again, nothing happens.

I know vi is working because in the "terminal" I can change directory to the Desktop and open the file in vi using the command "$vi foo.txt"; but I just can't figure out how to get the GUI to always open *.txt files in the vi editor.

Note: Additionally I want to open *.log files in the /usr/bin/vim but that should be the same procedure.

What are the steps to force a doubleclick of a *.txt file to open up in /usr/bin/vi?

---

### Post by sisco311 on 2010-09-01
vi is a CLI app, you have to run it in a terminal, open with -> custom command:
```
gnome-terminal -x vi
```

---

### Post by rocksockdoc on 2010-09-02
> **sisco311 said:**
> vi is a CLI app, you have to run it in a terminal, open with -> custom command:
```
gnome-terminal -x vi
```

Thanks for helping out. I had belatedly realized that I needed a terminal. I didn't know about "gnome-terminal" (until now) so I had solved it with "xterm -e vi" instead (see photo below).

For others to benefit, /usr/bin/vi and /usr/bin/vim and /usr/bin/vim-nox, etc., all require a terminal. There will not be an error when you try to open a file using them from the GUI; they just won't open up. Nothing will happen.

Another solution, I belatedly found out, is to install "gvim", which WILL open up from the GUI.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=168220&stc=1&d=1283421331[/IMG]

---

### Post by Sam on 2010-09-02
What about [vim-gnome](apt:vim-gnome) ?

---

### Post by Ghost_Mazal on 2010-09-02
Can one add it somehow to the right-click contect that it stays as an option under "open with" ? So that double click will stay with gedit but vi will be as an option for use sometimes.

---

### Post by sisco311 on 2010-09-02
> **Ghost_Mazal said:**
> Can one add it somehow to the right-click contect that it stays as an option under "open with" ? So that double click will stay with gedit but vi will be as an option for use sometimes.

Yes, right click on the file -> Properties -> Open With tab -> + Add button -> add vi to the list, then select gedit as the default editor. vi should show up in the Open With... menu.

---

### Post by rocksockdoc on 2010-09-04
As a summary (please correct if I'm wrong), the 'vi-like' programs that can be set for the *.txt default double-click editor are (afaik):

1. xterm -e /usr/bin/vi    ... or ... gnome-terminal -x vi
2. xterm -e /usr/bin/vim  ... or ... gnome-terminal -x vim
3. xterm -e Gvim ... or... gnome-terminal -x vim-gnome

---

### Post by sisco311 on 2010-09-05
> **rocksockdoc said:**
> As a summary (please correct if I'm wrong), the 'vi-like' programs that can be set for the *.txt default double-click editor are (afaik):

1. xterm -e /usr/bin/vi    ... or ... gnome-terminal -x vi
2. xterm -e /usr/bin/vim  ... or ... gnome-terminal -x vim
3. [s]xterm -e[/s] Gvim ... or... [s]gnome-terminal -x[/s] vim-gnome


Fixed :), vim-gnome is a GUI application, you don't have to run it in a terminal.

[http://wiki.answers.com/Q/What_is_the_difference_between_gui_and_cli](http://wiki.answers.com/Q/What_is_the_difference_between_gui_and_cli)

---

### Post by rocksockdoc on 2010-09-06
> **sisco311 said:**
> Fixed :), vim-gnome is a GUI application, you don't have to run it in a terminal

Thanks. I'm new to this operating system and quite a few things that just come naturally on the other operating systems need to be learned in this wonderful Ubuntu 10.04 (which is new to me).

Here's the corrected "Open With" summary for a click in the GUI.
```

1. xterm -e /usr/bin/vi    ... or ... gnome-terminal -x vi
2. xterm -e /usr/bin/vim  ... or ... gnome-terminal -x vim
3. Gvim ... or... vim-gnome 

```

---

### Post by rocksockdoc on 2011-04-24
> **sisco311 said:**
> vim-gnome is a GUI application, you don't have to run it in a terminal

I wasn't sure what "vim-gnome" is, but doing the requisite search for "vi" in the "Ubuntu Software Center", there seems to be only one "vi equivalent" anyway, which is GVim.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189869&stc=1&d=1303629813[/IMG]

---

### Post by coldraven on 2011-04-24
There is also nano. 
If you haven't  discovered it yet have a look at the Synaptic Package Manager.
I prefer it to the Software Centre because it gives more info, download size, dependencies and a list of installed files. (right click, select Properties, Files Tab) Useful for discovering documentation that accompanies a program and is not obviously visible.
You cannot use Synaptic and the Software Centre at the same time as they are both front ends for apt. synAPTic geddit?

---

