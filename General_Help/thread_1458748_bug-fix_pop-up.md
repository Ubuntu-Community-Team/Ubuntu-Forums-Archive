---
title: "bug-fix pop-up"
date: 2010-04-20
forum: General Help
---

### Post by utnu on 2010-04-20
The bugfix popup disappears before you can click on it.

Where do you go, to chase down whatever the popup was about?

---

### Post by Untitled_No4 on 2010-04-20
What version of KDE are you using?
What version of Kubuntu?
Does the popup appears when an application crashes or just sometimes?
Does it have an image of a ladybird?

---

### Post by utnu on 2010-04-20
KDE 4.3.2

Kubuntu 1.154
(by the way, what is the recommended way to find the version number ? )

The popup appears at random times, (no crash involved).

I think it has the image of a ladybug, (which you can only get a quick glimpse of )

---

### Post by Untitled_No4 on 2010-04-20
Okay, it is most likely just a pop-up telling you there are updates to your system. In KDE 4.3.2 those popup appeared and disappeared without you being able to bring them up again. In KDE 4.4 which is the version which will come with Kubuntu Lucid Lynx the you will be able to click on the notification icon (the i in your system tray) and see which notifications you have missed.

What you need to do now is update your system. Go to System -> KPackageKit in the menu and when it opens click on Software Updates and you will be able to update your system. 

To find your Kubuntu version run ```
cat /etc/issue
``` in terminal. It will say Ubuntu because that's the base system, and the name of the release. Yours should say Ubuntu karmic.

---

### Post by utnu on 2010-04-20
[QUOTE=]
To find your Kubuntu version run ```
cat /etc/issue
``` in terminal. It will say Ubuntu because that's the base system, and the name of the release. Yours should say Ubuntu karmic.[/QUOTE]
it says
Ubuntu 9.10 \n \l

---

### Post by Untitled_No4 on 2010-04-20
9.10 = Karmic Koala

[https://wiki.ubuntu.com/DevelopmentCodeNames](https://wiki.ubuntu.com/DevelopmentCodeNames)

---

### Post by Chris Musampa on 2010-04-20
> **Untitled_No4 said:**
> In KDE 4.4 which is the version which will come with Kubuntu Lucid Lynx the you will be able to click on the notification icon (the i in your system tray) and see which notifications you have missed.


Also works in Kubuntu Karmic for me.

```
me@karmic32:~$ kde4-config --version
Qt: 4.5.2
KDE: 4.3.2 (KDE 4.3.2)
kde4-config: 1.0

```

---

### Post by utnu on 2010-04-28
> **Untitled_No4 said:**
> . In KDE 4.4 which is the version which will come with Kubuntu Lucid Lynx the you will be able to click on the notification icon (the i in your system tray) and see which notifications you have missed..
I clicked the (i), and there it was . .  the latest bugfix.
Thanks

---

