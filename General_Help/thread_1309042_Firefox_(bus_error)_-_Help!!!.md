---
title: "Firefox (bus error) - Help!!!"
date: 2009-11-01
forum: General Help
---

### Post by dchurch24 on 2009-11-01
Hi all,

I recently installed 9.10 UbuntuStudio - and all was fine and dandy.

The update manager popped up this morning to tell me there were some updates, so I duly installed them.

I had firefox open at the time, and after the updates had run it told me I needed to restart it.  I did.

It ran fine for about 2 mins then crashed. Now it wont start at all.  I tried to open from the terminal and I get the error "Bus Error".

I rebooted the machine, and the error is still the same. I have uninstalled all flash players, but the error persists.

---

### Post by dchurch24 on 2009-11-01
Ahh - the update must corrupt xulrunner - a complete removal and reinstall and firefox is working (for now at least).

---

### Post by mashimario on 2009-12-19
> **dchurch24 said:**
> Ahh - the update must corrupt xulrunner - a complete removal and reinstall and firefox is working (for now at least).
same situation here, could you tell me how you removed and reinstalled Firefox? Thanks

---

### Post by HectorG on 2009-12-23
Same problem here I tried uninstalling and reinstalling. Also tried removing profile. Tried installing xulrunner then removing and reinstalling firefox. Still doesn't work.

Even running firefox in safe-mode gives me the bus error.

---

### Post by HectorG on 2009-12-29
Whoever hasn't gotten their firefox to work yet I found a way to get it to work. I hope it works for you as well... 

I couldnt get it to work with "sudo apt-get --remove firefox" but the following did work!

*************************************************************************************

System -> Synaptic Package Manager-> 

On the quick search type firefox and select everything related to firefox you can find. In my case I just had the regular firefox 3.5.6+nobinonly-0ubuntu0.9.10.1

make sure you select it and right click. 

select mark for complete uninstall and click apply. (it will select a couple of other packages to uninstall like ubufox ...

when its done reinstall it through the synaptic the same way you uninstalled it. 

Good Luck

---

