---
title: "Pidgin Facebook Protocol Icon"
date: 2011-05-03
forum: General Help
---

### Post by dekaru on 2011-05-03
I just installed the latest pidgin and pidgin-facebook-chat packages on Ubuntu 11.04 and I noticed that Facebook contacts are now treated as Jabber/XMPP contacts. Before today, I could easily distinguish which protocol my contacts were on, but this is no longer the case.

Does anyone have any idea on how to set the protocol icon back to Facebook's logo?

Thanks

---

### Post by hazrpg on 2011-08-21
I have the same issue too, yet I still haven't worked out how to fix this. Sounds like it could be a bug, since no matter how much I change "XMPP" to "Facebook (XMPP)" it still reverts back... and the icon doesn't show up. Its odd.

Could someone help shed some light on this?

Regards,
Haz

P.S. Sorry to drag up an old thread, I just thought there was no point starting a new one, when the old one wasn't answered yet.

---

### Post by hazrpg on 2011-08-21
I've found a solution/workaround for this, and it works quite well. There's a plugin that lets you override the protocol icon, which can be found her: [http://code.google.com/p/pidgin-icon-override/](http://code.google.com/p/pidgin-icon-override/)

To use:
1) Simply put the .so file into /home/<user>/.purple/plugins/
2) Look in the plugins section of Pidgin for "Protocol Icon Override" (if you can't find it, close and reopen pidgin).
3) Modify (or add, if you haven't already) an account, and in the advanced section you should now have a box to type in the icon you would like to override with. The name you type will depend on the icons you have available in /usr/share/pixmaps/pidgin/protocols/16. Don't add the .png part of the name in the box however.

Examples of names you can type:
aim
bonjour
facebook
gadu-gadu
google-talk
icq
irc
jabber
yahoo

Just to name a few. Hope this helps some of you out there.

---

### Post by davedorm on 2013-01-31
An oldie but goodie. Placed well on Google search and very helpful, thanks! ):P

---

