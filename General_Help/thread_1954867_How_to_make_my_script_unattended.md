---
title: "How to make my script unattended?"
date: 2012-04-08
forum: General Help
---

### Post by anon200 on 2012-04-08
Hi,

I have written a very simple bash script (at '/bin/maintain'):
```
apt-get update && apt-get upgrade && apt-get autoremove && apt-get autoclean
```I run this once in a while, I have automated the process to a degree.
However, I still have to answer things like:
```
After this operation, 4,096 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
```I wanted to ask if you know a way in which I can automatically answer all prompts with Y.

Thanks.

---

### Post by ridetheteapot on 2012-04-08
apt-get takes a -y option that will do it.

also for commands that dont have it build in you can check out a command called 'yes'

---

