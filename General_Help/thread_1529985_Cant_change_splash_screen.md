---
title: "Cant change splash screen"
date: 2010-07-13
forum: General Help
---

### Post by fusky on 2010-07-13
ok i have poured over many forums and countless posts on how to do this and i cant seem to get it,i have been trying for the past 8 hrs to change the splash screen in my ubuntu 10.04 lts lucid lynx,i have installed startup manager and splash screen and have tried using thos to edit my splash screen to no avail i have no idea what im doing wrong

---

### Post by Braik on 2010-07-13
Hi there,
 
I can understand that you are not so happy because you are not able to do something, but, as in any forum some polite forms are mandatory: HELLO, THANKS, etc.
 
Now to help you with your problem, since you have Lucid (10.04) you can forget all the forums you have read because the splash screen is no more launched by Usplash as previous versions (Karmic and below), but by [PLYMOUTH]("http://en.wikipedia.org/wiki/Plymouth_(software)").
 
I still don't tried this but if you want here is one link explaining this customisation:
 
[http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html](http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html)
 
Good luck,

---

### Post by bro brian on 2010-12-15
> **Braik said:**
> Hi there,
 
I can understand that you are not so happy because you are not able to do something, but, as in any forum some polite forms are mandatory: HELLO, THANKS, etc.
 
Now to help you with your problem, since you have Lucid (10.04) you can forget all the forums you have read because the splash screen is no more launched by Usplash as previous versions (Karmic and below), but by [PLYMOUTH]("http://en.wikipedia.org/wiki/Plymouth_%28software%29").
 
I still don't tried this but if you want here is one link explaining this customisation:
 
[http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html](http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html)
 
Good luck,

  **Holy Toledo!** I've been trying to figure this out all day. I even uninstalled everything that was not native to gnome (k3b & k9 copy applications - about 50 different things) during one suggestion. Braik, your instruction led me to the answer.
  I went to the link provided, and (towards the bottom of the page) it says:

[COLOR=Navy]Now you can run the following commands to change login and plymouth screens[/COLOR]
 [INDENT][COLOR=Navy]sudo update-alternatives --config default.plymouth[/COLOR]
 [COLOR=Navy]gksu -u gdm dbus-launch gnome-appearance-properties[/COLOR]
[/INDENT]

  I copied & pasted this into terminal, and it gave me the option to either go with #1 splash or #2 splash described. I entered 1, closed the terminal, and restarted. Everything was back to normal. Thanks for the "usplash vs Plymouth" as well, Braik. Your explanation & instruction did not fall on deaf ears!

---

