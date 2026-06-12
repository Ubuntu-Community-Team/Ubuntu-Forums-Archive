---
title: "Netbeans won't start after upgrade to 10"
date: 2010-08-20
forum: General Help
---

### Post by alberthendriks on 2010-08-20
Hi all,

While I was upgrading Ubuntu from 9 to 10, Netbeans was upgraded from 6.7 to 6.8. But now I cant start it anymore. I even uninstalled it in the Ubuntu Software Center and reinstalled it. When starting from the command line I shortly get the blue box with the loading bar but then it disappears and after a couple of seconds the command line finishes.
```

albert@albert-laptop:~$ netbeans
albert@albert-laptop:~$ 
```What can I do?

---

### Post by dsiembab on 2010-08-21
if you are having problems loading the application try
```
<nameofrunscript> > errorfile.txt
``` and see what it says
to find the name right click on the launcher and look at the properties

Me personally when I need a netbeans or eclipse, I usually download it directly from the applications website and make a bin folder and an app folder in my user directory. i.e.
```
mkdir ~/bin ~/app
```
take the zip or tgz and extract it into the app directory they are usually in a container folder i.e. the application is in a main folder.
Then I find the shell script that runs the application and make a symlink in the ~/bin folder i.e.
```
ln -s /home/<username>/app/<runfile> ~/bin
```
I find this easier to update the application and add plugins to without having to go through rpm for every plugin I want to load, you can then create a launcher for the application on the desktop.

---

### Post by alberthendriks on 2010-08-21
Since the commandline command didnt print anything the error file was also empty. But installing it myself was a good idea. I have it up and running now. Thanks!

---

