---
title: "set system Date/Time - normal user"
date: 2011-08-19
forum: General Help
---

### Post by rdk_ec on 2011-08-19
Hi,
I want to change the Date and Time of the system from my application. This can be done using the "Date -s" linux command. But the application has to be executed as root/sudo. 

is it possible that root can give permission to normal user to execute the "Date -s" command?

or any other suggestion to change the system date and time as a normal user?

---

### Post by dino99 on 2011-08-19
right click on the date/time to tweak your prefs: disable net update then change the date as you need/want

---

### Post by rdk_ec on 2011-08-19
But I would like to do this inside a java application dynamically.

---

### Post by tcsmith1978 on 2011-08-19
Could you advise what it is exactly you are wanting to do this for? It's not normal to change the system dynamically like this. Perhaps there is another way round this that we could help with.

---

### Post by rdk_ec on 2011-08-19
I am using ubuntu based system just for the front end where the core part is done by external hardware which has its own wireless communication network(eg. Digital Radio). 

Now the time on Ubuntu system has to be synchronized with the time on the external network. How can I do this? if not system time atleast the session time?

---

### Post by tcsmith1978 on 2011-08-19
Am still a little confused. Why does the other hardware change it's time/date so frequently? Sorry if I am missing the point! Just trying to find a solution. Can you give me a concrete example?

---

### Post by grahammechanical on 2011-08-19
Does this help?

[http://www.cyberciti.biz/faq/set-date-time-network-time-protocol-ntp/]("http://www.cyberciti.biz/faq/set-date-time-network-time-protocol-ntp/")

Regards.

---

### Post by tcsmith1978 on 2011-08-19
That's kind of what I was thinking but from what rdk_ec says - he wants to change it "on the fly"

---

### Post by rdk_ec on 2011-08-19
If for example the time has to be exactly the same on set of systems on the digital radio network then it is easy to configure the time in the base transmitting station and all the systems on the network will then synchronize to the transmitting stations time.

My GUI application is designed using java and to get time I use System.currentTimeMillis();. I compare the time on the digital radio network with the system time, if different I set the System time to network time.

---

### Post by tcsmith1978 on 2011-08-19
Can you synchronize the time to the network with ntupdate as per grahammechanical? Or better still - get all the machines to using the same Time Server?

---

### Post by rdk_ec on 2011-08-19
thought dint try yet.. looking at the procedure it seems I need to run it as a root which I don't want to do.

is it this complicated to just set the time as a normal user :-( 

someone told you can do this on SUSE distro.. dont know how true is this

---

### Post by dino99 on 2011-08-19
time ? which one ? gmt+10 or gmt-8 ? daylight saving ?
The time is different everywhere ;)

maybe consider the network time only (client) or server time.

---

### Post by rdk_ec on 2011-08-19
it doesn't matter if it is GMT + 1 or .. I need a way to change it as a normal user..

---

### Post by tcsmith1978 on 2011-08-20
I think Network Time is your best option... :(

---

### Post by rdk_ec on 2011-08-22
I am wondering if I explained my problem correctly? 

in simple words

How to execute the "Date -s" linux command as non-root/non-sudoer?

---

