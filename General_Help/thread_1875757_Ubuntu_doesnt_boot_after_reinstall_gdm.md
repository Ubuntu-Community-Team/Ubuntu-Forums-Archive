---
title: "Ubuntu doesnt boot after reinstall gdm"
date: 2011-11-05
forum: General Help
---

### Post by karol4722 on 2011-11-05
Hey
Since I've upgraded my ubuntu 11.04 to 11.10 I have few problems.
1. Everytime on boot i see 'Checking for network configuration' and 'boot without full network configuration' I've tried lots of solutions but nothing works ;x
2. I cant shut down my ubuntu, it stucks on 'checking unattended-upgrades'
3. I've tried yesterday **[this]("http://www.totalcomputersusa.com/2011/10/ubuntu-11-10-booting-system-without-full-network-configuration/") **solution so I removed network-manager, lightdm and gdm and reinstalled this. After reinstall, ubuntu doesnt boot. It stucks on 'Stopping System V runlevel compatibility'
What should I do?

btw sorry for my english :)

---

### Post by linuxaddix on 2011-11-05
burn an iso of 11.10 and do a fresh install.after the install log in log out then log back in.

---

### Post by LinuxFan999 on 2011-11-05
It looks like your install is completely broken. The only thing you can do is reinstall Ubuntu. You can use your copy of 11.04, or, if you have access to another computer, you could download a copy of 11.10 and use that instead.

---

### Post by karol4722 on 2011-11-05
I have access to this computer. I finally can boot it. I must press ctrl + alt + f1 and log on root and type startx then unity in terminal and it works. How can i fix it? Reinstall ubuntu is really  only thing I can do?

btw after upgrade to 11.10 everything worked good excepting long booting (checking for network configuration bla bla) yesterday i reinstalled gdm and everything crashed ;x

---

### Post by ajgreeny on 2011-11-05
> **karol4722 said:**
> I have access to this computer. I finally can boot it. I must press ctrl + alt + f1 and log on root and type startx then unity in terminal and it works. How can i fix it? Reinstall ubuntu is really  only thing I can do?

btw after upgrade to 11.10 everything worked good excepting long booting (checking for network configuration bla bla) yesterday i reinstalled gdm and everything crashed ;x
Have you enabled the root account, which is normally disabled in Ubuntu?  Ctrl+Alt+F1 does not give you the option of a root login normally, it just takes you to a command line where you can only login as normal user, and then use startx to get a GUI.

More info please, though I admit it sounds as if your system is a bit broken.  Clean installation is always the best option in my opinion, and particularly so with this move from gnome2 to gnome3.

---

### Post by karol4722 on 2011-11-05
That's what I do 
1. ctrl alt f1
2. sudo -i < login on root and 'startx'
3. ubuntu with just bar with file / edit / bookmarks etc appears
4. ctrl alt t < open terminal
5. type 'unity' to bring normal looking ubu

What info do you need? Clean istallation is last thing I do :(

look at this:
```
root@muhahaha:~# gdm

** (gdm-binary:18779): WARNING **: Failed to acquire org.gnome.DisplayManager

** (gdm-binary:18779): WARNING **: Could not acquire name; bailing out
root@muhahaha:~# 

```

EDIT:
I reinstalled ubuntu and everything is good but I still cant shutdown computer... It stucks on 'Ubuntu' loading. What do?

---

