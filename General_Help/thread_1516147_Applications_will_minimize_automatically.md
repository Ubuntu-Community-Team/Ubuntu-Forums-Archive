---
title: "Applications will minimize automatically"
date: 2010-06-23
forum: General Help
---

### Post by brock spencer on 2010-06-23
Applications will minimize automatically. when i select them they will maximize then immidiatly minimize.
i just installed ubuntu 10.04 on my netbook everything worked great then i ran the update manager it restarted. after that i cannont keep any apps open.
ubuntu 10.04 on acer aspire one netbook. clean install. ubuntu only.

---

### Post by dino99 on 2010-06-23
[http://packages.ubuntu.com/en/lucid/alltray](http://packages.ubuntu.com/en/lucid/alltray)

you can right click on the minimized icon into the systray and check the properties of this app

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
metacity --replace

if something is not configured as it'll expected, check for errors into .xsession-errors (/home , unhide it ctrl+h), and into: system admin logviewer

---

### Post by brock spencer on 2010-06-23
When i right click all it list is preferances. it will lunch then minimise. i cannont load the tray.

---

### Post by dino99 on 2010-06-23
goto: system admin hardware driver, and check that the driver is activated

have you run the previous commands into a terminal, and look for errors logged ?

---

### Post by brock spencer on 2010-06-23
well when i launch anything. hardware drivers, terminal, firefox anything it wont stay open enough for me to check or do anything. 
i am new to linux. is there a safe mode or anyway to revert back the updates?

---

### Post by dino99 on 2010-06-23
in case, check the powerconfig settings and screensaver too (disable them)

a little help about installing ubuntu:
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by brock spencer on 2010-06-23
i was able to log into just the terminal. i did the sudo commands but i cannont load the tray.
is there a sudo command for the tray?

---

### Post by brock spencer on 2010-06-23
everything works fine in failsafe mode.

---

