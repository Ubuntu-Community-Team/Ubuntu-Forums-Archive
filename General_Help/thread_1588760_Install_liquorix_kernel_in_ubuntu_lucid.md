---
title: "Install liquorix kernel in ubuntu lucid"
date: 2010-10-05
forum: General Help
---

### Post by rolandpish on 2010-10-05
Hi there.

I just installed a fresh box with a Ubuntu Lucid 32bit.

Is it possible and safe to install Liquorix Kernel in this distro?

I've done that in debian squeeze installations, but never done that in Ubuntu and really don't know if it's possible.

Thanks in advance.

Cheers

---

### Post by snowpine on 2010-10-05
Why *would* it work? Ubuntu is not Debian.

---

### Post by rolandpish on 2010-10-05
Thanks snowpine.

I'm new to liquorix and didn't know that this kernel was only for Debian. Now I know :)

Thanks again.

---

### Post by sidzen on 2010-10-21
> **rolandpish said:**
> Thanks snowpine.

I'm new to liquorix and didn't know that this kernel was only for Debian. Now I know :)

Thanks again.


Ubuntu was once in the Debian fold.  Alas, it has gone astray! 
(You are forgiven for not knowing!)

---

### Post by snowpine on 2010-10-21
If you are looking for a "bleeding edge" kernel for Ubuntu, check this out:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by rolandpish on 2010-10-21
> **snowpine said:**
> If you are looking for a "bleeding edge" kernel for Ubuntu, check this out:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Cool! thanks a lot. I'll check this out.

Cheers

---

### Post by sidzen on 2010-10-21
Thanks, snowpine.

---

### Post by spier on 2010-10-26
> **sidzen said:**
> Thanks, snowpine.

Running Maverick Meercat, installed Liquorix two weeks ago:

added following line to /etc/apt/sources.list
```
deb http://liquorix.net/debian sid main
```

installed the keyring...
```
apt-get install '^liquorix-([^-]+-)?keyring.?'
```

Voilà... bleeding edge kernel!!!

```
Linux laptop 2.6.36-0.dmz.2-liquorix-686 #1 ZEN SMP PREEMPT Mon Oct 25 01:08:47 UTC 2010 i686 GNU/Linux

```

Stable, so far. Seams faster (maybe a placebo effect) but my five years old laptop run really cooler now!

---

### Post by ironic.demise on 2010-10-26
I'm a little new to this and I'm interested, what is "bleeding edge" kernel?

---

### Post by spier on 2010-10-30
> **ironic.demise said:**
> I'm a little new to this and I'm interested, what is "bleeding edge" kernel?

