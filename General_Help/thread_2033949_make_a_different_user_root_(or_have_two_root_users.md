---
title: "make a different user root (or have two root users)"
date: 2012-07-27
forum: General Help
---

### Post by Subito Piano on 2012-07-27
Hi!  I really messed up my system, finally fixing it by a complete reinstall with my original username "dad" as the primary user and restoring my saved files.  It still gave me problems (such as no menu) - so i created a new user "mr_d" and moved all my files from "dad" to "mr_d," except some configuration files.  It's working great - but first I had to give "mr_d"  root privileges AND change ownership of all files from "root" to "mr_d."  

Unfortunately, there are some glitches remaining -- such as when I install a program, it comes automatically with "root" as the owner.  Is there a way i can make "mr_d" the root user instead of "dad" -- ?  Or if i even could make them BOTH "root,"  that would be helpful.  I can see down the road a few years when i get a new laptop or something, all these permissions/ownerships could really be goofed up unless i can replace "dad" with "mr_d" as the primary user (or have two "roots") and let all things be owned by "root."

Any thoughts appreciated...this all has cost me tons of time...

---

### Post by CatKiller on 2012-07-27
There is, and can only be, one root. Giving another user sudo privileges is really simple, though.

There is no "primary" user. Give ownership of user files to the user who should own them and stop mucking about with the others.

---

### Post by Subito Piano on 2012-07-27
Yeah i did change ownership but new downloads come in with root as owner and i can't open them 'til i change that.  It's not just an inconvenience, i fear it could turn out to be a big problem later.  I want to tranfer root from the old username to the new.

---

### Post by CatKiller on 2012-07-27
That's because the ownership of the Downloads directory is wrong. I can't remember the name of it, but one of the permissions is to allow new files to inherit the ownership of the parent directory.

EDIT: Or you're running whatever is creating the files as root. Don't do this.

---

### Post by arpanaut on 2012-07-27
This link might help you to understand things better:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

goodluck

---

### Post by Subito Piano on 2012-07-27
Thanks, guys. Nothing much new on the page -- i'm neither expert nor newbie.  I will see how things go, maybe try wiping everything in the home folder of user "dad," and copying some files from "mr_d" to "dad" and testing.  If all goes well i'll try a few more, then eventually move all the files back to "dad" and return ownership to "root" again.  (Assuming the primary user's files are supposed to be owned by "root" --- ????)

---

### Post by lisati on 2012-07-28
For "root"/superuser privileges, the preferred method of elevating privileges that is supported through this forum is the "sudo" command: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
More information can be found here: [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

@galvatron408: Although not strictly a violation of [this thread]("http://ubuntuforums.org/showthread.php?t=716201"), your suggestion seems a bit risky to me.

---

### Post by galvatron408 on 2012-07-28
He asked:

"Unfortunately, there are some glitches remaining -- such as when I  install a program, it comes automatically with "root" as the owner.  Is  there a way i can make "mr_d" the root user instead of "dad" -- ?  Or if  i even could make them BOTH "root,"  that would be helpful.  I can see  down the road a few years when i get a new laptop or something, all  these permissions/ownerships could really be goofed up unless i can  replace "dad" with "mr_d" as the primary user (or have two "roots") and  let all things be owned by "root.""

I answered. There's nothing wrong with showing someone how to do something they asked.

If someone said, "How do you blow away a partition" and you say.... use fdisk and do this and that. fdisk'ing a partition is quite dangerous but it is what they want.

Think about it.

Anyway, on a side note. There's too much police'ing going on. You know. It's fine if someone is maliciously posting a trick answer but I would never do that. ;)

---

### Post by CatKiller on 2012-07-28
> **Subito Piano said:**
>  (Assuming the primary user's files are supposed to be owned by "root" --- ????)

I don't know why you'd assume that when I've already told you that it isn't true.

A user's files should be owned by that user. There is no "primary" user. Using root when you don't know what you're doing is a Bad Plan.

---

### Post by Subito Piano on 2012-07-28
Hmm -- there might be some misunderstandings going on here, perhaps I've not been clear.

First -- I very much appreciate everyone's advice.

_Lisati & Cat Killer_: Yeah, I already visudo'd the sudoers file.  "mr_d" and "dad" are both members of the root group. I'm still having a hard time with files owned by "root."  They were not owned by "dad," even though copied from "dad's" partition.  These were documents, pictures, etc., not system files.  I changed ownership and can now manipulate these BUT still when I download, permissions come as "root."  I don't know why personal files copied from user "dad" would be owned by "root" instead of "dad" -- UNLESS perhaps because I used Puppy to copy them...but that does NOT make sense.  I've used Puppy for years for this kind of thing without problems, so I'm perplexed.

_ALL_:  I'm not trying to use Ubuntu as root -- I've been using Linux for maybe 10 years now and know the dangers (well -- not completely or i wouldn't be in this mess now, would I??  :P ).  I just don't see how these files have "root" as their owner...weird.  That's the reason I asked about the "primary user," I have no explanation for it.

Anyway -- ideas welcome, different opinions are as well...and momentarily things seem to work fine, but it's only day 3...

---

### Post by CatKiller on 2012-07-28
You don't need to muck about with the sudoers file and neither user should be in the root group. That is the user personal group of root and should only contain root. I believe you've got confused with the admin group, which can contain ornery users, and controls which users are able to call sudo.

As I understand it, your ownership got messed up because you used root to restore from some kind of backup. Change the ownership of user files so that they are owned by that user and stop trying to become root.

The only way new files would become owned by root (that I know about, anyway) is because either the program that created them was run as root or because the parent directory is owned by root & they are inheriting ownership.

EDIT: Or the files are on a different partition & you've done something funny with your fstab.

---

### Post by Subito Piano on 2012-07-28
OK - I try```
sudo useradd -g adm mr_d
```and it tells me ```
user 'mr_d' already exists
```How do I add an _existing_ user to the admin group?

---

### Post by CatKiller on 2012-07-29
> **Subito Piano said:**
> How do I add an _existing_ user to the admin group?

Through the Users and Groups tool, or with ```
sudo adduser mr_d admin
```

---

### Post by BkkBonanza on 2012-07-29
Your files were owned by root because you used the sudo command to copy/move them from dad to mr_d. You had to do that because when logged in as mr_d you can't get access to dad's files.

You fix that by using chown to change the ownership to the correct new owner. eg.

sudo chown mr_d path/to/files

Programs are always installed as owned by root but they run as whatever user starts them. So if you use sudo to run a program then it's running as root and will alter files usually as root. Run the program as mr_d and it will create new files owned by mr_d.

There is a file mode you can set to make files under a directory inherit the parent ownership. If you did that by accident then you could get unsual behaviour. These are the setuid/setgid modes (on directories only).

---

### Post by Morbius1 on 2012-07-29
> **Subito Piano said:**
> How do I add an _existing_ user to the admin group?
```
sudo gpasswd -a mr_d sudo
```[COLOR=Blue][I]Note: This will also work:
```
sudo gpasswd -a mr_d admin
```But keep in mind that there is no "admin" group any longer. Ubuntu allows you to use it in CLI for compatibility reasons since it wisely assumes that no one reads the release notes - [/I][/COLOR][COLOR=Blue]*I know I didn't.*[/COLOR][COLOR=Blue][COLOR=Black]

This is a very confusing thread btw and I'm not sure what's going on but you might want to compare the output of these commands to see if there are any differences:
[/COLOR][/COLOR]```
[COLOR=Black]id dad[/COLOR]
```[COLOR=Blue][COLOR=Black]
[/COLOR][/COLOR]```
[COLOR=Black]id mr_d[/COLOR]
```[COLOR=Blue][COLOR=Black]
[/COLOR][/COLOR]

---

### Post by Subito Piano on 2012-07-29
Yeah, this certainly is confusing - BUT the lights are coming on....!!! [IMG]https://empowering247.com/light-bulb36.png[/IMG] (Bkk -- thanks, that would explain the weird permission change.)

The way things stand at the moment is that adding myself as root gave me all the access i needed, but I still have to use "sudo" to do root-level work (which is definitely the way i want it).  However, looking at this: 

```
mr_d@dad:~$ id dad
uid=1000(dad) gid=1000(dad) groups=1000(dad),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),107(lpadmin),115(sambashare)
mr_d@dad:~$ id mr_d
uid=1002(mr_d) gid=1002(mr_d) groups=1002(mr_d),0(root)
```


 I'm thinking i need to add user "mr_d" to the same groups that user "dad" is in (adm, cdrom, sudo, and dip), take "mr_d" OUT of the root group, then STOP!  :)  Or should i leave things as they are?

Also "dad" and "mr_d" are in different groups and have different gid's.  Should i leave that alone or change mr_d to gid=1000 and group 1000?  (My hunch is to leave well enough alone...)

Danke, danke....i think this thread is almost finished.

---

