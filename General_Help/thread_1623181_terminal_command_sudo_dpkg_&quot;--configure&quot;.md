---
title: "terminal command sudo dpkg &quot;--configure&quot; &quot;-a&quot; processes halfway and stops"
date: 2010-11-16
forum: General Help
---

### Post by okkie on 2010-11-16
is there any other terminal command that will have a similar result to help me get update manager working in 10.10.Help will be appreciated.

---

### Post by mcduck on 2010-11-16
leave the quotes out of the command, they don't belong there.

```
sudo dpkg --configure -a
```

If that doesn't work, you'll pretty much have to tell a bit more about what kind of problem you are having for anybody to be able to help you.

---

### Post by okkie on 2010-11-17
thanks for your time.I get the following results and it only asked me once for my passwordokkie@mealone:~$ sudo dpkg --configure -a
okkie@mealone:~$ 
okkie@mealone:~$ sudo dpkg --configure -a
okkie@mealone:~$ sudo dpkg --configure -a
okkie@mealone:~$ sudo dpkg --configure -a
okkie@mealone:~$ 

Or must it be done in a root terminal?

---

### Post by okkie on 2010-11-17
I did the recent update in 10.10 but update was only done halfway when I was told to run the same command.I then also discovered that synaptic can not be accessed.Could the problem have anything to do with downloading medibuntu package which I have read is not suitable for 10.10 Maverick ?

---

### Post by okkie on 2010-11-20
after still trying to get command sudo dpkg --configure -a running I now got the following message and don't know where to report as I donn't know if it is a bug

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Any help will still be appreciated

---

### Post by melkespreng on 2010-11-20
Try 'Fix broken packages' under the Edit menu in synaptic. 

I had this problem today what a gone wrong java install, but that was because apt was locked in the terminal.

---

### Post by okkie on 2010-11-21
I cannot get into synaptic atall

---

