---
title: "Removing Packages with dpkg - Dependencies"
date: 2011-01-26
forum: General Help
---

### Post by ddjolley on 2011-01-26
Hi.  I'm new to Ubuntu.  Where I am going is that I want to remove Evolution and install Thunderbird.  I have a general question.  WRT any given package, how can I determine if that package is required by any other packages so that I wouldn't want to remove it?  Thanks for any input.

          ... doug

---

### Post by amra.sonntag on 2011-01-26
If you use synaptic under system-->administration it will show you the packeges that get removed with removing evolution.

In general the packet manager apt-get, that lies behind synaptic will resolve all dependencies and usally not allow you to break them. That way you cannot "destroy" your applications by accident.

---

### Post by sikander3786 on 2011-01-26
Keep an eye on the packages that are going to be remove.

On my system's Applications > Accessories > Terminal,

```
sudo apt-get remove evolution
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  evolution evolution-couchdb evolution-exchange evolution-indicator
  evolution-plugins

```

Make sure there are no other packages listed there.

But instead of removing Evolution, I would recommend to just install Thunderbird and leave Evolution as it is. You can make Thunderbird default.

---

### Post by Smart Viking on 2011-01-26
I would personally keep Evolution, because I mean it doesn't do any harm being there and I'm a little lazy.
```
apt-cache showpkg evolution
```

---

### Post by ddjolley on 2011-01-26
Hmmm.  So, let me see if I understand this correctly.  "apt-get remove package" will setup to remove the specified package and any other packages that are required by the specified package but not required by any other packages (iow, what I would call "orphan" packages).  AND it will alert you to the packages that are being removed and give you an opportunity to opt out before effecting the removals.  THAT IS VERY COOL!!!

Having said that and having tucked that information safely away in my general knowledge, I like the idea of just leaving Evolution installed on the system but making Thunderbird the default.  Disk space is cheap and having the ability to easily switch between the two is a definite plus.  Would anyone care to comment on how I set the default?  Thanks.

          ... doug

---

### Post by amra.sonntag on 2011-01-26
You can select the application you prefer at System --> Preferences --> prefered aplications. Something like that (i'm on a german ubuntu - so no guarantees on names).

P.S.: Yeah, apt-get is really great ;)

---

### Post by pl@yer on 2011-01-26
> **smart viking said:**
> i would personally keep evolution, because i mean it doesn't do any harm being there and i'm a little lazy.
```
apt-cache showpkg evolution
```

+1

---

### Post by Krytarik on 2011-01-27
> **ddjolley said:**
> Hmmm.  So, let me see if I understand this correctly.  "apt-get remove package" will setup to **remove the specified package and any other packages that are required by the specified package but not required by any other packages** (iow, what I would call "orphan" packages).  AND it will alert you to the packages that are being removed and give you an opportunity to opt out before effecting the removals.  THAT IS VERY COOL!!!

I want to correct that a bit. In fact it's the other way around: apt will set up to **remove the specified package and any packages which *depend on it***, and thus will warn you about the impending additional removal of those packages. Thus it is indeed possible that orphan packages remain. If the removed package was installed manually, you can use the command "sudo apt-get autoremove" to remove those packages which has been installed to satisfy dependencies. But I don't know if that works also with packages installed at the initial setup, can anyone confirm this?

Btw., I've indeed removed Evolution and all packages with the "evolution" in the name which are not needed by other packages or functions.

remove/purge all packages found with "evolution", except those:
- evolution-data-server-common
- evolution-data-server (needed for "About Me", not warned about, was still in menu)

Greetings.

---

### Post by pl@yer on 2011-01-27
I have been told to avoid using autoremove...I think I was told that there have been problems with it in the past? This was on the Debian forum.

I use deborphan and dpkg -P like so
```

for i in $(deborphan);do dpkg -P $i;done

```
I repeat that till there is nothing to being purged.

---

### Post by ddjolley on 2011-01-27
> it's the other way around: apt will set up to [B]remove the specified package
> and any packages which *depend on it*[/B],

OOPS!!  That's a major difference.  It makes sense to automatically remove packages that depend on the package being removed since they will be broken once that package is removed.  

> If the removed package was installed manually,
> you can use the command "sudo apt-get autoremove" to remove those packages
> which has been installed to satisfy dependencies

I need to learn more about autoremove.  It has always been a keen desire of mine to be able to do a bit of housekeeping and remove packages that were installed to satisfy a dependency that no longer exists (what I call "orphan" packages).

Thanks for the input.

         ... doug

---

### Post by Krytarik on 2011-01-27
I only came across the "autoremove" option in the last days, it seems to work as it should.
I used to remove all packages which has been installed as dependencies upon a manual installation by looking into the log of the install and selecting the packages by hand.

In Synaptic you can filter those packages by choosing the "Status" filter. Then there is also an option to filter those packages which are removed but have remaining config files, to effectively purge those packages.

---

