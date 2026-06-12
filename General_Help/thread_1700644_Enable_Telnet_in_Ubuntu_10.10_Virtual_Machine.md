---
title: "Enable Telnet in Ubuntu 10.10 Virtual Machine"
date: 2011-03-05
forum: General Help
---

### Post by CheezitDroid on 2011-03-05
I have been searching for the past hour trying to figure out how I can enable telnet on my Ubuntu 10.10 Virtual Machine. I am using VirtualBox to run my VM. I am trying to access that VM using PuTTy but most everything I have seen says I have to enable telnet first. The directions that I have found say to go to System > Administration > Services and enable telnet. I have nothing called Services under Administration. If someone can tell me where I find this elusive Services interface or another way to enable telnet on my VM it would be a big help. Thanks in advance.

---

### Post by Joe of loath on 2011-03-05
SSH is now preferred over telnet.

Simply run 'apt-get install openssh-server', and it'll work :)

---

### Post by CharlesA on 2011-03-05
Is there a specific reason for using telnet?

Normally you'd use SSH instead, as it offers more security then telnet.

Install it by running this:
```
sudo apt-get install openssh-server
```

---

### Post by CheezitDroid on 2011-03-05
This is part of a Lab I am doing for a class. I have to use Telnet even though its useless now and basically no one uses it. I can get SSH to work no problem but the Telnet is being a pain.

---

### Post by davidmohammed on 2011-03-05
I'm sure you are aware telnet is run from a terminal...

Accessories - Terminal

what happens if you just type

```
telnet 
```

it should give you a > prompt

---

### Post by CheezitDroid on 2011-03-05
I can telnet the VM into itself using the terminal but I have to use PuTTy to telnet into the Ubuntu VM from my host windows machine. Everything I've seen says you have to enable telnet. I just don't know how.

---

### Post by davidmohammed on 2011-03-05
you should install the telnetd-ssl server element in ubuntu

```
sudo apt-get install telnetd-ssl
```

---

### Post by CheezitDroid on 2011-03-05
I installed this before and I still cannot connect from outside of the VM.

---

### Post by davidmohammed on 2011-03-05
try the unsafe telnetd instead

sudo apt-get remove telnetd-ssl
sudo apt-get install telnetd

---

### Post by CharlesA on 2011-03-05
Also, are you using bridged networking, or NAT for the VM?

---

### Post by CheezitDroid on 2011-03-05
> try the unsafe telnetd instead

I tried both versions and neither worked. 

> Also, are you using bridged networking, or NAT for the VM?

I am using NAT. Would bridged be required for it to work?

---

### Post by CharlesA on 2011-03-05
> **CheezitDroid said:**
> 
I am using NAT. Would bridged be required for it to work?

Yep. With NAT you can connect to the host from the guest, but not from the host to the guest.

---

### Post by CheezitDroid on 2011-03-05
I tried changing it to bridged. PuTTy still said no. :)

---

### Post by uRock on 2011-03-05
Is the firewall activated? To disable;

```
sudo ufw disable
```

---

### Post by CheezitDroid on 2011-03-05
I tried it and it didn't make a difference. I emailed my instructor and he told me to skip it and use SSH. Thanks for the responses though!

---

### Post by davemiles871 on 2011-05-06
I have successfully got this working on 10.04 LTS as follows:

Install the telnet daemon with 

```
sudo apt-get install telnetd
```

unfortunately this doesn't do any of the other configuration steps that are required.

You also need to do the following:

1. Check xinetd is installed. If you have the folder /etc/xinetd.d on your system, then xinetd IS installed. Otherwise

```
sudo apt-get install xinetd
```

2. Now edit or create the file /etc/xinetd.d/telnet with your favourite editor:

It needs to contain as a minimum: 

[SIZE="1"]# default: on
# description: The telnet server serves telnet sessions; it uses
# unencrypted username/password pairs for authentication

service telnet
{
        disable = no
        flags = REUSE
        socket_type = stream
        wait = no
        user = root
        server = /usr/sbin/in.telnetd
        log_on_failure += USERID

# see below there may be other optional lines to add here

}[/SIZE]

