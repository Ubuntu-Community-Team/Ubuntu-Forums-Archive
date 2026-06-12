---
title: "enable sound in ubuntu server 10.04"
date: 2010-06-26
forum: General Help
---

### Post by kaq on 2010-06-26
Hi'

I am an almost noob to linux and have encountered what might be a minor problem I need to activate the sound in a server install and I have no X or any clue what I need to do...

Thanks in advance
Kasper

---

### Post by kaq on 2010-06-28
isn't there anybody who can help?

---

### Post by Helios747 on 2010-06-28
```
sudo apt-get install alsa-utils
```

Let apt-get install that and it's dependencies.

then run

```
alsamixer
```

to set the channel levels you want.

after that, run

```
sudo alsactl store
```

to save as default

Finally, run

```
sudo nano /etc/rc.local
```

add

```
alsactl restore
```

In it's own line ABOVE the exit 0 statement. That is a startup script so sound is restored on startup.

save, and close nano.

---

### Post by kaq on 2010-06-28
thanks

when I run alsamixer I get this error:

cannot open mixer no such file or directory.

I have added snd-via82xx to /etc/modules.

btw I have tried this link with no success

[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by Jay Hawk on 2010-08-28
If You dont actually log in on the server - but are using a ssh connection to control it, You need to let your user have membership of the audio group.

If You do this on the server

[B]sudo usermod -a -G audio yourUsername

[/B]You can control alsa sound remotely via ssh.

---

