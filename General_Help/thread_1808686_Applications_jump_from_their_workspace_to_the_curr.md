---
title: "Applications jump from their workspace to the current workspace"
date: 2011-07-20
forum: General Help
---

### Post by msp3k on 2011-07-20
Hi guys,

I believe I may have found a bug in Unity.  Under the right circumstances an application will jump from the workspace where I left them to my current workspace.  This is most noticeable with VirtualBox.  I built an Ubuntu 11.04 virtual machine so that I could test out new packages before I push them out to the rest of my machines.  But the window for the virtual machine constantly appears in my current workspace.  It may take a few minutes, or 30 minutes, but it will happen.

I can kind of understand it if a new window appears, but at least with VirtualBox, this happens on a running virtual machine seemingly randomly.

This is very annoying.

Has anyone else noticed this behavior?

---

### Post by msp3k on 2011-07-20
One guaranteed way to trip the bug seems to be to tell the virtual machine to reboot, then immediately switch workspaces.  When the virtual machine comes back online, the window will jump to the workspace that you're on.

---

