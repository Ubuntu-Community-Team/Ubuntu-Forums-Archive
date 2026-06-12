---
title: "Disabling keyboard repeat from the command-line"
date: 2010-04-11
forum: General Help
---

### Post by clockworksaint on 2010-04-11
Background:

Some Flash games don't work very well on Linux because when you hold down a key (such as one of the cursor keys) the Flash player sends the game multiple KeyDown and KeyUp events, leaving the game unable to tell the difference between a user holding a key or a user tapping a key quickly. (On other platforms it seems that typematic repeat generates multiple KeyDown events but not KeyUp events.)

Anyway, to work around this problem, I go to System->Preferences->Keyboard and disable "Key presses repeat when key is held down" when I want to play a Flash game, then put it back afterwards. I do this often enough that I'd like to set up some shortcut keys to change the setting. I figured out the following commands to turn it off and on again:

gconftool-2 --set /desktop/gnome/peripherals/keyboard/repeat --type bool false

gconftool-2 --set /desktop/gnome/peripherals/keyboard/repeat --type bool true

The problem:

My problem is that when I have tried entering these on the command-line (in a gnome-terminal), X-windows seems to get confused and behaves as though I'm holding down the enter key. It doesn't stop if I press enter again. I tried pressing ctrl-alt-f1 to switch to a text console and it worked fine, but when I pressed ctrl-alt-f7 to go back to X it still behaved as though I was holding down enter. I had to press ctrl-alt-backspace to reset X before it would return to normal. I *think* it happens in particular when changing the setting from true to false.

What should I do next? Should I report this as a bug somewhere? Or am I doing something obviously wrong?

I'm running Karmic Koala with all the updates.

---

### Post by clockworksaint on 2010-04-11
Oops, spoke too soon. This describes my problem:

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/367136](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/367136)

The workaround is to disable the "ally-keyboard" plugin, which appears to be for providing keyboard accessibility features.

---

