---
title: "trouble installing tor"
date: 2011-05-16
forum: General Help
---

### Post by sesquipedalian on 2011-05-16
Here are the instructions I am using to try and install tor

[https://www.torproject.org/docs/debian.html.en#ubuntu](https://www.torproject.org/docs/debian.html.en#ubuntu)

When I put 

"http://deb.torproject.org/torproject.org <maverick>"

in the terminal it gave me

"bash: syntax error near unexpected token `newline'"

I then proceeded to type in the next code just to see what would happen, at first, it seemed all I would have to do is type in my root password and get in, but it didn't work out so I started over again. Anyway this is what happened

@:~$ gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg: requesting key 886DDD89 from hkp server keys.gnupg.net
gpg: key 886DDD89: "deb.torproject.org archive signing key" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
@:~$ gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
OK
@:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
@:~$ apt-get install tor tor-geoipdb
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
@:~$ 
@:~$ sudo su
root@:/home/j# apt-get update

[long package list cut out for reading ease]

Reading package lists... Done
root@:/home/# apt-get install tor tor-geoipdb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package tor is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'tor' has no installation candidate
E: Unable to locate package tor-geoipdb
root@:/home/#



So, I am not sure at this point where my problem lies, anyone here have an idea?

---

### Post by Lateralis on 2011-05-16
That guide is hideous!

Click System -> Administration -> Software sources. 

You'll be prompted to type in your password.  Click the "Other Software" tab and hit the "add" button.  In the dialogue box which appears, type:

```

deb http://deb.torproject.org/torproject.org lucid main 

```

if you are running 10.04.  Change that to *natty* if you are running 11.04 or *maverick* if you are running 10.10.  You'll be asked if you want to refresh the package lists, which you can safely ignore for now.

Then in a terminal, type

```

gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -

```

This will add the key for the repository.  Then, refresh your lists and install the program:

```

sudo apt-get update
sudo apt-get install tor tor-geoipdb

```
  
As with all software that you install from non-Ubuntu repositories, ensure that you know what you are doing and are positive that any packages you install will not break anything currently installed.

---

