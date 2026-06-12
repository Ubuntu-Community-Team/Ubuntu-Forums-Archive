---
title: "(PIDGIN) Automatically close NickServ window?"
date: 2011-03-01
forum: General Help
---

### Post by Zen87 on 2011-03-01
Is it possible for Pidgins IRC to automatically close NickServ windows after authentication? Because right now it shows about 4-5 different windows everytime I login and it would be interesting if there is a away to remove them after authetication.

---

### Post by discipolo on 2011-03-19
sub, also annoyed by the various chat-windows ... is there any way?

---

### Post by KIAaze on 2011-04-17
I'm also looking for a solution to this.
The only solution I found so far is choosing to never popup windows for new conversations in the settings.

The other useful thing I found recently is the "hide chat" plugin, to not always popup windows for automatically joined IRC channels:
[http://developer.pidgin.im/ticket/7874](http://developer.pidgin.im/ticket/7874)
[http://developer.pidgin.im/wiki/ThirdPartyPlugins#Interfacetweaks](http://developer.pidgin.im/wiki/ThirdPartyPlugins#Interfacetweaks)
[https://launchpad.net/pidgin-hide-chat](https://launchpad.net/pidgin-hide-chat)

You'll need to check out the bazaar branch and compile from source since the latest release doesn't compile.
WARNING: It seems to currently produce a huge memory leak, so it's probably better not to use it at the moment.

I really wish there were a nice IRC client like xchat, which integrates with the indicator applet in Gnome (and the gnome keyring, like empathy does!).
Empathy and pidgin are not that great for IRC yet.

I should probably also check out KDE again to see what they have to offer on the messaging front. :)

---

### Post by sammingo on 2011-11-18
I believe you can use the pidgin plugin irchelper to achieve what you're asking.

---

### Post by discipolo on 2011-11-20
really? how? it doesnt have any configuration options does it?

---

### Post by LordDelta on 2011-12-19
As the previous poster said, irchelper doesn't actually to seem to do much, of anything...

Also the hide-on-join doesn't seem to work...maybe I'm not understanding how to use the plugin, but... it doesn't actually hide anything (I can hide the chats in the menu, but not the NickServs, which was the problem in the first place, not the channels which I don't mind seeing).

Also, slightly off-topic, but I'd like very much to know why the newer releases of glib2 don't include the .la in them, and don't want me to install those in the /usr/lib directories...very annoying for compiling new versions of pidgin (especially if the glib2 version keeps on changing).

---

