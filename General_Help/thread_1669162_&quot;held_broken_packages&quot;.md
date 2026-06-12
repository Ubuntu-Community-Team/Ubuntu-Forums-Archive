---
title: "&quot;held broken packages&quot;"
date: 2011-01-17
forum: General Help
---

### Post by Delsos on 2011-01-17
i tried to install my ATI propertary driver and it says  

**[[COLOR=black]E:Unable to correct problems, you have held broken packages [/COLOR]]("http://www.google.com/url?sa=t&source=web&cd=2&ved=0CCMQFjAB&url=https%3A%2F%2Flists.ubuntu.com%2Farchives%2Fubuntu-server-bugs%2F2010-March%2F029268.html&ei=lGw0Tb6bFcT48AbNh_TpCA&usg=AFQjCNF1-KcOFztN1KvTF_QMiggX9ztb4w&sig2=swIwwMEV4eJddzAxj_9ngw")**


i have held broken packages and it wont download/install the driver :S what should i do?
 
i have had a similar problem before i think, also when i used peppermint i couldnt install my driver, but forget it i like ubuntu the best....
 
so what is the easiest way to fix this? i have no clue how to find/fix broken packages....could this happen because i clicked skip during some parts of the installation of ubuntu?

---

### Post by wojox on 2011-01-17
Open you terminal and run:

```
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update

```

---

### Post by adeee on 2011-01-17
manually you can restore or recover broken package..

restart the computer 
Then start ubuntu in recovery mood.
there is option about and like 'dpkg Repair broken Packages'. select this your broken packages recovered ..

---

### Post by Delsos on 2011-01-17
> **wojox said:**
> Open you terminal and run:

```
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update

```


worked like a charm....gotta remember to write that down!

---

