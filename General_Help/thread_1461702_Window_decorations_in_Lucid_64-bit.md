---
title: "Window decorations in Lucid 64-bit"
date: 2010-04-24
forum: General Help
---

### Post by KayakJim on 2010-04-24
Trying out Lucid RC 64-bit desktop and noticed that all of the windows decorations are placing the control buttons (i.e. close, minimize, and maximize) on the left.

Does anyone know if there is a way to get them back on the right?

---

### Post by The Thunder Chimp on 2010-04-24
(Damn it, the release candidate has that too? For crying out loud, I hoped they would take that off before the official release!)

Go to System>Preferences>Appearance, and choose a different window border style, almost every border style doesn't have what you just mentioned, although the default does.

Tell me how it went!

---

### Post by KayakJim on 2010-04-24
> **The Thunder Chimp said:**
> (Damn it, the release candidate has that too? For crying out loud, I hoped they would take that off before the official release!)

Go to System>Preferences>Appearance, and choose a different window border style, almost every border style doesn't have what you just mentioned, although the default does.

Tell me how it went!

Every theme I tried did it.  :(

I tried the following:
Aging Gorilla (which is what I have been using since 8.10)
Ambiance
Atlanta
Bright
Clearlooks
ClearlooksClassic
Crux
Divinorum (Blue, Green, and Red)
Dust
Dust Sand
Esco
Inverted
Metabox
New Wave
Radiance
Simple

That is all the themes I have installed and they all have the window controls on the left instead of the right.

---

### Post by Koroviev on 2010-04-24
Launch gconf-editor, for example by pressing Alt + F2, typing gconf-editor and pressing Enter.

Navigate to apps > metacity > general on the left panel and find the button_layout option.

Set it to :minimize,maximize,close

---

### Post by KayakJim on 2010-04-24
> **Koroviev said:**
> Launch gconf-editor, for example by pressing Alt + F2, typing gconf-editor and pressing Enter.

Navigate to apps > metacity > general on the left panel and find the button_layout option.

Set it to :minimize,maximize,close

You rock! :guitar:

That fixed it right up. Thank you very much. :)

---

### Post by jerome1232 on 2010-04-24
This needs to be an option somewhere in the themes dialog.

Popular opinion seems to be towards having your controls on the left. It should be easy to change it that way if it is not going to be the default.

edit: and by left, I really meant right....


:)

---

### Post by The Thunder Chimp on 2010-04-24
> **jerome1232 said:**
> This needs to be an option somewhere in the themes dialog.

Popular opinion seems to be towards having your controls on the left. It should be easy to change it that way if it is not going to be the default.


Well, you got my vote. Although I have absolutely no intention of upgrading my Karmic. That is because bluetooth support was disbanded in Lucid (in Beta1 and Beta2 at least). I use my PS3 controller on my computer to play Nintendo 64 Games, and I don't want to lose my Super Mario 64 file \\:D/

By the way, I'm happy that there's a final solution to this problem. When I tried the Beta, I did by changing the theme. Glad it worked for you though. This is such a random, useless, confusing, and annoying thing.

---

### Post by KayakJim on 2010-04-25
> **The Thunder Chimp said:**
> Well, you got my vote. Although I have absolutely no intention of upgrading my Karmic. That is because bluetooth support was disbanded in Lucid (in Beta1 and Beta2 at least).

True in the RC as well. No Bluetooth but I thought that was something wrong with my system.

Thanks for the confirmation of that!

---

### Post by The Thunder Chimp on 2010-04-25
> **KayakJim said:**
> True in the RC as well. No Bluetooth but I thought that was something wrong with my system.

Thanks for the confirmation of that!

Glad I helped! You know that when you upgraded (I tried twice, once with Karmic to Beta1, and one from Karmic to Beta2) they give you a list of removed features. They say that "you may still be able to get support from the community". I'm back on Karmic now because my Windows partition messed itself up (what do you know?), and I had to reinstall the whole deal.

---

### Post by KayakJim on 2010-04-25
> **The Thunder Chimp said:**
> Glad I helped! You know that when you upgraded (I tried twice, once with Karmic to Beta1, and one from Karmic to Beta2) they give you a list of removed features. They say that "you may still be able to get support from the community". I'm back on Karmic now because my Windows partition messed itself up (what do you know?), and I had to reinstall the whole deal.

I was running Jaunty without issue and just went with a full fresh install rather than an upgrade. Luckily I have my /home on a separate partition making going back to Jaunty easy.

It is hard to believe they would remove Bluetooth support from an LTS release, especially when it has been working fine since 8.10. I seriously wonder sometimes what drugs the Canonical team is on when they make decisions like these.

---

### Post by Zintha on 2010-04-25
> **KayakJim said:**
> I was running Jaunty without issue and just went with a full fresh install rather than an upgrade. Luckily I have my /home on a separate partition making going back to Jaunty easy.

It is hard to believe they would remove Bluetooth support from an LTS release, especially when it has been working fine since 8.10. I seriously wonder sometimes what drugs the Canonical team is on when they make decisions like these.
I know -my- drug of choice has recently been Ubuntu.
Definatly taken away all my time :P
Not my money though, so I guess its a better drug.

---

### Post by KayakJim on 2010-04-25
> **Zintha said:**
> I know -my- drug of choice has recently been Ubuntu.
Definatly taken away all my time :P
Not my money though, so I guess its a better drug.

Yeah, what happened to "It just works"? Spending hours resolving incomplete implementations. :/

Windows doesn't take near as much effort to get running properly.

---

### Post by zipperback on 2010-04-28
> **KayakJim said:**
> Trying out Lucid RC 64-bit desktop and noticed that all of the windows decorations are placing the control buttons (i.e. close, minimize, and maximize) on the left.

Does anyone know if there is a way to get them back on the right?


Yes. Go here.
[http://ubuntuforums.org/showthread.php?p=9186310#post9186310](http://ubuntuforums.org/showthread.php?p=9186310#post9186310)

Get the Ambiance_R theme I created.

- zipperback
:popcorn:

---

### Post by zipperback on 2010-04-28
> **KayakJim said:**
> True in the RC as well. No Bluetooth but I thought that was something wrong with my system.

Thanks for the confirmation of that!

UHM? HUH?

I'm using bluetooth just fine out of the box with Lucid.
I recogizes my Phone and other BlueTooth devices without any problems.
- zipperback

---

