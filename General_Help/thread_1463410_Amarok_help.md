---
title: "Amarok help"
date: 2010-04-26
forum: General Help
---

### Post by fipem on 2010-04-26
hi there, I was wondering if you could pliz help me on a couple of thing, I need a command to tell the alarm to start the playback of amarok on the morning, I also need a way to be able to see lyrics in amarok, and last, any tip on how to make the amarok lauch faster? is takes like 5 min!

Amarok ver 2.3.0 
Ubuntu karmic koala

thanks a lot in advance and sorry for the english, best regards from Valparaíso - Chile

---

### Post by Axel-P on 2010-04-26
> **fipem said:**
> hi there, I was wondering if you could pliz help me on a couple of thing, I need a command to tell the alarm to start the playback of amarok on the morning, I also need a way to be able to see lyrics in amarok, and last, any tip on how to make the amarok lauch faster? is takes like 5 min!


5 mins?!?! Run it on the terminal, I'm sure you'll get some error message, those are useful in the forums ;).

I have no idea how to program the alarm in command line, but if you want to know how to see the lyrics in amarok search Ultimate Lyrics in the scripts list. Tools>Script Manager>Get more scripts>Most downloaded. And it's the first one ;)

Buena suerte!

---

### Post by fipem on 2010-04-26
> **Axel-P said:**
> 5 mins?!?! Run it on the terminal, I'm sure you'll get some error message, those are useful in the forums ;).

I have no idea how to program the alarm in command line, but if you want to know how to see the lyrics in amarok search Ultimate Lyrics in the scripts list. Tools>Script Manager>Get more scripts>Most downloaded. And it's the first one ;)

Buena suerte!

man you are gonna laugh, but what do you mean with "run it on the terminal" what command do I have to run?

thanks for the ultimate lyrics advise, cant download from amarok since it gives me an error, but I did it manualy, now restarting amarok

and it's taking like 10 minutes, I have 7.500 songs but I dont think it could be the problem

thanks!

---

### Post by fipem on 2010-04-26
[QUOTE=fipem;9179871]man you are gonna laugh, but what do you mean with "run it on the terminal" what command do I have to run?

thanks for the ultimate lyrics advise, cant download from amarok since it gives me an error (Loading of providers from file: [http://download.kde.org/ocs/providers.xml](http://download.kde.org/ocs/providers.xml) failed), but I did it manualy, now restarting amarok

and it's taking like 10 minutes, I have 7.500 songs but I dont think it could be the problem

thanks![/QUOTEit says:

 Unable to contact server - no website returned

:(

---

### Post by jollieadrina on 2010-04-26
[COLOR=#000000][FONT=Times New Roman][COLOR=#333333][FONT=arial]Hi, i installed amarok so i could manage my i pod shuffle but now i have bi idea how to put my music on my ipod, i am only familiar with i tunes, can anybody help??

[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by Axel-P on 2010-04-27
> Hi, i installed amarok so i could manage my i pod shuffle but now i have bi idea how to put my music on my ipod, i am only familiar with i tunes, can anybody help??

Usually you should see three parts in amarok's main screen, the first one is your collection, the second one is your song's info and the third one is your playlist. Plug your iPod and mount it (if necessary). You should then see it appearing in the first section of amarok (also try restarting amarok once your iPod is connected). Then you should be able to right click any song/album/artist/collection in your local connection and copy to collection>name of your iPod. One little thing. Sometimes my iPod freezes when connecting it to my machine, it's not big deal I just reset it. But I know that it freezes because of the screen. This may happen to you, but I have no idea how to find out if your iPod freezes without a screen :P

> man you are gonna laugh, but what do you mean with "run it on the terminal" what command do I have to run?

thanks for the ultimate lyrics advise, cant download from amarok since it gives me an error, but I did it manually, now restarting amarok

and it's taking like 10 minutes, I have 7.500 songs but I dont think it could be the problem


The command to run amarok it's pretty straight forward: amarok

You have connection issues? Does this only happens with amarok? Do you have any special configuration in amarok? Do you have any proxy?

Also try this. If you're in gnome and the only kde application you have is amarok, delete the .kde folder (it's a hidden folder) in your home folder. If you have KDE or if you have many kde applications erase the folder amarok located in YOUR HOME FOLDER/.kde/share/apps/

IMPORTANT
You will loose all your amarok configuration. Included manually installed plug-ins.

---

### Post by fipem on 2010-04-27
> **Axel-P said:**
> Usually you should see three parts in amarok's main screen, the first one is your collection, the second one is your song's info and the third one is your playlist. Plug your iPod and mount it (if necessary). You should then see it appearing in the first section of amarok (also try restarting amarok once your iPod is connected). Then you should be able to right click any song/album/artist/collection in your local connection and copy to collection>name of your iPod. One little thing. Sometimes my iPod freezes when connecting it to my machine, it's not big deal I just reset it. But I know that it freezes because of the screen. This may happen to you, but I have no idea how to find out if your iPod freezes without a screen :P



The command to run amarok it's pretty straight forward: amarok

You have connection issues? Does this only happens with amarok? Do you have any special configuration in amarok? Do you have any proxy?

Also try this. If you're in gnome and the only kde application you have is amarok, delete the .kde folder (it's a hidden folder) in your home folder. If you have KDE or if you have many kde applications erase the folder amarok located in YOUR HOME FOLDER/.kde/share/apps/

IMPORTANT
You will loose all your amarok configuration. Included manually installed plug-ins.

Thanks for the reply pal, I will run it on the command, by the way it takes that time while it shows me the startup image... in case it helps somehow to fix the issue...

I have no connection issue what so ever, and it only happens with amarok, the rest work fine and on the fly, I have just try to load a couple of scripts, one is the alarm (which doesnt even appear as installed but cant re-istall eaither since it says that I have to unistall the previous one, which again I cant even see) the other is ultimate lyrics which doesnt work for me, tryed to change the config several times with no luck, just unable to see lyrics. I dont have  any proxy.

I'll try ur recommendation, thanks! Best regards,

---

