---
title: "Help with server please."
date: 2011-05-09
forum: General Help
---

### Post by Chris230201 on 2011-05-09
Hello. 
first of all i would like to say hi, im Chris and im a new member to this forum. i hope im able to get all the info i need. please bear with any noobness on my part, i apologise in advance.

so what i want is a server to store mostly videos and i want to be able to access those movies for playback on mac, linux, windows, and xbox computers on my home network. basically a network HDD as opposed to the USB method that im stuck with now. on an apple forum ubuntu server edition was suggested to me as a solution. so i downloaded and installed ubuntu server on the machine i wish to use. but now im stuck, what next? have i even gone down the correct route?

one more thing to add; if possible can i also have a setup in which i can connect to my server via a web browser form a network other than my own?

im looking forward to any help and suggestions. also remember im a novice so try and go easy.

Thanks
Chris.

---

### Post by bodhi.zazen on 2011-05-09
You probably want to set up Samba.

[https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide)

Most of setting up Samba is editing a file, use nano, and read the manual section.

```
sudo nano -B /etc/samba/smb.conf
```

The -B option makes a backup, /etc/samba/smb.conf~

For your web server, you need to port forward (port 80)from your router to you web server. The details vary by router.

---

### Post by Chris230201 on 2011-05-09
> **bodhi.zazen said:**
> You probably want to set up Samba.

[https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide)

Most of setting up Samba is editing a file, use nano, and read the manual section.

```
sudo nano -B /etc/samba/smb.conf
```

The -B option makes a backup, /etc/samba/smb.conf~

For your web server, you need to port forward (port 80)from your router to you web server. The details vary by router.

Thanks for the quick reply man!
Ok so shall i start following that manual? it's important that it works cross platform.

---

### Post by BertN45 on 2011-05-09
The easy windows-like way is to open nautilus, go to the video directory, right click it and choose "Sharing options".

Your request wit respect to access over the internet is more complex. You need to know your external IP address which will look like xxx.xxx.xxx.xxx and the xxx is a number between 1 and 254. That number is changed by your ISP frequently. On top of that you have to change your router settings and do port forwarding. I would not use port 80, because it would  mess up your other browsing. I would use another port not in use yet. But you would have to supply the port number too when using the browser. You also have to think about security, because everybody can enter your network. So you should consider to use a VPN connection  (virtual private network).

In the past I circumvented all those problems by installing a peer-to-peer VPN. The name is "Logmein Hamachi". It allows you to create a kind of home network over the internet. I used it both for Windows and Ubuntu machines. It is reliable and offers good security, all  transfers are encrypted. You can do anything that you can do on the LAN over the Internet. I used it to share my network drives and to remotely control my desktop and file server at home in Santiago  from Europe. There are also Mac versions available and the Ubuntu one is in the Lab and Beta tab of the home page, take the .deb file and simply double click on it.

---

### Post by BertN45 on 2011-05-09
Check your Internet speed first using: [http://www.speedtest.net/](http://www.speedtest.net/) 
If you want to play your movies remotely you will need around 1.5 mbps **upload** speed minimal., based on my m4v compressed movies If you have HD video it will be more.

You might have to reduce your video resolution to accommodate your upload speed.

---

### Post by Chris230201 on 2011-05-11
sorry guys im really lost here.
so if i simply right click on a folder and share it, everything on my network will see it? it needs to work on mac's, linux, windows and my xbox 360. as soon as i get the home sharing working i will look into accessing my server over the internet. i only mention it now as i thought i best incase someone suggests i go down a route that would mean i cant access my files over the internet.

Thanks

---

### Post by bodhi.zazen on 2011-05-11
If you want to access files over the internet I highly suggest ssh.

ssh + keys + disable authentication.

On Linux you would use sshfs

On windows you would use winscp

Not sure about your other platforms, but neither samba or nfs are secure enough for access over the internet.

---

