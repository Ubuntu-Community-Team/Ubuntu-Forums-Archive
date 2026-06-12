---
title: "help with public key signatures?"
date: 2009-07-01
forum: General Help
---

### Post by Grock1722 on 2009-07-01
Hello All-

Good Lord do I love Ubuntu.

When I update programs and use Synaptic, I receive an error that says:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

I have searched around and found various ...solutions... to this situation, but not on my os, Jaunty.  Could someone here show me how to fix this?  Or point me towards where I need to be searching?

Thanks so much for your help,
G

---

### Post by drs305 on 2009-07-01
If you run this it should import the correct key:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2EBC26B60C5A2783

```

---

### Post by Grock1722 on 2009-07-01
Perfect.  

I believe I owe you a cigar.

---

### Post by drs305 on 2009-07-01
> **Grock1722 said:**
> Perfect.  

I believe I owe you a cigar.


I didn't notice the post count. Welcome to the Ubuntu forums!

I'll bring the cognac... :p

---

### Post by colloid on 2009-07-01
To: drs305

**When I start to run the update manager I got error message:**

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220

[COLOR=SeaGreen]**Question 1:**[/COLOR] What is that number "6AF0E1940624A220" at the end of that error message?


[B]Next, I did as you suggested. In a terminal I did:

[/B]eric4@notebook-A:~$ **sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6AF0E1940624A220**
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 6AF0E1940624A220
gpg: requesting key 0624A220 from hkp server keyserver.ubuntu.com
gpgkeys:** HTTP fetch error 7: couldn't connect to host**
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
eric4@notebook-A:~$ 


[COLOR=SeaGreen]**Question 2:** [COLOR=Black]As you can see I got: [/COLOR][/COLOR]HTTP fetch error 7: couldn't connect to host[COLOR=SeaGreen]. [COLOR=Black]Can any body tell me what this is about? (Note: I am well connected to the internet. My browser **is finding** and communicating with [http://keyserver.ubuntu.com](http://keyserver.ubuntu.com))

Bye.

[/COLOR][/COLOR]

---

### Post by drs305 on 2009-07-01
colloid,

the server appears to be down at the moment, which is why you can use the internet but not connect to this specific site. i used it a few hours ago when i made the post and the site and command were both working at that time. give it a bit and try again.

A few months ago launchpad started requiring keys to help guarantee the security of the packages you download. You have to have the 'public key' to verify downloads from the launchpad repositories. That's what the command does - puts the key into your system.

Launchpad sent this to repository maintainers a few months ago:

> Every PPA now has its own unique key, which Launchpad uses to 
sign the packages it builds in the archive.

People downloading a package from your PPA can now verify that it
hasn't been altered since Launchpad built it.

You can find out how to add the PPA key to your Ubuntu system 
here:

[https://help.launchpad.net/PPAKeys](https://help.launchpad.net/PPAKeys)


By the way, in the time it took to write this the server is back up and should be working for you. :-)

---

