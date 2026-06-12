---
title: "Unable to Install apache2 in ubuntu 10.10 [dependency issue]"
date: 2011-08-07
forum: General Help
---

### Post by rraj.be on 2011-08-07
Dear friends, I am trying to install local wordpress in my ubuntu 10.10.So i need LAMP. During apache2 installation, the following is the issue. Hope some one can help me to solve this issue.

raj@abc:~$ sudo apt-get install apache2
[sudo] password for raj: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 apache2 : Depends: apache2-mpm-worker (= 2.2.16-1ubuntu3) but it is not going to be installed or
                    apache2-mpm-prefork (= 2.2.16-1ubuntu3) but it is not going to be installed or
                    apache2-mpm-event (= 2.2.16-1ubuntu3) but it is not going to be installed or
                    apache2-mpm-itk (= 2.2.16-1ubuntu3) but it is not going to be installed
           Depends: apache2.2-common (= 2.2.16-1ubuntu3) but it is not going to be installed
E: Broken packages
raj@abc:~$

---

### Post by ~!geek!~ on 2011-08-07
Setting up Lamp server from repository is quite easy:
For getting lamp on ubuntu you may use "tasksel"

In your case first of all fix the broken apache, 
You may use > sudo apt-get autoremove and  > sudo apt-get --fix-missing <packagename> to fix the broken apache.

Now for setting up LAMP:
Use this (You may want to test if broken packages had been fixed because following steps can only work when you are able to use apt-get)
1) > sudo apt-get install tasksel
2) > sudo tasksel
3) Select Lamp server from the list of available packages(use space bar and tab to navigae the list). It will ask for the packages you can select which you should based on your preferences.
Also it will ask for one or two passwords like for mysql... .Remember the paswords 
If it does not ask for phpmyadmin (the gui for managing mysql database), you may install it using > sudo apt-get install phpmyadmin.
The process is intuitive enough.!!!

---

### Post by rraj.be on 2011-08-07
Hi  ~!geek!~, 
I dont see any broken packages to be fixed. Should i run 
```
sudo apt-get --fix-missing apache2
```

By the way i tries tasksel also. The same happens there. It stops abruptly.

---

### Post by rraj.be on 2011-08-07
The problem was My security updates were turned off. Once i enabled them, It worked like charm... 

Thanks for astraljava of #ubuntu for the help.. :)

---

