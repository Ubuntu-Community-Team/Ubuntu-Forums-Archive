---
title: "Time Problem"
date: 2009-10-26
forum: General Help
---

### Post by fachamix on 2009-10-26
I have a problem, I presume its something really simple but I am new in linux.
 
I have a server with Ubuntu 9.04, it works as a File Share Server.
Nobody uses it ( I mean , with mouse, and keyboard .... locally), Its just a File Server.
 
So I change the date and time manually, and I leave it on my Server Room
 
Sometimes I have ti Restart the server, and every time I do that, the date and Time is modify.
 
I am pretty sure that something happends when UBUNTU is booting up the OS, and my network cable is ALWAYS pluging up, so something is going on during boot time on my network that modifyies my datetime settings.
 
 
any suggestions ?
 
thanks a lot

---

### Post by akakingess on 2009-10-26
Could it be the battery on the motherboard that is not saving the time? Just a noobie suggestion.

---

### Post by fachamix on 2009-10-27
Its some service.
 
the battery of my motherboard works fine.
 
If I reboot my PC without the network cable, the time is the same as the BIOS, but if i reboot with the network cable pluged in , the time changes.
 
I presume that some service reaches the Net to get My timezone info during boot time, I DONT WANT THIS TO HAPPEN
 
how can I know wich service is, how can I stop the proc ???
 
thanks a lot

---

### Post by Tony Flury on 2009-10-27
Let me get this right - you have a file server in your network that you want to be deliberately out of step with the real time ?

The service that keeps the time in step is called nntp - you will need to stop it - and make sure it does not start again.
```

sudo /etc/init.d/nntp stop

```

Should stop the nntp service cleanly - not sure how to prevent it starting up though - something in the init.d files should do it i would have thought.

Bear in mind that if you have machines that use that file server, and those machines do have nntp running, then things will get very confusing, as the on board clock on your server will drift (and that drift can be very large if the CMOS battery gets run down, or the system is left switched on for long periods), and the other machines wont drift - meaning that files saved on the file server will effectively get incorrect time stamps. 

I am very puzzled as to why you want a file share server running with the incorrect time, but each to their own.

---

### Post by P4man on 2009-10-27
im guessing you got the timezone set up wrongly? Upon boot ubuntu synchs the time and applies the time zone and then you manually set it "wrong" again? Check the timezone in system>adminstration>time and date settings.

---

### Post by CharlesA on 2009-10-27
You can do it from the terminal by running this command: dpkg-reconfigure tzdata

---

