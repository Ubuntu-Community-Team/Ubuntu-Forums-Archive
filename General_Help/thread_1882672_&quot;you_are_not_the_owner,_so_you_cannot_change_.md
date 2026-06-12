---
title: "&quot;you are not the owner, so you cannot change these permissions&quot;"
date: 2011-11-17
forum: General Help
---

### Post by ramus313 on 2011-11-17
so i have a My Passport external hard drive that i plugged into my desktop because i have some .mov files i need to transfer, but when i try to drag the folder over, i get a ""this destination is read only". when i check the properties, it says the owner is root and the group is root, and it gives me the message that i put as the title. I am very new to ubuntu so im kind of confused.. i tried switching to root via su root in the terminal but that doesnt really do anything. any help would be appreciated, thanks!

---

### Post by philinux on 2011-11-17
> **ramus313 said:**
> so i have a My Passport external hard drive that i plugged into my desktop because i have some .mov files i need to transfer, but when i try to drag the folder over, i get a ""this destination is read only". when i check the properties, it says the owner is root and the group is root, and it gives me the message that i put as the title. I am very new to ubuntu so im kind of confused.. i tried switching to root via su root in the terminal but that doesnt really do anything. any help would be appreciated, thanks!

Where are you dragging the file to?

---

### Post by ramus313 on 2011-11-17
> **philinux said:**
> Where are you dragging the file to?

i am dragging the file from my desktop, where i saved it, to the my passport folder

---

### Post by dFlyer on 2011-11-17
sudo chown -R youname:yourname /media/drivename

This will give you permission to the drive. If you wish to change it back:

sudo chown -R root:root /media/drivename

---

### Post by nothingspecial on 2011-11-17
What file system is the external drive formatted as?

---

### Post by ramus313 on 2011-11-17
Ok i tied the what you said 
DFlyer but it didnt work... i plugged it into  my mac, and changed the permision to eveyone: read and write from there, it was everyone: read only before. know when i look at the permissions it says the owner is 99-user #99 and the group is 99. i dont know what this means but it no longer says the owner is root...

---

