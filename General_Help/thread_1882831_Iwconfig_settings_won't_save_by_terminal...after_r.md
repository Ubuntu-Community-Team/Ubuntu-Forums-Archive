---
title: "Iwconfig settings won't save by terminal...after reboot network settings revert"
date: 2011-11-18
forum: General Help
---

### Post by slixz85 on 2011-11-18
hi, i have been having internet wifi problems and turning off the power management on my wifi usb adapter seem to help it a bit better but it still just starts idling in the middle of a page loading for a few minutes. it is a pain. but the sudo iwconfig wlan0 power off command helps it a bit but after i restart the computer if i type in iwconfig then i see that the power management is back on for it. so does anyone know how i can make this command save and does terminal do this alot?

---

### Post by Toz on 2011-11-18
Try adding it to /etc/rc.local before the exit 0 statement. Example:
```

iwconfig wlan0 power off
exit 0
```

/etc/rc.local will execute each time your computer boots.

---

### Post by slixz85 on 2011-11-22
> **Toz said:**
> Try adding it to /etc/rc.local before the exit 0 statement. Example:
```

iwconfig wlan0 power off
exit 0
```

/etc/rc.local will execute each time your computer boots.


yeah i normally dont type exit just click the x but after i put in sudo iwconfig wlan0 power off it still doesnt save it after reboot. it does definitely change it though after i put in the command iwconfig wlan0 power off but just after reboot every time i have to redo it. i have no idea what is wrong with my wifi as well. extremely slow... the connection goes in and out of idle every couple seconds in the middle of loading pages.

---

### Post by Toz on 2011-11-22
If you want the "iwconfig wlan0 power off" command to survive a reboot, add it to the file "/etc/rc.local" (above the existing "exit 0" command that already exists in that file). On every boot, that file (/etc/rc.local) is executed and if you have the iwconfig command in there, it too will get executed at every boot.

---

### Post by slixz85 on 2011-11-22
> **Toz said:**
> If you want the "iwconfig wlan0 power off" command to survive a reboot, add it to the file "/etc/rc.local" (above the existing "exit 0" command that already exists in that file). On every boot, that file (/etc/rc.local) is executed and if you have the iwconfig command in there, it too will get executed at every boot.

ok thanks

---

