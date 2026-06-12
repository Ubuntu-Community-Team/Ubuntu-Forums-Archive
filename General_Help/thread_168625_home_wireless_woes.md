---
title: "home wireless woes"
date: 2006-04-30
forum: General Help
---

### Post by inovermyheadd on 2006-04-30
So, my Dad set up a wireless network at the house protected with basic WEP protection.  He set it up so that you need a passphrase that I guess creates passwords.   

I can't say that I really understand it.

anyhow,

The problem is, when I try to connect via my wireless card I can see the network name in the eth1 config, but it does not give a space to type in a passphrase...just the WEP key, whatever that is.  I tried to type his passphrase into the WEP space, but it asks for either a 5 or 13 character key, depending on if it is a 64 or 128 bit encryption.

Does anyone know what I am talking about?  I honestly barely do...:-D 

Thanks for the help!
Donald

---

### Post by cskeide on 2006-04-30
The passphrase you selected, would create a hexadecimal key. This is the one you need in order to connect. On my wireless router the hex key is visible in the routers web interface. Ask your Dad how he set up the passphrase, and he will most likely be able to show you the hex key you need.

---

### Post by inovermyheadd on 2006-05-01
hey thanks for the help.

I got 4 ten digit codes from my father, and tried them all without success.  

There is a really long code called a network key that he gave me, and it did not work either.

I don't get it.

My university's wireless detects with ease...then all I have to do is put my school username and password into a website that automatically comes up when I open a browser....then all is well.

Is there something else I'm missing?

---

### Post by Jason_25 on 2006-05-01
Your school network is likely unencrypted, and uses a proxy of some kind.  Since your home network is using encryption, you are facing a couple of problems. 

First, is finding out the exact hexadecimal key to use.  It will be probably be 10 or 26 characters long depending on whether it is 40-bit or 128-bit.  Sometimes, there as as many as four in the router.  But only one is the "active" key.  You'll probably want to be on another pc connected to the router to troubleshoot this.

The next problem is that the graphical network tool doesn't work well for encryption.  You can either use the command line tool iwconfig or use network-manager to connect.  Alternatively, you could enter your settings + the key into the /etc/network/interfaces file and restart the /etc/init.d/network script to do the same thing.

---

### Post by inovermyheadd on 2006-05-01
SOLVED

My dad accidently set the network up to only accept a few devices...after he added my computer it works wonderfully

---

### Post by elamericano on 2006-05-01
Glad that worked out for you. To clarify, a 10 digit hexidecimal number is a wep key (40-bits). A passphrase is a string used to derive the actual key. A few venders have phrases for wep, which only works for their products, but most only allow you to enter the wep key directly. You will mostly hear of passphrases with WPA-PSK authentication. That passphrase generates a 256-bit hexadecimal key (64 digits), but the passphrase method has a standard implementation, so you only need to know the passphrase for WPA-PSK.

Long response, but the point was that the passphrase is not the key.

---

