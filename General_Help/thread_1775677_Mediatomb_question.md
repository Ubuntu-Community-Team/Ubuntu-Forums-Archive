---
title: "Mediatomb question"
date: 2011-06-05
forum: General Help
---

### Post by griffsterb on 2011-06-05
So I got mediatomb up and running to stream to my PS3, but I want to try to fix something. This may seem extremely anal, but on my PS3 it lists 2 mediatomb 'devices'. One of them contains all of my media that I am able to play. But the other is just empty. I want to find out how to configure mediatomb so that the empty mediatomb device does not show up on the list of devices on the PS3. 

This seems pretty obscure so I don't know if anyone can actually answer this for me. But any help is appreciated. Thanks.

---

### Post by Thegmandrive on 2011-06-11
This means that you have two Mediatomb's running. 

If you run "killall mediatomb"  this will kill both that you have running. you can try to run command "killall mediatomb && mediatomb"

are you running mediatomb as root? I only ask because I was at first.. and that is not best practice. 

anyway, after you kill mediatomb just restart media tomb by typing "mediatomb"

---

