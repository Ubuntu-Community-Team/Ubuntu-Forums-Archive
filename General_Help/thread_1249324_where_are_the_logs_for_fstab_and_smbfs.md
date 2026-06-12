---
title: "where are the logs for fstab and smbfs"
date: 2009-08-25
forum: General Help
---

### Post by silverrope on 2009-08-25
I am running xubuntu 9.04, but I believe this questions applies to all variants. I have installed smbfs in order to mount windows shared folders (started in /etc/modules). I have placed the following line in /etc/fstab:

```

//Server/SharedFolder    /media/fstabsmb    smbfs    iocharset=utf8,credentials=/home/username/.smbcredentials,uid=1000    0    0

```This worked nicely for two days (several reboots/logins), but today it did not work on reboot/login. However, I mounted the windows shares in the terminal using:

```

sudo mount -a

```So everything appears to be working. I would like to find out why my shares failed to mount on logging in today. Could someone point me to the appropriate logs (for fstab and smbfs for example) in order to debug this?

**Addition**:
I suspect the reason that my shares did not mount is the order of occurrence during the login process. If the smbfs mount occurred before the connection to the wireless lan then that would clearly fail. If someone could also show me how to tweak the login process (or point to some documentation), I would appreciate it.

---

### Post by silverrope on 2009-08-26
So anyone out there who can help a Unix newbie with this basic question, i.e., how do I analyse what is happening in the login process? What logs should I look at?

---

### Post by nikhilk on 2009-08-26
> **silverrope said:**
> So anyone out there who can help a Unix newbie with this basic question, i.e., how do I analyse what is happening in the login process? What logs should I look at?

You can find Samba logs under /var/log/samba.

---

### Post by danwood76 on 2009-08-26
The fstab will mount way before your wifi gets connected so this will be your problem.

If you add a line to the /etc/rc.local file containing the "mount -a" command it will be executed once you have logged on and may stand a better chance of mounting.

---

### Post by silverrope on 2009-08-26
> **nikhilk said:**
> You can find Samba logs under /var/log/samba.

Thank you, I will take a look.

> **danwood76 said:**
> The fstab will mount way before your wifi gets connected so this will be your problem.

If you add a line to the /etc/rc.local file containing the "mount -a" command it will be executed once you have logged on and may stand a better chance of mounting.

Thanks I will try this out, at least to assure that the shares are mounted. I also thought the mount occurs way too early, but now I wonder if the problem is due to something else. It sometimes works, sometimes doesn't so perhaps it is a race condition.

---

### Post by silverrope on 2009-08-26
> **danwood76 said:**
> If you add a line to the /etc/rc.local file containing the "mount -a" command it will be executed once you have logged on and may stand a better chance of mounting.

OK, I tried this, but it doesn't work (I think I need to use sudo). But how do I pass the superuser password to the rc file?

---

### Post by dardack on 2009-08-26
> **silverrope said:**
> OK, I tried this, but it doesn't work (I think I need to use sudo). But how do I pass the superuser password to the rc file?

sudo nano (or your favorite cmd line editing tool) /etc/rc.local

then before exit 0 line add "mount -a" as it's own line and without the ""

then in nano ctrl+o writes it and ctrl+x exits, reboot.

BTW to the poster about the rc.local thank you so much, couldn't remember what i had done on my last laptop to get this to work, cause on wired connections the connection occurs before fstab but on wifi after.

---

### Post by dardack on 2009-08-26
Ok so that didn't work 100%, what I added to my rc.local at the end before exit 0 (i have other stuff that runs I wanted this to run last):

```
while ! ifconfig wlan0 | grep "inet addr" ; do
    sleep 1
done
mount -a

```

What this does is every second checks to see if wlan0 has an ip address, until it gets one it keeps checking, now yes if your wifi never gets it will forever run, but for my little laptop at home no biggy and even when i travel almost 90% of the hotels have wifi anyways, then once it get's an address it mounts the fstab file.  so replace wlan0 with your wifi interface type.

---

### Post by silverrope on 2009-08-27
> **dardack said:**
> 
```
while ! ifconfig wlan0 | grep "inet addr" ; do
    sleep 1
done
mount -a

```


Thanks, I will try this, but isn't a "sudo mount -a" needed for the last line? I noticed that if I run "mount -a" in the terminal, then it tells me I don't have the privileges. Is rc.local run with root privileges?

---

### Post by jocko on 2009-08-27
> **silverrope said:**
> Thanks, I will try this, but isn't a "sudo mount -a" needed for the last line? I noticed that if I run "mount -a" in the terminal, then it tells me I don't have the privileges. Is rc.local run with root privileges?
rc.local is run during boot, before you log in your user, so yes, it's run as root.

It shouldn't be necessary to add anything to rc.local to be able to mount a network share on boot. My laptop's wireless connection doesn't connect until after I have logged in to gnome, but still it automounts my network shares (nfs, not samba) when the connection comes up.

---

### Post by silverrope on 2009-08-27
> **jocko said:**
> rc.local is run during boot, before you log in your user, so yes, it's run as root.

It shouldn't be necessary to add anything to rc.local to be able to mount a network share on boot. My laptop's wireless connection doesn't connect until after I have logged in to gnome, but still it automounts my network shares (nfs, not samba) when the connection comes up.

Hmm, if rc.local is run during boot and before login, then that would be too early. I have noticed that my shares do mount just after the wifi connection. But unfortunately this doesn't happen all the time (fails about 10-20% of the time). I am monitoring the samba logs to see if I can detect what is going wrong. But there doesn't seem to be any different logged items when the shares fail to mount. Are there logs for fstab mounts indicating success or failures?

Well, maybe this is something I have to live with if I stay with xubuntu.

---

### Post by dardack on 2009-08-27
Yes I've noticed since 9.04 that samba fails to mount my  network shares on every single login, but i'm using wicd instead  of network manager because wicd gives better reception/less loss packets for my particular wireless card.  So don't know if that's why.  Anyways, by adding the checking code in rc.local if my wifi has an ip address my network shares have always been mounted now.

---

### Post by silverrope on 2009-08-28
Thanks for the script! I had it running as a test for awhile and the shares mounted every time I rebooted. When I removed it, on the first reboot the shares didn't mount! I added some extra debugging conditions to try to figure out what is going wrong. The xubuntu gurus ought to fix this on the next release.

---

### Post by dardack on 2009-08-30
Your welcome.  My problem occurs on Ubuntu so not just xbuntu.  Also, i've had ubuntu start without the graphical so I could see what's happening, the mount for fstab occurs before the wifi get's an IP address.  Also, when the GUI start's if mount -a is in your rc.local file, it also occurs before the wifi get's an IP address (from the logs), so that's why this script is needed.  

In theory they should add a network drive mounting file (like fstab but for network drives) that occurs once an IP address is assigned.

---

### Post by gkinal on 2010-10-29
I know this is an old thread BUT this problem (network smbfs mounts do not show up automatically) still exists.

I have the same problem with 10.04 lucid and with WiCD as the network interface on a WIRED network. Apparently even a mount -a command in rc.local occurs too early. 

I am going to try the "keep waiting for a network connection" loop to see if that works; if so there would need to be a timeout in the event of no network within, say, 10 seconds.

It is a pity - my Mac does not behave this way - if I don't have my home NAS available, it just reports that it cannot mount the "folder."

And no Windoze computer (at least since maybe W98) behaves in such a non-intuitive, illogical way.

GVK

---

