---
title: "how to change Computer name ?"
date: 2006-04-30
forum: General Help
---

### Post by ozkan on 2006-04-30
how to completly change Computer name ???

---

### Post by Ramses de Norre on 2006-04-30
system > administration > networking > general: you can set the hostname (= computername) there.

---

### Post by jpkotta on 2006-04-30
Be careful of what you set it to.  You can break sudo.  A safe bet is a single word with alphanumeric characters.  Just make sure it's set to something, because an empty hostname **will** break sudo.

---

### Post by ozkan on 2006-05-01
system > administration > networking > general: you can set the hostname (= computername) there.

i think this not the real local machine name !! this is the networking name. 
For Programmers ;
LocalDevice.getLocalDevice().getFriendlyName(); it returns me the old name even i have changed it with  "system > administration > networking > general".

i have still the same name of my machine

---

### Post by bram on 2006-05-04
re,

Where do you set it via the command line?

---

### Post by Ramses de Norre on 2006-05-04
sudo vi /etc/hosts
Set a line in the first section:
```
127.0.0.1 localhost.localdomain localhost comp_name
```
Do you know how to use vi? You can use nano or some otherone too.

---

### Post by ozkan on 2006-05-06
well i have another problem now ... i think i named it with a wrong name ... sudo su does'nt work it says "unable to lookup hanubuntu via gethostbyname()" what i must do ? 
help :)

---

### Post by ozkan on 2006-05-06
well i logged  in to system with  recovery mode . there is no need to put sudo . so i changed with "vi /etc/hosts"

---

