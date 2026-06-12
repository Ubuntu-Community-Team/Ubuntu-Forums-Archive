---
title: "Software error,install and uninstall"
date: 2009-10-20
forum: General Help
---

### Post by maxenzo2 on 2009-10-20
Hi guys,i'm new on the forum,and new on linux.But i have a big question(well its big for me),this i will talk about its just an example.
I have installed virtual box from a ubuntu .deb,but some days after,the icons on the apps menu vanished,so i have uninstalled using "sudo apt-get update" and "$sudo apt-get remove virtualbox-3.0",he started to uninstall and all,but when was finished,i installed it again from a new downloaded .deb,but the programs continued to have the same bug,how can it have the same bug if its a new install? this happened with amarok2(not the same bug as vbox,but this one i installed and removed with synaptics).
So this is the question,since ubuntu dont have a resgistry like windows to give problems,what is creating this problem? 
this happends in all the software,its like if linux remenbers how the software was when uninstalled,and when installed again the program continues with the same bug.

---

### Post by ajgreeny on 2009-10-20
You probably need to use ```
sudo apt-get --purge remove packagename
```As you say there is no registry in ubuntu, and all the configurations for applications are stored in plain text files either in your home folder, or in various file system folders such as /etc, /usr.  In order to completely remove configuration you will need to use the purge command shown, or synaptic "Remove completely", and then delete or rename the hidden folders that relate to those apps in your home folder.  These all begin with a . which means you may not even know they are there.  If you can't see any use the Edit ->Show hidden files (Ctrl+H) and they will all appear in nautilus.

I hope this may help you, but of course it will depend on the reason for the problem appearing in the first place.

---

### Post by meindian523 on 2009-10-20
How exactly do you mean "the icons vanished"?

---

### Post by maxenzo2 on 2009-10-20
> **meindian523 said:**
> How exactly do you mean "the icons vanished"?
I installed the program,and the icon to launch virtualbox was on the apps,i used virtualbox and all,some days later i was going to launch virtualbox to install pc-bsd,and the icon wasn' t there,not even on the configuration of the menu.So i opened the file system,and i have made a search,and it found the launcher(and all the other files from vitualbox),and i launched it,and it have give me an error(i dont remenber what was writen),so i uninstalled,and installed it again,but then he continued in the same way,with the same error,and it doesn't create a laucher icon on the apps.But this doenst happend just to this applications,it happends to all of them(if it has some kind of problem),thats what i whant to understand.Because when that happends on windows(when some app gets corrupted),i go to registry or the app folder,and i just need to erase the garbage the program left behind,and its done i make a fresh install and the app runs agains as before.
Thats what i whant to know,i whant to know how to make a fresh install,like if the app was never installed on linux before,so it can work well again.

---

