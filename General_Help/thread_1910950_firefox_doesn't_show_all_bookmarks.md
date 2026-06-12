---
title: "firefox doesn't show all bookmarks"
date: 2012-01-18
forum: General Help
---

### Post by xadder on 2012-01-18
Hi,
I have ubuntu 11.10 on both a desktop PC and a portable Thinkpad x220i, and share bookmarks between the two via links to places.sqlite in the .mozzila/firefox/xxxxx.... directories.

On the desktop PC, all bookmarks are fine. On the x220, some are missing. Most notable is the first entry on the menu panel, "Smart Bookmarks". This is completely missing on the x220, but my favourite option on the desktop.

Help....

---

### Post by rickyLOLZ on 2012-01-18
> **xadder said:**
> 

xadder,

Please tell us your screen resolution so we can figure out what's wrong.

---

### Post by xadder on 2012-01-18
How do I get screen resolution? It has been years since I thought about that.

I doubt if that is the problem though. What seems to be happening is that the bookmarks at the top of each list (I have eg Smart bookmarks, news, Ubuntu and Free Software etc.) are missing. For the ones with many bookmarks, I see the bottom, looking fine, but not the top. (For example, I usually keep ubuntu forums at the top of the Ubuntu and Free Software menu), and the very short Smart bookmarks is empty. It is as though the first 10 or so entries are missing.

---

### Post by sudodus on 2012-01-18
Maybe there will be some inconsistency because you use the same file for both computers. It is possible to export the bookmarks as a html file from one computer to the other and import the bookmarks to firefox from that html file.

Of course, there will be problems of updating/syncing, so lets us hope someone comes in a shows how to do what you want!

Edit: use ```
xrandr
``` to get the screen resolution

---

### Post by xadder on 2012-01-18
I have been using the same system for years between several machines, but maybe something changed recently. I can start to look at other methods of syncing.

In case it was relevant, the output of xrandr is:

Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 277mm x 156mm
   1366x768       60.1*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9 


Thanks anyway,

---

### Post by xadder on 2012-01-19
Problem solved, kind-of.

I installed the Xmarks add-on on both computers. Now all looks well. Would have been nice to know what went wrong, but maybe Xmarks is more flexible anyway.

---

### Post by sudodus on 2012-01-20
> **xadder said:**
> Problem solved, kind-of.

I installed the Xmarks add-on on both computers. Now all looks well. Would have been nice to know what went wrong, but maybe Xmarks is more flexible anyway.
Thanks for sharing :-)

... and if you are satisfied, please mark this thread SOLVED

---

