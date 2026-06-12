---
title: "Finding all the linux machines connected the network"
date: 2012-09-12
forum: General Help
---

### Post by fernansha on 2012-09-12
good morning everybody,

a doubt, about machines connected to the network. 
How can one find all the linux machines connected to the network. 
without being a root. 
like machines has numbers eg: pc12345 
with any information, we already have is there a way to spot all the linux machines?? 

thanks

---

### Post by Statia on 2012-09-12
You could run nmap with OS fingerprinting on your subnet.
Not sure if you need to be root for the fingerprintng though.
man nmap is your friend.

---

### Post by fernansha on 2012-09-12
nmap sure will give it a try.

# the main purpose is we have more than 100 machines in the building, which is all linux, we know only few of their pc numbers. so with nmap how exactly u can look for the machines ??

---

### Post by Statia on 2012-09-12
You give nmap a range of IP-adresses to scan, for instance 192.168.1.1-255.
That will scan all the machines in your network, then you look at the output to find the Linux machines. You can have nmap write it's output to a file, even in XML, so you can use tools like grep to filter out the Linux machines.

---

### Post by markbl on 2012-09-12
As he said, read "man nmap". It uses all sorts of tricks to find hosts. No point explaining all the options here.

---

### Post by Lars Noodén on 2012-09-12
Just a hint: it is the -O option for [nmap](http://manpages.ubuntu.com/manpages/precise/en/man1/nmap.1.html).  However, there are two caveats.  

First, make sure you have an agreement with your network administrator before scanning.  Scans or mistakes in scanning may set off alarms and it is best to pave the way before you begin.  

Second, the fingerprinting seems not to identify the development version of Ubuntu.  I don't have older versions to test but it's important to note that the fingerprinting is just a guess and not 100% accurate.

Happy scanning.

---

### Post by fernansha on 2012-09-12
Thanks a lot guys, will give it a try though. 
was really helpful.

---

