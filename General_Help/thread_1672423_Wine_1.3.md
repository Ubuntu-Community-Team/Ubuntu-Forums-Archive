---
title: "Wine 1.3"
date: 2011-01-20
forum: General Help
---

### Post by infectedbrain on 2011-01-20
I just followed the instructions on the winehq site to compile and install the wine 1.3 source but i cant get access to the program some help would be great.
 
thanks,
infectedbrain


EDIT: I got it there is no GUI for this one but okay.... sorry for stupid post

---

### Post by Conzo on 2011-01-20
> **infectedbrain said:**
> I just followed the instructions on the winehq site to compile and install the wine 1.3 source but i cant get access to the program some help would be great.

thanks,
infectedbrain



first you need to add software sources to your menu   

right click ubuntu icon in the corner ,,,,  click edit menus ,,,,srcoll down the left side till you see admin....  then on the right side  ( check mark ) software sources 

Close this down and open the program from admin area and add these to thrid party or other sources

Add one line at a time  
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) maverick main 
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) maverick main then you will need to add the ppa 

[http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x5A9A06AEF9CB8DB0](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x5A9A06AEF9CB8DB0)

Copy and paste the whole thing to Gedit and save as   WINE.KEY 

now under the software sources ( authentication  tab ) Import Key  ( the one you just saved ) 
then its off to the Synaptic package manager ( in the admin area ) search for wine and then Check mark the wine ver. you want and click apply   all restart the computer  WINE is a little pickie sometimes 


Conzo

---

