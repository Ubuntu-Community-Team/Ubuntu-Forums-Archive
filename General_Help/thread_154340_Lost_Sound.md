---
title: "Lost Sound"
date: 2006-04-02
forum: General Help
---

### Post by ltr20 on 2006-04-02
Hello,

I've been using ubuntu for a few days and I lost sound today. I get no sound in XMMS/XINE etc. I know it's not a problem with my soundcard because in windows i can listen to music and watch movies fine.

---

### Post by Cesium on 2006-04-02
[QUOTE=ltr20]Hello,

I've been using ubuntu for a few days and I lost sound today. I get no sound in XMMS/XINE etc. I know it's not a problem with my soundcard because in windows i can listen to music and watch movies fine.[/QUOTE]
I just lost my sound too and I've been using Ubuntu for a while.

---

### Post by Qrk on 2006-04-02
For Xmms, this might work...

Right click on Xmms and select Options->Preferences->I/O Plugins->Output Plugins

Change it from OSS to ALSA

Another problem might be mplayer ... which sometimes doesn't exit correctly. Go to System->Administration->System Monitor and exit mplayer. (other programs that might still be using the sound card, exit them too. Mplayer is usually the culprit)

---

### Post by ltr20 on 2006-04-03
XMMS is using ALSA and i don't have MPLAYER installed. When ubuntu starts up i don't even hear the welcome sounds.

---

### Post by louis_nichols on 2006-04-09
I had a similar problem once.

What you should check is: go to system/administration/users and groups. Select your user and click properties. Go to user privileges and see that "use audio devices" is checked. At one point, for myself, sound had dissapeared completely too. For some reason, that option was unchecked. But as soon as I checked it, sound was fine again.

Of course, see that all apps use alsa and it is selected as source and sink under system/preferences/multimedia systems selector and used by all apps.

---

