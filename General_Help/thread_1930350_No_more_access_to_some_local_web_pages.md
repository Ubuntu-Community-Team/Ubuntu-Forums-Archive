---
title: "No more access to some local web pages"
date: 2012-02-23
forum: General Help
---

### Post by dclement on 2012-02-23
Hello,

I can no longer access some web pages on my LAN. Here is the story: I have a network drive (Synology DS106j) which also acts as photo server, local address 192.168.0.9. I do see it under 'Network'.

But in Firefox, if I try and type [http://192.168.0.9/photo/](http://192.168.0.9/photo/) , I get the error message "Firefox cannot connect with server at 192.168.0.9."

However, I still do have access to the management interface of the NAS ([http://192.168.0.9:5000](http://192.168.0.9:5000) -- port 5000, then). How come?

I also tried Epiphany et Chromium with identical results. So I cannot blame a recent Firefox upgrade (10.0.2).

I am running Ubuntu Lucid. TIA for any help!

Regards, Daniel

---

### Post by jonobr on 2012-02-23
Assuming your using apache as your webserver

then using a terminal window, type

```
sudo /etc/init.d/apache status
```
If it reports that it is not running
try starting again
```
sudo /etc/init.d/apache start
```

if it gives an error when starting then open a thread on that.

Cheers

---

### Post by dcstar on 2012-02-24
> **dclement said:**
> Hello,

I can no longer access some web pages on my LAN. Here is the story: I have a network drive (Synology DS106j) which also acts as photo server, local address 192.168.0.9. I do see it under 'Network'.

But in Firefox, if I try and type [http://192.168.0.9/photo/](http://192.168.0.9/photo/) , I get the error message "Firefox cannot connect with server at 192.168.0.9."

However, I still do have access to the management interface of the NAS ([http://192.168.0.9:5000](http://192.168.0.9:5000) -- port 5000, then). How come?

I also tried Epiphany et Chromium with identical results. So I cannot blame a recent Firefox upgrade (10.0.2).

I am running Ubuntu Lucid. TIA for any help!

Regards, Daniel

The NAS is not running a web server on port 80. Check the configuration of it or reboot it.

This will test the connection:

```
telnet 192.168.0.9 80
```

---

### Post by dclement on 2012-02-24
Thanks for the quick replies. That solved my problem.

For a reason, the web server on the Syno NAS was stopped. It resumed working when I restarted it.

Since I made no change to its config, the only explanation I see for this is a recent power cut, which has stopped the Syno unexpectedly. Perhaps not all services restart normally when power is restored.

Thanks again - regards, Daniel

---

### Post by jonobr on 2012-02-24
Those things should autstart but you never know,

Might be an idea just to keep an eye on it as maybe something else is up

---

