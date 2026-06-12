---
title: "limewire java help"
date: 2006-03-30
forum: General Help
---

### Post by zapcojake on 2006-03-30
When I try to run limewire I get this error.

Something went wrong with LimeWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

It used to work until I reinstalled.  My setup is 
AMD64 Sempron 2800+
MSI rs480 mobo
512 ram
80gig sata
I am running 32 bit breezy with Java installed by automatix
I followed the guide I found in the Wiki here which worked before.  thanks in advance--Jake

---

### Post by arnieboy on 2006-03-30
install blackdown's version of java from the repositories:
```
sudo apt-get install j2re1.4
```
then set that as the default java environment:
```
sudo update-alternatives --config java
```
choose the appropriate option from the list.
now re-run limewire.

---

### Post by bathwater on 2006-04-02
hello im new to this whole linux thing and im trying to get limewire installed ...i did the command listed above to install j2rel and it say .......couldnt find package j2rel.4.

any help would be appreciated.

---

### Post by zapcojake on 2006-04-02
probably don't have all your repositories enabled in synaptic.  See the howto section

---

### Post by zapcojake on 2006-04-02
Hello, I tried the Java fix Arnieboy suggested and this is what happened.
jake@ubuntu64:~$ runLime.sh
Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.4.2-02]
Configuring environment...
Loading LimeWire:
Invalid or corrupt jarfile LimeWire.jar

******************************************************************
Something went wrong with LimeWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

---

### Post by x5452 on 2006-04-09
finally something worked, i have installed and uninstalled limewire, frostwire and gnutella multiple times trying to get one to work right, when i installed jre1.4 limewire worked! thanks.  now that 1.4 is set as my default, will that hinder anything else that needs 1.5 to run?

---

