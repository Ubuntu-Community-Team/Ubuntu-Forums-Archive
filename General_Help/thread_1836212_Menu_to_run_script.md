---
title: "Menu to run script"
date: 2011-08-30
forum: General Help
---

### Post by jpr25 on 2011-08-30
Hi all,

I have a script and want to make a entry in the menu so when I press the button it open a terminal changes to right directory if needed and runs the script.

This is what I have but it does not seem to work.



```
sh -c "cd /pentest/enumeration/dns/dnsenum/ && ./dnsenum.pl ;sudo -s"
```This does not work I dont get no terminal

---

### Post by VCoolio on 2011-08-30
man gnome-terminal. Try like this:```
gnome-terminal --working-directory=/pentest/enumeration/dns/dnsenum/ -x perl dnsenum.pl && sudo -i
``` This may need some tweaking. The sudo -s at the end isn't going to do much and you should probably use sudo -i anyway if you really need to be root after the script finishes (sudo -s will run "as root" whereas sudo -i will run as user with root permissions; difference is in the env settings that are assumed).

---

### Post by jpr25 on 2011-08-31
Thanks this seems to work on a few things but not everything. If I install a package from the package manager like dnswalk how would I make entry in the menu can i just do gnome-terminal dnswalk ?  Also I have tried doing 

```
gnome-terminal --working-directory=/pentest/enumeration/application/ -x python dnsenum.pl 
```

And the terminal flashed up then goes. I have to make a menu for a mixture of script's and packages from shell,perl,python

thanks

---

### Post by VCoolio on 2011-08-31
Does [this](http://ubuntuforums.org/showthread.php?t=1015654) help?

---

### Post by jpr25 on 2011-08-31
I will try that later what about if its a package that has been installed as by default you dont need to give it a full path. 

can you just do gnome-terminal dnswalk?

---

### Post by VCoolio on 2011-08-31
If there is an executable installed in the folders belonging to your $PATH (check with "echo $PATH" what folders and "which dnswalk" to see where dnswalk is) then yes. But it needs -e or -x, so: 
gnome-terminal -e dnswalk
or 
gnome-terminal -x dnswalk.
Run "man gnome-terminal" to check the difference between -x and -e.

---

