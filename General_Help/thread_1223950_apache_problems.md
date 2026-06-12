---
title: "apache problems"
date: 2009-07-26
forum: General Help
---

### Post by roquin on 2009-07-26
Hi, guys, im trying to setup apache server in ubuntu 9.04 desktop. there is some thing  wrong when i try to install apache, the files does not go to /var/www .they go to some where out( actually the first time i install them they got there(var/ww)but i uninstall it because was not working right, 

Then i try many times and the files whent some where out, and im getting messages from command line. I know there is some thing wrong. so what i want  is a way to start over by erasing all that mess(apache) and 

start over. but without reinstalling ubuntu because it take long time to setup everything(software installation.)so does some body understand what i want please post your idea and i would appreciate it. thanks (sorry engles grammar)

---

### Post by SyL on 2009-07-27
```
sudo apt-get remove apache
```then 

```
sudo apt-get install apache apache-doc apache-ssl apache-perl apache-common apache-utils 
```


HTH

---

### Post by credobyte on 2009-07-27
> **roquin said:**
> 
Then i try many times and the files whent some where out, and im getting messages from command line. 

File can't take a vacation without your permission ! What "messages" did you received from your "command line" ( via email or what ? ) ?

---

