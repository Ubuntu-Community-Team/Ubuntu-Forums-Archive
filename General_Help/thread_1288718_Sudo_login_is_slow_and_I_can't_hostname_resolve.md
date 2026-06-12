---
title: "Sudo login is slow and I can't hostname resolve"
date: 2009-10-11
forum: General Help
---

### Post by iankellogg on 2009-10-11
I have two different computers running 8.10 on one and 9.04 on another. We had a power surge which took out the NIC on one but left the other intact. I replaced the NIC on the broken one with a PCI adapter and everything seemed okay at first. However, even with nameservers listed in /etc/resolve.conf I can't resolve any hostname at all. And I'm not sure if this is a side affect of it or not, but it takes on the order of minutes to login with 'sudo su' or any 'sudo (command)'. As well as that, I can't even log into the machines with SSH anymore as it takes 4 minutes to prompt for a password and then it just times out and says connection closed by server. 

I can still access these machines by their ip address through apache and through samba so I know that their NIC's are working correctly but still can't log in or resolve hostnames =/

---

### Post by iankellogg on 2009-10-13
Bump, Is it really that hard for someone to help me?

---

### Post by sandeep37 on 2009-10-13
Check your host name in your localhost name, it may be start with (".","/"@ etc) . Which cause problem

---

### Post by Jimmynemo2 on 2009-10-13
Did you replace your host file? I used to do that as an antimalware protection- but in ubuntu the host file needs some parts left alone.

Also, if you dont get answers, bumps are fine, but snide comments tend to get you no where, remember, people dont owe you help.

---

### Post by kanikilu on 2009-10-13
I'm having a little trouble understanding your setup, can you clarify this a bit? You say you have 2 computers you are trying to access, so I'm assuming there is a 3rd computer involved that you are trying to access them from. Is this another Ubuntu/Linux machine, or Windows? If from Windows, have you tried flushing the DNS (ipconfig /flushdns)? Perhaps your router has the DNS cached, have you tried restarting it?

---

### Post by iankellogg on 2009-10-14
This problem started happening with no changes to the machines. Aside from one of them had to have an NIC replacement. But other than ONE machine getting a new NIC they are untouched. In fact I can't touch them because one Can't display out of video (drivers refuse to work but I dont care) and I can't log into ether of these machines.

I have many machines in my house and many servers in a rack where these two machines live. All servers are linux be it redhat or ubuntu. The two machines that are having these login and DNS resolving issues are Ubuntu 8.10 (for the machine that is 100% untouched) and 9.04 (for the one that needed a NIC replacement and can't display video).

All machines in my house can log in to each other, except these two. 

My windows machine can ssh correctly and same with other linux computers. 

If I try to ssh into the two machines in question. It takes around 3-4 minutes for the password prompt to come up. After which, another 2-3 minutes and then I get "Connection Closed by Server"

I know there is a DNS issue because on the ubuntu 8.10 machine I have a keyboard and mouse hooked up, but Can not browse the internet. 

Both of these machines run Samba and NFS and I am able to mount these file systems with no issues.  I hope this is in enough detail. The problem is really bothering me because it has caused mythtv to stop working (can't get the show times).

---

### Post by bab1 on 2009-10-14
> ...even with nameservers listed in /etc/resolve.conf I can't resolve any hostname at allIs the /etc/resolve.conf a typo?  It should be /etc/resolv.conf.

Is one of the nameservers for local DNS resolution?  Have you checked the mapping of hostnames to IP addresses?

---

