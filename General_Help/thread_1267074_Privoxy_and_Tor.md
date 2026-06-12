---
title: "Privoxy and Tor"
date: 2009-09-15
forum: General Help
---

### Post by Thomas.Kast on 2009-09-15
I know I have tor and privoxy configured right because it has been working without trouble for most websites. But, every once in a while I get this error message:


Forwarding failure

Privoxy was unable to socks4a-forward your request [http://ubuntu.com/](http://ubuntu.com/) through localhost:
SOCKS request rejected or failed.

: Does anyone have any suggestions or had this happen to them?

---

### Post by jasmineaura on 2009-09-28
**Do the following:**

1. Open the file "/etc/privoxy/config" in your favorite text editor (as root)
```
sudo nano /etc/privoxy/config
```

2. Replace:
```
forward-socks4a / localhost:9050 .
```

With:

```
forward-socks5 / localhost:9050 .
```

3. Restart privoxy:
```
sudo /etc/init.d/privoxy restart
```

**The following is OPTIONAL!**

1. _Install Vidalia_ : a graphical user interface to control/configure TOR. Default install should work out-of-the-box for you and no additional configuration needed.

```
sudo aptitude install vidalia
```

2. _Install firefox torbutton extension_ : Allows you to single-left-click right corner of your status bar in firefox - at the bottom - to toggle "Tor Disabled" / "Tor Enabled".

```
sudo aptitude install torbutton-extension
```

Don't forget to close and reopen firefox after you install torbutton extension if you already had it running while installing.

For additional (updated) help on using Tor on Ubuntu, check:
[https://www.torproject.org/docs/debian#ubuntu](https://www.torproject.org/docs/debian#ubuntu)

Hope that helps :)

--Jas

---

### Post by jasmineaura on 2009-09-28
Additional note, for people using the **jaunty repository** listed [in the link I mentioned above]("https://www.torproject.org/docs/debian#ubuntu"), while running **Karmic Koala** (latest development release as of date) - **since there isn't yet a karmic repository on [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org)**

I noticed "libevent1" package was dropped in karmic, in favor of new "libevent-1.4-2" package.

Simply, download the latest libevent1 package from jaunty universe (search it from [http://packages.ubuntu.com](http://packages.ubuntu.com) ), download it, then install it using `dpkg`

Example:
```
# cd /usr/src
# wget http://mirrors.kernel.org/ubuntu/pool/main/libe/libevent/libevent1_1.3e-3_i386.deb
# dpkg -i libevent1_1.3e-3_i386.deb
```

Then you can easily install tor (and tor-geoipdb) from jaunty dist on the torproject repository without any dependency issues :)
```
# aptitude install tor tor-geoipdb
```

Hope this helps anyone..

--Jas

---

