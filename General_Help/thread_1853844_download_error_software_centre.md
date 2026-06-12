---
title: "download error software centre"
date: 2011-10-03
forum: General Help
---

### Post by sirvinniei on 2011-10-03
every time I download something with software center i get this error
```
installArchives() failed: Selecteren van voorheen niet geselecteerd pakket p7zip. 
(Database inlezen ...  (Database inlezen ... 5%% (Database inlezen ... 10%% (Database inlezen ... 15%% (Database inlezen ... 20%% (Database inlezen ... 25%% (Database inlezen ... 30%% (Database inlezen ... 35%% (Database inlezen ... 40%% (Database inlezen ... 45%% (Database inlezen ... 50%% (Database inlezen ... 55%% (Database inlezen ... 60%% (Database inlezen ... 65%% (Database inlezen ... 70%% (Database inlezen ... 75%% (Database inlezen ... 80%% (Database inlezen ... 85%% (Database inlezen ... 90%% (Database inlezen ... 95%% (Database inlezen ... 100%% (Database inlezen ... 206647 files and directories currently installed.) 
Uitpakken van p7zip (uit .../p7zip_9.04~dfsg.1-1_i386.deb) ... 
Processing triggers for man-db ... 
Instellen van ttf-wqy-zenhei (0.9.45-1) ... 
Regenerating fonts cache... failed; see /var/log/fontconfig.log for more information. 
dpkg: fout bij afhandelen van ttf-wqy-zenhei (--configure): 
 subproces installed post-installation script gaf een foutwaarde 1 terug 
Instellen van p7zip (9.04~dfsg.1-1) ... 
No apport report written because MaxReports is reached already
Fouten gevonden tijdens behandelen van: 
 ttf-wqy-zenhei 
Instellen van ttf-wqy-zenhei (0.9.45-1) ... 
Regenerating fonts cache... failed; see /var/log/fontconfig.log for more information. 
dpkg: fout bij afhandelen van ttf-wqy-zenhei (--configure): 
 subproces installed post-installation script gaf een foutwaarde 1 terug 

```ussualy the program does work afterwards when i try it.

---

### Post by sirvinniei on 2011-10-08
bump, does anybody know a solution?

---

### Post by sirvinniei on 2011-11-08
double bump

---

### Post by matt_symes on 2011-11-08
Hi
[FONT=monospace]
I don't totally understand what is in the code block in post [/FONT][FONT=monospace]#1[/FONT][FONT=monospace] but i think [/FONT]the font ttf-wqy-zenhei[FONT=monospace] is not configured correctly.

Open a terminal and type

[/FONT]```
sudo dpkg --configure ttf-wqy-zenhei

```

After doing that type

```
dpkg -l ttf-wqy-zenhei
```

That is a small L after dpkg. 

Post the results of both commands back here. Give a translation into English as well if you can.

Kind regards

---

### Post by sirvinniei on 2011-11-08
> **matt_symes said:**
> Hi
[FONT=monospace]
I don't totally understand what is in the code block in post [/FONT][FONT=monospace]#1[/FONT][FONT=monospace] but i think [/FONT]the font ttf-wqy-zenhei[FONT=monospace] is not configured correctly.

Open a terminal and type

[/FONT]```
sudo dpkg --configure ttf-wqy-zenhei

```After doing that type

```
dpkg -l ttf-wqy-zenhei
```That is a small L after dpkg. 

Post the results of both commands back here. Give a translation into English as well if you can.

Kind regards
```
vincent@ultimo sapientiae:~$ sudo dpkg --configure ttf-wqy-zenhei
sudo: unable to resolve host ultimo sapientiae
[sudo] password for vincent: 
Instellen van (translation: configuring of) ttf-wqy-zenhei (0.9.45-3) ...
Regenerating fonts cache... failed; see /var/log/fontconfig.log for more information.
dpkg: fout bij afhandelen van (translation: error with handling) ttf-wqy-zenhei (--configure):
 subproces installed post-installation script gaf een foutwaarde 1 terug (translation: gave error value 1)
Fouten gevonden tijdens behandelen van (translation: errors found with handling of) :
 ttf-wqy-zenhei
vincent@ultimo sapientiae:~$ dpkg -l ttf-wqy-zenhei
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Naam           Versie         Omschrijving
+++-==============-==============-============================================
iF  ttf-wqy-zenhei 0.9.45-3       "WenQuanYi Zen Hei" A Hei-Ti Style (sans-ser
vincent@ultimo sapientiae:~$ ^C
vincent@ultimo sapientiae:~$
```heres what my  terminal says

