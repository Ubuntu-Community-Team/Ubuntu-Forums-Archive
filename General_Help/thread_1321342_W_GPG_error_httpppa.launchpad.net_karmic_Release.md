---
title: "W: GPG error: http://ppa.launchpad.net karmic Release:"
date: 2009-11-10
forum: General Help
---

### Post by slugicide on 2009-11-10
I keep getting this. Since this was part of the default install, shouldn't it be correct?


W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 90345E8D2FEF0CE2

---

### Post by MelDJ on 2009-11-10
try the link in my sig

---

### Post by Transmutable on 2009-12-04
I've been through the usual links a couple of times, but for the life of me I cannot find the pub key for [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release

It's been driving me nuts! I just want to watch a @#$% DVD! I've got all the right packages installed, I just can't update.

ETA: Naturally, the second I post, my problem is somehow mysteriously solved. TM:0, Ubuntu Magic: 1.

---

### Post by Artologic on 2009-12-07
I still have the problem noted above :-(

---

### Post by MelDJ on 2009-12-07
tried the link in my sig?

---

### Post by vskram21 on 2009-12-07
i too have the same problem how can i solve this error message is

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7A5579BA519AE6BB
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by snowpine on 2009-12-07
> **vskram21 said:**
> i too have the same problem how can i solve this error message is

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7A5579BA519AE6BB
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

You can only have one package manager open at a time. Quit any other package management applications (Synaptic, Add/Remove Programs, apt-get in a terminal, etc) that are running.

launchpad.net is not part of the default Ubuntu sources list. Don't add anything to your sources list unless you understand the reason why, are willing to accept the risks, and you know how to add the key. (MelDJ had the answer back in post #2... didn't anyone click the link???)

---

### Post by MooseDog on 2010-01-01
found an easy, terminal-based solution:

starting with your output (from OP above):

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 90345E8D2FEF0CE2

copy-n-paste the following into your terminal:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4E5E17B5
```

except, stop! don't hit enter quite yet.  do you see the last 8 characters in your original terminal output?  in our demo here it's: *2FEF0CE2*, yours will be what it is.

copy that over the last 8 character string in the command above.

then! hit enter, then update and happiness ensues.

---

### Post by besweeet on 2010-01-14
I can't seem to do what you just mentioned. I can't get a connection to keyserver.ubuntu.com............. I need to get this going to I can install the Broadcom drivers for Ubuntu in ChromeOS so I can see if I can get this working on my MacBook Pro.

---

### Post by pmulgaonkar on 2010-01-14
I am having similar problems. I get a "keyserver timed out" message from gpg.

Maybe the keyserver is down.

--p

---

### Post by besweeet on 2010-01-14
I just tried it. It seems to be working now :).

---

### Post by WylieE on 2010-06-25
> **MooseDog said:**
> found an easy, terminal-based solution:

starting with your output (from OP above):



copy-n-paste the following into your terminal:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4E5E17B5
```

except, stop! don't hit enter quite yet.  do you see the last 8 characters in your original terminal output?  in our demo here it's: *2FEF0CE2*, yours will be what it is.

copy that over the last 8 character string in the command above.

then! hit enter, then update and happiness ensues.

THANK YOU! THANK YOU!  THANK YOU!  
I appreciate you writing out this solution, which worked perfectly for me.
I could not try the link in the sig, since part of my problem is that I could not watch videos till I fixed this.

---

### Post by Neobuntu on 2010-07-08
Run your..
> 
sudo apt-get update
...and note the number at the end, of this error.

Copy and Paste that into a terminal and then press your "Home" key to take it to the beginning of the line.

Now copy and paste (right click menu) those commands,
> sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com
 except for the example number. Make sure there's a space before your found number and hit Enter.

Do another update and you should have no more error.

---

### Post by solsen300 on 2010-10-11
When I run that command I get the below.


Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 6E871C4A881574DE
gpg: requesting key 881574DE from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

---

### Post by rps63ifid on 2010-10-11
I'm seeing the same error here this afternoon, trying to update my 10.10 box. I can open a browser session to keyserver.ubuntu.com, but the apt-add command fails on the two keys that seem to be causing problems on my box:

[http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release
[http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release

---

### Post by opiumpoetry on 2011-03-13
> **MooseDog said:**
> found an easy, terminal-based solution:

starting with your output (from OP above):



copy-n-paste the following into your terminal:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4E5E17B5
```

except, stop! don't hit enter quite yet.  do you see the last 8 characters in your original terminal output?  in our demo here it's: *2FEF0CE2*, yours will be what it is.

copy that over the last 8 character string in the command above.

then! hit enter, then update and happiness ensues.

worked for me 2. thanx.

---

