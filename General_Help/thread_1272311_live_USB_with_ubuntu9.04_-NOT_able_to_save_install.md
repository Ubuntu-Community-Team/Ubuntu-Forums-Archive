---
title: "live USB with ubuntu9.04 -NOT able to save installations settings all"
date: 2009-09-22
forum: General Help
---

### Post by harikatt on 2009-09-22
hi,

can any body help me,, i successfully able run live usb ubuntu 9.04 ,, but user or settings or installtion packages are not storing,, how to activate write permissions on usb live .. for this..

---

### Post by glickboy on 2009-09-22
Clarify what you mean by 'not storing' whats not saving? what are you trying to write to?  You can't write to the usb stick containing the live image.  Any software that you install or configuration files that you modify are not saved.  Only copies of them are saved in RAM for the duration of your Ubuntu Live session.  If you want to save something, you will have to manually mount a disk (internal, external, another usb stick, etc) and save it on there.

---

### Post by P4man on 2009-09-22
You need to either install ubuntu or make a so called "persistent" live stick. Google on it for a gazillion how-to's. I think you almost must create a user (other than the default "ubuntu" user, since that user account is recreated from scratch each boot).

---

### Post by harikatt on 2009-09-22
i am trying to make new wireless,, wired connection dialup connections,, and new user groups while booting from live usb stick,, but everything is wiping out,, with an restart of live usb,, how can all my changes in the customization of settings of ubuntu save,,,

---

### Post by harikatt on 2009-09-22
what ever configuration settings i change or customize,, everything going out,, not saving.. 


(may be this is what i want   "persistent" live stick)

---

### Post by harikatt on 2009-09-22
with more information,, now.

i installed,, [http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/)

in that way, persistent install,, but still why i couldnt have my own user groups and dsl dialup i created,, couldnt be saved.. why??? even my user names newly created.. couldnt be saved why,, i am using transcent 1gb pendrive

---

### Post by P4man on 2009-09-22
> **harikatt said:**
> with more information,, now.

i installed,, [http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/)

in that way, persistent install,, but still why i couldnt have my own user groups and dsl dialup i created,, couldnt be saved.. why??? even my user names newly created.. couldnt be saved why,,** i am using transcent 1gb pendrive**

from your own link: Minimum Flash Drive Capacity: 2GB

That how to uses 1GB (or more) persistence files. The live cd needs another 650Mb. You could theoretically make a live stick with a ~350Mb persistence file to save your settings, but it will be full in a blink of an eye. considering how cheap flash drives are, Id say go buy a bigger one.

---

### Post by harikatt on 2009-09-22
thanks p4man.. i will try on 2gb

---

### Post by harikatt on 2009-09-24
thanks to everyone,, my question have been solved,,

its the only matter of 2gb and above pendrive, with an installation of persistence installation

---

