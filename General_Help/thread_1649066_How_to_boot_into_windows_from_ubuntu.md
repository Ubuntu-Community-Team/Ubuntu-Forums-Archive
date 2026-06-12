---
title: "How to boot into windows from ubuntu???"
date: 2010-12-19
forum: General Help
---

### Post by karthick87 on 2010-12-19
I use dual boot with ubuntu 10.04 and windows xp.Rarely i go for windows xp..Is there a way to reboot into windows straight away from ubuntu..???I rarely boot into Windows so that i don't want to make it the default entry...Can anybody help??

---

### Post by Verbeck on 2010-12-19
[http://www.virtualbox.org/wiki/Migrate_Windows](http://www.virtualbox.org/wiki/Migrate_Windows)
could be helpful

---

### Post by karthick87 on 2010-12-19
It's not what i am looking for,I have found out the solution..


[LIST]
[*]First you have to edit your grub.
  ```
sudo gedit /etc/default/grub
```
[*]Search for the line **GRUB_DEFAULT=0** and modify it to** GRUB_DEFAULT=saved**  [IMG]http://i.imgur.com/fN2O4.png[/IMG]
[*]Update your grub using the following command.
  ```
sudo update-grub
```
[*]Now create a file and add these lines,            
  ```
!/bin/bash
WINDOWS_ENTRY=`grep menuentry /boot/grub/grub.cfg  | grep --line-number Windows`
MENU_NUMBER=$(( `echo $WINDOWS_ENTRY | sed -e "s/:.*//"` - 1 ))
gksu grub-reboot $MENU_NUMBER
gksu reboot
```
[*]Make the script executable.
[*]And now you can run this script from terminal to reboot into windows.
[*]Or you can execute the following command in your terminal   
  ```
sudo grub-reboot X
```
[*]Where X is the menuentry position of the OS you want to restart in from the GRUB menu.(starting with 0 as the first entry)
[/LIST]
  **For Example:**   
  
[LIST]
[*]If this is your grub menu and if you want to boot into windows you should give the value of X as 5.
[*]```
sudo grub-reboot 5
```
[*]  [IMG]http://i.imgur.com/ljPk2.png[/IMG]
[*]You can also create a launcher for the above command,so that double clicking the launcher will reboot into windows.
[/LIST]

---

