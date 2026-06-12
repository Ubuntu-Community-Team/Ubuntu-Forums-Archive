---
title: "Switch Workspace from fullscreen Terminal Server Client session"
date: 2010-09-25
forum: General Help
---

### Post by w4n on 2010-09-25
Hey guys,

I'd like to know if any of you guys know a way to easily switch from a workspace where a fullscreen Terminal Server Client is running to another workspace (ideally using his configured switch command like [ctrl]+[alt]+[arrow])?

I know that you can leave the fullscreen mode temporarily with [ctrl]+[alt]+[enter]. But thats much work if you have to switch often between the workspaces. Here's how I do it know:
1. Press [ctrl]+[alt]+[enter] to leave fullscreen
2. Click out of terminal session
3. Switch workspace [ctrl]+[alt]+[arrow]
4. Switch back
5. Enable Fullscreen

I sure hope there's an easier way for this, do you have any idea?

---

### Post by w4n on 2010-09-25
I did a bit of research and found a [bug on Launchpad (#270997)]("https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/270997") which adresses my problem. Rdesktop grabs all the keyboard input and ignores the window managers key bindings even though the K option is set. Unfortunately this got never fixed, so I'm using another rdp client (Remmina - which works fine) for now.

---

