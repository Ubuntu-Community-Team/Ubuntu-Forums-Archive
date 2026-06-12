---
title: "Set Name For Machine"
date: 2009-07-02
forum: General Help
---

### Post by mthalis on 2009-07-02
I wrote a program that run on apache server. I run it using   
> [http://192.168.20.253/test/index.php](http://192.168.20.253/test/index.php). so what I want is use name instated of use ip address like
> [http://name/test/index.php](http://name/test/index.php)
Because my program share within the network then i want hide my IP address.

---

### Post by WRDN on 2009-07-02
Try this:

First, backup /etc/nsswitch.conf:

```
sudo cp nsswitch.conf nsswitch.conf.bak
```

Now, edit it:

```
gksudo gedit /etc/nsswitch.conf
```

Change the line starting "hosts: files" to:

```
hosts: files wins dns
```

Install winbind:

```
sudo apt-get install winbind
```

You should now be able to ping the hostname.

---

### Post by mthalis on 2009-07-02
I did what you say but i couldn't figure out what you exactly say. please explain it more.

---

### Post by WRDN on 2009-07-02
WinBind allows you to login to a machine using Windows/UNIX/Linux. It does this by making the UNIX machine think the Windows machine is a UNIX machine.

Once you've gone through the steps, get the hostname of the machine you want to contact (the web server), and open a Terminal and type "ping [hostname]". Alternatively,just try entering the hostname in a web browser.
I prefer using ping as it shows it is at least possible to contact the machine. Web browsing would only show Apache is setup correctly.

---

### Post by mthalis on 2009-07-02
any references?

---

