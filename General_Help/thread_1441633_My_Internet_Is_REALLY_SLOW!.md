---
title: "My Internet Is REALLY SLOW!"
date: 2010-03-29
forum: General Help
---

### Post by emanuel.b on 2010-03-29
OK, so here's my problem. I have a Gateway MT6458 Laptop. I access the internet with a Verizon MIFI 2200, and a Ativa (Office Depot) Wireless G PC-Card. (Probably has the Atheros chip in it.) When I get on the internet, getting to websites is a pain. Whenever I try to load a site, it gets stuck on "waiting for http://www.whatever.com". (Probably because it dropped the connection). I have to reload the site several times for it to work. (I tried to post this at least 15 times before it worked.) My internet speed isn't affected though, still getting 75 - 200 kb/s. (I know it seems a little slow for people lucky enough to get high speed where they live, but that's as fast Verizon's network goes.) Does anybody have an answer for my problem?

---

### Post by crucialhoax on 2010-03-29
You could try using wicd:

```
sudo apt-get install wicd
```

hopefully that helps.

---

### Post by emanuel.b on 2010-03-29
OK, I'll Try that (Even though I don't know how using a different network manager will solve the problem.), and let you know what happens...

---

### Post by cabaro on 2010-03-29
You could try iptraf to see details of your connection.

```
sudo apt-get install iptraf
```
```
sudo iptraf
```

---

### Post by emanuel.b on 2010-03-31
Alright, I tried installing wicd, but my wireless card stopped working altogether. So since I didn't have another way of connecting to the internet, I had to reinstall Ubuntu. After that, I installed iptraf, but I don't see how that is going to help me with my problem. Does anyone else have a solution?

---

### Post by emanuel.b on 2010-04-06
Just bumping it up, It's been 6 days! Any help would be appreciated!

---

### Post by emanuel.b on 2010-04-08
Could really use some help here please!

---

### Post by emanuel.b on 2010-04-08
Well, since no one would help me, I decided to try Opera. It works GREAT! I love it. Thanks anyway to anyone who tried to help. :)

---

### Post by pieface on 2010-04-08
This worked for me and others:

[https://store.opendns.com/setup/device/ubuntu/](https://store.opendns.com/setup/device/ubuntu/)

i hope it helps

---

### Post by emanuel.b on 2010-04-08
Thanks! Worked like a charm! :)

---

