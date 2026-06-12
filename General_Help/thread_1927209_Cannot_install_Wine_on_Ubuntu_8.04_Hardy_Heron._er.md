---
title: "Cannot install Wine on Ubuntu 8.04 Hardy Heron. error: Unauthenticated package"
date: 2012-02-17
forum: General Help
---

### Post by kingnug on 2012-02-17
Thank you for your time. I recently removed Wine via synaptic package manager from my system. Now I would like to install it again. When i go to "Add/Remove programs" and select Wine, select apply, then put in my password then when the summary window comes up it says 

Apply the following changes?
This is your last opportunity to look through the list
of marked changes before they are applied.

WARNING

You are about to install software that cant be 
authenticated! Doing this could allow a mallicious individual 
to damage or take control of your system.

---------------------------------------------------------------
 V NOT AUTHENTICATED
   Wine

 V To be installed
   Wine

 V Unchanged 
   ...
   ...
---------------------------------------------------------------

  **(Show Details): 
  wine (version1.2~winehq0~ubuntu~8.04-0ubuntu1) will be installed

I click apply and then an error message:

"The following details are provided:"
W: Failed to fetch [http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_1.2~winehq0~ubuntu~8.04-0ubuntu1_i386.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_1.2~winehq0~ubuntu~8.04-0ubuntu1_i386.deb)
  404 Not Found
 
And the only option is to close the window... Any help would be appreciated. Thank you

---

### Post by cortman on 2012-02-17
Well, the first solution that comes to mind is upgrade your Ubuntu. 8.04 is two years out of support already. I would recommend upgrading to 10.04 (LTS) and then to 12.04 when it's released in April of this year.
If you prefer not to, for whatever reason, I would ask you to run

```
sudo apt-get update
```

and post the results. Also

```
cat /etc/apt/sources.list
```

And post that as well. It looks as though you may need to re-add the Wine repository.

---

### Post by kingnug on 2012-02-17
Thank you for your response. I used your first command and got this...

Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg                
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages    
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages
  404 Not Found
W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/hardy/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/apt/dists/hardy/main/binary-i386/Packages.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


Should i use the second command now??

---

### Post by cortman on 2012-02-17
Those Wine repositories are nonexistent. You can re-set them up (if indeed they still provide support for 8.04, which I'm not sure of) by following [this tutorial]("www.winehq.org/download/ubuntu").

---

### Post by kingnug on 2012-02-17
As always I appreciate the help, I guess it is just time to get a better computer... i am on a 14Gb dell and i don't know if it will be able to run a newer version of Ubuntu. thank you for your time

---

### Post by cortman on 2012-02-17
Lubuntu 11.10 (latest version) would probably run like a champ on your computer; I can't tell how old it is from the info, but lubuntu is built for low spec machines, and is still quite up-to-date.
Either that or you could try Bodhi Linux, which is Ubuntu based and uses e17 DE. Jeff Hoogland (its Creator) says it'll run on a rubber band and a squirrel.

---

### Post by kingnug on 2012-02-18
cool thanx. i'll try that

---

