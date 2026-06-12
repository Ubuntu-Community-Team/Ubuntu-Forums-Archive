---
title: "how to setup local LAN chat with my wife | 2 computers Ubuntu 10.04"
date: 2011-01-07
forum: General Help
---

### Post by zappal on 2011-01-07
Hi ya'll ):P
I'm sorry, I have searched around about this topic, but everything just beats around the bush regading setting up jabber xmpp and all that stuff. But it seems this is built right into Ubuntu but it doesn't appear to work. I would prefer to do this built in with Empathy as opposed to Pidgin. But if we must use Pidgin, then so be it.

I see that Empathy has some setting, when i click Chat accounts, then select:
No, I just want to see people online nearby for now.
[IMG]http://img21.imageshack.us/img21/540/locallanchatsetup.png[/IMG]
But then there is just a close button and nothing happens.

Does anyone have any advice?

Extra notes:
We're both running Ubuntu 10.04 Lucid Lynx
We are wireless
We know each others local ip 192.168.10.x
firewall is disabled

---

### Post by zappal on 2011-01-08
nobody knows?

---

### Post by gradinaruvasile on 2011-01-08
That feature is supposed to work via avahi in Empathy. But Empathy has many unpolished features.
There are other programs that can do local chat, it depends what you need.

I used this:

[http://sourceforge.net/projects/ezim/](http://sourceforge.net/projects/ezim/)

You need java to be installed (sun-java6-jre package). It has text chat and file transfer. Just unpack it and run the .jar file with java (open with "java -jar" if not associated).

Edit: make sure you can ping each other, some wireless routers have a feature called ap isolation that, if enabled, dont let connected clients see each other.

---

