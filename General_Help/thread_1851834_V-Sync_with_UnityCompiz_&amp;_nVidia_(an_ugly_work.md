---
title: "V-Sync with Unity/Compiz &amp; nVidia (an ugly workaround)"
date: 2011-09-29
forum: General Help
---

### Post by quequotion on 2011-09-29
Every time I log in, if I use the standard Unity/Compiz desktop, I get a really bad desktop experience. I have seen a lot of posts about this around the internet, mostly from people using the proprietary nVidia driver.

Most of the time, people suggest to disable v-sync in compiz settings and/or driver settings. This *slightly* improves the desktop's responsiveness and works around frequent crashes, but the tearing is awful.

I found a way to get a (mostly) tear-free desktop in Natty, with Unity/Compiz and nVidia. I believe there is a better way.
 

First, these are symptoms my desktop initially has (at every log in):

The screen is "cut" along a horizontal line, usually near the middle of the screen or somewhat below it. You can find this by draging a window across it or watching a video in fullscreen. It's pretty obvious and very ugly. (see attached screenshot)

Typed characters don't appear until another character is typed. (ie, typing "abcdef" looks like "abcde" until you type "g")

Menu items highlighted by the mouse remain highlighted after the cursor has moved on to another item. The same when using the keyboard to scroll through menus. (***really annoying*** because I tend to follow the decorations around the cursor rather than the cursor itself)

The ugly workaround (which proves there must be a better way):

Restart X.

I re-enabled the [ctrl]+[alt]+[backspace] keys.

After loging in, I restart the X server with [ctrl]+[alt]+[backspace] and log in again.

The result is a tear-free desktop (with v-sync enabled in both compiz and nvidia-settings).

I'm sure this issue can be fixed. I suspect something is loading out of order at boot, so restarting the X server sets things right.

---

### Post by quequotion on 2011-10-19
This bug has become much worse in Oneiric and this workaround doesn't work anymore.

[I filed  bug report](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/875564) but it isn't getting much attention.

---

