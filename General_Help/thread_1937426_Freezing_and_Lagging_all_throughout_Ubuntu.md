---
title: "Freezing and Lagging all throughout Ubuntu"
date: 2012-03-07
forum: General Help
---

### Post by justinrpg on 2012-03-07
I have Ubuntu on a Guest OS on VirtualBox and my Ubuntu seems to freeze and lag during the whole time I use it!!! It's making me not want to use it!!! none of my other Guests do that!!! Just Ubuntu!!! all I do with the Ubuntu Guest is run a Pokémon Facebook account off of it!!! so I don't know what could be the problem!!! any help would be appreciated!!!

---

### Post by justinrpg on 2012-03-09
is NOBODY going to help me????????? :sad: How Rude!!! this is a REAL problem!!!

---

### Post by QIII on 2012-03-09
Everyone's problems are real and they are important to them.

But please understand two things:

1.  We are all here voluntarily as we have time to give.

2.  The community is spread around the world.  The guy with the best answer may live in Bangalore and you may be in Des Moines.  He may have been asleep when you posted this.

Now, as to your problem.  I run Ubuntu and derivatives in VBox all the time without problems.  Clearly, something is different between us.

Your request for help is vague and generalized.

Can you give us some information about what it is you are doing when your machine freezes and any other symptoms that precede the freeze?

(Some general advice when asking for help in an online forum:  One question mark or exclamation point is sufficient and don't call those who are able to give help "rude" because they do not do so immediately.  People have a tendency  to react rather poorly to being disparaged.)

---

### Post by justinrpg on 2012-03-10
> **QIII said:**
> Everyone's problems are real and they are important to them.

But please understand two things:

1.  We are all here voluntarily as we have time to give.

2.  The community is spread around the world.  The guy with the best answer may live in Bangalore and you may be in Des Moines.  He may have been asleep when you posted this.

Now, as to your problem.  I run Ubuntu and derivatives in VBox all the time without problems.  Clearly, something is different between us.

Your request for help is vague and generalized.

Can you give us some information about what it is you are doing when your machine freezes and any other symptoms that precede the freeze?

(Some general advice when asking for help in an online forum:  One question mark or exclamation point is sufficient and don't call those who are able to give help "rude" because they do not do so immediately.  People have a tendency  to react rather poorly to being disparaged.)


I said it is all throughout Ubuntu! the whole time I am using it! it is worse when I bring up the internet in Ubuntu!

---

### Post by disabled20191128 on 2012-03-10
first of all cool down, we are trying to help here, ok?
So can you give us more information concerning the host's specs and the guest's settings?

---

### Post by disabled20191128 on 2012-03-10
try an older ubuntu version

---

### Post by justinrpg on 2012-03-10
Host

Windows 7 
Intel Pentium Dual CPU T3200 2.0GHZ (2 CPUs)
Memory 4096MB RAM
Video Mobile Intel 965 Express Chipset Family 358MB


Guest:
Base Memory: 512MB
Video Memeory: 12MB
8GB Fixed Medium storage

I used VirtualBox's Recommended setting

---

### Post by QIII on 2012-03-11
"All throughout Ubuntu" is a bit hard to diagnose.  It is also a bit overstated, I suspect.

Tell us one thing we can concentrate on.

---

### Post by Old_Grey_Wolf on 2012-03-11
Those specs a very similar to my laptop. 

I give the Ubuntu guest 1GiB of memory. That is what is recommended for an Ubuntu install.

---

### Post by akshay.sulakhe on 2012-03-11
All through the ubuntu. Sounds like a virus spreading all throughout the body. lol. :P.. Well,i am guessing u need more power in whatever system ur using. I read the specs,just push in some more ram,some more video memory(i dunno how ur gonna do that). If a particular application is lagging,it might be becoz of the application issue,whole system lag is coz of some other problems. Do you mind checking the process usage,which process is going too high,do the preliminary checks. Re-install if necessary. And ya,plz dont say people are rude and all,u shud especially thank all those who helped you even after u called people on the forum rude. I mean,seriously.

---

### Post by matt_symes on 2012-03-11
Hi

> **Old_Gray_Wolf said:**
> Those specs a very similar to my laptop. 

I give the Ubuntu guest 1GiB of memory. That is what is recommended for an Ubuntu install.

I concur. Give the VM more memory and a bigger drive.

When it's freezing and laggy, it is accessing the hard drive ? Do you have swap set up ?

Have you ran utilities such as htop, iotop, free, ntop, nethogs, dstat (etc) in a terminal to pinpoint why it's laggy ?

Kind regards

---

### Post by Old_Grey_Wolf on 2012-03-11
> **matt_symes said:**
> 
Have you ran utilities such as htop, iotop, free, ntop, nethogs, dstat (etc) in a terminal to pinpoint why it's laggy ?

He has to install the packages for htop, iotop, ntop, nethogs, and dstat before he can run them. Nice tools but they are not installed by default. I start to tell someone to run a command quite often, then I remember it is not installed by default. :)

---

### Post by matt_symes on 2012-03-11
Hi

> **Old_Gray_Wolf said:**
> He has to install the packages for htop, iotop, ntop, nethogs, and dstat before he can run them. Nice tools but they are not installed by default. I start to tell someone to run a command quite often, then I remember it is not installed by default. :)

Very good point ! Because i install all these as soon as i install Ubuntu, i tend to forget that.

From the command line.

```
sudo apt-get install htop sysstat ntop nethogs dstat
```

You should also be able to get them from software center and synaptic as well i think.

You will need to enable the universe repository for most of the ones i suggested.

```
matthew@matthew-Aspire-7540:~$ apt-cache show htop sysstat ntop nethogs dstat | grep Section:
Section: universe/utils
Section: admin
Section: universe/net
Section: universe/net
Section: universe/admin
matthew@matthew-Aspire-7540:~$
```

Kind regards

---

