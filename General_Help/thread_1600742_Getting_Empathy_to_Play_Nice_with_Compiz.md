---
title: "Getting Empathy to Play Nice with Compiz"
date: 2010-10-19
forum: General Help
---

### Post by amishphysicist on 2010-10-19
Hi All,

Does anyone know the class name for Empathy's chat windows and buddy list?

On Ubuntu 10.10:

System->Preferences->CompizConfig Settings Manager->Window Management->Place Windows->Fixed Window Placement

Trying to grab the Empathy window class doesn't produce any results and adding "empathy" as a windows class to control only affects the "about empathy" window and not the conversations or the contact list.

It'd be nice if Empathy behaved like the rest of my programs and allowed me to restrict it to a specific workspace. Not sure what class I should be using. Any ideas?

Thanks!

---

### Post by chessnerd on 2010-10-19
I've never used Empathy, but it is possible it is using multiple processes for its windows. Have a look at the System Monitor (System > Administration > System Monitor) when Empathy is running and see if there are multiple processes with "empathy" in the name. If so, you could try adding one of those.

---

### Post by amishphysicist on 2010-10-20
Interesting.  Looks like Empathy doesn't supply anything worthwhile to Compiz.  Here are the results of [Compiz's window matching commands:]("http://wiki.compiz.org/WindowMatching")

```
meh@muh:~$ xprop WM_CLASS | cut -d\" -f2
gnome-panel
meh@muh:~$ xprop WM_CLASS | cut -d\" -f2
WM_CLASS:  not found.
meh@muh:~$ xprop _NET_WM_WINDOW_TYPE | cut -d_ -f10

meh@muh:~$ xprop WM_WINDOW_ROLE | cut -d\" -f2
WM_WINDOW_ROLE:  not found.
meh@muh:~$ xprop WM_NAME | cut -d\" -f2
WM_NAME:  not found.
meh@muh:~$ xwininfo | grep "Window id:" | cut -d ' ' -f4
0x1e00290

```

Strange that Empathy doesn't provide anything except for the XID.  I'll have to see if the XID is dynamic, or if it always has the same value across restarts, respawns, etc.  I've posted a bug to Empathy about this, but I'm not holding my breath there.

---

### Post by amishphysicist on 2010-10-20
Hmm. Looks like the xid doesn't want to do anything, anyhow. So I guess I'm pretty much stuck. Bummer.

```
xwininfo: Window id: 0x1e00290 (has no name)

  Absolute upper-left X:  1271
  Absolute upper-left Y:  95
  Relative upper-left X:  1271
  Relative upper-left Y:  95
  Width: 246
  Height: 959
  Depth: 0
  Visual: 0x21
  Visual Class: TrueColor
  Border width: 0
  Class: InputOnly
  Colormap: 0x0 (not installed)
  Bit Gravity State: ForgetGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: yes
  Corners:  +1271+95  -403+95  -403-26  +1271-26
  -geometry 246x959+1271-26


```

If anyone else runs into this, I've logged a bug against Empathy here:
[https://bugzilla.gnome.org/show_bug.cgi?id=632481]("https://bugzilla.gnome.org/show_bug.cgi?id=632481")

---

