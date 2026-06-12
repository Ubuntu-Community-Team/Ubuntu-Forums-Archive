---
title: "problems getting FF to load"
date: 2011-06-16
forum: General Help
---

### Post by hunterkasy on 2011-06-16
I am running ubuntu 11.04 64 unity, and everything has been working great except for the last 3-4 days, when I click on FF in the unity launcher the FF icon does it thing with fading in and out just like it always does when it is loading, but now it won't load, sometimes if I click the hell out of it then it will load and sometimes it wont, if I log into classic FF still wont load but If I click the hell out of FF in classic eventually it will load, and work and load back up in unity for a while then eventually it will stop loading again at random

I currently using chromium which is working fine but I don't care for it that is why I would rather use FF if I can get it to load again

I have installed all available updates for the system by using the update manager.

does anyone have any idea's?

---

### Post by lovinglinux on 2011-06-16
Start Firefox in safe mode from a terminal:

```
firefox -safe-mode
```

Open the add-ons manager by typing **about:addons** in the address bar, then disable the **Global Menu Bar Integration**. Close Firefox and launch it normally.

If that doesn't work, but i starts in safe mode, then there is another add-on causing the problem.

Otherwise, see [http://www.webgapps.org/tutorials/firefox/troubleshooting/general-troubleshooting](http://www.webgapps.org/tutorials/firefox/troubleshooting/general-troubleshooting)

---

### Post by hunterkasy on 2011-06-16
> **lovinglinux said:**
> Start Firefox in safe mode from a terminal:

```
firefox -safe-mode
```

Open the add-ons manager by typing **about:addons** in the address bar, then disable the **Global Menu Bar Integration**. Close Firefox and launch it normally.

If that doesn't work, but i starts in safe mode, then there is another add-on causing the problem.

Otherwise, see [http://www.webgapps.org/tutorials/firefox/troubleshooting/general-troubleshooting](http://www.webgapps.org/tutorials/firefox/troubleshooting/general-troubleshooting)

I put Firefox -safe-mode into the terminal

user1@user1-Satellite-L305:~$ firefox -safe-mode
** (<unknown>:4480): DEBUG: NP_Initialize
** (<unknown>:4480): DEBUG: NP_Initialize succeeded
** (<unknown>:4482): DEBUG: NP_Initialize
** (<unknown>:4482): DEBUG: NP_Initialize succeeded
** (<unknown>:4484): DEBUG: NP_Initialize
** (<unknown>:4484): DEBUG: NP_Initialize succeeded
** (<unknown>:4486): DEBUG: NP_Initialize
** (<unknown>:4486): DEBUG: NP_Initialize succeeded
/usr/lib/firefox-4.0.1/firefox-bin: symbol lookup error: /usr/lib/mozilla/plugins/libvlcplugin.so: undefined symbol: NPP_Initialize
user1@user1-Satellite-L305:~$

---

### Post by lovinglinux on 2011-06-16
> **hunterkasy said:**
> I put Firefox -safe-mode into the terminal

user1@user1-Satellite-L305:~$ firefox -safe-mode
** (<unknown>:4480): DEBUG: NP_Initialize
** (<unknown>:4480): DEBUG: NP_Initialize succeeded
** (<unknown>:4482): DEBUG: NP_Initialize
** (<unknown>:4482): DEBUG: NP_Initialize succeeded
** (<unknown>:4484): DEBUG: NP_Initialize
** (<unknown>:4484): DEBUG: NP_Initialize succeeded
** (<unknown>:4486): DEBUG: NP_Initialize
** (<unknown>:4486): DEBUG: NP_Initialize succeeded
/usr/lib/firefox-4.0.1/firefox-bin: symbol lookup error: /usr/lib/mozilla/plugins/libvlcplugin.so: undefined symbol: NPP_Initialize
user1@user1-Satellite-L305:~$

The problem is cause by VLC plugin. Tty this:

```
sudo apt-get purge mozilla-plugin-vlc
sudo apt-get purge totem-mozilla
sudo apt-get install gecko-mediaplayer
sudo apt-get install --reinstall firefox
```

Restart Firefox.

Those commands will remove VLC and Totem plugins, if installed, then install the gecko-mediaplayer, which is much better in my opinion. It will also re-install Firefox.

---

### Post by hunterkasy on 2011-06-17
> **lovinglinux said:**
> The problem is cause by VLC plugin. Tty this:

```
sudo apt-get purge mozilla-plugin-vlc
sudo apt-get purge totem-mozilla
sudo apt-get install gecko-mediaplayer
sudo apt-get install --reinstall firefox
```

Restart Firefox.

Those commands will remove VLC and Totem plugins, if installed, then install the gecko-mediaplayer, which is much better in my opinion. It will also re-install Firefox.

I removed vlc and everything works fine, thanks for your help

---

### Post by lovinglinux on 2011-06-17
> **hunterkasy said:**
> I removed vlc and everything works fine, thanks for your help

You are welcome.

---

### Post by coderand on 2011-06-22
I uninstalled 'mozilla-plugin-vlc' and that fixed the problem I had with Firefox not launching. :D

---

