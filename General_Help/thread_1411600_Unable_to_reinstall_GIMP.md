---
title: "Unable to reinstall GIMP"
date: 2010-02-20
forum: General Help
---

### Post by niteling on 2010-02-20
I installed Ubuntu karmic awhile ago and GIMP comes pre installed with it. I am still getting used to GIMP... I used Photoshop which i still have running on vista on another partition but cant be bothered switching.

I have tried to do some simple things with help from in program help and support and noticed that some features were missing or aren't properly so i decided to remove and install it agian today but unable to install it again because i keep getting this error...

The following packages have unmet dependencies:
  gimp: Depends: libgimp2.0 (<= 2.6.7-z) but 2.7.2-2009090102~jj is to be installed
        Depends: gimp-data (<= 2.6.7-z) but 2.7.2-2009090102~jj is to be installed
E: Broken packages

Thanks

---

### Post by bobcollard on 2010-02-20
> **niteling said:**
> I
The following packages have unmet dependencies:
  gimp: Depends: libgimp2.0 (<= 2.6.7-z) but 2.7.2-2009090102~jj is to be installed
        Depends: gimp-data (<= 2.6.7-z) but 2.7.2-2009090102~jj is to be installed
E: Broken packages

Thanks
Open Synaptic Package Manager and in Edit/Fix Broken Packages  Then Apply changes.

---

### Post by halj32 on 2010-02-20
try installing & use Synaptic Package Manager

---

### Post by niteling on 2010-02-20
I have tried with both terminal, synaptic and ubuntu software center, hajl32

And bobcollard I do edit/fix broken packages and the screen just flashes and nothing seems to happen... and i tried again and still the same error.

thanks so much for the help!:D

---

### Post by bobcollard on 2010-02-20
> **niteling said:**
> I have tried with both terminal, synaptic and ubuntu software center, hajl32

And bobcollard I do edit/fix broken packages and the screen just flashes and nothing seems to happen... and i tried again and still the same error.

thanks so much for the help!:D
Fixing them and Applying Changes are two separate steps.

---

### Post by niteling on 2010-02-20
OK so i go to edit click fix broken packages... what should happen... apply changes doesn't show up.

sorry I'm pretty new to this.

---

### Post by bobcollard on 2010-02-20
> **niteling said:**
> OK so i go to edit click fix broken packages... what should happen... apply changes doesn't show up.

sorry I'm pretty new to this.
"Apply" is in the Menu at the top of the panel in Synaptic Package Manager.  Sorry, I forget about people being Newbies and get carried away.

---

### Post by _khAttAm_ on 2010-02-20
Click "Custom Filters" at lower left side of synaptic window. Now in the upper left, click "Broken". Mark the packages there for reinstallation or removal (whatever works).
Hope this helps.

---

### Post by niteling on 2010-02-20
I know what you mean but it isn't working... i just did a quick look on ubuntu help 

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

the package doesn't get marked for repair.

---

### Post by _khAttAm_ on 2010-02-20
^what happens when you try to remove it altogether (you can reinstall it later?) i.e. mark for removal

---

### Post by niteling on 2010-02-20
I did a full removal or im pretty sure i did..
the only option that comes up when i go to mark it, is for installation...

---

### Post by _khAttAm_ on 2010-02-20
^what packages are in the broken custom filter?
what is your problem now?

---

### Post by niteling on 2010-02-20
sorry to say but nothing comes in there.

EDIT heres a screenshot to show i'm the right area

[http://i839.photobucket.com/albums/zz316/niteling/Screenshot-2.png](http://i839.photobucket.com/albums/zz316/niteling/Screenshot-2.png)

---

### Post by stoneage on 2010-02-20
It looks to me like a version mismatch. Synaptic seems to think you are trying to install Gimp 2.7 with Gimp 2.6 dependencies.

Try removing the dependencies then reinstall?

---

### Post by niteling on 2010-02-20
> **stoneage said:**
> It looks to me like a version mismatch. Synaptic seems to think you are trying to install Gimp 2.7 with Gimp 2.6 dependencies.

Try removing the dependencies then reinstall?

Thanks that worked I didn't know that there was a whole heap of other stuff still there from the installation. Im still learning now i know what do next time

Thanks everyone :D

---

