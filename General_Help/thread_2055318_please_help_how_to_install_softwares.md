---
title: "please help how to install softwares"
date: 2012-09-09
forum: General Help
---

### Post by nareshsonti on 2012-09-09
HI sir 
I am using first time for ubuntu linux 12.04 .But its very diffcult me when i am install any  softwares comparing windows very diffcult.please help any one me how to install softwares , how to see installation folders and also how to install JEE servers(weblogic r tomcat) 
i am waiting for your replay's

thanks and regards
naressonti

---

### Post by zombifier25 on 2012-09-09
Search in the Ubuntu Software Center. No need to go anywhere. Just search for the apps you want and click "Install". Or use the terminal:
```
sudo apt-get install chromium
```
for Chromium browser.

About web servers, see [here](https://help.ubuntu.com/12.04/serverguide/index.html) on how to set up a basic web server on Ubuntu. Note that setting up a web server and using a desktop computer are different from each other, so it should not be done on Ubuntu Desktop Edition (the one with the Software Center)

---

### Post by raja.genupula on 2012-09-09
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by idoitprone on 2012-09-09
> **zombifier25 said:**
> Search in the Ubuntu Software Center. No need to go anywhere. Just search for the apps you want and click "Install". Or use the terminal:
```
sudo apt-get install chromium
```for Chromium browser.

About web servers, see [here]("https://help.ubuntu.com/12.04/serverguide/index.html") on how to set up a basic web server on Ubuntu. Note that setting up a web server and using a desktop computer are different from each other, so it should not be done on Ubuntu Desktop Edition (the one with the Software Center)

synaptic package packager is easier to use
```

sudo apt-get install synaptic

sudo synaptic
```

---

### Post by raja.genupula on 2012-09-09
> **idoitprone said:**
> synaptic package packager is easier to use
```

sudo apt-get install synaptic

sudo synaptic
```

+1 and software center is very much easier to new people and it is pre-installed  . 

its always better to use gksudo instead of sudo while launching GUI application which need root access .

---

### Post by ramsharan065 on 2012-09-09
In order to install any software, you can use software center. But all software cannot be installed using software center.

---

### Post by elliotn on 2012-09-09
> **raja.genupula said:**
> +1 and software center is very much easier to new people and it is pre-installed  . 

its always better to use gksudo instead of sudo while launching GUI application which need root access .

synaptic is the easiest of them all
sudo apt-get install tomcat

---

### Post by jerrrys on 2012-09-09
[Synaptic Package Manager +1]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F")

---

### Post by Cheesemill on 2012-09-09
This link will tell you everything you need to know about installing software:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

