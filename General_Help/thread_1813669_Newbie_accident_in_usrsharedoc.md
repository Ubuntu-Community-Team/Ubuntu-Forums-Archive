---
title: "Newbie accident in /usr/share/doc"
date: 2011-07-28
forum: General Help
---

### Post by Hans58 on 2011-07-28
Hi All,

I'm not a complete newbie in Linux, but I was working some years solely with Windows. But some weeks ago I remembered my old love and installed Ubuntu Natty 64 bit. Last night I installed also Oracle 11gR2 64 and got it finally running after some fights with missing packets and unexpectedly placed libs. (Unexpected by Oracle installer). Nevertheless; Oracle is running now.

Ok so far. This is the good news. The bad news:  In one of these fights I was in a terminal-session and accidentally entered sudo rm -r /usr/share/doc while I wanted to delete /usr/share/doc/libstdc++5. I wondered why this takes so long time and stopped it as I saw what I did. But too late of course, there are many subdirectories missing.

My question now:** Is there a way using apt-get, dpkg or similar to rebuild these subdirectories in /usr/share/doc?**

Natty is still running fine for now. But what happens if there are updates or new packets? I would really appreciate your ideas.

Cheers
Hans

---

### Post by jerrrys on 2011-07-29
i have wondered if doc's was really necessary.  if your natty is still running, i guess i got my answer.  however system files have a habit of rebuilding themself.  i don't know if this is the case with doc's, but try this and understand that this is untried by me.

sudo apt-get update

sudo apt-get upgrade

---

### Post by staticd on 2011-07-29
/usr/share/doc contains mostly man pages and the like. If you know some one with a similar software setup as yours try just copying their /usr/share/doc. Tar the directory to preserve unix permissions if you are transporting it on a pendrive.( In case jerrys suggestion doesn't work. Tell us if it did.).

---

### Post by jwbrase on 2011-07-29
> **Hans58 said:**
> Hi All,

I'm not a complete newbie in Linux, but I was working some years solely with Windows. But some weeks ago I remembered my old love and installed Ubuntu Natty 64 bit. Last night I installed also Oracle 11gR2 64 and got it finally running after some fights with missing packets and unexpectedly placed libs. (Unexpected by Oracle installer). Nevertheless; Oracle is running now.

Ok so far. This is the good news. The bad news:  In one of these fights I was in a terminal-session and accidentally entered sudo rm -r /usr/share/doc while I wanted to delete /usr/share/doc/libstdc++5. I wondered why this takes so long time and stopped it as I saw what I did. But too late of course, there are many subdirectories missing.

My question now:** Is there a way using apt-get, dpkg or similar to rebuild these subdirectories in /usr/share/doc?**

Natty is still running fine for now. But what happens if there are updates or new packets? I would really appreciate your ideas.

Cheers
Hans

Well, probably the best way is to ignore it for now, and then, if you need to look up documentation for a package and it's not there, try reinstalling the package (if it's still not there after a reinstall, the program probably never had documentation). AFAIK, /usr/share/doc is there for your convenience only, so it's no use going to the inconvenience of trying to restore anything in it until not having it puts you at an inconvenience.

Furthermore, AFAIK, as updates come in for packages, they should restore that package's documentation in /usr/share/doc.

---

### Post by jwbrase on 2011-07-29
> **jerrrys said:**
> i have wondered if doc's was really necessary.  if your natty is still running, i guess i got my answer.  however system files have a habit of rebuilding themself.  i don't know if this is the case with doc's, but try this and understand that this is untried by me.

sudo apt-get update

sudo apt-get upgrade

That will restore the documentation of packages for which newer versions are available, but not for anything for which no upgrades are available.

---

### Post by Hans58 on 2011-07-29
Hi All,

Many thanks for your thoughts. I did apt-get update/upgrade. The "update" parameter seemed not to store anything. At least no significant disk-activity. And "upgrade" said 4 times 0.

But if you say /usr/share/doc is rather important for documentation and man-pages then no problem. The most time I'm using Google to find answers for Linux-questions. :)

Thanks and have a nice weekend All.

Cheers
Hans

---

### Post by jerrrys on 2011-07-29
for manpages i find this link useful

[http://www.linuxmanpages.com/](http://www.linuxmanpages.com/)

and don't forget googlubuntu for forum searches

---

