---
title: "Missing linux-ubuntu-modules! Please help me get back to a working system!"
date: 2012-09-21
forum: General Help
---

### Post by latebeat on 2012-09-21
Hello guys,
I've done a ton of research before resorting to posting here but I'm still new to linux so I really need your help.
I was using the dkms module for intel snd for my audio and I was trying to see if I could get the native kernel module instead to work so I removed alsa-hda-dkms from my system but that left me with a non working alsa configuration 

I have no devices listed under /proc/asound/devices and even alsamixer gives me a file not found error.

So I've spent a day googling and almost everyone suggests reinstalling alsa along with the kernel and kernel modules to get back to a working state
i.e. ```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```

I tried that and everything reinstalled fine apart from the kernel modules.

**I get this error with linux-ubuntu-modules**
```
sudo aptitude reinstall linux-ubuntu-modules-`uname -r`
[B]Couldn't find any package whose name or description matched "linux-ubuntu-modules-3.2.0-31-generic"
Couldn't find any package whose name or description matched "linux-ubuntu-modules-3.2.0-31-generic"[/B]
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.

```


I really don't know what else to do at this point apart from installing everything from scratch and I would really hate to resort to that :(

Any help would be greatly greatly appreciated!

---

### Post by josephmills on 2012-09-21
`` is depreciated

  try 
```


sudo aptitude reinstall linux-ubuntu-modules-$(uname -r)


```

though I do not know what linux-ubuntu modules is

```
apt-cache search linux-ubuntu-*
```

Brings back nothing But I am on 12.10 so maybe it is different or something. I would say look at the moadues maybe you are looking for a different package ?

---

### Post by latebeat on 2012-09-21
> **josephmills said:**
> `` is depreciated

  try 
```


sudo aptitude reinstall linux-ubuntu-modules-$(uname -r)


```

though I do not know what linux-ubuntu modules is

Oh, didn't know what.. anyhow same thing:

```
$sudo aptitude reinstall linux-ubuntu-modules-$(uname -r)
**Couldn't find any package whose name or description matched "linux-ubuntu-modules-3.2.0-31-generic"**
Couldn't find any package whose name or description matched "linux-ubuntu-modules-3.2.0-31-generic"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
```

---

### Post by steeldriver on 2012-09-21
I think the 'ubuntu' is superfluous - try

```
linux-modules-$(uname -r)
```

... unless you previously had non standard modules (backports?)

---

### Post by latebeat on 2012-09-21
> **steeldriver said:**
> I think the 'ubuntu' is superfluous - try

```
linux-modules-$(uname -r)
```

... unless you previously had non standard modules (backports?)

Yes, I do have backports enabled..

Same thing without the ubuntu in there :(

```
$ sudo apt-get install linux-modules-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Unable to locate package linux-modules-3.2.0-31-generic**
```

---

### Post by steeldriver on 2012-09-21
hmm... well maybe try

```
apt-cache policy $(uname -r)
```

which should tell you the candidates for anything with your kernel in their name

---

### Post by latebeat on 2012-10-07
> **steeldriver said:**
> hmm... well maybe try

```
apt-cache policy $(uname -r)
```

which should tell you the candidates for anything with your kernel in their name

So just to close this thread, it was an issue with alsa. In the end everything is working fine now and didn't need to reinstall anything

---

