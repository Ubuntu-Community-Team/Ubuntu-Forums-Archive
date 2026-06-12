---
title: "graphic card drivers don't work"
date: 2011-09-04
forum: General Help
---

### Post by Duty on 2011-09-04
for gaming didn't really work with most of the games on my notebook (15.4" Samsung R510-Aura-T5750 Danio), i've been trying to install a new driver for my graphic card (NVIDIA GeForce 9200M GS) but both of the ones in system --> system management --> additional drivers don't work, they just make my toolbar and so on disappear... :(
has anyone an idea, what to do? :confused:

---

### Post by blitzit on 2011-09-04
First download the latest drivers for your piece from NVIDIA's site. (For India, the site is [http://www.nvidia.co.in/Download/index.aspx?lang=en-in](http://www.nvidia.co.in/Download/index.aspx?lang=en-in). Search the one for your country.) Either note down or remember where you kept the file, you will need it later. It's best if you leave it in your home folder.

After having done that, you will need to:
[LIST=1]
[*]Uninstall all the NVIDIA stuff that came with ubuntu (Do this by: sudo apt-get remove --purge nvidia*)
[*]Blacklisting some stuff in blacklist.conf (Make the following changes in /etc/modprobe.d/blacklist.conf)
[/LIST]

Add the following lines to /etc/modprobe.d/blacklist.conf
```
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

```

Now reboot your machine. It is possible that your ubuntu won't boot properly complaining about graphics drivers. Don't panic. 

There are now 2 chances.

Possibility 1: Your x-screen doesn't come up at all.
Log into the command prompt and run the driver (which you should have left in your home folder or some other folder which you remember/have noted down)
```
sudo sh ./NVIDIA-Linux-x86-xxx.xx.xx.run
```

Do a reboot.
```
sudo reboot
```


Possibility 2: Your x-screen comes up.
Close your x-server by doing this:
```
sudo service gdm stop
```

Your screen will go blank because you just stopped your screen managing service. Open a terminal by doing Alt+F2.

Then run the driver software:
```
sudo sh ./NVIDIA-Linux-x86-xxx.xx.xx.run
```

Do a reboot.
```
sudo reboot
```

That should do it for you.

---

