---
title: "CUPS Service Stopped"
date: 2010-08-04
forum: General Help
---

### Post by Twig E. Pottox on 2010-08-04
unable to print to / install / locate Dell P1500 laser

The printing troubleshooter says:

 "CUPS service does not appear to be running. to correct this , choose SYSTEM->Administration->Services from the main menu and lookfor the cups service"

unfortunately there is no->Services tag under ->Administration to look for the CUPS Spooler.

running 10.04 64 Bit on a dual boot with vista AMD6000 box Printing is fine on the vista side so the printer and usb connection is fine.

any hints on troubleshooting this?  Thanks in advance.

---

### Post by Morbius1 on 2010-08-04
Try restarting the cups service manually and see if the error goes away:
```
sudo service cups restart
```

---

### Post by sydbat on 2010-08-04
> **Morbius1 said:**
> Try restarting the cups service manually and see if the error goes away:
```
sudo service cups restart
```If this does not work, try this```
sudo apt-get install --reinstall cups
```

---

### Post by Twig E. Pottox on 2010-08-04
Thanks for your help.  that did the trick the printer is now recognized as is cups. 

Still sorting our driver issues ... Hope its not another post.

---

### Post by Morbius1 on 2010-08-04
If you find that every time you boot cups has not started then that is a known bug. This workaround seems to work: [http://ubuntuforums.org/showpost.php?p=9405854&postcount=4](http://ubuntuforums.org/showpost.php?p=9405854&postcount=4)

---

