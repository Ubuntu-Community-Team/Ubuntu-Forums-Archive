---
title: "Package Managers"
date: 2011-08-05
forum: General Help
---

### Post by JASONFUSARO on 2011-08-05
Simple question:

I have the following package managers installed:

Ubuntu Software Center
debian package search
synaptic package
adept installer
adept manager
smart package manager
muon package manager


If I install packages using a different package manager such as trying each one out to see how they function, will it eventually lead to problems?

From what I can gather from investigating after the fact it can.


I have broken packages which I am trying to correct using aptitude.

Is it wise to just pick one and stick with it, and if so which one?

Smart package manager appears to try and tackle this problem.

I believe this is the cause of my broken gnome system?

Thank you for any input on this question.

---

### Post by oldos2er on 2011-08-05
As long as you're using only one package manager at a time, there shouldn't be a problem. 

Try ```
sudo aptitude install -f
``` to fix your broken packages.

---

### Post by JASONFUSARO on 2011-08-05
```

jason@UbuntuStudio64bit:~$ sudo aptitude install -f
[sudo] password for jason: 

The following NEW packages will be installed:
  gnome-accessibility-themes-extras gnome-games-extra-data 
0 packages upgraded, 2 newly installed, 0 to remove and 7 not upgraded.
Need to get 0 B/4,356 kB of archives. After unpacking 10.4 MB will be used.
Do you want to continue? [Y/n/?] y


(Reading database ... 548064 files and directories currently installed.)
Unpacking gnome-accessibility-themes-extras (from .../gnome-accessibility-themes-extras_3.0.0-0ubuntu1~build2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/gnome-accessibility-themes-extras_3.0.0-0ubuntu1~build2_all.deb (--unpack):
 trying to overwrite '/usr/share/themes/HighContrast/index.theme', which is also in package gnome-themes-standard 2.91.93-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
No apport report written because MaxReports is reached already
                                                              Unpacking gnome-games-extra-data (from .../gnome-games-extra-data_2.30.0-1ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/gnome-games-extra-data_2.30.0-1ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/share/gnome-games-common/cards/bonded.svg', which is also in package gnome-games-common 1:3.0.2-0ubuntu1~natty2
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-accessibility-themes-extras_3.0.0-0ubuntu1~build2_all.deb
 /var/cache/apt/archives/gnome-games-extra-data_2.30.0-1ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:


```



Yes it is the reason I messed thing up, if you look at my other threads, after doing some investigating I have come to this conclusion.


I don't think there is a way to rectify it either?


I should have become more knowledgeable before using each to see how they ran.

Do you think it is correctable or a lost cause?

Some things are working but unfortunately again I installed home on the  same partition, and proceeded to download just about every package on earth :D

---

### Post by JASONFUSARO on 2011-08-05
I started a couple of threads in other areas many views few replies?


These are just a few of the many things I tried:

