---
title: "Public folder and SSH security"
date: 2012-10-14
forum: General Help
---

### Post by Azrael84 on 2012-10-14
Is it possible to share folder (e.g. the Public folder) on a network without SSH?
I've done this following a guide that involved installed openSSH and it works really well, but I am just worried about security vulnerabilities. I just want to share the one folder rather than be able to PuTTY into the computer etc.

If not is there a way I can secure the openSSH?

---

### Post by JRV on 2012-10-14
Have you tried SFTP:
```

nautilus sftp://USER@HOSTNAME/home/USER/Public

```

---

### Post by Lars Noodén on 2012-10-14
To add to JRV's client-side suggestion, on the server side of things you can disable shell login for all or a few of the users by forcing an SFTP session.  It's very easy.

There are dozens of tutorials around on how to make your SSH sessions SFTP-only. Here is one to get started with.

[http://www.howtoforge.com/setting-up-sftp-in-a-hurry-for-file-uploads](http://www.howtoforge.com/setting-up-sftp-in-a-hurry-for-file-uploads)

---

### Post by HermanAB on 2012-10-14
Another age old trick to secure a FTP server (any type), is to separate the upload and download directories.  That way, only the admin can move files from the upload side of things to the download side of things, thus preventing mischief.

---

### Post by rizzeh on 2012-10-14
If you happen to have Python installed and need quickly to share a folder:
```
python -m SimpleHTTPServer
```
[http://www.linuxjournal.com/content/tech-tip-really-simple-http-server-python]("http://www.linuxjournal.com/content/tech-tip-really-simple-http-server-python")

---

### Post by robtygart on 2012-10-14
> **rizzeh said:**
> If you happen to have Python installed and need quickly to share a folder:
```
python -m SimpleHTTPServer
```
[http://www.linuxjournal.com/content/tech-tip-really-simple-http-server-python]("http://www.linuxjournal.com/content/tech-tip-really-simple-http-server-python")

Very cool, thank you for posting this. I just started playing with SSH so I got to remotly login and then share some files I wanted off that computer.

---

### Post by Habitual on 2012-10-15
> **rizzeh said:**
> If you happen to have Python installed and need quickly to share a folder:
```
python -m SimpleHTTPServer
```[http://www.linuxjournal.com/content/tech-tip-really-simple-http-server-python](http://www.linuxjournal.com/content/tech-tip-really-simple-http-server-python)

Security Advice:
Do make a sub-directory and place any files that you wish to share in it and run the python code **from that directory**.

---

### Post by robtygart on 2012-10-15
Question? If your going to run python SimpleHTTPServer. Does running App-Armor help at all?

---

### Post by Azrael84 on 2012-10-16
thanks for all the replies

---

### Post by rizzeh on 2012-10-17
> **robtygart said:**
> Question? If your going to run python SimpleHTTPServer. Does running App-Armor help at all?

There is a package for it, however i would rather use python server as a quick and dirty solution to share files over local network and wouldn't permanently run it. 

[http://packages.ubuntu.com/precise/python-libapparmor](http://packages.ubuntu.com/precise/python-libapparmor)

---

### Post by robtygart on 2012-10-17
> **rizzeh said:**
> There is a package for it, however i would rather use python server as a quick and dirty solution to share files over local network and wouldn't permanently run it. 

[http://packages.ubuntu.com/precise/python-libapparmor](http://packages.ubuntu.com/precise/python-libapparmor)

Well if your going to have it running for even an hour, I would like to keep my computer secure right? 

With SimpleHTTPServer, its not just LAN, anyone over the internet can too?  


But then again what can they do with out root access?

---

### Post by rizzeh on 2012-10-19
to be exposed to internet ports need to be forwarded, default is 8000. 
otherwise NAT protects, just like any other port that isn't open

---

