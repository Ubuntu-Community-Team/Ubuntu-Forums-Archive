---
title: "Missing dead keys in Jaunty"
date: 2009-09-19
forum: General Help
---

### Post by gilli4 on 2009-09-19
Hello,

I know that this always was and is a common issue and I have read many threads about it but none of the given solutions have worked for me so pardon for bringing up this specific issue one more time.

In Ubuntu Studio 9.04 I can't turn on my dead keys, thus I can't write letters like "é" and such.

So far I have removed SCIM to make sure there is no additional mapping but it didn't help.

Under System->Settings->Keyboard settings I have chosen the "Germany Dead acute" layout (I'm in Germany) but to no avail.

I have changed my xorg.conf and have added the following options to the keyboard section:
```

Section "InputDevice"
	Identifier     "Keyboard0"
	Driver         "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "de"
	Option          "XkbVariant"    "deadacute"
EndSection

```
But still the dead keys function is suppressed. Characters like these ´^°~ are written immediately opposed to how I wish it to be.

The only moment I do have dead keys is on the logon page, when Gnome hasn't started yet.

I am thankful for any help.

Best regards,

Gilzad

---

### Post by gilli4 on 2009-09-21
Isn't there anyone who can help me?

---

### Post by StuartN on 2009-09-21
> **gilli4 said:**
> Isn't there anyone who can help me?

In System->Preferences->Keyboard choose the Layouts tab, then Other options. Select the Compose key position and choose a convenient key, such as Right-Control. Pressing the compose key, then ' and then e gives é.

---

### Post by gilli4 on 2009-09-21
Thank you for suggesting the workaround.
Still I'm interested in actually activating the dead keys and appreciate any hints towards that.

---

### Post by StuartN on 2009-09-22
> **gilli4 said:**
> Thank you for suggesting the workaround.
Still I'm interested in actually activating the dead keys and appreciate any hints towards that.

It is not a workaround. It is the method for activating dead keys.

---

### Post by bobince on 2009-09-22
Stuart: dead keys is a different way of getting diacriticals than the compose key. However I do agree that the compose key is in almost every way preferable; I would strongly recommend using compose in preference to dead keys.

Having said that, the German dead key layout does just work for me; you shouldn't need to touch xorg.conf to enable it. Have you tried creating a new user and setting the layout there, in case there's something odd resetting the layout in your current user profile?

---

### Post by gilli4 on 2009-09-24
bobince, thanks a bunch for your suggestion.
I tried that and it just turned out the way you described it. The dead keys are active on the other account. Can you give me a hint how I can compare/exchange the specific settings? Or where else I should look for anything that might be resetting my keyboard layout?

---

