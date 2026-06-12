---
title: "Package Manager error"
date: 2010-12-23
forum: General Help
---

### Post by Mr. McD on 2010-12-23
I am getting the following error when trying to open the Package Manager on my laptop.
This is Ubuntu 10.10

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_maverick_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by sikander3786 on 2010-12-23
Welcome to the forums :-)

From Applications > Accessories > Terminal post the output of these commands.

```
sudo rm /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_maverick_main_binary-i386_Packages
```

```
sudo apt-update && sudo apt-get upgrade
```

While posting, click the # icon in post menu and paste your text in between the generated code tags to make it easy to read.

---

### Post by Mr. McD on 2010-12-23
> **sikander3786 said:**
> Welcome to the forums :-)

From Applications > Accessories > Terminal post the output of these commands.

```
sudo rm /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_maverick_main_binary-i386_Packages
```  rm: cannot remove `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_maverick_main_b': No such file or directory
rm: cannot remove `inary-i386_Packages': No such file or directory

 

```
sudo apt-update && sudo apt-get upgrade
```While posting, click the # icon in post menu and paste your text in between the generated code tags to make it easy to read.

stephen@stephen-ME051:~$ sudo apt-get update && apt-get upgrade
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg
Ign [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/) maverick/main Translation-en            
Ign [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/) maverick/main Translation-en_US         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                                                               
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en                                               
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                                                            
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en                                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                                                     
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg                                                            
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                                
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en                                  
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en_US                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                                                    
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US                                      
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                                                                
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US                                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                                                    
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US                                  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en         
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en         
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US                            
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en                                 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US                              
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US                                         
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en                                      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US                                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en                                      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US                                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                                                                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                                                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg                              
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en              
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US           
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_maverick_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by sikander3786 on 2010-12-23
> E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_maverick_main_[COLOR="Red"]b i[/COLOR]nary-i386_Packages

That space between 'b' and 'i' sounds strange.

Anyhow,

```
gksudo nautilus
```

Open up /var/lib/apt/lists from your root partition and delete the file named us.archive.ubuntu.com_ubuntu_dists_maverick_main_b inary-i386_Packages and try apt-get update again.

Be cautious, you'll be running Nautilus as root so don't delete/modify anything by mistake ;-)

---

### Post by Mr. McD on 2010-12-23
That fixed the problem. I can now access the Package Manager.

Thanks much.




> **sikander3786 said:**
> That space between 'b' and 'i' sounds strange.

Anyhow,

```
gksudo nautilus
```Open up /var/lib/apt/lists from your root partition and delete the file named us.archive.ubuntu.com_ubuntu_dists_maverick_main_b inary-i386_Packages and try apt-get update again.

Be cautious, you'll be running Nautilus as root so don't delete/modify anything by mistake ;-)

---

