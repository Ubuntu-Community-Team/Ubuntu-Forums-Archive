---
title: "Having a minor (hopefully) issue with sound, help!"
date: 2009-08-30
forum: General Help
---

### Post by georgeeboy on 2009-08-30
Well first of all this is my first post in these forums, so whats up :)

Anyways, im having an issue with my sound, it works when turning on the computer at the login screen but i cant get any sound on firefox or through amarok.  It was working fine before, im thinking i installed something and it caused it not to work or it is due to a usb stick in which i played music from, which worked fine....but when i turned off and on my laptop it stopped and hasnt worked since.

I have a dell mini 9

can anyone help??

---

### Post by uylug on 2009-08-30
Ok, let's start by making sure your settings are not messed up.

Create a new user and set a password for it. This will let us test the computer with the default user settings without affecting **your** settings.

Add the new user
```
sudo useradd testuser
```

Set a password for it
```
sudo passwd testuser
```

Login as the new user and check if it works!

Good luck!

---

### Post by georgeeboy on 2009-08-30
Created a new user and set a pword using those 2 commands and restarted but still no sound.

my volume is all the way up on taskbar as well as on the mini 9's keyboard, HDA intel alsa is currently the device and that hasnt been changed

---

### Post by uylug on 2009-08-30
Did you login as the new user?

---

### Post by georgeeboy on 2009-08-30
yep, logged in as a new user but to no avail :(

---

