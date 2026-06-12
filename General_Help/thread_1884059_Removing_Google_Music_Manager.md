---
title: "Removing Google Music Manager"
date: 2011-11-20
forum: General Help
---

### Post by rob22941 on 2011-11-20
I need to remove Google Music Manager. I can't find where it was installed via .deb package. Anyone any ideas?

---

### Post by roger_1960 on 2011-11-20
Hi

Possibly in a hidden folder in your home folder?  Use CtrH to show hidden files/folders which are in format .name in nautilus

---

### Post by rob22941 on 2011-11-20
> **roger_1960 said:**
> Hi

Possibly in a hidden folder in your home folder?  Use CtrH to show hidden files/folders which are in format .name in nautilus

Looked in home folder and hidden files. Nothing in nautilus folder either.

---

### Post by philinux on 2011-11-20
> **rob22941 said:**
> I need to remove Google Music Manager. I can't find where it was installed via .deb package. Anyone any ideas?

How did you install it.

---

### Post by rob22941 on 2011-11-20
> **philinux said:**
> How did you install it.

Installed with a .deb package.

---

### Post by philinux on 2011-11-20
> **rob22941 said:**
> Installed with a .deb package.

Ok so using a terminal.

sudo apt-get purge insertnameofapplication

Or use synaptic package manager to do it.

---

### Post by rob22941 on 2011-11-20
> **philinux said:**
> Ok so using a terminal.

sudo apt-get purge insertnameofapplication

Or use synaptic package manager to do it.

Fixed purge worked. Took me 3 times but worked.

---

### Post by h.raed on 2012-01-28
> **philinux said:**
> Ok so using a terminal.

sudo apt-get purge insertnameofapplication

Or use synaptic package manager to do it.

I didn't found google music manger on package manager 
and what to put after purge on terminal because when i put google music manager i get 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package google
E: Unable to locate package music
E: Unable to locate package manager
please help me .thanks

---

### Post by kelbizzle on 2012-02-27
In the terminal run:
```
sudo apt-get purge google-musicmanager-beta
```

---

