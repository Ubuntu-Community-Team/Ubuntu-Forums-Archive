---
title: "Update Manager continues to fail..."
date: 2010-02-15
forum: General Help
---

### Post by CharlesJWelsh on 2010-02-15
I launch update manager and try to install updates and I am running into a problem. It tells me that I have a "Broken Package" on my system. (I HAVE TRIED TO RE-INSTALL THE PACKAGE (Python) BUT IT GIVES ME SAME ERROR AS Update Manager) and this is what shows up in the "Details Panel": "dpkg: parse error, in file '/var/lib/dpkg/available' near line 54: missing package name" there is more to it thus I have included a screenshot. Any help would be greatly appreciated.  -CJ

::ALSO; I am running Ubuntu 9.10 "Karmic Koala"

---

### Post by stoneage on 2010-02-15
Hey, no need to shout, man.

It sounds like you have a broken package:-
[https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages](https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages)

---

### Post by Easy Limits on 2010-02-15
Try going in to Synaptic and look for Custom Filters > Broken.  You should be able to resolve the issue there.

---

### Post by buhmillion on 2010-02-15
It may be a little off-topic, but the font in the screenshots is amazing! what is it called?

---

### Post by CharlesJWelsh on 2010-02-15
Yes this I realized... However I have already done this step. And I did it again so I could provide a picture of the issue...

::Font is "Purisa Bold"

---

### Post by CharlesJWelsh on 2010-02-15
> **Easy Limits said:**
> Try going in to Synaptic and look for Custom Filters > Broken.  You should be able to resolve the issue there.

I have done this. The package is python somethin or other. And I believe the problem may be a little more complicated than a broken package...

---

### Post by Easy Limits on 2010-02-15
In the Update Manager > Software Sources which items do you have check marked?

---

### Post by overdrank on 2010-02-15
Hi and welcome, please be patient. Creating multiple threads on the same issue can cause confusion. Thanks :)

---

### Post by CharlesJWelsh on 2010-02-15
nothing. and i have 2 options...

---

### Post by Easy Limits on 2010-02-15
Can you put up a screen shot?

---

### Post by CharlesJWelsh on 2010-02-15
here ya go :)

---

### Post by Easy Limits on 2010-02-15
What do you have check marked under the Ubuntu Software tab and Updates tab?

Btw, I do suggest you check mark those two boxes.

---

### Post by CharlesJWelsh on 2010-02-15
this stuff...

---

### Post by Easy Limits on 2010-02-15
Looks like you have your Software Sources set up right.  Did you check those two empty boxes in the Other Software tab?

---

### Post by CharlesJWelsh on 2010-02-15
yeah and i tried fixing the broken package... still gives me that error about line 54 or somethin. its in one of the pics...

---

### Post by Easy Limits on 2010-02-15
My next suggestion was to un-install the package but I guess from reading your first post you have already done that.  Unfortunately, that's all I got for suggestions.

---

### Post by CharlesJWelsh on 2010-02-15
I solved it. I had to create a new /var/lib/dpkg/available
and i did it like this :)

> sudo mv /var/lib/dpkg/available /var/lib/dpkg/available.oldBusted
> sudo touch /var/lib/dpkg/available
> sudo apt-get update

---

