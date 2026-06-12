---
title: "Cannot delete a shortcut on my dekstop"
date: 2011-01-25
forum: General Help
---

### Post by cyroz on 2011-01-25
I'm having this problem when i want to delete an icon on my desktop. 

The icon won't allow me to delete it as it will show error "The specified location is not supported. I attached a screenshot of my desktop. The file that i want to delete is "g on 192.168.0.182.volume". It was a link to my shared network.

I've tried delete via terminal but when i viewed my desktop using "ls -a" , the file didn't show up.

Hope anyone can help me. 
Or maybe easy solution is my removing my gnome-desktop

I'm using Ubuntu Maverick.

TQ

[[IMG]http://img339.imageshack.us/img339/1769/errorxih.th.png[/IMG]](http://img339.imageshack.us/i/errorxih.png/)

---

### Post by philinux on 2011-01-25
What do the permission say under it's Properties Tab.

---

### Post by cyroz on 2011-01-25
"the permission couldn't be determined"

---

### Post by Smart Viking on 2011-01-25
Try this:
```
rm -fv ~/Desktop/192.168.0.182.volume
```

if that doesn't work get output from:
```
lsattr ~/Desktop/192.168.0.182.volume
```
```
file ~/Desktop/192.168.0.182.volume
```
```
ls -l /home/smartviking/Desktop/192.168.0.182.volume
```

---

### Post by cyroz on 2011-01-25
```
shahmi@cyroz:~$ rm -fv ~/Desktop/192.168.0.182.volume
shahmi@cyroz:~$ lsattr ~/Desktop/192.168.0.182.volume
lsattr: No such file or directory while trying to stat /home/shahmi/Desktop/192.168.0.182.volume
shahmi@cyroz:~$ file ~/Desktop/192.168.0.182.volume
/home/shahmi/Desktop/192.168.0.182.volume: ERROR: cannot open `/home/shahmi/Desktop/192.168.0.182.volume' (No such file or directory)
shahmi@cyroz:~$ ls -l /home/Shahmi/Desktop/192.168.0.182.volume
ls: cannot access /home/Shahmi/Desktop/192.168.0.182.volume: No such file or directory
shahmi@cyroz:~$ 
```

ur first instruction doesn't remove the link.
here the output that i got after doing what u've asked me.

---

### Post by Smart Viking on 2011-01-25
In terminal:
```
gconf-editor
```
Then go to apps>nautilus and play with the options.

---

### Post by matt_symes on 2011-01-25
Hi

What do you get if you type

```
ls -l ~/Desktop/
```

Do you see the file ?

Kind regards

---

### Post by cyroz on 2011-01-25
> **matt_symes said:**
> Hi

What do you get if you type

```
ls -l ~/Desktop/
```

Do you see the file ?

Kind regards

```
shahmi@cyroz:~$ ls -l ~/Desktop
total 1004
drwxrwxrwx 2 shahmi shahmi    4096 2010-12-06 23:11 app
drwxr-xr-x 4 shahmi shahmi    4096 2010-11-15 16:31 PDFV_Portable
-rw-r--r-- 1 shahmi shahmi 1016118 2011-01-06 08:44 train - if it's love -edited.mp3
```

it just showed nothing...

---

### Post by cyroz on 2011-01-25
[> **Smart Viking said:**
> In terminal:
```
gconf-editor
```
Then go to apps>nautilus and play with the options.

how do i play with option?
i can't edit anything.

---

### Post by cyroz on 2011-01-25
this is a screenshot when i opened gconf-editor.

i found the exactly link in the App>Nautilus>Desktop-metadata

From there , i tried to delete it but it can't.

Do gconf-editor is functioning as regedit in window?

How should i do with it?

[[IMG]http://img15.imageshack.us/img15/1322/screenshot2jn.th.png[/IMG]](http://img15.imageshack.us/i/screenshot2jn.png/)

---

### Post by ajgreeny on 2011-01-25
In terminal use ```
sudo updatedb && locate 192.168.0.182.volume
```which should tell you where any files or folders with that name are located.  You should then be able to delete them either with terminal or nautilus.

Just a thought:  this is not a relic of an ssh (or other) mounted volume, is it?  If so you may be able to right click on it and select unmount, or just reboot if needed.

---

### Post by matt_symes on 2011-01-25
Hi

I don't know if this will fix it but have you considered run GConf cleaner ?

```
sudo apt-get install gconf-cleaner
```

You might want to read up on it first though.

Kind regards

---

### Post by cyroz on 2011-01-26
> **matt_symes said:**
> Hi

I don't know if this will fix it but have you considered run GConf cleaner ?

```
sudo apt-get install gconf-cleaner
```

You might want to read up on it first though.

Kind regards

Thankz matt_symes.

It's work perfectly after i restart the lappy.

Thankz a lots guys for helping me to solve the problem

Mod , the problem already solved.
:P

---

