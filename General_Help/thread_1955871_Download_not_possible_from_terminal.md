---
title: "Download not possible from terminal"
date: 2012-04-10
forum: General Help
---

### Post by pavi_elex on 2012-04-10
I am not able to download from terminal

It wants to connect through proxy server ( 0% [Connecting to 192.168.0.1 (192.168.0.1)] )
192.168.0.1 is IP address of server through which all computers are connected.
Ip's of these systems are
192.168.0.2
192.168.0.3
192.168.0.4
etc...
But there are two-three systems which are not connected through server. They are  connected directly.
Ip's of these systems are
192.168.2.5
192.168.2.6
etc...
When I try to install software through terminal, it sticks on 0% [Connecting to 192.168.0.1 (192.168.0.1)] and it is not able to download.
I am not able to download any software from ubuntu software center. 
Same condition for synaptic package manager too.

Please help me...

---

### Post by zeljkojagust on 2012-04-10
Is 192.168.0.1 proxy address or maybe gateway address?

---

### Post by pavi_elex on 2012-04-10
It is IP address of proxy server from which all systems are connected except three.

---

### Post by zeljkojagust on 2012-04-10
Ok, can you access internet in general?

---

### Post by zeljkojagust on 2012-04-10
And did you configure your apt.conf to use proxy?
[https://help.ubuntu.com/community/AptGet/Howto#APT_configuration_file_method](https://help.ubuntu.com/community/AptGet/Howto#APT_configuration_file_method)

---

### Post by pavi_elex on 2012-04-10
yes i can access internet through browser but I can not download through terminal, ubuntu software center & synaptic package manager.
I am using ubuntu 11.10

Here is my apt.conf
```
Acquire::http::proxy "http://192.168.0.1:8080/";
Acquire::ftp::proxy "ftp://192.168.0.1:8080/";
Acquire::https::proxy "https://192.168.0.1:8080/";
```
It looks like it is correct because this my proxy server address and this is my port
Here are my proxy settings which I have done for browser to access internet.
```
Manual Proxy Configuration
  HTTP proxy: 192.168.0.1   PORT: 8080
   use this proxy server for all protocols (checked)
   No proxy for:  localhost,127.0.0.1
```
& by this settings I can access internet in all browsers.

---

### Post by raja.genupula on 2012-04-10
TRY:1 open the network settings and from there at proxy settings apply as system wide .

TRY 2: [http://askubuntu.com/questions/77449/how-to-configure-proxy-authentication-to-work-with-ubuntu-software-center](http://askubuntu.com/questions/77449/how-to-configure-proxy-authentication-to-work-with-ubuntu-software-center)

---

