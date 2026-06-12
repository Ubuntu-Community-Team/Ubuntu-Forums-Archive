---
title: "recording macros in jEdit"
date: 2011-04-14
forum: General Help
---

### Post by dragonfly41 on 2011-04-14
I've installed jEdit .. 
following instructions here ..

[http://getch.wordpress.com/2009/02/17/install-jedit-in-ubuntu-how-to/](http://getch.wordpress.com/2009/02/17/install-jedit-in-ubuntu-how-to/)

In trying to record a macro 
Macros > Record Macro
I can see "Macro recording" message in status bar

but no macro code is generated and no macro can be run.

Any ideas on getting macros to work in jEdit?

---

### Post by dragonfly41 on 2011-04-14
I've misunderstood the scope of jEdit macros .. they work o.k. within the context of jEdit.

They do not record keystrokes for example in writing commands into ubuntu terminal.

I'm looking for the equivalent functionality of AutoHotKey in windows .. but in ubuntu ..

[http://www.autohotkey.com/docs/Tutorial.htm](http://www.autohotkey.com/docs/Tutorial.htm)

---

### Post by dragonfly41 on 2011-04-14
Exploring the options further .. is it feasible for jEdit editor to substitute for the ubuntu Terminal command line editor?

Macros could then be applied to commands.

Currently I've learned from various threads that I can't copy and paste text from jEdit into terminal editor.

---

### Post by dragonfly41 on 2011-04-15
I'm clarifying my initial question in this thread ..

[COLOR=Navy]*How do I add jEdit into the list of "default terminal emulators" so that I can run commands from within jEdit .. and then refer to jEdit library of macros to paste pre-recorded commands into command line?*[/COLOR]

I've been reading a bit more about x-terminal-emulator

[http://www.howtogeek.com/howto/ubuntu/set-the-default-terminal-emulator-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/set-the-default-terminal-emulator-on-ubuntu-linux/)

```

~$ sudo update-alternatives --config x-terminal-emulator
There are 5 choices for the alternative x-terminal-emulator (providing /usr/bin/x-terminal-emulator).

  Selection    Path                             Priority   Status
------------------------------------------------------------
* 0            /usr/bin/gnome-terminal.wrapper   40        auto mode
  1            /usr/bin/gnome-terminal.wrapper   40        manual mode
  2            /usr/bin/koi8rxterm               20        manual mode
  3            /usr/bin/lxterm                   30        manual mode
  4            /usr/bin/uxterm                   20        manual mode
  5            /usr/bin/xterm                    20        manual mode

Press enter to keep the current choice
[*], or type selection number: 

```

Can I add jEdit to the above options?

---

