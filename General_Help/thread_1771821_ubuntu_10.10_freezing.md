---
title: "ubuntu 10.10 freezing"
date: 2011-05-30
forum: General Help
---

### Post by otaji on 2011-05-30
when ubuntu 10.10 freezes, what can one do that is similar to using in Windows ctrl+alt+del to get to task manager ??

---

### Post by sea_dawg on 2011-05-30
Have you tried ctrl + alt + del  ?

If that fails you can try in terminal

```
shutdown -h now
```

---

### Post by IWantFroyo on 2011-05-30
alt-f2, type "gnome-system-monitor"

The processes tab works like Window's ctrl-alt-del.

I would advise you go into keyboard shortcuts and set "gnome-system-monitor" to open when you hit ctrl-alt-del.

---

### Post by sea_dawg on 2011-05-30
I should have asked if it is the whole os that is frozen or a single app window?

shutdown does just what it sounds like, it shuts the machine down.

If an app is frozen try this:

in terminal:
```
xprop | grep _NET_WM_PID
```

The cursor changes to a cross.  Click the offending window to get the PID

back in terminal:

```
kill PID
```

---

### Post by otaji on 2011-05-31
> **sea_dawg said:**
> Have you tried ctrl + alt + del  ?

If that fails you can try in terminal

```
shutdown -h now
```
thanks for your replies. yes I tried Ctrl+alt+delete with no luck.
What is 'terminal'? How do you put in a 'code'?

---

### Post by searchfgold6789 on 2011-05-31
You would have to open a 'terminal window' (Applications > Accessories > Terminal) and then type in computer commands.
The terminal window allows you to type in or copy/paste in commands that Ubuntu uses to execute corresponding tasks as the user wishes. For an example: I want to use the terminal to copy a file from one place to another. I would open the terminal first. Then I would type in the code for copying a file from one place to another (The source file is /Folder/ubuntu.iso; the destination is /home/richie/Projects). I would type the command into the terminal:```
richie@ubuntu-desktop:~$ cp /Folder/ubuntu.iso /home/richie/Projects {I then press enter to send the command}
richie@ubuntu-desktop:~$
```and then my file would be copied. If you want more info about the terminal, then here is a good guide: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by otaji on 2011-06-03
> **searchfgold6789 said:**
> You would have to open a 'terminal window' (Applications > Accessories > Terminal) and then type in computer commands.
The terminal window allows you to type in or copy/paste in commands that Ubuntu uses to execute corresponding tasks as the user wishes. For an example: I want to use the terminal to copy a file from one place to another. I would open the terminal first. Then I would type in the code for copying a file from one place to another (The source file is /Folder/ubuntu.iso; the destination is /home/richie/Projects). I would type the command into the terminal:```
richie@ubuntu-desktop:~$ cp /Folder/ubuntu.iso /home/richie/Projects {I then press enter to send the command}
richie@ubuntu-desktop:~$
```and then my file would be copied. If you want more info about the terminal, then here is a good guide: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
many thanks for this info

---

