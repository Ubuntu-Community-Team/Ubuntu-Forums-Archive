---
title: "I can't connect to my school's WiFi on Ubuntu, only."
date: 2012-08-09
forum: General Help
---

### Post by HunterDX77M on 2012-08-09
I can't seem to connect to my school's WiFi with Ubuntu. Here's what happens: I'm in school, I login, and the WiFi auto-connects. The connect lasts for about 2 minutes max, and then I'm disconnected. After that, I cannot reconnect to the WiFi unless I restart and the problem returns again in another few minutes or so. And so I have no choice but to use Windows because I simply can't connect on Ubuntu.  

Here's the strange thing. On Windows, I can connect to WiFi just fine. On Ubuntu, I can connect to my home's WiFi, just not school's. What's going on? Why does Ubuntu immediately drop my connection at school?

Ubuntu 12.04
Windows XP
Intel(R) WiFi Link 5100 AGN

I want to give the relevant information about my school's network connection, but I don't know what to give or where to get it. The first step would be if someone could show me where to get that. Thanks!

---

### Post by Zirts on 2012-08-09
Might it be something done in the schools router configurations?  Maybe ask the IT guy of you school to change it up so you could access their Wifi.

---

### Post by Mark Phelps on 2012-08-09
Don't mean to be discouraging -- but in MY experience, these problems are nearly always driver related -- and Ubuntu tends to trail behind Windows in networking drivers because the hardware vendors address MS Windows needs first.

If you're connecting at all, which apparently you are, you're probably stuck having to use Windows  because you already have the proper driver installed for Ubuntu.

However, if you're using NDISWrapper in Ubuntu, that means you're using the Windows wireless driver, and you should check to see if there is a newer version of it.  You might try using the same driver that Windows is using.

---

