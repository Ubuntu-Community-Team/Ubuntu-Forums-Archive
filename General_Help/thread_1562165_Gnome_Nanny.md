---
title: "Gnome Nanny"
date: 2010-08-27
forum: General Help
---

### Post by nigsy on 2010-08-27
Hi all,
I have dowmloaded the latest version of Gnome Nanny, but have run into an instal problem at the first hurdle:

I have extracte the folder to Documents:
Cd/ to the folder and run the ./configure command and get this message:



**No package 'pygtk-2.0' found**


I have checked the install files and edited the lines which contain the  above to now read pygtk -2.0 >=2.8 as 2.8 is the version of python I  have installed. In package manager it only goes back to v2.2.

Any ideas how I can get around this error?

Running Ubuntu 9.1 karmic Koala.

---

### Post by 3rdalbum on 2010-08-27
'pygtk-2.0' is a Python module. The version number of pygtk is unrelated to the version number of Python itself.

PyGTK should be preinstalled, but try:

```
sudo apt-get install python-gtk2-dev
```

To tell you the truth I'm not sure exactly what python-gtk2-dev provides, but usually when you're compiling software and it complains about a missing library, you need to install the package that has "-dev" at the end of the name. This package also brings in "python-gtk2" if you don't already have it.

---

### Post by nigsy on 2010-08-27
Thanks, had to install about 5 other python related packages before the ./configure comand worked.

Then did the make & make install and just got a load of access denied messages - so I've given up.

---

### Post by WorMzy on 2010-08-27
"make" should work as a normal user, "make install" requires sudo.

---

### Post by nigsy on 2010-08-27
Cheers,
I'm new to this Linux stuff, but learning all the time..patience is required though;)

---

### Post by WorMzy on 2010-08-27
No worries. You'll probably encounter a few more problems like that, but once you understand why you're getting the errors it'll start making sense. So don't give up so easily. :)

In this case, "make" compiles the source code and puts the output files in a directory owned by your user, this is used to check that the make process will execute without any problems when you run it for real (with "make install"). "make install" compiles the code and puts the output files into the system directories, which your user can't write to by default. So you use "sudo make install" instead, which runs the command as the root user, who *can* write to the system directories.

---

