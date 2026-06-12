---
title: "Software Center does not install, apt-get update does not update"
date: 2012-03-20
forum: General Help
---

### Post by Last_Ship on 2012-03-20
When I am using the US Server and attempt to install something in the Software Center I get the error message "failed to download package files, check your Internet connection" (or something to that effect). I changed to the main server, and now when I attempt to install a program, for example Wine, the install progress bar flashes for a second and then disappears and does not install the program.

Also, upon performing a sudo apt-get update I receive the following:

Err [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease
  
Err [http://archive.canonical.com](http://archive.canonical.com) maverick InRelease
  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease
  
Err [http://download.skype.com](http://download.skype.com) stable InRelease
  
Err [http://linux.dropbox.com](http://linux.dropbox.com) oneiric InRelease
  
Err [http://dl.google.com](http://dl.google.com) stable InRelease
  
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick InRelease
  
Err [http://deb.opera.com](http://deb.opera.com) stable InRelease
  
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) oneiric InRelease
Err [http://repository.spotify.com](http://repository.spotify.com) stable InRelease
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security InRelease
  
Err [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg
  Unable to connect to Localhost:8118: [IP: ]
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg
  Unable to connect to Localhost:8118: [IP: ]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg
  Unable to connect to Localhost:8118: [IP: ]
Err [http://download.skype.com](http://download.skype.com) stable Release.gpg
  Unable to connect to Localhost:8118: [IP: ]
Err [http://linux.dropbox.com](http://linux.dropbox.com) oneiric Release.gpg
  Unable to connect to Localhost:8118: [IP: ]
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg
  Unable to connect to Localhost:8118: [IP: ]
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release.gpg
  Unable to connect to Localhost:8118: [IP: ]
Err [http://deb.opera.com](http://deb.opera.com) stable Release.gpg
  Unable to connect to Localhost:8118: [IP: ]
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) oneiric Release.gpg
Err [http://repository.spotify.com](http://repository.spotify.com) stable Release.gpg
  Unable to connect to Localhost:8118: [IP: ]
Err [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg
  Unable to connect to Localhost:8118: [IP: ]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg
  Unable to connect to Localhost:8118: [IP: ]
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) oneiric Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg
  Unable to connect to Localhost:8118: [IP: ]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg
  Unable to connect to Localhost:8118: [IP: ]
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) oneiric/main i386 Packages/DiffIndex
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release.gpg
  Unable to connect to Localhost:8118: [IP: ]
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) oneiric/main TranslationIndex
Err [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) oneiric/main i386 Packages
  couldn't connect to host
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) oneiric/main Translation-en_US
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) oneiric/main Translation-en
Reading package lists... Done
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/InRelease](http://archive.ubuntu.com/ubuntu/dists/oneiric/InRelease)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/InRelease](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/InRelease)  

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/InRelease](http://archive.canonical.com/ubuntu/dists/oneiric/InRelease)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/InRelease](http://extras.ubuntu.com/ubuntu/dists/oneiric/InRelease)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/InRelease](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/InRelease)  

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/oneiric/InRelease](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/oneiric/InRelease)  

W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/InRelease](http://download.skype.com/linux/repos/debian/dists/stable/InRelease)  

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/InRelease](http://archive.canonical.com/ubuntu/dists/maverick/InRelease)  

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/oneiric/InRelease](http://linux.dropbox.com/ubuntu/dists/oneiric/InRelease)  

W: Failed to fetch [http://dl.google.com/linux/earth/deb/dists/stable/InRelease](http://dl.google.com/linux/earth/deb/dists/stable/InRelease)  

W: Failed to fetch [http://packages.medibuntu.org/dists/maverick/InRelease](http://packages.medibuntu.org/dists/maverick/InRelease)  

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/InRelease](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/InRelease)  

W: Failed to fetch [http://deb.opera.com/opera/dists/stable/InRelease](http://deb.opera.com/opera/dists/stable/InRelease)  

W: Failed to fetch [http://repository.spotify.com/dists/stable/InRelease](http://repository.spotify.com/dists/stable/InRelease)  

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/Release.gpg](http://archive.canonical.com/ubuntu/dists/oneiric/Release.gpg)  Unable to connect to Localhost:8118: [IP: ]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg](http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg)  Unable to connect to Localhost:8118: [IP: ]

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Unable to connect to Localhost:8118: [IP: ]

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/oneiric/Release.gpg](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/oneiric/Release.gpg)  Unable to connect to Localhost:8118: [IP: ]

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/Release.gpg](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/Release.gpg)  Unable to connect to Localhost:8118: [IP: ]

W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/Release.gpg](http://download.skype.com/linux/repos/debian/dists/stable/Release.gpg)  Unable to connect to Localhost:8118: [IP:]

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/oneiric/Release.gpg](http://linux.dropbox.com/ubuntu/dists/oneiric/Release.gpg)  Unable to connect to Localhost:8118: [IP: ]

W: Failed to fetch [http://dl.google.com/linux/earth/deb/dists/stable/Release.gpg](http://dl.google.com/linux/earth/deb/dists/stable/Release.gpg)  Unable to connect to Localhost:8118: [IP: ]

W: Failed to fetch [http://packages.medibuntu.org/dists/maverick/Release.gpg](http://packages.medibuntu.org/dists/maverick/Release.gpg)  Unable to connect to Localhost:8118: [IP: ]

W: Failed to fetch [http://deb.opera.com/opera/dists/stable/Release.gpg](http://deb.opera.com/opera/dists/stable/Release.gpg)  Unable to connect to Localhost:8118: [IP: ]

W: Failed to fetch [http://repository.spotify.com/dists/stable/Release.gpg](http://repository.spotify.com/dists/stable/Release.gpg)  Unable to connect to Localhost:8118: [IP: ]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Unable to connect to Localhost:8118: [IP: ]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg)  Unable to connect to Localhost:8118: [IP: ]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg)  Unable to connect to Localhost:8118: [IP: ]

W: Failed to fetch [https://private-ppa.launchpad.net/commercial-ppa-uploaders/crossover-games/ubuntu/dists/oneiric/main/binary-i386/Packages](https://private-ppa.launchpad.net/commercial-ppa-uploaders/crossover-games/ubuntu/dists/oneiric/main/binary-i386/Packages)  couldn't connect to host

W: Some index files failed to download. They have been ignored, or old ones used instead.

I've checked, fairly thoroughly i think, the forums and I have not yet seen a threat that addresses this problem specifically. I apologize if there is and I somehow missed it.

I'm relatively new to Ubuntu/Linux, so any help or insight would be greatly appreciated. Thank you.

---

### Post by cortman on 2012-03-20
Hi, welcome to Ubuntu!

The output of the apt-get update command would indicate that it's completely unable to contact the repository servers. This could be because


[LIST]
[*]You're using an unconfigured proxy
[*]Your computer is not connected to the internet
[*]The server is not reachable (change mirrors)
[/LIST]

Can you first confirm that you're connected to the internet and not using a proxy?

---

### Post by IWantFroyo on 2012-03-20
```
ping -c 3 google.com
```

Please run this in Terminal and post the output here. It seems like your connection might be having issues.

---

### Post by Last_Ship on 2012-03-21
Here is the ouput of the ping:
64 bytes from ord08s08-in-f1.1e100.net (74.125.225.97): icmp_req=1 ttl=48 time=35.5 ms
64 bytes from ord08s08-in-f1.1e100.net (74.125.225.97): icmp_req=2 ttl=48 time=49.7 ms
64 bytes from ord08s08-in-f1.1e100.net (74.125.225.97): icmp_req=3 ttl=48 time=32.4 ms

--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 32.477/39.261/49.757/7.528 ms

My connection seems to be working. I'm able to access sites and my mail client, thunderbird is not having any trouble either.

---

### Post by Last_Ship on 2012-03-21
I can confirm that my connection is working. I can access sites and my mail client, thunderbird, is working without any problems. I do have a proxy, TOR, however it is not running anywhere.

---

### Post by cortman on 2012-03-21
Make sure TOR is not running at all, and try changing your server mirrors (go to Settings>Software Sources).

---

### Post by Last_Ship on 2012-03-21
Yes, I can confirm that TOR is not running at all. I've tried switching from the US server to the Main and I still get the same response from apt-get update. When I'm on the US server, Software Center will give me a "failed to download package files check your internet connection" message. If I switch to the main and try to install a program in Software Center I will get the install progress bar momentarily and then it will disappear without having installed the program.

---

### Post by mraandtux on 2012-03-21
Try to change a different software source.

---

### Post by cortman on 2012-03-21
> **matt2422 said:**
> Yes, I can confirm that TOR is not running at all. I've tried switching from the US server to the Main and I still get the same response from apt-get update. When I'm on the US server, Software Center will give me a "failed to download package files check your internet connection" message. If I switch to the main and try to install a program in Software Center I will get the install progress bar momentarily and then it will disappear without having installed the program.

Hm, run

```
cat /etc/apt/apt.conf
```

If this returns that there is no file, then that isn't causing the problem. If apt.conf has a bunch of proxy info in it, you will need to delete it.

---

### Post by Last_Ship on 2012-03-25
Thanks so much for the responses. It looks like the system settings were set for there to be a proxy but one was never configured. How I was still able to access the internet I do not know. I think I've got it fixed now though, thanks again I really appreciate the help.

---

### Post by cortman on 2012-03-26
Great, glad it worked.
Mark this thread [SOLVED] if you would. Thanks!

---

### Post by alphabravo8 on 2012-05-01
thanks dudes that post has been most useful for me too!

---

