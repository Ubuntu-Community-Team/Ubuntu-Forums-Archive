---
title: "How to customize Update Manager ?"
date: 2010-07-22
forum: General Help
---

### Post by farmerjohn73 on 2010-07-22
I am new to Ubuntu.  I installed 10.04Lucid Lynx on my lenovo laptop with 80 GB, 1GB Ram.  My usage is very simple.  Browse Internet.  I did not install Open Office or Evolution.

My problem is, when the Update Manager shows the updates it shows updates for Open Office and Evolution and applications I did not install also.  

I want to disable that.  How do I do it?

Pls help.

---

### Post by lisati on 2010-07-22
I've edited the title of your thread: an "upload" isn't the same thing as an "update." :)

---

### Post by mcduck on 2010-07-22
> **farmerjohn73 said:**
> I am new to Ubuntu.  I installed 10.04Lucid Lynx on my lenovo laptop with 80 GB, 1GB Ram.  My usage is very simple.  Browse Internet.  I did not install Open Office or Evolution.

My problem is, when the Update Manager shows the updates it shows updates for Open Office and Evolution and applications I did not install also.  

I want to disable that.  How do I do it?

Pls help.

It shows updates for those applications because they are installed. It doesn't make difference if you install something or if it comes included by default, the package manager simply checks what packages you have on your computer and offers you updates for them when available.

If you don't want to use those applications, and don't want to update them, then your best option is to simply uninstall them (be careful when uninstalling Evolution, though, as some Evolution components are used by Gnome and removing those packages will break your desktop. The main application itself is safe to remove).

It *is* possible to freeze certain installed package to current version, which wold stop it from updating, but if you don't want the package in the first place then doing this really makes no sense. Especially when you remember that all the updates you get are security updates and fixes for more serious bugs...

---

### Post by farmerjohn73 on 2010-07-23
Sorry and thank u, lisati ! ;)

mcduck,  I uninstalled them but they are still showing in synaptic manager and when i click on them, context menu is offering to mark them for installation.  

I think if they dont exist in the synaptic manager itself, the update manager won't offer updates.  Am I right?

if so, How do i remove them from the synaptic manager list?

some body please help 'coz i am new to ubuntu and linux and can't understand which CAN be left without updating and which CANNOT be left without updating.

thanks in advance..

---

### Post by varunendra on 2010-07-23
Their appearance in synaptic (with blank check-box) means they are available in the repos and you can install them if you wish. To remove them from synaptic, you'll have to disable their relative repositories from 'Software Sources' (System>Administration>Software Sources). But this is not recommended because then all the other software associated with those repos will also disappear from synaptic list (only the installed ones will remain listed).

[Although you can do so if it helps your cause (I'm not sure if it will) and you are comfortable with it. You can always enable a repository to install a package from there and disable it again after installation]

---

### Post by mcduck on 2010-07-24
> **farmerjohn73 said:**
> Sorry and thank u, lisati ! ;)

mcduck,  I uninstalled them but they are still showing in synaptic manager and when i click on them, context menu is offering to mark them for installation.  

I think if they dont exist in the synaptic manager itself, the update manager won't offer updates.  Am I right?

if so, How do i remove them from the synaptic manager list?

some body please help 'coz i am new to ubuntu and linux and can't understand which CAN be left without updating and which CANNOT be left without updating.

thanks in advance..
Like the above post says, Synaptic shows all the available packages in all the repositories you have enabled. You only get updates for the ones that you have *installed*. So if Synaptic shows you that Evolution is available, and gives you option to install it, it sounds like it's not currently installed any more and thus you won't get updates for it either.

---

### Post by farmerjohn73 on 2010-07-28
Thank you friends !

I remember that the update manage is downloading the updates for the softwares not installed also (May be updating the repositories ! ).

I will check again and post the outcome here.

thanks a lot friends :smile:

---

