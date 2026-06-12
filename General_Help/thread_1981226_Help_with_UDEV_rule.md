---
title: "Help with UDEV rule"
date: 2012-05-16
forum: General Help
---

### Post by Odvesims on 2012-05-16
Hey There Everyone!!

Well, i recently implemented PAMUsb to prevent access to a Ubuntu Server machine without a USB key which stores the password. Now, i want it to lock all the VTYs whenever the USB is unplugged. I have done some research and i figured that what i need is a UDEV rule that triggers a script whenever the device is unplugged.. However i have been unable to do such thing.

Can anyone help me out? Would be much appreciated!!

Thanks!! :D

P.S: I know that PAMUsb has something that could work similar, however it only does it for GUI machines since what the sintax does is bringing up the "lock/screensaver" screen up and, since terminals dont have such thing, it doesnt work there.

---

### Post by matt_symes on 2012-05-17
Hi

> **Odvesims said:**
> Hey There Everyone!!

Well, i recently implemented PAMUsb to prevent access to a Ubuntu Server machine without a USB key which stores the password. Now, i want it to lock all the VTYs whenever the USB is unplugged. I have done some research and i figured that what i need is a UDEV rule that triggers a script whenever the device is unplugged.. However i have been unable to do such thing.

Can anyone help me out? Would be much appreciated!!

Thanks!! :D

P.S: I know that PAMUsb has something that could work similar, however it only does it for GUI machines since what the sintax does is bringing up the "lock/screensaver" screen up and, since terminals dont have such thing, it doesnt work there.

First time i've seen pam_usb before.

From the web site though here.

[https://github.com/aluzzardi/pam_usb/wiki/Getting-Started](https://github.com/aluzzardi/pam_usb/wiki/Getting-Started)

> The pam_usb agent (pamusb-agent) allows you to automatically execute commands upon locking and unlocking events. Those events are generated when you insert or remove your authentication device. To configure the commands, you have to edit pam_usb's configuration file (/etc/pamusb.conf) and add agent entries into your user section.

For instance, you could automatically start your screensaver as soon as you remove the device, and deactivate it when you plug the device back.

GNOME (gnome-screensaver):

<user id="scox">
  <device>MyDevice</device>
  <agent event="lock">gnome-screensaver-command --lock</agent>
  <agent event="unlock">gnome-screensaver-command --deactivate</agent>
</user>


Will this allow you to run the script you need ?

Kind regards

---

### Post by Odvesims on 2012-05-18
> **matt_symes said:**
> Hi



First time i've seen pam_usb before.

From the web site though here.

[https://github.com/aluzzardi/pam_usb/wiki/Getting-Started](https://github.com/aluzzardi/pam_usb/wiki/Getting-Started)



Will this allow you to run the script you need ?

Kind regards

Hey Matt!! Thanks for replying! Thats what i stated on the "P.S" section of my message. The "agent" thing brings up the screensaver for either GNome/KDE based enviroments. Since a terminal doesnt have a GUI, it means no screensaver screen can be brought up. I have tried tweeking the "agent" commands, but no luck so far.

Any other suggestions? :|

---

### Post by Odvesims on 2012-05-18
Ok, so apparently the "GNome-Screensaver" is a downloadable package! Im getting it and will try with the base agent thing they have at the PamUsb config. We'll let y'all know once i test it!

---

### Post by Odvesims on 2012-05-18
Nothing, it didnt work :/

---

### Post by matt_symes on 2012-05-18
Hi

I was thinking more along the lines of..

```
<user id="scox">
<device>MyDevice</device>
<agent event="lock">**/path/to/lock_script.sh**</agent>
<agent event="unlock">**/path/to/unlock_script.sh**</agent>
</user>
```

where /path/to/lock_script.sh would lock the vttys and /path/to/unlock_script.sh would unlock the vttys.

I would image that the command inside <agent event...>...</agent> just gets called by the pam_usb module.

You can test whether this is so; edit the xml as so

```
<user id="scox">
<device>MyDevice</device>
<agent event="lock">**touch /home/your_user_name/lock**</agent>
<agent event="unlock">**touch /home/your_user_name/unlock**</agent>
</user>
```

Obviously change your_user_name to *cough* your username :D Then reboot to ensure the configuration changes are picked up by pam.

If it creates files called lock and unlock in your home folder when you lock and unlock the machine, i would expect you could put a path to an executable script and run that instead.

Then maybe the script could lock the ttys and/or run the screensaver.

These are just musing mind but i would check to see if that is how pam_usb behaves.

If your server does not have X installed then don't bother with Gnome-screen saver. I.E is it a command line server only ?

Kind regards

---

### Post by Odvesims on 2012-05-18
Thanks for the reply Matt! 

Well, i have done that aswell, changing the command between the <agent> tags to call my script but with no luck. I have even tried to run the command itself between the tags, but that has also proven to not work. I'll keep trying though, but i just dont know what else i could do. Thats why i've been interested in seeing if i can set a udev rule that would trigger the locking event when the usb is unplugged.. No luck there either :/

I do sincerely appreciate your interest in helping me Matt! :D

---

### Post by Odvesims on 2012-05-18
Oh yeah, its a command-line only server.

---

### Post by matt_symes on 2012-05-18
Hi

I'm going to set it up myself on a spare install on a spare partition. I will tell you how i get on.

Kind regards

---

### Post by matt_symes on 2012-05-19
Hi

I will set this up. I have been a bit busy today.

Kind regards

---

