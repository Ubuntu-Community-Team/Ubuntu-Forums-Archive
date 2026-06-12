---
title: "Flash Player Crashes with Firefox/ Chrome/ Chromium"
date: 2012-02-22
forum: General Help
---

### Post by didkoslawow on 2012-02-22
I searched in the forum, but i found only old problems. The solutions of them did not helped me at all. I tried to install manualy flash from adobe, also adobe-flashplugin and flashplugin-installer etc in repos, but with no luck.

FP crash in video sites like youtube and vbox7(dot)com (it's bulgarian alternative of youtube), but no crashing in flash pics and some games like 5strike(dot)com.
Here is a code when I run chrome/firefox/chromium in terminal and try to run flash video.
Firefox
```
didko@Acer:~$ firefox
WARNING: pipe error (68): &#1045;&#1076;&#1085;&#1086;&#1089;&#1090;&#1088;&#1072;&#1085;&#1085;&#1086; &#1087;&#1088;&#1077;&#1082;&#1098;&#1089;&#1074;&#1072;&#1085;&#1077; &#1085;&#1072; &#1074;&#1088;&#1098;&#1079;&#1082;&#1072;&#1090;&#1072; &#1086;&#1090; &#1086;&#1090;&#1089;&#1088;&#1077;&#1097;&#1085;&#1072;&#1090;&#1072; &#1089;&#1090;&#1088;&#1072;&#1085;&#1072;: file /build/buildd/firefox-10.0.2+build1/build-tree/mozilla/ipc/chromium/src/chrome/common/ipc_channel_posix.cc, line 419
```
Chromium
```
didko@Acer:~$ chromium-browser 
[20165:20175:21125651132:ERROR:web_data_service.cc(625)] Cannot initialize the web database: 2

(exe:20306): Gdk-WARNING **: XID collision, trouble ahead

(exe:20306): Gdk-WARNING **: XID collision, trouble ahead

```

Edit: I'm using Ubuntu 11.10 with gnome-shell

---

### Post by lovinglinux on 2012-02-22
Get [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/). Run the Wizard after installation. If it still crashes, run the wizard again, but unselect the option to override GPU validation in the Tweaking section.

---

### Post by didkoslawow on 2012-02-22
Still the same problem. :(

---

### Post by lovinglinux on 2012-02-22
> **didkoslawow said:**
> Still the same problem. :(

Please click Flash-Aid menu, select "Help >> Generate Report" and paste the result here.

---

### Post by didkoslawow on 2012-02-22
It says that the file was not found. - /home/didko/Desktop/firefox-report.txt.

---

### Post by lovinglinux on 2012-02-22
> **didkoslawow said:**
> It says that the file was not found. - /home/didko/Desktop/firefox-report.txt.

Please attach the firefox-report.txt file generated in your desktop after running the commands below:

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'pluginreg.dat' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat ~/.mozilla/firefox/**/pluginreg.dat >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by didkoslawow on 2012-02-22
There it is. I needed to creat folder Desktop in my home dir and it was ok. Sorry for missunderstanding.

---

### Post by lovinglinux on 2012-02-22
Nothing wrong in your report.

Plase try to log into Unity 3D and test a flash video, then log into Unity 2D and do the same, just to see if the problem is related to gnome-shell.

---

### Post by didkoslawow on 2012-02-22
Still the same crashes.:confused:

---

### Post by lovinglinux on 2012-02-22
> **didkoslawow said:**
> Still the same crashes.:confused:

Do you have the latest video driver installed and activated? Make sure of that and test it. Also try to create a new user, just for testing. It could be some gnome settings causing this. A new user would avoid using bad config files.

If that doesn't result in any improvement boot into a LiveCd and check if the problem can be replicated. If yes, I would check if your hardware is working properly and if it is properly ventilated.

---

### Post by didkoslawow on 2012-02-23
My drivers for Nvidia GeForce 9500M GS were installed via jockey-gtk. This is "version current" - recommended
```
NVIDIA Driver Version: 280.13
```
About a week ago, I tried to install version 173, but it was a total mess. Interesting thing is that the crashes started whit no updates/upgrades. They starts from nowhere. I will try whit new user and report for you soon as I can. 
Thanks for helping me. 8-[

Edit: Ok, I just install the update for chromium-browser and the problem is solved :shock:. Now I've got no problem with mozilla/google chrome/chromium-browser. I guess it was a problem whit chromium after all. Thank you for your help mate!
I will change the title of my thread to Solved.

---

### Post by didkoslawow on 2012-02-23
Ok, the crashes are back! But now I know where is the problem!
I'm configurating my sound card by using this thread [http://ubuntuforums.org/showthread.php?t=921637](http://ubuntuforums.org/showthread.php?t=921637). When crashes were gone my sound card was not installed! When I installed the script for alsa and restart, I have sound, but flash is crashing agayn. :confused::confused:

---

### Post by lovinglinux on 2012-02-23
> **didkoslawow said:**
> Ok, the crashes are back! But now I know where is the problem!
I'm configurating my sound card by using this thread [http://ubuntuforums.org/showthread.php?t=921637](http://ubuntuforums.org/showthread.php?t=921637). When crashes were gone my sound card was not installed! When I installed the script for alsa and restart, I have sound, but flash is crashing agayn. :confused::confused:

At least you know the problem comes from alsa.

I am not sure if this is a solution or if you need extra configuration , but you could try to install *flashplugin-nonfree-extrasound*. I remember a few years back that it was used to solve some flash audio issues. If it doesn't solve the problem, I would recommend removing the package and then running this:

```
sudo apt-get autoremove
```

This will remove unnecessary packages installed as dependency of the *flashplugin-nonfree-extrasound*.

---

### Post by didkoslawow on 2012-02-23
How can I romove the alsa that was installed by the script and install the one that is in the repositories? I was trying to config the CineDash panel, that's why I installed the alsa from the script, before that I have no problems.

---

### Post by lovinglinux on 2012-02-23
Try this:

```
sudo apt-get install --reinstall libasound2 lib32asound2 libasound-plugins linux-sound-base alsa-base
```

---

### Post by didkoslawow on 2012-02-23
The following packages are missing:
```
lib32asound2 libasound-plugins
```

I realised that I have installed pulseaudio and alsa* on my Ubunutu, realy don't know what cause the flash crash. In the morning, when I login in guest account it works out of the box, whit no crashes, and now even in guess account I get crashes. I realy messed up my system, am I?

I am considering to dist-upgrade to 12.04, is safe for daily using? I hope that, this will solve my annoying problem.

---

### Post by lovinglinux on 2012-02-23
> **didkoslawow said:**
> The following packages are missing:
```
lib32asound2 libasound-plugins
```

I realised that I have installed pulseaudio and alsa* on my Ubunutu, realy don't know what cause the flash crash. In the morning, when I login in guest account it works out of the box, whit no crashes, and now even in guess account I get crashes. I realy messed up my system, am I?

I am considering to dist-upgrade to 12.04, is safe for daily using? I hope that, this will solve my annoying problem.

Ubuntu 12.04 is sitll alpha, so is not recommended.

If you have a separate partition for your /home you can easily reinstall Ubuntu 11.10 without losing your personal stuff.

---

