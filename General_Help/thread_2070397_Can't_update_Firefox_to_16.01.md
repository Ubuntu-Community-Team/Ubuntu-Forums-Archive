---
title: "Can't update Firefox to 16.01"
date: 2012-10-12
forum: General Help
---

### Post by grey1beard on 2012-10-12
I'm trying to get my wife's laptop reconnected via Firefox. 
I launched it this evening and it couldn't connect, so I checked the version and it showed 16.0.
Tried update manager, but that didn't offer anything.
Deleted firefox via software centre, then installed, and got the same version.
Repeated, but this time re-booted between delete and install, but same result.
Deleted via Synaptic, then looked at version in software centre after rebooting, and it still offered 16.0, so instead I tried installing via terminal.

This appears to be trying to re-install 16.0.
> "Selecting previously deselected package firefox.
Unpacking firefox ( .../firefox_16.0+buildfrom " etc. etc.

Lower down, it says 
> Please restart all running instances of firefox, or you will experience problems.

Problems!!! - you're not kidding.

Grateful for any help in sorting out this mess.

My first request is for help in removing all and any firefox bits, then what's the safest way to get 16.1(?) installed.

John

---

### Post by grey1beard on 2012-10-12
Should I use **apt-get purge firefox**, then  **apt-get install firefox** ?

Is it that simple ?

John

---

### Post by pqwoerituytrueiwoq on 2012-10-12
sudo apt-get update;sudo apt-get install firefox
make sure firefox is not in offline mode

---

### Post by Frogs Hair on 2012-10-12
Firefox 16 was pulled  from the Mozilla site because of a security problem  and has now returned after being patched. If Firefox normally updates via the update manager on your Ubuntu version just wait for the update. If not you  can look into the stable PPA. I see 11.04 listed which reaches end of life this month .

---

### Post by grey1beard on 2012-10-12
I think that is something I've already tried, but I did it again.
The first command produces a considerable number of Err lines, plus a few Failed to fetch lines.
The second command says that firefox is already the latest version (it's still 16.0, I checked)
If you need the screen shot of terminal, I can manage that but will take a little time.
John

---

### Post by pqwoerituytrueiwoq on 2012-10-12
would rather a copy/paste of the text...
is it a bunch of 404 errors?
```
lsb_release -d -s
```

---

### Post by grey1beard on 2012-10-12
Hi Frogs Hair,
Yes, it's because of the earlier problem, which my laptop has resolved through update, that when she tried to get on line, and couldn't I assumed that because her laptop showed 16.0 was still installed, that just running update manager would resolve the problem.
But it doesn't. I keep getting back to 16.0, whatever I do.
As I can't get her laptop connected, I'm not sure how to proceed, other than what I've tried so far. 
Could you expand on the ppa info for me ?
John

---

### Post by pqwoerituytrueiwoq on 2012-10-12
if you need a ppa for firefox/thunderbird
```
sudo apt-add-repository ppa:ubuntu-mozilla-security/ppa;sudo apt-get update;sudo apt-get install firefox
```

---

### Post by grey1beard on 2012-10-12
Hi  pqwoerituytrueiwoq
Do I run that after I've purged firefox, or with the system as it is now ?
John

---

### Post by pqwoerituytrueiwoq on 2012-10-12
you can purge if you feel like it, but it does not matter when all is said and done

---

### Post by grey1beard on 2012-10-12
> **pqwoerituytrueiwoq said:**
> would rather a copy/paste of the text...
is it a bunch of 404 errors?
```
lsb_release -d -s
```
have attached the terminal screen shot

---

### Post by grey1beard on 2012-10-12
> **pqwoerituytrueiwoq said:**
> you can purge if you feel like it, but it does not matter when all is said and done

Great, I'll go for it !
John

---

### Post by grey1beard on 2012-10-12
> **pqwoerituytrueiwoq said:**
> if you need a ppa for firefox/thunderbird
```
sudo apt-add-repository ppa:ubuntu-mozilla-security/ppa;sudo apt-get update;sudo apt-get install firefox
```

> sudo apt-add-repository ppa:ubuntu-mozilla-security/ppa
produced 
> Error reading [https://launchpad.net/api/1.0/~](https://launchpad.net/api/1.0/~) etc
Couldn't resolve host 'launchpad.net'

---

### Post by pqwoerituytrueiwoq on 2012-10-12
can this system even connect to the Internet? because it looks like it is not connected

---

### Post by grey1beard on 2012-10-12
](*,)Just opened wicd and it says no network found !!!
Please hold while I investigate.
John

---

### Post by grey1beard on 2012-10-12
Just rebooted the router, then cold booted the laptop.
Now have a connection, so I'll just try Update manager before I go any further.
john

---

### Post by grey1beard on 2012-10-12
Bingo !

My apologies to one and all for any time wasted.
It seems to me that I was led astray by the wicd icon on the top bar showing what I took to be a connection made.
Then, when I then tried to sort out the perceived problem(getting stuck with 16.0) via terminal and others, I overlooked any hints of a connection problem.

Lesson learned there, I hope.

Regards all,
John

---

### Post by Frogs Hair on 2012-10-12
Keep in mind that 11.04  is end of life this month  and it is easier to upgrade while the repository is still active.  [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by LisaM on 2012-10-14
I am running 12.04, and regularly run the Update Manager.  However my version of Firefox is still only 3.6.13 and some websites like Hulu.com say they won't support it any more.  

I just followed your instructions and the response is that my version of Firefix is already the latest version.  What is the problem?

ETA:  After opening Synaptic (sudo synaptic) and searching Firefox, I found that even though the newest version of Firefox had been installed, the old version somehow hadn't gotten uninstalled.  I was able to mark it for removal and get it uninstalled, so now I've got the new version working.

---

