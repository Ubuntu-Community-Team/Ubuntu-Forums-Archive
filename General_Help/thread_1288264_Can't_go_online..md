---
title: "Can't go online."
date: 2009-10-11
forum: General Help
---

### Post by Rodart on 2009-10-11
hi, i wanted to test linux (never used it before) so i downloaded Ubuntu 9.04 desktop i386 , i installed it on virtual pc, using my ethernet nvidia nforce as the ethernet adapter, the same i'm using in my windows vista. So, I installed Ubuntu , it's working great, but i can't manage it to go online or to install the soundcard drivers, the drivers cd i have only has drivers for Fedora , RHEL4.0 and SUSE 10.1, my internet connection comes by a Motorola surfboard modem as local  or something like that,i don't know if this is due that i'm using Virtual pc, or because of my internet connection, so if anyone can help me i'll be glad :D.
 
Thanks :D
 
Rodart.

---

### Post by davidryderuk on 2009-10-11
The sound and ethernet issues are probably due to virtual pc's configuration. I'm afraid I can't help you with the issue though as I've only ever used Virtual-box, a free alternative. 

The only thing I can suggest is that maybe Ubuntu will work better under Virtual-box.

[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

Edit:

Alternatively you could try running the following command in Ubuntu's terminal (Applications > Accessories > Terminal)

```
sudo lshw -short
```

If virtual pc is configured properly then you should see devices listed next to the network and multimedia entries. In any case the output from that command will help people on this forum diagnose your problem better.

---

### Post by davidryderuk on 2009-10-11
By the way if you decide to follow the instructions I linked to before and use virtual box, you need to enable the audio manually. This is relatively simple. 

1. Click on settings.

2. In the new window that comes up click on Audio.

3. Tick the box that says "Enable Audio"

The ethernet should work without changing anything, as long as you reboot windows after installing virtual box.

---

### Post by Rodart on 2009-10-11
> **davidryderuk said:**
> The sound and ethernet issues are probably due to virtual pc's configuration. I'm afraid I can't help you with the issue though as I've only ever used Virtual-box, a free alternative. 
 
The only thing I can suggest is that maybe Ubuntu will work better under Virtual-box.
 
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
 
Edit:
 
Alternatively you could try running the following command in Ubuntu's terminal (Applications > Accessories > Terminal)
 
```
sudo lshw -short
```
 
If virtual pc is configured properly then you should see devices listed next to the network and multimedia entries. In any case the output from that command will help people on this forum diagnose your problem better.
 
i tryed the terminal thing, but there's some kind of problem because it tells me that the network adapter (eth0) is a DECchip 21140 fasternet. And it's supposed to be a nforce, i will try with virtual box, and then with the ubuntu live cd.
thanks.
 
Rodart.

---

### Post by davidryderuk on 2009-10-11
That's normal actually. Virtual pc goes through windows to get to the network adaptor, so the adaptor you see in Linux isn't actually the real ethernet device but a virtual one.

I still think that running Linux on virtual box will be easier and slightly faster. However I just found a guide to getting Linux running on virtual pc that I though I should mention.

[http://arcanecode.com/2008/04/24/installing-ubuntu-804-under-microsoft-virtual-pc-2007/](http://arcanecode.com/2008/04/24/installing-ubuntu-804-under-microsoft-virtual-pc-2007/)

It describes how to get your Internet working. There's also a comment on how to get the sound working, but since it's easy to miss I'll summarise it here. 

1. Open the terminal and type the following:

```
gksudo gedit /etc/modules
```

2. In the subsequent text file add "snd-sb16" to the bottom of the file, on a new line.

3. Reboot the machine and hopefully your sound should now work.

4. In order to get the network adaptor to work, you should be able to just right click on the network icon in the top right hand corner and click on the "Enable Networking" icon.

---

### Post by Rodart on 2009-10-11
i tested ubuntu with another pc , wich it has a dsl connection, I tryed the live cd and it works perfectly , i'm typing this from this pc, i wan't to install this ubunto in my home pc, but i don't know if it will be able to get online, I will try the live cd at home, my audio is from the on board asus-m2nx plus, hd audio, but from this pc, ubuntu recognised the audio device, i'm comfussed about this :confused:. I can't install ubuntu in my home pc untill i'm sure it will work online :/.

Thanks ,

Rodart.

---

### Post by Rodart on 2009-10-12
Ok, it was because of virtual pc, I tryed the live cd and it worked perfectly online.

Thanks for your help :).

Rodart.

---

### Post by davidryderuk on 2009-10-12
Okay,
If your considering installing ubuntu on your computer you should look at wubi. It allows you to install Ubuntu on your windows drive, and thus avoids having to repartition your computer. It also makes Ubuntu easier to remove. 

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Have you tried the instructions I posted above for virtual pc? 

> I just found a guide to getting Linux running on virtual pc that I though I should mention.

[http://arcanecode.com/2008/04/24/ins...rtual-pc-2007/](http://arcanecode.com/2008/04/24/ins...rtual-pc-2007/)

It describes how to get your Internet working. There's also a comment on how to get the sound working, but since it's easy to miss I'll summarise it here.

1. Open the terminal and type the following:

Code:

gksudo gedit /etc/modules

2. In the subsequent text file add "snd-sb16" to the bottom of the file, on a new line.

3. Reboot the machine and hopefully your sound should now work.

4. In order to get the network adaptor to work, you should be able to just right click on the network icon in the top right hand corner and click on the "Enable Networking" icon.

---

