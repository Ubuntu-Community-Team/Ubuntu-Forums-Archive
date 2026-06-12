---
title: "Empathy Vs pidgin"
date: 2010-05-05
forum: General Help
---

### Post by nbulchandani on 2010-05-05
Hello,
can anyone tell me why empathy is being kept in all the versions even when it does not have a proxy support.can anyone tell me any way to setup empathy behind a proxy server..maybe with proxy chains i think?
Thanks

---

### Post by graemev on 2010-05-08
Beats me too... my son just installed 10.04 ... I expected to see pidgin back and Empathy removed (since it does not work) ... but the reverse is true ... now he's lost IM access totally. ... probably regrets the upgrade.

---

### Post by DJ_Max on 2010-05-08
You do realize you can install pidgin yourself right? It's in the official repositories even.

Just because it does not support proxy isn't good enough reason why it shouldn't be kept up to date and bundled with Ubuntu. It goes great with Gnome and it's lightweight

---

### Post by graemev on 2010-05-08
He can install it and use it to send a message but the desktop integration has been done with empathy ... so he'll never be online UNLESS ha manually installs & then starts pidgin each time ....yes he could autostart it ... but  then he has a full window (not just the notify box)  ... so 90% of the time he's "off the net".

it looks like the empathy developers have no plans to fix this they are relying n support from a library. Until they get that, empathy simply does not work (and so should be maked as broken in the repository)  ...when it doe get library support  ..then I can start to complain to the empathy developers about lack of individual proxy support ... I don't want every tool to use the SAME proxy  ...so it needs to be configurable per tool (like firefox ....and pidgin )

---

### Post by DJ_Max on 2010-05-08
Empathy works, but it has issues with proxies. I'm using it fine, Empathy is the default client for Gnome, which is why it was included in a default install. If you dont like it install something else

---

### Post by henrydubb on 2010-05-08
> **nbulchandani said:**
> Hello,
can anyone tell me why empathy is being kept in all the versions even when it does not have a proxy support.can anyone tell me any way to setup empathy behind a proxy server..maybe with proxy chains i think?
Thanks

It does look pretty silly to have Empathy bundled and not Pidgin but if you have a support issue (irc) Pidgin not Empathy is recommended. 

Yes Pidgin can easily be installed and likewise the me menu uninstalled. The primary reason I don't use the me menu is choice of im client. If it was Pidgin I would most likely us it, although its much easier doing that stuff from a browser.

---

### Post by antoiner_roquentin on 2011-06-08
I switched from Empathy to Pidgin today and noticed that the menu in the top right corner where I can list my availability and my "about me" settings does not seem to work with the chat accounts or availability option. From what I gather reading this thread that part of the GUI is tied directly to the program called Empathy. Is that correct? If so, are those options on the menu just "dead"?

I decided on Pidgin instead because I wanted better support for IRC and figured I could just use Skype if I really wanted to video conference with anyone. What do you all think about IRC support from Pidgin VS Empathy?

---

### Post by hatalar205 on 2011-06-08
> **antoiner_roquentin said:**
> I switched from Empathy to Pidgin today and noticed that the menu in the top right corner where I can list my availability and my "about me" settings does not seem to work with the chat accounts or availability option. From what I gather reading this thread that part of the GUI is tied directly to the program called Empathy. Is that correct? If so, are those options on the menu just "dead"?

I decided on Pidgin instead because I wanted better support for IRC and figured I could just use Skype if I really wanted to video conference with anyone. What do you all think about IRC support from Pidgin VS Empathy?

When you open Pidgin, Tools - Preferences - System Tray Icon (change to Always)

---

### Post by antoiner_roquentin on 2011-06-09
Hey, that makes the bar work! You are awesome hatalar205, thanks!

---

### Post by dimas869 on 2012-05-06
which is the repository for pidgin?

---

### Post by ubuntu27 on 2012-05-07
Pidgin is in the main repository. You can install with the following command in the terminal.
```
[sudo apt-get install pidgin]("apt://pidgin")
```

Or just **click on [it]("apt://pidgin")** ;-)

---

### Post by dimas869 on 2012-05-07
thanks ubuntu27, you are right...although i would like to point out an issue i am having on it with a hotmail.com account either using MSN or WLM protocol that i am not able to receive the custom smileys from my friends (only see the trigger and also my friend in his/her messenger) and they dont receive my file transfer requests...do you think you can help me?...i am using Ubuntu 12.04 and the pidgin 2.10.3

thanks

sorry....after restarting pidgin WLM protocol from msn-pecan plugin fixed the problem for me

---

