---
title: "Problem with rapidshare and aria2c"
date: 2011-03-02
forum: General Help
---

### Post by IvoP123 on 2011-03-02
aria2c is the best rapidshare downloader for linux IMHO, but it seems that not many people use it. Is there anyone here who downloads rapidshare links with this program?
Everything was working fine until 3 days ago when i get this error for every rapidshare link i try to download:

2011-03-02 13:58:15.536249 ERROR - CUID#80 - Download aborted. URI=[http://rapidshare.com/files/347330033/c-hnts.part74.rar](http://rapidshare.com/files/347330033/c-hnts.part74.rar)
Exception: [AbstractCommand.cc:265] errorCode=1 URI=https[://rs738l35.rapidshare.com/files/347330033/c-hnts.part74.rar]("http://ubuntuforums.org/://rs738l35.rapidshare.com/files/347330033/c-hnts.part74.rar")
  -> [InitiateConnectionCommandFactory.cc:85] errorCode=1 https is not supported yet.

Is there anyone who can help please? :-|

---

### Post by Jose Catre-Vandis on 2011-03-02
Are you using a script,and including login info? Here's mine that I used to use:
```
#!/bin/bash
aria2c --http-user=12345 --http-passwd=9876543 -i /home/jose/rsurls -j 1 -s 1 -d /home/jose
```
where rsurls is a text file containing links. 

I haven't used rapidshare like this for some time, and they have changed things around a bit.

---

### Post by IvoP123 on 2011-03-02
> **Jose Catre-Vandis said:**
> Are you using a script,and including login info? Here's mine that I used to use:
```
#!/bin/bash
aria2c --http-user=12345 --http-passwd=9876543 -i /home/jose/rsurls -j 1 -s 1 -d /home/jose
```where rsurls is a text file containing links. 

I haven't used rapidshare like this for some time, and they have changed things around a bit.

i use login information in aria2.conf file which is located in ~/.aria2/ folder and it worked for some time and it stopped working 3 days ago...

---

### Post by Kalden on 2011-03-07
Aria2c doesn't work here either.
I noticed rapidshare changes the url from http into https.
According to man aria2c you can specify a https-proxy-user and https-proxy-passwd. In that case you need also a https proxy.
However I don't know what that is.

---

### Post by IvoP123 on 2011-03-07
> **Kalden said:**
> Aria2c doesn't work here either.
I noticed rapidshare changes the url from http into https.
According to man aria2c you can specify a https-proxy-user and https-proxy-passwd. In that case you need also a https proxy.
However I don't know what that is.

i really hope that someone does :)
i wrote my own script using aria2c and would really like to make this work

---

### Post by luigi_mb on 2011-03-07
aria2c from the repos is v1.8.0, but the most recent release is v1.10.9. You could try to uninstall the repo version, get the source of the new release, build and install it. That's what I did. It _may_ solve your problem.

/luigi

---

### Post by Cpierce on 2011-03-07
I use jdownloader, and it has worked well for me.

---

### Post by IvoP123 on 2011-03-08
> **Cpierce said:**
> I use jdownloader, and it has worked well for me.

I don't like it. Uses much resources. I also wrote script to extract downloaded files so jdownloader doesn't really have anything that would make me use it. unfortunately, i use it now cause aria2 doesn't work

> **luigi_mb said:**
> aria2c from the repos is v1.8.0, but the most  recent release is v1.10.9. You could try to uninstall the repo version,  get the source of the new release, build and install it. That's what I  did. It _may_ solve your problem.
/luigi

i already done that. 1.10.9 doesn't work either :(

---

### Post by IvoP123 on 2011-03-19
If anyone is interested... Problem solved with aria2c version 1.11.0 :P
So... this thread is marked solved now

---

