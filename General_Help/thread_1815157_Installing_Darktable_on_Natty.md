---
title: "Installing Darktable on Natty"
date: 2011-07-30
forum: General Help
---

### Post by m005k on 2011-07-30
Trying to install Darktable on Natty. At this point it seem I have entered the info to add and update the repository ok, but it isn't showinmg up as an option to install in the Ubuntu Software Center. Here is my type in:

ubuntu@ubuntu:~$ sudo add-apt-repository ppa:pmjdebruijn/darktable-release
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 18002889824B24A6F47FCF9C40C18E9EC07EE05F
gpg: requesting key C07EE05F from hkp server keyserver.ubuntu.com
gpg: key C07EE05F: "Launchpad PPA for Pascal de Bruijn" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty InRelease
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main TranslationIndex
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted TranslationIndex
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main Translation-en
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates InRelease                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted TranslationIndex      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe TranslationIndex        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Sources       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe Sources         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main i386 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe i386 Packages   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main TranslationIndex    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Translation-en              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Translation-en        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Translation-en          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Translation-en_US   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Translation-en      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Reading package lists... Done
ubuntu@ubuntu:~$ 


What am I doing wrong?

Mike

---

### Post by m005k on 2011-07-30
Opps forgot to do this sudo apt-get install darktable. Looked like it install, but I can't find it.

Mike

---

### Post by m005k on 2011-07-30
I guess I need to read directions better. Their PDF says to run it from terminal and it came up fine. If someone wants to tell me how to get a link on my desktop to run it and not go through the terminal that would be nice!

---

### Post by cleary on 2011-08-28
it's in your application menu - if you're using natty + unity, you'll find it by hitting the ubuntu key and typing "darktable" - 

It'll then show you an icon that you can use to start, or copy to your launcher panel

If you're using the gnome interface, you should find the link under the graphics menu (which you can then right click to copy to your desktop or drag up to your quick launch area).

---

