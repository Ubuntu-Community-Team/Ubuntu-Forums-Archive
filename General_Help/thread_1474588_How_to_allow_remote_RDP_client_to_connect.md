---
title: "How to allow remote RDP client to connect"
date: 2010-05-06
forum: General Help
---

### Post by satimis on 2010-05-06
Hi folks,

xrdp
gnome
ubuntu 9.10

I have xrdp installed running on the PC.  Please advise how to allow remote Linux PC to connect Ubuntu 9.10?  TIA

Do I need to install;
libcurl4-openssl-dev
libpam0g-dev
vnc4server


B.R.
satimis

---

### Post by sprince09 on 2010-05-06
Install xrdp on the machine you want to connect to.

Install tsclient on the machine you want to use to connect to the remote machine.

Run tsclient, choose `RDP` for the protocol and enter the IP address of the remote machine, then hit connect.

Enjoy :)

---

### Post by satimis on 2010-05-06
Hi  sprince09,


Thanks for your advice.

I followed following link;
[http://ubuntuwiki.net/index.php/Xrdp,_installing](http://ubuntuwiki.net/index.php/Xrdp,_installing)

to install XRDP.

Now it works.  Client can connect Ubuntu server on the LAN.  But Ubuntu server takes up the entire client desktop.  Is there a solution?  Thanks


> **sprince09 said:**
> Install xrdp on the machine you want to connect to.

Install tsclient on the machine you want to use to connect to the remote machine.

I have tsclient installed and running on the local machine

Start tsclient to connect the remote machine Ubuntu 9.10 on LAN.  It connects but taking up the entire Gnome desktop of the local machine, same as rdesktop.

On Terminal Server Client
-> Display
Remote Desktop Size
- Use default screen size
- Use specified screen size
having no effect.

On remote machine;
vncserver -geometry 800x600 :1

Any suggestion?  TIA

B.R.
satimis

---

### Post by sprince09 on 2010-05-07
> **satimis said:**
> 

Now it works.  Client can connect Ubuntu server on the LAN.  But Ubuntu server takes up the entire client desktop.  Is there a solution?  Thanks

...
...

Start tsclient to connect the remote machine Ubuntu 9.10 on LAN.  It connects but taking up the entire Gnome desktop of the local machine, same as rdesktop.



You mean when you run rdesktop/tsclient and successfully connect, the resulting window is full-screened? In that case make sure your settings in rdesktop/tsclient aren't conflicting with the server-side settings. Try going to the 'Display' tab in tsclient and forcing the window size to be 800x600.

Also, I'm not sure if this makes a difference or not, but I'm running vnc4server (not tightvncserver) on my machine, and I'm also running 10.04. For me, the process of getting this all up and running consisted of just the following:

```

scott@galatea:~$ sudo aptitude install vnc4server xrdp tsclient

```

and then once installation was complete, I checked it with 

```

scott@galatea:~$ rdesktop localhost

```

In my previous post I didn't realize that VNC was a required component to make this all work (sorry, I'm definitely not an expert on any of this!)

---

### Post by satimis on 2010-05-07
> **sprince09 said:**
> You mean when you run rdesktop/tsclient and successfully connect, the resulting window is full-screened? In that case make sure your settings in rdesktop/tsclient aren't conflicting with the server-side settings. Try going to the 'Display' tab in tsclient and forcing the window size to be 800x600.

Also, I'm not sure if this makes a difference or not, but I'm running vnc4server (not tightvncserver) on my machine, and I'm also running 10.04. For me, the process of getting this all up and running consisted of just the following:

```

scott@galatea:~$ sudo aptitude install vnc4server xrdp tsclient

```

and then once installation was complete, I checked it with 

```

scott@galatea:~$ rdesktop localhost

```

In my previous post I didn't realize that VNC was a required component to make this all work (sorry, I'm definitely not an expert on any of this!)

Hi sprince09,

I tried your suggestion before without result.  They seems having no function here.

The only solution is to lower the screen resolution of the remote XRDP server.  Then the window forward won't take up the entire screen.  But another problem popup my friend working on the server complains the font size on the screen becomes very large unable working comfortably on it.

B.R.
satimis

---

### Post by sprince09 on 2010-05-07
Huh, I'm stumped then :/

---

