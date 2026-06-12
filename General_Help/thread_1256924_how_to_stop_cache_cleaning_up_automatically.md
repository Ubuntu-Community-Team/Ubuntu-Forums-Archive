---
title: "how to stop cache cleaning up automatically"
date: 2009-09-03
forum: General Help
---

### Post by varunmagical on 2009-09-03
Hello guys,
I Format & install ubuntu many times & I ofen need to backup my cache to avoid fetching packages again.
But After some days older packages in cache are lost.
These older ones are important because newer packages are dependent on them.
These are needed during re installation.
How to stop this cleaning up of cache?

---

### Post by drs305 on 2009-09-03
When and what is automatically removed from /var/apt/cache appears to be controlled by files in /etc/apt/apt.conf.d.

*01autoremove* - What types of packages are never removed are set in . 
*10periodic* - Sets the autoclean interval.
And probably the one you are most interested in:
*20archive* 
> 
APT::Archives::MaxAge "30";
APT::Archives::MinAge "2";
APT::Archives::MaxSize "500";


---

### Post by CatKiller on 2009-09-03
You can do this from within Synaptic (assuming that's what you use to install packages). Settings &#8594; Preferences &#8594; Files &#8594; Leave all downloaded packages in the cache.

If you use the command-line tools, you can set APT's policies as drs305 describes.

---

### Post by drs305 on 2009-09-03
> **CatKiller said:**
> You can do this from within Synaptic (assuming that's what you use to install packages). Settings &#8594; Preferences &#8594; Files &#8594; Leave all downloaded packages in the cache.

If you use the command-line tools, you can set APT's policies as drs305 describes.

While I was 'researching' a response to this thread I came upon a post by a user who indicated Synaptic's actions didn't prevent the cache from eventually being emptied. Of course, it could have been a bug or something that user did - I would not take his post as gospel.

In any case, I went to Synaptic, changed the setting to "Leave all ..." and it did *not* change the settings in the files I mentioned.

Synaptic gives the choices of:
[I]
Leave all downloaded packages in cache
Delete downloaded packages after installation
Only delete packages which are no longer available
[/I]
My guess is that Synaptic will leave the packages in cache, but the cache will still be under control of APT, and thus emptied when APT decides it is time.
 So the user might be advised to make the changes in both.

---

### Post by varunmagical on 2009-09-03
> **drs305 said:**
> When and what is automatically removed from /var/apt/cache appears to be controlled by files in /etc/apt/apt.conf.d.

*01autoremove* - What types of packages are never removed are set in . 
*10periodic* - Sets the autoclean interval.
And probably the one you are most interested in:
*20archive*
Thank you for your reply.
But How to change that interval to like 999 days?
What these number signify? Do they specify time in days?

---

### Post by drs305 on 2009-09-03
> **varunmagical said:**
> Thank you for your reply.
But How to change that interval to like 999 days?
What these number signify? Do they specify time in days?

Yes, the "30" would be time in days.
To change this value:
```

gksudo gedit /etc/apt/apt.conf.d/20archive

```

Setting the max days value to "0" will disable it (won't ever be deleted).
For max size, the number is in MB. Use "0" to disable the maximum size.

---

### Post by varunmagical on 2009-09-03
> **drs305 said:**
> Yes, the "30" would be time in days.
To change this value:
```

gksudo gedit /etc/apt/apt.conf.d/20archive

```

Setting the max days value to "0" will disable it (won't ever be deleted).
For max size, the number is in MB. Use "0" to disable the maximum size.

Thank you!
I have asked another question related...
[http://ubuntuforums.org/showthread.php?t=1257036](http://ubuntuforums.org/showthread.php?t=1257036)

---

