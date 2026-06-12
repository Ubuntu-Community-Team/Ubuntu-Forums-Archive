---
title: "Bug in gksu/menubar. Anyone else noticed?"
date: 2006-06-19
forum: General Help
---

### Post by Horizon on 2006-06-19
Have any of you noticed that when you have a menu open (applications/places/system) and gksu tries to bring up a prompt you get that "could not grab mouse" warning/error?

If you want to replicate it you can put a menu bar next to your notification area and click the update manager icon in your notification area and then quickly click system before the prompt comes up.

The reason I'm posting here is because I was curious to see if this bug existed in kde too. Anyone here that uses kde willing to test if the kde menus also cause this warning/error?

If anyone is interested or wants to confirm it I filed the bug here: [https://launchpad.net/bugs/47048](https://launchpad.net/bugs/47048)

---

### Post by Horizon on 2006-06-22
*bump* no one?

---

### Post by MarinaraOfDeath on 2006-06-22
Yeah, I saw that the other day. It looks like some sort of half-assed attempt at a security measure:

"You can't do anything else while loading a program with root privileges. Nevermind that once the program is loaded you can switch to whatever program you want..."

---

### Post by Horizon on 2006-06-22
[QUOTE=MarinaraOfDeath]Yeah, I saw that the other day. It looks like some sort of half-assed attempt at a security measure:

"You can't do anything else while loading a program with root privileges. Nevermind that once the program is loaded you can switch to whatever program you want..."[/QUOTE]
lol you think it's a security feature?I never really thought of that. It sounds like a pretty stupid one to me because it doesn't provide any security...

Also it's only with the menus...you can launch a program etc. it just won't let you have a menu open which is why I thought it must be something to do with the way the menu highlights or gets focus or something.

---

### Post by mannheim on 2006-06-22
When gksudo is launched, it tries to "grab" the keyboard and mouse, so that it has exclusive use of them. This is a security measure: it is designed to prevent a password-stealing program from grabbing your password. Without this measure, a malicious program could read your password while you thought you were typing it into gksudo's dialog. Or even if there is nothing malicious, you might find that you had accidentally brought your text editor to the foreground, so that instead of typing you password into gksudo you accidentally typed it in your text editor before you realised what you were doing. If your text editor has an "undo" feature, that password is now stored in memory even if you delete it from the text editor ... and so on.

So that's why gksudo tries to grab keyboard and mouse.

The fact that open menus prevent gksudo grabbing the keyboard and mouse is possibly a bug.

---

### Post by Horizon on 2006-06-23
[QUOTE=mannheim]When gksudo is launched, it tries to "grab" the keyboard and mouse, so that it has exclusive use of them. This is a security measure: it is designed to prevent a password-stealing program from grabbing your password. Without this measure, a malicious program could read your password while you thought you were typing it into gksudo's dialog. Or even if there is nothing malicious, you might find that you had accidentally brought your text editor to the foreground, so that instead of typing you password into gksudo you accidentally typed it in your text editor before you realised what you were doing. If your text editor has an "undo" feature, that password is now stored in memory even if you delete it from the text editor ... and so on.

So that's why gksudo tries to grab keyboard and mouse.

The fact that open menus prevent gksudo grabbing the keyboard and mouse is possibly a bug.[/QUOTE]
Hmm I see what you mean with the security thing. What it seems to me is that the menus were written without this in mind. So I guess this would be more appropriate to fix through the gnome-panel...to maybe let go of the mouse and keyboard for gksu. I'm not really sure how it works, maybe there is already a mechanism to check which application has grabbed the keyboard and mouse but that also sounds like a security-risk-in-waiting if it's not done right...

---

