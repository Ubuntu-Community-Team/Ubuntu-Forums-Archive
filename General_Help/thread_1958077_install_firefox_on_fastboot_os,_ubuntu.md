---
title: "install firefox on fastboot os, ubuntu?"
date: 2012-04-13
forum: General Help
---

### Post by ayoldt on 2012-04-13
First of all; i'm a noob in linux. 

I've a computer with a preinstalled version of linux fastboot(medion). the only /default browser is chromium. Thas oke, but icant see all content on the web like video's. Hence i wanted to install firefox, but i dont know how. i tried the unbuntu firefox howto( [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)). But i cant open de file like it is supposed to, i'm even not sure the system is running with ubuntu. I cant find the version of linux it is working on. I think its ubuntu, but i'm not sure.the file browser is: Nautilus 2.32.2.1. and in the control panel it says: system 2.0.87744.

A long explenation, but my question is does somebody know how i can find what os im using and how i can install firefox.

thanks

---

### Post by webtechquery on 2012-04-14
hi

may be you should try ubuntu installation of firefox as mentioned in the following post..

[http://www.webtechquery.com/index.php/2011/07/firefox-5-ubuntu-firefox-5-linux/](http://www.webtechquery.com/index.php/2011/07/firefox-5-ubuntu-firefox-5-linux/)

as it is ff 5 written over there, but u will hopefully find the latest version while clicking on the link of ff5 download.

let me know if it works.

[http://www.webtechquery.com/](http://www.webtechquery.com/)

---

### Post by lovinglinux on 2012-04-14
Please attach the firefox-report.txt file generated in your desktop after running the commands below on a terminal. To do that, copy each line, paste on a terminal and click Enter:

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
```

---

