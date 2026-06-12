---
title: "Proxy in Console"
date: 2006-04-11
forum: General Help
---

### Post by jonnymccullagh on 2006-04-11
I am having trouble with FTP and Remote Desktop etc proxy settings. I am inside a corporate network and Web Browsing works fine as I set the proxy details within the browser.

FTP and RDP work within my local network but do not go out to the internet. I have ruled out firewall problems with my security team and the problem must be more localised.

At the command line non of the following work:
wget [http://www.google.com](http://www.google.com)
ftp 111.222.222.111
telnet ... etc

Also when I do:
echo $http_proxy
I get nothing back.

My question is: Do I need to set http_proxy, ftp_proxy and even rdp_proxy somewhere to get this running?

Thanks in advance for any help,
jonny

---

### Post by jonnymccullagh on 2006-04-12
bumping this cause I really need help sorry!

From the command line FTP, telnet etc do not work and I get error messages:
telnet: Unable to connect to remote host: Network is unreachable

I need these protocols to be aware of the proxy but I am not sure how to set them. I read in another post for Hoary that someone else was having difficulty setting proxy details in various different places - this is a mark against linux for me.

I have added:
export http_proxy="http://192.168.8.249:80/"

to 3 different files:
[LIST=1]
[*]/etc/environment
[*]/etc/profile
[*]/etc/bash.bashrc
[/LIST]

Now wget seems to be working at the command line. But I need to know what to put in to these files so that FTP, RDP, TELNET etc will go through the proxy also.

I'm not sure if the following is possible:
export rdp_proxy="rdp://192.168.8.249:80/"

Please help,
thanks,
jonny

---

### Post by Al3xanR0 on 2006-04-12
```
HTTP_PROXY=http://userid:password@proxy.com or ip.addr:port#/
```

then 

```
export HTTP_PROXY
```

then to confirm 

```
env
```

you should be able to (scroll) locate your newly entered environment variable, this has always worked for me irrespective of distro.

---

### Post by jonnymccullagh on 2006-04-13
This is still causing me lots of headaches and it is essential to me not returning to windows. Typing:
env
shows me the http_proxy variable as [http://1.2.3.4:80/](http://1.2.3.4:80/)

When I type 

wget 123.124.125.126

it works fine but when I type

ftp 123.124.125.126

it does not work with an error 'Network is unreachable'. 
Although ftp to a machine on my same subnet works e.g. ftp 192.168.1.2 

Is there no one out there who has had this problem before?
thanks,
jonny

---

### Post by Al3xanR0 on 2006-04-13
[QUOTE=jonnymccullagh] but when I type ftp 123.124.125.126

it does not work with an error 'Network is unreachable'. 
Although ftp to a machine on my same subnet works e.g. ftp 192.168.1.2 

Is there no one out there who has had this problem before?
thanks,
jonny[/QUOTE]

The env var solution that I provided previously was for http you will need to create one for ftp as well, they are different protocols and therefore use different ports. 
You will need to create the variable the same way instead it will be labled FTP_PROXY and the the portnum will be 21 vs 80 for http.

---

