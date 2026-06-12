---
title: "update manager's applying changes window stucks"
date: 2012-06-07
forum: General Help
---

### Post by amrnegm on 2012-06-07
I am running ubuntu 11.10. the update manager shows a list of important security updates, all contain the word 'kernel'. when I run install updates, the 'applying changes' window freezes at the 'waiting' state.

And there is another problem with the update manger which I don't know whether it is related to this one. When I want to upgrade to ubuntu 12.4 and prompts me to enter password, it tells incorrect password msg, although I am certain it is right.

anyone can help?

---

### Post by Cheesehead on 2012-06-07
Please post the content of your /var/log/apt/term.log to [http://pastebin.ubuntu.com](http://pastebin.ubuntu.com) , and post the pastebin link here.

I advise against trying to upgrade to 12.04 until after your 11.10 problem is resolved.

---

### Post by amrnegm on 2012-06-08
> **Cheesehead said:**
> Please post the content of your /var/log/apt/term.log to [http://pastebin.ubuntu.com](http://pastebin.ubuntu.com) , and post the pastebin link here.


here is the content of term.log
[http://pastebin.ubuntu.com/1031266/](http://pastebin.ubuntu.com/1031266/)

---

### Post by amrnegm on 2012-06-10
is there anyone to help?

---

### Post by amrnegm on 2012-06-16
eventually, I found a solution. 
I ran the following commands from shell

```

sudo apt-add-repository ppa:francisbrwn9/kernels
sudo apt-get update
sudo apt-get dist-upgrade

```

I think the problem cause is that the above software source, which I added in the first command, was absent from sources.list file.
Also, the ubuntu 12.04 update problem was solved just as the first problem was solved. Alhamdul lellah :)

---

