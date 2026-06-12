---
title: "Firefox not working after rm -r 7rhwb7bi.default"
date: 2012-01-21
forum: General Help
---

### Post by goldie4042 on 2012-01-21
I was trying to delete firefox browsing history from the terminal. After reading a few threads on the subject I thought that I found a way to do this (rm -r 7rhwb7bi.default). I have now realized that I have deleted the entire directory instead of the files inside of the directory (I think). Now firefox will not start at all. I keep getting an error message that says "firefox is already running but is not responding". Does anyone know how to get that directory back or get firefox running again.

Also I tried to uninstall firefox and reinstall it with the commands below but it didnt work. Did I do this correctly?

apt-get remove firefox
apt-get install firefox

---

### Post by pqwoerituytrueiwoq on 2012-01-21
[FONT=Courier New]rm -rf ~/.mozilla[/FONT]
firefox will be reset to default

'I keep getting an error message that says "firefox is already running but is not responding".'
[FONT=Courier New]killall firefox[/FONT]
then launch as normal

if you ran [FONT=Courier New]rm -r 7rhwb7bi.default[/FONT] from your home folder you did nothing, a folder named [FONT=Courier New]7rhwb7bi.default[/FONT] could exist in  [FONT=Courier New]~/.mozilla/firefox[/FONT]

---

### Post by goldie4042 on 2012-01-21
Wow I have been googling this for about three days (because I still have chromium browser) to no avail. The first response on the matter on this forum gets it right. Thanks pqwoerituytrueiwoq. And to answer your question, yes I did change to the mozilla directory and deleted it from there. But after using your method the folder came back and firefox is now working again. Again thanks.

---

