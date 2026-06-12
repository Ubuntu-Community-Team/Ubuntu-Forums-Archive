---
title: "no nvidia kernel after update"
date: 2012-08-13
forum: General Help
---

### Post by Acradon on 2012-08-13
Hi there, 

I had a major issue installing my GeForce GT520 on Ubuntu 10.04 LTS initially. It took me all evening to find a suited walkthrough. However it worked in the end. Now suddenly maybe 2 month or so later I do an update through the update manager and ffffluppp again with the graphic card issues. So now it tells me that it can't load the nvidia kernel. WTF? how? WHY? Why ME?

Symptoms are that the resolution is not correct. I try to run the xconfig but it says that X is not turned on or so. Which is the same as last time, but the initial error before the login screen is different (i.e. can't run kernel) before it always just told me to restart X. Funny guy I say...tell me how? 
Unfortunately I can't find that old walktrhough again, but I remember that I had to virtually kill my whole graphics configuration and install new through terminal. This included loosing the gui. 

Maybe I don't have to go through this trauma again, but should I need to, is there someone who can walk me through it?

Acradon

---

### Post by Acradon on 2012-08-13
bump

---

### Post by Acradon on 2012-08-13
Seriously? nobody has an idea?

At this point I'll try anything. 

I tried to uninstall the nvidia-current driver and reinstalled the old (173) driver. This did not work. Same problem. I tried to just restart gdm in terminal. Nothing. My resolution is compressed and only fills half the screen, parts are chopped off. What is going on here? 

I have reinstalled the nvidia current driver and tried to remove the settings and blacklist novaeu and the gang as it was so nicely put in one of the forums here. nothing. Still that crappy kernel problem. It tells me that the kernel does not initialise and that I have to restart X. What a laugh, it doesn't do anything when I restart, just tells me to restart it. 
This update is starting to remind me more and more of running a windows system.... automatic update and then blue screen

---

### Post by Acradon on 2012-08-14
Ok

two days of foraging on the net in low res mode finally amounted to a solved problem. 

For anyone who might have the same problem, you will have to uninstall all and everything nvidia. I did that by uninstalling anything through synaptic. 

apparently alternatively in the terminal it should be

sudo apt-get remove --purge nvidia-*

that did something as in listing all the nvidia files and then ended in saying couldn't find nvidia-* package or something like that. 

I still had the driver file in my download folder you will have to download that through the nvidia site I believe.

Then I killed the GUI (this seems to be necessary as previously without this step it did not work. 

To kill the GUI press CTRL+ALT+F1

login as root

then

sudo /etc/init.d/gdm stop

I think, this might be overkill but it didn't harm anything


then cd inot the folder with the saved driver file in my case downloads folder

then

sudo sh ./NVIDIA-LinuxXXXXXXXXX.run  (enter specific file name)

then sudo reboot

that worked. Resolution back to normal'

Acradon

---

