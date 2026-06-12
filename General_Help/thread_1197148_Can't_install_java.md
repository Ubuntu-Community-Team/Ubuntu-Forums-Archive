---
title: "Can't install java"
date: 2009-06-25
forum: General Help
---

### Post by g35celicaz on 2009-06-25
I just installed ubuntu 8.10 on my laptop and i cant install dvd support, audio and video codecs, flash and java.


I went to this website where i got the command to put in the terminal to install dvd support, audio and video codecs, flash and java:


[http://linuxowns.wordpress.com/2008/10/30/5-things-to-do-after-installing-ubuntu-810-intrepid-ibex/](http://linuxowns.wordpress.com/2008/10/30/5-things-to-do-after-installing-ubuntu-810-intrepid-ibex/)



And put this command in the terminal:

    sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list && wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add – && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2



And it gave me this:

g35celicaz@g35celicaz-laptop:~$     sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list && wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add – && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
[sudo] password for g35celicaz: 
--2009-06-25 16:21:18--  [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 278 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[=================================================================================>] 278         --.-K/s   in 0s      

2009-06-25 16:21:19 (8.11 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [278/278]

gpg: can't open `–': No such file or directory


What can I do?

Please help!

 - Thanks:)

---

### Post by credobyte on 2009-06-25
Flash, media codecs, etc. :
```
sudo apt-get install ubuntu-restricted-extras
```
Java :
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

---

### Post by ~sHyLoCk~ on 2009-06-25
Do:
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

And then:
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```


Then try installing from synaptic itself.

---

### Post by AlexsAntidote on 2009-06-25
To answer your question specifically regarding the code you were trying to use from that website, I think there was an extra dash in there... 

Original code:
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add – && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

Try this instead:
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O | sudo apt-key add – && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

I think that will fix it... There's probably better ways to do what you are trying to do, but this should work now anyway...

---

