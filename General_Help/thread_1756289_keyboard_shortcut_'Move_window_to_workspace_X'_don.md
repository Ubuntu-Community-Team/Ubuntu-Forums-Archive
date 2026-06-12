---
title: "keyboard shortcut 'Move window to workspace X' don't work for me"
date: 2011-05-12
forum: General Help
---

### Post by pabc on 2011-05-12
on my main PC (10.04) I have Alt+1,Alt+2 etc configured to jump to that specific workspace and ctrl+Alt+1,ctrl+alt+2 etc to move the focused window to the specific workspace and it works fine.
 
trying to replicate that on my netbook (11.04/unity) however fails. I can set the keyboard shortcuts up to switch to different workspaces but the shortcuts to move a window to a specific workspace just dont seem to work.
 
the default RSI inducing default ctrl+shift+alt+(up,down,left & right) to move a window to an adjacent workspace does however.
 
is this specific to my install?
 
if so how can I fix it?
if not how do i file a bug report?

---

### Post by pabc on 2011-05-17
5 days seems long enough to wait before a 'bump'
 
any ideas why only the default shortcut keys seem to work for moving a window around workspaces in unity?

---

### Post by gmargo on 2011-05-17
I think it has to do with the window manager.  

Using 11.04 Natty, I tried this under Unity-2D (which uses the **metacity** window manager), and those keyboard shortcuts work fine.

However, under Unity-3D ("normal" Unity using the **compiz** window manager), they do not work. (Alt-1 works but Ctrl-Alt-1 does not)

The "Keyboard Shortcuts" seem to apply only to **metacity**, and not **compiz**. The Alt-1, Alt-2 seem to work because they are mapped by **compiz** to do what you expect.  

If you install the **compizconfig-settings-manager** package, then System-Settings will have a "CompizConfig Settings Manager" entry. Inside that, you can select various compiz modules, many of which have their own keyboard mappings.  See the "Viewport Switcher" module.  That one is mapping Alt-1, Alt-2 to do the switch-workspace function.

I cannot find a module that implements a "move this window to this workspace" function in the standard install.  However, if you install the **compiz-plugins-extra** package, there will be a module called "Put" which seems to be meant to implement "put to arbitrary viewport" but I could not get it to work.

This is not the definitive word on the subject - just what I was able to figure out by mucking about with it - corrections/additions welcome.

---

### Post by pabc on 2011-05-18
thank you. at least i know i'm not going mad. i'll just have to sit tight and cope then.

---

### Post by sid_waste on 2011-09-20
on my main PC (10.04) I have Alt+1,Alt+2 etc configured to jump to that  specific workspace and ctrl+1,ctrl+2 etc to move the focused  window to the specific workspace and it is not wroking for me... though move window to one space left works fine.
It looks like wats working for you isnt working for me.
any help how u were right at it?

> **pabc said:**
> on my main PC (10.04) I have Alt+1,Alt+2 etc configured to jump to that specific workspace and ctrl+Alt+1,ctrl+alt+2 etc to move the focused window to the specific workspace and it works fine.
 
trying to replicate that on my netbook (11.04/unity) however fails. I can set the keyboard shortcuts up to switch to different workspaces but the shortcuts to move a window to a specific workspace just dont seem to work.
 
the default RSI inducing default ctrl+shift+alt+(up,down,left & right) to move a window to an adjacent workspace does however.
 
is this specific to my install?
 
if so how can I fix it?
if not how do i file a bug report?

---

### Post by sid_waste on 2011-09-20
test!

---

### Post by merindol on 2012-02-02
Hi.

To be able to put a window on an arbitrary viewport under Unity through keyboard hotkeys I had to create a script because the Put plugin doesnt work.

- This script works with a 4x1 desktop (4 horizontal viewports on 1 line).
- In case it's not installed by default (in a terminal) : sudo apt-get install wmctrl x11-utils
- Download [http://pastebin.com/qm7CuhMx](http://pastebin.com/qm7CuhMx)
- Copy the script to ~/bin/putWindowOnViewport.sh
- Assign those commands to your hotkeys :
    sh $HOME/bin/putWindowOnViewport.sh 1
    sh $HOME/bin/putWindowOnViewport.sh 2
    sh $HOME/bin/putWindowOnViewport.sh 3
    sh $HOME/bin/putWindowOnViewport.sh 4

Good luck.

---

### Post by otakuj462 on 2012-04-21
To anyone else who comes across this article, the best solution I found was to use the Put plugin for compiz. Unfortunately, the place window funcitonality of the put plugin has an upstream bug, described here:
[https://bugs.launchpad.net/ubuntu/+source/compiz-fusion-plugins-main/+bug/684019](https://bugs.launchpad.net/ubuntu/+source/compiz-fusion-plugins-main/+bug/684019)

There is a patch which solves the issue. To build and apply it, see instructions here:
 [https://bugs.launchpad.net/ubuntu/+source/compiz-fusion-plugins-main/+bug/684019/comments/18](https://bugs.launchpad.net/ubuntu/+source/compiz-fusion-plugins-main/+bug/684019/comments/18)

---

### Post by vangop on 2012-05-23
> **merindol said:**
> Hi.

To be able to put a window on an arbitrary viewport under Unity through keyboard hotkeys I had to create a script because the Put plugin doesnt work.



Good luck.

Tried the script, but it won't work. I've tried to change the viewport_x coords based on my resolution - stil it jumps to the next WS and then back. No window is moved..

---

