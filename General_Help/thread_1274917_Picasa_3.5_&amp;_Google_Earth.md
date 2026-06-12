---
title: "Picasa 3.5 &amp; Google Earth"
date: 2009-09-25
forum: General Help
---

### Post by gewitty on 2009-09-25
Just installed Picasa 3.5, which runs happily under Wine in Jaunty. The new facial recognition feature is awesome. It's accuracy is amazing, even with poor quality images.

However, the Geotagging feature is giving me a problem since Picasa doesn't seem to recognise that I already have Google Earth installed and keeps asking me to install it.

Can anyone tell me how I can make the association, so that Picasa can use GE?

A second problem has also manifested itself: When I click on the 'Places' button (bottom right), it seems to try to load a Google map. This doesn't happen and the whole application locks up. I can only stop it by forcing it to quit, but when I restart it, it just goes back to trying to load the map and locks up again.

I'm guessing that this is something to do with the long-running problem that I and many others have had with Google maps, which often fail to load in Firefox and other browsers. The trouble here is that in failing to load, the map feature completely screws up Picasa.

What I haven't figured out yet, is how I can restart Picasa without it going straight back to trying to load a map.

---

### Post by archiesteel on 2009-09-25
> **gewitty said:**
> A second problem has also manifested itself: When I click on the 'Places' button (bottom right), it seems to try to load a Google map. This doesn't happen and the whole application locks up. I can only stop it by forcing it to quit, but when I restart it, it just goes back to trying to load the map and locks up again.

The only way I found out of this was to start regedit (in the same WINE environment Picasa is installed in), go to HKEY_USERS, then select the correct user folder (mine was called S-1-5-4, the only other folder was .Default), then Software -> Google -> Picasa -> Picasa2 -> Preferences and make sure the active_metadata_tab key is empty.

This should allow you to restart Picasa without it trying to reload Google Maps (though it obviously won't fix the actual bug, at least you'll be able to use the program...)

---

### Post by jakobb on 2009-10-14
I have installed Picasa 3.5 in the wine environment of ies4linux,
and the maps are working fine.
Facebook uploader is also working, in this environment.

I don't know what to do in order to make GE work, so I'm Listning.

---