```

sudo apt-get install  ubuntu-desktop
    LONG LIST THEN
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libmono-system-web2.0-cil : Depends: libmono-system-data-linq2.0-cil (>= 1.0) but it is not going to be installed
                             Depends: libmono2.0-cil (>= 2.6.3) but it is not going to be installed
                             Depends: libgdiplus but it is not going to be installed
 libruby1.8 : Depends: libreadline5 (>= 5.2) but it is not going to be installed
 mono-xsp2 : Depends: mono-xsp2-base (= 2.6.5-3) but it is not going to be installed
 monodoc-base : Depends: libmono-system-web1.0-cil (>= 1.0) but it is not going to be installed
E: Broken packages

===================================================================
jason@UbuntuStudio64bit:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
N: Ignoring file 'apt-build' in directory '/etc/apt/sources.list.d/' as it has no filename extension
jason@UbuntuStudio64bit:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del libgtkhtml-editor-4.0-0 4.0.0-1~build1 [83.9 kB]
Del libgtkhtml-4.0-dev 4.0.0-1~build1 [462 kB]
Del gir1.2-polkit-1.0 0.101-4~natty1 [13.9 kB]
Del libpolkit-agent-1-0 0.101-4~natty1 [23.5 kB]
Del libgtkhtml-4.0-0 4.0.0-1~build1 [370 kB]
Del libgtkhtml-editor-4.0-dev 4.0.0-1~build1 [147 kB]
Del libgtkhtml-4.0-common 4.0.0-1~build1 [565 kB]
Del policykit-1 0.101-4~natty1 [57.6 kB]
Del libpolkit-backend-1-0 0.101-4~natty1 [45.8 kB]
Del libpolkit-gobject-1-0 0.101-4~natty1 [45.5 kB]
**[COLOR=Red]N: Ignoring file 'apt-build' in directory '/etc/apt/sources.list.d/' as it has no fi[/COLOR]**

^   there is a copy of this but when the command is run it gets blanked out even if put the saved file info in it ^






========================================================================
jason@UbuntuStudio64bit:~$ sudo apt-get clean



=========================================================================
jason@UbuntuStudio64bit:~$ sudo apt-get autoremove
Reading package lists... Done                                                       
Building dependency tree                                                            
Reading state information... Done                                                   
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.                      
N: Ignoring file 'apt-build' in directory '/etc/apt/sources.list.d/' as it has no filename extension                                            




======================================================================================
jason@UbuntuStudio64bit:~$ sudo killall synaptic                                    
synaptic: no process found            



========================================================================================                                              
jason@UbuntuStudio64bit:~$ sudo apt-get dist-upgrade                                
Reading package lists... Done                                                       
Building dependency tree                                                            
Reading state information... Done                                                   
Calculating upgrade... Done                                                         
The following packages have been kept back:                                         
  gnome-themes-standard                                                             
The following packages will be upgraded:                                            
  gir1.2-polkit-1.0 gnome-accessibility-themes libpolkit-agent-1-0                  
  libpolkit-backend-1-0 libpolkit-gobject-1-0 policykit-1                           
6 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.                      
Need to get 602 kB of archives.                                                     
After this operation, 4,096 B disk space will be freed.                             
Do you want to continue [Y/n]? y
Get:1 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ natty/main libpolkit-gobject-1-0 amd64 0.102-1~natty1 [45.5 kB]
Get:2 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ natty/main libpolkit-agent-1-0 amd64 0.102-1~natty1 [23.6 kB]
Get:3 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ natty/main gir1.2-polkit-1.0 amd64 0.102-1~natty1 [14.1 kB]
Get:4 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ natty/main gnome-accessibility-themes all 3.0.0-0ubuntu1~build2 [414 kB]
Get:5 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ natty/main libpolkit-backend-1-0 amd64 0.102-1~natty1 [45.8 kB]
Get:6 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ natty/main policykit-1 amd64 0.102-1~natty1 [58.3 kB]
Fetched 602 kB in 5s (117 kB/s)       
(Reading database ... 548064 files and directories currently installed.)
Preparing to replace libpolkit-gobject-1-0 0.101-4~natty1 (using .../libpolkit-gobject-1-0_0.102-1~natty1_amd64.deb) ...
Unpacking replacement libpolkit-gobject-1-0 ...
Preparing to replace libpolkit-agent-1-0 0.101-4~natty1 (using .../libpolkit-agent-1-0_0.102-1~natty1_amd64.deb) ...
Unpacking replacement libpolkit-agent-1-0 ...
Preparing to replace gir1.2-polkit-1.0 0.101-4~natty1 (using .../gir1.2-polkit-1.0_0.102-1~natty1_amd64.deb) ...
Unpacking replacement gir1.2-polkit-1.0 ...
Preparing to replace gnome-accessibility-themes 2.32.1-0ubuntu1 (using .../gnome-accessibility-themes_3.0.0-0ubuntu1~build2_all.deb) ...
Unpacking replacement gnome-accessibility-themes ...
dpkg: error processing /var/cache/apt/archives/gnome-accessibility-themes_3.0.0-0ubuntu1~build2_all.deb (--unpack):
 trying to overwrite '/usr/share/themes/HighContrastInverse/index.theme', which is also in package gnome-themes-standard 2.91.93-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to replace libpolkit-backend-1-0 0.101-4~natty1 (using .../libpolkit-backend-1-0_0.102-1~natty1_amd64.deb) ...
Unpacking replacement libpolkit-backend-1-0 ...
Preparing to replace policykit-1 0.101-4~natty1 (using .../policykit-1_0.102-1~natty1_amd64.deb) ...
Unpacking replacement policykit-1 ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-accessibility-themes_3.0.0-0ubuntu1~build2_all.deb
N: Ignoring file 'apt-build' in directory '/etc/apt/sources.list.d/' as it has no filename extension
E: Sub-process /usr/bin/dpkg returned an error code (1)







```

I also tried it with package managers but not luck.


Is this a hopeless situation or is there a fix out there somewhere??


Just want to get Ubuntu Studio back



Thanks

---

### Post by oldos2er on 2011-08-05
Try clearing the apt cache, ```
sudo aptitude autoclean
``` then retry ```
sudo aptitude install -f
```

---

### Post by JASONFUSARO on 2011-08-05
I started another thread diff title I tried that also, there is a list of what I tried

