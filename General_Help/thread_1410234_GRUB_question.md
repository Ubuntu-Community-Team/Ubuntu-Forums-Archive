---
title: "GRUB question"
date: 2010-02-18
forum: General Help
---

### Post by Sirsteveo on 2010-02-18
Im very new to linux just put it on my cpu with dual boot. Im not quite sure how to ask this question but i hope someone understands and can help. When i boot up my cpu GRUB comes up as normal it says
Ubuntu, Linux 2.6.31-19-generic
Ubuntu, Linux 2.6.31-19-generic (recovery mode)
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
Windows 7 (Loader)
What is Ubuntu, Linux 2.6.31-14-generic, Ubuntu, Linux 2.6.31-14-generic (recovery mode) i have not tryed to boot to it yet but does this mean I have 3 OS on my computer i didnt know i installed ubuntu twice, or even how i installed it twice all i did was put disc in followed steps but it put 2 of them on there? If there is two of them how do i get that seccond one off i dont need.

---

### Post by pastalavista on 2010-02-18
Whenever the Linux kernel is updated in Ubuntu, the old kernel is not removed in case the new kernel has any bugs or incompatibilities with your system. You can remove older kernels after you're sure the new one is working OK.

Open Synaptic Package manager and search for "linux-image" and completely remove the older ones. It will also remove the entry from grub.

---

### Post by Sirsteveo on 2010-02-18
I can highlight them but it wont let me remove them. Will only let me mark for installation not mark for removal.

---

### Post by Sirsteveo on 2010-02-18
and would i wanna delete everything that is not installed?

---

### Post by pastalavista on 2010-02-18
In Synaptic, packages with a green box are installed and an empty, white box not installed. Try selecting the 'Status' option in the bottom-left panel and "Installed" in the top left. You shouldn't be able to remove a package that isn't installed, or install one that is already installed (except reinstall). Right-click an item to see all your options.

---

### Post by Sirsteveo on 2010-02-18
nope still wont let me delete

---

### Post by r_s on 2010-02-18
If it is not installed you can update your grub and see the change( but it updates the grub automatically, after you remove any older kernels,)

---

### Post by Sirsteveo on 2010-02-18
You just saying i need to update grub? I just wanna delete the old kernals so they dont show up.

---

### Post by r_s on 2010-02-18
to delete the older kernels you need to follow the procedure mentioned by *pastalavista, *by deleting the older kernels using synaptic package manager and it will itself update your grub to remove those entries.

---

### Post by Sirsteveo on 2010-02-18
Yea, i understand that but in  synaptic package manager it will not allow me to delete anything from it when I highlight the ones to delete it only says highlight to install not highlight to delete

---

### Post by r_s on 2010-02-18
[http://www.youtube.com/watch?v=ilNRVgBl27w](http://www.youtube.com/watch?v=ilNRVgBl27w)
well just have a look at this , and reply if you are facing a problem

---

### Post by Sirsteveo on 2010-02-18
yea, i just cant click and mark for complete removal. The option is grey and cannot be clicked on.

---

### Post by r_s on 2010-02-19
is the option being shown for a green box.

---

### Post by royale1223 on 2010-02-19
worked for me..

---

