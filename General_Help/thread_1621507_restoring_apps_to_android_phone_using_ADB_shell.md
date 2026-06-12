---
title: "restoring apps to android phone using ADB shell"
date: 2010-11-14
forum: General Help
---

### Post by neuro99 on 2010-11-14
Hi,

I'm using ubuntu netbook remix, and am fairly new to it although I am eager to learn.

I ran into problems restoring apps on my android HTC desire phone using TitaniumBackup. 

All I have is the backup directory on my SD card which consists of (for each app) a ".properties", ".tar.gz" and some also have a ".gz" file. 

so decided to do it manually by following these instructions I found after much google searching:

adb shell
# cd /
# cp /sdcard/TitaniumBackup/*.gz /data/apps
# gzip -d *.gz
# rm *.gz
# cd /
# tar -zxvf /sdcard/TitaniumBackup/*.tar.gz

however I have run into a number of problems. 
I managed to copy all .gz files to /data/app
I initially had problems with the next step, but found it worked if I did cd /data/app first.
rm *.gz was OK

the last step is more problematic, I kept getting the error:
"not found in archive"

but appeared to get around it by using:
echo /sdcard/TitaniumBackup/*.tar.gz | xargs -n 1 tar -zxvf
instead (another command found from google)

I decided to post on here as the problems I've encountered appear to be associated with the use of linux commands, but any help from someone who is familiar with android would be much appreciated.

---

