---
title: "Getting Latest Version of Rhythmbox"
date: 2009-08-30
forum: General Help
---

### Post by craig10x on 2009-08-30
Hi:  I have Ubuntu 9.04....and i believe that there is more recent (stable) versions of Rhythmbox  available?
    
 First question...is it worth updating?  (any real improvements in later versions)
    
 Second question:  What is the easiest way to get the updated version?  
    
 I notice that Update Manager never seems to offer new versions of these native Ubuntu programs...so how can you get them to send it over to you?  Or is there some other way you have to do it?

Also, i was wondering why they don't seem to send over new versions of native Ubuntu programs (except Firefox, it seems) without having to ask for it...

I recall to get the latest version of Pidgin on Update Manager, and i had to type a request for it in the terminal....It would be nice if they would send these things over automatically...:confused:

Thanks in advance for all feedback on this  :)

---

### Post by uylug on 2009-08-30
The easiest way to upgrade programs is by using the package manager.

Like this:

Update the list of programs and versions
```
sudo apt-get update
```

Install or update Rhythmbox
```
sudo apt-get install rhythmbox
```

---

### Post by wojox on 2009-08-30
Open a terminal and type:

```
sudo apt-get update
```
```
sudo apt-get -u upgrade
```

This will upgrade any packages.

If rhythm-box doesn't show up you can wait for it to be added to the repo's or download it your self from their site.

---

### Post by craig10x on 2009-08-30
So, if i understand this correctly...if i type this into the terminal, then it will update the package manager for all new versions of any programs that are listed in it...and then i can install from the manager?

sudo apt-get update

---

### Post by craig10x on 2009-08-31
pardon my confusion...i am relatively new to Ubuntu and Linux (just a few months away from windows....lol) and i RARELY use the terminal.....

would those upgrades also get listed on the add/remove programs after awhile when i enter that in the terminal....or does that only upgrade the listings in the Package Manager?

---

### Post by wojox on 2009-08-31
I've got Rhythmbox 0.12.0 in synaptic. So if you want a more updated one you will need to look outside the repos.

---

### Post by jrox717 on 2009-08-31
The apt-get upgrade command works the same way as the Package Manager which alerts you to new updates to your packages. This should update your packages to the newest version in the repositories, though some packages have newer versions available, but they are not included in the repositories and you would have to install them yourself (which is, when they're not bundled for Ubuntu/Debian, considerably more difficult). If you want to look for the most up-to-date packages without using the command line, use Synaptic (System > Administration > Synaptic Package Manager).

According to Rhythmbox's website, the newist stable version is 0.12.4. 
Oh, and after a search on [www.getdeb.org](www.getdeb.org), I found it: [http://www.getdeb.net/app/Rhythmbox](http://www.getdeb.net/app/Rhythmbox)
 Just download the .deb package and double click to start the install. But just so you know-- because you didn't install it through apt-get or synaptic, this copy will not be upgraded from the repositories.
Good luck!

---

### Post by craig10x on 2009-08-31
When i download a newer version, will it just up grade the version i currently am using...or do i need to delete my current version first?

By the way...i appreciate all the help on this ;-)

---

### Post by jrox717 on 2009-08-31
I believe it should upgrade your current version, but don't quote me on that. In any case, removing the current version (try apt-get purge or "completely remove" in Synaptic) couldn't hurt.

---