You can optionally add any of the following, subject to the configuration of you local network.

[SIZE="1"]only_from = 10.126.204.0/23 #Only users in 10.126.204.0 can access to
only_from = .mynet.com #allow access from mynet.com
no_access = 10.126.204.{101,105} #not allow access from the two IP.
access_times = 8:00-9:00 20:00-21:00 #allow access in the two times
[/SIZE]

You should update the xinetd configuration to allow logon success and failure logging as my example for the telnet config file above shows a configuration where failed logon attempts are written to a logfile, so also make the following changes to /etc/xinetd.conf

[SIZE="1"]# Simple configuration file for xinetd
#
# Some defaults, and include /etc/xinetd.d/
defaults
{
# Please note that you need a log_type line to be able to use log_on_success
# and log_on_failure. The default is the following :
# log_type = SYSLOG daemon info
instances = 60
log_type = SYSLOG authpriv
log_on_success = HOST PID
log_on_failure = HOST
cps = 25 30
}[/SIZE]

Now you can restart the xinetd server with:

```
service xinetd restart
```

and check by looking at /var/log/syslog, where something like the following output will have appeared at the end (hint: in a separate terminal session, run ```
tail -f /var/log/syslog
```, whilst you do all the other stuff)

[SIZE="1"]May  6 14:00:22 ipplansvr xinetd[7098]: Exiting...
May  6 14:00:22 ipplansvr xinetd[7131]: Reading included configuration file: /etc/xinetd.d/chargen [file=/etc/xinetd.conf] [line=18]
May  6 14:00:22 ipplansvr xinetd[7131]: Reading included configuration file: /etc/xinetd.d/daytime [file=/etc/xinetd.d/daytime] [line=28]
May  6 14:00:22 ipplansvr xinetd[7131]: Reading included configuration file: /etc/xinetd.d/discard [file=/etc/xinetd.d/discard] [line=26]
May  6 14:00:22 ipplansvr xinetd[7131]: Reading included configuration file: /etc/xinetd.d/echo [file=/etc/xinetd.d/echo] [line=25]
May  6 14:00:22 ipplansvr xinetd[7131]: Reading included configuration file: /etc/xinetd.d/nrpe [file=/etc/xinetd.d/nrpe] [line=26]
May  6 14:00:22 ipplansvr xinetd[7131]: Reading included configuration file: /etc/xinetd.d/telnet [file=/etc/xinetd.d/telnet] [line=16]
May  6 14:00:22 ipplansvr xinetd[7131]: Reading included configuration file: /etc/xinetd.d/time [file=/etc/xinetd.d/time] [line=14]
May  6 14:00:22 ipplansvr xinetd[7131]: removing chargen
May  6 14:00:22 ipplansvr xinetd[7131]: removing chargen
May  6 14:00:22 ipplansvr xinetd[7131]: removing daytime
May  6 14:00:22 ipplansvr xinetd[7131]: removing daytime
May  6 14:00:22 ipplansvr xinetd[7131]: removing discard
May  6 14:00:22 ipplansvr xinetd[7131]: removing discard
May  6 14:00:22 ipplansvr xinetd[7131]: removing echo
May  6 14:00:22 ipplansvr xinetd[7131]: removing echo
May  6 14:00:22 ipplansvr xinetd[7131]: removing time
May  6 14:00:22 ipplansvr xinetd[7131]: removing time
May  6 14:00:22 ipplansvr xinetd[7131]: xinetd Version 2.3.14 started with libwrap loadavg options compiled in.
May  6 14:00:22 ipplansvr xinetd[7131]: Started working: 2 available services[/SIZE]

From the top..., this shows the existing xinetd exiting, then starting and reading the configuration files in /etc/xinetd.d, then reporting its started, with two services running - in my case these will be nrpe (from nagios) and telnet.

As a final check, run the following and expect output like:

```
[SIZE="1"]root@ipplansvr:/etc/xinetd.d# netstat -a | grep telnet
tcp        0      0 *:telnet                *:*                     LISTEN     
root@ipplansvr:/etc/xinetd.d# [/SIZE]
```

Share enjoy.

Dave

---

