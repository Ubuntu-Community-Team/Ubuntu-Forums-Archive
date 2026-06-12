---
title: "Kdenlive 9.0 broken packages"
date: 2012-05-16
forum: General Help
---

### Post by Jack7on on 2012-05-16
Hi! I've been using Ubuntu for the past 2 years now and untill now I've never had any problems I couldn't overcome, After scrowling round the internet for the past 2 hours looking for help I've had no luck.

I'm trying to install the new Kdenlive 9.0, But whenever I try I always get the broken packages error, I've tried all the ways I can think of to fix it and it's not working. :(

When trying sudo install via terminal I get 
```
E: Unable to correct problems, you have held broken packages.

```
When I try via Synaptic or Software center I come across similar messages.

I tried to do apt-get clean apt-get autoremove apt-get update apt-get upgrade apt-get install -f. But neither of them helped.
And yes I've tried clicking fix packages + adding packages via software sources.

Any help will be very much appreciated :)

---

### Post by Chelidze on 2012-05-24
try

```
sudo add-apt-repository ppa:sunab/kdenlive-release && sudo apt-get update && sudo apt-get install kdenlive
```

---

