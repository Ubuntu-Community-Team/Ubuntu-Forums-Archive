---
title: "$HOME folders erased, on a regular basis"
date: 2011-11-14
forum: General Help
---

### Post by blueblank on 2011-11-14
So, after the 6th time, I'm taking this to the forums.

Basically, my home directory gets wrecked on a regular basis. After an install[EDIT: Ubuntu 11.10 alternate install amd_64 via usb], I set up my files like I usually do; a folder that I symlink link to my portable config files. After a short time, almost everything I've setup gets erased, and my home folder will have just a skeleton of files. Folders I've added (plus the folders extant Downloads, etc), links I've made, all get erased and then the next time I login fresh as new.  

After the second time this happened, I reinstalled, making only minimal changes (nothing to the system other than installing programs and making symlinks). This happened several times again while logged in, and once while I was logged out.

I tried again, with a new image. This happened again (after I installed chromium-browser, while in my xmonad session). I thought possibly my xmonad setup was in some sort of conflict so I did some research on making it more gnome congruent (due for an overhaul anyway...). 

This happened again last night, after I made some progress with my xmonad setup.

Any help fixing this would be appreciated. I've not yet found anything similar here or elsewhere online. Intermittent and spontaneous erasure of my files is not helping me get any work done.

---

### Post by arubislander on 2011-11-14
Hi, Welcome to the forums.

Could you clarify somthing for us so we can better help you.

Is your home directory symlinked to another place as in:
```
$ ls -l /home
... someuser -> /somewhere/else/

```
or do you have a symlink in your home directory to somewhere else?

And where is somehwere else? Is it on the same harddrive, a network share?

---

### Post by blueblank on 2011-11-14
My $HOME is not symlinked to anywhere, and it is on the same partition as the root system, i.e. nothing fancy. All local, very much a standard install except I have /boot on another partition and it is an encrypted install (decrypted at setup, set up via alternate-install manual partitioning, something I've done for some time now as part of my standard setup, no issues previous) 

All the links I've made are within my $HOME, to a folder I've added e.g a symlink from .bashrc to the actual location of .bashrc. It became much easier a while back to drop in a directory of my configs and add links to that folder rather than worry about specific placement. These are are all files that aren't out of the ordinary, they would be there to begin with, with programs installed.

---

### Post by carranty on 2011-11-14
I've no idea why it would be doing this.  You say

> 
something I've done for some time now as part of my standard setup, no issues previous


Can you tell us when this started happening, did you install a different version of Ubuntu, or come to Ubuntu from a different flavour of linux.  I'm trying to get at whats changed since it was working fine - because right now I'm stumped.

---

### Post by blueblank on 2011-11-14
> **carranty said:**
> I've no idea why it would be doing this.  You say



Can you tell us when this started happening, did you install a different version of Ubuntu, or come to Ubuntu from a different flavour of linux.  I'm trying to get at whats changed since it was working fine - because right now I'm stumped.

This is an install of Ubuntu 11.10, this is the first I've installed 11.10, though I'm familiar with ubuntu/linux from previous versions, just not this version of Ubuntu or this particular issue.

This issue is new, with this version. My setup has had no (or minor) issues since 8/9 versions, which is to say very few problems where previous I had worked through a system.

If anyone would like to see my setup, I'll link to the git repo.

---

### Post by arubislander on 2011-11-14
> **blueblank said:**
> After a short time, almost everything I've setup gets erased, and my home folder will have just a skeleton of files. Folders I've added (plus the folders extant Downloads, etc), links I've made, all get erased and then the next time I login fresh as new.

So what you're saying is that from time to time your whole home directory gets nuked as if you were logging in as a brand new, recently added user?

I am suspecting this has nothing to do with your symlinks and something to do with the encryption. But I don't have any specifics yet.

---

### Post by blueblank on 2011-11-14
> **arubislander said:**
>  I am suspecting this has nothing to do with your symlinks and something to do with the encryption. But I don't have any specifics yet.

 Oky....this would be the first I've had any trouble with the encryption scheme. What evidence do you have for this reasoning?  Question marks for: why do you suspect this, where to start investigating this, what to do in the meantime(how to secure my files if I can't encrypt).  I could try an unencrypted install, but that would wholly disappoint me.

---

### Post by arubislander on 2011-11-22
I'm not up to speed with the encryption implementation on Ubuntu. But I seem to remember it being something like having a seperate encrypted filesystem that is mounted to your home folder at login.
The reason I suspect this might be the issue is that if for some reason the filesystem is not mounted to your home folder, then you would get what you describe, i.e. a home folder that is completely empty.

---

### Post by oldos2er on 2011-11-22
Have you run any disk checks like **smartctl** to rule out any hard disk problems?

---

