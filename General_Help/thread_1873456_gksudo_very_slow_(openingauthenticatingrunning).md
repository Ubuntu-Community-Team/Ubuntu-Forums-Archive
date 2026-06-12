---
title: "gksudo very slow (opening/authenticating/running)"
date: 2011-11-01
forum: General Help
---

### Post by KnockKnockPenny on 2011-11-01
I am running Firefox and Thunderbird each as their own dedicated, limited user account (e.g. "firefox" run as the user "limited_browser") as a first phase of containing risky Internet-facing applications. I configured the limited user accounts and startup mechanism based on the guide I found at [http://calum.org/posts/running-firefox-as-another-user-using-sudo](http://calum.org/posts/running-firefox-as-another-user-using-sudo). Whilst this does work, invoking gksudo and subsequent application startup is infuriatingly slow. My startup script for each app is like the following:
```
xhost +SI:localuser:limited_browser
gksudo -u limited_browser -l firefox
xhost -SI:localuser:limited_browser

```When I run the script, it takes around 20-30 seconds for the gksudo dialog to appear. Once I've entered my password, it takes a further 10-20 seconds to start the application. As before, whilst it does run eventually, based on the hardware spec I'm very surprised at the delay in starting the app. Everything else on the system is extremely snappy and I've been pleased with performance. This system is a brand new workstation, running Xubuntu 11.10 (amd64) with all updates up to 31st October 2011. Hardware is an Phenom II 1100T 6-core CPU with 16GB RAM and a 120GB Vertex 3 SSD (ext4, full disk crypto with encrypted LVM setup through alternate installer). The slow gksudo opening happens with both Firefox and Thunderbird (each have their own script) - I've not yet tried with other apps such as an IRC client.

I'd appreciate some advice on what I might be doing wrong. I've already checked the hosts file is correct, routing seems OK, DNS configuration correct and there are no error messages in the logs indicating a relevant or deeper problem.

Many thanks in advance.

---

### Post by lovinglinux on 2011-11-02
I am a little bit tired right now digest all the information on that link, but the whole thing sounds like a very bad idea to me.

If you want to protect Firefox, so it can't modify you user files, learn how to use [AppArmor](http://ubuntuforums.org/showthread.php?t=1008906).

---

### Post by CharlesA on 2011-11-02
> **lovinglinux said:**
> 
If you want to protect Firefox, so it can't modify you user files, learn how to use [AppArmor](http://ubuntuforums.org/showthread.php?t=1008906).

+1. There really isn't a need to run firefox as a different user since by default you your user doesn't have root privileges unless you use sudo.

---

### Post by gsmanners on 2011-11-02
I think chroot might be a better solution, as well (if you don't like apparmor for some reason).

---