Ok. Lets see.
> Bleeding edge technology refers to technology that is so new that the user is required to risk unreliability, and possibly greater expense, in order to use it.[[http://en.wikipedia.org/wiki/Bleeding_edge_technology]("http://en.wikipedia.org/wiki/Bleeding_edge_technology")

Now, every Ubuntu release is based on a specific, freezed kernel, i.e. Jaunty shipped with 2.6.32, Maverick ships with 2.6.35.
So, for those who feel brave to try the newest kernels released by [linux.org/]("http://www.linux.org/"), you'll have to look for alternatives like liquorix. But, as wikipedia told, there are risks!


hope this (and my English) makes sense!

---

### Post by ironic.demise on 2010-10-30
> **spier said:**
> Ok. Lets see.
[http://en.wikipedia.org/wiki/Bleeding_edge_technology]("http://en.wikipedia.org/wiki/Bleeding_edge_technology")

Now, every Ubuntu release is based on a specific, freezed kernel, i.e. Jaunty shipped with 2.6.32, Maverick ships with 2.6.35.
So, for those who feel brave to try the newest kernels released by [linux.org/]("http://www.linux.org/"), you'll have to look for alternatives like liquorix. But, as wikipedia told, there are risks!


hope this (and my English) makes sense!

Perfect sense, and your English is fine. Honestly, so many people here speak perfect english but are under some illusion that they struggle to speak the language. Anyway thank you for the response it has helped.

---

### Post by nutellajunkie on 2010-11-17
> **snowpine said:**
> Why *would* it work? Ubuntu is not Debian.

Of course it works, unless im dreaming here. Works perfectly okay.. Straight forward install from the directions given before me.

So far, so good.

Looking forward to that ~200 line patch I just heard about!

---

### Post by VMC on 2010-11-17
> **spier said:**
> 
installed the keyring...
```
apt-get install '^liquorix-([^-]+-)?keyring.?'
```

Voilà... bleeding edge kernel!!!



```
$ sudo apt-get install '^liquorix-([^-]+-)?keyring.?'
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Couldn't find package ^liquorix-([^-]+-)?keyring.?**

---

### Post by spier on 2010-11-17
> **VMC said:**
> ```
$ sudo apt-get install '^liquorix-([^-]+-)?keyring.?'
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Couldn't find package ^liquorix-([^-]+-)?keyring.?**


Hi, 

probably some issue with repo availibility.

Just tried it and seams ok:
```
sudo apt-get install '^liquorix-([^-]+-)?keyring.?'
...
liquorix-archive-keyring is already the newest version.
liquorix-keyring is already the newest version.
liquorix-keyrings is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by snowpine on 2010-11-17
Glad it is working out for you... and I stand corrected. :)

---

### Post by dentaku65 on 2010-11-17
I'm getting this error when I try to install liquorix kernel:

```
sudo apt-get install linux-image-2.6.36-0.dmz.11-liquorix-686 linux-headers-2.6.36-0.dmz.11-liquorix-686 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-headers-2.6.36-0.dmz.11-liquorix-686: Depends: libncurses5 (>= 5.7+20100313) but 5.7+20090803-2ubuntu3 is to be installed
E: Broken packages
```

I'm running on Lucid

---

### Post by spier on 2010-11-17
> **dentaku65 said:**
> I'm getting this error when I try to install liquorix kernel:

```
...

The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-headers-2.6.36-0.dmz.11-liquorix-686: Depends: libncurses5 (>= 5.7+20100313) but 5.7+20090803-2ubuntu3 is to be installed
E: Broken packages
```

I'm running on Lucid

Not sure what is happening.

Libncurses5 should be in ubuntu repos. Try install it, i.e. 

sudo apt-get install libncurses5

or, if it is already installed, try to reinstall through synaptic package manager (mine says it is in version 5.7+20100626-0ubuntu1);

or check if your repositories in /etc/apt/sources.list...

---

### Post by ww2 on 2010-11-17
> **dentaku65 said:**
> I'm getting this error when I try to install liquorix kernel:

```
sudo apt-get install linux-image-2.6.36-0.dmz.11-liquorix-686 linux-headers-2.6.36-0.dmz.11-liquorix-686 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-headers-2.6.36-0.dmz.11-liquorix-686: Depends: libncurses5 (>= 5.7+20100313) but 5.7+20090803-2ubuntu3 is to be installed
E: Broken packages
```

I'm running on Lucid

You need to install a more recent (date 20100313) version of the libncurses5 package. Search Maverick's (Ubuntu 10.10) repositories, get the corresponding .deb file and manually install.

---

### Post by dentaku65 on 2010-11-19
> **ww2 said:**
> You need to install a more recent (date 20100313) version of the libncurses5 package. Search Maverick's (Ubuntu 10.10) repositories, get the corresponding .deb file and manually install.

I found a differend way to use cgroups without using a patched kernel:

Here the trick:
[http://yep.it/pqkcoq](http://yep.it/pqkcoq)

Here for Ubuntu version:
[http://pastebin.com/raw.php?i=sHRYRuAN](http://pastebin.com/raw.php?i=sHRYRuAN)

Really boost! :D

---

### Post by angelsguitar on 2011-01-08
I'm running the liquorix kernel on Ubuntu Studio 10.10 64 bit. No problems so far, and notice positive improvement in realtime performance and system responsiveness over generic kernel.

---

### Post by Bucky Ball on 2011-01-08
If I install Liquorix kernel it will be available as an option with all my current kernels when I boot? So if it doesn't run I can choose my previous kernel? I'm imagining so and this could be a silly question but just making sure.  Keen to try it out. ;)

---

### Post by MeGodzillaUDead on 2011-01-08
Another successful install on 10.04LTS!  Here's what I did in case anyone has trouble synthesizing the steps from the above posts: 

 -install the (newer) version of libncurses5 from the Maverick suppositories
-add liquorix kernel sources (NOT LIQOURIX like I tried to spell it at first) 
-install key signatures 
-install kernel image 
-reboot and start making music! 

    Big ups to damentz for putting out this kernel and big ups to the Ubuntu developers for making so easy to get it to work with Ubuntu!  -MeGodzillaUDead

---

### Post by angelsguitar on 2011-01-09
> **Bucky Ball said:**
> If I install Liquorix kernel it will be available as an option with all my current kernels when I boot? So if it doesn't run I can choose my previous kernel? I'm imagining so and this could be a silly question but just making sure.  Keen to try it out. ;)

Yes, it adds itself to the grub menu, just like all Ubuntu kernels do. You can choose any previous kernel if it doesn't work.

---

### Post by Bucky Ball on 2011-01-09
Thanks angelsguitar. How ya doin'? Haven't seen you about in awhile. ;)

---

### Post by Bucky Ball on 2011-01-09
This is it for me:

 ```
binky@tosher:~$ sudo apt-get install '^liquorix-([^-]+-)?keyring.?'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ^liquorix-([^-]+-)?keyring.?
E: Couldn't find any package by regex '^liquorix-([^-]+-)?keyring.?'
binky@tosher:~$ 
```

No go.

---

### Post by angelsguitar on 2011-01-10
> **Bucky Ball said:**
> This is it for me:

 ```
binky@tosher:~$ sudo apt-get install '^liquorix-([^-]+-)?keyring.?'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ^liquorix-([^-]+-)?keyring.?
E: Couldn't find any package by regex '^liquorix-([^-]+-)?keyring.?'
binky@tosher:~$ 
```

No go.

Hi Bucky Ball! Hope you're doing fine.

Yeah, that happened to me too.  Just do ```
sudo apt-get install liquorix-keyring liquorix-keyrings
``` and you'll be all set.

---

### Post by Bucky Ball on 2011-01-10
Thanks for that Angel, but virtually the same:

```
binky@tosher:~$ sudo apt-get install liquorix-keyring liquorix-keyrings
[sudo] password for binky: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package liquorix-keyring
E: Unable to locate package liquorix-keyrings
```

I'll have a bit more of a dig about now. ;)

---

### Post by Bucky Ball on 2011-01-10
I managed to get keyring installed, update grub, reboot. No sign of Liquorix kernel. What am I doing wrong I wonder?

*EDIT: This is what:

```

sudo echo "deb http://liquorix.net/debian sid main" > /etc/apt/sources.list.d/liquorix.list
sudo apt-get update
sudo apt-get install '^liquorix-([^-]+-)?keyring.?'
**sudo apt-get install '.*liquorix'**
reboot
```

From post #24 on this page:

[http://forums.anandtech.com/showthread.php?p=31046262](http://forums.anandtech.com/showthread.php?p=31046262)

(thanks VinDSL)

Once I input the line in bold all was fine. Liquorix unfortunately can't see my wireless (wlan0).
iwconfig yields no sign of wlan0; just lo and eth0. Any ideas? I will post a separate thread to deal with this perhaps. ;)

---

### Post by VinDSL on 2011-01-11
> **Bucky Ball said:**
> I managed to get keyring installed, update grub, reboot. No sign of Liquorix kernel. What am I doing wrong I wonder?

*EDIT: This is what:

```

sudo echo "deb http://liquorix.net/debian sid main" > /etc/apt/sources.list.d/liquorix.list
sudo apt-get update
sudo apt-get install '^liquorix-([^-]+-)?keyring.?'
**sudo apt-get install '.*liquorix'**
reboot
```

From post #24 on this page:

[http://forums.anandtech.com/showthread.php?p=31046262](http://forums.anandtech.com/showthread.php?p=31046262)

(thanks VinDSL)You're welcome!  (I'm a member here too)  :)

BTW, I'm running the Liquorix [COLOR="DarkBlue"]**2.6.37-0.dmz.1**[/COLOR] kernel now.

So far, so good!

---

### Post by Bucky Ball on 2011-01-11
> **VinDSL said:**
> You're welcome!  (I'm a member here too)  :)

BTW, I'm running the Liquorix [COLOR=DarkBlue]**2.6.37-0.dmz.1**[/COLOR] kernel now.

So far, so good!

Cheers VinDSL. Your instructions worked a treat for me. As I say, no sign of wireless on my machine using that kernel unfortunately. Might try the 2.6.37-0.dmz.1 and see if that makes a difference. Where did you obtain it?

---

### Post by VinDSL on 2011-01-12
> **Bucky Ball said:**
> Cheers VinDSL. Your instructions worked a treat for me. As I say, no sign of wireless on my machine using that kernel unfortunately. 

Might try the 2.6.37-0.dmz.1 and see if that makes a difference. Where did you obtain it?Well, there are numerous ways of doing this, but...

Basically, you want to use the Debian 'future' pool, instead of the Debian 'main' pool.

**Main Repo** (what you're using now)
```

deb http://liquorix.net/debian [COLOR="Red"]**sid main**[/COLOR] #Liquorix Kernel
deb-src http://liquorix.net/debian [COLOR="red"]**sid main**[/COLOR] #Liquorix Kernel Source

```

**Future Repo** (what you want to switch to)
```

deb http://liquorix.net/debian [COLOR="red"]**sid main future**[/COLOR] #Liquorix Experimental Kernel
deb-src http://liquorix.net/debian [COLOR="red"]**sid main future**[/COLOR] #Liquorix Experimental Kernel Source

```

Personally, I want to keep them both around, in case 2.6.37-0.dmz.1 doesn't work out, soooo...

The Liquorix section in my sources.list looks like this (main repo commented out / future repo active):

```

# deb http://liquorix.net/debian sid main #Liquorix Kernel
# deb-src http://liquorix.net/debian sid main #Liquorix Kernel Source
deb http://liquorix.net/debian sid main future #Liquorix Experimental Kernel
deb-src http://liquorix.net/debian sid main future #Liquorix Experimental Kernel Source

```

Once you've designated the future pool as your Liquorix repo, simply do an update, using:

[LIST]
[*]Update Manager
[*]Synaptic Package Manager
[*]Ubuntu Tweak
[*]CLI, or...
[*]Whatever method you normally use for updates
[/LIST]

...and 2.6.37-0.dmz.1 should be one of your choices.

Make sense?!?!?  ;)

---

### Post by Bucky Ball on 2011-01-12
Yea, thanks heaps VinDSL. Gotta go out for awhile but will try that immediately I get back and let you know. ;)

---

### Post by nnn= on 2011-01-30
I get this: ```
WARNING: The following packages cannot be authenticated!   linux-headers-2.6.37-0.dmz.6-liquorix-686 linux-image-2.6.37-0.dmz.6-liquorix-686 linux-headers-2.6-liquorix-686 linux-image-2.6-liquorix-686 Install these packages without verification [y/N]?
``` I did ```
sudo apt-get install '^liquorix-([^-]+-)?keyring.?'
``` (for which I had to sudo bash, otherwise perm den) and got this verification prompt as well. I pressed n, but now, doing ```
sudo apt-get install '.*liquorix'
``` I get it again, so I chose to seek advice here, instead of just proceeding unverified.

---

### Post by VinDSL on 2011-01-30
Have you tried...

```

sudo apt-get update && sudo apt-get upgrade

```

Watch for any public keyring errors at the end of the dialog, and fix them, as needed.

---

### Post by nnn= on 2011-01-31
Thanks, after updates everything proceeded without errors.

---

### Post by opodaniel on 2011-02-21
Nice one, follow it , working like a charm. How can I add PAE option to this nice kernel? 
I have 2 computers one don't need the PAE option since it only got 2Gb of Ram, but the other one have 4G Ram and now 1Gb is taking  a  well deserved holiday :d.
So how to compile/patch this kernel to enable PAE?

---

### Post by gamepoint on 2011-02-24
cannot install..this message appear

E: linux-image-2.6.37-1.dmz.2-liquorix-686: subprocess installed post-installation script returned error exit status 9
E: linux-image-2.6-liquorix-686: dependency problems - leaving unconfigured

---

### Post by VinDSL on 2011-02-25
> **gamepoint said:**
> cannot install..this message appear[...]
What process are you using to install Liquorix?

Personally, I used the PPA to install Liquorix, and Synaptic (Packager Manager) to update it.

---

### Post by VinDSL on 2011-02-25
> **opodaniel said:**
> Nice one, follow it , working like a charm. How can I add PAE option to this nice kernel?
You got me!  I've never tried that...

You can always follow the band, and use one of their pre-compiled hacks.

For instance:  [http://bandshed.net/kernels/](http://bandshed.net/kernels/)

---

### Post by gamepoint on 2011-02-25
I'm using the method in this thread earlier..After that followed by sudo apt-get update
Then using PPA, i searched for 'liquorix' and install everything that appear..Only 3-4 results as far i can remember.The kernel header and the images

---

