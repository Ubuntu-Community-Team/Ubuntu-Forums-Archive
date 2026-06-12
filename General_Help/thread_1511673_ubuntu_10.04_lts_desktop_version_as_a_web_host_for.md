---
title: "ubuntu 10.04 lts desktop version as a web host for production site"
date: 2010-06-17
forum: General Help
---

### Post by freakshowtm on 2010-06-17
is it possible  to use ubuntu 10.04 lts desktop version as a web host for a production site?..

if it is possible, can anyone give me links on how to do it?..

preferably a step by step guide because i'm new to linux..

---

### Post by dcstar on 2010-06-17
> **freakshowtm said:**
> is it possible  to use ubuntu 10.04 lts desktop version as a web host for a production site?..

if it is possible, can anyone give me links on how to do it?..

preferably a step by step guide because i'm new to linux..

Install Apache, search for HOWTOs on using it for appropriate details.

---

### Post by okplayer02 on 2010-06-17
yes you can install the LAMP stack Linux Apache Mysql Php on your desktop version but just be reminded that having a GUI run on top of a server can add security holes in your web server. I suggest that you could run Webmin on a server edition giving you a way to configure your server graphically.

---

### Post by freakshowtm on 2010-06-17
thanks but is there any specific guide you can give me?..

i have already read a lot of guides but i'm still stuck..
now, i'm confused because i have tried to follow different guides..

i don't know if i will still continue with my current install or start from scratch..

i have my localhost working but it will not work if i try accessing it via url..
i don't know if i setup the ip address and dns correctly..

---

### Post by okplayer02 on 2010-06-26
here is a community documentation on LAMP for ubuntu you will see the steps.


[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by athx on 2010-06-26
Word of warning: in being a webhost, your box will be a lot more likely to be compromised; I'd advise, that unless you've got a fair bit of experience in securing nix boxes and configuring services like apache, you give it a miss. I'm all too well aware this will be largely ignored, but that's not my loss.

---

