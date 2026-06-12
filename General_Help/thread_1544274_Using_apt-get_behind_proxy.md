---
title: "Using apt-get behind proxy"
date: 2010-08-02
forum: General Help
---

### Post by rohit raj on 2010-08-02
I have just upgraded from kubuntu 9.10 to kubuntu 10.04. Earlier my apt-get was working after setting http_proxy and ftp_proxy variables in .bashrc. But now in Kubuntu 10.04 apt-get is not working? What to do

---

### Post by rohit raj on 2010-08-02
someone help

---

### Post by anglican on 2010-08-02
> **rohit raj said:**
> I have just upgraded from kubuntu 9.10 to kubuntu 10.04. Earlier my apt-get was working after setting http_proxy and ftp_proxy variables in .bashrc. But now in Kubuntu 10.04 apt-get is not working? What to doI set my PROXY variables in /etc/profile.d/proxy.sh. Something like (change IP number to suit):
> export http_proxy=http://192.168.1.1:3128/
export ftp_proxy=http://192.168.1.1:3128/
export no_proxy=.your.domain
export HTTP_PROXY=http://192.168.1.1:3128/
export FTP_PROXY=http://192.168.1.1:3128/
export NO_PROXY=.your.domain
apt-get should just need the necessary environment variable setting.

H

---

### Post by rohit raj on 2010-08-02
I created the file /etc/profile.d/proxy.sh still apt-get does not works. Except apt-get and kpackagekit my internet work. Earlier when i was on kubuntu 9.10 my apt-get was working, kpackagekit was working and i had got apt-get working by putting just these 2 lines in .bashrc

#proxy
export http_proxy="http://192.168.15.2:8000/"
export ftp_proxy="ftp://192.168.15.2:8000/"

But curiously even at that time(Kubuntu 9.10)  my kpackagekit was working but if i tried to install recommeded update from update-notifier. I was getting the following error

```
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_IN.bz2  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_IN.bz2  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch http://dl.google.com/linux/deb/dists/stable/Release.gpg  Could not connect to dl.google.com:80 (209.85.153.93). - connect (111: Connection refused) [IP: 209.85.153.93 80]


```
By the way i upgraded from 9.10 to 10.04 using apt-get.

---

### Post by anglican on 2010-08-03
> **rohit raj said:**
> I created the file /etc/profile.d/proxy.sh still apt-get does not works. Except apt-get and kpackagekit my internet work. Earlier when i was on kubuntu 9.10 my apt-get was working, kpackagekit was working and i had got apt-get working by putting just these 2 lines in .bashrc

#proxy
export http_proxy="http://192.168.15.2:8000/"
export ftp_proxy="ftp://192.168.15.2:8000/"

But curiously even at that time(Kubuntu 9.10)  my kpackagekit was working but if i tried to install recommeded update from update-notifier. I was getting the following error

```
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_IN.bz2  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_IN.bz2  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch http://dl.google.com/linux/deb/dists/stable/Release.gpg  Could not connect to dl.google.com:80 (209.85.153.93). - connect (111: Connection refused) [IP: 209.85.153.93 80]


```By the way i upgraded from 9.10 to 10.04 using apt-get.
apt-get should just take its proxy settings from those environment variables, however this can be over-ridden with an entry in[COLOR=#993300]**[COLOR=Black] /etc/apt/apt.conf, [/COLOR]**[COLOR=Black]something like:[/COLOR][/COLOR] 
```
Acquire::http::proxy “http://myname:mypassword@proxy:8080&#8243;; 
```Since you've upgraded, maybe there's something like that causing a problem... alternatively, maybe adding such an entry will fix your problem ;) 
BTW are you sure the port number for your proxy is 8000 and not 8080?


H

---

### Post by rohit raj on 2010-08-03
Thanks it did solved the problem. I should have done it earlier as i was modifying apt.conf in ubuntu 9.04. But since it was not required in kubuntu 9.10 and i did not knew what to do with apt.conf.d directory. I was perplexed. Thanks a lot

---

