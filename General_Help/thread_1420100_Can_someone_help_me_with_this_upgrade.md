---
title: "Can someone help me with this upgrade?"
date: 2010-03-02
forum: General Help
---

### Post by petedes5 on 2010-03-02
So i am an extreme ubuntu noob.
[http://ubuntuforums.org/showthread.p...10#post6589810]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")


I download the alsaupgrade.tar file from the attached files part of the thread.

All that i got was the .sh file that was text only ????
peter@peter-laptop:~$ sudo ./AlsaUpgrade-1.0.22.1-2.sh -c
sudo: ./AlsaUpgrade-1.0.22.1-2.sh: command not found
peter@peter-laptop:~$ 


i saved it to my desktop ran the above command and got nothing

---

### Post by wojox on 2010-03-02
You need to:

```
cd Desktop
```

```
tar xvf AlsaUpgrade-1.0.22.1-2.tar
```

```
sudo ./AlsaUpgrade-1.0.22.1-2.sh -d
```

```
sudo ./AlsaUpgrade-1.0.22.1-2.sh -c
```

```
sudo ./AlsaUpgrade-1.0.22.1-2.sh -i
```

```
sudo shutdown -r 0
```

---

### Post by petedes5 on 2010-03-02
thank you thank you thank you!!!

---

