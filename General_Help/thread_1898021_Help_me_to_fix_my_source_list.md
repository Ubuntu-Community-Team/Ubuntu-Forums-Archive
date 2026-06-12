---
title: "Help me to fix my source list"
date: 2011-12-20
forum: General Help
---

### Post by asifnaz on 2011-12-20
I am using ubuntu 10.04 . here is my source list ( I cant install anything )

#deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid mai$
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted univ$
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted $


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

---

### Post by seawolf167 on 2011-12-20
You can generate a new [list here]("http://repogen.simplylinux.ch/")

To use it, first backup your current list

```
cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

then overwrite your current list with the one you just generated

```
gedit /etc/apt/sources.list
```

and update it

```
sudo apt-get update
```

---

### Post by asifnaz on 2011-12-20
> **seawolf167 said:**
> You can generate a new [list here]("http://repogen.simplylinux.ch/")

To use it, first backup your current list

```
cp /etc/apt/sources.list /etc/apt/sources.list.backup
```then overwrite your current list with the one you just generated

```
gedit /etc/apt/sources.list
```and update it

```
sudo apt-get update
```

I generated my source list and it looks like this 

```
deb http://pk.archive.ubuntu.com/ubuntu/ lucid main restricted universe multive$
deb-src http://pk.archive.ubuntu.com/ubuntu/ lucid main restricted universe mul$


deb http://pk.archive.ubuntu.com/ubuntu/ lucid-security main restricted univers$
deb http://pk.archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe$
deb http://pk.archive.ubuntu.com/ubuntu/ lucid-proposed main restricted univers$
deb http://pk.archive.ubuntu.com/ubuntu/ lucid-backports main restricted univer$
deb-src http://pk.archive.ubuntu.com/ubuntu/ lucid-security main restricted uni$
deb-src http://pk.archive.ubuntu.com/ubuntu/ lucid-updates main restricted univ$
deb-src http://pk.archive.ubuntu.com/ubuntu/ lucid-proposed main restricted uni$
deb-src http://pk.archive.ubuntu.com/ubuntu/ lucid-backports main restricted un$


deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner
```

But still not working

 asifnazir@ubuntu:~$ sudo apt-get install update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package update
asifnazir@ubuntu:~$

---

### Post by snowpine on 2011-12-20
The correct syntax is:

```
sudo apt-get update
```

By including 'install' in there, you are instructing it to install the package named 'update' which doesn't exist.

If you have a GUI desktop environment then you can use Ubuntu Software Center/Muon/Synaptic/etc so you don't have to worry about terminal commands. :)

/etc/apt/sources.list is an important system file and I do not recommend editing it directly.

---

### Post by pastalavista on 2011-12-20
[QUOTE=asifnaz;11552291
 asifnazir@ubuntu:~$ sudo apt-get install update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package update
asifnazir@ubuntu:~$[/QUOTE]

```
sudo apt-get update
```
NOT 'sudo apt-get install update'
then run ```
sudo apt-get upgrade
```

---

### Post by asifnaz on 2011-12-20
> **snowpine said:**
> The correct syntax is:

```
sudo apt-get update
```By including 'install' in there, you are instructing it to install the package named 'update' which doesn't exist.

If you have a GUI desktop environment then you can use Ubuntu Software Center/Muon/Synaptic/etc so you don't have to worry about terminal commands. :)

/etc/apt/sources.list is an important system file and I do not recommend editing it directly.

Yes it is updating now . I don't mind using CLI to install apps and can you please tell me if my source list is OK..?

---

### Post by snowpine on 2011-12-20
> **asifnaz said:**
> Yes it is updating now . I don't mind using CLI to install apps and can you please tell me if my source list is OK..?

Your sources.list was never broken as far as I can see (and I do not recommend that you edit this file); the problem was your invalid command "sudo apt-get install update".

You can use "man apt-get" to learn additional syntax.

---

### Post by seawolf167 on 2011-12-20
> **asifnaz said:**
> Yes it is updating now . I don't mind using CLI to install apps and can you please tell me if my source list is OK..?

Yea, it looks good, I don't think it was ever actually "broken". You may need to enable more repos in the future based on any software preferences you may desire. You can read more about the Repositories [here]("https://help.ubuntu.com/community/Repositories/Ubuntu"). You can simply check other sources you may need in the future.

---

### Post by snowpine on 2011-12-20
I am assuming you've restored your backup and rolled back to your original, not-broken sources.list from post #1. If you keep the new sources.list in post #3 then you have enabled the "proposed," "partner," and "backports" repositories; did you do that on purpose?

---

### Post by asifnaz on 2011-12-20
> **snowpine said:**
> Your sources.list was never broken as far as I can see (and I do not recommend that you edit this file); the problem was your invalid command "sudo apt-get install update".

You can use "man apt-get" to learn additional syntax.

It was not installing anything but now I see my mistake . I have edited my source list without saving it . But I have save it here on ubuntu forums :D

---

### Post by snowpine on 2011-12-20
Excellent; good luck and let us know if there are additional errors! :)

---

### Post by asifnaz on 2011-12-20
> **snowpine said:**
> I am assuming you've restored your backup and rolled back to your original, not-broken sources.list from post #1. If you keep the new sources.list in post #3 then you have enabled the "proposed," "partner," and "backports" repositories; did you do that on purpose?

No I did not do this on purpose I do not know what they mean . So what should I don now..? can you please edit my source list (if possible ) and post back here

---

### Post by asifnaz on 2011-12-20
> **snowpine said:**
> Excellent; good luck and let us know if there are additional errors! :)

Original list was not working and i totally replaced it with one i generated :confused: it is working fine so far

---

### Post by snowpine on 2011-12-20
If you are happy with it, that's all that matters. :)

Here is a brief description of the repositories you accidentally added to your system:

[https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates)

More info:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

You can revert to your backup sources.list by reversing the command that Seawolf167 gave in post #2:

```
cp /etc/apt/sources.list.backup /etc/apt/sources.list
```

However if you've already updated your system with the Proposed repo enabled, it is probably too late to go back.

---

### Post by asifnaz on 2011-12-20
> **snowpine said:**
> If 

You can revert to your backup sources.list by reversing the command that Seawolf167 gave in post #2:

```
cp /etc/apt/sources.list.backup /etc/apt/sources.list
```However if you've already updated your system with the Proposed repo enabled, it is probably too late to go back.

I have updated with those proposed repos . I am just worried because the other user said there might be some errors

---

### Post by snowpine on 2011-12-20
Nothing to worry about; it just means you'll get proposed updates a little bit before the rest of the world, and your system may be slightly less stable/reliable..

---

