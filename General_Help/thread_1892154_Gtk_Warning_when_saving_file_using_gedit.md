---
title: "Gtk_Warning when saving file using gedit"
date: 2011-12-07
forum: General Help
---

### Post by spindler on 2011-12-07
I just installed Ubuntu and I am attempting to edit the interface file located at  /etc/network

When I save the file I get the following message:

Gtk-WARNING **: Attempting to set the permissions of '/root/.local/share/recently-used.xbel', but failed:  No such file or directory

Any idea what this error is?

How do I fix it?

Thanks

Spindler

---

### Post by 2F4U on 2011-12-07
How do you start gedit?

---

### Post by seawolf167 on 2011-12-07
Assuming you started gedit through the terminal like so

```
gedit /path/to/file
```

Try instead

```
gksu gedit /path/to/file
```

---

### Post by spindler on 2011-12-07
using the following command did not make the error go away when I edited the file.


sudo gksu gedit /etc/network/interfaces

Why would I get this error on a standard install? 

I did not change anything in the install.  I just did the following:

1.  Install 11.04 followed the instruction.
2.  Updated the system using update manager
3.  Attempt to change the interfaces file so I can use a static IP address.

I should mention I moved back to 11.04  because of the network/internet connectivity issues with 11.10.  I have been working with 11.04 since it was released and reloaded it a couple of time since its release and I am happy with its stability. 

I ONLY STARTED TO GET THE GKT-WARNING ERROR RECENTLY.   Could there be something in the files that are downloaded when I update the system using update manager?

This error is present for both 11.04 and 11.10...... and is  BAD!    _Stability is everything.   _I need to feel confident that 11.04 will work for me.   migrating to 11.10 has been very costly to my organization.   

**Should I be worried about the stability of 11.04?**
[B]
What module do I need to install to get ride of the Gkt-WARNING errors?[/B]

---

