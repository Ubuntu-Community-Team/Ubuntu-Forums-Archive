---
title: "exec format error in java install"
date: 2009-09-28
forum: General Help
---

### Post by Stickiler on 2009-09-28
ok i tried to install the program Tuxguitar, through the terminal, and after it finished downloading the files, it ran the configuration, then proceeded to die with a strange error, "Exec Format Error", now after that, i couldnt install anymore packages, so i proceeded to attempt to remove the Tuxguitar packages, and i succeeded in removing most of them, however 8 packages remain, and the output of the command 

sudo apt-get install
and 
sudo apt-get -f install

is listed below:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ttf-wqy-zenhei (0.8.34-cvs20081027-0ubuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing ttf-wqy-zenhei (--configure):
 subprocess post-installation script returned error exit status 2
Setting up java-common (0.30ubuntu4) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing java-common (--configure):
 subprocess post-installation script returned error exit status 2
Setting up libswt-gtk-3.4-java (3.4-2ubuntu3) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libswt-gtk-3.4-java (--configure):
 subprocess post-installation script returned error exit status 2
Setting up ttf-bengali-fonts (1:0.5.4ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing ttf-bengali-fonts (--configure):
 subprocess post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up ttf-kannada-fonts (1:0.5.4ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing ttf-kannada-fonts (--configure):
 subprocess post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up ttf-oriya-fonts (1:0.5.4ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing ttf-oriya-fonts (--configure):
 subprocess post-installation script returned error exit status 2
Setting up ttf-telugu-fonts (1:0.5.4ubuntu2) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing ttf-telugu-fonts (--configure):
 subprocess post-installation script returned error exit status 2
Setting up oss-compat (0.0.4+nmu2) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing oss-compat (--configure):
 subprocess post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 ttf-wqy-zenhei
 java-common
 libswt-gtk-3.4-java
 ttf-bengali-fonts
 ttf-kannada-fonts
 ttf-oriya-fonts
 ttf-telugu-fonts
 oss-compat
E: Sub-process /usr/bin/dpkg returned an error code (1)

```does anybody know what could be the problem? i would really appreciate it if somebody would be able to tell me what is wrong, and possibly a few solutions to the problem.
thanks for any and all help offered.

EDIT: running dpkg --configure -a returns no output to the screen.

---

### Post by zvacet on 2009-09-28
```
sudo dpkg --configure -a
```

---

### Post by Stickiler on 2009-09-28
> **zvacet said:**
> ```
sudo dpkg --configure -a
```

did you not read the edit???? i already ran that command, it does not do anything to fix the situation.

---

### Post by zvacet on 2009-09-28
> EDIT: running dpkg --configure -a returns no output to the screen.

According to that you run command without sudo.If you used sudo you didn´t told that.You can try same command with one package at the time.For example

```
sudo dpkg --configure ttf-wqy-zenhei
```

and after that do the same with the rest of packages.

---

### Post by Stickiler on 2009-09-28
> **zvacet said:**
> According to that you run command without sudo.If you used sudo you didn´t told that.You can try same command with one package at the time.For example

```
sudo dpkg --configure  ttf-wqy-zenhei
```and after that do the same with the rest of packages.

i still get that same error, thanks for your help though.

---

### Post by zvacet on 2009-09-28
Well, I made mistake with command.It should be 

```
sudo dpkg --configure ttf-wqy-zenhei
```

Just one space not two.

---

### Post by Stickiler on 2009-09-28
> **zvacet said:**
> Well, I made mistake with command.It should be 

```
sudo dpkg --configure ttf-wqy-zenhei
```Just one space not two.

i had noticed that, and as such had corrected it when i ran the commands. still the same error, i have run this command multiple times for each package. any other ideas?

---

### Post by zvacet on 2009-09-29
```
sudo apt-get -f install
```

---

### Post by Stickiler on 2009-09-29
> **zvacet said:**
> ```
sudo apt-get -f install
```
that produces the same error, as the main post says lol.

---

### Post by Stickiler on 2009-10-01
i decided to just format and reinstall my ubuntu, i couldnt find another way that would fix the problem.

---

### Post by arielon on 2009-11-07
c'mon... i was hoping to find an answer here...

```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up bcmwl-kernel-source (5.10.91.9+bdcom-0ubuntu4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up fakeroot (1.12.4ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing fakeroot (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 bcmwl-kernel-source
 fakeroot
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any clues on what should be done?? this happens every time I install or reconfigure any package.

---

