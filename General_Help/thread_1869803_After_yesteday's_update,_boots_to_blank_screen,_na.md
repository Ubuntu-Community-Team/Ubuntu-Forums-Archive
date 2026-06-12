---
title: "After yesteday's update, boots to blank screen, nautilus stuck"
date: 2011-10-26
forum: General Help
---

### Post by JavaQueen on 2011-10-26
I encountered a problem after yesterday's update. I'm running Ubuntu 10.10 and  after the update, a screen appeared telling me Nautilus needs  to restart to complete updates. Nothing happened when I clicked restart in that update  window (window stayed on screen), so I restarted my laptop. Upon reboot, I got a blank screen after the text Ubuntu 10.10. I  did try to boot from the latest recovery option...same blank screen. I  am, however, able to boot in low graphics mode. When I was able to do  this, the same "Nautilus needs to restart to complete updates" window  appeared. Again, nothing happened when I clicked the restart button in the window. Suggestions?Thanks so much for any help.

---

### Post by raja.genupula on 2011-10-26
actually while my updates are installing once i have lost power and then system gone off.

when i restart it,its not having proper look and extra stuff.

i again did updating 
sudo apt-get update
sudo apt-get upgrade

its suggested me to do sudo dpkg-reconfigure -a or something else i didn't remember properly but i am sure its gonna suggest something to do and its gonna make it .

all the best

---

### Post by JavaQueen on 2011-10-26
Raja,

Thank you so much for your response. I did as you suggested. I no longer get the "Nautilus needs to restart" window. However, my laptop still won't reboot. After the text Ubuntu 10.10 flashes, my laptop goes to a blank screen. I'm open to any other suggestions.

Thanks,
Angela

---

### Post by raja.genupula on 2011-10-26
hi man 

do this

```
sudo apt-get install --reinstall gnome-desktop
```

all the best.

---

### Post by JavaQueen on 2011-10-26
Ok, I did that. Results are:
E: Unable to locate package gnome-desktop

---

### Post by JavaQueen on 2011-10-27
I've tried:
sudo apt-get update
sudo apt-get upgrade

sudo apt-get clean

The only way I can boot up my computer is to go into the grub menu, choose the latest recovery option the select failsafe graphics mode. I have no idea what happened. My computer worked beautifully until the latest update. Any suggestions?

---

### Post by flipper T on 2011-10-27
probably a graphics driver issue.

in failsafe mode can you go to additional drivers & reinstall driver ?

if so, i would give this a go.

if you have a number of options here, try each driver in turn, deactivating the previous one as you go.

good luck.

---

### Post by raja.genupula on 2011-10-27
```
sudo apt-get remove --purge nautilus
sudo apt-get autoclean
sudo apt-get install nautilus
```

all the best

---

### Post by JavaQueen on 2011-10-27
> **flipper T said:**
> probably a graphics driver issue.

in failsafe mode can you go to additional drivers & reinstall driver ?

if so, i would give this a go.

if you have a number of options here, try each driver in turn, deactivating the previous one as you go.

good luck.
Thank you, thank you, thank you!!!!!  That was exactly the problem! I didn't realize my graphics driver was out of date. Uninstalled the old one, downloaded and installed the new one and now everything works great! Thank you so much for taking the time to suggest this. Of all the things I was thinking it could be, the graphics driver never occurred to me. Have a fantastic day!

---

### Post by flipper T on 2011-10-27
same thing happened to me 2 weeks ago :)

---

