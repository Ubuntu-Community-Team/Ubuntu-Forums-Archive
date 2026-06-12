---
title: "Update Manager Problem"
date: 2010-11-12
forum: General Help
---

### Post by Wuxin on 2010-11-12
I am new to Ubuntu so you will have to address my issue in very specific, but easy to understand terms.  So far I've been happy with the general performance of Ubuntu, but when I went to use the Update Manager, I received the following message: "Failed to download repository information--Check your Internet connection."  I've been searching relentlessly online to find a satisfactory resolution of this problem, but nothing I found thus far solves the issue.  Others have cited this problem with updates on Ubuntu, but no one has either solved it or solved it in a language that I can understand.  Meanwhile, my updates are mounting up and I have no way to install them.  Does anyone know how this problem can be fixed?  Again, I like Ubuntu but this particular problem has been driving me crazy!

---

### Post by rcayea on 2010-11-12
Have you selected the repositories you want in the Software Sources area?

---

### Post by 73ckn797 on 2010-11-12
See attached images. Ignore the 3rd & 4th sources (Medibuntu) of the second image. Those were added in addition to the standard choices.

---

### Post by Wuxin on 2010-11-12
Yes, I have done all the above and still it doesn't work.  (There are changes in my listings since I'm using Ubuntu 10.10 but it seems to be in place.  Anything further?

---

### Post by garvinrick4 on 2010-11-12
Open a terminal: Applications to Accessories to Terminal and copy and paste:
```
sudo apt-get update
```
That will refresh your sources.list

---

### Post by Wuxin on 2010-11-13
Okay, I gave that command and received the following in the terminal:

Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [65B]
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release.gpg [197B]                
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en                
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en_US             
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en            
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en_US         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) free Release.gpg                             
Ign [http://packages.medibuntu.org/maverick/](http://packages.medibuntu.org/maverick/) free/non-free Translation-en       
Ign [http://packages.medibuntu.org/maverick/](http://packages.medibuntu.org/maverick/) free/non-free Translation-en_US    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release                             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg                          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US       
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US    
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) free Release                                 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free Sources/DiffIndex              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free Sources/DiffIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free i386 Packages/DiffIndex        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free i386 Packages/DiffIndex    
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports Release.gpg                
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) free/non-free Sources                        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) free/non-free i386 Packages                  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free Sources                        
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free Sources          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free i386 Packages
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed Release.gpg [198B]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free i386 Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) free/non-free Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) free/non-free i386 Packages
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports Release          
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) free/non-free Sources              
  404  Not Found
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed Release [31.4kB]
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) free/non-free i386 Packages              
  404  Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources 
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
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/multiverse i386 Packages
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/restricted i386 Packages [14B]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/main i386 Packages [33.2kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/multiverse i386 Packages [14B]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/universe i386 Packages [18.0kB]
Fetched 83.1kB in 2s (35.7kB/s)                         
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch [http://packages.medibuntu.org/maverick/dists/free/non-free/source/Sources.gz](http://packages.medibuntu.org/maverick/dists/free/non-free/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://packages.medibuntu.org/maverick/dists/free/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/maverick/dists/free/non-free/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

Now what do I do with all this information?  It appears there are some "errors" and "failed to fetch" items--what does this mean?  Thank you for your input; it is appreciated!

---

### Post by Wuxin on 2010-11-13
I just attempted another Update Manager install and received the following reply:

Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.

Now this is bogus!  I have authenticated all of my listed sources--I purposely didn't
want to place any limits on what the manager would install.  Even with that, I'm still getting nowhere.  What is inhibiting my Update Manager from performing its function?

Thank you.

---

### Post by arpanaut on 2010-11-13
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Run the command under "Adding the Repository"
It seems that you have not imported the correct medibuntu GPG key
That "should" fix it.
[B]
[/B]

---

### Post by Wuxin on 2010-11-14
A thought occurred to me: my router has a firewall and it could be that the firewall is preventing system updates from being installed.  My firewall has an option called "firewall pinholes" which allow specific servers to enter my system without being interpreted as viruses, etc.  I'm beginning to think that the firewall sees attempts to install system updates as a malicious intruder.  How do I create a pinhole that would allow Ubuntu to perform update installations?  Does Ubuntu have a specified name that would be recognizable to my router/firewall?  Thanks everyone for your generous help and support.

---

### Post by mcduck on 2010-11-15
nope, arpananut is correct and you need to fix your medibuntu source and install the GPG key for it.

See the 404 errors in "apt-get update" output about Medibuntu? I don't think hey actually have a repository called "free/non-free" as in your apt-get output, the repositories they have are "maverick/free" and "maverick/non-free".

Also the "untruested packages" is a result from missing the GPG key for some repository. Medibuntu, in your case.

---

### Post by Wuxin on 2010-11-15
No, I am sorry Arpanaut and McDuck, but the command
you advised accomplished nothing.  When trying to execute
Update Manager I still receive the following reply:

Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.

Am I alone in having difficulty with this or have others reported
problems with the Update Manager?  This is very frustrating because
I'm sure I'm missing out on updates that could be helpful to my
system.  What do you advise from here?

Again, thank you one and all for your assistance and patience!

---

### Post by garvinrick4 on 2010-11-23
deb [http://mirror.pnl.gov/ubuntu/](http://mirror.pnl.gov/ubuntu/) natty-security main restricted
# deb-src [http://mirror.pnl.gov/ubuntu/](http://mirror.pnl.gov/ubuntu/) natty-security main restricted
deb [http://mirror.pnl.gov/ubuntu/](http://mirror.pnl.gov/ubuntu/) natty-security universe
# deb-src [http://mirror.pnl.gov/ubuntu/](http://mirror.pnl.gov/ubuntu/) natty-security universe
deb [http://mirror.pnl.gov/ubuntu/](http://mirror.pnl.gov/ubuntu/) natty-security multiverse
# deb-src [http://mirror.pnl.gov/ubuntu/](http://mirror.pnl.gov/ubuntu/) natty-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick free non-free
# deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) natty main
#deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

### medibuntu free non-free is ok but as mcduck stated only needed a medibuntu key
as a fix.  [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
 
#Update Manager does what you tell it to do with settings in software sources
in the 5 tabs of settings. All ppa's including medibuntu need GPG keys installed and our
normally with the site you have found the ppa you want to install. Then you have to:
```
sudo apt-get update
```#run above in terminal to install in /etc/apt/sources.list
###For you new users do your software sources first thing after install:

---

