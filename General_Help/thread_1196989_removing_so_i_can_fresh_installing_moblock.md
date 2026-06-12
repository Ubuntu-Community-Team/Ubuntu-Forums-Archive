---
title: "removing so i can fresh installing moblock"
date: 2009-06-25
forum: General Help
---

### Post by kehon on 2009-06-25
i want to fresh install moblock so that i get the default prefrences i gave me a terminal screen to setup the options with before but everytime i do reinstall or remove and then add it it wont give me that screen again so i can choose the block list where is the conf file i need to remove so that i get this screen again i want it default because the other one blocks way to many connections it even blocks google

---

### Post by ajgreeny on 2009-06-25
You need to purge the application which will get rid of all the configs from the file system, but not from your /home.  If there are any hidden config files in /home you will need to remove them manually.  If you can see it in synaptic, even though you may not have installed it that way, you can choose "Completely remove" and that should do it.

---

### Post by kehon on 2009-06-25
thanks that worked i tried --purge before but this time i did sudo apt-get purge moblock and then did install moblock and it worked thanks

---

### Post by jre on 2009-06-26
Basically you have to do "sudo apt-get purge blockcontrol", because this package maintains the blocklist configuration.

Further you can always reconfigure a package without uninstalling:
sudo dpkg-reconfigure blockcontrol

Finally, you can use the GUI mobloquer to select lists or edit /etc/blockcontrol/blocklists.list

---

