---
title: "AdobeReader download won't open"
date: 2011-06-15
forum: General Help
---

### Post by 016284 on 2011-06-15
Greetings,

after downloading Adobe from firefox, when in downloads I click AdbeRdr9.4.2-1_i486linux_enu.bin
the program won't start.

Could not display ''/home/Ted/Downloads/AdbeRdr9.4.2-1_i486linux-enu.bin''.

---

### Post by btindie on 2011-06-15
You need to set the eXecutable bit for it to be erm, executed.
```
chmod +x /home/Ted/Downloads/AdbeRdr9.4.2-1_i486linux-enu.bin
```
Then from the terminal type
```
/home/Ted/Downloads/AdbeRdr9.4.2-1_i486linux-enu.bin
```

---

### Post by tgalati4 on 2011-06-15
The reason for this hoop-jumping is it prevents execution of arbitrary code (say virus) on your machine.  You have to explicitly "activate" an executable file by using the +x flag (add execution privilege).  Then you have to specify the actual path name using either the full path name or a shortcut:

./Adb(tab key)

These two procedures keeps linux sweet-smelling.

---

### Post by 016284 on 2011-06-16
> **btindie said:**
> You need to set the eXecutable bit for it to be erm, executed.
```
chmod +x /home/Ted/Downloads/AdbeRdr9.4.2-1_i486linux-enu.bin
```Thankyou for your answer but where exactly I need to type this?

---

### Post by 016284 on 2011-06-16
Problem not solved yet, where I need to put this?


chmod +x /home/Ted/Downloads/AdbeRdr9.4.2-1_i486linux-enu.bin

---

### Post by oldos2er on 2011-06-16
Acroread is in the 'extra' repository. To enable it, open a terminal (Alt-F2, gnome-terminal) and run ```
gksu gedit /etc/apt/sources.list
``` Remove the comment marks # from the lines 

deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

When you're done, run ```
sudo apt-get update
``` Use your favorite package manager e.g. Software Center or Synaptic to install it. I'm assuming you're running 11.04 Natty Narwhal.

---

### Post by 016284 on 2011-06-16
> **oldos2er said:**
> Acroread is in the 'extra' repository. To enable it, open a terminal (Alt-F2, gnome-terminal) and run ```
gksu gedit /etc/apt/sources.list
``` Remove the comment marks # from the lines 
 
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
 
When you're done, run ```
sudo apt-get update
``` Use your favorite package manager e.g. Software Center or Synaptic to install it. I'm assuming you're running 11.04 Natty Narwhal.
 
+1 Sir very helpful.

---

### Post by 016284 on 2011-06-16
Tested now and doesn't work.
Ubuntu 10.04 here.

---

### Post by oldos2er on 2011-06-16
For 10.04, try 

deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) lucid main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) lucid main

---

