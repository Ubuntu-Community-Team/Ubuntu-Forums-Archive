---
title: "can't update Ubuntu"
date: 2012-03-28
forum: General Help
---

### Post by stookin on 2012-03-28
Hi

I'm new and running Ubuntu 11.10 and happy with it.

However when I update I get these errors:
```
W: Failed to fetch http://archive.ubuntu.com/dists/oneiric/main/binary-i386/Packages  404  Not Found [IP: 91.189.92.179 80]

W: Failed to fetch http://archive.ubuntu.com/dists/oneiric/universe/binary-i386/Packages  404  Not Found [IP: 91.189.92.179 80]

W: Failed to fetch http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```Also when after a while I see a red alert (a red exclamation mark in a triangle) in the upper right corner, next to the keyboard sign.
When I click on it it says that I need to update Ububntu and that the packages are over 9 days old (every day that number gets higher, so tomorrow it will say over 10 days old)

Help, I don't know how to fix this.

---

### Post by PhantomTurtle on 2012-03-28
You posted about this in your other thread here - [http://ubuntuforums.org/showthread.php?t=1946313]("http://ubuntuforums.org/showthread.php?t=1946313"). If nobody is answering bump it after 24 hours. It looks like you problem was solved in that thread though, so why post again?

---

### Post by stookin on 2012-03-28
No it wasn't solved. Do you want me to close the thread now:confused:

---

### Post by PhantomTurtle on 2012-03-28
> **stookin said:**
> No it wasn't solved. Do you want me to close the thread now:confused:

I cannot close it since I am not a mod but I don't know if somebody else will. However you should just post on the thread that you already have. Also in that thread post what happens after you modify the sources.list file.

Additionally I don't know if you are allowed to post two threads with about the same thing. Like I said before just bump it, if it has not been answered for over a day.

---

### Post by stookin on 2012-03-28
Ok, sorry for double post then.
Thought it would be easier if I made a new post about it.

But I won't in the future.

anyway, this is my sources.list file:

```
deb http://archive.ubuntu.com oneiric main universe

deb http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu hardy main
deb-src http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu hardy main

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ oneiric-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-security universe
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-security multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
```Edit: So should I bump my other post now as well?

Edit #2: Nothing happens
I just keep getting the errors I mentioned earlier.
I also tried to uninstall crebs in synaptic package manager, no crebs there
I also tried to comment-out the crebs lines in sources.list, as you can see, no crebs there :s
I'm lost.

---

### Post by PhantomTurtle on 2012-03-28
Well I guess you can just forget about the other thread. I'm not sure why you would get that even when the error, but you can always remove the ppa. To do that open terminal and type in:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:ppanamehere
```

Also you could try this - [http://www.webupd8.org/2010/04/ubuntu-sources-list-generator-available.html]("http://www.webupd8.org/2010/04/ubuntu-sources-list-generator-available.html"), [http://www.webupd8.org/2009/07/ubuntu-sources-list-generator.html]("http://www.webupd8.org/2009/07/ubuntu-sources-list-generator.html"). This will link you to a website that can generate a new sources.list file for you, but be aware that I have NOT tried this out and I cannot guarantee that it will work.

---

### Post by stookin on 2012-03-28
Thank you
and I will try that, I'm just learning about ubuntu, installing everything I like, testing everything out.
If I screw it up I will reinstall it again.

For now I'm just screwing around checking how it works and such. I will test it out.

Edit:
The first line
```

sudo apt-get install ppa-purge

```
was successful I believe

However when I tried this line:
```

sudo ppa-purge ppa:ppanamehere

```This happened:
```

sudo ppa-purge ppa:ppanamehere
Updating packages lists
W: Failed to fetch http://archive.ubuntu.com/dists/oneiric/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://archive.ubuntu.com/dists/oneiric/universe/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
Warning:  apt-get update failed for some reason
PPA to be removed: ppa:ppanamehere ppa:ppanamehere
Warning:  Could not find package list for PPA: ppa:ppanamehere ppa:ppanamehere
```

---

### Post by PhantomTurtle on 2012-03-28
Just so where clear, you replaced ppa:ppanamehere with the actual name of the ppa right? If yes, the ppa also has to be enabled to be purged.

---

### Post by stookin on 2012-03-28
Updated my sources.list file to the online generated one:
```

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://nl.archive.ubuntu.com/ubuntu/ oneiric main restricted universe multiverse 
deb-src http://nl.archive.ubuntu.com/ubuntu/ oneiric main 

###### Ubuntu Update Repos
deb http://nl.archive.ubuntu.com/ubuntu/ oneiric-security main restricted universe multiverse 
deb http://nl.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted universe multiverse 
deb-src http://nl.archive.ubuntu.com/ubuntu/ oneiric-security main

```

ran:
sudo apt-get update

Got these errors again:
```

W: Failed to fetch http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by stookin on 2012-03-28
> **PhantomTurtle said:**
> Just so where clear, you replaced ppa:ppanamehere with the actual name of the ppa right? If yes, the ppa also has to be enabled to be purged.
Sorry no I just blindly pasted your command line in my terminal

I didn't even read "ppanamehere"
Which ppa name should I enter, crebs?
so the code will be:
```

sudo ppa-purge ppa:crebs
```am I right or wrong?

I entered it,
I got this:

```

Updating packages lists
W: Failed to fetch http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
Warning:  apt-get update failed for some reason
PPA to be removed: ppa:crebs ppa:crebs
Warning:  Could not find package list for PPA: ppa:crebs ppa:crebs

```

---

### Post by cortman on 2012-03-28
I'm almost reluctant to help due to the reprehensible nature of your other thread, but here's an answer.
You need to edit the sources.list file. In a terminal type

```
gksu gedit /etc/apt/sources/sources.list
```In that file find the line that looks like

```
deb http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages
```Delete that line. Save it and close.
Then go to System Settings>Software Sources and change your repository mirrors. Run

```
sudo apt-get update
```

That should fix it.

---

### Post by stookin on 2012-03-28
I know, I must have a pretty bad reputation on this forum already :s
I will try to fit in better next time.

I would like to thank you for taking the nerve to help me, you and [PhantomTurtle]("http://ubuntuforums.org/member.php?u=1450094") fixed it.
Thank you. I have no more errors when updating.

It's solved.

Thanks so much <3
I have another question, in windows when you press ALT+num3 you get a heart
In my ubuntu this doesn't work yet..
maybe im not allowed to ask so ill just su (shut up)

---

### Post by cortman on 2012-03-28
> **stookin said:**
> I know, I must have a pretty bad reputation on this forum already :s
I will try to fit in better next time.

I would like to thank you for taking the nerve to help me, you and [PhantomTurtle]("http://ubuntuforums.org/member.php?u=1450094") fixed it.
Thank you. I have no more errors when updating.

It's solved.

Thanks so much <3
I have another question, in windows when you press ALT+num3 you get a heart
In my ubuntu this doesn't work yet..
maybe im not allowed to ask so ill just su (shut up)

Live and learn. It's good you're willing to adjust- we all make mistakes! Glad your problem is solved. Always feel free to post in the style that you used with this thread. :)

Re emoticons, all the available ones are on the sidebar of the reply/new post box.

Good luck and best wishes!

---

