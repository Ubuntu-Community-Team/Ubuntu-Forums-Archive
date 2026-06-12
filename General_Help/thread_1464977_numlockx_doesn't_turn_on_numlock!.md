---
title: "numlockx doesn't turn on numlock!"
date: 2010-04-28
forum: General Help
---

### Post by the pearly gates on 2010-04-28
Hello,

I have a logitech dinova keyboard and the number pad doesn't work. I tried searching for a solution ([http://ubuntu-ky.ubuntuforums.org/showthread.php?t=844194](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=844194) ) by using a program called numlockx, and have ran this in the terminal as:

```
numlockx on
```

but still nothing! I am running Ubuntu 9.10. 

Does anyone have any suggestions? I even changed my keyboard in System->Preferences->Keyboard to "Logitech DiNova" but that didn't help.  Am I missing something here?

Thanks

---

### Post by zvacet on 2010-04-29
Like link say after installing numlockx type in applications>accessories>terminal

```
sudo cp /etc/gdm/Init/Default /etc/gdm/Init/Default.bak
```

```
gksudo gedit /etc/gdm/Init/Default
```

and above the line that says "exit 0" add the following:
[B]if [ -x /usr/bin/numlockx ]; then
/usr/bin/numlockx on 
fi[/B]
 Save and close file.Next time when you start comp numlock should be on.

---

### Post by the pearly gates on 2010-04-29
> **zvacet said:**
> Like link say after installing numlockx type in applications>accessories>terminal

```
sudo cp /etc/gdm/Init/Default /etc/gdm/Init/Default.bak
```

```
gksudo gedit /etc/gdm/Init/Default
```

and above the line that says "exit 0" add the following:
[B]if [ -x /usr/bin/numlockx ]; then
/usr/bin/numlockx on 
fi[/B]
 Save and close file.Next time when you start comp numlock should be on.

I tried this, but this did not work either. Do you know why?

---

### Post by the pearly gates on 2010-04-29
Actually, hitting 1,2,3,4, 6,7,8, or 9 on the keypad will move the mouse. Strange...

EDIT:

After searching the other forums, I found that under

System-> Preferences --> mousekeys [tab]  

was checked for some reason.

Unchecking this box solved the problem.

---

