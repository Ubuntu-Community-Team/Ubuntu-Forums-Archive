---
title: "Connection sharing troubles"
date: 2006-06-10
forum: General Help
---

### Post by enigmamachine42 on 2006-06-10
I have enabled connection sharing in Firestarter, but a host (I will call this one "A") connected to my main pc ("B") by ethernet cannot access anything past the wireless interface of B.  At one time, I had it so that the host could ping the router connecting me to the internet, but couldn't actually access the internet.  This is the best I have ever been able to get my connection sharing to work.  Since then, I have somehow messed even that up.  If anyone has any suggestions, they would be greatly appreciated.

---

### Post by woedend on 2006-06-10
Im confused as to your setup.  So here is my terminology.  PCa is connected to the internet via a router/modem.  PCb is connected to PCa and is trying to access the internet also.  On PCa, you need firestarter running...when you set firestarter up, naturally it asks which is the internet connected device and which is local.  make sure local is the card that connects to PCb and internet is the card connecting you to the router/modem(your internet connection).  Great, then enable internet connection sharing, which you've done.  What you must do then is go to administration - networking, and set the card selected earlier as local(that goes to PCb) and set its ip address to something like 192.168.2.1, mask to 255.255.255.0, and no gateway.  Then, on PCb, set the ip address to static of 192.168.2.2, subnet mask of 255.255.255.0, and default gateway of 192.168.2.1

Let me know if you need more help, I've got mine working like this as we speak so trust me you can get it :)

---

### Post by enigmamachine42 on 2006-06-10
I tried your directions on the pc that will be my router, but with no success (initially).  While I was writing a reply detailing my failure, I decided to try pinging from PCb one last time just to make sure I wouldn't be wasting your time.  Success!  Inexplicable though it may be, I'll take it.  Thank you for your help.

---

### Post by woedend on 2006-06-11
one more thing.  make sure that on PCb you specify your ISP's DNS servers.

---

