---
title: "usb devices with windows xp on vmware server"
date: 2006-06-22
forum: General Help
---

### Post by jnev on 2006-06-22
hey guys, I don't know if this is the correct place for this as it isn't related to ubuntu persay, but I did install winxp on vmware based on a tutorial from this site :mrgreen: 

anyways, I have a pda running windows mobile 5.0 (dell axim x51v) that I would like to be able to sync with windows in vmware. now, I use to have vmware player installed and vmware was able to pass the usb connection through to windows so I could sync it. however, I just installed vmware server and it can't do that, so I've been having to boot into windows to sync it, which is very annoying. anyone know how to configure vmware server to be able to sync it?

thanks

EDIT
forgot to mention that the windows image is the same, so the problem isn't with the windows image itself, but with vmware. I assume that there has to be a way to do what I want.. vmware server is a higher-end product, there would be a serious problem if it didn't have some of the functionality of vmware player.

---

### Post by AndyCooll on 2006-06-22
Hmmm ...I've also started using server with a WinXP image. However just tried my USB key and that was found fine, and the USB controller has kicked into action. The real test would probably be when I try connecting the wife's mp3 player (which isn't here at the mo).

I installed the USB key after I booted up the image (since I believe such devices can only display on one of the OS's at a time, i.e. either Linux or XP).

Also have you also installed VMware tools?

:cool:

---

### Post by scxtt on 2006-06-22
you have to enable the device (assuming you've added USB support to your particular VM's config - which is easy to do) ... so click on "VM" in the menu bar, navigate to "Removable Devices" (i think) and find your USB device ... XP should notify you that it's found a new USB device immediately ... i just rebuilt the DB for my iRiver H300 via XP in VMware server ...

---

### Post by jnev on 2006-06-22
usb drives work fine.. it's my pda that doesn't work. and I already have attempted enabling it in removable drives. the problem is that it's not even listed there. and yes, I have installed vmware tools.

---

### Post by jnev on 2006-06-23
bump... anyone?

---

### Post by Sye d'Burns on 2006-06-23
I've managed to hotsync my tapwave zodiac using a win2k vmware install. 

What I did was:

```
-Start the win2k machine and wait for all services to load
-Click over to a console in ubuntu and type 
' sudo rmmod visor '
' enter password '

-Then I right-clicked in the VM to make sure that it was active.
-Click the hotsync button on your cradle.
``` 

This works for me but you have to be sure that you click into the VM the very next thing after removing the visor mod otherwise it will reload before you've started the hotsync.

---

### Post by Sye d'Burns on 2006-06-24
I was just wondering if this worked for you. I'm not quite certain that it will since you didn't mention a vmware visor error specifically. I'm also not too sure about the differences between windows mobile devices and palmOS devices when it comes to hotsyncing.

---

