---
title: "where is streamtuner for dapper?"
date: 2006-04-20
forum: General Help
---

### Post by djroadrash on 2006-04-20
hi everyone, i was trying to download streamtuner for dapper (not the first time though) and its not there, it comes back saying:
E: coudnt find package streamtuner.
i had noticed that the last time i downloaded it was not working properly a lot of errors before it would start. 
anyone knows what happened. i know that shoutcast and live365 had problems, but i think shoutcast is fixed.
ideas?
djroadrash:D

---

### Post by croak77 on 2006-04-20
You sure its not there? I'm not on my ubuntu box. So I can't check but...

[http://packages.ubuntu.com/dapper/net/streamtuner](http://packages.ubuntu.com/dapper/net/streamtuner)

---

### Post by djroadrash on 2006-04-20
yeah its pretty strange, i added the universe and all repositories available in synaptic and nothing, still the same E: couldn't find pakage streamtuner.
:-k 
i do a lot of fresh installations, i fix and build laptops and desktops and sell them with ubuntu and other distros (usually debian ones). i download some applications so people dont have to figure out so much. just to make it easy. and last week i did two computers, one on ubuntu 64 and an other on 32, both on dapper. i downloaded streamtuner and started getting error mesages when streamtuner is booting. like i said, shoutcast was broken last week but it was fine a couple of days ago. i just went to streamtuner's website and it mentions  that live365 was updating or something and had broken the 365 part of streamtuner. but i could still get xiph to work. but this last one i dont know. never happened to me.
maybe someone knows

---

### Post by djroadrash on 2006-04-20
ok, this is even worst than i thought, im not able to download anything. i tried supertux, gnomebaker, nothing, same mistake. this is a fresh install, but did a dist-upgrade right away, and it had problems, it would not finish and so at the end i had a freeze on the splash screen. so the only way i could work on it was typing ctrl-alt-f1 and work on comand line, to fix this, i first tried to apt-get update, but it would freeze at 99% and could not get the last download for the security packages. so instead i did apt-get -f install. and then the dist-upgrade finished succesfully.then i could boot the computer and i did manage to download xmms but after that i tried streamtuner and thats when things started to get weird.
i might have to install again.
:confused:

---

### Post by djroadrash on 2006-04-20
well i figured out, so if you read this sorry for the waist of time, i did a apt-get update and everything started to work again. any idea why this happened?
thanx

---