[http://ubuntuforums.org/showthread.php?t=1819105](http://ubuntuforums.org/showthread.php?t=1819105)

---

### Post by jerrrys on 2011-08-05
you really shouldn't double post

i think post 2 is the fix

[http://ubuntuforums.org/showthread.php?t=1803619](http://ubuntuforums.org/showthread.php?t=1803619)

---

### Post by cariboo on 2011-08-05
Please don't create multiple threads on the same subject. I have merged two of your threads.

---

### Post by JASONFUSARO on 2011-08-05
> **jerrrys said:**
> you really shouldn't double post

i think post 2 is the fix

[http://ubuntuforums.org/showthread.php?t=1803619](http://ubuntuforums.org/showthread.php?t=1803619)



It appeared to work but
same ending message on everything I try


```


Reading package lists... Done
N: Ignoring file 'apt-build' in directory '/etc/apt/sources.list.d/' as it has no filename extension



```Apology for not seeing the do's and don'ts sooner unfortunate mistake.


The problem did in fact change somewhat and I thought a different topic would be a better forum as there is no way to change the topic.


I feel like I committed some heinous crime, you guys swoop in quick, it was an honest mistake I never read the do's and don'ts which is my responsibility, don't get me wrong, it is a good thing that you run a tight ship and we, (all members) should be grateful for that fact, but truly it was not done in a malicious manner, it was just to solve a problem.

EDIT************

I have reread the code of conduct of which there is some mention of double threading, and if you read my threads they are regarding different aspects, Cairo dock makes only a mention of my package managers which exist in the  package manager thread which mentions the package managers that I mentioned in the cairo dock thread which is about the blank screen which may or may not be related to the package manager which after investigating brought up that question, and why I posted that thread. Next time I will try to determine the best way to post a question and whether it relates or does not relate.

---

### Post by jerrrys on 2011-08-05
was not meant to be an attack, just a notification.  no need to take it personal. :(

could you post your  sources.list.d?

this just may be a conflict between the different package managers that your running.

and while on the subject of package managers.  synaptic package manager has been the standard for years. it has many more uses than just downloading packages.

the software center is undergoing a makeover right now and really just have to wait and see what happens with it.

what do i think of the software center?  i removed it with SPM :)

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

[http://www.ubuntugeek.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html](http://www.ubuntugeek.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html)

[http://www.ubuntugeek.com/synaptic-package-manager-beginners-guide-for-ubuntu-users.html](http://www.ubuntugeek.com/synaptic-package-manager-beginners-guide-for-ubuntu-users.html)

---

### Post by JASONFUSARO on 2011-08-05
> **jerrrys said:**
> was not meant to be an attack, just a notification.  no need to take it personal. :(

could you post your  sources.list.d?

this just may be a conflict between the different package managers that your running.

and while on the subject of package managers.  synaptic package manager has been the standard for years. it has many more uses than just downloading packages.

the software center is undergoing a makeover right now and really just have to wait and see what happens with it.

what do i think of the software center?  i removed it with SPM :)

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

[http://www.ubuntugeek.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html](http://www.ubuntugeek.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html)

[http://www.ubuntugeek.com/synaptic-package-manager-beginners-guide-for-ubuntu-users.html](http://www.ubuntugeek.com/synaptic-package-manager-beginners-guide-for-ubuntu-users.html)



Here it is, at some point I was getting an error when running an apt command about a file being empty, and I believe it was the apt-build.list so I copied in the save and reran but got the same empty message, so the apt command was somehow deleting the contents??? 

```

jason@UbuntuStudio64bit:/etc/apt$ ls sources.list.d
apt-build                      screenlets-ppa-natty.list.save
apt-build.list                 yannubuntu-boot-repair-dev-natty.list
apt-build.list.save            yannubuntu-boot-repair-dev-natty.list.save
gnome3-team-gnome3-natty.list  yannubuntu-boot-repair-natty.list
opera.list                     yannubuntu-boot-repair-natty.list.save
opera.list.save                yannubuntu-os-uninstaller-dev-natty.list
screenlets-ppa-natty.list      yannubuntu-os-uninstaller-dev-natty.list.save


```Thanks

No offense taken

as I stated previously

> 
 don't get me wrong, it is a good thing that you run a tight ship and [COLOR=Red]we, (all members) should be grateful for that fact,[/COLOR]
P.S.  I know now that checking out different packages cause conflicts, live and learn, I am in my experimental Linux usage check out everything I can stage.

Eventually I will settle in, choose one distro, and one set of packages and really get to enjoy everything.


:biggrin:

---

### Post by jerrrys on 2011-08-06
never used yannubuntu so cant help you on that.  since your just playing around, i say just use it.  its just on the ignore list.

PPA's are a collection of the latest software releases and will not always work well 

and one more plug for SPM.  it will tell your what your downloading and if any conflicts exist.  and this is done before the download starts.  have fun

---

