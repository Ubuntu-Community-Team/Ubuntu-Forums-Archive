---
title: "Hmmm this is weird"
date: 2006-05-23
forum: General Help
---

### Post by spamzilla on 2006-05-23
When I type su in the Terminal command line, I get the following message:

su:Authentication failiure.
Sorry.

I then get returned back to user@ubuntu:~$

Why is this? I recently did a fresh install of Ubuntu and since then, I cannot use the su command :(

I have made sure I can give admin commands, so this shouldn't be the probelm.

---

### Post by Sef on 2006-05-23
it's sudo

sudo apt-get update

sudo apt-get upgrade

etc....

Read this about sudo and root

[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

---

### Post by spamzilla on 2006-05-23
Sef, I was on about getting into the root user command line using "su" which I can no longer do.

Sorry for any confusion :)

---

### Post by spamzilla on 2006-05-23
Thanks for that link :P

sudo passwd root

That was the line I needed to gain access to the root user!

EDIT:

Another question. When you download a file, where does it get saved to?

For example, someone said to do this:

> Ok, now it's downloaded we need to unpack the file. First use the 'cd' command to change directory to wherever you downloaded it. For me it's /downloads

cd /downloads

---

### Post by Ramses de Norre on 2006-05-23
Or just use sudo su, you wont need to enable the root password then.

For the downloading: firefox downloads to ~/Desktop by default, wget to the currecnt directory (probably ~ when you didn't cd to someplace else).
Other programs have their own settings.

---

### Post by towsonu2003 on 2006-05-23
[QUOTE=spamzilla]
sudo passwd root
[/QUOTE]
```

sudo -i # su -
sudo -s -H # su

```
so you won't have to enable root and possibly break some stuff..

---

### Post by PriceChild on 2006-05-23
yeah i just use
 
sudo su -

---

