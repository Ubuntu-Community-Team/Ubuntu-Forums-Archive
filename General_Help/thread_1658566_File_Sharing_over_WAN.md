---
title: "File Sharing over WAN"
date: 2011-01-02
forum: General Help
---

### Post by rmausser on 2011-01-02
I have a Server Computer with a 2.0 TB RAID on it. 

I want to be able to access and modify the files on it from any computer remotely.

Is what I am looking for an "SSH Tunnel" to fileshare over the Internet? 

If this is what I want, please help me find the resources for doing this. I dont even know where to begin!

I am running Ubuntu 10.10.

I am not looking for remote computing. I cannot guarantee that the remote computer I am on will have Ubuntu on it. I want the files to show up like they would over normal SMB/SAMBA networking. 

I just want to be on any computer in the world, enter in an IP address, enter a password, connect, and be able to access my files.

I have a Static IP for my home internet. I know, im so lucky :D

Thank you.

---

### Post by noah++ on 2011-01-02
What you want to do is pretty common, and it's one of those nice things that's easier to accomplish when the home server is running Linux as opposed to Windows.

Install the **openssh-server** package on your home machine. I believe once you install it, it starts itself, and configures itself to start at boot.

Then on the client side, you can log into your home machine securely, with your normal login credentials, with

[LIST]
[*]sshfs (clients available for Linux and Windows), and locally mount any remote directory your remote user has access to.
[*]an SFTP client like Filezilla, and drag and drop files in an Explorer/Nautilis style shell
[*]an NX client, providing a Remote Desktop kind of experience (NX server software also required at home, I think)
[/LIST]
If your home computer is behind a router, then with default settings, you'll need to forward port 22 to it.

---

### Post by cipherboy_loc on 2011-01-02
Openssh-server does not start its self at boot time. To autostart it:
```
sudo update-rc.d ssh defaults
```
This will add ssh to the default run levels.

Depending on how advanced you would rate yourself, you could also tunnel something like FTP (everybody), Samba (Windows mainly), or NFS (Linux only) over that SSH tunnel, for an added layer of security.


Cipherboy

> **noah++ said:**
> What you want to do is pretty common, and it's one of those nice things that's easier to accomplish when the home server is running Linux as opposed to Windows.

Install the **openssh-server** package on your home machine. I believe once you install it, it starts itself, and configures itself to start at boot.

Then on the client side, you can log into your home machine securely, with your normal login credentials, with

[LIST]
[*]sshfs (clients available for Linux and Windows), and locally mount any remote directory your remote user has access to.
[*]an SFTP client like Filezilla, and drag and drop files in an Explorer/Nautilis style shell
[*]an NX client, providing a Remote Desktop kind of experience (NX server software also required at home, I think)
[/LIST]
If your home computer is behind a router, then with default settings, you'll need to forward port 22 to it.

---

### Post by noah++ on 2011-01-02
I just checked, and it is starting automatically for me in Maverick. As security-insane as I think it is, that means I have been letting it starting at boot time ever since I installed it. YMMV.

---

### Post by rmausser on 2011-01-02
You guys are AWESOME!!

How would I setup Samba to tunnel over SSH?

Keep in mind the client computer will be both another Ubuntu computer and sometimes Windows 7 PC's.

Thanks again!

---

### Post by HermanAB on 2011-01-02
Howdy,

Use SSH to forward port 445 to tunnel Samba.

---

### Post by b0b138 on 2011-01-02
Another option is to setup a vpn server either on your computer or on your router if it has that option. I used to run pptp on my linksys router. Very easy and windows can connect without having to have other software (like for ssh)

---

### Post by cipherboy_loc on 2011-01-02
> **HermanAB said:**
> Howdy,

Use SSH to forward port 445 to tunnel Samba.


If you do not know how to do that, [here]("http://www.linuxhorizon.ro/ssh-tunnel.html") is a good tutorial on that sort of thig, which can be easily modified to work for samba.


Cipherboy

---

### Post by perspectoff on 2011-01-03
> **cipherboy_loc said:**
> If you do not know how to do that, [here]("http://www.linuxhorizon.ro/ssh-tunnel.html") is a good tutorial on that sort of thig, which can be easily modified to work for samba.


Cipherboy

Tutorial says localports under 1024 can only be forwarded by root. That's not true. If it were, you couldn't forward port 445. Other errors in tutorial?

---

### Post by rmausser on 2011-01-03
> **b0b138 said:**
> Another option is to setup a vpn server either on your computer or on your router if it has that option. I used to run pptp on my linksys router. Very easy and windows can connect without having to have other software (like for ssh)

Is there any tutorials on how to do this?

Thanks!

---

### Post by msandoy on 2011-01-03
The most secure way of doing what you want with both windows and linux clients, is to use SSH server and install filezilla on windows clients. It can connect to ssh servers. Use sshfs on linux clients. Works like a charm, and it is secure.

Just make sure you have a properly secure password, since using keys might be problematic if you move between different computers.

---

### Post by perspectoff on 2011-01-06
I agree with all of the above. OpenVPN is good, as is OpenSSH, and especially vsftpd or proftpd FTP servers with FileZilla.

My recent favourite, though, are WebDAV folders served through Apache, which not only can be accessed by almost any browser, but also by nearly all File Manager programs on any OS. Plus, IME very few system administrators blocks HTTP, so it can be used in spite of firewalls, etc.

I love it.

My current instructions for WebDAV are at

Ubuntuguide.org:
[http://ubuntuguide.org/wiki/U_WebDAV](http://ubuntuguide.org/wiki/U_WebDAV)

or 

Kubuntuguide.org:
[http://kubuntuguide.org/K_WebDAV](http://kubuntuguide.org/K_WebDAV)

---

