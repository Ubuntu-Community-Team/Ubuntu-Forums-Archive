---
title: "LAN chat client"
date: 2012-08-05
forum: General Help
---

### Post by c2tarun on 2012-08-05
hi friends

In my flat we have 4 laptops, 3 with windows and one with kubuntu. We all are connected to a wifi router. is there any app with we can chat on our home network?

---

### Post by Dylan1473 on 2012-08-05
*Nevermind, seems Empathy has no Windows version.*

This is just a vague memory so just throwing it out there, but I think Empathy has some kind of LAN chat feature. You could also try setting up a local IRC server or something, but that would of course be ridiculous overkill.

EDIT: Empathy does indeed have a LAN chat feature.

EDIT AGAIN: But no Windows version, apparently. Disregard.

---

### Post by HermanAB on 2012-08-05
Skype, Google, Yahoo all do chat and voice.

Otherwise, you can run a Jabber server and use Pigeon.

---

### Post by c2tarun on 2012-08-05
> **HermanAB said:**
> Skype, Google, Yahoo all do chat and voice.

Otherwise, you can run a Jabber server and use Pigeon.

For skype, google and Yahoo we require internet. :( Is there no software that can be used without internet?

---

### Post by Dylan1473 on 2012-08-05
Well, running a server doesn't technically require internet and isn't necessarily that difficult. Once the initial setup is finished chatting on it will require virtually no effort. Is that something you're willing to attempt?

EDIT: It's a little old but [here's a tutorial to install a server called jabberd2]("http://nil.uniza.sk/instant-messaging/xmpp/installing-jabberd2-server-ubuntu-1010-maverick"), if you're wondering. It's meant for Ubuntu 10.10 but it should probably work in 12.04 as well. There may be simpler solutions, I'm not sure - never hosted a jabber server before. Anyway, it can be installed on your Ubuntu computer for sure (I checked and it's still in the repositories) and should be accessible through LAN. If you port forward to it you can of course use it over the internet as well. After this (or any jabber server) is set up, you'll be able to chat on it using many different chat clients including the open source, cross platform and feature rich Pidgin.

---

### Post by c2tarun on 2012-08-06
> **Dylan1473 said:**
> Well, running a server doesn't technically require internet and isn't necessarily that difficult. Once the initial setup is finished chatting on it will require virtually no effort. Is that something you're willing to attempt?

EDIT: It's a little old but [here's a tutorial to install a server called jabberd2]("http://nil.uniza.sk/instant-messaging/xmpp/installing-jabberd2-server-ubuntu-1010-maverick"), if you're wondering. It's meant for Ubuntu 10.10 but it should probably work in 12.04 as well. There may be simpler solutions, I'm not sure - never hosted a jabber server before. Anyway, it can be installed on your Ubuntu computer for sure (I checked and it's still in the repositories) and should be accessible through LAN. If you port forward to it you can of course use it over the internet as well. After this (or any jabber server) is set up, you'll be able to chat on it using many different chat clients including the open source, cross platform and feature rich Pidgin.


This might work :) I'll go home and try today. Thanks
I'll reply if this works

---

