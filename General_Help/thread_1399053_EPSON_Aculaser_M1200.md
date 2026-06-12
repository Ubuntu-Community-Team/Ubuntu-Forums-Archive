---
title: "EPSON Aculaser M1200"
date: 2010-02-05
forum: General Help
---

### Post by bukarrar on 2010-02-05
Hi guys, 
I bought today a Laserprinter (EPSON Aculaser M1200) and I cant install it on my system. I got Ubuntu 9.10
can anyone help me please!
thanx

---

### Post by ellgor on 2010-02-05
Hi,

Go to the "Avasys" site,its for Epson's, and get their package.

Regards, Ellgor.

---

### Post by bukarrar on 2010-02-05
Hi Ellgor, thank u for ur Replay!
I could not find the file on AVASYS website, there are many models, but my model isn't there. is there an other website?
Regards bukarrar

---

### Post by dozdozez on 2010-04-02
> **bukarrar said:**
> Hi Ellgor, thank u for ur Replay!
I could not find the file on AVASYS website, there are many models, but my model isn't there. is there an other website?
Regards bukarrar

I bought the same printer and managed to get it working:

the epson M1200 is the same as EPL6200L

follow the instructions of marlus here:

[http://ubuntuforums.org/showthread.php?t=696363&highlight=6200l](http://ubuntuforums.org/showthread.php?t=696363&highlight=6200l)

good luck

---

### Post by vayira on 2010-09-09
Did you get it working properly? I've just bought one & am very disappointed by the lack of obvious drivers.

---

### Post by vayira on 2010-09-09
I just took my one back to the shop. I couldn't bear the idea of having constant hassles to install it. I think I try and get a HP printer instead.

---

### Post by Francesco72 on 2010-11-23
Hallo.
I'm new in this forum.
I've this printer (epson m1200), i use Ubuntu 10.04 64bit. I  tried all but i can't resolve. 
Someone can help me??? please, sorry but i'm new in Linux and i don't understand nothing about this!!!!!!
thank

---

### Post by tora201 on 2010-12-26
Go here: [http://ubuntuforums.org/showthread.php?t=1335619&highlight=EPL6200L](http://ubuntuforums.org/showthread.php?t=1335619&highlight=EPL6200L)

It works. I just tested it with a 12 page test. Did not seem to misprint, as has happened in the past. Good luck

---

### Post by marianoa on 2011-09-26
Salve a tutti,

sono decisamente in ritardo ma forse puo' ancora servire; io ho risolto seguendo alla lettera questa guida

[URL="http://valdan.net/?p=552"]http://valdan.net/?p=552
[/URL]
Buona fortuna!

---

### Post by samuelranta on 2012-01-16
Got it also working following the instructions given by Marlus. Here's my 10 section version of Marluses instructions:

1. Download epsoneplijs-0.4.1.tgz -file from address [http://sourceforge.net/projects/epsonepl/files/epsonepl/0.4.1/epsoneplijs-0.4.1.tgz/download](http://sourceforge.net/projects/epsonepl/files/epsonepl/0.4.1/epsoneplijs-0.4.1.tgz/download)

2. From terminal, in the directory where you downloaded epsoneplijs-0.4.1.tgz -file, type command: tar zxvf epsoneplijs-0.4.1.tgz 

3. Go to directory epsoneplijs-0.4.1, which you just created, with command: cd epsoneplijs-0.4.1

4. Type command: ./configure --prefix=/usr

5. Type command: sudo make install

6. Download file: [http://www.nemesys.fi/tiedostot/ubuntu/EPL-6200L-Hardy.ppd](http://www.nemesys.fi/tiedostot/ubuntu/EPL-6200L-Hardy.ppd) 

7. Connect your printer to your computer and turn it on. (You can do it in the beginning, but at least now you need it connected and powered on.)

8. Go to System Settings &#8594; Printing &#8594; click “Add” and choose from the list Epson AL-M1200.

9. Click "Forward". Ubuntu searches for drivers for some time and then gives “New printer”-window with the title “Choose driver”.

10. Tick the box "Provide PPD file” and navigate to the directory where you downloaded it and choose it.

11. Click "Open" and "Forward". Ubuntu asks if you want a test page.

---

