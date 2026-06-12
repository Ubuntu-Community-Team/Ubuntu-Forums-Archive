---
title: "authentication problemz lucid"
date: 2010-07-31
forum: General Help
---

### Post by Scooter_X on 2010-07-31
So I just fresh-installed lucid, can't install anything from the software center, and if I try to apt-get a package or install from the package manager it warns me about a lack of authentication. I've been digging, and I'm wanting to try to see if my 'policykit authentication agent' has a bug. I've read that I should check for it under startup applications and see if my issue lies therein, but I can't even find the dang thing in startup apps! (post # 15 in *[this thread]("http://ubuntuforums.org/showthread.php?t=1393324&highlight=ubuntu+software+center+untrusted+packages")* is where I read that) Anyone know where I can look to check it?

Anyway, not sure if that's gonna fix it or not yet, and if anyone has another suggestion as to what to do, please let me know! Thanks!

---

### Post by JC Cheloven on 2010-07-31
Did you try
```

sudo dpkg-reconfigure -a
``` (?)

You can see [here]("http://manpages.ubuntu.com/manpages/hardy/man8/dpkg-reconfigure.8.html") what this command does.

---

### Post by Scooter_X on 2010-08-01
> **JC Cheloven said:**
> Did you try
```

sudo dpkg-reconfigure -a
``` (?)

You can see [here]("http://manpages.ubuntu.com/manpages/hardy/man8/dpkg-reconfigure.8.html") what this command does.

Ran through the whole thing, got nothing. Still same thing. Bummer.

---

### Post by Scooter_X on 2010-08-01
sudo apt-get update:

```
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://linux.dropbox.com/ubuntu/dists/lucid/Release.gpg  Something wicked happened resolving 'linux.dropbox.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

mebbe this helps someone help me

---

### Post by Scooter_X on 2010-08-01
Update: I was just able to install a couple packages without it hollering at me. Both through apt-get and the software center. HOWEVER my updates still say that something 'wicked' happened. Grr... 'No address associated with hostname' is what it says. ... what? It can't find the servers or something?

Edit: Hey, could it have something to do with my router's configuration? I wonder...

---

### Post by JC Cheloven on 2010-08-01
> **Scooter_X said:**
> Update: I was just able to install a couple packages without it hollering at me. Both through apt-get and the software center. HOWEVER my updates still say that something 'wicked' happened. Grr... 'No address associated with hostname' is what it says. ... what? It can't find the servers or something?

Edit: Hey, could it have something to do with my router's configuration? I wonder...
Mmm, maybe changing the mirror where you download your programs from, will update all packaging... just try: go to 
system -> administration -> software sources 
And where it reads 'dowload from' (u probably have an usa server), change to another server, for example an uk server or whatever.

Then reload, and see if it helped.
JC

---

### Post by Scooter_X on 2010-08-04
Yea, I had tried that before. I just got internet access again (they're 'fixing' stuff on the roof at my apartment but busted the cable that gave us internet) so I can finally reply, but yea I tried several in the US and some elsewhere in the world, but no go. Besides, the ones that were having problems are under 'Other Software' so they'd probably go off of whatever server they were originally intended to use, I would think. Instead of being part of the "main" repositories like multiverse and universe. Oh well, I've just disabled them, I get all my regular ubuntu updates like normal, and I don't really need to update dropbox unless something breaks, but then I can just go find the latest release and go from there. I just hope I can add other PPAs later and have them work... I'm gonna try that right now in fact.

---

