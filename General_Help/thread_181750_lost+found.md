---
title: "lost+found"
date: 2006-05-24
forum: General Help
---

### Post by ice60 on 2006-05-24
hi, a couple of times i've had to maunally fix errors found during fsck at boot, also i think i've had afew bad shut downs. however, everything is working fine now. (i think that's related to lost+found)

my lost+found directory (/lost+found) has alot of files in it, lots of different formats, from thumbs to things which look like system files - sockets, scripts, fifo's, device-blocks etc, etc. from the things i know about, i know i don't need them.

is my system using any of these files? or are they there incase i want them and if my computer is running OK now can the whole of lost+found can safely be deleted? thanks.

---

### Post by tonyr on 2006-05-24
[QUOTE=ice60]hi, a couple of times i've had to maunally fix errors found during fsck at boot, also i think i've had afew bad shut downs. however, everything is working fine now. (i think that's related to lost+found)

my lost+found directory (/lost+found) has alot of files in it, lots of different formats, from thumbs to things which look like system files - sockets, scripts, fifo's, device-blocks etc, etc. from the things i know about, i know i don't need them.

is my system using any of these files? or are they there incase i want them and if my computer is running OK now can the whole of lost+found can safely be deleted? thanks.[/QUOTE]

If you are **sure** you don't need them,  it's ok to delete them.   The system
is not using them; **fsck** just needs a conventional place to dump leftovers
and orphans after it has repaired the filesystem as best it can. Don't delete 
the **/lost+found** directory, just its contents.

---

### Post by glinsvad on 2006-05-24
> 
i think i've had afew bad shut downs.

Et tu? For some reason Breezy has started exhaling on me - complete power off in a matter of split seconds :shock:. Is that what's been happening to you as well?

Enough of my problems, lost+found cannot possibly be in use by the system. It is merely used to save files that can't be successfully restored after a crash.

> 
Vir prudens non contra ventum mingit

Why not? Vires acquirit eundo
[http://www.yuni.com/library/latin_8.html]("http://www.yuni.com/library/latin_8.html")

EDIT: Revera linguam latinam vix cognovi

---

### Post by ice60 on 2006-05-24
thanks for the help, tony and glinsvad. i'll probably delete the contents.
[QUOTE=tonyr]If you are **sure** you don't need them,  it's ok to delete them.[/QUOTE]
i'm not totally sure. i've had to do two manual repairs with fsck, [the first](http://www.ubuntuforums.org/showthread.php?t=160632), was long enough ago that i hope as things are working now everything was fixed. it involved many, many more repairs then the second which only had afew errors.

i think the first fsck repair was about the allocated place for alot of files being incorrect and needing to be 'updated/changed'. i had to manually press 'y' (for yes rather then 'n' for no) for each correction. i ended up putting a big screwdriver upturned on the 'y' key and resting it on the monitor so i'd automatically said yes to the changes lol. it took about 15 minutes - i went downstairs and made tea and breakfast and it was still going when i got back.

[QUOTE=glinsvad]Et tu? For some reason Breezy has started exhaling on me - complete power off in a matter of split seconds :shock:. Is that what's been happening to you as well?[/QUOTE]
no, i think my problems have been fsck related. i'm mainly not around when my computer shuts down because i listen to podcasts as i go to sleep and use shutdown -h to turn it off.

however, when i do see it shutdown %90 of the time it's fine, but sometimes it hangs on the desktop of about 30-50 seconds before starting the 'text' shutdown where it shows you shutdown process e.g. changing to runlevel 6 etc, etc.

[QUOTE=glinsvad]
Why not? Vires acquirit eundo
[http://www.yuni.com/library/latin_8.html]("http://www.yuni.com/library/latin_8.html")

EDIT: Revera linguam latinam vix cognovi[/QUOTE]
i'm a fairly serious person, so i think what i have is fine. i'm thinking very hard about using this instead -
Volo anaticulam cumminosam meam!

---

### Post by glinsvad on 2006-05-24
[QUOTE=ice60]
i ended up putting a big screwdriver upturned on the 'y' key and resting it on the monitor so i'd automatically said yes to the changes lol.
[/QUOTE]
He he that's ingenuity.

In the future use the yes-command to continuously pipe 'y' to fsck like this:
```

yes | fsck whatever

```

[QUOTE=ice60]
i'm a fairly serious person, so i think what i have is fine. i'm thinking very hard about using this instead -
Volo anaticulam cumminosam meam![/QUOTE]
:mrgreen: Also a lesser known counterpoint to your current signature would be Adversus solem ne loquitor

---

### Post by tonyr on 2006-05-24
[QUOTE=glinsvad]
In the future use the yes-command to continuously pipe 'y' to fsck like this:
[/QUOTE]

**fsck** has a **-y** option that means, as you might have guessed,
'say **yes** to everything'.  It should apply to all linux related partition
types.  There are some that don't use it.  See **man fsck**.

---

### Post by ice60 on 2006-05-24
[QUOTE=glinsvad]He he that's ingenuity.

In the future use the yes-command to continuously pipe 'y' to fsck like this:
```

yes | fsck whatever

```
[/QUOTE]thanks, i wonder when i might next need it, i sometimes start/shutdown Ubuntu 3 times aday so was thinking of changing fsck to more than every 30 reboots, but as i have these spasmodic errors i should leave it. anyway, i have a new HDD i'm going to use for Dapper in a couple of weeks
[QUOTE=glinsvad]
:mrgreen: Also a lesser known counterpoint to your current signature would be Adversus solem ne loquitor[/QUOTE]i could have done with that when i first took an interest in politics :mrgreen:  roflmao

---

### Post by ice60 on 2006-05-24
[QUOTE=tonyr]**fsck** has a **-y** option that means, as you might have guessed,
'say **yes** to everything'.  It should apply to all linux related partition
types.  There are some that don't use it.  See **man fsck**.[/QUOTE]
thanks, next time anything happens and i'm stuck in the CLI i'll remember to use man, i hadn't thought of that :rolleyes:

---

