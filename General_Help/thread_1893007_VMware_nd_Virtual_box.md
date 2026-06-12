---
title: "VMware nd Virtual box"
date: 2011-12-09
forum: General Help
---

### Post by gman3000000 on 2011-12-09
Hi Im trying to install VMware and virtualbox.
I have managed to install virtualbox and install winxp on a virtual machine.
However i can not get usb to work or linking to my back up partition.

lokked through help fine on web can seem to get either of these up and running please help.

I also want to try run VMware, I have download it from there site but have no Idead how to install it?

Many Thanks

---

### Post by BC59 on 2011-12-09
For the VirtualBox installation follow the instructions here:

[http://www.webupd8.org/2011/04/virtualbox-ubuntu-1104-natty-narwhal.html](http://www.webupd8.org/2011/04/virtualbox-ubuntu-1104-natty-narwhal.html)

To have USB working you need to download the Extension Pack described above.

For installing VMware simpler way is to run this in terminal:

```
sudo apt-get install open-vm-tools
```

---

### Post by gman3000000 on 2011-12-09
Yes have installed extensions. any idea what else to try?

Have just installed vm tools next step please?

---

### Post by haqking on 2011-12-09
you need extensions pack and in vboxusers group.



```
sudo usermod -a -G vboxusers username
```

---

### Post by haqking on 2011-12-09
> **gman3000000 said:**
> Yes have installed extensions. any idea what else to try?

Have just installed vm tools next step please?

you are talking about 2 different products here.

Virtualbox needs extensions pack and your user in vboxusers.

VM tools is for vmware.

Which one are you using or having problems with ?

---

### Post by gman3000000 on 2011-12-09
> **haqking said:**
> you need extensions pack and in vboxusers group.



```
sudo usermod -a -G vboxusers username
```

Say's user group does not exist

---

### Post by gman3000000 on 2011-12-09
> **haqking said:**
> you are talking about 2 different products here.

Virtualbox needs extensions pack and your user in vboxusers.

VM tools is for vmware.

Which one are you using or having problems with ?

both usb issue with vbox and trying insatll vmware

---

### Post by zeljkojagust on 2011-12-09
Maybe this will help you with VirtualBox: [https://zeljkojagust.wordpress.com/2011/09/04/virtualisation-with-virtualbox-preparing-the-environment/#more-168](https://zeljkojagust.wordpress.com/2011/09/04/virtualisation-with-virtualbox-preparing-the-environment/#more-168)
And as for VM Ware I don't know how smart is to run two virtualization hypervisors on the same machine. It's better for you to decide which one you prefer better and use only that one.

---

### Post by gman3000000 on 2011-12-09
I will but im trying to see which one I like

---

### Post by BC59 on 2011-12-09
> **gman3000000 said:**
> Say's user group does not exist

In place of *username* put your username.

My suggestion is to use VirtualBox is much easier to configure.

---

