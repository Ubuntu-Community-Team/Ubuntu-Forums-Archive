---
title: "how to install Matlab in ubuntu 10.04?"
date: 2011-02-05
forum: General Help
---

### Post by jolian ramos on 2011-02-05
how to install Matlab in ubuntu 10.04?

---

### Post by dino99 on 2011-02-05
a little googling around can give you some help:

[http://newyork.ubuntuforums.org/showthread.php?t=1563015](http://newyork.ubuntuforums.org/showthread.php?t=1563015)

into synaptic you can also find scilab (matlab like)

---

### Post by jolian ramos on 2011-02-10
i am sorry but i want to know how to open Matlab after installing it i already install it in usr/Matlab/R2010b but i don't know how to run the programe?

---

### Post by 3Miro on 2011-02-10
From terminal:
```
/usr/Matlab/R2010b/bin/matlab
```

You can make this command as a shortcut to either the menu or desktop. The proper icons to go with the shortcut are in
```
/usr/Matlab/R2010b/X11/icons
```

---

### Post by jolian ramos on 2011-02-10
it still doesn't run i copy your code as it is in terminal but it gives me nothing 
/usr/Matlab/R2010b/bin/matlab

---

### Post by 3Miro on 2011-02-10
> **jolian ramos said:**
> it still doesn't run i copy your code as it is in terminal but it gives me nothing 
/usr/Matlab/R2010b/bin/matlab

Not even an error message? If there is no error message (like file not found, permission denied or something of the sort), then there may be an issue with the Matlab installation.

---

### Post by jolian ramos on 2011-02-10
when i copy paste your code /usr/Matlab/R2010b/bin/matlab as it is in terminal it gives me 
bash:/usr/Matlab/R2010b/bin/matlab:no such file or directory

---

### Post by 3Miro on 2011-02-10
> **jolian ramos said:**
> when i copy paste your code /usr/Matlab/R2010b/bin/matlab as it is in terminal it gives me 
bash:/usr/Matlab/R2010b/bin/matlab:no such file or directory

So it does give you something.

The matlab executable is in bin/matlab relative to where you put Matlab itself. If you put Matlab in /usr/Matlab/R2010b, then my code should work. Otherwise, you have to see where Matlab is installed.

Open the nautilus (Places -> Home) and try to find where Matlab is. Then look for bin/matlab. You should be able to start it with either "run" or "run in terminal".

---

### Post by jolian ramos on 2011-02-10
ok how to uninstall matlab totally from computer

---

### Post by HermanAB on 2011-02-10
Howdy,

Try SciLab.  It is better and costs nothing.

---

### Post by jolian ramos on 2011-02-10
ok how to uninstall matlab totally from computer?????????

---

### Post by 3Miro on 2011-02-10
> **jolian ramos said:**
> ok how to uninstall matlab totally from computer?????????

Unless the CD or whatever you used comes with an uninstall key, you will have to find the Matlab folder and delete it. Use

```
gksudo nautilus
```

if you get "permission denied". However, BE CAREFUL WITH GKSUDO you can erase important things and really damage your system.

---

### Post by jolian ramos on 2011-02-10
i find the bin folder and find matlab i double click on it and choose run in terminal but nothing open at all !!!!!!!!!!!!!!!!!!!

---

### Post by 3Miro on 2011-02-10
> **jolian ramos said:**
> i find the bin folder and find matlab i double click on it and choose run in terminal but nothing open at all !!!!!!!!!!!!!!!!!!!

It crashes probably because you are missing a library or something. Now that you know where it is, you can use the terminal to cd into that folder:

```
cd /wherervet/matlab/is/bin
```

and then run the matlab executable with:

```
./matlab
```

Then you should get an error message about what the problem is. Post the message here.

---

### Post by jolian ramos on 2011-02-10
giving me error of loading shared libraries :libxp.so.6:cannot open shared object file :no such file or directory 

what does this mean ?

---

### Post by 3Miro on 2011-02-10
> **jolian ramos said:**
> giving me error of loading shared libraries :libxp.so.6:cannot open shared object file :no such file or directory 

what does this mean ?

You need to install the library.

Go to System -> Admin -> Synaptic Package Manager and search for libxp. Install it and Matlab should run.

---

### Post by jolian ramos on 2011-02-10
thank you it works

---

### Post by 3Miro on 2011-02-10
> **jolian ramos said:**
> thank you it works

Glad to hear it. If you have no other questions, please mark the thread as "solved".

---

### Post by jolian ramos on 2011-02-10
i have only one more question 
it is not practical to open in each time matlab using this way how can i make a desktop icon for run quick run?

---

