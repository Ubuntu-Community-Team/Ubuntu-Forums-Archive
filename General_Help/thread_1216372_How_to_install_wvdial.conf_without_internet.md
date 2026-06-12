---
title: "How to install wvdial.conf without internet???"
date: 2009-07-18
forum: General Help
---

### Post by charanpreethu on 2009-07-18
Hi,
    I am using Mint Gloria.I Have windows Xp also in my system.
Internet doesnot work in Mint,in order to make it work I should download wvdial.conf and edit it,but without internet how can I download it and edit it.Internet works in windows xp.Is there any way to download it in xp and edit it in mint????

---

### Post by t0p on 2009-07-18
**1** Check if **wvdial** is already installed.  You do this by typing into the terminal:

```
which wvdial
```

If it's installed, you'll get a reply like

```
/usr/bin/wvdial
```

If it's there, go to step 4. If it's not there, you need to install it.  Go to Step 2.

**2**  You need to go to a computer with working internet connection.  It doesn't matter which OS it's running.  Go to [packages.ubuntu.com]("http://packages.ubuntu.com").  Search for **wvdial** - remember to search for the version to go with your version of Ubuntu (hardy, intrepid, jaunty).  Save it to removable medium - CD-RW, usb stick, etc).  Take it home.

**3**  Put the package onto your Desktop.  Install it (Right-click the .deb and select to Install).  Once it's installed, go to step 4.

**4**  Make sure your modem is plugged in.  Type into the terminal

```
sudo wvdialconf
```

The program will scan the system for modems.  It will create the file /etc/wvdial.conf and write the relevant info to it.  Now you can edit /etc/wvdial.conf.  You'll need to have admin privs to do that, so you'll need to run an editor as root - hit **Alt+F2** and type into the box that appears:

```
sudo gedit /etc/wvdial.conf
```

Edit the file as required.

---

### Post by charanpreethu on 2009-07-18
Thanks for the reply.I will try it now.

---

### Post by charanpreethu on 2009-07-18
I downloaded the package and tried to install but i got these errors

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/x/xplc/libxplc0.3.13_0.3.13-1build1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xplc/libxplc0.3.13_0.3.13-1build1_i386.deb) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libwvstreams4.4-base_4.4.1-0.2ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libwvstreams4.4-base_4.4.1-0.2ubuntu2_i386.deb) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libwvstreams4.4-extras_4.4.1-0.2ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libwvstreams4.4-extras_4.4.1-0.2ubuntu2_i386.deb) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libuniconf4.4_4.4.1-0.2ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libuniconf4.4_4.4.1-0.2ubuntu2_i386.deb) Could not resolve 'archive.ubuntu.com'

---

### Post by t0p on 2009-07-19
Hmm. looks like there are dependencies (programs that wvdial needs in order to work), and the installer is trying to download them.  The computer has no internet access, so the download fails.

The only thing I can suggest is you return to packages.ubuntu.com and get the packages that the installer is trying to get.  Problem is, those packages may have dependencies of their own - then you'll need to manually download *them* and so on...

This is what we call **dependency hell** - a vicious circle that's very difficult to bust out of.  It'd make your life a whole lot better if you could get internet access for your machine. Maybe use a cellphone or something... (check my sig for a link to a tut on using a cellphone to connect to the internet)

Oh yes, one other thing.  I told you to get the package 'wvdial' from packages.ubuntu.com.  I think you may also need to get **'wvdialconf'** - I can't remember if it comes packages with wvdial or if you need to get it separately. Best to search for it, just in case.

---

### Post by KeyserSoze93 on 2009-07-19
can you download the wvdial.conf to Windows My Documents or where ever and the copy it from you windows partition with Ubuntu?

---

