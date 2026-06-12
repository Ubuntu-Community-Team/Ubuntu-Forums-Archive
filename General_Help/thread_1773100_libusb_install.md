---
title: "libusb install?"
date: 2011-06-01
forum: General Help
---

### Post by orrymr on 2011-06-01
Hi all,
I'm trying to install libusb. I've downloaded a file from [http://sourceforge.net/projects/libusb/files/libusb-0.1%20%28LEGACY%29/0.1.12/](http://sourceforge.net/projects/libusb/files/libusb-0.1%20%28LEGACY%29/0.1.12/)
I've unzipped the file; the folder's on my desktop. I've tried to install this, but I'm not sure how. Under installation it says: See the file 'INSTALL'. 
There are a few files that start with this term: INSTALL.libusb, INSTALL.libusb.in and install-sh. The first two appear to be the same, while the latter appears to be some sort of program. When I double click it, I get a few options, including "run". I assumed this was the correct way to install the program, but when I hit run, nothing happens. I've displayed this file, but this gives me no additional information... I've tried running it in terminal: nothing. Maybe it has installed, and I just don't know it :/ How would I even check if it's installed? 


(I'm only installing libusb because I need it for something else)

:confused:

---

### Post by linuxinstalledfromhdd on 2011-06-01
You can try enabling backports in synaptic and reload, and then simply try a search for the package you want with synaptic search?

 Did that help?

Don't forget to unselect backports and reload after you get it installed.

---

### Post by orrymr on 2011-06-01
I don't know what that means...  :frown:

---

### Post by linuxinstalledfromhdd on 2011-06-01
That's ok.

What you have done is download a package directly and tried to install it. 

You don't have to do it that way with Ubuntu.

In your Terminal enter this command:

sudo synaptic

This will open synaptic package manager.  Do a search for the package you want this way, if you find it, right click to install it. 

Try this and let me know if this helped. :popcorn:

---

### Post by orrymr on 2011-06-01
But if I've already got the package downloaded, is there no way to install it, without having to re-download and installing through synaptic?

I did a search for libusb on Synaptic and got a whole bunch of results; I'm not sure which is the one I want. I'm pretty sure that the package I've downloaded has all the stuff I need, so I'd rather install that one.

---

### Post by linuxinstalledfromhdd on 2011-06-01
Ok BUMP

---

