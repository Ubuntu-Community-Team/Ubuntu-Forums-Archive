---
title: "Noob Questions - Preferred Applications and Font Selection"
date: 2011-03-21
forum: General Help
---

### Post by mudzereli on 2011-03-21
I've just switched over to Ubuntu yesterday. I'm loving the change, but there are a few things I'm having trouble with. 

When I go to System -> Preferences -> Preferred Applications -> System, it says GNOME Terminal.

When I execute Accessories -> Terminal, it loads xterm.

When I go to System -> Preferences -> Preferred Applications -> Internet -> Browser, it says Custom

Whenever I click a link, it loads Firefox

1. Should the GNOME Preferred Applications be affecting these?
2. If so, is there something I need to do to make it take effect?
3. If not, what do the Preferred Applications affect?


My next question is regarding font selection.

A fellow linux user told me to check out the "terminus" font. He had me do a bit of searching using xfontsel and I couldn't find it. I also looked through System -> Preferences -> Appearance -> Fonts. I couldn't find anything named "terminus." I did some searching on the internet, and was able to find the name of the package, so I try sudo apt-get install console-terminus. It says it's already installed. I'm not sure where to proceed from here.

Thanks in advance!

---

### Post by Script Warlock on 2011-03-21
> **mudzereli said:**
> I've just switched over to Ubuntu yesterday. I'm loving the change, but there are a few things I'm having trouble with. 

When I go to System -> Preferences -> Preferred Applications -> System, it says GNOME Terminal.

When I execute Accessories -> Terminal, it loads xterm.

When I go to System -> Preferences -> Preferred Applications -> Internet -> Browser, it says Custom

Whenever I click a link, it loads Firefox

1. Should the GNOME Preferred Applications be affecting these?
2. If so, is there something I need to do to make it take effect?
3. If not, what do the Preferred Applications affect?


My next question is regarding font selection.

A fellow linux user told me to check out the "terminus" font. He had me do a bit of searching using xfontsel and I couldn't find it. I also looked through System -> Preferences -> Appearance -> Fonts. I couldn't find anything named "terminus." I did some searching on the internet, and was able to find the name of the package, so I try sudo apt-get install console-terminus. It says it's already installed. I'm not sure where to proceed from here.

Thanks in advance!

what do want to achieve with your terminus font? after installing you you may want to refresh it with fc-cache -f -v

---

### Post by mudzereli on 2011-03-21
> **Script Warlock said:**
> what do want to achieve with your terminus font? after installing you you may want to refresh it with fc-cache -f -v

I'd like to use it for my terminal font.

My main goal is this:

1. Switch my default Terminal to rxvtu (I've got it installed, and I know I can create a launcher, but I want to know why the heck the preferred application settings don't seem to be doing anything)

2. Switch my Terminal font to terminus.

I've tried what you've suggested, but I am still unable to find the terminus font.

Thanks!

---

### Post by Script Warlock on 2011-03-21
open terminal go to edit>profile preference>general> untick the "use system fixed width font" and select the terminus font you installed.

manual setting
terminal
sudo update-alternatives --config x-terminal-emulator

browser
sudo update-alternatives --config x-www-browser

---

### Post by mudzereli on 2011-03-21
> **Script Warlock said:**
> open terminal go to edit>profile preference>general> untick the "use system fixed width font" and select the terminus font you installed.

manual setting
terminal
sudo update-alternatives --config x-terminal-emulator

browser
sudo update-alternatives --config x-www-browser

Terminus isn't listed under my system fixed width fonts. Although when I type sudo apt-get install console-terminus, it says I already have it.

I've also tried this: sudo update-alternatives --config x-terminal-emulator

```
mudzereli@mudzereli-P35-DS3L:~$ sudo update-alternatives --config x-terminal-emulator
[sudo] password for mudzereli: 
There are 6 choices for the alternative x-terminal-emulator (providing /usr/bin/x-terminal-emulator).

  Selection    Path                             Priority   Status
------------------------------------------------------------
  0            /usr/bin/gnome-terminal.wrapper   40        auto mode
  1            /usr/bin/gnome-terminal.wrapper   40        manual mode
  2            /usr/bin/koi8rxterm               20        manual mode
  3            /usr/bin/lxterm                   30        manual mode
* 4            /usr/bin/urxvt                    20        manual mode
  5            /usr/bin/uxterm                   20        manual mode
  6            /usr/bin/xterm                    20        manual mode

Press enter to keep the current choice[*], or type selection number: 
```

It seems to have selected it, but doesn't have any effect on which one is the default one.

Thanks again for all of the help!

---

### Post by Script Warlock on 2011-03-21
choose "zero" as default terminal emulator

install xfonts-terminus

---

