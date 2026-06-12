---
title: "Extract an .exe file"
date: 2010-12-15
forum: General Help
---

### Post by tweaktolive on 2010-12-15
I was having a problem in windows and coudn't install an application (I think it's corrupt as installation is interrupted in between) , so i was wondering whether i could extract the
entire .EXE in ubuntu (without using WINE , because it fails too) using some third party software.

Any suggestion ?

Thanks!!

---

### Post by surfer on 2010-12-15
.exe files are usually executable files. they can be executed an not extracted (like zip files). on linux, wine is your only option to run such a file.

---

### Post by Simian Man on 2010-12-15
I don't think so.  Extractable .exe's are just programs whose job is to write some files, they're not generic file container formats like .zip or .tar.  Also, if neither Windows nor wine can run this program, it makes me think there's likely something wrong with it.  Maybe try re-downloading/acquiring the file?

---

### Post by e24ohm on 2010-12-15
If the application was writen in C# or VB, you might be able to use Mono and run the .exe. I have been playing around with the GTK# and Mono framework.

---

### Post by gandaran on 2010-12-15
> **tweaktolive said:**
> I was having a problem in windows and coudn't install an application (I think it's corrupt as installation is interrupted in between) , so i was wondering whether i could extract the
entire .EXE in ubuntu (without using WINE , because it fails too) using some third party software.

Any suggestion ?

Thanks!!
some .exe files but not all can be extracted on Linux, I have done it many times before when I had windows extracting the whole installer and then just run the application on windows without actually installing it using the installer.
right now I cant remember which application I used, it was some command line app installed from package manager,(I'll try to find out) I believe peazip can also do it. 
[http://www.peazip.org/peazip-linux.html](http://www.peazip.org/peazip-linux.html)

---

### Post by tweaktolive on 2010-12-15
Hey gandaran ,

Did you do something like 'Extract' in your command prompt .

I installed an app recently , even i will check it out !!

---

