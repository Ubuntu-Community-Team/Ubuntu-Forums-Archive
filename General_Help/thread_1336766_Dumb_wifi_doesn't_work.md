---
title: "Dumb wifi doesn't work"
date: 2009-11-24
forum: General Help
---

### Post by Eragon0605 on 2009-11-24
I am running ubuntu 9.10 karmic koala. I am running a desktop computer, so I have to plug in a usb wifi adapter to get internet. Ubuntu detects the usb drive and displays all the available networks, but none of them connect! First, I tried the one from my router (which is like 8 feet away). When I try to enter the password, I get a loading animation for about 2 or 3 minutes, then it asks for the key again. I know it is the right key. I tried WEP 128-bit Pssphrase and the default WEP 40/128-bit Key. I dual-boot ubuntu with windows 7, and windows connects to the internet fine. I also tried connecting to my neighbor's unsecure wifi (har-har) and it says that I am connected, but when I try to use firefox, it says i'm not connected to the internet...

---

### Post by Mike_IronFist on 2009-11-24
> **Eragon0605 said:**
> I am running ubuntu 9.10 karmic koala. I am running a desktop computer, so I have to plug in a usb wifi adapter to get internet. Ubuntu detects the usb drive and displays all the available networks, but none of them connect! First, I tried the one from my router (which is like 8 feet away). When I try to enter the password, I get a loading animation for about 2 or 3 minutes, then it asks for the key again. I know it is the right key. I tried WEP 128-bit Pssphrase and the default WEP 40/128-bit Key. I dual-boot ubuntu with windows 7, and windows connects to the internet fine. I also tried connecting to my neighbor's unsecure wifi (har-har) and it says that I am connected, but when I try to use firefox, it says i'm not connected to the internet...

You could reset your router.

---

### Post by Ancanus on 2009-11-24
Try using a different network manager.

Connect by wire to your router and 

```
sudo aptitude install wicd
```

---

### Post by Eragon0605 on 2009-11-24
Alright, tried wicd. I like this interface much better :). Now when I try to connect, everything goes smoothly, until it gets to the part where it gets the IP address. It sits there, loading for about 2-3 minutes (again) and then I get an error message saying "Connection Failed: Unable to Get IP Address".

---

### Post by Agent Smith on 2009-11-24
Mine does this also. What i did was assign an ip address manually and it connects everytime. Hope this helps.

---

### Post by Eragon0605 on 2009-11-24
Alright, IP error fixed. Now I get an access point error. It says it's verifying access point association, and then almost immediately I get an error message saying "Connection failed: Could not contact the wireless access point." Wow, these errors just keep on coming!

---

