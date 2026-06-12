---
title: "/usr/lib/ was deleted.. Unable to login into ubuntu"
date: 2010-09-09
forum: General Help
---

### Post by devLinux on 2010-09-09
While installing some new packages,
i intended to delete /usr/lib/xxx/* by 
using ../../../*. But i missed one slash (../../*) .

Due to that, all the regular files in usr/lib were deleted.

Now i can boot only in recovery mode.

I re-installed some libraries using wget.

But for "apt-get upgarde", it is saying ,
dependency on synaptic.

And the loop goes like never ending..

Is their any way to reinstall the lib files in /usr/lib/?

Am using ubuntu 10.04 LTS

---

### Post by TeoBigusGeekus on 2010-09-09
I'd boot up with a live cd, backup any crucial files and reinstall (keeping the home partition unformatted).
It's the only way to be sure...

---

### Post by devLinux on 2010-09-09
No other way:-(????? I have to reinstall all the applications 
i installed ??????

---

### Post by TeoBigusGeekus on 2010-09-09
I think so...
Even if you copy the contents of /var/lib from a fresh installation of ubuntu to your system, you'd still miss the folders from the applications you had installed there. So, you'd have to reinstall all your software anyway, with high chance of system crashes.
Go with the clean install.

---

### Post by nothingspecial on 2010-09-09
Yep, you`ve hosed it.

It might be possible to chroot from a live cd and reinstall every library you`ve deleted but in this case a full reinstall would be a million times easier and quicker.

---

### Post by devLinux on 2010-09-09
If a take a backup excluding /mnt, /sys,/usr and restoring , will it replace the /usr of the re-installed one?

---

### Post by nothingspecial on 2010-09-09
If you make a /home partition, and create the users in the same order as you created them on this installation, all your setting will remain.

See this

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by yota on 2010-09-09
Before throwing the system on the trash I'll try this:

```

dpkg -S /usr/lib

```

if it works it should tell every single package that had something installed on /usr/lib
Then you should try to reinstall all those packages, and if you make it we can consider the system recovered.
I would try (in order):
```

aptitude reinstall $(dpkg -S /usr/lib| tr -d ',')

```
or
```

apt-get install --reinstall $(dpkg -S /usr/lib| tr -d ',')

```
or eventually
```

aptitude download $(dpkg -S /usr/lib| tr -d ',')
dpkg -i *.deb

```
other attempts can be done, such as redirecting the list to a file, transferring it to another machine where doind "aptitude download", then transfer the file back to the original pc and install them via dpkg.

It sure is a difficult journey, but I believe it can be done!

---

### Post by devLinux on 2010-09-09
[HTML]apt-get install --reinstall $(dpkg -S /usr/lib| tr -d ',')[/HTML]

i tried this ... but the output is like this

Reinstallation of $xxx is not possible, it cannot be downloaded.
.
.
.
Couldn't find package compizconfig-backend-gconf

---

### Post by yota on 2010-09-09
> **devLinux said:**
> [
i tried this ... but the output is like this

Reinstallation of $xxx is not possible, it cannot be downloaded.


Probably it's just that network is down in recovery mode...

Bring net up ("service networking start" should suffice, but your milleage may vary...) and retry.

Let us know how it goes!

---

### Post by devLinux on 2010-09-09
no.. it is not because of that.. apt-url was not there.. i tried to install it through wget. but it shows some other dependency.. apt-kde.. I wget ted that too.. but the dependency tree is growing.. I lost my patience.. After all that try only , i started thread

---

### Post by pikachu714 on 2010-12-13
This has happened to me too...
I had launched terminal and did sudo -i to become root, then opened up a nautilus window
i went to /usr and clicked on lib because i was gonna copy it
then a person pressed delete
what should I do?
I tried what yoda said:
[QUOTE=Yoda]Before throwing the system on the trash I'll try this:


```
dpkg -S /usr/lib
```
[/QUOTE]
A ton of stuff came up on the screen, and I saw names of packages i reconized.
I tried the other things he said, they didn't work. It said, cannot find shared library(the /usr/lib folder?)
I accessed ubuntu from windows, and the /usr/lib folder was empty.
Can I fix it, or should i just reinstall?

---

### Post by WorMzy on 2010-12-13
If "a person" just pressed delete, then chances are that the entire of /usr/lib is now in /root/.local/share/Trash/files

If this is the case, then just move it back. Use a LiveCD if sudo doesn't work any more.

---

