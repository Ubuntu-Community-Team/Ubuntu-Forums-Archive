---
title: "hellp cant update"
date: 2010-12-01
forum: General Help
---

### Post by calamardo85 on 2010-12-01
sorry i tried every solution posted i could find but they didn't solve my problem im using karmic    every time i try to update with update manager i can't click in the install button, because it is turned off     the sudo apt-get update  sudo apt-get upgrade doesent work either i suppose because after i do it the update manager counts to the same amount of packages needed to be installed    i also unchecked all the boxes in software sources>other sources and tried to update selecting only one by one and nothing happens    please help

---

### Post by NLMark1983 on 2010-12-01
Cn you post a screenshot or copy the text in the terminal when you try the apt-get command? This way we might tell you what is or isn't happening.

---

### Post by calamardo85 on 2010-12-01
```
 
ricardo@ricardo:~$ sudo apt-get update && sudo apt-get upgrade [sudo] password for ricardo: 
Hit http://mirrors.us.kernel.org karmic Release.gpg
Ign http://mirrors.us.kernel.org karmic/main Translation-en_US
Ign http://mirrors.us.kernel.org karmic/restricted Translation-en_US
Ign http://mirrors.us.kernel.org karmic/universe Translation-en_US
Ign http://mirrors.us.kernel.org karmic/multiverse Translation-en_US
Hit http://mirrors.us.kernel.org karmic-updates Release.gpg
Ign http://mirrors.us.kernel.org karmic-updates/main Translation-en_US
Ign http://mirrors.us.kernel.org karmic-updates/restricted
 Translation-en_US 
   Ign http://mirrors.us.kernel.org karmic-updates/universe Translation-en_US 
     Ign http://mirrors.us.kernel.org karmic-updates/multiverse Translation-en_US 
   Hit http://mirrors.us.kernel.org karmic-security Release.gpg  
                  Ign http://mirrors.us.kernel.org karmic-security/main Translation-en_US 
        Ign http://mirrors.us.kernel.org karmic-security/restricted Translation-en_US  
Ign http://mirrors.us.kernel.org karmic-security/universe Translation-en_US   
  Ign http://mirrors.us.kernel.org karmic-security/multiverse Translation-en_US  
Hit http://mirrors.us.kernel.org karmic Release
Hit http://mirrors.us.kernel.org karmic-updates Release
Hit http://packages.medibuntu.org karmic Release.gpg
                 Hit http://mirrors.us.kernel.org karmic-security Release
                        Hit http://mirrors.us.kernel.org karmic/main Packages
                           Hit http://mirrors.us.kernel.org karmic/restricted Packages
                     Hit http://mirrors.us.kernel.org karmic/universe Packages
  Hit http://mirrors.us.kernel.org karmic/multiverse Packages
Hit http://mirrors.us.kernel.org karmic-updates/main Packages
Hit http://mirrors.us.kernel.org karmic-updates/restricted Packages
Hit http://mirrors.us.kernel.org karmic-updates/universe Packages
Hit http://mirrors.us.kernel.org karmic-updates/multiverse Packages
Hit http://mirrors.us.kernel.org karmic-security/main Packages
Hit http://mirrors.us.kernel.org karmic-security/restricted Packages
Hit http://mirrors.us.kernel.org karmic-security/universe Packages
Ign http://packages.medibuntu.org karmic/free Translation-en_US
Hit http://mirrors.us.kernel.org karmic-security/multiverse Packages
            Ign http://packages.medibuntu.org karmic/non-free Translation-en_US
             Hit http://packages.medibuntu.org karmic Release
           Hit http://packages.medibuntu.org karmic/free Packages
     Hit http://packages.medibuntu.org karmic/non-free Packages
Hit http://packages.medibuntu.org karmic/free Sources
      Hit http://packages.medibuntu.org karmic/non-free Sources
  Reading package lists... Done
                              Reading package lists... Done
Building dependency tree
        Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ricardo@ricardo:~$ 
 
``` thanks i couldnt paste to look more readable total noob hehe

---

