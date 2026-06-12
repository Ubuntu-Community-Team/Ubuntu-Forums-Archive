---
title: "What on earth are these lines on my desktop?"
date: 2010-08-10
forum: General Help
---

### Post by narnie on 2010-08-10
Hello,

For the past several versions, I have these lines on my desktop. I was able to find out this window information about them:

```
WM_HINTS(WM_HINTS):
		Client accepts input or input focus: True
		Initial state is Normal State.
		window id # of group leader: 0x5600001
WM_WINDOW_ROLE(STRING) = "alert"
_NET_WM_ALLOWED_ACTIONS(ATOM) = _NET_WM_ACTION_MOVE, _NET_WM_ACTION_RESIZE, _NET_WM_ACTION_STICK, _NET_WM_ACTION_CLOSE, _NET_WM_ACTION_CHANGE_DESKTOP, _NET_WM_ACTION_ABOVE, _NET_WM_ACTION_BELOW
XdndAware(ATOM) = BITMAP
_MOTIF_DRAG_RECEIVER_INFO(_MOTIF_DRAG_RECEIVER_INFO) = 0x6c, 0x0, 0x5, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x10, 0x0, 0x0, 0x0
_NET_WM_SYNC_REQUEST_COUNTER(CARDINAL) = 90346353
_NET_WM_WINDOW_TYPE(ATOM) = _NET_WM_WINDOW_TYPE_UTILITY
_NET_WM_USER_TIME(CARDINAL) = 114173934
_NET_WM_USER_TIME_WINDOW(WINDOW): window id # 0x5629370
WM_CLIENT_LEADER(WINDOW): window id # 0x5600001
_NET_WM_PID(CARDINAL) = 2523
WM_LOCALE_NAME(STRING) = "en_US.utf8"
WM_CLIENT_MACHINE(STRING) = "toshiba-laptop"
WM_NORMAL_HINTS(WM_SIZE_HINTS):
		program specified location: 0, 0
		program specified minimum size: 0 by 0
		window gravity: NorthWest
WM_PROTOCOLS(ATOM): protocols  WM_DELETE_WINDOW, WM_TAKE_FOCUS, _NET_WM_PING, _NET_WM_SYNC_REQUEST
WM_CLASS(STRING) = "Alert", "Firefox"
WM_ICON_NAME(STRING) = 
_NET_WM_ICON_NAME(UTF8_STRING) = 
WM_NAME(STRING) = 
_NET_WM_NAME(UTF8_STRING) =
```
This shows it as some type of firefox alert. Why is it there? How to get rid of them (short of pkill firefox, etc).

I have included a pic from the bottom right portion of my screen (as in where the download alert pops up).

With thanks,
Narnie

---

### Post by Peter09 on 2010-08-10
To double check its worth looking at your graphics card setup, this is likely the source.
 
```
lshw -C video
```
 
should give you details of driver and card.

---

### Post by Shrek01 on 2010-08-10
I had that problem on a computer with an ATI card and a generic driver (ATI stopped developing drivers for it).
I found out that by disabling the visual effects, the lines were gone.
*System->Preferences->Appearance-> Visual Effects: None*

---

### Post by john.hernandez on 2010-08-10
These problem is because of your driver. Just fix them properly will solve your issue. I had similar issue before but my computer guy reinstalled the driver.

---

### Post by narnie on 2010-08-10
> **Shrek01 said:**
> I had that problem on a computer with an ATI card and a generic driver (ATI stopped developing drivers for it).
I found out that by disabling the visual effects, the lines were gone.
*System->Preferences->Appearance-> Visual Effects: None*

This worked with no effects enabled.

---

### Post by narnie on 2010-08-10
> **Peter09 said:**
> To double check its worth looking at your graphics card setup, this is likely the source.
 
```
lshw -C video
```
 
should give you details of driver and card.

I am purposefully using the generic ATI driver (and proprietary driver is buggy on my system). Pleasantly, 3D render is now hardware and compiz works (I've missed my eye-candy on the system).

Narnie

```
$ lshw -C video
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: M92 [Mobility Radeon HD 4500 Series]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:31 memory:c0000000-cfffffff(prefetchable) ioport:6000(size=256) memory:d8300000-d830ffff memory:d8320000-d833ffff(prefetchable)
```

---

### Post by narnie on 2010-08-10
> **john.hernandez said:**
> These problem is because of your driver. Just fix them properly will solve your issue. I had similar issue before but my computer guy reinstalled the driver.

I'm great in linux with many things, but graphics is not one of them. How do I go about fixing my driver issues?

This is on a fresh install of Lucid (10.04), but has occurred since at least jaunty, if not intrepid.

Narnie

---

