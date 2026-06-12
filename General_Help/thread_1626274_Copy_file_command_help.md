---
title: "Copy file command help"
date: 2010-11-20
forum: General Help
---

### Post by markoid63 on 2010-11-20
I need to copy a file from my desktop to a system folder but unsure how. It needs to go to the "etc/X11" folder. Any help would be greatly appreciated.  ](*,)

---

### Post by daimaru on 2010-11-20
```
sudo cp ~/Desktop/filetocopy /etc/X11/
```you can also open nautilus (window manager) with root privileges and do a normal copy paste (graphical way)
```
gksu nautilus &
```1) browse to your /home/username/Desktop
2) select copy 
3) browse to /etc/X11 and paste it

---

### Post by karthick87 on 2010-11-20
```
sudo cp /source /destination
```

---

### Post by karthick87 on 2010-11-20
> **daimaru said:**
> ```
sudo cp ~/Desktop/filetocopy /etc/X11/
```you can also open nautilus (window manager) with root privileges and do a normal copy paste (graphical way)
```
gksu nautilus &
```1) browse to your /home/username/Desktop
2) select copy 
3) browse to /etc/X11 and paste it


What is the difference between **sudo nautilus** and **gksu nautilus &**

---

### Post by matt_symes on 2010-11-20
Hi

Read this. It may clarify things

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[B]gksu nautilus &

[/B]The** &** will run the command in the background and still allow you to type into the terminal. 

When you close the terminal it will kill nautilus.

Use

nohup gksu nautilus &

to ensure the command runs after the terminal is closed and runs in the background (no hangup).

Kind regards

---

### Post by Hippytaff on 2010-11-20
gksudo should be used when opening gui things
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
:-)

---

### Post by markoid63 on 2010-11-20
Thankyou so much everyone for your help, mission accomplished. You are all awesome.
:p

---

