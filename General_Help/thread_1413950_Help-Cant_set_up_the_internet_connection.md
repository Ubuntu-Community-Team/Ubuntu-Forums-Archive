---
title: "Help-Cant set up the internet connection"
date: 2010-02-23
forum: General Help
---

### Post by goldengriffin on 2010-02-23
I got a dsl broadband connection....I have dual booting on my lappy(Windows7 and ubuntu 9.10)....my problem is i cannot set up the internet connection in ubuntu while i am using the connection in windows7....I am a total newbie in linux..plz help me
                                                 ](*,):(

---

### Post by nixclusive on 2010-02-23
I found [this guide](https://help.ubuntu.com/community/ADSLPPPoE) very helpful in setting up my broadband internet connection.

---

### Post by sparazza on 2010-02-23
Have you tried to set up a connection like described here? [NetworkManager0.7#Connection Types]("https://help.ubuntu.com/community/NetworkManager0.7#Connection Types")

Set up a DSL connection in network manager with same user and password that you use in win7. Try also with casuals user/pwd, because they are not very important.

If this doesn't work reply here or at most try this [PPPoE config]("https://help.ubuntu.com/8.04/internet/C/modems-adsl-pppoe.html")
Is for an old version of Ubuntu and maybe this get you some misconfiguration troubles, but you can try it with no problem.:P

Regards
Sparazza

---

### Post by shihkster1015 on 2010-02-24
an annoying but working solution would be to go to terminal and type "sudo pppoeconf"

---