### Post by calamardo85 on 2010-12-01
```
$ lspci
ricardo@ricardo:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for ricardo: 
Hit http://mirrors.us.kernel.org karmic Release.gpg
Ign http://mirrors.us.kernel.org karmic/main Translation-en_US
Ign http://mirrors.us.kernel.org karmic/restricted Translation-en_US
Ign http://mirrors.us.kernel.org karmic/universe Translation-en_US
Ign http://mirrors.us.kernel.org karmic/multiverse Translation-en_US
Hit http://mirrors.us.kernel.org karmic-updates Release.gpg
Ign http://mirrors.us.kernel.org karmic-updates/main Translation-en_US
Ign http://mirrors.us.kernel.org karmic-updates/restricted Translation-en_US   
Ign http://mirrors.us.kernel.org karmic-updates/universe Translation-en_US     
Ign http://mirrors.us.kernel.org karmic-updates/multiverse Translation-en_US   
Hit http://mirrors.us.kernel.org karmic-security Release.gpg                   
Ign http://mirrors.us.kernel.org karmic-security/main Translation-en_US        
Ign http://mirrors.us.kernel.org karmic-security/restricted Translation-en_US  
Ign http://mirrors.us.kernel.org karmic-security/universe Translation-en_US    
Ign http://mirrors.us.kernel.org karmic-security/multiverse Translation-en_US  
Hit http://mirrors.us.kernel.org karmic Release
Hit http://mirrors.us.kernel.org karmic-updates Release
Hit http://packages.medibuntu.org karmic Release.gpg                
Hit http://mirrors.us.kernel.org karmic-security Release                       
Hit http://mirrors.us.kernel.org karmic/main Packages                          
Hit http://mirrors.us.kernel.org karmic/restricted Packages                    
Hit http://mirrors.us.kernel.org karmic/universe Packages 
Hit http://mirrors.us.kernel.org karmic/multiverse Packages
Hit http://mirrors.us.kernel.org karmic-updates/main Packages
Hit http://mirrors.us.kernel.org karmic-updates/restricted Packages
Hit http://mirrors.us.kernel.org karmic-updates/universe Packages
Hit http://mirrors.us.kernel.org karmic-updates/multiverse Packages
Hit http://mirrors.us.kernel.org karmic-security/main Packages
Hit http://mirrors.us.kernel.org karmic-security/restricted Packages
Hit http://mirrors.us.kernel.org karmic-security/universe Packages
Ign http://packages.medibuntu.org karmic/free Translation-en_US
Hit http://mirrors.us.kernel.org karmic-security/multiverse Packages           
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US            
Hit http://packages.medibuntu.org karmic Release          
Hit http://packages.medibuntu.org karmic/free Packages    
Hit http://packages.medibuntu.org karmic/non-free Packages
Hit http://packages.medibuntu.org karmic/free Sources     
Hit http://packages.medibuntu.org karmic/non-free Sources 
Reading package lists... Done                             
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ricardo@ricardo:~$ 


```

---

### Post by yetiman64 on 2010-12-01
> 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. would suggest to me that your system is up to date and there is nothing for the commands to do.

If this is the case then the "Install Updates" button on the Update manager _will_ be greyed out as there are no updates to install. 

No other errors showed up in the terminal output you posted. That is everything looks OK. How long has it been since you last had updates available ?

---

### Post by calamardo85 on 2010-12-01
> **yetiman64 said:**
> would suggest to me that your system is up to date and there is nothing for the commands to do.

If this is the case then the "Install Updates" button on the Update manager _will_ be greyed out as there are no updates to install. 

No other errors showed up in the terminal output you posted. That is everything looks OK. How long has it been since you last had updates available ?


thanks for cheking it i swear i spent half the day trying to update because i cant use pidgin any more ang when tryed to update about 60 updates allways came up in the update manager but never got  installed, so i tried every thred un the subject. dont know wich worked, all came from trying to use pidgin i unistalled it an put emesene all working good apparently
thanks again for your attention

---

### Post by ghostborg on 2010-12-03
One of my Ubuntu 10.10 Gnome systems does not update like the others.
Once Update manager is launched indicating there are updates available, I click on install updates, Authentication box appears, type in password and click authenticate and nothing happens. I have to Force quit the authentication box and then close Update manager and launch it again then it works on the second try.

---

### Post by sikander3786 on 2010-12-03
Might be you had some daily build ppas enabled under Software Sources > Other Software Tab?

---

