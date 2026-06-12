---
title: "Deb repacking?"
date: 2012-04-01
forum: General Help
---

### Post by linktopower on 2012-04-01
Okay hello again. today I'm curios to find out How could I repack a deb file thats already been installed. and make it usable on another system.

heres what I'm trying to do. Computer A has ubuntu 11.10. And It has Wine installed on it. But Computer B has no Wine On it. I was wondering is there a way to repack wine and its dependencies to allow me to install it on Computer B?

---

### Post by JC Cheloven on 2012-04-01
Hint 1:
In /var/cache/apt/archives you'll find the files .deb for all propgrams you installed. You can copy the desired .deb's from here and go install to a machine with the same ubuntu version and architecture (ie, 32 or 64 bits).

Hint 2:
Your question suggest that you haven't internet in Computer B (if you have, you can simply install from the repos whatever you need). There is a way of generating a download script using synaptic. Basically you use synaptic in Computer B to generate a script containing the info about what you need to download. Then, in Computer A (w/ internet) you run that script and the stuff is downloaded. Then you go back to Computer B to install the stuff.  For more details please [check here]("https://help.ubuntu.com/community/Synaptic/PackageDownloadScript").

Hope this helps

Note: as far as I know, to repackage from an installed program is a rather unusual concept. It should be possible though, but I guess very few people has thought about it.

---

### Post by Frogs Hair on 2012-04-01
If you have a computer that is not online and can't down load the dependencies needed for an application you look at the link . I have not used this method though .  [https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

You may be able to locate the package but you would need the dependencies . Another option would be to learn to build the entire package with dependencies  included .

---

### Post by linktopower on 2012-04-01
> Hint 1:
 In /var/cache/apt/archives you'll find the files .deb for all propgrams you installed. You can copy the desired .deb's from here and go install to a machine with the same ubuntu version and architecture (ie, 32 or 64 bits).
I've looked there But I was unable to find any packages...

> Hint 2:
 Your question suggest that you haven't internet in Computer B (if you have, you can simply install from the repos whatever you need). There is a way of generating a download script using synaptic. Basically you use synaptic in Computer B to generate a script containing the info about what you need to download. Then, in Computer A (w/ internet) you run that script and the stuff is downloaded. Then you go back to Computer B to install the stuff. For more details please check here.
Yeah computer B does not have a active Internet connection.
I've never thought about using a synaptic script. That would work!.
Thanks for that link.

> Note: as far as I know, to repackage from an installed program is a rather unusual concept. It should be possible though, but I guess very few people has thought about it.
Its quite possible I have done it too move a Program  from the first computer too the second one. but that thing is... I really do not now what the dependencies are for wine. so I thought Some one might now of a way to make 
```
dpkg-repack
``` 
Repack up The Wine program and every one of the dependencies. 
NOTE: I've only done this once to get a One single program off Comp A to Comp B.

> If you have a computer that is not online and can't down load the dependencies needed for an application you look at the link . I have not used this method though . [https://help.ubuntu.com/community/Ap...ine/Repository](https://help.ubuntu.com/community/Ap...ine/Repository)

 You may be able to locate the package but you would need the dependencies . Another option would be to learn to build the entire package with dependencies included .
I'll have to try Sometime thanks :)
And How could I build the package with the dependencies included?

---

### Post by JC Cheloven on 2012-04-02
> **linktopower said:**
> .
(...) I really do not now what the dependencies are for wine. 
Again in Synaptic, seach for the wine version you're interested in (there may be several available), right-click, -> properties, -> dependencies tab. 

I really can't live without that synaptic thing :lolflag:

---

### Post by linktopower on 2012-04-04
Oh Duh. I forgot about that... Thanks for the remninder.

---

