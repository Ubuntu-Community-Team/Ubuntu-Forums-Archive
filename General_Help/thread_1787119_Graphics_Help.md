---
title: "Graphics Help"
date: 2011-06-20
forum: General Help
---

### Post by colmeweb on 2011-06-20
I am running 10.04 on a toshiba satellite and I can't seem to solve this little graphics problem. Whenever I run something like google earth or supertuxcart the image gets distorted. The attached picture gives some example. Any suggestions?

---

### Post by ChipOManiac on 2011-06-20
Nice effect though... :D Perhaps something with the drivers?

---

### Post by pqwoerituytrueiwoq on 2011-06-20
you can try the xswat ppa
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update

---

### Post by colmeweb on 2011-06-22
@ pqwoerituytrueiwoq

Tried, no luck. Thanks though.

---

### Post by wildmanne39 on 2011-06-22
> **colmeweb said:**
> I am running 10.04 on a toshiba satellite and I can't seem to solve this little graphics problem. Whenever I run something like google earth or supertuxcart the image gets distorted. The attached picture gives some example. Any suggestions?Hi, 
    Install CompizConfig Settings Manager from either the Software Center, or Synaptic.
    Click on the Composite tab, and un-check Detect refresh rate.
    Back to main menu.
    Click on the OpenGL tab.
    Uncheck Sync to Vblank.

---

### Post by colmeweb on 2011-06-25
> 
Hi, 
Install CompizConfig Settings Manager from either the Software Center, or Synaptic.
Click on the Composite tab, and un-check Detect refresh rate.
Back to main menu.
Click on the OpenGL tab.
Uncheck Sync to Vblank.


Ok, I have had Compiz for a while and I just spent the last 5 minutes going through it trying to find the tabs you suggested. I couldn't find it anywhere. I hate to have to ask this but could you tell me step by step how to find this. I have attached a picture of my Compiz start screen so you know what I am working with. 

Thanks

---

### Post by colmeweb on 2011-06-30
Any other help?

---

### Post by colmeweb on 2011-07-11
Ok, I found a way to do what wildmanne39 suggested but it didn't work, anybody ells?

---

### Post by wildmanne39 on 2011-07-11
Hi, run these commands in a terminal
```
sudo lshw
```
```
lspci | grep VGA
```
```
lsmod
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

