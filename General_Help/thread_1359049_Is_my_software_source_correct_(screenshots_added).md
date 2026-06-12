---
title: "Is my software source correct (screenshots added)"
date: 2009-12-19
forum: General Help
---

### Post by emigrant on 2009-12-19
hi all,
can you please verify that my source list is correct.
i couldnt update the system :(
i get this error:
```

$ sudo apt-get update
[sudo] password for emigrant: 
Ign http://archive.canonical.com jaunty Release.gpg                 
Ign http://us.archive.ubuntu.com jaunty Release.gpg                            
Ign http://archive.canonical.com jaunty/partner Translation-en_US              
Ign http://lk.archive.ubuntu.com jaunty-backports Release.gpg       
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US                 
Ign http://archive.canonical.com jaunty Release                                
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US     
Ign http://lk.archive.ubuntu.com jaunty-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US           
Ign http://lk.archive.ubuntu.com jaunty-backports/restricted Translation-en_US 
Ign http://archive.canonical.com jaunty/partner Packages                       
Ign http://us.archive.ubuntu.com jaunty-updates Release.gpg                    
Ign http://lk.archive.ubuntu.com jaunty-backports/universe Translation-en_US   
Ign http://archive.canonical.com jaunty/partner Sources                        
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US         
Ign http://lk.archive.ubuntu.com jaunty-backports/multiverse Translation-en_US
Ign http://archive.canonical.com jaunty/partner Packages                       
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US   
Ign http://lk.archive.ubuntu.com jaunty-backports Release                      
Ign http://archive.canonical.com jaunty/partner Sources                        
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://lk.archive.ubuntu.com jaunty-backports/main Packages                
Err http://archive.canonical.com jaunty/partner Packages             
  400 Bad Request
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Ign http://lk.archive.ubuntu.com jaunty-backports/restricted Packages          
Err http://archive.canonical.com jaunty/partner Sources                        
  400 Bad Request
Ign http://us.archive.ubuntu.com jaunty-security Release.gpg                   
Ign http://lk.archive.ubuntu.com jaunty-backports/universe Packages    
Ign http://us.archive.ubuntu.com jaunty-security/main Translation-en_US
Ign http://lk.archive.ubuntu.com jaunty-backports/multiverse Packages  
Ign http://us.archive.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://lk.archive.ubuntu.com jaunty-backports/main Sources                 
Ign http://us.archive.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://lk.archive.ubuntu.com jaunty-backports/restricted Sources           
Ign http://us.archive.ubuntu.com jaunty-security/multiverse Translation-en_US
Ign http://lk.archive.ubuntu.com jaunty-backports/universe Sources             
Ign http://us.archive.ubuntu.com jaunty Release
Ign http://lk.archive.ubuntu.com jaunty-backports/multiverse Sources           
Ign http://us.archive.ubuntu.com jaunty-updates Release                
Ign http://us.archive.ubuntu.com jaunty-security Release                       
Ign http://lk.archive.ubuntu.com jaunty-backports/main Packages        
Ign http://us.archive.ubuntu.com jaunty/main Packages                          
Ign http://lk.archive.ubuntu.com jaunty-backports/restricted Packages
Ign http://us.archive.ubuntu.com jaunty/restricted Packages                    
Ign http://lk.archive.ubuntu.com jaunty-backports/universe Packages
Ign http://lk.archive.ubuntu.com jaunty-backports/multiverse Packages          
Ign http://lk.archive.ubuntu.com jaunty-backports/main Sources                 
Ign http://lk.archive.ubuntu.com jaunty-backports/restricted Sources           
Ign http://us.archive.ubuntu.com jaunty/main Sources                   
Ign http://lk.archive.ubuntu.com jaunty-backports/universe Sources             
Ign http://us.archive.ubuntu.com jaunty/restricted Sources             
Ign http://lk.archive.ubuntu.com jaunty-backports/multiverse Sources           
Ign http://us.archive.ubuntu.com jaunty/universe Packages              
Ign http://us.archive.ubuntu.com jaunty/universe Sources                       
Err http://lk.archive.ubuntu.com jaunty-backports/main Packages
  400 Bad Request
Ign http://us.archive.ubuntu.com jaunty/multiverse Packages
Ign http://us.archive.ubuntu.com jaunty/multiverse Sources
Err http://lk.archive.ubuntu.com jaunty-backports/restricted Packages          
  400 Bad Request
Ign http://us.archive.ubuntu.com jaunty-updates/main Packages          
Err http://lk.archive.ubuntu.com jaunty-backports/universe Packages            
  400 Bad Request
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Packages    
Err http://lk.archive.ubuntu.com jaunty-backports/multiverse Packages          
  400 Bad Request
Ign http://us.archive.ubuntu.com jaunty-updates/main Sources           
Err http://lk.archive.ubuntu.com jaunty-backports/main Sources                 
  400 Bad Request
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Sources     
Err http://lk.archive.ubuntu.com jaunty-backports/restricted Sources           
  400 Bad Request
Ign http://us.archive.ubuntu.com jaunty-updates/universe Packages      
Err http://lk.archive.ubuntu.com jaunty-backports/universe Sources             
  400 Bad Request
Ign http://us.archive.ubuntu.com jaunty-updates/universe Sources       
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Packages            
Err http://lk.archive.ubuntu.com jaunty-backports/multiverse Sources   
  400 Bad Request
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Sources     
Ign http://us.archive.ubuntu.com jaunty-security/main Packages
Ign http://us.archive.ubuntu.com jaunty-security/restricted Packages
Ign http://us.archive.ubuntu.com jaunty-security/main Sources
Ign http://us.archive.ubuntu.com jaunty-security/restricted Sources
Ign http://us.archive.ubuntu.com jaunty-security/universe Packages
Ign http://us.archive.ubuntu.com jaunty-security/universe Sources
Ign http://us.archive.ubuntu.com jaunty-security/multiverse Packages
Ign http://us.archive.ubuntu.com jaunty-security/multiverse Sources
Ign http://us.archive.ubuntu.com jaunty/main Packages
Ign http://us.archive.ubuntu.com jaunty/restricted Packages
Ign http://us.archive.ubuntu.com jaunty/main Sources
Ign http://us.archive.ubuntu.com jaunty/restricted Sources
Ign http://us.archive.ubuntu.com jaunty/universe Packages
Ign http://us.archive.ubuntu.com jaunty/universe Sources
Ign http://us.archive.ubuntu.com jaunty/multiverse Packages
Ign http://us.archive.ubuntu.com jaunty/multiverse Sources
Ign http://us.archive.ubuntu.com jaunty-updates/main Packages
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Packages
Ign http://us.archive.ubuntu.com jaunty-updates/main Sources
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Sources
Ign http://us.archive.ubuntu.com jaunty-updates/universe Packages
Ign http://us.archive.ubuntu.com jaunty-updates/universe Sources
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
Ign http://us.archive.ubuntu.com jaunty-security/main Packages
Ign http://us.archive.ubuntu.com jaunty-security/restricted Packages
Ign http://us.archive.ubuntu.com jaunty-security/main Sources
Ign http://us.archive.ubuntu.com jaunty-security/restricted Sources
Ign http://us.archive.ubuntu.com jaunty-security/universe Packages
Ign http://us.archive.ubuntu.com jaunty-security/universe Sources
Ign http://us.archive.ubuntu.com jaunty-security/multiverse Packages
Ign http://us.archive.ubuntu.com jaunty-security/multiverse Sources
Err http://us.archive.ubuntu.com jaunty/main Packages
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty/restricted Packages
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty/main Sources
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty/restricted Sources
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty/universe Packages
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty/universe Sources
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty/multiverse Packages
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty/multiverse Sources
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-updates/main Packages
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-updates/restricted Packages
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-updates/main Sources
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-updates/restricted Sources
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-updates/universe Packages
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-updates/universe Sources
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-security/main Packages
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-security/restricted Packages
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-security/main Sources
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-security/restricted Sources
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-security/universe Packages
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-security/universe Sources
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-security/multiverse Packages
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-security/multiverse Sources
  400 Bad Request
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/jaunty/partner/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/jaunty/partner/source/Sources  400 Bad Request

W: Failed to fetch http://lk.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://lk.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://lk.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://lk.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://lk.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/source/Sources  400 Bad Request

W: Failed to fetch http://lk.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/source/Sources  400 Bad Request

W: Failed to fetch http://lk.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/source/Sources  400 Bad Request

W: Failed to fetch http://lk.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/source/Sources  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources  400 Bad Request

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by Darael on 2009-12-19
Hmm... You might want to try changing your mirror to another. It might help. Otherwise, no idea.

---

### Post by audiomick on 2009-12-19
Hallo.
+1 Dareal
All looks normal to me. All that occurs to me is to try another mirror or try again later / tomorrow. I have seen a few posts that indicate that the US mirror occasionally has problems.

---

### Post by emigrant on 2009-12-19
hi,
thank you for your replies.
i have tried many mirrors. and same problem for all.
im having this problem for about a week now :(

---

### Post by plucky on 2009-12-19
Try disabling the **backports** repository and then reload.See if that makes a difference.


Good Luck

---

### Post by audiomick on 2009-12-19
> **plucky said:**
> Try disabling the **backports** repository and then reload.See if that makes a difference.


Good Luck

As far as that goes, try disabling everything except main, see if that works, and add the other one by one.

---

### Post by emigrant on 2009-12-19
no luck>
source list:

```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntu.gnu.gen.tr/ubuntu/ jaunty main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.gnu.gen.tr/ubuntu/ jaunty-updates main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ubuntu.gnu.gen.tr/ubuntu/ jaunty-backports main

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

[COLOR=Red]deb http://ubuntu.gnu.gen.tr/ubuntu/ jaunty-security main[/COLOR]

#tor
##deb http://deb.torproject.org/torproject.org jaunty main

# Remastersys
##deb http://www.geekconnection.org/remastersys/repository ubuntu/
```


result:
```

~$ sudo apt-get update
[sudo] password for emigrant: 
Ign http://ubuntu.gnu.gen.tr jaunty Release.gpg
Ign http://ubuntu.gnu.gen.tr jaunty/main Translation-en_US
Ign http://ubuntu.gnu.gen.tr jaunty-updates Release.gpg
Ign http://ubuntu.gnu.gen.tr jaunty-updates/main Translation-en_US
Ign http://ubuntu.gnu.gen.tr jaunty-backports Release.gpg
Ign http://ubuntu.gnu.gen.tr jaunty-backports/main Translation-en_US
Ign http://ubuntu.gnu.gen.tr jaunty-security Release.gpg
Ign http://ubuntu.gnu.gen.tr jaunty-security/main Translation-en_US
Ign http://ubuntu.gnu.gen.tr jaunty Release      
Ign http://ubuntu.gnu.gen.tr jaunty-updates Release
Ign http://ubuntu.gnu.gen.tr jaunty-backports Release
Ign http://ubuntu.gnu.gen.tr jaunty-security Release
Ign http://ubuntu.gnu.gen.tr jaunty/main Packages
Ign http://ubuntu.gnu.gen.tr jaunty-updates/main Packages
Ign http://ubuntu.gnu.gen.tr jaunty-backports/main Packages
Ign http://ubuntu.gnu.gen.tr jaunty-security/main Packages
Ign http://ubuntu.gnu.gen.tr jaunty/main Packages
Ign http://ubuntu.gnu.gen.tr jaunty-updates/main Packages
Ign http://ubuntu.gnu.gen.tr jaunty-backports/main Packages
Ign http://ubuntu.gnu.gen.tr jaunty-security/main Packages
Err http://ubuntu.gnu.gen.tr jaunty/main Packages
  400 Bad Request
Err http://ubuntu.gnu.gen.tr jaunty-updates/main Packages
  400 Bad Request
Err http://ubuntu.gnu.gen.tr jaunty-backports/main Packages
  400 Bad Request
Err http://ubuntu.gnu.gen.tr jaunty-security/main Packages
  400 Bad Request
W: Failed to fetch http://ubuntu.gnu.gen.tr/ubuntu/dists/jaunty/main/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://ubuntu.gnu.gen.tr/ubuntu/dists/jaunty-updates/main/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://ubuntu.gnu.gen.tr/ubuntu/dists/jaunty-backports/main/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://ubuntu.gnu.gen.tr/ubuntu/dists/jaunty-security/main/binary-i386/Packages  400 Bad Request

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by plucky on 2009-12-19
Have you considered re-installing?

There seems to be a major problem with your package installer which is not going to be fixed with the usual sources.list fixes as you are still getting "400 Bad request errors" even with just the main repository,although the **backports** repository is still enabled.

Good Luck

---

### Post by emigrant on 2009-12-20
> **plucky said:**
> Have you considered re-installing?

There seems to be a major problem with your package installer which is not going to be fixed with the usual sources.list fixes as you are still getting "400 Bad request errors" even with just the main repository,although the **backports** repository is still enabled.

Good Luck

is it possible to re-install only the packag installer?
i had to build a long way through a slow internet connection the system i currently run.
it seems i can install through apt-get install only the update is not working :(

thank you for your help

---

### Post by plucky on 2009-12-20
> **emigrant said:**
> is it possible to re-install only the packag installer?
i had to build a long way through a slow internet connection the system i currently run.
it seems i can install through apt-get install only the update is not working :(

thank you for your help

If apt-get is working,then it is unlikely to be the package installer that is broken,it is more likely to be the update manager.You could try ```
sudo apt-get install --reinstall update-manager
``` from a terminal window and see if that makes a difference.

Good Luck

---

### Post by emigrant on 2009-12-20
> **plucky said:**
> If apt-get is working,then it is unlikely to be the package installer that is broken,it is more likely to be the update manager.You could try ```
sudo apt-get install --reinstall update-manager
``` from a terminal window and see if that makes a difference.

Good Luck

thank you very much for your tireless help. i appreciate it very much.
:(:(:(

```
$ sudo apt-get install --reinstall update-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of update-manager is not possible, it cannot be downloaded.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by emigrant on 2009-12-22
bump :(

---

### Post by houseworkshy on 2009-12-22
As you are on a slow connection go to software sources, on the first tab "ubuntu software" use the drop down menu and select other, on the pop up which opens click "select best server".  That should automatically scan for the best ( fastest ) one for you at the moment.  Once that is done use the information one this page [https://help.ubuntu.com/9.04/add-applications/C/adding-repos.html](https://help.ubuntu.com/9.04/add-applications/C/adding-repos.html) to set up fresh repositories.  It might be the validation keys which are wrong.  To save time spent finding out home in on one which is official and see if it works, if it does you will have to trawl through whichever other ones that you want but at least you will have had a proof of concept that you are not wasting your time.  If it doesn't work...well burn a copy of all you want to save ( if you are tidy it will all be under home )  because you may be forced to reinstall.  There is another test worth making.  Boot from the live cd and install, as an example clamtk, this will only be installed into ram, but it should work.  If it doesn't the problem is likely to be outside your system, if it does well I don't know....firewall?

---

### Post by emigrant on 2009-12-23
> **houseworkshy said:**
> As you are on a slow connection go to software sources, on the first tab "ubuntu software" use the drop down menu and select other, on the pop up which opens click "select best server".  That should automatically scan for the best ( fastest ) one for you at the moment.  Once that is done use the information one this page [https://help.ubuntu.com/9.04/add-applications/C/adding-repos.html](https://help.ubuntu.com/9.04/add-applications/C/adding-repos.html) to set up fresh repositories.  It might be the validation keys which are wrong.  To save time spent finding out home in on one which is official and see if it works, if it does you will have to trawl through whichever other ones that you want but at least you will have had a proof of concept that you are not wasting your time.  If it doesn't work...well burn a copy of all you want to save ( if you are tidy it will all be under home )  because you may be forced to reinstall.  There is another test worth making.  Boot from the live cd and install, as an example clamtk, this will only be installed into ram, but it should work.  If it doesn't the problem is likely to be outside your system, if it does well I don't know....firewall?

thank you for your reply. me in slow internet in the sense, im using mobile broadband with limted bandweth. i only get about 100 mb perday.
is it possible that the keys are wrong and causing prob?
is re-installing the last resort?

one of my friends also having the same problem after i installed jaunty at his home along with TOR and polipo :(

---

### Post by houseworkshy on 2009-12-23
I don't know much about those two programs except that TOR is an anonymising proxy, Could be something to do with that, removing them and seeing what happens then would be a logical experiment.

The live cd one is also worth a shot I think.

What happens if you try this?

1/Boot up from the live cd and choose the "try" option.  Then you'd be running from the cd which is not writeable and should be pristine.
2/Go to software sources ( may as well go via synaptic as we'll be using that next ) and enable all but the source code one
3/choose the best server
4/reload, as prompted
5/search for clamtk and install it.  This will only be installed to ram and will of course vanish when you reboot.

Did it work?  If it did than we are looking at a software problem on your hard drive so may fix it by fiddleing around.  If not we're on a hideing to nothing and should be thinking in terms of modem conf and a phonecall to the isp.

I KNOW this technique works.  It is one of the handy things one can do with a live cd; virus scaning a windows system for files which are not available, or destructive, when it's running.

As an aside if ever you should need it, sometime mb's are less critical, there is a nice video on the technique here
  
[http://www.youtube.com/watch?v=9h3q5ss40oY](http://www.youtube.com/watch?v=9h3q5ss40oY)

Right now we only need to know where the problem is.

---

### Post by houseworkshy on 2009-12-23
Actually you do have a lot of repositories enabled.  When you do the loading of lists look at the mb count.  See how big the updates are and check it against your isp policies, some categorize by type.  On my recent install of 8.04, which is admitedly quit old now, the updates were quite hefty.  It may even be that.  100mb is only one seventh of a cd.  If so the earlier posts suggesting that you remove some repositories could well have been correct.  If it is that the work around would be to use applications like aptoncd and download .deb files elsewhere when you want to install.

---

