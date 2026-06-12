---
title: "Force Restart on CTRL+ALT+DEL"
date: 2011-01-02
forum: General Help
---

### Post by yigosan on 2011-01-02
Hi,

I've hired a dedicated Ubuntu10.10 Server on a remote colocation. I needed a GUI to be able to hook into my KVM guests, so I installed xubuntu-desktop.

My dedicated server provider provides me very useful free service. I can request a CTRL+ALT+DEL to my server through their web based server control panel, and I can boot into a live image from their network. This is vital for me to be able fix back configuration problems.

However after I have installed xubuntu-desktop (XFCE I believe), the CTRL+ALT+DEL no longer reboots the machine.

I've been struggling with this simple issue for quite a few days, I simply can't get it to work.

I've tried setting it through XCFE 4 Settings Manager. It does not work. From my understanding any keyboard shortcuts defined here are specific to user, so I think they'll not work when the server is in login screen (no user logged in).

I've tried to put control-alt-delete.conf files in /etc/init and /etc/init/d , neither seems to trigger reboot. 

Any help will result in a big hug.

Greetz.

---

### Post by yigosan on 2011-01-02
Sorry i've made a typo mistake, the directories i've made the change are

/etc/event.d/control-alt-delete

/etc/control-alt-delete.conf

---

### Post by Dave_L on 2011-01-02
Is there a reason you can't connect to the server via SSH and issue a reboot command, e.g., "shutdown -r now"?

---

### Post by yigosan on 2011-01-02
Hi Dave, thanks for responding,

I will be changing my network settings to do bridged networking for my KVM guests. If i screw up my network settings (which i probably will at first try), I will lose all my ssh/network access to this server.

If that happens, i want to be able to issue a CTRL+ALT+DEL from my dedicated provider, boot from network, and fix back my configuration.

---

