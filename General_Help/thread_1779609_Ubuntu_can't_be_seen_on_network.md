---
title: "Ubuntu can't be seen on network"
date: 2011-06-10
forum: General Help
---

### Post by Kissell on 2011-06-10
I reinstalled ubuntu 10.10 from scratch, didn't like 11.04.  At the time I decided to finally switch this box to my new computer naming convention.  That was a mistake, I have an appliance that took a long time to configure hundreds of lines that all reference this box by name.

So I changed the hostname back to what it was before I reinstalled the box by running hostname and also changing the /ect/hostname file.  This seemed to work, the command prompt shows the name correctly.

Now the machines on my network cannot see this ubuntu box...  :(

I think it is a WINS problem?  I updated the samba config to make sure it has wins support, rebooted ubuntu and all the other computers, still, nobody can see the ubuntu box by name.

I can access the ubuntu box from a windows machine by either using its IP address or putting the box in the windows host file, but i need it to be able to be found automatically by name without configuration, because like I said earlier, I have an appliance that relies on finding it by name, and there is no way to configure its host file, so I have to fix this on the ubunut box.  It used to work, before I reintalled ubuntu.

---

### Post by papibe on 2011-06-10
Could you post the result of this ?
```
$ ps aux | grep mbd
```
Regards.

---

### Post by Kissell on 2011-06-10
ps aux | grep mbd
> 
root     13181  0.0  0.2  16796  4148 ?        Ss   15:49   0:00 smbd -F
root     13184  0.0  0.0  16796  1160 ?        S    15:49   0:00 smbd -F
root     13804  0.0  0.1  17020  3852 ?        S    16:14   0:00 smbd -F
root     14026  0.0  0.0   4012   764 pts/1    S+   17:33   0:00 grep --color=auto mbd


---

### Post by papibe on 2011-06-10
OK.

It is a [bug]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/572410"). The process that broadcast the machine name it is called nmbd, and obviously is not running in your computer.

To solve it, upgrade your server to the latest updates. It seems that a newer version has been released.

If that does not work, this solve the problem for me:
```
$ sudo dpkg-reconfigure samba-common-bin
```
Hope it helps.

---

### Post by Kissell on 2011-06-10
I run "sudo dpkg-reconfigure samba-common-bin" it said.
> 
update-alternatives: using /usr/bin/nmblookup.samba3 to provide /usr/bin/nmblookup (nmblookup) in auto mode.
update-alternatives: using /usr/bin/net.samba3 to provide /usr/bin/net (net) in auto mode.
update-alternatives: using /usr/bin/testparm.samba3 to provide /usr/bin/testparm (testparm) in auto mode.


Then I did the previous command and there still is no process running for nmdb, just the same as before.

---

### Post by papibe on 2011-06-10
Restart samba:
```
$ sudo service smbd restart
```

---

### Post by Kissell on 2011-06-10
Tried to run "nmdb"
> 
No command 'nmdb' found, did you mean:
 Command 'nmbd' from package 'samba' (main)
 Command 'mdb' from package 'mono-debugger' (universe)
 Command 'imdb' from package 'imdb-tools' (universe)
nmdb: command not found


tried to install it using "apt-get install nmdb"
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nmdb
root@SERVER-KISSELL:/etc# nmdb
No command 'nmdb' found, did you mean:
 Command 'nmbd' from package 'samba' (main)
 Command 'mdb' from package 'mono-debugger' (universe)
 Command 'imdb' from package 'imdb-tools' (universe)
nmdb: command not found


tried to install it using "apt-get install samba"
> 
root@SERVER-KISSELL:/etc# apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 315 not upgraded.


still no nmdb running.  :(

---

### Post by Kissell on 2011-06-10
> **papibe said:**
> Restart samba:
```
$ sudo service smbd restart
```

sudo service smbd restart
> 
smbd start/running, process 14555


ps aux | grep mbd
> 
root     14555  0.2  0.1  16804  4064 ?        Ss   17:59   0:00 smbd -F
root     14558  0.0  0.0  16804  1164 ?        S    17:59   0:00 smbd -F
root     14560  0.0  0.0   4012   764 pts/1    S+   17:59   0:00 grep --color=auto mbd


---

### Post by papibe on 2011-06-10
Did you try the suggestions on the bug report?
```
$ sudo apt-get install samba-common-bin
```
and
```
$ sudo apt-get install samba-common
```
Then restart samba.

Regards.

---

### Post by Kissell on 2011-06-10
> **papibe said:**
> Did you try the suggestions on the bug report?
```
$ sudo apt-get install samba-common-bin
```
and
```
$ sudo apt-get install samba-common
```
Then restart samba.

Regards.

Oops, my bad, I just ran the command you posted...

Did "apt-get install samba-common-bin"

nmdb is running now.

:)  yeah!

I'll go try it on that box, see if it can see it now.

---

### Post by papibe on 2011-06-10
Glad you solve it.

---

### Post by Kissell on 2011-06-12
No no, it was all you, I've tested it, and it is 100% fixed...  nmbd just wasn't running on the linux box, and now that it is, there is no more problem.  thanks a lot!

---

