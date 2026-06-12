---
title: "/root - problem with entering the directory and editing file inside"
date: 2009-11-28
forum: General Help
---

### Post by johnyjj2 on 2009-11-28
Hello!

I'd like to do the fifth step ([http://www.roseindia.net/ant/installing-ant-in-linux.shtml](http://www.roseindia.net/ant/installing-ant-in-linux.shtml)) and I edit file /root/.bash_profile . Unfortunately, I cannot enter root directory through explorer (or how it is called in Ubuntu), so I try to write in console "cd /root", but it says again that I don't have privileges. "sudo cd /root" doesn't help. How to enter /root or edit the file?

Greetings!

---

### Post by dcstar on 2009-11-28
> **johnyjj2 said:**
> Hello!

I'd like to do the fifth step ([http://www.roseindia.net/ant/installing-ant-in-linux.shtml](http://www.roseindia.net/ant/installing-ant-in-linux.shtml)) and I edit file /root/.bash_profile . Unfortunately, I cannot enter root directory through explorer (or how it is called in Ubuntu), so I try to write in console "cd /root", but it says again that I don't have privileges. "sudo cd /root" doesn't help. How to enter /root or edit the file?

```
gksudo "dbus-launch nautilus --no-desktop --browser %U"
```

---

### Post by bluestar14 on 2009-11-28
try saying sudo and a space before command Ex:
```
sudo (yourcommand)
```

---

### Post by johnyjj2 on 2009-11-29
Thank you for your answers!

I already tried "sudo (yourcommand)", as explained in my first post ("sudo cd /root"). Command "gksudo "dbus-launch nautilus --no-desktop --browser %U"" doesn't help, it asks me about password, I type it and nothing happens. Finally I succeded with "sudo gedit /root/.bash_profile". There was nothing in this file what surprised me. I added those three lines, saved and left gedit.

I'd like to install required software, mentioned here: [http://cmusphinx.sourceforge.net/sphinx4/#download_and_install](http://cmusphinx.sourceforge.net/sphinx4/#download_and_install) , i.e. 1. Java SE 6 Development Kit (JDK 6 Update 14), 2. Ant 1.6.0.   

Ad 1. I've got file jdk-6u18-ea-bin-b05-linux-i586-18_nov_2009.bin. I unpack it with sh command and accept the licence. I enter the directory and type ./configure, but it doesn't work. I don't see any INSTALL file and file README.htm doesn't contain any useful information. How to install JDK6u18 (Java SE)?

Ad 2. I follow steps mentioned here: [http://www.roseindia.net/ant/installing-ant-in-linux.shtml](http://www.roseindia.net/ant/installing-ant-in-linux.shtml) . I just finished step number five, sixth step is, if I understand properly, just restarting the computer. So Ant should work now.

Greetings!

---

### Post by johnyjj2 on 2009-12-04
May I have your answer, please?

---

