---
title: "Update Manager"
date: 2006-06-25
forum: General Help
---

### Post by MarvinZurcher on 2006-06-25
When I click on update manager the window jusst flashes on the screen then then it is gone. I can't use the updater. The last ime I used it ,it didn't work I got these messases.[ATTACH]11741[/ATTACH]

[ATTACH]11742[/ATTACH]

[ATTACH]11743[/ATTACH]

---

### Post by tonyr on 2006-06-25
These probably mean exactly what they say: either a network link is down
somewhere, or the repos in question are offline or unavailable for xome reason.

I expect your local network access is OK since you are posting here.  Wait
a while and try again.  You could also try to ftp to therepo sites directly.

---

### Post by MarvinZurcher on 2006-06-25
Update Manager still does not work and Synaptic Package Manager doesn't either. I get thiss message when trying to run Synaptic Package Manager.

---

### Post by tonyr on 2006-06-25
Make  backup copy of /etc/apt/sources.list:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak

```

Post **/etc/apt/sources.list** here.

In Synaptic, go to **Settings->Repositories** and see what that says about your 
repositories list.

Try replacing your existing repositories file /etc/apt/source.list with a default version.
Here's mine:
```

#
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Alpha i386 (20060329.1)]/ dapper main restricted


# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Alpha i386 (20060329.1)]/ dapper main restricted

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe
# deb http://us.archive.ubuntu.com/ubuntu/ dapper multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

Note that I use **us** repositories. There are also **eu**, **ca**, and **gb** repositories, and possibly others.

---

### Post by MarvinZurcher on 2006-06-25
When I clicked on Synaptic Package Manager Settings->Repositories I got this.](*,)

---

### Post by tonyr on 2006-06-25
It's acting like your repositories file is bad, or something about Synaptic's ability
to read the repositories file is broken.

Open a terminal (Applications->Accessories->Terminal) and type this:
```

ls -l /etc/apt
cat /etc/apt/sources.list

```

and post the results.

Then in the same terminal type
```

sudp apt-get update

```

and report that result, too.

---

### Post by MarvinZurcher on 2006-06-26
Here are the screens.

---

### Post by tonyr on 2006-06-26
By George!  That's it!

There is supposed to be a file named **sources.list** in the directory **/etc/apt**,
and it's **not there**!   Where did it go???? Who knows?!?!?

In a terminal do
```

sudo cp /etc/apt/sources.list_backup_200606212007 /etc/apt/sources.list

```

and try your Update Manager again.  You may need to re-login.


EDIT: Fortunately, the Update Manager or Synaptic or somebody makes backup copies
of **sources.list** automatically.  The one I chose is the most recent one, as the date
in the name indicates.

---

### Post by MarvinZurcher on 2006-06-26
Thanks tonyr. That got the update manager to appear on the screen but there is still something wrong with it. I get this message when I run update mgr.

---

### Post by Jasper Houtman on 2006-06-26
Nothing to worry about.
Either that server is busy or otherwise temporarily unavailable.
Or they are nolonger online, if it keeps giving you that alert over the next couple of days then just remove those repositories from the sources list.

---

### Post by MarvinZurcher on 2006-06-26
Thanks Jasper.

---

### Post by tonyr on 2006-06-26
These repositories do not appear to exist anymore.  The 
**[http://theli.free.fr/packages/breezy](http://theli.free.fr/packages/breezy)** URL has been marked **obsolete**.
There is a **dapper** repository there, however.  You might try changing
your repository entry to use that (if you are using Dapper 6.0.6 LTS).

I couldn't find any trace of **[http://koti.mbnet.fi/~ots](http://koti.mbnet.fi/~ots)** at all.

To get Update Manager to work anyway, remove these references from
your repository list.   If you really need whatever is in those repositories,
the **dapper** repo at **theli.free.fr** may have what you want,  but you'll
have to chase down the stuff that was at **koti.mbnet.fi/~ots** yourself.

EDIT:  That **~ots** probably means that the directory was in a personal
account maintained and/or served at that URL (**theli**).  The owner may
have moved, or the structure of accounts management at the server may have 
changed.

---

### Post by MarvinZurcher on 2006-06-26
HOW DO i CHANGE THE REPOSITORY?

---

### Post by tonyr on 2006-06-26
In Synaptic, under **Settings->Repositories**, find the one you are interested in and
select it.  The set of actions on the side should now include **Add**, **Remove**, and **Edit**.
Go for it.

You can also edit **/etc/apt/sources.list** directly, as **root**, using the **sudo**
command with an editor of your choice.  I do
```

sudo vi /etc/apt/sources.list

```

since I use the **vi** editor.  Other popular simple editors are **nano** and
**gedit**.

---

### Post by MarvinZurcher on 2006-07-01
The update manager will not download updates. I get this message. I don't know what I did wrong or if it is a bug.[EMAIL="tazano815@yahoo.com"]tazano815@yahoo.com[/EMAIL]

---

### Post by tonyr on 2006-07-01
This usually means that the file was not available at the repository.  Either it is not there
or the repository is off line.   If this is the problem, you can wait awhile and try again. The 
version of the file that failed to update is rather old for Ubuntu 6.0.6 LTS.  The file/version 
I see on my machine is **libmysqlclient14_4.1.15-1ubuntu5_i386.deb**.

---

### Post by MarvinZurcher on 2006-07-04
Thanks tonyr everything seems to be working for the time being. I don't know anything about computers, and without help I'am lost.

---

### Post by tonyr on 2006-07-04
It's a great adventure.  Sally forth.  Don't trust 'em.  Carry a big nerf hammer to smite
them with when things aren't going right. Don't be afraid to reboot. Backup. Don't
be afraid to re-install. Ask questions.  Answer questions.

Good luck.

---

