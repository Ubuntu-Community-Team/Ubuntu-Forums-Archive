---
title: "Workspace switching disabled in 9.04 x64"
date: 2009-06-29
forum: General Help
---

### Post by Error 404 on 2009-06-29
I've downloaded and installed Ubuntu 9.04 x64 onto my current gaming rig, dual booting with Vista HP 32-bit, and so far I've managed to get almost everything working correctly (finding MP3 support was a PITA though).
I'm enjoying Ubuntu's speed and flexibility, but for some reason multiple workspaces has been disabled. Ctrl+Alt+(Left/Right) no longer works. The workspace icon shows I have 2 workspaces, but wont let me switch!
I've checked, and those keyboard shortcuts are enabled. I even tried disabling the desktop cube effect in compiz, although I know my graphics card can easily run it.
Any ideas why this is happening? I liked my cube and second desktop :(

---

### Post by CatKiller on 2009-06-29
Have you got the Workspace Switcher plugin enabled?

---

### Post by Error 404 on 2009-06-29
> **CatKiller said:**
> Have you got the Workspace Switcher plugin enabled?

Are you talking about GNUstep Workspace Manager (package name: gworkspace.app)?
If so, then thats not installed. I would think a workspace switcher is already installed, since I have the option to add a switcher applet to the taskbar...
Shall I install the GNUstep plugin?

---

### Post by CatKiller on 2009-06-29
> **Error 404 said:**
> Are you talking about GNUstep Workspace Manager (package name: gworkspace.app)?

No, I'm talking about the Compiz plugin. I have no idea what you're talking about :)

If you've got compizconfig-settings-manager installed, which I assume you have since you talked about disabling the cube, it's

System -> Preferences -> CompizConfig Settings Manager -> Desktop -> Viewport Switcher

(I don't know why Compiz calls workspaces viewports)

If it isn't enabled, you can't switch workspaces under Compiz; that's what that plugin is for.

---

### Post by Error 404 on 2009-06-29
It was enabled, and even just normal switching (by clicking on the workspace switcher applet) doesn't work. Even with almost everything but Viewport switcher in Compiz disabled no luck!
This was happening before the updates as well...

---

### Post by CatKiller on 2009-06-29
If you're using the cube, you'll need the Rotate Cube plugin enabled as well. If you aren't, you'll probably want one of the other ways of displaying the workspaces (like Desktop Wall) enabled instead.

---

