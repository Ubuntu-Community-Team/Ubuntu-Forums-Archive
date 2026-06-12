---
title: "Permission problem again .gvfs"
date: 2010-01-10
forum: General Help
---

### Post by axelsvag on 2010-01-10
I need to remove a folder. This operation I have done millions of times so I should know the tricks but I am completely stuck. Here is the problem. I try to put a file inside the /home/.gvfs folder. But I was not allowed to. First I tried to use nautilus to locate the file and change permission. I get in the menus and permission is set to my username all is well. But when I try to change from read only to read and write the permision goes back in 1 s. OK I try to use ```
sudo nautilus
``` but now the .gvfs folder is lost even if I show all hidden files. I can say that all other hidden files is howed but not the .gvfs folder. OK I take the terminal way. When I use sudo ls --all in the home folder I can see the .gvfs but if I try to remove it it says acces denied. So this is a mystery. A folder seen in nautilus as user but is not visible as root. And impossible to change permission. I feels like the folder is kidnapped by some process.

My main effort is to fix my Ipod problems in Karmic and I used theese instructions [HTML]http://fatbuttlarry.blogspot.com/2010/01/ipod-touch-iphone-3g-ubuntu-910-in-5.html[/HTML]

---

### Post by 3rdalbum on 2010-01-10
You don't put things directly into .gvfs - it's just where Gnome virtual filesystems get mounted to.

---

### Post by axelsvag on 2010-01-10
OK, but why is it impossible to make the command work? 
```
echo -e "\n\nPlease type the name of your ipod:"; read ipod_name; mkdir -p ~/.gvfs/$ipod_name/iTunes_Control/Device/; ipod-read-sysinfo-extended `sudo lsusb -v | grep 'iSerial' | awk 'length($0)>=68' | awk '{print $3}'` ~/.gvfs/$ipod_name/
```

---

