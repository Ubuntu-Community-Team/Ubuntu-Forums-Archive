---
title: "inconsistent wi-fi connection"
date: 2011-07-06
forum: General Help
---

### Post by Hartfield on 2011-07-06
Ever since I got a new router I've been having inconsistent wi-fi connection.  Every now and then the speed becomes very slow to the point i have to re-connect, and it does, and then everything is okay. 

Other times the signal just drops and i have to reset the computer to re-connect.  I have a Ubuntu 11.04 & my router is a Netgear router. 

Any leads?

---

### Post by plucky on 2011-07-06
> **Hartfield said:**
> Ever since I got a new router I've been having inconsistent wi-fi connection.  Every now and then the speed becomes very slow to the point i have to re-connect, and it does, and then everything is okay. 

Other times the signal just drops and i have to reset the computer to re-connect.  I have a Ubuntu 11.04 & my router is a Netgear router. 

Any leads?

Have you tried changing the Channel Number the the Router is using for wi-fi?

In your area it might be getting interference from other devices.

Good Luck

---

### Post by Hartfield on 2011-07-06
> **plucky said:**
> Have you tried changing the Channel Number the the Router is using for wi-fi?

In your area it might be getting interference from other devices.

Good Luck

I have not, Ho would I go about doing that?

---

### Post by plucky on 2011-07-07
> **Hartfield said:**
> I have not, Ho would I go about doing that?

Open your browser and input the IP address of your router.(Check the label on your router)

Login and then navigate to the wi-fi section and select the channel number.

To find what channels are being used in your area,open a terminal and run ```
sudo iwlist scan
``` should tell you what channels are being used by other routers.

Good Luck

---

### Post by createdcreature on 2011-07-07
The IP would probably be '192.168.0.1'. Put that into your address bar.

---

### Post by Hartfield on 2011-07-11
I went ahead and changed the channel.  It was set in "auto" and i switched to an actual number.  The problem still continues.  It tends to increase as I dload certain files on vuze.

---

### Post by Hartfield on 2011-07-17
BUMP. :guitar:

---

