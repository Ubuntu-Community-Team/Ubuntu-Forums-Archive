---
title: "gpgkeys: HTTP fetch error 7: couldn't connect to hos"
date: 2010-03-24
forum: General Help
---

### Post by Almeida1 on 2010-03-24
When I run sudo apt-get update I get the following message at the bottom:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE
W: GPG error: [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) all Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CCC158AFC1289A29
W: GPG error: [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CCC158AFC1289A29

I have tried numerous ways to add the keys i.e:

gpg --keyserver keyserver.ubuntu.com --recv-keys EF4186FE247510BE && gpg --export --armor EF4186FE247510BE | sudo apt-key add -

However, I then get the following message:

gpg: requesting key 247510BE from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

Does anyone know what the problem is and why I cannot connect?

Thanks

---

### Post by Almeida1 on 2010-03-24
I seem to have got rid of the error message by unchecking all sources except the following:

[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)

Therefore, I now have the following unchecked:

[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)
[http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt)
[http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt)
[http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu)

Is this ok or do I need any of these checked??

---

### Post by raywood on 2010-07-11
I used the Ubuntu Sources List Generator to produce the list of commands I needed to enter, in order to enable the repositories I wanted.  I ran those commands.  I got several instances of this pair of errors:

```
gpgkeys: HTTP fetch error 7:  couldn't connect to host
gpg: no valid OpenPGP data found.
```

The desired repositories are listed in Software Sources > Other Software, but not in Software Sources > Authentication.

Suggestions?

---

### Post by approaching on 2010-08-20
I am fairly certain that this has to do with a proxy, though I wish I had something better to say about fixing it. I tried setting both my http_proxy and https_proxy variables in my .bashrc (sourced) to no avail, though that doesn't mean that you shouldn't try that out.
i.e. in .bashrc put in these lines:
```

export http_proxy="my.proxy:port"
export https_proxy="my.proxy:port"

```
I doubt it uses the ftp_proxy, but you can set that too if you have one.

---

### Post by Charidan on 2012-04-24
Where are you checking and unchecking these sources? How do I find that menu?

---

### Post by audiomick on 2012-04-24
I think it should be an entry in the "edit" menu of the software centre called "package sources" or something similar

---

### Post by oldos2er on 2012-04-24
Old thread closed.

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

