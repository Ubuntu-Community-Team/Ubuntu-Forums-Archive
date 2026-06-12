---
title: "thunderbird + Firefox"
date: 2009-07-25
forum: General Help
---

### Post by oliv66 on 2009-07-25
Hello,

I have a problem with Thunderbird + Firefox.

I installed FF 3.5.1 in my home /home/olivier/firefox/ from the tarball.

I choose from System/perferences/prefered applications FF 3.5.1

When I launch Firefox 3.5.1 from Gnome or from a terminal it is FF 3.5.1 that is well-launched

When I click on a URL from Thunderbird, it is FF 3.0.0.12 which is launched except if I already launched FF 3.5.1

I tried to change two options from TB by using ALt +C 

```
user_pref("network.protocol-handler.app.http", "/home/olivier/firefox/firefox");
user_pref("network.protocol-handler.app.https", "/home/olivier/firefox/firefox");
```

but at any time, it is still /usr/bin/firefox which reappears....

I tried to write it in pref.js with no success again. Why is it impossible to change in Thunderbird ?

I tried to use sudo update-alternative --config x-www-browser with no success and finally removed this entry by mistake.

what can I do ?

Thanks for your help,

Olivier

---

