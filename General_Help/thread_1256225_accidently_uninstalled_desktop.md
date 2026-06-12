---
title: "accidently uninstalled desktop"
date: 2009-09-02
forum: General Help
---

### Post by elfinkind on 2009-09-02
Ok, I admit I'm a relatively new user.

I further admit that I'm an idiot.

With that, let me state that I wanted to uninstall firefox 2.0 and replace it with 3.5. I believe I got 3.5 installed, but I couldn't find it, and every time I opened firefox it was the old version, which I can't stand. 

So, I got smart and went to synaptic and tried to uninstall firefox completely so I could start over with only 3.5. 

Turns out I managed to uninstall the desktop with it. Firefix is built in? Now I only have command line functionality.

I am NOT a command line commando!

I have tried sudo apt-get install ubuntu-desktop to no avail.

I tried sudo apt-get -f install ubuntu-desktop, also to no avail.

I see that it is telling me that it can't resolve the archive site for the items it needs.

Can someone tell me what I am doing wrong? I can and will completely re-install ubuntu if needed, but I would rather learn how to fix this for future reference.

Thanks for any help!

---

### Post by NightwishFan on 2009-09-02
What version of Ubuntu do you have? You may have gutsy or feisty if you have Firefox 2. Both are not supported any longer.

To check which version you have, type this in a terminal.
```
lsb_release -a
```

Then get back to me.

---

### Post by elfinkind on 2009-09-02
I have version 9.04, codename jaunty. I just got it and installed it three days ago. 

Also, that command returned the following:

No LSB modules are available.

Not sure if that is significant or not...

---

### Post by NightwishFan on 2009-09-02
Try this command:
```
sudo apt-get update
```

See if it updates, if not, then try to use dpkg in Recovery Mode. To boot into recovery mode you have to choose it during startup.

---

### Post by elfinkind on 2009-09-02
I have tried that, also to no avail. Upgrade does nothing. I keep getting the error that the archive could not be resolved.

dpkg didn't help. I really screwed this up big!

---

### Post by NightwishFan on 2009-09-02
Hold on. Just relax. I should be around for 20 more minutes, which may be enough to fix your problem, or get more help.

We may be able to fix your problem by editing the apt sources. Please tell me the exact error line that apt update reports. If you can get to a command line I can likely help you.

---

### Post by oldos2er on 2009-09-02
> **elfinkind said:**
> I have tried that, also to no avail. Upgrade does nothing. I keep getting the error that the archive could not be resolved.
 

 Have you tried different servers? System, Administration, Software Sources, click the drop-down menu next to Download from:, Other, Select Best Server.

 Edit: ubuntu-desktop is a metapackage; its removal shouldn't affect your system in any way (unless you upgrade to a newer distro).

---

### Post by NightwishFan on 2009-09-02
I would suggest the same, though the user says they have only command line, so I will walk them through editing the sources.list. I have to leave soon, so if you can do so that would be excellent.

---

### Post by credobyte on 2009-09-02
> **oldos2er said:**
> Have you tried different servers? System, Administration, Software Sources, click the drop-down menu next to Download from:, Other, Select Best Server.

 Edit: ubuntu-desktop is a metapackage; its removal shouldn't affect your system in any way (unless you upgrade to a newer distro).

How he could do that from CLI ? :P


Post the output of:
```
cat /etc/apt/sources.list
```

---

### Post by elfinkind on 2009-09-02
I'm not sure what you mean; I'm stuck with command line only, no GUI that I can detect, therefore no drop-down menu. 

The following appears multiple times when I run sudo apt-get update:

W: Failed to fetch (URLs here) Could not resolve (different ones here, including us.archive.ubuntu.com and security.ubuntu.com)

Also, I get:

W: Some index files failed to download, they have been ignored, or old ones used instead.

And:

W: You may want to run apt-get update to correct these problems.

I don't understand that last one, since I just ran update, but there it is.

And I am not panicked or upset. I'm actually laughing, as I put this install on an old drive to play with it. I'm trying to learn, not worried about losing anything. Like I said, if I can't get this resolved, I'll simply re-install Ubuntu and be done with it. I would rather learn what I did wrong and/or how to fix it, but I'm not hung on this in any way.

I appreciate the help!

---

### Post by elfinkind on 2009-09-02
> **credobyte said:**
> How he could do that from CLI ? :P


Post the output of:
```
cat /etc/apt/sources.list
```

I understand that the hash mark means it doesn't actually look at these sites, but I include them anyway.

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
#deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

Then there are these:

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse

There was more at the top, but it scrolled so stinking fast that I couldn't catch it all. I *think* it was all preceded by hash marks, so wasn't important, but not 100% sure.

---

### Post by credobyte on 2009-09-02
Try ( it'll download and replace your soruces list with mine - don't worry, it'll backup yours as well ) this:
```
sudo cp /etc/apt/sources.list $HOME/.sources.list && wget http://linosun.id.lv/sources.list && sudo mv sources.list /etc/apt && sudo apt-get update && sudo apt-get install ubuntu-desktop

```

---

### Post by oldos2er on 2009-09-02
> **elfinkind said:**
> I'm not sure what you mean; I'm stuck with command line only

 I missed that--my bad.

---

### Post by elfinkind on 2009-09-02
Ok, it looks like I am just straight up not able to resolve web addresses. 

I got the following:

Resolving linosun.id.lv... failed: Name or service not known. wget:unable to resolve host address 'linosun.id.lv

Would something I did when I uninstalled everything make it so I am no longer properly hooked to the internet?

---

### Post by fluffman86 on 2009-09-02
are you sure you're connected to the internet?

```
ping -c 4 yahoo.com
```

---

### Post by elfinkind on 2009-09-02
How can I put my system online from CLI?

---

### Post by elfinkind on 2009-09-02
ping: unknown host yahoo.com

---

### Post by fluffman86 on 2009-09-02
Ok, you definitely aren't online.  

Plug into an ethernet cable and try the ping again

---

### Post by elfinkind on 2009-09-02
I am already plugged into an ethernet cable. I had this machine online before I got happy and screwed everything up. I never unplugged it. I used sudo ifconfig eth0 up just now, then used ifconfig to check it. I am definitely not online, and don't know for sure why. I think I just need to get the install CD out and redo this install from scratch. 

I will wait for more, but that's where I'm thinking I need to go.

---

### Post by credobyte on 2009-09-02
:: Never mind ::

Looks like you've screwed up .. I would simply re-install ( faster an easier than pulling your hair out while trying to fix these problems ) - just don't forget to backup your data ( USB ? ).

---

### Post by elfinkind on 2009-09-02
I love it! I FUBAR'd my computer! 

I figured this would turn out to be the case, and have been prepared to do exactly that pending any momentous input from those who know more than I ever will...

I didn't have anything on that system that needed to be backed up, so I'm running the re-install now. 

Can anyone tell me how to work the old firefox off of this install (9.04), and replace it with the latest version?

And thank you all so much for trying - I am, as usual, beyond salvation...

---

### Post by fluffman86 on 2009-09-02
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa) should have all the info you need.

---

