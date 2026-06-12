---
title: "Transfer files remotely from vista to Ubuntu"
date: 2009-10-15
forum: General Help
---

### Post by Neezer on 2009-10-15
I'm trying to send some files, or possibly an entire folder to my ubuntu box remotely from a vista laptop.

I'm away from home right now and I'd like to get this set up via ssh. I have ssh up and running and working great. Eventually I want to turn the ubuntu machine into a media server on the LAN, and a way for me to access files and possibly music anywhere I have an internet connection.

I have looked into samba and have installed it on my ubuntu box, but I am at a loss for what to do next.

---

### Post by bodhi.zazen on 2009-10-15
If you have ssh installed, use scp or winscp

[http://winscp.net/eng/docs/screenshots](http://winscp.net/eng/docs/screenshots)

---

### Post by jbrown96 on 2009-10-15
Here's some documentation on what to do. [https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba") You won't need to do most of the stuff, but there are parts that will tell you exactly what to do. If you still have questions post back here. Don't forget to include what you have done.

---

### Post by bodhi.zazen on 2009-10-15
> **jbrown96 said:**
> Here's some documentation on what to do. [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba) You won't need to do most of the stuff, but there are parts that will tell you exactly what to do. If you still have questions post back here. Don't forget to include what you have done.

I would NOT advise Samba over the internet. Samba is fine over the LAN.

---

### Post by Neezer on 2009-10-15
> **bodhi.zazen said:**
> I would NOT advise Samba over the internet. Samba is fine over the LAN.

what would you advise over the internet? I do have ssh up and running with putty on the laptop. I'll be doing all of this work remotely from the laptop at this time. when I'm home in 3 weeks or so I'll be able to use the gui on the ubuntu box.

---

### Post by bodhi.zazen on 2009-10-16
> **Neezer said:**
> what would you advise over the internet? I do have ssh up and running with putty on the laptop. I'll be doing all of this work remotely from the laptop at this time. when I'm home in 3 weeks or so I'll be able to use the gui on the ubuntu box.

Use ssh

When you transfer a file with ssh it is called "scp"

You mount a file system with sshfs

[http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html#more-44](http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html#more-44)

If you are on a Windows system you use winscp, which is a gui (graphical) application and connects over ssh.

[http://winscp.net/eng/docs/screenshots](http://winscp.net/eng/docs/screenshots)

[img]http://winscp.net/eng/data/media/screenshots/commander.png[/img]

Be sure to secure your ssh server (I suggest you use keys).

[SSH/OpenSSH/Keys - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")

---

