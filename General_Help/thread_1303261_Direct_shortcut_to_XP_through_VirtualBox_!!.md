---
title: "Direct shortcut to XP through VirtualBox !!"
date: 2009-10-28
forum: General Help
---

### Post by chinmaya_n on 2009-10-28
Hello !

I know it is a silly question to discuss but i could not resist myself asking this!!
I 've WinXP installed as a guest OS in virtual-box. What I need is to start XP whenever i needed in single click or through a launcher etc.,
What generally i do is:
1.Start Virtual Box then
2.Start the XP machine! (Which opens in another window)
3.Close the Virtual Box window

I don't need all this mess! I just want a single icon or short cut or a launcher to directly start the XP....
I know the question shows my laziness but Its interesting to me

**Edit:** Is there any possibility to do that?
Does anyone ever thought ab't this?

---

### Post by The Cog on 2009-10-28
It's in the virtualbox manual, available form their website. There is a command-line launcher - vboxmanage or something like that. 

I guess you have to put the vboxmanage command into an application launcher - right-click the deskcop and create launcher, or right-click the gnome menu icon, choose edit and then add a new menu item.

---

### Post by chinmaya_n on 2009-10-28
Alright but what is the command?
Did u try it?

Edit: I refered the manual but i could not find it....! :(

---

### Post by alphaniner on 2009-10-28
This is the part where you do your own research.

---

### Post by chinmaya_n on 2009-10-28
> **alphaniner said:**
> This is the part where you do your own research.

Alright!! ;)

**Edit:** I found it ...!! It is here: [http://www.ubuntugeek.com/how-to-control-virtual-machines-virtualbox-using-vboxmanage.html](http://www.ubuntugeek.com/how-to-control-virtual-machines-virtualbox-using-vboxmanage.html)

In a nut shell it is like this ```
$ VBoxManage startvm "Windows XP"
```
We can place the name of the virtual machine which we want to start, in the quotes to start that one! 
Or we can place the UUID of that VM using the command ```
$ VBoxManage startvm *_UUID_*
```
We can get that UUID by using the command ***$ VBoxManage list vms***

Thanx to everyone for help!!

---

### Post by euroverclock on 2009-12-01
the exact command you have to put into the application launcher is : 

VBoxManage startvm "Windows xp"

REPLACE Windows xp with the correct name of the virtual machine

---

### Post by chinmaya_n on 2009-12-02
> **euroverclock said:**
> the exact command you have to put into the application launcher is : 

VBoxManage startvm "Windows xp"

REPLACE Windows xp with the correct name of the virtual machine

Thanks for the correction!
Actually i named my VM as "Windows XP"... ;)

```
VBoxManage startvm "<name of your virtual-machine>"
```

---

