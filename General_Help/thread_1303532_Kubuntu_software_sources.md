---
title: "Kubuntu software sources?"
date: 2009-10-28
forum: General Help
---

### Post by tuahaa on 2009-10-28
Well, I installed KDE on my Gnome desktop and I want the software sources for Kubuntu. Can anybody tell me which ones I need to add? Or does Kubuntu and Ubuntu share common updates?

---

### Post by hwttdz on 2009-10-28
The kubuntu packages should be in the ubuntu repositories.  So I don't think you have anything to worry about.  One thing to do is open up synaptic and instead of using main server, or server for the us (or other location) try finding the best server, this spreads out load which is better for the servers, and makes updates faster, which is better for you.

---

### Post by XDevHald on 2009-10-28
This can be found in your sources.list. Use the following command below to execute your file to view these sources IF you're running Kubuntu. If you're not then it will only show Ubuntu's software sources list. Check your **Software Sources** application in **System** > **Administration** > **Software Sources** (If you're running Karmic). If not then check your **Update Manager** in **Settings** and choose your sources you want to use.

```
sudo gedit /etc/apt/sources.list
```

---

### Post by philinux on 2009-10-28
Should be gksudo gedit .....

---

### Post by XDevHald on 2009-10-28
Using gksudo on a text file is not needed. This is ONLY to be used for graphical applications, not text files. Recommended is sudo gedit /file/location/to/edit

---

### Post by tuahaa on 2009-10-28
Don't worry, I switched back to Gnome now. I want my system bugfree and fast.

Now, I need to see how I get the KDE splash screen on Gnome =P

---

### Post by XDevHald on 2009-10-28
Glad to have you back on Gnome. Yeah, adding KDE splash to a Gnome desktop is not really a winner in my eyes hehe. Enjoy your desktop!

---

