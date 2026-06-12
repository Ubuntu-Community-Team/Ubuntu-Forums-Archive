---
title: "Cannot install simple compiz"
date: 2011-09-09
forum: General Help
---

### Post by theunsatiated on 2011-09-09
I have Ubuntu 11.04 running in Ubuntu Classic mode
I wanted to install additional plugins to compiz
I learnt that to do so I need to install Simple comiz settings manager

when i try the code
[COLOR="red"]sudo apt-get install simple-ccsm[/COLOR]

I get an error this way

[COLOR="Red"]Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 simple-ccsm : Depends: python-compizconfig (>= 0.8.2) but it is not going to be installed
               Depends: compizconfig-settings-manager (>= 0.8.2) but it is not going to be installed
[/COLOR]

I have 0.9.4-0ubuntu1 (python-compizconfig)
and 0.9.4-0ubuntu2 (compizconfig-settings-manager)

I've been strugling with this for hours
plz help

---

### Post by mc4man on 2011-09-09
You can run compizconfig-settings-manager instead
command of 
ccsm
simple-ccsm is not compatible with the compiz version used in 11.04

---

### Post by theunsatiated on 2011-09-09
> **mc4man said:**
> You can run compizconfig-settings-manager instead
command of 
ccsm
simple-ccsm is not compatible with the compiz version used in 11.04

How do I add new compiz plugins then?
Ex: Burn animation for minimize

---

### Post by mc4man on 2011-09-09
You could install 
compiz-plugins-extra

Edit: don't use 11.04 anymore and never used the classic mode much so don't know if it is susceptible to having all compiz plugins unset as the unity session is.

You may want to get a list of current enabled plugins before fooling around in ccsm too much, though it may not matter in Classic
If so one way is to run ccsm from a terminal  - it will list all currently enabled, can be copied out

---

### Post by raja.genupula on 2011-09-09
look in ubuntu software center for all the things 
just type what ever you want in the search box , you gonna found what ever you want 


all the best

---

### Post by theunsatiated on 2011-09-09
Just found the fix
[COLOR="Red"]sudo apt-get install compiz-fusion-plugins-extra[/COLOR]
And then I opened CCSM, enabled animation addons...
No I can BURN, BEAM etc...

> **mc4man said:**
> You could install 
compiz-plugins-extra
Thanks

> look in ubuntu software center for all the things 
just type what ever you want in the search box , you gonna found what ever you want 

Tried a lot...in vain
I like the terminal better(for now)
Thanks anyway

---

### Post by raja.genupula on 2011-09-09
i am glad that you have solved . ,,,, please mark the thread as solved when you got solved from thread tools .

---

