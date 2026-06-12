---
title: "FTP client with web UI?"
date: 2010-11-21
forum: General Help
---

### Post by enneth on 2010-11-21
Hi,

I'm looking for an FTP client that has a web UI, i.e. I want to be able to access the FTP client on my Ubuntu desktop at my other home via the web.
I have two homes as I travel much because of work, and in my primary home I have a desktop running Ubuntu. In my second home I have a NAS server. What I want is to be able to access my Ubuntu desktop's FTP client via the web and thereby be able to upload files to my NAS server.

Is there a such FTP client? Or is there any other way that I can make the Ubuntu desktop upload files without me having to sit around at my laptop watching the progress as it is the case if I use scp? If I close the terminal window during a file transfer, the file transfer stops too.

The NAS server runs on a Marvell 800 MHz (ARM) so it is possible to run the armel dist of Debian on it if that would make things easier.

---

### Post by Verbeck on 2010-11-21
net2ftp is a good web based ftp client
[http://www.net2ftp.com/homepage/download.html](http://www.net2ftp.com/homepage/download.html)

you'll still need to keep the browser window open

---

### Post by enneth on 2010-11-21
Thanks for the reply! I already tried net2ftp and it wasn't much of a success as I can't keep the window open while I'm on the move. 

Is it possible to somehow make an scp transfer that doesn't cancel if you close the terminal window? I'm thinking I'll connect to the Ubuntu desktop via SSH from my laptop, then transfer the file via scp from my Ubuntu desktop to the NAS server, then close the terminal window on my laptop and somehow keep the connection between Ubuntu desktop and NAS alive. Is that possible?

---

### Post by matt_symes on 2010-11-21
Hi

Maybe you could run a script with the nohup command and run as a background process.. That will keep the script running when the terminal is closed.

man nohup

Something along the lines of.....

nohup /path/to/script.sh &

Kind regards.

---

### Post by tredegar on 2010-11-21
> **enneth said:**
> Thanks for the reply! I already tried net2ftp and it wasn't much of a success as I can't keep the window open while I'm on the move. 

Is it possible to somehow make an scp transfer that doesn't cancel if you close the terminal window? I'm thinking I'll connect to the Ubuntu desktop via SSH from my laptop, then transfer the file via scp from my Ubuntu desktop to the NAS server, then close the terminal window on my laptop and somehow keep the connection between Ubuntu desktop and NAS alive. Is that possible?

Yes.
You can use **screen**. See 
[http://nathan.chantrell.net/old-stuff/linux/an-introduction-to-screen/](http://nathan.chantrell.net/old-stuff/linux/an-introduction-to-screen/)

Pay attention to the bit about "Detaching/reattaching sessions" which I think is exactly what you need.

---

### Post by enneth on 2010-11-21
That sounds exactly as the command I'm looking for! Thanks a bunch!

---

