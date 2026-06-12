---
title: "Cannot connect to WIFI after installing Ubuntu 10.04"
date: 2010-11-30
forum: General Help
---

### Post by jmschuaquico on 2010-11-30
Hi! I just installed Ubuntu 10.04 in my laptop and I can't connect to WIFI. When I boot with Windows 7, the connection is fine. I think the problem is with the drivers so I decided to boot on Windows 7 and look for the driver for Ubuntu. Problem is, I do not know what driver do I download. I need Help. Here's an image of my Device Manager in Windows 7.

[IMG]http://img153.imageshack.us/img153/2118/devicemanagerb.png[/IMG]

---

### Post by rahilm on 2010-11-30
I suppose you need to install broadcomm drivers...
can u connect to the internet via ubuntu??

if yes.. then try System->Administration->Additional Drivers

---

### Post by jmschuaquico on 2010-11-30
I can't connect via Ubuntu. I haven't tried wired either because the only available connection is tru WIFI only. I can only try wired connection when I go home, which is on the weekend. I need to make Wifi working on my Ubuntu asap.

Can i download the driver tru Windows and install it tru USB to Ubuntu? And what specific drivers? I'm sorry, I'm a real noob at this. and thanks.

---

### Post by rahilm on 2010-11-30
ok.. don't worry...its still possible..

boot into ubuntu..
goto system->administration->Additional Drivers

There you may (u hav to if this has to work) find Broadcomm listed..

Select it and at the bottom press Enable(or install or wtv .. i don;t remember)..

Ubuntu will try to download the required file.. but hey.. no connection...

So, the most possible thing to happen is that it will display an error message saying it cannot download the certain file.. and it will list the name of the file..

There you will find the URL of the required file.. just copy it into a text file .. save the text file in the windows partition.. boot into windows. and download the file..

come back to ubuntu and install the file..

done

---

### Post by jmschuaquico on 2010-11-30
I just tried it. system->administration->Hardware Drivers (no additional drivers)
It didn't list a thing. T_T

anything else?

---

### Post by inso_741 on 2010-11-30
take a look [here]("http://ubuntuforums.org/showthread.php?t=1592044&page=3")
try blacklisting b43 and wl modules....the try getting the source code for the drivers through windows and compile it in ubuntu

---

### Post by jmschuaquico on 2010-12-01
Thank you everyone for your reply.

I was able to wire my laptop to an internet connection. I have now downloaded the required driver. Thanks!

---

### Post by kanishkdudeja on 2010-12-01
Great. Please mark the thread as solved.

---

