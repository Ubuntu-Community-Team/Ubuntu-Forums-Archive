---
title: "How to upgrade virtual box from 4.1 to 4.2"
date: 2012-10-01
forum: General Help
---

### Post by achu91 on 2012-10-01
I am a novice ubuntu user ,please guide me on how to upgrade virtual box from 4.1 to 4.2.I am using ubuntu 12.04.

---

### Post by leclerc65 on 2012-10-02
You download the new Deb and install it. Also remove the Extension Pack then add the new one. Normally the update is very reliable, but to play safe export the appliance just in case. It's the best feature of Vbox. I replace Ubuntu 11.04 with Lubuntu 12.04, install new Vbox, import the appliance and voila, my XP is up and working right away. Don't forget to redo the Guest Addition.

---

### Post by achu91 on 2012-10-02
Thanks boss.First i tried your method by unistalling through software manager.but it didnt not succesd.Then i was able to unustall fully by using terminal and the following commands

1 for unistalling
sudo dpkg -r virt*
**[COLOR=#ff6600][/COLOR]**
then for installing
sudo dpkg -i package.deb  //where pakage is the name of the downloaded virtual box file.


Thanks for replying and sorry for posting this silly question.

---

### Post by jeremyjjbrown on 2012-11-19
> **achu91 said:**
> 
Thanks for replying and sorry for posting this silly question.

It's not that silly at all. I've been using ubuntu for years and your post reminded me how to remove an old .deb

However, I would strongly reccomend adding a few more characters before the wildcard

sudo dpkg -r virtualbox*

Lest you inadvertently remove something else you want, like virtual-machine-manager.

---

