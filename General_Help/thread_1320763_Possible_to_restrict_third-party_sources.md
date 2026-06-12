---
title: "Possible to restrict third-party sources?"
date: 2009-11-09
forum: General Help
---

### Post by CoreyB. on 2009-11-09
I added the GetDeb repo for the frostwire package.  I opened the update manager and it asked me to update transmission from the GetDeb ppa.  But the only reason I want the GetDeb ppa is for the frostwire package, not to update other packages.

Is it possible to make every package that GetDeb and the default Ubuntu repos have in common to default to the Ubuntu repos and not offer me the updates from GetDeb?

Thanks

---

### Post by tuwe on 2009-11-09
You could use apt pinning: [https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

I've never used it myself, so unfortunately i can't give you a working example. The wiki page looks good though.

---

### Post by CoreyB. on 2009-11-09
> **tuwe said:**
> You could use apt pinning: [https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

I've never used it myself, so unfortunately i can't give you a working example. The wiki page looks good though.

Thanks but I'm not sure that is exactly what I want to do.

I can't believe there isn't some easy way to make one repo trump another on all packages they have in common.

---

### Post by CoreyB. on 2009-11-09
I will try and rephrase my question to make it more clear:

How do I make packages from the official Ubuntu repositories become the default packages in Synaptic, Update Manager, etc.

Example:

I have the GetDeb PPA.  The GetDeb PPA contains transmission.  I want to install transmission so I go to Synaptic and find that transmission from the GetDeb PPA is the default version, but I want the one from the official repos.

How do I make all of the software default from the official Ubuntu repos, instead of the third party PPAs?

---

### Post by CoreyB. on 2009-11-10
Or is it possible just to use one package from a ppa?  Could I edit my sources list to specify to only monitor one package from a ppa?

---

### Post by ranch hand on 2009-11-10
One way of doing this is to edit your /etc/apt/sources.list and comment out the offending repos.

If you do that and run;
```

sudo apt-get update

```
they will not be used at all.

You can un-comment them, run the above command and check them on occasion.

If you use synaptic for your updates you can set it to tell you what section the package comes from.

A lot of ppas just deal with one package.

If I, personally, were using Update Managers I would not use third party repos.

---

### Post by honestguvnor on 2009-11-10
> I have the GetDeb PPA. The GetDeb PPA contains transmission. I want to install transmission so I 
> go to Synaptic and find that transmission from the GetDeb PPA is the default version, but I want 
> the one from the official repos.

This is a way to totally break things. Is transmission the same version and compiled with the same parameters? If it is not or you do not know then you have to use one in the external repository.

I would suggest that for a distribution like Ubuntu where stability is not strongly weighted you are far better off compiling the extra programs like GetDeb and sticking with the libraries in the main system.

Distributions like Centos/RHEL which strongly weight stability do have mechanisms for doing what you want but it does require the repository owners to be careful and work with the main release.

---

### Post by alphaniner on 2009-11-10
I came across a post recently about assigning priority to software sources (as in: you can do it and here's how), but I have no idea what the thread was.

Edit: Googling 'apt source priority' returned some promising results.

---

### Post by CoreyB. on 2009-11-10
I tried creating /etc/apt/preferences containing

Package *
Pin: origin archive.getdeb.net
Pin-Priority: -1

but it seems to have no effect.

What am I doing wrong?

Edit: I seem to got it to work my /etc/apt/preferences file contains:

Package: *
Pin: origin archive.getdeb.net
Pin-Priority: 99

Maybe it was because I changed /etc/apt/conf.d/01ubuntu to contain:

APT::Default-Release "karmic";

but I am not sure if this is necessary, try without first.

---

