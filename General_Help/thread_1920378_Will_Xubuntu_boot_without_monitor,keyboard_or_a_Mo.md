---
title: "Will Xubuntu boot without monitor,keyboard or a Mouse ?"
date: 2012-02-04
forum: General Help
---

### Post by BADGER.BRAD on 2012-02-04
Sounds like a strange question I know but I'll explain myself, earlier today I set up an old PC to run Boinc on Xubuntu with the intention of leaving it running in my workshop. I got the PC to boot and auto connect to my Wifi router but as I only have one monitor, keyboard and mouse when I set it up in the workshop I have no idea if it is running. Will it boot without these or will the lack of hardware Hang the machine ? I cannot see it when I do a WIFI network search from my main PC ( also running Xubuntu) but am not sure if this search would show that machine as it's not actually a network just another PC connected to my Router should I be able to see it ?

Many thanks all for your help

Brad

---

### Post by kherring7383 on 2012-02-04
Let me first address configuring the computer's BIOS setup regarding no keyboard. Make sure the BIOS is configured not to halt on errors since there will not be a keyboard and if the BIOS setting is not changed, it will stop booting until it gets a response from a keyboard to continue the POST.

Secondly, you'll  need to set Xubuntu for no log in password (auto login)  since there's no keyboard to enter one. Lastly test the boot up with an attached display.

Technically I never actually tried this with Xubuntu but I know it works with Windows. 

Good Luck.

---

### Post by uRock on 2012-02-04
> **kherring7383 said:**
> Let me first address configuring the computer's BIOS setup regarding no keyboard. Make sure the BIOS is configured not to halt on errors since there will not be a keyboard and if the BIOS setting is not changed, it will stop booting until it gets a response from a keyboard to continue the POST.

+1 My system refused to boot without making those changes. If you are setting the system up with shared folders and such, then they will be available as soon as boot is complete.

---

### Post by sudodus on 2012-02-04
Yes, you need to set it to run without a keyboard. And it needs no mouse and no screen (except to check that it is running). If you have sshd running, you can check with ssh via the network that it is running. Well, you can log in and do whatever you wish.

You need not log in for certain things to run, for example you need not log in to a server, it can still perform many tasks. But autologin make things easier to manage :-)

---

### Post by BADGER.BRAD on 2012-02-05
Many thanks everyone, I will need to get the PC back up here in order to set it to boot without a keyboard although I do have a keyboard that I could attach, In the end I wish to be able to use the PC in the workshop for Internet radio and a few other uses once I obtain a monitor from Freecycle.

Many thanks all

Brad

---

### Post by ph4nt0m117 on 2012-02-10
Question to your question:  Why not get a KVM since you only have one keyboard, mouse, and monitor.

---

### Post by BADGER.BRAD on 2012-02-11
Whats KVM

---

### Post by sudodus on 2012-02-11
[[COLOR="Red"]_http://en.wikipedia.org/wiki/KVM_switch_[/COLOR]]("http://en.wikipedia.org/wiki/KVM_switch")

but I'm not sure you want that, because the cables are only approx. 2 m. Login via network might be better in your case.

---

