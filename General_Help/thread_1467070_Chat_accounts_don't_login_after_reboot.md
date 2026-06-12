---
title: "Chat accounts don't login after reboot"
date: 2010-04-30
forum: General Help
---

### Post by CBung on 2010-04-30
Hello,

I setup my chat accounts in this new social business, but after a reboot, even though the accounts are checked 'enabled, they did not sign on automatically. I can't fathom that this is expected behaviour. Is anyone else having this problem? Try logging out then logging in.

Bung

---

### Post by rakkhi on 2010-07-28
I am having this same problem with 10.0.4 accounts setup work fine, reboot and they all show offline. Remove them and add them again and they work again.

Help please.

---

### Post by davidmohammed on 2010-07-28
have you tried adding a startup application (preferences - startup applications)?  Add a new entry running the command line

empathy

---

### Post by fragos on 2010-07-28
I have empathy in my startup applications but proper startup of chat is inconsistent. Sometimes my system boots with chat accounts not connected and no empathy icon in the applet bar. Empathy is however running. I then open the Chat accounts preferences and individually disable and then enable each account. Last I kill the running empathy with the System Monitor and then restart empathy with <Alt>F2. All will then work correctly.

---

### Post by rakkhi on 2010-07-29
what should I enter at startup? The chat application is running just the accounts show offline. When I remove an account and add it again it works.

Reboot stops working again.

---

### Post by davidmohammed on 2010-07-29
...

when creating a new startup option I use the following command line

sh -c "sleep 30 && empathy -h &" 

what this does is wait 30 seconds after login and start empathy in hidden mode.

---

### Post by xenton on 2010-10-10
> **davidmohammed said:**
> ...

when creating a new startup option I use the following command line

sh -c "sleep 30 && empathy -h &" 

what this does is wait 30 seconds after login and start empathy in hidden mode.

Was just having the same problem and this has sorted it, thank you kindly :P

---

