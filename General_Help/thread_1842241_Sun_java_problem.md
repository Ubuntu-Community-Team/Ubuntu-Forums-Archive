---
title: "Sun java problem"
date: 2011-09-11
forum: General Help
---

### Post by somoking on 2011-09-11
Recently i tried to install wine and i got this
 
 > File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the sun-java6-jre package. This might mean you need to manually fix this package.
After looking through other failed download attempts i noticed that all my problems end with 
> SystemError: E:I wasn't able to locate file for the sun-java6-jre package. This might mean you need to manually fix this package.
I do not know how to manually fix the package any help

---

### Post by mmsmc on 2011-09-11
ok, how are you installing it(synaptics, through website?)

---

### Post by raja.genupula on 2011-09-11
just type wine in your terminal 
then its gonna give you the present supported versions it have . install from there or use synaptic(as our above friend said )

---

### Post by somoking on 2011-09-21
> **mmsmc said:**
> ok, how are you installing it(synaptics, through website?)
I tried to install it both through the website and through software center

> **raja.genupula said:**
> just type wine in your terminal 
then its gonna give you the present supported versions it have . install  from there or use synaptic(as our above friend said )
i also tried that it did not work
this is what i got which i assume says that nothing was installed
> somoking@somoking-NP187AAR-ABA-s5120f:~$ wine
The program 'wine' can be found in the following packages:
 * wine1.2
 * wine1.3
 * wine1.0
Try: sudo apt-get install <selected package>
somoking@somoking-NP187AAR-ABA-s5120f:~$ sudo apt-get install <selected package>bash: syntax error near unexpected token `newline'
somoking@somoking-NP187AAR-ABA-s5120f:~$ sudo apt-get install wine1.3
[sudo] password for somoking: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 sun-java6-jre : Depends: sun-java6-bin (>= 6.26-1natty1) but it is not going to be installed or
                          ia32-sun-java6-bin (>= 6.26-1natty1) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
 wine1.3 : Depends: libesd0 (>= 0.2.35) but it is not going to be installed
           Depends: libmpg123-0 (>= 1.6.2) but it is not going to be installed
           Depends: libopenal1 but it is not going to be installed
           Recommends: ttf-symbol-replacement-wine1.3 but it is not going to be installed
           Recommends: ttf-umefont but it is not going to be installed
           Recommends: ttf-droid but it is not going to be installed
           Recommends: ttf-mscorefonts-installer but it is not going to be installed
           Recommends: winbind but it is not going to be installed
           Recommends: wine1.3-gecko but it is not going to be installed
           Recommends: gnome-exe-thumbnailer but it is not going to be installed or
                       kdebase-runtime but it is not going to be installed
           Recommends: winetricks but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
somoking@somoking-NP187AAR-ABA-s5120f:~$ apt-get -f install libesd0
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
somoking@somoking-NP187AAR-ABA-s5120f:~$ 



And just to make this clear my problem is not wine its java in general anytime i try to use a java program it will bring me up with an error saying it can not find java folder

---

### Post by raja.genupula on 2011-09-21
> **somoking said:**
> I tried to install it both through the website and through software center


i also tried that it did not work
this is what i got which i assume says that nothing was installed



And just to make this clear my problem is not wine its java in general anytime i try to use a java program it will bring me up with an error saying it can not find java folder

Hey , did you interrupted any installation which is with apt-get or updating ? 
restart your system and try again .

one more thing i need ```
sudo apt-get update
```  output . paste that output here . 

all the best . sorry for late reply .

---

### Post by psrdotcom on 2011-09-21
Have to tried $ sudo wine .. 

Since, you are saying like, its java problem.

Try to open Java Runtime and check whether it is opening or not?

If it not opening .. then try to uninstall and install the java once.

Might be your problem will get resolved.

Try to use sudo when you are trying to install/uninstall any software.. Some directories needs root permission while installing or unistalling..

Have a nice day :)

---

### Post by raja.genupula on 2011-09-21
```
somoking@somoking-NP187AAR-ABA-s5120f:~$ apt-get -f install libesd0
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```
hey i have not seen the last line properly.
ok do this 

```
sudo apt-get -f install
```
and then 
```
sudo apt-get install wine1.3
```
and let me know what you got

---

### Post by somoking on 2011-09-27
> **raja.genupula said:**
> Hey , did you interrupted any installation which is with apt-get or updating ? 
restart your system and try again .

one more thing i need ```
sudo apt-get update
```  output . paste that output here . 

all the best . sorry for late reply .

heres the output
somoking@somoking-NP187AAR-ABA-s5120f:~$ sudo apt-get update
[sudo] password for somoking: 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                         
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                   
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg [198 B]  
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]                        
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg [198 B] 
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release [31.4 kB]              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release [31.4 kB]             
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources [69.6 kB]         
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex               
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources [107 kB]         
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources [14 B]      
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources [11.3 kB]     
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources [657 B]    
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages [188 kB]   
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages [14 B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages [40.1 kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources [753 B]   
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources [27.0 kB]   
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources [1,888 B] 
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages [323 kB]  
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages [2,077 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                      
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages [839 B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages [94.2 kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages [4,264 B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
Fetched 934 kB in 5s (177 kB/s)
Reading package lists... Done
somoking@somoking-NP187AAR-ABA-s5120f:~$ 

After restarting ubuntu i learned that it is time sensitive
when i first restarted system it was working fine but just the same after 4 days i come up with the same problem
here is what happens when i try to download anything
> Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the sun-java6-jre package. This might mean you need to manually fix this package.


here is what the pop up literally say 
> There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks

---

### Post by raja.genupula on 2011-09-27
Look at my post 7, I am sure its gonna solve your issue.
try that . 

All The best.

---

### Post by g123386761 on 2011-10-01
> **raja.genupula said:**
> Look at my post 7, I am sure its gonna solve your issue.
try that . 

All The best.
OMG TYSM!! I was unable to do anything until I read this post :D! Thanks!

---

### Post by somoking on 2011-10-02
OK so i have followed your instructions
yet i still cannot install it 
this time for a stupider reason i cannot accept the terms of use agreement 
i have pressed enter i have typed ok i have fooled around with it for quite awhile is there something stupid i missed

---

### Post by Shehab Ahmed on 2011-10-02
> **somoking said:**
> OK so i have followed your instructions
yet i still cannot install it 
this time for a stupider reason i cannot accept the terms of use agreement 
i have pressed enter i have typed ok i have fooled around with it for quite awhile is there something stupid i missed

you can accept it by choosing the OK using arrows in your keyboard then click the space-bar
:)

---

