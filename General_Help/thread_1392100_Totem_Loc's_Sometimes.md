---
title: "Totem Loc's Sometimes"
date: 2010-01-27
forum: General Help
---

### Post by Tourdog on 2010-01-27
I have Movie Player (Totem) and as an alternate VLC.  Both will play  store bought encrypted DVDs very well etc.

   However, Movie Player when on "YouTube" for instance will frequently  flag the search operation with one/ two of the following:

"Error looking up URI/ cannot resolve host name"  or

"Error looking up Video URI"
automount failed:  mount point for
org.gtk.vfs; mountpoint.http already running"  or

"An error occurred
location not found"

It is difficult to clear and unstick these red flags.

Audio from Rhythmbox Music Player is awesome.

What dependent file or plug-in am I lacking or need to delete...... to  fix?  :sad:

TIA !!!

---

### Post by dpm4 on 2010-06-20
If u have swf player plugin installed for firefox, uninstall it.I tried it. it worked.

---

### Post by kc8kod on 2010-07-27
I had the exact same problem, however I did not uninstall anything.

My successful fix was to install the package swfdec-gnome through Synaptic. Works perfect for me now.

---

### Post by x-shaney-x on 2010-08-04
Same problem here too.
Installing swfdec-gnome got around that error but now I get ```
Could not open location; you might not have permission to open the file.
```

I hate to say it but seems another example of a lucid app being incomplete or not fully working.
If they are going to have a youtube plugin in totem it should have the dependencies it needs or leave out the plugin altogether.  Unless it needs some kind of restricted library then it should offer up the option of installing anything else needed once the plugin is enabled.

I remember an error in mandriva related to the totem youtube plugin and I can't remember if it was the same error but the solution was to install something jpeg related.

---

