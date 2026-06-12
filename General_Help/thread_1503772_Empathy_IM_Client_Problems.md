---
title: "Empathy IM Client Problems"
date: 2010-06-07
forum: General Help
---

### Post by ice_666 on 2010-06-07
Greetings.
Im running a fresh install of Ubuntu 10.4 LTS

Up until a few hours ago everything was fine. The Indicator Applet 0.3.7 In the upper right corner in Ubuntus GNOME Panel 2.30.0 was fine.
On the Mail Icon i had all 3 option for communication, chat, setup mail & broadcast.
The problem im having now, is the chat feature has dissapeared from The Indicator Applet 0.3.7.

Heres what happened:

I installed the Ubuntu Tweak 0.5.4.1 program. All was well.
I installed the PPA for Telepathy Source.
After that, Empathy IM client was no longer a selectable option in the GNOME Panel 2.30.0.
Not only that but when i manualy launch Empathy IM client  from, Applications/Internet it loads but my facebook chat account says "network error" and wont reconnect as it done so before.

I have tried uninstalling the source, and the Empathy IM client.
Makes no difference.

I just want the chat option back in the The Indicator Applet 0.3.7 and the facebook chat account to work in  Empathy IM client.

Does anyone know how to fix this ??????????????????????:confused:

---

### Post by ice_666 on 2010-06-07
[SOLVED]

Went into synaptic package manager and uninstalled all empathy modules.
The chats back in the Indicator Applet 0.3.7 but still not facebook chat account ??????????
WTF ??????

help anyone ?

---

### Post by aggiemarine07 on 2010-06-10
@ice_666 try this: 
1. un-enable the account in empathy (edit-->accounts-->select the facebook account--> uncheck "enabled"
2.then open up your browser and log-out of facebook
3.then log back in with your facebook username (not your email address) 4.then re-enable your account in empathy. 

This process worked for me.

---

