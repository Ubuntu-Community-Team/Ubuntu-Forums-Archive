---
title: "at-spi-registryd-wrapper"
date: 2009-11-08
forum: General Help
---

### Post by ali313 on 2009-11-08
hi
i upgraded my ubuntu 9.04 to karmic and now every time i want to log out or shutdown in ubuntu this error will appear:
[IMG]http://motahharipur.persiangig.com/image/at_spi.png[/IMG]
  what i must do to solve it?

---

### Post by ali313 on 2009-11-08
no anyone?

---

### Post by P4man on 2009-11-08
its related to orca screen reader and other "assistive technologies". Chances are you are not using any of that, so you may as well not load it.
Go to systam > prefences > startup applications (or sessions I think in jaunty_ and disable it there. Will save you a few milliseconds in faster boot too ;)

---

### Post by ali313 on 2009-11-08
thank for reply
I disabled **at-spi-registryd-wrapper **but now when i run an application for example gedit this errors appear:
```
 ali@ali-desktop ~/Desktop$ gedit

(gedit:6313): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(gedit:6313): atk-bridge-WARNING **: IOR not set.

(gedit:6313): atk-bridge-WARNING **: Could not locate registry

```what this errors mean? 
other problem that the firefox and terminal will be open at start up ubuntu and dont save the changes in **startup applications**!!

---

### Post by P4man on 2009-11-08
apparently you are running something that depends on the accessibility deamon. No idea what, but I suppose gedit works fine nonetheless as those are just warnings (W) not errors.

See if you are starting any other service related to accessibility, like Visual Assistance in that same sessions or startup list.

---

### Post by P4man on 2009-11-08
> **ali313 said:**
> 
other problem that the firefox and terminal will be open at start up ubuntu and dont save the changes in **startup applications**!!

You can set gnome to save your session in the session diaglue (second tab I think). If you dont like that, just disable it. Enabled it will remember which apps where running when you logged out and restart them when you log in.

---

### Post by ali313 on 2009-11-08
> You can set gnome to save your session in the session diaglue (second tab I think). If you dont like that, just disable it. Enabled it will remember which apps where running when you logged out and restart them when you log in.
it is disable and firefox and termial are not open at shutdown but they will open on startup!!

---

### Post by P4man on 2009-11-08
thats weird. Can you perhaps post a screenshot of your maximized "session" list? Or do you see anything in there that might be related to it?

---

### Post by ali313 on 2009-11-08
a list of enabled programs in **startup applications**:
bluetooth Manager
disk notifications
emerald
gnome keyring daemon
gnome login sound
gnome settings daemon helper
indicator applete
parcellite (clipboard manager)
policykit authentication agent
screansaver
seahorse daemon
user folder update
volume control

i dont thing that these are relate to it

---

### Post by P4man on 2009-11-08
nope, me neither

If you are absolutely 100% certain you are not saving your session, then try installing bootup manager from add/remove programs. Run it from system > adminstratin > bootup manager. Perhaps that may shed some light..

---

