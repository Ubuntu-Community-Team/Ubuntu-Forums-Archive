---
title: "Control remote desktop"
date: 2012-01-13
forum: General Help
---

### Post by Jeroen De Dauw on 2012-01-13
I have an Ubuntu 11.10 server which is hooked up to a beamer but does not have any input devices (keyb, mouse). I have ssh access to this server and want to be able to control the GUI from my laptop (which is running Kubuntu 11.10). Is there an easy way to do this? I want as little setup work as possible.

---

### Post by HermanAB on 2012-01-13
Generally, you don't need a remote GUI, since you already have a local GUI:
$ ssh -X -C -c arcfour128 user@server "gedit /etc/fstab"

---

### Post by drdos2006 on 2012-01-13
I use Webmin to control my server.

Logon to your server and download from your server with :
```

sudo wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.570_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.570_all.deb)

Install with :
sudo dpkg -i webmin_1.550_all.deb

Add extra libraries with :
sudo apt-get -f install

Then you connect to the server with [https://server_IP:10000](https://server_IP:10000)

```
regards

---

### Post by Jeroen De Dauw on 2012-01-17
> **HermanAB said:**
> Generally, you don't need a remote GUI, since you already have a local GUI:
$ ssh -X -C -c arcfour128 user@server "gedit /etc/fstab"

Yeah, I know I can do this, but I want to control the remote GUI, not have a local one. So I don't even need to have the remote GUI duplicated locally, since it is already visible to me via beamer. All I need is a way to interact w/ it, ie send keystrokes and move the mouse.

---

