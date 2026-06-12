---
title: "Incorrect number of updates available"
date: 2011-04-30
forum: General Help
---

### Post by slloyd11 on 2011-04-30
I'm running 10.4.2LTS

Whenever I log in via the terminal, byobu tells me:

15 packages can be updated.
10 updates are security updates.

However sudo apt-get upgrade says no updates

Why is this and how can I correct it?

Thanks

---

### Post by sikander3786 on 2011-04-30
> **slloyd11 said:**
> I'm running 10.4.2LTS

Whenever I log in via the terminal, byobu tells me:

15 packages can be updated.
10 updates are security updates.

However sudo apt-get upgrade says no updates

Why is this and how can I correct it?

Thanks
Welcome to the forums :-)

Can you please run this command all at once and post the complete output.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by slloyd11 on 2011-04-30
certainly

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) lucid/main Translation-en_GB                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                                                     
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_GB    
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_GB                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_GB                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release.gpg
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by WorMzy on 2011-04-30
byobu?

If apt-get says there's no updates pending, then there are no updates pending, and byobu is wrong.

---

### Post by sikander3786 on 2011-04-30
Yes there are no updates pending in that output. Test once more with byobu.

---

### Post by slloyd11 on 2011-04-30
Still the same message about 15 updates...

---

### Post by WorMzy on 2011-04-30
I don't know where it gets it's information from, but it's wrong. Ignore it.

---

### Post by slloyd11 on 2011-04-30
I'd rather if it told me correct information

---

### Post by MidSpeck on 2011-05-03
Just so **slloyd11** doesn't feel so lonely, I have been having the same issue for a week or two now although it shows a different number for me.

I figured I would wait until new updates were available and that would help reset it.  But, it didn't.  I had a set of updates just earlier this week but it still shows the old numbers upon login.

---

### Post by Turtle.net on 2011-05-03
See [http://ubuntuforums.org/showpost.php?p=10762966&postcount=22](http://ubuntuforums.org/showpost.php?p=10762966&postcount=22)

Just remove /etc/motd.tail (or move it to /etc/motd.tail.back just to be sure)

---

### Post by MidSpeck on 2011-05-03
> **Turtle.net said:**
> Just remove /etc/motd.tail (or move it to /etc/motd.tail.back just to be sure)

This seemed to reset it for me.  Thanks Turtle.

---

### Post by frio on 2011-05-06
Same issue here and removing /etc/motd.tail worked for me as well.

---

