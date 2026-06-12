---
title: "Please help with updates"
date: 2009-09-06
forum: General Help
---

### Post by seamles on 2009-09-06
Here is the error I get, 

GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/jaunty/Release](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/jaunty/Release)  Unable to find expected entry  maindeb-src/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

Don't know what to do!

---

### Post by leonardo_neo on 2009-09-06
Try these commands....

> gpg --keyserver subkeys.pgp.net --recv 2EBC26B60C5A2783

Then...

> gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add -

After that..

> sudo apt-get update

I believe this should help....

---

### Post by seamles on 2009-09-06
Thanks for the quick response, 

I still get this error. 

W: Failed to fetch [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/jaunty/Release](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/jaunty/Release)  Unable to find expected entry  maindeb-src/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Bucky Ball on 2009-09-06
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)

Follow that carefully; use the correct code for your release then add the GPG key at the bottom of the other codes.

---

### Post by seamles on 2009-09-06
This community is awesome. Thanks to your response too. 

I did all this and still got this error. 

W: Failed to fetch [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/jaunty/Release](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/jaunty/Release)  Unable to find expected entry  maindeb-src/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.


It's not that big of a deal because everything else works but I thought I'd just check with the great community. I can also just wait until it tells me to update again and see if I get the same problem.

Thanks all

---

### Post by scion xd on 2009-09-06
go to:

$ gksudo gedit /etc/apt/sources.list
find 

deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main

and make them loook like this:


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
[B]deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main[/B]

deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) intrepid release
deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main


I think i had the same problem and foung answwer on ggogle.

---

### Post by seamles on 2009-09-06
Hi Sorry,

I tried to go to that location but couldn't figure it out...

---

### Post by scion xd on 2009-09-06
go to this website it will explain better then i can,

[https://answers.launchpad.net/zgegball-themes/+question/80785](https://answers.launchpad.net/zgegball-themes/+question/80785)

---

### Post by Bucky Ball on 2009-09-06
To get to a terminal:

Applications->Accessories->Terminal

Then copy and paste the code given previously:

```
gksudo gedit /etc/apt/sources.list
```

Find the lines mentioned and change them. If they are comments out with a '#' that would be your problem. Remove the '#' from the beginning of the line if that is the case and try before changing them.

---

### Post by ackanao on 2009-09-06
Then just go through synaptic - goto "Settings -> Repositories" and then select "Third-Party Software" tab; Delete your bisigi ppa's and add these:

deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main

Then import the gpg key:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 881574DE
```

**EDIT**:
*Bucky Ball has beat me to it*

---

### Post by seamles on 2009-09-06
Sweet thank you all! 

I got it,

I just deleted a space from there somehow previously. 

Put it back and it's much better now!

---

### Post by Bucky Ball on 2009-09-06
> **seamles said:**
> Sweet thank you all! 

I got it,

I just deleted a space from there somehow previously. 

Put it back and it's much better now!

Well spotted! Good work ...

---

