---
title: "Nothing in sudo gedit /etc/default/grub"
date: 2011-10-18
forum: General Help
---

### Post by atentik on 2011-10-18
I am having some reboot problem. Essentially, the computer gets stack at 
*Checking battery status, after some research, I found out [here]("http://ubuntuforums.org/showthread.php?t=1859203") and [here]("http://ubuntuforums.org/showthread.php?t=1745837") that I should edit a grub file but when I tried to edit it,there is no grub file in /etc/default. Can someone help me get this working? 

Thanks.

---

### Post by haqking on 2011-10-18
> **atentik said:**
> I am having some reboot problem. Essentially, the computer gets stack at 
*Checking battery status, after some research, I found out [here]("http://ubuntuforums.org/showthread.php?t=1859203") and [here]("http://ubuntuforums.org/showthread.php?t=1745837") that I should edit a grub file but when I tried to edit it,there is no grub file in /etc/default. Can someone help me get this working? 

Thanks.

what version of Ubuntu are you using, i know it says 11.04 in your profile but that is rearely accurate ?

can you show us the contents of default

```
cd /etc/default
```

```
ls
```

then post output

also dont use sudo with gedit.

```
gksudo gedt /etc/default/grub
```

---

### Post by atentik on 2011-10-18
I just upgraded to 11.10. I tried the command you suggested but it won't work either. By the way, when I reboot the system, I only get blank screen and it gets stack at *Checking battery status ........Ok
So I typed [HTML]sudo gdm[/HTML] after pressing Ctrl+Alt+F2 and login in. Could that be the reason why I am not able to edit the grub file?

Btw: here is the output from my /etc/default

[PHP]acpid            console-setup      kernel-helper-rc  rcS
acpi-support     cron               kerneloops        rsync
alsa             cryptdisks         kexec             rsyslog
apmd             cups               keyboard          saned
apport           dbus               klogd             speech-dispatcher
avahi-daemon     devpts             locale            ssh
bind9            dictd              mcelog            syslogd
bind9.dpkg-dist  google-chrome      nss               ufw
bluetooth        google-talkplugin  ntpdate           useradd
bootlogd         halt               prelink           winbind
brltty           irqbalance         pulseaudio
cacerts          jetty              pyro-nsd
[/PHP]

---

### Post by atentik on 2011-10-18
Can someone help? Please.

---

### Post by atentik on 2011-10-18
Does every that upgraded to ubuntu 11.10 don't have grub in their /etc/default folder?

---

### Post by haqking on 2011-10-18
> **atentik said:**
> Does every that upgraded to ubuntu 11.10 don't have grub in their /etc/default folder?

yes it should be in /etc/default

You might want to look at repairing it ?

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by atentik on 2011-10-18
> **haqking said:**
> yes it should be in /etc/default

You might want to look at repairing it ?

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Thanks for the suggestion. The procedure is for grub2 but from what I have been reading, the ubuntu 11.10 uses grub3. Does it matter? Also, do you know how the file in grub got removed? Also, can I just file a grub text file somewhere from online and place it in the folder?

Thanks

---

### Post by haqking on 2011-10-18
> **atentik said:**
> Thanks for the suggestion. The procedure is for grub2 but from what I have been reading, the ubuntu 11.10 uses grub3. Does it matter? Also, do you know how the file in grub got removed? Also, can I just file a grub text file somewhere from online and place it in the folder?

Thanks

no it uses version 1.99 which is grub 2

you can use

```
grub-install -v
```

to see its version

---

### Post by atentik on 2011-10-18
Alright, I did that and it says (GNU GRUB 0.97). Seems like mine is wayyy behind. Any idea why?

---

### Post by haqking on 2011-10-18
> **atentik said:**
> Alright, I did that and it says (GNU GRUB 0.97). Seems like mine is wayyy behind. Any idea why?

That is GRUB legacy as it is known.

And you have 11.10 ?

Have you been upgrading from way older versions or something?

anyways the information in that link should sort you out by updating your grub which should also give you the grub file in /etc/default

A expect you have been upgrading and not doing a fresh install perhaps

---

### Post by mcduck on 2011-10-18
> **atentik said:**
> Alright, I did that and it says (GNU GRUB 0.97). Seems like mine is wayyy behind. Any idea why?

That depends on what was the version of ubuntu you originally installed. Upgrades will not change Grub version, so if the original Ubuntu install you made was one that still used Grub0.97 instead of Grub2, then no matter what upgrades you've made you'll still be using Grub0.97.

You can upgrade to Grub2 manually, if you want to, but meanwhile you can simply do the changes you were trying to do in the old Grub's config file, */boot/grub/menu.lst*. (whatever changes you make, remember to also do them in the default options section of the menu.lst file. Otherwise the next kernel update will erase them. And unlike with Grub2, you don't need to run "sudo upate-grub afterwards.)

---

### Post by atentik on 2011-10-18
> **mcduck said:**
> That depends on what was the version of ubuntu you originally installed. Upgrades will not change Grub version, so if the original Ubuntu install you made was one that still used Grub0.97 instead of Grub2, then no matter what upgrades you've made you'll still be using Grub0.97.

You can upgrade to Grub2 manually, if you want to, but meanwhile you can simply do the changes you were trying to do in the old Grub's config file, */boot/grub/menu.lst*. _**(whatever changes you make, remember to also do them in the default options section of the menu.lst file. Otherwise the next kernel update will erase them.**_ And unlike with Grub2, you don't need to run "sudo upate-grub afterwards.)

Thanks. What do you mean by the "default options section"? Is there a another list somewhere besides the one in /boot/grub/menu.lst?

---

### Post by mcduck on 2011-10-19
> **atentik said:**
> Thanks. What do you mean by the "default options section"? Is there a another list somewhere besides the one in /boot/grub/menu.lst?

In the same menu.lst file there's a section marked as "default options". You should see it quite easily if you read through the comments in the file. (Which is a good idea anyway, as the comments pretty much explain what every options does, an what you should edit & how).

The default options is right above the "debian automagick kernels list"-section of the file. (another important section in menu.lst, everything inside this section is automatically generated based on the default options and the kernel version you have available, so you should keep everything else, like Windows boot entries, outside of this area)

---

