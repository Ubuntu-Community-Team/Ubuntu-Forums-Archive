---
title: "Samba"
date: 2006-04-06
forum: General Help
---

### Post by Fatstink on 2006-04-06
I am using Kubunut 5.10 Breezy Badger and have installed samba, however I don't know how to get it up and running.  Any ideas???

---

### Post by moephan on 2006-04-06
If you haven't already done so, check here:
[http://ubuntuguide.org/#sambaserver](http://ubuntuguide.org/#sambaserver)

Cheers, Rick

---

### Post by Fatstink on 2006-04-06
Is there a GUI I can get for Samba?

---

### Post by moephan on 2006-04-06
There are several, but none are too good IMHO. If you search for "samba" in synaptic, you will find:

tksmb: a samba client gui that allows you to browse a network
swat: a web based configuration tool for samba server

You can look install and try out some others as well that may be up there. Check here for instructions on using synaptic to install software: [http://ubuntuguide.org/#synaptic](http://ubuntuguide.org/#synaptic)

Cheers, Rick

---

### Post by Fatstink on 2006-04-07
I am using Kubuntu so I don't have synaptic.  Any other way to get it that you know of?

---

### Post by feathers on 2006-04-07
Then use adept to install it.

---

### Post by Fatstink on 2006-04-07
When I got the TkSmb package, extracted it but I get an error.

bash: ./INSTALL: /usr/bin/expectk: bad interpreter: No such file or directory

should I redirect it or am I missing a package??

---

### Post by chusome on 2006-04-07
I've found webmin to be the easiet for configuring samba.
To install it type:

sudo apt-get install webmin-samba

The point browser to [http://127.0.0.1:10000](http://127.0.0.1:10000)
Webmin makes alot of things easier.

---

### Post by xmastree on 2006-04-07
Shouldn't that be https?
How do I log into to webmin once it's installed? It won't accept my usual login...

Edit: Belay that, I found /usr/share/webmin/changepass.pl

Comment still stands about https though.

---

### Post by Fatstink on 2006-04-07
sudo apt-get install webmin-samba,  does not exist... any other way to get it?

---

### Post by Fatstink on 2006-04-07
Does anyone know of either a good GUI for Samba or a good HOWTO to help me set up a server and start sharing???

---

### Post by mcanada on 2006-04-07
I have found the official Samba documentation to be the most helpful overall. You can find it at [www.samba.org](www.samba.org).

If you would like to share a directory then try this from Konsole:

```
sudo nano /etc/samba/smb.conf
```

add this to the end of the file
```
[myshare]
path=/home/myuser

```

where "myshare" is the name of the share you are wanting to create and the path leads to a path on your server.

and use CTRL+x to exit and save. This is a simple share example. You would then be able to access that share.

---

### Post by Fatstink on 2006-04-07
But how do I actually set up the Samba server???

---

### Post by wanger123 on 2006-04-08
Make sure you have samba and smb4k (gui for samba) installed. Go to system settings --> System services --> admin mode. Make sure that the samba service is running and selected to start at boot. Then reboot and open smb4k and you should see your network computers.

You can also enter smb:/ in konqueror address bar

cheers
wanger

---

### Post by Fatstink on 2006-04-08
where do I get smb4k, it's not in Adept or Synaptic????

---

