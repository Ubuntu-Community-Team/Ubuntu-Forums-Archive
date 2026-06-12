---
title: "&quot;Broken Packages&quot; installation error - help!"
date: 2011-11-01
forum: General Help
---

### Post by doctorbighands on 2011-11-01
I've just finished a fresh install of Kubuntu 11.10 on a desktop machine. Everything went (relatively) smoothly, except for one thing: When I go to try to install Banshee (I loathe Amarok, that's why), I get the following error in the terminal:

```
<me>@<mycomputer>:~$ sudo apt-get install banshee
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 banshee : Depends: libwebkitgtk-1.0-0 (>= 1.3.10) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

It hasn't given me this error for any other packages, apps, or updates I've tried to install.

I've tried all the usual fixes I can think of and find: apt-get update, apt-get -f install, apt-get autoclean, apt-get clean, dpkg --configure -a, and the list goes on. All of those either run fine or give no output, signaling that everything is "working."

Here are some insights and best guesses:

*The problem seems to arise (emphasis on "seems to") after installing Synaptic. However, after uninstalling Synaptic to test this theory, the problem persists.

*I'm running an LTSP cluster at my work that's based on Kubuntu 11.10, and it's giving me the very same error message. This tells me the problem may have something to do with Kubuntu, KDE, or version 11.10.

Any help is very much appreciated! Thank you!

---

### Post by inameiname on 2011-11-01
> **doctorbighands said:**
> I've just finished a fresh install of Kubuntu 11.10 on a desktop machine. Everything went (relatively) smoothly, except for one thing: When I go to try to install Banshee (I loathe Amarok, that's why), I get the following error in the terminal:

```
<me>@<mycomputer>:~$ sudo apt-get install banshee
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 banshee : Depends: libwebkitgtk-1.0-0 (>= 1.3.10) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```It hasn't given me this error for any other packages, apps, or updates I've tried to install.

I've tried all the usual fixes I can think of and find: apt-get update, apt-get -f install, apt-get autoclean, apt-get clean, dpkg --configure -a, and the list goes on. All of those either run fine or give no output, signaling that everything is "working."

Here are some insights and best guesses:

*The problem seems to arise (emphasis on "seems to") after installing Synaptic. However, after uninstalling Synaptic to test this theory, the problem persists.

*I'm running an LTSP cluster at my work that's based on Kubuntu 11.10, and it's giving me the very same error message. This tells me the problem may have something to do with Kubuntu, KDE, or version 11.10.

Any help is very much appreciated! Thank you!

If apt-get -f install or dpkg --configure -a isn't working, I guess the next thing to try would be to install libwebkitgtk. I am not sure why it would not already be set to install alongside, particularly as I did see that package, with a version later than the minimum required ([http://packages.ubuntu.com/search?keywords=libwebkitgtk&suite=default&section=all&arch=any&searchon=names](http://packages.ubuntu.com/search?keywords=libwebkitgtk&suite=default&section=all&arch=any&searchon=names)), inside the Ubuntu Natty's repo. So unless Kubuntu Natty's repo keeps older versions, I don't know why you couldn't just install that package and have it work. Then, if still getting an error, try to reinstall banshee.

One final thing, if you happen to be installing Banshee from a PPA, sometimes there can be a dependency missing, such as libwebkitgtk. I don't know if that is the issue, of course, but always something to keep an eye out for.

And as for Synaptic being a cause for the problem, I don't really know why it would be.

Oh, and if it is indeed a Kubuntu issue, I am afraid I am at a loss.

---

### Post by doctorbighands on 2011-11-01
I went to try to install the specified dependency, as you suggested, and guess what...
```
<me>@<mycomputer>:~$ sudo apt-get install libwebkitgtk-1.0-0
[sudo] password for <me>: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libwebkitgtk-1.0-0 : Depends: libgail18 (>= 1.18.0) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

I wonder how recursive I'd have to get before I find the dependency that would actually install. :)

I'm at a total loss. It acts as if the package manager isn't cooperating, but it seems to want to install lots of other things without complaint.

Is there, maybe, an error log somewhere that I could consult? I wouldn't even know which application's error log to look at, but still...

---

### Post by doctorbighands on 2011-11-01
Okay, so, as a result of having nothing left to try at the moment, I decided to go ahead and take a stroll into dependency hell, just to see what would happen. Here's the result:
```
<me>@<mycomputer>:~$ sudo apt-get install libgail18
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgail18 : Depends: libgtk2.0-0 (= 2.24.6-0ubuntu4) but 2.24.6-0ubuntu5 is to be installed
E: Unable to correct problems, you have held broken packages.
<me>@<mycomputer>:~$ sudo apt-get install libgtk2.0-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk2.0-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Apparently that's the end of the line, dependency-wise. Question is, why is it trying to install the newer version of libgtk?

Maybe if we can answer that, we can solve this issue!

---

### Post by skynet2060 on 2011-11-01
Banshee may not be supported anymore.

---

### Post by doctorbighands on 2011-11-01
> **skynet2060 said:**
> Banshee may not be supported anymore.

Really? Didn't it replace Rhythmbox as the default media player in Oneiric?

---

### Post by inameiname on 2011-11-02
> **doctorbighands said:**
> I went to try to install the specified dependency, as you suggested, and guess what...
```
<me>@<mycomputer>:~$ sudo apt-get install libwebkitgtk-1.0-0
[sudo] password for <me>: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libwebkitgtk-1.0-0 : Depends: libgail18 (>= 1.18.0) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```I wonder how recursive I'd have to get before I find the dependency that would actually install. :)

I'm at a total loss. It acts as if the package manager isn't cooperating, but it seems to want to install lots of other things without complaint.

Is there, maybe, an error log somewhere that I could consult? I wouldn't even know which application's error log to look at, but still...

Doh! That figures. Dependency after dependency. I just do not understand why the banshee found in the official repos is having so much trouble. I can understand this, and have experienced such an issue before, with a PPA repo for an updated banshee or whatnot, but not just one found in a repo for the specific version you are using. If this is indeed a case, it might be a bug with Ubuntu. If so, you can file a bug report. I just don't know why it wouldn't be supported anymore in Kubuntu Oneiric.

---

