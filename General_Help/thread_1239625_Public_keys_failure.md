---
title: "Public keys failure?"
date: 2009-08-13
forum: General Help
---

### Post by Toke on 2009-08-13
When I press reload in synaptic package manager I get this error message.
> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31CCA643CC60BA1F
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B5115B98AA836CA8There is some console command for getting assorted updates, it gives the same error message.
I think it appeared around the time I tried to install Unknown Horizons but are not sure if there are any connection or what they are for. The update manager somehow omits python-fife as well, it's just shaded out.

There is a tread here on how to get a pubkey, it gives me a timeout on server.

Does anyone have any idea of what to do?

---

### Post by michy99 on 2009-08-13
Run this in a terminal:```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CC60BA1F
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AA836CA8
```

---

### Post by Toke on 2009-08-13
> toke@Toke-laptop:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CC60BA1F
[sudo] password for toke: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys CC60BA1F
gpg: requesting key CC60BA1F from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
toke@Toke-laptop:~$ 

I think this is what I found and tried before.
Are there such a thing as invalid keys?

---

### Post by Toke on 2009-08-13
> toke@Toke-laptop:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AA836CA8
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys AA836CA8
gpg: requesting key AA836CA8 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
toke@Toke-laptop:~$ 

Same for the other one.

---

### Post by michy99 on 2009-08-13
It looks like the keyserver is not responding for some reason. What repositories have you added lately? Usually, you can download the key from launchpad and add it manually.

---

### Post by Toke on 2009-08-13
I have added some Third-Party Software locations.

[http://ppa.launchpad.net/nickel62metal/ubuntu/](http://ppa.launchpad.net/nickel62metal/ubuntu/) jaunty main
[http://ppa.launchpad.net/sunab/ppa/ubuntu](http://ppa.launchpad.net/sunab/ppa/ubuntu) jaunty main
[http://deb.unknown-horizons.org/](http://deb.unknown-horizons.org/) release main
WineHQ - Ubuntu 9.04 "jaunty Jackalope"
Medibuntu - Ubuntu 9.04 "jaunty Jackalope" free non-free
Medibuntu (source) - Ubuntu 9.04 "jaunty Jackalope" free non-free (Source Code)

What is launchpad?

---

### Post by michy99 on 2009-08-13
Ok, here is how to add the keys manually. The two ppa's that you need keys for are here:```
https://launchpad.net/~nickel62metal/+archive/ppa
https://launchpad.net/~sunab/+archive/ppa
```Go to the first one and look where it says 'Signing key' Click on the number beside it. On the next page, click on 'CC60BA1F' This is the key.

Select everything except the top bold line and save to a text file. Name it Key1 and save to your desktop.

Go to the second site and do the same thing, but save it as Key2.

Go to System->Administration->Software Sources. Click Authentication tab. Click Import Key File. Choose the Key1 file you saved to your desktop. Do the same for Key2.

---

### Post by Toke on 2009-08-13
It ended with a browser error/timeout.
The error message suggested a busy keyserver or some firewall. 
I have no idea what firewall my connection got, it is through the company head office so it could be anything.

---

### Post by michy99 on 2009-08-13
Yeah, it seems like your firewall may be preventing you from connecting to certain locations. Most companies don't really like employees adding software they don't know about. You can get rid of the error by disabling those repositories.

---

### Post by Toke on 2009-08-13
One of them is for a driver for my laptops webcam but does not support my model, the other is for Kdenlive, a video editor I am not using.
Unticking them in software sources removes the error messages.

---

### Post by Toke on 2009-08-13
Thanks for the help.
My problem seems to be that I am at work for over a month at a time :)

---

### Post by michy99 on 2009-08-13
> **Toke said:**
> Thanks for the help.
My problem seems to be that I am at work for over a month at a time :)

That definitely sounds like a problem.

---

### Post by Toke on 2009-08-13
Well, I do get the same time as vacation (seafarer).

How do I add "fixed" to tread title ?

---

### Post by drysdan on 2009-08-13
Same exact issue here.  Trying to install Chromium in Jaunty.  Keyserver worked fine yesterday.  Today I get the same timeout error.  I tried getting the key manually, but when I click on the link for the key, it times out too...  

I tried keyserver.ubuntu.com on [http://downforeveryoneorjustme.com](http://downforeveryoneorjustme.com), and it said it's down for everyone.  True or not??

---

