---
title: "Can i get Virtual Box to read CD's"
date: 2010-01-05
forum: General Help
---

### Post by sh@ne on 2010-01-05
I plug a CD in of any kind, even my flash drive, but i cant get virtual box to read it, is there any way that i can do this, thanks.

---

### Post by SecretCode on 2010-01-05
For a CD you need to tell virtualbox to give the specific vm access to your physical CD drive - depending on your version of virtualbox, go to 'cd/dvd drives' or 'storage' in the settings, and pick your physical drive.

If you need more help, please say which version of vbox you're using.

USB devices incl flash drives are a bit more complicated. Firstly, you need the 'PUEL' licensed version, not the open-source version. Then you need to enable the USB controller in the vm settings. Then you need to insert the device and select it in the running vm from its runtime vbox menu.

---

### Post by sh@ne on 2010-01-05
I have the Sun Virtualbox 3.1.2. and i dont know where you mean by cd/dvd drives.

---

### Post by nitstorm on 2010-01-05
there is a tab called devices (drop-down menu, next to file and all that stuff, sorry i dunno the right word for it ) i think, if u go there, u can choose to mount media or something, been a while since i used the app, but i have used my usb drives and cd/dvd drives on it earlier, its totally there man! jus look around... :)

---

### Post by blur xc on 2010-01-05
Are you using the PUEL version or the OSE version (ose is in the repositories)...

And what do you mean by "plugging in a cd"?  If you are using usb devices, you need to run the PUEL version (PEUL?  I can't ever remember) from the Vbox website.  If you want to get fancy, they have their own ppa you can add to your sources.list and get updates that way.

I run Vista in VBox, and when Vista has focus, cd's autorun normally when I insert them.  It's never been an issue.  Several versions ago, I had lots of problems w/ USB drives, but they've been worked out for a while now.  Under the devices menu, expand out usb devices, and check mark the one you want passed through to your guest os.  Don't check the ones for your keyboard or mouse.  Leave those in control of your host, please...  When you check mark them, as I understand it, the device is unmounted from the host and mounted in the guest.  Unchecking it to the virtual machines is the same and removign it from the usb port. 

BM

---

### Post by sh@ne on 2010-01-05
ok, yes, i got it, thanks for all the help.

---

