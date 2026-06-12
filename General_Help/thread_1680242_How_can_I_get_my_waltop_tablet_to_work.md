---
title: "How can I get my waltop tablet to work?"
date: 2011-02-02
forum: General Help
---

### Post by Mr_VeRiTy on 2011-02-02
Hi, I just bought an aiptek re-branded waltop graphics tablet, and it sort-of works, but when I click, the click wont end until I move the pen out of range of the graphics tablet, does anybody know how to fix this?

EDIT: Also, when I edit the 50-wacom.conf file as instructed in a tutorial (I just uncommented the part about waltop) it just makes the cursor jump to the top left corner when i try to use the pen.

---

### Post by Mr_VeRiTy on 2011-02-02
Could it just be the pen that is broken?

---

### Post by Favux on 2011-02-02
Hi Mr_VeRiTy,

It sounds like your Waltop isn't on the Wacom driver.  The match line may not be working for you.  Let's look at the output in a terminal of:
```
xinput list
```

---

### Post by Mr_VeRiTy on 2011-02-02
> **Favux said:**
> Hi Mr_VeRiTy,

It sounds like your Waltop isn't on the Wacom driver.  The match line may not be working for you.  Let's look at the output in a terminal of:
```
xinput list
```
The output was 
```
Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Areson USB Device                           id=10    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Slim Tablet      id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]

```Sorry for the delayed reply. On the ubuntu help pages, it says that my tablet works with the wizardpen driver, and I did the steps it told me to do but it still doesn't work properly. It is an AIPTEK Slim Tablet U600 Premium II and it's on[ this list.]("https://help.ubuntu.com/community/TabletSetupWizardpen")

---

### Post by Mr_VeRiTy on 2011-02-02
Nevermind, I got it to work, I used [this tutorial]("http://ubuntuforums.org/showpost.php?p=9252390&postcount=1") and used the Gpen f509 70-wizardpen.conf settings, and now it works great ^_^

---

### Post by Favux on 2011-02-02
Hi Mr_VeRiTy,

Just to let you know the intended driver for the Waltop tablets is the Wacom driver.  Since you are in Maverick you should be able to use the Wacom rather than the WizardPen driver, which is needed in Lucid.  See the [Waltop HOW TO]("http://ubuntuforums.org/showpost.php?p=9966110&postcount=1").

The advantage is the Wacom driver uses a Bezier curve for pressure rather than a linear pressure curve like the WizardPen driver and so is better for drawing.  Although right now there may be an issue with both stylus buttons acting the same even if you set them differently.  Since it is likely in Natty the Waltop will automatically placed on the Wacom driver hopefully that issue will be fixed soon.

---

### Post by Mr_VeRiTy on 2011-02-02
> **Favux said:**
> Hi Mr_VeRiTy,

Just to let you know the intended driver for the Waltop tablets is the Wacom driver.  Since you are in Maverick you should be able to use the Wacom rather than the WizardPen driver, which is needed in Lucid.  See the [Waltop HOW TO]("http://ubuntuforums.org/showpost.php?p=9966110&postcount=1").

The advantage is the Wacom driver uses a Bezier curve for pressure rather than a linear pressure curve like the WizardPen driver and so is better for drawing.  Although right now there may be an issue with both stylus buttons acting the same even if you set them differently.  Since it is likely in Natty the Waltop will automatically placed on the Wacom driver hopefully that issue will be fixed soon.
I tried using the wacom driver earlier, but the cursor kept jumping to the top left corner. What is the difference between linear and bezier curve pressure?

---

