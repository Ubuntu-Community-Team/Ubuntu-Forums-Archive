---
title: "Installing Flash on my New Ubuntu OS"
date: 2006-06-12
forum: General Help
---

### Post by konacoffeeguy on 2006-06-12
Hi, 
  I would like to install flash-nonfree on my New Ubuntu OS. This is for my parents and they are very skeptical but I convinced them to try a linux OS out as they have had problems with Viruses in the past. I found that when I type 

sudo apt-get install flashplugin-nonfree
sudo update-flashplugin


it say's the flashplugin-nonfree isn't there.
 How do I get around this problem? I'm not quite sure if I wrote the wrong thing in the terminal. 
 
Thanks , 
 Konacoffeeguy

---

### Post by tobiaspb on 2006-06-12
Hi.

You have to enable the extra repositories.

Open menu "System -> Administration -> Synaptic Package Manager"

In Synaptic click on menu "Settings -> Repositories"

Double click on Ubuntu 6.06 LTS (Binary) and click all four boxes under "Components" and click OK, then Close and Close again.

Now update by clicking the "Reload" button. Now you can install flash from either Synaptic or the command line as you described earlier.

Hope this helps. :-)

---

### Post by konacoffeeguy on 2006-06-12
Wow, 
   This worked great. Thank you very much for the help. 

 P.S. Somone should fix the wiki, it shows how to do it a diffrent way that doesn't work on the latest release.

---

