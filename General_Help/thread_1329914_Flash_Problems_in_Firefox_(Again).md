---
title: "Flash Problems in Firefox (Again)"
date: 2009-11-17
forum: General Help
---

### Post by jdorenbush on 2009-11-17
Well I was having problems interacting with Flash before and I thought I had the [problem solved]("http://ubuntuforums.org/showthread.php?t=1283533"), but just recently it started up again.

I can see and view Flash, but interacting with it is almost impossible. Interacting with YouTube player controls used to be the main problem, but that doesn't seem to be an issue.

Now I simply can't navigate through a Flash built website. Flash links, I suppose you could call them, don't do anything.

I've tried uninstalling/installing the "flashplugin-installer 10.0.32.1ubuntu1". I've tried the steps in the linked post above (manually downloading and putting the libflashplayer.so in my plugins directory). Both steps do not work.

Very frustrating that I can't even browse Flash websites...

---

### Post by emotard on 2009-11-17
There are solutions for this at the bug report on this problem at [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407)

---

### Post by garvinrick4 on 2009-11-17
sudo gedit apt-get etc/apt/soures.list


Type that in a Terminal copy and paste so we can go over them.


Then Code:    sudo apt-get remove flashplugin-nonfree
        Code:    sudo apt-get clean



We will then get the right repositories and reload the software. Okay.

---

### Post by jdorenbush on 2009-11-18
> **garvinrick4 said:**
> sudo gedit apt-get etc/apt/soures.list

I must be doing something wrong... It is coming up blank??

---

### Post by garvinrick4 on 2009-11-18
Sorry there was a typo:  Code:  sudo apt-get etc/apt/sources.list

---

### Post by jdorenbush on 2009-11-18
> **garvinrick4 said:**
> Sorry there was a typo:  Code:  sudo apt-get etc/apt/sources.list

That gave me an error, "E: Invalid operation etc/apt/sources.list"

Then I tried the above but also with the "gedit" part in it. I got the same thing as before, 2 blank documents in gedit, "apt-get" and "sources.list"

I also get a weird mention of GTK stuff when putting the command in.

jeff:~$ sudo gedit apt-get etc/apt/sources.list
/usr/share/themes/MurrinaCandido/gtk-2.0/gtkrc:84: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/MurrinaCandido/gtk-2.0/gtkrc:85: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.

---

### Post by garvinrick4 on 2009-11-18
I am so sorry I am giving you my typo's on one easy command.

[I]sudo gedit /etc/apt/sources.list  


That will give you your sources list to post in here. So sorry.
[/I]

---

