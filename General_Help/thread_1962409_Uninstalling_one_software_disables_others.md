---
title: "Uninstalling one software disables others?"
date: 2012-04-21
forum: General Help
---

### Post by Undefine on 2012-04-21
I am using ubuntu 11.10. I am trying to uninstall few software's which I will never need. 
I tried removing one games and it said "To remove xx games xx items have to be removed. I clicked yes and after that I lot of games were deleted. :confused:

How can I remove one software and make sure other similar software which came within the same package doesnt gets deleted.

I use XFCE 4.8 as my DE now, I want to remove a CD and DVD burning tool named Xfburn that came along with other goodies(extra stuff with xfce), it says "To remove Xfburn, these items must be removed as well". --"Enhancetments for the xfce4 desktop environment" 

Should I use "sudo apt-get remove Xfburn" and it will only remove this software?

Thanks for your replies.

---

### Post by Metul Burr on 2012-04-21
best to delete from where you installed it from soft.center or terminal. But the terminal will not accidently delete unintended things

will delete
```
sudo apt-get remove Xfburn
```

delete and get rid of configuration files
```
sudo apt-get purge Xfburn
```

---

### Post by Undefine on 2012-04-21
> **Metul Burr said:**
> best to delete from where you installed it from soft.center or terminal. But the terminal will not accidently delete unintended things

will delete
```
sudo apt-get remove Xfburn
```

delete and get rid of configuration files
```
sudo apt-get purge Xfburn
```

> undefined@undefine:~$ sudo apt-get remove xfburn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  feh giblib1 xfonts-terminus
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  xfburn xfce4-goodies
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 1,995 kB disk space will be freed.
Do you want to continue [Y/n]? 

Should I do it? Your suggestion is what?

---

### Post by Metul Burr on 2012-04-21
you can continue and and delete both and then download the xfce4-goodies from synaptic
```
sudo synaptic
```

---

