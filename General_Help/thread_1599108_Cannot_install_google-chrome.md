---
title: "Cannot install google-chrome"
date: 2010-10-17
forum: General Help
---

### Post by CorruptDNA on 2010-10-17
I installed the ubuntu 9.10 and tried installing google chrome.. when i was downloading there was a tip that if i didnt want the repository i should use this command:
   19  sudo touch /etc/default/google-chrome

but after i used it i was unable to install google chrome..
so id like to know if there is any way to reverse this command or something..
thanks...

---

### Post by Dans564 on 2010-10-17
Run these commands in this order

set up key with
```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add - 

```

set up repo with
```
sudo sh -c 'echo "deb http://dl.google.com/linux/deb/ stable main" >> /etc/apt/sources.list.d/google.list'

```

set up and install chrome with
```
sudo aptitude update 
sudo aptitude install google-chrome-stable
```

---

### Post by CorruptDNA on 2010-10-20
thanks...solved..

---

