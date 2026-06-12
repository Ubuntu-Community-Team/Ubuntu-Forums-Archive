---
title: "Which instant messaging on LAN tool should I use for multiplatform?"
date: 2010-09-18
forum: General Help
---

### Post by abcuser on 2010-09-18
Hi,
I need to install instant messaging program that will operate inside a LAN, but I can't find any tool that would meed the following requirements:

1. Instant messaging tool working inside LAN. It should not communicate to the internet like Google Talk or Skype - network traffic must NOT leave local network - sensitive office info will be shared.
2. Must work on Windows (Windows XP and Windows 7) and Linux (Ubuntu, Debian and openSuse).
3. It should be easy to install if possible without specially dedicated server.
4. It should make it possible to users to communicate in user groups (group chat) - three or more people are writing to each other.
5. It must be a FLOSS or at least freeware (free as a beer).
6. It must have a GUI (no terminal solution)

Any suggestion which program should I use?
Thanks

---

### Post by ST3ALTHPSYCH0 on 2010-09-18
Have you looked into an Openfire server with Spark clients?

---

### Post by hugmenot on 2010-09-18
Bonjour a.k.a. Avahi a.k.a. iChat a.k.a. link-local XMPP.

You need no server, the clients discover and contact each other directly. File transfers are possible too.

No idea how much it scales, and whether your network ops tolerate link-local mDNS stuff. But I’ve seen it work properly for a network exceeding 100 users.

Possible clients are Pidgin, Empathy, Gajim, iChat. Dunno about Windows-only clients.

---

### Post by abcuser on 2010-09-19
@ST3ALTHPSYCH0, haven't tried this but it looks like specially dedicated server is required where server portion of code resists. (braking rule 3 from my first post requirements).

---

### Post by abcuser on 2010-09-19
@hugmenot, I have tried "Bonjour", I did the following:
1. On Windows besides installing Pidgin from web page [http://www.pidgin.im/](http://www.pidgin.im/) I have also downloaded and installed the following software which must be installed to enable Pidgin to communicate using Bonjour protocol: [http://support.apple.com/kb/DL999](http://support.apple.com/kb/DL999)
2. In Ubuntu I installed "pidgin" package.
3. In both Pidgins (Windows and Ubuntu) I have set Bonjour protocol and set Username, First name and Last name.
Communication works fine. I have also tried using Empathy on Ubuntu and selecting "People Nearby" protocol (this is actually Bonjour protocol but with more friendly 'human' name).

This is very nice and simple solution, but one problem left. I can't create group chat using Bonjour protocol. In Pidgin I double click on main Piding window to chat with user and then from Conversation menu select Join a chat I can't select Bonjour account. The same problem in Empaty from Conversation menu Invite Participant is grayed out for users using People Nearby protocol.

Is there any way I can enable group chat using Bonjour protocol? Is there any Pidgin extension or something like that?

---

### Post by hugmenot on 2010-09-20
Sorry to inform you:
```
freenode #pidgin
<me> group chat with bonjour/link-local xmpp. is this possible, theoretically?
<datallah> me: no
```

---

### Post by hugmenot on 2010-09-22
Apparently Empathy has it’s own implementation of serverless group chats:

[http://telepathy.freedesktop.org/wiki/Clique](http://telepathy.freedesktop.org/wiki/Clique)

I haven’t found any other clients implementing that.

---

### Post by abcuser on 2010-09-23
One more problem using bonjour protocol is security aspect. Everyone in network just sets: username, firstname and lastname no authentication required (because there is no server to authenticate). So I don't think this bonjour solution is secure for using sensitive office information. I can' be 100% sure that I am really chatting to Jack if everyone on network can set his/hers username/firstname/lastname to Jack.

If I understand correctly if security is required then IM server is also required and bonjour is not the protocol to use. Am I right? Is there any way I can be 100% sure that I am chatting with "Jack" using bonjour protocol?

---

