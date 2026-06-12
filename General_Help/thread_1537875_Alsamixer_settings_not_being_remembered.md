---
title: "Alsamixer settings not being remembered"
date: 2010-07-24
forum: General Help
---

### Post by cozski on 2010-07-24
Hello

I use a Toshiba L300 Laptop and an Acer Aspire Netbook. After recent upgrades to Lucid I have to use the terminal to access alsamixer and turn up the sound on both when I boot-up. I have to do this every-time I boot up as it doesn't remember the change. Any thoughts/suggestions?

Thanks

---

### Post by viralmeme on 2010-07-24
$sudo alsactl store

---

### Post by cozski on 2010-07-25
Thanks.... but now when I run the alsamixer command in terminal it says 'no such file or directory' and the $sudo alsactl store command gets 'save_state:1502: No soundcards found...'

Any ideas?

---

### Post by viralmeme on 2010-07-26
Click here .. | [save_state:1502]("http://webcache.googleusercontent.com/search?q=cache:ek5yQnZ4OpEJ:ohioloco.ubuntuforums.org/showthread.php%3Fp%3D8367621+save_state:1502+alsamixer&cd=3&hl=en&ct=clnk&gl=uk") |

---

### Post by cozski on 2010-07-26
```

```Thanks... well the suggestion in the link you sign posted me to worked; unistalled and re-installed alsa and working fine. But the command to store the settings is giving me this 

[PHP]cozski@cozski-laptop:~$ $sudo alsactl store
alsactl: save_state:1530: Cannot open /var/lib/alsa/asound.state for writing: Permission denied
[/PHP]

---

### Post by lidex on 2010-07-26
More options:
First try these terminal commands:
```
sudo mv /etc/rc0.d/K50alsa-utils /etc/rc0.d/S50alsa-utils
sudo mv /etc/rc6.d/K50alsa-utils /etc/rc6.d/S50alsa-utils

```
Reboot

No help?
Open this file for editing:
```
gksudo gedit /etc/pulse/default.pa
```
Scroll down to this line:
```
load-module module-device-restore
```
Comment it out so it looks like this:
```
#load-module module-device-restore
```
Save. Close. Logout/in.

No help? Comment out line 372 in /etc/init.d/alsa-utils
Should look like this when you're done:
```
# mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=1
```

---

### Post by cozski on 2010-08-15
Thanks lidex, that resolved it. Just out if interest the other lines below do not have the # symbol... should they? I tend to have ongoing problems with my built-in mic when using skype... could this be related in any way?

### Automatically restore the volume of streams and devices
#load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore

Thanks again :)

---

### Post by lidex on 2010-08-15
> **cozski said:**
> Thanks lidex, that resolved it. Just out if interest the other lines below do not have the # symbol... should they? I tend to have ongoing problems with my built-in mic when using skype... could this be related in any way?

### Automatically restore the volume of streams and devices
#load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore

Thanks again :)

That's all as it should be. As for skype, make sure the option to allow skype to control mixer settings (paraphrasing here) is disabled.
Please mark the thread solved using 'Thread Tools' up top.

---

