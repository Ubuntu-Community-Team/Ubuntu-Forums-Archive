---
title: "sudo ./postgresplus-8.4.1-2-lixuz-x64.bin command not found"
date: 2010-07-21
forum: General Help
---

### Post by markhorrocks on 2010-07-21
I am trying to install postgres using the one click installer from [http://www.enterprisedb.com/learning/pginst_guide.do](http://www.enterprisedb.com/learning/pginst_guide.do). 

I downloaded the file into Downloads and ls shows me the file. When I enter the command "sudo ./postgresplus-8.4.1-2-linux-x64.bin", I get "sudo: ./postgresplus-8.4.1-2-linux-x64.bin: command not found".

What am I doing wrong?

---

### Post by lykeion on 2010-07-21
PostgreSQL 8.4.3 is available in the repos, install like this:
```
sudo apt-get install postgresql
```

Read more here: [Ubuntu Community Documentation PostgreSQL]("https://help.ubuntu.com/community/PostgreSQL")

---

### Post by ellekigjj on 2010-07-21
hello

---

