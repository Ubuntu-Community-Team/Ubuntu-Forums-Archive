---
title: "cant open most websites"
date: 2011-11-05
forum: General Help
---

### Post by dashhamid on 2011-11-05
i use ubuntu10.04 for two years.but yesterday i noticed cant open any website except Google. i changed mtu size to 1492 for eth0.but didnt work.i reinstalled ubuntu again and 
the problem not solved and this time i want install openjdk-6-jre from synaptic package manager. but there is not any jdk distribution in synaptic .unfortunately the command 
sudo apt-get install openjdk-6-jre gives me an error.

Help me please

---

### Post by nickleboyblue on 2011-11-05
...I don't know a solution, but it sounds to me like the only reason why Google loads is because it's in your browser's cache, which would mean that, for some reason, your connection isn't working.  If you connect over wifi normally, try plugging in and see if that works.  If it does, there's something wrong with your wireless card.  If it does not, it probably has nothing to do with your computer and you need to check with your router or your network administrator.

Changing any Ubuntu network settings, like adding blocked ip addresses, setting up a proxy, or something similar is very difficult and can lead to this kind of problem very easily.  If you've been doing this sort of thing as of late, you may need to find a way to reverse all of the settings you just tweaked.

---

### Post by _0R10N on 2011-11-05
This problem only occurs when surfing the web? Which browser have you tried? any other internet based program works?

---

### Post by _0R10N on 2011-11-05
why do you relate this issue to openjdk?

---

