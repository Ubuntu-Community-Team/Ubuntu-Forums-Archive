---
title: "Software-center crashes after authentication &gt;workaround found"
date: 2010-05-20
forum: General Help
---

### Post by Blue Rose on 2010-05-20
Goodmorning :-)
So here's what's going on:
software-center crashes everytime I want to install something.

I can browse through the lists as long as I want. It asks for authentication when I click install, but as soon as I 'OK' my password both the authentication and the main SC-window disappear.

This is what I get when I start in Konsole (I'm running Kubuntu 10.04 32bits with all updates)
```
linda@shiny:~$ software-center 
WARNING:root:No styling hints for Raleigh were found... using Human hints.
WARNING:root:No styling hints for Raleigh were found... using Human hints.
WARNING:root:No styling hints for Raleigh were found... using Human hints.
WARNING:root:No styling hints for Raleigh were found... using Human hints.
WARNING:root:No styling hints for Raleigh were found... using Human hints.
WARNING:root:No styling hints for Raleigh were found... using Human hints.
WARNING:root:No styling hints for Raleigh were found... using Human hints.
WARNING:root:No styling hints for Raleigh were found... using Human hints.
WARNING:root:No styling hints for Raleigh were found... using Human hints.
Segmentation fault

```

However I found out that running it with 'kdesudo software-center' works without problems. (That's why I tagged this SOLVED already)
Though I am not sure if this is right? The proper way would be to open as user and browse around, and only sudo stuff when actually installing something...

Any thoughts?

---

### Post by yeus on 2010-06-21
*bump* well.. no new thoughts..  but I have the same problem. At least we are not alone :)

---

