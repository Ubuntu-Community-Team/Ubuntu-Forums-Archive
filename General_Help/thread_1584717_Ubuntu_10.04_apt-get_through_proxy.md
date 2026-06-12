---
title: "Ubuntu 10.04 apt-get through proxy"
date: 2010-09-29
forum: General Help
---

### Post by Lucr3tius on 2010-09-29
I'm not sure what could be wrong but I can't download any packages now.

I need mdadm (or if anyone knows of a better utility) to manage a software RAID5 on this HP DL320 G6 because all it has is a SATA controller that isn't intelligent enough for RAID5 (I have it disabled in BIOS).

I've tried using ```
sudo apt-get update
``` from the terminal window and it tells me that it fails to fetch updates.  As a possible fix I edited etc/bash.bashrc to include ```
 export http_proxy=http://username:password@proxyserver:port/
```

After that update I rebooted just to be sure and tried it again, same error.

I figured since it wouldn't work using the terminal window I would give Synaptic a try...
Inside Synaptic I've edited the network settings under preferences to add the information for the proxy server I'm trying to get through.  I can search for "mdadm" and it returns nothing.

The kicker is that I can download and install software in Synaptic that is already in the list, it just won't find mdadm.

Thanks everyone for any insight.  I'm still relatively new to Linux, but getting more comfortable.

---

### Post by Lucr3tius on 2010-09-29
I figured it out!

I created a file called "proxy" in /etc/apt/apt.config.d/
In that file I added:
```
Acquire::http::Proxy "http://username:password@proxy:port";
```I also found a function for bash.bashrc that I think I can use to make this more dynamic and less of a security risk.

```
function proxy()
{
    echo -n &#8220;username:&#8221;
    read -e username
    echo -n &#8220;password:&#8221;
    read -es password
    export http_proxy=&#8221;http://$username:$password@proxy:port&#8221;
    export ftp_proxy=&#8221;http://$username:$password@proxy:port&#8221;
    echo -e &#8220;\nProxy environment variable set.&#8221;
}
```I'm going to try and use the environment variables created with this function to modify the proxy file I created in apt.config.d so that I don't have to store my password in plain text on the machine.

---

### Post by Rankin1 on 2011-01-16
Hey
I'm trying to attempt the same thing but for some reason I don't have the access level required to add that file to /etc/apt/apt.config.d <---- I may have typed that wrong but I'm using the root that you posted, cant remember if its the same. Anyway it wont let me add that "Proxy" file, I'm the admin on my Ubuntu 10.04 but obviously that doesn't make a difference. Any help you can give me with getting the access I need would be appreciated

---

