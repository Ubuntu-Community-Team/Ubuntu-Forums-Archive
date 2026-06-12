---
title: "Duplicate sources"
date: 2012-03-10
forum: General Help
---

### Post by meduser on 2012-03-10
Everytime I run apt-get update in terminal, I get the duplicated sources, and lists /var/lib/apt/lists/dl.google.com_linux_earth_deb_dists_stable_main_binary-i386_Packages as the file. I have gone to the file location, and removed it. It is then gone for a day. The next day, I run apt-get update, and I have duplicated sources /var/lib/apt/lists/dl.google.com_linux_earth_deb_dists_stable_main_binary-i386_Packages back again...I have tried using vi in the terminal and removing it, I have tried rm, and it shows as gone, until I do an apt-get update.

I am sorry for the questions, I just want to have this run as smoothly as possible. I am loving the system so far, I just need a nudge here and there.

Thanks in advance

---

### Post by raja.genupula on 2012-03-10
I am sure this gonna help you

```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

---

### Post by meduser on 2012-03-10
OK, I just did that...we'll see how that goes.

Thank you...

again this forum blows me away..less than 10 minutes from problem asked, to solution...just awesome.

---

### Post by raja.genupula on 2012-03-10
if you didnt get any error message while update then I am sure it will be fine .

---

### Post by meduser on 2012-03-10
yes, there was no error. 

Thanks again.

---

### Post by meduser on 2012-03-11
just to follow this up, I have updated this morning and the solution above seems to have fixed the problem. I have no duplicated sources after running update in terminal. 

Thanks you so much.

---

### Post by meduser on 2012-03-12
and another follow up, the duplicated sources are back today...

W: Duplicate sources.list entry [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_earth_deb_dists_stable_main_binary-i386_Packages)


so now what?

---

### Post by meduser on 2012-03-14
anyone have any ideas...still getting duplicated sources. I have gone into the /var/lib/apt/lists file and delete google earth, it disappears until the next day, and then it is back. Nothing really seems to be wrong, it just annoys me that I have errors.

Any suggestions are appreciated....;p

---

### Post by oldos2er on 2012-03-14
> **meduser said:**
> and another follow up, the duplicated sources are back today...

W: Duplicate sources.list entry [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_earth_deb_dists_stable_main_binary-i386_Packages)


so now what?

Can you run these two commands and post the output here? ```
ls /etc/apt/sources.list.d/

cat /etc/apt/sources.list
```

---

### Post by meduser on 2012-03-14
ok for ls /etc/apt/sources.list.d/ I got :
```

root@gary-home:~# ls /etc/apt/sources.list.d/
dropbox.list                                    medibuntu.list
dropbox.list.save                               medibuntu.list.save
echidnaman-qapt-experimental-oneiric.list       screenlets-dev-ppa-oneiric.list
echidnaman-qapt-experimental-oneiric.list.save  screenlets-dev-ppa-oneiric.list.save
google-earth.list                               screenlets-ppa-oneiric.list
google-earth.list.save                          screenlets-ppa-oneiric.list.save
google.list                                     tualatrix-next-oneiric.list
google.list.save                                tualatrix-next-oneiric.list.save
kubuntu-ppa-backports-oneiric.list              ubuntu-on-rails-ppa-oneiric.list
kubuntu-ppa-backports-oneiric.list.save         virtualbox.list
kubuntu-ppa-ppa-oneiric.list                    virtualbox.list.save
kubuntu-ppa-ppa-oneiric.list.save

```

and for the second command, cat /etc/apt/sources.list: 
```

root@gary-home:~# cat /etc/apt/sources.list
# 

# deb cdrom:[Kubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111011)]/ oneiric main restricted

# deb cdrom:[Kubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111011)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://mu.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://mu.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mu.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://mu.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mu.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://mu.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://mu.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://mu.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mu.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://mu.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://mu.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://mu.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mu.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://mu.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main

```

---

### Post by oldos2er on 2012-03-14
Check /etc/apt/sources.list.d/google.list and /etc/apt/sources.list.d/google-earth.list
Do they have the same content?

---

### Post by meduser on 2012-03-14
ok, so trying this: vi  /etc/apt/sources.list.d/google.list

results in:

```
deb http://dl.google.com/linux/earth/deb/ stable main

```

trying this: vi  /etc/apt/sources.list.d/google-earth.list

results in:

```
deb http://dl.google.com/linux/earth/deb/ stable main

```

looks identical to me. Now the vi  /etc/apt/sources.list.d/google-earth.list, says I can comment out the entry. Can I do that and problem solved? Or can I just remover on of the two files?

I await your response.

And thanks in advance. I really appreciate the help.

---

### Post by oldos2er on 2012-03-14
I would just delete one of the list files. ```
sudo rm /etc/apt/sources.list.d/google-earth.list
``` then ```
sudo apt-get update
```
Hopefully that should fix it.

---

### Post by meduser on 2012-03-14
I'll try that..brb..

---

### Post by meduser on 2012-03-14
Ok, I erased that file, updated and no duplicate sources. I have been here before, so I won't mark as solved yet, but I am hopeful..lol

Thanks again for the help. I hope it works.

---

### Post by oldos2er on 2012-03-14
You're welcome, and I hope it continues to work too!

---

### Post by meduser on 2012-03-15
Quick update...
just updated as I do every morning, and no duplicated sources...looking good.

---

### Post by meduser on 2012-03-17
Ok, so three days now and no duplicated sources. I am going to mark this thread as solved now.

Thanks again for the help. It was much appreciated.

---