### Post by jdorenbush on 2009-11-18
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) karmic main restricted
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) karmic restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) karmic-updates main restricted
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) karmic universe
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) karmic multiverse
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) karmic-security main restricted
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) karmic-security restricted main multiverse universe #Added by software-properties
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) karmic-security universe
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) karmic-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free
# deb [http://ppa.launchpad.net/gm-notify-maintainers/ppa/ubuntu](http://ppa.launchpad.net/gm-notify-maintainers/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/gm-notify-maintainers/ppa/ubuntu](http://ppa.launchpad.net/gm-notify-maintainers/ppa/ubuntu) karmic main
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) karmic-proposed restricted main multiverse universe
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) karmic-proposed restricted main multiverse universe
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) karmic-backports restricted main multiverse universe
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) karmic-backports restricted main multiverse universe
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main
deb [http://ppa.launchpad.net/merlwiz79/aurora/ubuntu](http://ppa.launchpad.net/merlwiz79/aurora/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/merlwiz79/aurora/ubuntu](http://ppa.launchpad.net/merlwiz79/aurora/ubuntu) karmic main

---

### Post by garvinrick4 on 2009-11-18
I do not see karmic partners.

Add this line:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

If not you have to copy and paste the line starting with deb
to Software Sources to other software tab to ADD and paste it
in APT line click add source and close.

While in Other Software tab make sure disabled on upgrade to karmic
and disabled on upgrade to karmic non-free   are checked.

close and will be added to repositories.

Go to Terminal Code:   sudo apt-get update
                       Code: sudo apt-get clean
                       Code: sudo apt-get update
                            
Now add your software.

Here is my repositories: Seems to work fine.
rick@ubuntu:~$ sudo apt-get update
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic Release.gpg
Ign [http://mirror.anl.gov](http://mirror.anl.gov) karmic/main Translation-en_US                        
Ign [http://mirror.anl.gov](http://mirror.anl.gov) karmic/restricted Translation-en_US                  
Ign [http://mirror.anl.gov](http://mirror.anl.gov) karmic/universe Translation-en_US                    
Ign [http://mirror.anl.gov](http://mirror.anl.gov) karmic/multiverse Translation-en_US                  
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic-updates Release.gpg                           
Ign [http://mirror.anl.gov](http://mirror.anl.gov) karmic-updates/main Translation-en_US                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release.gpg                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Translation-en_US       
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_US      
Ign [http://mirror.anl.gov](http://mirror.anl.gov) karmic-updates/restricted Translation-en_US          
Ign [http://mirror.anl.gov](http://mirror.anl.gov) karmic-updates/universe Translation-en_US            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://mirror.anl.gov](http://mirror.anl.gov) karmic-updates/multiverse Translation-en_US          
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic-security Release.gpg                          
Ign [http://mirror.anl.gov](http://mirror.anl.gov) karmic-security/main Translation-en_US               
Ign [http://mirror.anl.gov](http://mirror.anl.gov) karmic-security/restricted Translation-en_US         
Ign [http://mirror.anl.gov](http://mirror.anl.gov) karmic-security/universe Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release                      
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Ign [http://mirror.anl.gov](http://mirror.anl.gov) karmic-security/multiverse Translation-en_US         
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic-backports Release.gpg                         
Ign [http://mirror.anl.gov](http://mirror.anl.gov) karmic-backports/restricted Translation-en_US        
Ign [http://mirror.anl.gov](http://mirror.anl.gov) karmic-backports/main Translation-en_US              
Ign [http://mirror.anl.gov](http://mirror.anl.gov) karmic-backports/multiverse Translation-en_US
Ign [http://mirror.anl.gov](http://mirror.anl.gov) karmic-backports/universe Translation-en_US
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic Release                             
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic-updates Release                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_US  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release                     
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic-security Release                              
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic-backports Release                             
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic/main Packages                                 
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic/restricted Packages                           
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic/main Sources                                  
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic/restricted Sources                            
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic/universe Packages                             
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic/universe Sources                              
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic/multiverse Packages                           
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic/multiverse Sources                            
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic-updates/main Packages                         
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic-updates/restricted Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages                         
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic-updates/main Sources                          
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic-updates/restricted Sources          
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic-updates/universe Packages                     
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic-updates/universe Sources                      
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic-updates/multiverse Packages                   
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic-updates/multiverse Sources                    
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic-security/main Packages                        
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic-security/restricted Packages                  
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic-security/main Sources                         
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic-security/restricted Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Packages          
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic-security/universe Packages                    
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic-security/universe Sources           
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic-security/multiverse Packages        
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic-security/multiverse Sources         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages           
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic-backports/restricted Packages       
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic-backports/main Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic-backports/multiverse Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) karmic-backports/universe Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
Reading package lists... Done
rick@ubuntu:~$

---

### Post by jdorenbush on 2009-11-18
What did you mean by "While in Other Software tab make sure disabled on upgrade to karmic and disabled on upgrade to karmic non-free are checked."

I did everything else. Do I manually add the flashplugin now? What is the best way to add that do you think?

---

### Post by garvinrick4 on 2009-11-18
Check in Software sources: 2nd tab is Other Software: Sometimes on upgrade there will
be the third party software gets disabled. There will be 2 lines that says 
"disabled on upgrade to karmic" and disabled on upgrade to karmic free non-free

Make sure you check those to box's in Other Software tab then close so they reload.
and then do a  "sudo apt-get update" without qoutes.

OK as long as you have updated and did a clean.
You have to clean to get the old programs out of your cache so they will reload new ones
from the repositories. Or you just keep reloading a broken package. 

Now do you want   the whole "ubuntu-restricted-extras"   package flash, codecs, fonts, the works.

Or do you just want  the "flashplugin-nonfree package.

It will tell you the whole story in Synaptic and just add from there.
Should be no problem.  If you want to do it from command line, go ahead

sudo apt-get install ubuntu-restricted-extras

or just     "sudo apt-get install flashplugin-nonfree"  without qoutes.

Let me know if it go's well.  You did get your karmic partner loaded I take it. And check
that it is in your system.

---

### Post by jdorenbush on 2009-11-18
I don't see the "disabled on upgrade to karmic" thing you mentioned.

But I think I did everything else correctly, but still no luck.

Here is a link to a screen shot that shows 4 windows: Synaptic Package Manager and 3 Software Sources tabs (Ubuntu Software, Other Software, and Updates)

[http://img412.imageshack.us/img412/9689/75447241.png](http://img412.imageshack.us/img412/9689/75447241.png)

---

### Post by garvinrick4 on 2009-11-18
Okay so flash still refuses to say it is there.

Let us try this.

Go to Software Sources and to 1st tab Ubuntu Software.
Download from click tab on right edge and go to Other.
In other go down to  "mirror.anl.gov"  and choose that server.
Close and that Mirror will load in your system.
It is a 10 gigabyte bandwidth from 5 to 100 times bigger than any other in
the United States and is updated on a daily basis. Yours is 1 gig and  1 day behind.
No big deal but sometimes a new mirror works, the worst that can happen is you
will have a faster download most of the time.

sudo apt-get update

sudo apt-get remove flashplugin-nonfree

sudo apt-get clean

sudo apt-get install flashplugin-nonfree

sudo apt-get update

sudo apt-get upgrade


Hopefully it will have install. Go to any flashplayer video right click on video while playing
go down to flashplayer select it and it will go to adobe and tell you what version you
have installed. Just so you know it is all ok.

If not 

sudo apt-get build-dep flashplugin-nonfree

dpkg --configure -a

sudo apt-get update

see if all is ok.  If not
check Synaptic to see if front page bottom says any broken packages

Let me know.

---

### Post by jdorenbush on 2009-11-18
I did all those steps. Flash still seems to operate with the same problems. I can see the video, but I can't interact. For example [http://www.averybrewing.com](http://www.averybrewing.com) - the "Enter" button highlights when I hover over it, but when I click it, it does nothing. This is how all Flash sites are behaving. I can see the site, I can see the effects, but I can't navigate. Even if I right click and goto "Settings" it locks me into the first page of settings without the ability to click through the tabs or interact with the settings.

I was able to right click on the Flash video file and click, "About Adobe Flash Player 10..."

That took me to an Adobe website that said, "You have version 10,0,32,18 installed"

---

### Post by garvinrick4 on 2009-11-19
I went to your link and it came up nicely hit enter went no farther. I play all flash videos 
fine and asked for version of Flash and it was the latest version.
 IF ANYONE out there will go to this link and see if they hit enter does it go any further.
And post to this thread. Now I am just dead curious what this is that doesnt exept latest
version of Flashplayer.

[http://www.averybrewing.com/](http://www.averybrewing.com/)


Thank you very much.

---

### Post by marin123 on 2009-11-23
i have a problem with flash... i have adobe flash correctly installed but when i open plugins in firefox i dont see it... i copied libflash.so to all plugins directories (firefox and mozilla) but i cant see it... i only have shockwave 10.0.r32 plugin in firefox... am i doing something wrong? please help... thanks! :)

---

### Post by jdorenbush on 2009-11-23
Yeah I am still having the same problem... Any other solutions?

---

### Post by jdorenbush on 2009-11-25
**UPDATE:** Tested in Chrome... same problem here.

Also I noticed that the Gmail attachment progress bar is non-existent. I tried it on a Windows XP machine using Firefox and the loading bar works, but on Ubuntu I just don't see it... I assume that this loading bar is animated with Flash and that's why I'm having problems?

**UPDATE 2:** Solved. Was using the new 10.1 Flash player, which doesn't work with 64 bit. Had to install the old 10.0 version. Only thing that isn't working w/ Flash is the Gmail Advanced Attachment Features.

---

### Post by prkos on 2009-11-30
> **garvinrick4 said:**
> I went to your link and it came up nicely hit enter went no farther. I play all flash videos 
fine and asked for version of Flash and it was the latest version.
 IF ANYONE out there will go to this link and see if they hit enter does it go any further.
And post to this thread. Now I am just dead curious what this is that doesnt exept latest
version of Flashplayer.

[http://www.averybrewing.com/](http://www.averybrewing.com/)


Thank you very much.
I'm having the same problem. Flash works when I go to youtube for example, but doesn't work on viddler because the play button does nothing. On very rare occasions it works, probably on a fresh restart. 

When I go the website you mentioned hitting enter does nothing. 

My flashplugin-nonfree is version 10.0.32.18ubuntu1

---

### Post by jdorenbush on 2009-12-01
> **prkos said:**
> I'm having the same problem. Flash works when I go to youtube for example, but doesn't work on viddler because the play button does nothing. On very rare occasions it works, probably on a fresh restart. 

When I go the website you mentioned hitting enter does nothing. 

My flashplugin-nonfree is version 10.0.32.18ubuntu1

Are you on 64 bit?

---

### Post by prkos on 2009-12-01
> **jdorenbush said:**
> Are you on 64 bit?
yes AMD64

---

### Post by jdorenbush on 2009-12-14
In my Synaptic I don't have anything "Flash" installed. I did it all manually. Try following these steps:

1. Download: [Flash Player 10.0.32 for 64-bit Linux]("http://www.sendspace.com/file/hby77u")
(*I couldn't find an archived link on Adobe's website for this older version of Flash. I uploaded the one I am using to SendSpace. If anyone can find an official link to adobe. please provide.*)

2. Remove the flashplugin via Synaptic Package Manager.

3. Hit Alt+F2 and type "gksu nautilus" and then hit Enter.

4. Navigate to /usr/lib/mozilla/plugins/. If there is a "libflashplayer.so" file there, back it up.

5. Extract libflashplayer.so from the gzip file you downloaded (libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz) into your mozilla/plugins/ folder.

6. Restart Firefox

The Flash Player should now be working for you. I have tested Flash Player 10.0.32 in a 64-bit environment in a current version of Firefox, and am currently using it in Chrome. Works the same in both browsers.

Let us know if that worked.

---

### Post by prkos on 2009-12-14
Thank you! It works! I can see some videos I couldn't see for several weeks, and the website [http://www.averybrewing.com/](http://www.averybrewing.com/) works too. 

I actually had that 64-bit flash file on my HDD, I guess this is how I fixed it in Jaunty but forgot about it. 

Where do 64-bit versions come from? How come it's not in the repos?

---

### Post by CompShrink on 2009-12-17
Link from the official site:
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz")

[From this thread]("http://ubuntuforums.org/showthread.php?t=1356862").

---

### Post by jdorenbush on 2009-12-18
> **CompShrink said:**
> Link from the official site:
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz")

[From this thread]("http://ubuntuforums.org/showthread.php?t=1356862").

That's version 10.0.42. The version I proved is 10.0.32 which is the only one that works for me. The newer ones I have problems with.

---

