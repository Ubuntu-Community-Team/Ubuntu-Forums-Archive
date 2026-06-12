---
title: "accidently deleted some important files"
date: 2010-06-21
forum: General Help
---

### Post by blackhawx on 2010-06-21
I made an attempt to delete evolution, but apparently a few of its files were connecte to desktop?  so now whenever i try to log into ubuntu, my username and password gets approved, then the screen goes black with a little bit of text , and then it takes be right back to the log in screen.

I see a lot of people saying that if you are in the text counsel mode, simply type in..

sudo apt-get -f install ubuntu-desktop


and that will fix your issue.  But I am not connected to the network in text-console mode.  I always connect to my network when I log in with the little network icon on the desktop panel.  How do i connect to my network from the text-console??? what does the code look like?

thanks

---

### Post by warfacegod on 2010-06-21
That -f in the code can go. It should read:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by nothingspecial on 2010-06-21
If you have a wired connection, then, boot into console mode
```

sudo ifconfig eth0 up
sudo dhclient
sudo apt-get install ubuntu-desktop
```

The first 2 lines will connect you to the internet.

---

### Post by blackhawx on 2010-06-21
thank you so much for the tips. but i think i did something wrong.  Earlier I assumed "networking restart" would auto detect my network settings.  but i think that screwed me up because now when i try to dhclient, it doesnt find my IP address. It just finds a bunch of 255.555.555 addresses.  nor if i do ipconfig MY IP.  Instead I get an error that says the device does not exist :(

is there another way to install gnome and desktop from my usb stick rather than the internet from the text console?


this is so weird - how is it that now, while i'm in windows vista, i can connect to my IP and type this message, but when i reboot my system in ubuntu in safe mode, it cannot find the same IP with dhclient?????? it just doesn't make sense to me...

---

### Post by warfacegod on 2010-06-21
You can use Vista (gag) to download unetbootin and make another Ubuntu LiveUSB.

---

