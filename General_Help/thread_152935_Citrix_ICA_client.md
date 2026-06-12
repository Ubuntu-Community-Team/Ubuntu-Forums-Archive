---
title: "Citrix ICA client"
date: 2006-03-30
forum: General Help
---

### Post by gregleimbeck on 2006-03-30
I am trying to get Citrix to work on kubuntu, so I installed the ICA client.  When I login to the NFuse gateway, and click on one of the published apps, it tries to open launch.ica, but I don't have ICA files associated with anything yet.  

I try to point it to /usr/lib/ICAClient/wfica to open the file, but it doesn't do anything.  There must be something simple I am missing (be gentle - I know next to nothing about Linux)

TIA

---

### Post by dpack on 2006-03-30
It sounds like FireFox did not get the ICA plugin. When you install the ICA Client for Linux you must install it with root privileges to have it install the browser plug-in. Download the Admin Guide here and jump down to page 23 for instructions.

[http://support.citrix.com/kb/entry.jspa?externalID=CTX101298](http://support.citrix.com/kb/entry.jspa?externalID=CTX101298)

---

### Post by gregleimbeck on 2006-03-30
I will give that a try...but I know the ICA client isn't working because at this point I am just saving the .ica file and trying to open it with wfica.

---

### Post by gregleimbeck on 2006-03-30
You were right on - I found this and followed it verbatim and its working now!  Thanks!

1. Download Citrix 9.0 client for Linux (RPM version):
[http://www.citrix.com/site/SS/downloads/details.asp?dID=2755&downloadID=3323#top](http://www.citrix.com/site/SS/downloads/details.asp?dID=2755&downloadID=3323#top)

2. Install addtional libraries:
apt-get install libxaw6 libmotif3
3. Link libXm.so.3 so wfcmgr.bin can see it (bug in Citrix client):
ln -s /usr/X11R6/lib/libXm.so.3 /usr/lib/libXm.so.3
4. Convert .rpm to .deb using alien command:
sudo alien ICAClient-9.0-1.i386.rpm
5. Install newly created icaclient_9.0-2_i386.deb file:
sudo dpkg -i icaclient_9.0-2_i386.deb
6. Copy over plugins for Firefox/Mozilla:
sudo ln -s /usr/lib/ICAClient/npica.so /usr/lib/mozilla/plugins/npica.so
sudo ln -s /usr/lib/ICAClient/npica.so /usr/lib/mozilla-firefox/plugins/npica.so

You may have to do the following if using older Citrix Server
1. Configure ICAClient:
sudo /usr/lib/ICAClient/wfcmgr -icaroot /usr/lib/ICAClient
2. Goto the Tools menu and choose settings.

3. Select Server Location from the selection bar.

4. Goto Network Protocol selection bar and change it to TCP/IP and click the Apply button.

---

### Post by dpack on 2006-03-31
That was a lot more complicated than what I had to do! This is how easy it was for me.

1. Downloaded the ICA Client for Linux in .tar.gz format: [http://www.citrix.com/English/SS/downloads/details.asp?dID=2755&downloadID=3323&pID=186](http://www.citrix.com/English/SS/downloads/details.asp?dID=2755&downloadID=3323&pID=186)
2. Extracted the contents of the .tar.gz
3. In Terminal: sudo ./setupwfc
4. Selected 1 to install
5. Accepted the default path
6. Confirmed I wished to proceed
7. Accepted the License Agreement
8. Then exited after install.

That gave me the ICA FireFox plugin I needed for NFUSE. If I needed Program Neighborhood then I simply need to add the following:
1. sudo apt-get install libxaw6 libmotif3
2. sudo ln –s /usr/X11R6/lib/libXm.so.3 /usr/lib/libXm.so.3

Then I'd be finished! But I did have to work with getting a certificate installed for NFUSE, but that is another matter. Glad you got it though!

---

### Post by GazzaK on 2006-04-28
dpack - running the install as per your post, I get this on the very last command:

```
sudo ln &#8211;s /usr/X11R6/lib/libXm.so.3 /usr/lib/libXm.so.3/
ln: when making multiple links, last argument must be a directory
```

Any ideas?

Edit - Got this working now, don't know why it would not run the first time?

---

### Post by GazzaK on 2006-04-28
[QUOTE=dpack]But I did have to work with getting a certificate installed for NFUSE, but that is another matter. Glad you got it though![/QUOTE]

Can you also offer any help at all on how you installed this certificate, as I have the exact same problem

---

### Post by redevil34 on 2007-04-28
> **GazzaK said:**
> dpack - running the install as per your post, I get this on the very last command:

```
sudo ln –s /usr/X11R6/lib/libXm.so.3 /usr/lib/libXm.so.3/
ln: when making multiple links, last argument must be a directory
```

Any ideas?

Edit - Got this working now, don't know why it would not run the first time?

I'm stuck at the same point.  Do you actually have this directory?

---

