---
title: "Transmission issue"
date: 2010-05-10
forum: General Help
---

### Post by sarin_cv on 2010-05-10
Hi all... I usually set temperory speed limits in transmission from 2-8 AM since I am having free downloads then... during other times i set upload and download speed as '0'. But even if I set it as zero some kind of data transmission happens and my internet providers records says around 15 MB of upload and download each...this is issue is only with transmission.. i use bittorrent also with wine ... it does not have this kind of issue... I have observed that many other people are also having the same issue... but no one is really bothered of it because the upload/download is low... plz help...

---

### Post by Vaphell on 2010-05-10
maybe transmission doesn't transfer any content data when set to 0 but still communicates with the other peers to exchange info and update their status? Such overhead is definitely non-zero and i can see it adding up to 15 megabytes. Disabling all torrents or killing it entirely would be the way to go, but i assume you use some automatic built-in throttling?

---

### Post by sarin_cv on 2010-05-10
My internet connection requires a login and I can't schedule it... so usually I login and start transmission before going to bed... The only way I can schedule downloads in transmission is by setting temperory speed limits... rest of the times the torrents will be in active state... is there anyway to disable or pause the downloads and start it only during the scheduled times?? What transmission is missing is a scheduler like uTorrent or bitTorrent for Windows...

---

### Post by sarin_cv on 2010-05-10
any comments??

---

### Post by nitstorm on 2010-05-10
Have you tried Vuze? I think it has a scheduler. Also  can transmission just resume the downloads it was last downloading wen closed? If it has that feature then try looking into putting it into the crontab. But give vuze a try first, it might have what you are looking for. Not sure if it does, but just a maybe..

---

### Post by sarin_cv on 2010-05-10
scheduling as cron job seems to be a solution..let me try this... I had tried Vuze before when I was using opensuse. It was giving me lower download speeds when compared to others... Transmission is the perfect one but this has been the only issue I've faced...

---

### Post by nitstorm on 2010-05-10
then cron job it is :D

---

### Post by sarin_cv on 2010-05-10
but cronjob didn't work... :( I have created a shell script and executed this as cronjob... in the shell script there are only two lines...first for setting the env, and then /usr/bin/transmission...but iti didn't work.... can somebody post the code if someonehas done it??

---

### Post by teeedubb on 2010-05-10
utorrent under wine?

---

### Post by sarin_cv on 2010-05-11
not uTorrent... bitTorrent.. why?

---

### Post by teeedubb on 2010-05-11
utorrent is the best torrent app out there, but its windows only. I run utorrent on ubuntu 10.04 and have no issues, it has a built in scheduler so it will do what you need.

---

### Post by sarin_cv on 2010-05-11
ok...bittorrent and utorrent are having similar interfaces... i was using bittorrent in Jaunty.. but after installing Lucid, I am getting very low download speeds(less than 10 KBps)...may be due to some firewall settings... no idea....thats y i returned to transmission....

---

### Post by sarin_cv on 2010-05-11
solved the issue with cron....worked this way

00 02 * * * export DISPLAY=:0 && /usr/bin/transmission

---

### Post by sarin_cv on 2010-05-11
but why this one does not work?

00 02 * * * /usr/bin/transmission

---

### Post by nitstorm on 2010-05-11
Because you need a display because transmission is a GUI and not a CLI program.

---

