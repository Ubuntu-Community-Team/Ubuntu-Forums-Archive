---
title: "XRDP HowTo"
date: 2011-04-28
forum: General Help
---

### Post by mastermindg on 2011-04-28
Does anybody know of a decent guide to getting xrdp working on 10.04. I've installed it but it's not working on of the box. The configuration files are blank under /etc/xrdp.

Thanks.

---

### Post by mastermindg on 2011-04-28
Got xrdp.ini configured and I'm able to connect now. However, black screen and nothing else.

---

### Post by cavalier911 on 2011-04-29
[B]Lubuntu 10.04 Lucid XRDP Setup
[/B]```
sudo apt-get install xrdp vino
``````
sudo leafpad /usr/share/applications/vino-preferences.desktop
```Change
OnlyShowIn=GNOME;
To
#OnlyShowIn=GNOME;
Save/Close
```
sudo cp /etc/xrdp/xrdp.ini /etc/xrdp/xrdp.ini.bak
``````
sudo leafpad /etc/xrdp/xrdp.ini
```[globals]
bitmap_cache=yes
bitmap_compression=yes
port=3389
crypt_level=low
channel_code=1

[xrdp1]
name=RDP2VINO
lib=libvnc.so
username=ask
password=ask
ip=127.0.0.1
port=5900

Remove everything below.
Save/Close

Restart xrdp
```
sudo service xrdp restart
```Start vino
menu/Preferences/Remote Desktop
Tested as working settings:
Sharing: both boxes checked
Security: nothing checked 
By default xrdp/sesman autostarts on boot with init.d file.
Use sysv-rc-conf to configure it to not autostart if desired.
Vino which is required to access desktop does not autostart.
Vino autostart : 
menu/Preferences/Desktop Session Settings/Automatically Started Applications
Check Enabled Remote Desktop
OK

---

### Post by mastermindg on 2011-04-29
XRDP.ini had same configuration. I removed authentication from vino and manually started vino-server. I'm still getting a black screen :( when connecting.

---

### Post by cavalier911 on 2011-04-29
> **mastermindg said:**
> Does anybody know of a decent guide to getting xrdp working on 10.04. I've installed it but it's not working on of the box. The configuration files are blank under /etc/xrdp.

Thanks.

Blank configuration files equals failed install of xrdp.

Update apt-get.
```
sudo apt-get update
```
Empty package cache to force download of new xrdp.deb
```
sudo apt-get clean
```
Remove xdrp and purge corrupt or misconfigured config files.
```
sudo apt-get -y purge xrdp
```
Download/install xrdp no autoinstall recommended vnc4server you have vino.
```
sudo apt-get --no-install-recommends install xrdp
```
Read the output at the end of the install.Make sure the rsa keys are generated/saved and xdrp sesman is started with no errors.

Complete every step of the setup instructions in my previous post in the order given.

---

### Post by mastermindg on 2011-04-30
Thanks cavalier911! I really appreciate all the help.

I figured out that the issue is not with xrdp, it's with my rdp client. I'm attempting to connect via my Galaxy tablet using pocketcloud. It doesn't seem to like xrdp. I'll work it from this side.

Thanks again.

---

### Post by mastermindg on 2011-04-30
Good news: I'm able to connect now using a different app on Anroid: Remote Desktop (standard version).

However, when I connect via RDP from android or windows I'm able to affect my desktop but I'm not able to see any of those changes in my window. For example: I can switch to a different tab on my browser in my active session and it will show this change live but NOT on my connecting device.

Any ideas?

---

### Post by JoeGoalie on 2011-12-13
> **cavalier911 said:**
> Start vino
menu/Preferences/Remote Desktop
Tested as working settings:
Sharing: both boxes checked
Security: nothing checked 
By default xrdp/sesman autostarts on boot with init.d file.
Use sysv-rc-conf to configure it to not autostart if desired.
Vino which is required to access desktop does not autostart.
Vino autostart : 
menu/Preferences/Desktop Session Settings/Automatically Started Applications
Check Enabled Remote Desktop
OK
I am stuck here.  How do I start Vino?  Also, in Menu>Preferences Remote Desktop is nowhere to be found...

---

### Post by fpinero on 2013-01-12
cavalier911's guide works perfectly, Thank you cavalier911. 
The main problem I see, and it's disturbing, is that you are allowing connect via a VNC client to your computer to anyone.
Doing this "(vino) Security: nothing checked" Anyone can connect to your PC via your 5900 port without being forced to enter a paswd.
If you connect to your PC using a terminal server client, you are asked for an user and password, but if you connect to your PC using a vnc client, you login your computer directly, no password is required. Sounds scary.

Regards

---

### Post by overdrank on 2013-01-12
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

