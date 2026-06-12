---
title: "Dash empty after update Ubuntu 12.04"
date: 2012-07-28
forum: General Help
---

### Post by Chiefree on 2012-07-28
Dash empty after update Ubuntu 12.04:

[IMG]http://uppix.net/d/d/5/0951ea59b12c11e0e241c6e08fb81.png[/IMG]

I try some commands:
unity --reset
unity --replace
sudo apt-get install --reinstall unity
but they not work for me.
Plz help me.
Thanks.

---

### Post by matt_symes on 2012-07-28
As i assume this thread is not solved, i have changed to thread status from solved, for you, to Ubuntu.

---

### Post by raja.genupula on 2012-07-28
I think your VGA drivers are the problem here . what kind of drivers you got ? give a try with reinstalling them and one more thing is before going to try with reinstallation of VGA drivers . press ctrl+alt+F1 and login there . and then type as 

```
unity --reset  

sudo restart lightdm 
```

the commands one by one . . 

all the best with your trails .

---

### Post by Chiefree on 2012-07-28
> **raja.genupula said:**
> I think your VGA drivers are the problem here . what kind of drivers you got ? give a try with reinstalling them and one more thing is before going to try with reinstallation of VGA drivers . press ctrl+alt+F1 and login there . and then type as 

```
unity --reset  

sudo restart lightdm 
```the commands one by one . . 

all the best with your trails .

Thank for your help.
I use Nvidia GF 310M on Acer AS 5745G.
After i install Nvidia drivers, Ubuntu Dash works but only use Unity 2D.
Unity 3D not works. 
Then, I install Bumblebee to use Unity 3D, Unity 3D worked and Ubuntu dash empty again. How to fix my problem??
Sorry for my English. Are you understand me?

---

