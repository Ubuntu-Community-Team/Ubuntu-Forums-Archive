---
title: "installing and running wine"
date: 2010-01-15
forum: General Help
---

### Post by DavidDJ on 2010-01-15
I am new to linux and am having trouble installing wine.  I have gone to [http://www.winehq.org/download](http://www.winehq.org/download), clicked on the ubuntu linkand followed the instructions adding the wineHQ apt Repository, added *ppa:ubuntu-wine/ppa to software sources*. Closed, pressed reload. the first time I did this it came back with a Key error, repeted it twice and something was downloaded, but I cant find it, or wine anywhere. Is it installed or do I need to do something else. Also I have downloaded the windows program I want to run and cant get it to run ether. If some one can help me I would gratliy appreciate it.

---

### Post by Manyette on 2010-01-15
No expert here, but I donwloaded wine from the Software Center, the beta version, and the only problem I had is that I had to execute the program install twice.  first time it didin't really install,  Second time it installeed and ran just fine.  If you're not running Karmic, I suspect you can get the same version from Synaptic.

---

### Post by warfacegod on 2010-01-15
Wine can be had in Synaptic simply by searching for wine. It can also be installed from Ubuntu S.C. as well as Add/Remove.

---

### Post by Jackzor on 2010-01-15
Doesn't ```
sudo apt-get install wine
```

Install wine?

---

### Post by howefield on 2010-01-15
> **Jackzor said:**
> Doesn't ```
sudo apt-get install wine
```

Install wine?

No. At least, not the version the OP wants.

He wants wine1.2

---

### Post by Jackzor on 2010-01-15
> **howefield said:**
> No. At least, not the version the OP wants.

He wants wine1.2

Ah. My mistake

---

### Post by DavidDJ on 2010-01-15
I did "sudo apt-get install wine" and the return was

wine: depends: wine1.2 but it is not going to be installed
E: broken packages

How do I force wine 1.0.1

---

### Post by d3v1150m471c on 2010-01-15
> **DavidDJ said:**
> I am new to linux and am having trouble installing wine.  I have gone to [http://www.winehq.org/download](http://www.winehq.org/download), clicked on the ubuntu linkand followed the instructions adding the wineHQ apt Repository, added *ppa:ubuntu-wine/ppa to software sources*. Closed, pressed reload. the first time I did this it came back with a Key error, repeted it twice and something was downloaded, but I cant find it, or wine anywhere. Is it installed or do I need to do something else. Also I have downloaded the windows program I want to run and cant get it to run ether. If some one can help me I would gratliy appreciate it.

synaptic... or:

sudo apt-get install wine (please note there is also a wine1.2 which may better suit your needs)

Secondly...what is it you are trying to run in wine?

---

### Post by d3v1150m471c on 2010-01-15
> **DavidDJ said:**
> I did "sudo apt-get install wine" and the return was

wine: depends: wine1.2 but it is not going to be installed
E: broken packages

How do I force wine 1.0.1

use synaptic

---

### Post by Manyette on 2010-01-15
Hi David, Pehhaps I am missing something here, but Synaptic  Package Manager would be the way to go.  It has wine 1.2 available, and it you do have broken packages, the "broken package" filter will allow you to fix the problem.

---

### Post by DavidDJ on 2010-01-15
what is the Synaptic  Package Manager?

---

### Post by Manyette on 2010-01-15
Go to System -> Administration -> Synaptic Package Manager.  In the search box at the upper right, enter "wine".  When you get the display you want, right click on it and select "install".  Then apply, and then apply again in the toolbar.

---

### Post by DavidDJ on 2010-01-15
Thanks for the info on synaptic pakage manager, I ran it 3 times and got this response. 

wine1.2:
 Depends: libaudio2  but it is not installable
 Depends: libmpg123-0 (>=1.6.2) but it is not installable
 Depends: libopenal1  but it is not installable
 Recommends: ttf-liberation  but it is not installable
 Recommends: winbind  but it is not installable
 Recommends: wine1.2-gecko  but it is not installable
 Recommends: ttf-mscorefonts-installer  but it is not installable

Does it mean the package is broken, if so who do I let know.

I am running ubuntu 9.10 and I want to run taxact offline.

---

### Post by Manyette on 2010-01-15
Hi David, I'm assuming you didn't get any error messages in synaptic.  My only suggestion at this point is to go back to Synaptic package manager, open it, and in the bottom left panel select  custom filters.  One of those filters is called "broken packages"  Select that and enter wine in the search box if required.  If  that doersn't give you any help instructions, then I am out of ideas, and it will take someone more knowledgeable than myself to go any farther.

---

### Post by DavidDJ on 2010-01-15
> **Manyette said:**
> Hi David, I'm assuming you didn't get any error messages in synaptic.  My only suggestion at this point is to go back to Synaptic package manager, open it, and in the bottom left panel select  custom filters.  One of those filters is called "broken packages"  Select that and enter wine in the search box if required.  If  that doersn't give you any help instructions, then I am out of ideas, and it will take someone more knowledgeable than myself to go any farther.

I did what you recommended and there is nothing there. Thanks for your help hope someone else knows what I can do.

---

### Post by DavidDJ on 2010-01-16
> **DavidDJ said:**
> Thanks for the info on synaptic pakage manager, I ran it 3 times and got this response. 

wine1.2:
 Depends: libaudio2  but it is not installable
 Depends: libmpg123-0 (>=1.6.2) but it is not installable
 Depends: libopenal1  but it is not installable
 Recommends: ttf-liberation  but it is not installable
 Recommends: winbind  but it is not installable
 Recommends: wine1.2-gecko  but it is not installable
 Recommends: ttf-mscorefonts-installer  but it is not installable

Does it mean the package is broken, if so who do I let know.

I am running ubuntu 9.10 and I want to run taxact offline.

Can anyone tell me what to do whrn this return happens. I checked in synaptic under custom filters broken and there is nothing. 
Is there a way to go back to an earlier version? Is that a bad idea? How do I report this problem?

---

### Post by Manyette on 2010-01-16
Hi David, I'm not sure what to advise.  I fear that your earlier attempt to load wine have somehow had a deleterious effect on your system.  If it were me, I would reinstall, but that depends on how much additional work that woulde entail for you.  If you have alreawdy loaded and configured a lot of files and data it might not be practical to do so.  After all, the install is easy and quick.  The following configuration and file transfers can be much more time consuming.  I guess it's your call, but from what you have said, I think my option would be a reinstall, because something is obviuosly pretty badly screwed up.  Sorry I can't be of more help, but you are well beyond what little knowledge that I have,.

---

### Post by Manyette on 2010-01-16
Hi David, I would add that if you do decide to reinstall, initially I hope you will stay with loading software either from Synaptic Package manager, or the Software Center if you are using Karmic.

---

### Post by DavidDJ on 2010-01-16
> **Manyette said:**
> Hi David, I'm not sure what to advise.  I fear that your earlier attempt to load wine have somehow had a deleterious effect on your system.  If it were me, I would reinstall, but that depends on how much additional work that woulde entail for you.  If you have alreawdy loaded and configured a lot of files and data it might not be practical to do so.  After all, the install is easy and quick.  The following configuration and file transfers can be much more time consuming.  I guess it's your call, but from what you have said, I think my option would be a reinstall, because something is obviuosly pretty badly screwed up.  Sorry I can't be of more help, but you are well beyond what little knowledge that I have,.
Thank you    Don Manyette and semper fi

---

### Post by HeadHunter00 on 2010-01-16
Add the repository again, but this time, also download Scott Richie's gpg key and add it via the authentication tab in software sources, then reload

---

### Post by HeadHunter00 on 2010-01-16
actually never mind, you dont need the repos. Just download wine from this URL:[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by d3v1150m471c on 2010-01-16
> **DavidDJ said:**
> what is the Synaptic  Package Manager?

In your adventures with Ubuntu, you'll learn to love synaptic. Synaptic is a cornerstone application on your system. It allows you to download software from the repositories. You can configure what it will allow you to download ( this will also effect your update manager and apt-get) by going into system>administration>software sources, and checking or unchecking various sources. You have to press the reload button in synaptic for this to take effect. Chances are if you cannot find something that's commonly accessible on ubuntu you don't have one of the repos or sources enabled. Be careful with this though, as again, it will also effect your updates as well.

You can add other repos and software keys to your software sources but it's not recommended for said reasons.

---

### Post by HeadHunter00 on 2010-01-16
> **DavidDJ said:**
> Thanks for the info on synaptic pakage manager, I ran it 3 times and got this response. 

wine1.2:
 Depends: libaudio2  but it is not installable
 Depends: libmpg123-0 (>=1.6.2) but it is not installable
 Depends: libopenal1  but it is not installable
 Recommends: ttf-liberation  but it is not installable
 Recommends: winbind  but it is not installable
 Recommends: wine1.2-gecko  but it is not installable
 Recommends: ttf-mscorefonts-installer  but it is not installable

Does it mean the package is broken, if so who do I let know.

I am running ubuntu 9.10 and I want to run taxact offline.
install wine from aptitude or smart package manager:> sudo aptitude install wine1.2 (or wine)
aptitude is better at resolving dependencies. and smart package manager uses aptitude(I think). Anyhoo, this should help. If you want to try out smart, then type this command:> sudo aptitude install smartpm

---

### Post by Jinx42 on 2010-02-01
I know this is an old topic, but could maybe help others.

I had similar problems and always ended up with some un-installable files.

Eventually I picked another server System-> Administration-> Software Sources, and it was able to resolve the missing files.

So it seems either the choosen server I had was out of sync (unlikely) or my apt-get update didnt really get the entire list of packages downloaded properly.

---

