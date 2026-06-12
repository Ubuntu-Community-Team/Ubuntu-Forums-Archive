---
title: "Compiz 0.9.2.1 problems"
date: 2010-12-30
forum: General Help
---

### Post by messie on 2010-12-30
Greetings, 

I have installed compiz 0.9.2.1 on my maverick and everything goes smoothly except one thing: When I open the compiz config settings manager, I can check the boxes for the options, yet my preferences do not seem to be applied at all, and when I reopen tha manger, they revert back to the original state. Moreover, clicking on the I con of the preference I choose will not get me into the menu. I have tried reinstalling all the compiz components, but I get the same result. Any Ideas?

---

### Post by Idefix82 on 2010-12-30
In the System->Preferences->Appearance dialog, click the rightmost tab and make sure that the bottom option is selected (I am not in front of Ubuntu right now, so don't remember exactly what the labels are).

---

### Post by hawthornso23 on 2010-12-30
First things first. Is compiz running? You need proprietary drivers installed. Check this in System>Administration>Hardware Drivers . 

```
compiz --replace ccp &
```

in a terminal to start compiz.

---

### Post by messie on 2010-12-30
hmm there seems to be a problem with the drivers... I cannot enable the extre visuals as it asks me to enable nvidia drivers, yet I have ATI card and no fglrx, just the open source ones. Things were smooth with the last compiz tho...


Seems like i have to enable the ATI drivers.. Can anyone point me into doing this? Last time I enabled the ATI drivers Screen went blank and I had to purge them and return to the open source ones...

---

### Post by lidex on 2010-12-30
Perhaps you should just go back to the maverick version. I think 0.9.2.1 is not ready for prime time
outside of natty. At least reference this:[http://www.webupd8.org/2010/11/install-compiz-0921-in-ubuntu-1010.html](http://www.webupd8.org/2010/11/install-compiz-0921-in-ubuntu-1010.html)

---

### Post by messie on 2010-12-30
Well I have tried this in order to uninstall compiz and revert back to 0.8 but it does not work, as this ppa does not exist in my sources... Is there any other way to go back to 0.8?

---

### Post by hawthornso23 on 2010-12-30
> 
Seems like i have to enable the ATI drivers.. Can anyone point me into  doing this? Last time I enabled the ATI drivers Screen went blank and I  had to purge them and return to the open source ones...What graphics hardware do you have? The proprietary drivers for older ATI cards can't handle the newer version of XOrg in recent ubuntu versions. Is this you?

---

### Post by messie on 2010-12-30
Well I have an ATI radeon HD4650, And that caused me a lot of problems in 10.04. I ahd to remove the fgrlx drivers or the Screen would stay black

---

### Post by lidex on 2010-12-30
> **messie said:**
> Well I have tried this in order to uninstall compiz and revert back to 0.8 but it does not work, as this ppa does not exist in my sources... Is there any other way to go back to 0.8?

How did you install this to begin with if not from a PPA? 
GO into synaptic, search 'compiz' - no quotes - and mark all the compiz packages for removal and apply. Restart and post results.

---

### Post by messie on 2010-12-30
> **lidex said:**
> How did you install this to begin with if not from a PPA? 
GO into synaptic, search 'compiz' - no quotes - and mark all the compiz packages for removal and apply. Restart and post results.


Well I have tried sudo apt-get install --reinstall "compiz packages" but it always installs 0.9.2.1 version.. Plus I don't remember what repo I found it from...

---

### Post by lidex on 2010-12-30
Are you using maverick?
Go into synaptic and search compiz. Select the compiz package in the right pane. Click on the package menu and select "Force Version". It should bring up a dialog with drop down menu to select available versions. Select the older version and apply.

---

### Post by messie on 2010-12-30
Thanks guys, worked a treat. Forcing the older version was the trick.

---

### Post by lidex on 2010-12-30
Great. Now uncheck the repo with 0.9.2.1 in software sources so it won't try to upgrade it again.

---