---

### Post by matt_symes on 2011-11-08
Hi> 
[FONT=monospace]
[/FONT]Regenerating fonts cache... failed; see /var/log/fontconfig.log for more information.
<snip>
iF  ttf-wqy-zenhei 0.9.45-3       "WenQuanYi Zen Hei" A Hei-Ti Style (sans-ser

The problem is your font is half installed. It's having trouble regenerating the font cache for some reason.

I would ask you to post this file  /var/log/fontconfig.log but i don't think i would understand it.

Open a terminal and type

```
fc-cache -fv | grep ttf-wqy-zenhei
```

Post results back here.

Kind regards

---

### Post by sirvinniei on 2011-11-08
> **matt_symes said:**
> Hi

The problem is your font is half installed. It's having trouble regenerating the font cache for some reason.

I would ask you to post this file  /var/log/fontconfig.log but i don't think i would understand it.

Open a terminal and type

```
fc-cache -fv | grep ttf-wqy-zenhei
```Post results back here.

Kind regards
I entered this in a terminal
where can i find those results?

---

### Post by matt_symes on 2011-11-08
Hi

> **sirvinniei said:**
> I entered this in a terminal
where can i find those results?

If you see nothing after that command that means it has not added it to your font cache at all.

Let's remove the font altogether.

```
sudo apt-get remove --purge ttf-wqy-zenhei
```

Then lets reinstall it again.

```
sudo apt-get install ttf-wqy-zenhei 
```

Kind regards

---

### Post by sirvinniei on 2011-11-08
> **matt_symes said:**
> Hi



If you see nothing after that command that means it has not added it to your font cache at all.

Let's remove the font altogether.

```
sudo apt-get remove --purge ttf-wqy-zenhei
```Then lets reinstall it again.

```
sudo apt-get install ttf-wqy-zenhei 
```Kind regards
```
vincent@ultimo sapientiae:~$ fc-cache -fv | grep ttf-wqy-zenhei
vincent@ultimo sapientiae:~$ sudo apt-get remove --purge ttf-wqy-zenhei
sudo: unable to resolve host ultimo sapientiae
[sudo] password for vincent: 
Pakketlijsten worden ingelezen... Klaar
Boom van afhankelijkheden wordt opgebouwd       
Statusinformatie wordt gelezen... Klaar  
De volgende pakketten werden automatisch geïnstalleerd en zijn niet langer nodig:
  libpanel-applet-4-0 libswscale0 gir1.2-totem-1.0 libavutil50 libpostproc51
  alien-arena-common libtotem0 libseed-gtk3-0 libavformat52 libenet0debian1
  libavcodec52 ttf-aenigma libreadline5 gir1.2-totem-plparser-1.0
  gir1.2-panelapplet-4.0
U kunt deze verwijderen via 'apt-get autoremove'.
De volgende pakketten zullen VERWIJDERD worden:
  ttf-wqy-zenhei*
0 pakketten opgewaardeerd, 0 pakketten nieuw geïnstalleerd, 1 te verwijderen en 0 niet opgewaardeerd.
1 pakketten niet volledig geïnstalleerd of verwijderd.
Door deze operatie zal er 16,9 MB schijfruimte vrijkomen.
Wilt u doorgaan [J/n]? j
(Database inlezen ... 288024 files and directories currently installed.)
ttf-wqy-zenhei wordt verwijderd ...
Wissen van configuratiebestanden voor ttf-wqy-zenhei ...
Processing triggers for fontconfig ...
vincent@ultimo sapientiae:~$ sudo apt-get install ttf-wqy-zenhei
sudo: unable to resolve host ultimo sapientiae
Pakketlijsten worden ingelezen... Klaar
Boom van afhankelijkheden wordt opgebouwd       
Statusinformatie wordt gelezen... Klaar  
De volgende pakketten werden automatisch geïnstalleerd en zijn niet langer nodig:
  libpanel-applet-4-0 libswscale0 gir1.2-totem-1.0 libavutil50 libpostproc51
  alien-arena-common libtotem0 libseed-gtk3-0 libavformat52 libenet0debian1
  libavcodec52 ttf-aenigma libreadline5 gir1.2-totem-plparser-1.0
  gir1.2-panelapplet-4.0
U kunt deze verwijderen via 'apt-get autoremove'.
De volgende NIEUWE pakketten zullen geïnstalleerd worden:
  ttf-wqy-zenhei
0 pakketten opgewaardeerd, 1 pakketten nieuw geïnstalleerd, 0 te verwijderen en 0 niet opgewaardeerd.
Er moeten 9185 kB aan archieven opgehaald worden.
Door deze operatie zal er 16,9 MB extra schijfruimte gebruikt worden.
Ophalen:1 http://nl.archive.ubuntu.com/ubuntu/ oneiric/main ttf-wqy-zenhei all 0.9.45-3 [9185 kB]
9185 kB opgehaald in 16s (573 kB/s)                                            
Selecteren van voorheen niet geselecteerd pakket ttf-wqy-zenhei.
(Database inlezen ... 288013 files and directories currently installed.)
Uitpakken van ttf-wqy-zenhei (uit .../ttf-wqy-zenhei_0.9.45-3_all.deb) ...
Processing triggers for fontconfig ...
Instellen van ttf-wqy-zenhei (0.9.45-3) ...
Regenerating fonts cache... failed; see /var/log/fontconfig.log for more information.
dpkg: fout bij afhandelen van ttf-wqy-zenhei (--configure):
 subproces installed post-installation script gaf een foutwaarde 1 terug
Fouten gevonden tijdens behandelen van:
 ttf-wqy-zenhei
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
sorry, no translation because the text is so big but i will translate if there are specific things you need to know

---

### Post by matt_symes on 2011-11-08
Hi

Can you post the output of [FONT=monospace]the file [/FONT]/var/log/fontconfig.log. 

Can you run it through Google translate please.

Kind regards

---

### Post by sirvinniei on 2011-11-09
> **matt_symes said:**
> Hi

Can you post the output of [FONT=monospace]the file [/FONT]/var/log/fontconfig.log. 

Can you run it through Google translate please.

Kind regards
```
vincent @ end Sapientiae: ~ $ fc-cache-fv | grep ttf-wqy-zenhei
vincent @ end Sapientiae: ~ $ sudo apt-get remove - purge ttf-wqy-zenhei
sudo: unable to resolve host end Sapientiae
[Sudo] password for vincent:
Reading package lists ... Ready
Dependencies tree is constructed
Status information is read ... Ready
The following packages were automatically installed and are no longer needed:
  libpanel-applet 4-0 libswscale0 gir1.2-totem-1.0 libavutil50 libpostproc51
  alien-arena-common-libtotem0 libseed gtk3-0 libavformat52 libenet0debian1
  libavcodec52 ttf-aenigma gir1.2 libreadline5-1.0-totem-plparser
  gir1.2 panel applet-4.0
It can be removed using 'apt-get auto remove.
The following packages will be REMOVED:
  ttf-wqy-zenhei *
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Through this operation, 16.9 MB of disk release.
Would you like to continue [Y / n]? j
(Reading database ... 288024 files and directories Currently installed.)
ttf-wqy zenhei-removed ...
Deleting configuration files for ttf-wqy-zenhei ...
Processing triggers for fontconfig ...
vincent @ end Sapientiae: ~ $ sudo apt-get install ttf-wqy-zenhei
sudo: unable to resolve host end Sapientiae
Reading package lists ... Ready
Dependencies tree is constructed
Status information is read ... Ready
The following packages were automatically installed and are no longer needed:
  libpanel-applet 4-0 libswscale0 gir1.2-totem-1.0 libavutil50 libpostproc51
  alien-arena-common-libtotem0 libseed gtk3-0 libavformat52 libenet0debian1
  libavcodec52 ttf-aenigma gir1.2 libreadline5-1.0-totem-plparser
  gir1.2 panel applet-4.0
It can be removed using 'apt-get auto remove.
The following NEW packages will be installed:
  ttf-wqy-zenhei
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
9185 kB of archives should be retrieved.
Through this operation, 16.9 MB of additional disk space will be used.
Get: 1 http://nl.archive.ubuntu.com/ubuntu/ oneiric / main ttf-wqy zenhei-all 0.9.45-3 [9185 KB]
9185 KB picked up in 16s (573 KB / s)
Selecting previously deselected package ttf-wqy-zenhei.
(Reading database ... 288013 files and directories Currently installed.)
Unpacking ttf-wqy-zenhei (from .../ttf-wqy-zenhei_0.9.45-3_all.deb) ...
Processing triggers for fontconfig ...
Setting up ttf-wqy-zenhei (0.9.45-3) ...
Regenerating fonts cache ... failed, see / var / log / fontconfig.log for more information.
dpkg: error processing ttf-wqy zenhei-(- configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-wqy-zenhei
E: Sub-process / usr / bin / dpkg returned an error code (1)
```
```
/usr/share/fonts: caching, new cache contents: 0 fonts, 4 dirs
/usr/share/fonts/X11: caching, new cache contents: 0 fonts, 4 dirs
/usr/share/fonts/X11/Type1: caching, new cache contents: 49 fonts, 0 dirs
/usr/share/fonts/X11/encodings: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/util: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap: caching, new cache contents: 0 fonts, 2 dirs
/usr/share/fonts/cmap/adobe-japan1: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap/gs-cjk-resource: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/truetype: caching, new cache contents: 1 fonts, 20 dirs
/usr/share/fonts/truetype/font-install: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/truetype/freefont: caching, new cache contents: 13 fonts, 0 dirs
/usr/share/fonts/truetype/msttcorefonts: Bus error
```

---

### Post by matt_symes on 2011-11-09
Hi
[FONT=monospace]
[/FONT]> /usr/share/fonts/truetype/msttcorefonts: Bus errorLooks like the Microsoft true type fonts are the root cause of the problem here.

Can you post the output of 

```
dpkg -l | grep msttcorefonts
```It may be worth trying to purge and reinstall them on your system.

```
sudo apt-get remove --purge msttcorefonts
``````
sudo apt-get install msttcorefonts
```I have never come across a bus error when regenerating the font cache so i have to be careful about any advice i give here. It may be because the font is corrupted but this is supposition.

Wait to see what others think.

Kind regards

---

### Post by sirvinniei on 2011-11-09
> **matt_symes said:**
> Hi
[FONT=monospace]
[/FONT]Looks like the Microsoft true type fonts are the root cause of the problem here.

Can you post the output of 

```
dpkg -l | grep msttcorefonts
```It may be worth trying to purge and reinstall them on your system.

```
sudo apt-get remove --purge msttcorefonts
``````
sudo apt-get install msttcorefonts
```I have never come across a bus error when regenerating the font cache so i have to be careful about any advice i give here. It may be because the font is corrupted but this is supposition.

Wait to see what others think.

Kind regards
the first command didn work,
I was  able to remove  te packages but when i try to install ( run last command) 
i get this (see attachment)
and I can press the ok button

---

### Post by sirvinniei on 2011-11-09
downloaded it with updatemanager,
now I can once again use the softwarecentre without errors thanks dude

---

### Post by matt_symes on 2011-11-09
Hi
[FONT=monospace]
[/FONT]> dpkg -l | grep msttcorefonts                     > the first command didn work,You mean it did not return anything ? Maybe that was part of the problem as it was trying to configure them. Was this an upgrade from an earlier version ?

I'm glad it's fixed :D

Please mark this thread as solved.

Kind regards

---

