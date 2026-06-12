---
title: "Connect to the internet using terminal"
date: 2010-05-02
forum: General Help
---

### Post by Elitemike on 2010-05-02
Does anyone happen to know how to connect to a WPA2 wireless network using only the terminal ?

---

### Post by beastrace91 on 2010-05-02
Doing this via the CLI is not ideal, but if you must I suggest you start [here]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking")

Regards,
~Jeff

---

### Post by Untitled_No4 on 2010-05-02
1. Turn your wifi on
```
sudo ifconfig wlan0 up
```

2. Scan your network
```
sudo iwlist wlan0 scan
```

3. Once you found the id of your network run
```
sudo iwconfig wlan0 essid [your id]
```

4. Set your key
```
sudo iwconfig wlan0 key [key]
```

5. Connect 
```
sudo dhclient
```

---

### Post by Elitemike on 2010-05-02
when i enter the command for the key i get this.

Error for wireless request "set Encode" (8B2A) :
    invalid argument "my key"

---

### Post by Untitled_No4 on 2010-05-03
Is your key a passphrase? Try this then```
iwconfig wlan0 key s:[KEY]
```

---

### Post by Elitemike on 2010-05-03
it still does not work, it gets the same error

---

### Post by KeyserSoze93 on 2010-05-03
Check out [http://vidner.net/martin/software/cnetworkmanager/](http://vidner.net/martin/software/cnetworkmanager/). It is an interface to the existing network connection manager, which runs from the terminal. It's somewhat easier than using the iwconfig command manually.

---

