---
title: "sudo: unable to resolve host graham-desktop"
date: 2010-05-13
forum: General Help
---

### Post by capo1949 on 2010-05-13
Hi All
I am trying to install skype on ubuntu 9.04 and following instructions at
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype).
I Fall at the first hurdle with;-
graham@graham-desktop:~$ sudo echo "deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free #Skype" | sudo tee -a /etc/apt/sources.list > /dev/null
sudo: unable to resolve host graham-desktop

I have googled the alarm and have returned post looking to check the etc/host file, this does not exist on my system. I am using a dell desktop and a belkin router.

Some assistance would be much appreciated

---

### Post by sisco311 on 2010-05-13
It's /etc/hosts and it should look like this:
```

...
#<ip-address>   <hostname.domain.org>   <hostname>
127.0.0.1               localhost.localdomain   localhost
127.1.0.1               **graham-desktop**
...
```

To edit it run:
```
gksu gedit /etc/hosts
```

---

### Post by Iowan on 2010-05-13
My machines have the hostname in */etc/hosts* associated with 127.0.1.1

Did you change the hostname (*/etc/hostname*)? That's the kind of error message that pops up when one of the above gets changed without the other.

---

### Post by Woody1987 on 2010-05-13
Just go to the skype website and download it. [http://www.skype.com/intl/en-gb/get-skype/on-your-computer/linux/]("http://www.skype.com/intl/en-gb/get-skype/on-your-computer/linux/")

---

### Post by capo1949 on 2010-05-14
Hi
Thanks for your replies.
Tried 1st suggestion got ;-
graham@graham-desktop:~$ /etc/hosts
bash: /etc/hosts: Permission denied
graham@graham-desktop:~$ sudo /etc/host
sudo: unable to resolve host graham-desktop
[sudo] password for graham: 
sudo: /etc/host: command not found
graham@graham-desktop:~$ 


so went on to try it with editor ;-
127.0.0.1	localhost yourhost
127.0.1.1	yourhost

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts 

so ammended as suggested to;-
127.0.0.1	localhost.localdomain   localhost
127.0.1.1	graham-desktop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

works great now thanks all for your help

could you please advise how this could have happened?

---

