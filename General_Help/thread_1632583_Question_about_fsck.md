---
title: "Question about fsck"
date: 2010-11-28
forum: General Help
---

### Post by blenderfox on 2010-11-28
Hi all, just a quick question about fsck.

I know I can force a fsck run at next reboot using

```
shutdown -rF now
```

or

```
touch /forcefsck
```

My question is, can I force the fsck to more indepth checks such as doing directory optimisations, bad blocks checks, etc. maybe by passing parameters to the fsck call during startup?

---

### Post by blenderfox on 2011-05-03
Anybody? :P

---

### Post by Nasair on 2011-05-03
[http://adminschoice.com/repairing-unix-file-system-fsck](http://adminschoice.com/repairing-unix-file-system-fsck)
Shows some of the commands. have you tried in a terminal:
```
fsck --help
```For more commands?

I don't use fsck unless it runs by its self after a bad shutdown.
Hope this helps some how.

---

### Post by blenderfox on 2011-05-03
> **Nasair said:**
> [http://adminschoice.com/repairing-unix-file-system-fsck](http://adminschoice.com/repairing-unix-file-system-fsck)
Shows some of the commands. have you tried in a terminal:
```
fsck --help
```For more commands?

I don't use fsck unless it runs by its self after a bad shutdown.
Hope this helps some how.

No, no, this isn't what I'm talking about. I can force fsck to run at boot by using the touch forcefsck command. During this boot-up fsck, I want to pass additional arguments to the fsck run, such as checking for bad sectors, optimising directories, etc. I'm not talking about running it in a terminal window.

---

### Post by Nasair on 2011-05-03
> No, no, this isn't what I'm talking about. I can force fsck to run at boot by using the touch forcefsck command. During this boot-up fsck, I want to pass additional arguments to the fsck run, such as checking for bad sectors, optimising directories, etc. I'm not talking about running it in a terminal window.

I know the normal ```
touch forcefsck
``` checks for bad sectors and all that, but from what I understand fsck its self doesn't have a whole lot of options as it is mean to fix drive issues. See below for detail on all of its options:
[http://linux.about.com/od/commands/l/blcmdl8_fsck_.htm](http://linux.about.com/od/commands/l/blcmdl8_fsck_.htm)

Do you know a way the normal fsck can do directory optimization?
Otherwise, I believe ```
touch forcefsck
``` is doing everything it needs to.

I did do some testing and I don't see a clear way to to use ```
touch forcefsck
``` with any arguments such as ```
touch forcefsck -P
``` Now I am using Xubuntu but I don't believe this should make a difference in this case.

I did a lot of searching on the Internet and I haven't seen any hint or mention of using additional parameters. Unless someone else knows something I'm led to believe there isn't a way to do these things with the touch command or some of the other options out there to force a fsck from within Ubuntu and have additional arguments in the string.

---

### Post by blenderfox on 2011-05-03
That's also what I thought. I was hoping there would be a way to do something like

```
fsck -fsVCD
```

At bootup, before the drives are mounted. Based on the lack of responses, I guess the answer is no. :(

---

### Post by Nasair on 2011-05-03
Ah, I see how you're trying to use it now. I don't know how often you'd like to run this but you could make a script that runs this, saves the out put, once done starts Ubuntu and have the script started by GRUB.
:)
Or if you only need to run it once in a while you could just make it an option in GRUB...or if you log everyone off and use the shell or live disc to run fsck you'd be safe that way as well.

---

### Post by blenderfox on 2011-05-03
> **Nasair said:**
> Ah, I see how you're trying to use it now. I don't know how often you'd like to run this but you could make a script that runs this, saves the out put, once done starts Ubuntu and have the script started by GRUB.
:)
Or if you only need to run it once in a while you could just make it an option in GRUB...or if you log everyone off and use the shell or live disc to run fsck you'd be safe that way as well.

At the moment, I run it just before I clonezilla my hard drive, which does me fine for now. I might take your option of grubbing a script. Thanks.

---

