---
title: "don't know how to install."
date: 2009-09-07
forum: General Help
---

### Post by morerats on 2009-09-07
i just installed ubuntu from the live disc i burnt a few days back, however i need some help please.

i've downloaded smoothwall express as this is a firewall i believe? i did look for firestarter in add/remove but couldn't find it.

anyway i have two smoothwall icons on the desktop. one says 3.0-sp1-x86_64 and the other is the same but with .iso on the end. my question is what do i do now!!!
i am also currently downloading the free avg package too.

i've downloaded the flash player as well. i clicked on open with gdebi package installer, so i think i've installed it, but can't find it anywhere.

when i started downloaded the player i was asked what type, i clicked on deb, is that correct?
when i try to get to my favourite website i get a blank screen with 'i am alive' written on it, do you know what this is?

is it possible to check only on your own threads on the forum?

thanks.

---

### Post by ecmatter on 2009-09-07
Use ufw (uncomplicated firewall) instead.  It should already be installed on your system.

Open Terminal and type:

```

ufw enable

```

Followed by:

```

ufw default deny

```

If the terminal spits out something to the effect 'ufw:command not found', then ufw isn't installed on your system.  Add it by typing:

```

sudo apt-get install ufw

```

And then run the commands to enable ufw and set the default policy.

---

### Post by ecmatter on 2009-09-07
that should be:

```

sudo ufw enable

```

and...

```

sudo ufw default deny

```

---

### Post by morerats on 2009-09-07
thanks for that.

do i open 'terminal' and do this? i tried it there but kept being told
You need to be root to run this script, don't know what that means.

---

### Post by The Cog on 2009-09-07
> **morerats said:**
> thanks for that.

do i open 'terminal' and do this? i tried it there but kept being told
You need to be root to run this script, don't know what that means.
Yes. From the menu, Applications->Accessories->Terminal.

root is the name of the account that has full rights over the whole machine. You should never actually log in as root for security reasons, but you can temporarily raise your priviledge (borrow the keys?) by using the sudo command.

Sudo runs the supplied command as root, so you should not have seem an error message saying you should be root. I don't know what went on there. Maybe you followed ecmatters first post where he forgot to put sudo in front?

See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by MelDJ on 2009-09-07
as for flash, did you try installing the flashplugin nonfree from synaptic package manager?

---

### Post by P4man on 2009-09-07
You most likely don't need a firewall.
On ubuntu, by default, nothing is listening on any incoming ports. Closing those ports with a firewall makes no difference. You only need a firewall if you're installing some services and you don't want ppl (or some ppl) to access it. For 99% of ubuntu users, a firewall is pointless (if it werent, it would be enabled by default).

> is it possible to check only on your own threads on the forum?

Yes. first of all, subscribe to your own threads. Then in "quick links" you'll see "subscribed threads". Another way is "search" and then "find all your threads".

---

### Post by morerats on 2009-09-07
i just went to system-accessories-synaptic package manager, and picked the flash player and installed it[i think!] i still have the same 'package' on my desktop, should that change?

so what is the usual procedure after downloading something, is there one particular way for everything?

thank you.

---

### Post by MelDJ on 2009-09-07
is this installed: flashplugin-nonfree?

---

### Post by morerats on 2009-09-07
no, the free one.

---

### Post by nothingspecial on 2009-09-07
remove the flash player you have and install flashplugin-nonfree.

Better still install the one direct from adobe`s website. There is a .deb file.

---

