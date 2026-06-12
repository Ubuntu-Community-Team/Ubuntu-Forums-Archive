---
title: "Help With Installing Python OpenGL  Support"
date: 2009-07-19
forum: General Help
---

### Post by chrisl121212 on 2009-07-19
I am completely new with Ubuntu so go easy on me. I had tried running Chess in 3D view and is said "No Python OpenGL support". I went in add/remove programs and tried installing a NVidia driver (I tried every driver), but I always got an error saying "conflicts with other programs". Can someone please help me out?:confused:

---

### Post by abhilashm86 on 2009-07-19
> **chrisl121212 said:**
> I am completely new with Ubuntu so go easy on me. I had tried running Chess in 3D view and is said "No Python OpenGL support". I went in add/remove programs and tried installing a NVidia driver (I tried every driver), but I always got an error saying "conflicts with other programs". Can someone please help me out?:confused:

did you install free glut libraries?? 
look here for setting up IDE in ubuntu for openGL support,
[http://ubuntuforums.org/showthread.php?t=590676](http://ubuntuforums.org/showthread.php?t=590676)

[http://www.futuredesktop.org/codeblocks_on_ubuntu_8.04.html](http://www.futuredesktop.org/codeblocks_on_ubuntu_8.04.html)

hope this helps........

---

### Post by unutbu on 2009-07-19
There is a bug report and a solution here:
[https://bugs.launchpad.net/ubuntu/+source/pyopengl/+bug/351284](https://bugs.launchpad.net/ubuntu/+source/pyopengl/+bug/351284)

---

### Post by chrisl121212 on 2009-07-19
I don't understand how to install the free glut.:?

---

### Post by unutbu on 2009-07-19
chrisl121212, open a terminal (Applications>Accessories>Terminal) and type (or copy-and-paste)
```

gksu gedit /etc/apt/sources.list
```

Go to the bottom of the file and add this line:
```

deb http://ppa.launchpad.net/robert-ancell/ppa/ubuntu jaunty main 

```
Save and exit gedit (the text editor). In the terminal now type
```


sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 149D38A7
sudo apt-get update
```

This will update your computer's database of available packages.

Now install the python-opengl package:
```

sudo apt-get install python-opengl
```

Then try running the chess program again.
If it does not work, please post the entire output from the terminal.

---

### Post by abhilashm86 on 2009-07-19
> **chrisl121212 said:**
> I don't understand how to install the free glut.:?

to install freeglut, check this, type following in terminal,
```

sudo apt-get install freeglut3 freeglut3-dev

```

then same as i told, open an editor, do the codeing, save it, exit, 
use g++ it c++ or python
```

g++ -lGL -lglut test1.cpp -o test1

```

---

### Post by abhilashm86 on 2009-07-19
hey if you want to add sound in opengl programs, you can install openaL libraries, works great, check my website, i've a program tutorial,[see this openAL]("http://abhilash.co.nr/"), please check in programming tips.......

---

