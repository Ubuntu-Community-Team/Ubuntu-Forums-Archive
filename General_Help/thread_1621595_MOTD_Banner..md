---
title: "MOTD Banner."
date: 2010-11-14
forum: General Help
---

### Post by Chint on 2010-11-14
I have tried amend the MOTD banner but it keeps resetting back to default motd message. I don't get it.  Running latest 10.x version on Linux on Vmware.

I am editing this file. sudo vim /etc/motd

---

### Post by gmargo on 2010-11-14
The Message-Of-The-Day (motd) file is generated dynamically.  Note that **/etc/motd** is actually a link to **/var/run/motd**.  See the man pages **motd(5)** and especially **motd.tail(5)** for information on how to append to the dynamic element (using /etc/motd.tail) or turning off the dynamic bit by using a symbolic link.

---

### Post by Chint on 2010-11-14
Sorry, I am very new to Linux just know the very basic stuff. So how to I get to that link to deactivate the dynamic link in the **/etc/motd** so I can use my own one. Where do I find the man page for** MOTD**? Also what is a **Symbolic** link?

---

### Post by gmargo on 2010-11-14
> So how to I get to that link to deactivate the dynamic link in the **/etc/motd** so I can use my own one.
On the command line:```

sudo vi /etc/motd.static                 # Add your static message
sudo rm /etc/motd                        # remove old symlink
sudo ln -s /etc/motd.static /etc/motd    # link static motd file

```> Where do I find the man page for** MOTD**?On the command line:
```

man 5 motd
man 5 motd.tail

```> Also what is a **Symbolic** link?[http://en.wikipedia.org/wiki/Symbolic_link](http://en.wikipedia.org/wiki/Symbolic_link)

---

### Post by Chint on 2010-11-14
That has worked going to read up on it. But it now seems to be printing out twice and no resizing.

Thank you for your help! Much appreciated.

---

