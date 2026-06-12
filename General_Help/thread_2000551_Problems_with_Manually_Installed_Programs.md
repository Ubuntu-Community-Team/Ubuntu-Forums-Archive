---
title: "Problems with Manually Installed Programs"
date: 2012-06-09
forum: General Help
---

### Post by WBMachinery on 2012-06-09
I recently install Maple 13 manually (without Software center, APT or Synaptics). The files were installed in /root. (The progam works great)

The program didn't create any shortcut and could only be started manually via a command.  

```
sudo ./root/maple13/bin/xmaple&
```


I've tried to lock it to the launcher.

I made an alias in the ~/.bash_aliases file with the same command but nothing happens when I run it. 

I've also tried changing the location of the files to 
```
/opt
```

and to 
 
```
/usr/local/bin
```

And changing the command in the alias,but the problem persist.

What else can I do.

---

