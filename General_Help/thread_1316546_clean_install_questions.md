---
title: "clean install questions"
date: 2009-11-06
forum: General Help
---

### Post by ptviperz on 2009-11-06
I've got a perfectly working dual boot machine with 

win7 on sda
9.04 on sdb
/home on sdc

I'd like to do a clean install on the 9.04 disk but I'm concerned about what happens to the settings and apps I have on my /home drive. Would I need to reinstall everything to make it work properly? I understand that the new / would be ext4 while my /home would be ext3

Any thoughts would be appreciated..

---

### Post by nothingspecial on 2009-11-06
Back up any config files you have edited to your home partition so that you can easily copy them back eg /etc/apt/sources.list or /etc/modules or whatever.

Then create a list of your currently installed apps

```
dpkg --get-selections > ~/pkgs.lst
```

After you`ve installed your new system

```
sudo apt-get install dselect
sudo dpkg --set-selections < ~/pkgs.lst
sudo apt-get dselect-upgrade
```

To get them all back

---

