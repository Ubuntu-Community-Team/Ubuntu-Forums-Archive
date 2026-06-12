---
title: "How do you assign key function in Ubuntu?"
date: 2012-08-23
forum: General Help
---

### Post by oxf on 2012-08-23
I need to assign a different function to one of my keys. I was led to believe that they kep map if thats what it is is in a file  in folder  /etc/x11/xkb.  Howiever, that folder is empty.
Anyway how to I determin which keys have what function?

Thanks
Veronica

---

### Post by oxf on 2012-08-23
Let me re-phrase this..
Somewhere in the startup process there must be a file that sets the Keymap, i.e. which keys do what function. I presume this can be edited. Where is this file locateda? and how do I edit it?

---

### Post by drmrgd on 2012-08-23
Are you talking about keyboard  shortcuts (like Ctrl + <somthing> = open a new window) or you want to reassign a key to a different task (like Page Up now equals SysRq)?  I'm on Kubuntu, and it's a little different.  From my old Ubuntu days, I believe this can be changed with gconf-editor and / or dconf-editor (a quick Google search on this prior to posting was unclear as it seems there is a transition going on between the two currrently).  Have a look and see if you can change what you need with either of those tools.

---

### Post by oxf on 2012-08-23
> **drmrgd said:**
> Are you talking about keyboard  shortcuts (like Ctrl + <somthing> = open a new window) or you want to reassign a key to a different task (like Page Up now equals SysRq)?  I'm on Kubuntu, and it's a little different.  From my old Ubuntu days, I believe this can be changed with gconf-editor and / or dconf-editor (a quick Google search on this prior to posting was unclear as it seems there is a transition going on between the two currrently).  Have a look and see if you can change what you need with either of those tools.

No I'm not talking short cuts. I need to completely reasign the key to a different task.

---

### Post by drmrgd on 2012-08-23
> **oxf said:**
> No I'm not talking short cuts. I need to completely reasign the key to a different task.

I think it's the same either way from what I was reading.  It seems the building keyboard remap tool is not working or buggy, and people are using dconf-editor or gconf-editor as a workaround.  Would that suit you?

---

### Post by oxf on 2012-08-23
> **drmrgd said:**
> I think it's the same either way from what I was reading.  It seems the building keyboard remap tool is not working or buggy, and people are using dconf-editor or gconf-editor as a workaround.  Would that suit you?

Thanks

I think so. I can launch gconf-editor but once open I'm lost as to finding where I edit key assignments?

Veronica

---

### Post by oxf on 2012-08-24
bmp

---

### Post by oxf on 2012-08-26
bmp

---

