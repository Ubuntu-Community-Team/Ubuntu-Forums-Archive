---
title: "Lucid x64: Chat Applet is not auto connecting on boot, same with Ubuntu One"
date: 2010-05-03
forum: General Help
---

### Post by gohanssjn on 2010-05-03
Hello.

When I get into 10.04 x64, everything starts up on it's own except my chat applet and Ubuntu one.

To get chat accounts to work I have to start Empathy manually and then close it.  Then the applet shows me as online.

Likewise, I have to open the Ubuntu One preferences to get it to start syncing.

Ideas?

---

### Post by gohanssjn on 2010-05-04
Hmm, same thing on my laptop.  Am I missing something here?  Are they not supposed to start on login?

---

### Post by bfor75 on 2010-05-07
I have no idea if they are "supposed" to start at login or not.  I don't believe that chat did in previous versions of Ubuntu, but I'm not sure.

If you want to force empathy to start at login, you can go to preferences->startup applications and add a new startup program with command```
empathy -h
``` (assuming you don't want the contact list to pop up when you log on - if you do you can leave off the "-h").

I believe you could start Ubuntu One by creating a similar startup program with command ```
ubuntuone-launch
``` but I haven't created an Ubuntu One account yet so I'm not sure if this is the right command.

---

### Post by Cowchip7 on 2010-08-01
It connects when you uncheck and check "enable" in each account... there should be an option to just sign in! Ubuntu should get on that!

---

