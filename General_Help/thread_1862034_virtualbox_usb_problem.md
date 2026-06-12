---
title: "virtualbox usb problem"
date: 2011-10-16
forum: General Help
---

### Post by kybush on 2011-10-16
Hi

I have just installed Virtualbox in 11.10 and when i go to settings i get this message  

VirtualBox is not currently allowed to access USB devices. You can change this by adding your user to the 'vboxusers' group. 

Where can i change this in 11.10


thanks

---

### Post by haqking on 2011-10-16
> **kybush said:**
> Hi

I have just installed Virtualbox in 11.10 and when i go to settings i get this message  

VirtualBox is not currently allowed to access USB devices. You can change this by adding your user to the 'vboxusers' group. 

Where can i change this in 11.10


thanks

go to terminal

```
sudo usermod -a -G vboxusers username 
```

where username means your username, make sure you have the extensions pack installed also

---

### Post by kybush on 2011-10-16
No it's not working still cannot connect USB drive

---

### Post by haqking on 2011-10-16
> **kybush said:**
> No it's not working still cannot connect USB drive

so youve added yourself to the group

connected the USB device, chose the device from the devices menu in the VM and it is not appearing ?

what is the error ?

and do you have the extensions pack installed

you need to be clearer, "it doesnt work" is fairly vague

---

### Post by kybush on 2011-10-16
Sorry it works i have just restarted my comp and it works


thank you :D

---

### Post by haqking on 2011-10-16
> **kybush said:**
> Sorry it works i have just restarted my comp and it works


thank you :D

ok cool, no worries.

Remember to mark the thread as solved using thread tools menu.

Cheers

---

