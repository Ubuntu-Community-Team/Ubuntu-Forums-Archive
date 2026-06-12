---
title: "AutoCreate Script"
date: 2011-03-20
forum: General Help
---

### Post by OldManRiver on 2011-03-20
All,

I noticed that the "Snaptic Package Manager" has an option to "Generate Package download script"  which I ran but noticed these 2 shortfalls:
[LIST=1]
[*]Uses the wget command instead of "apt-get install"
[*]Does not actually locate all installed packages
[/LIST]
I was wanting to replicate the install on one machine to another and thought this would really be great if it could be used in that mode, but without the correction of these two problems, would still be a difficult process to replicate a machine.

Does anyone know how/where an autocreate script is or can be made for such a replication process?

Thanks!

OMR

---

### Post by tredegar on 2011-03-29
See [here]("http://www.linuxquestions.org/questions/linux-newbie-8/transferring-packages-to-new-install-debian-542460/")
Post #6 is relevant.

---

### Post by OldManRiver on 2011-05-02
All,

Well learned how to use:
```
dpkg --get-selections > /home/ins_packages.txt

``` to record existing apps and
```
dpkg --set-selections < /home/ins_packages.txt & dselect install
``` to restore, but now in order for the full "AutoCreate" to work right need to learn how to capture the existing launchers and restore them.

Anyone know that one?

Thanks!

OMR

---

### Post by Crusty Old Fart on 2011-05-02
I don't know how relevant this might be for what you're trying to do. However, in my early days with Ubuntu, I would hose the sytem so badly at times that I needed to reinstall it to have any hopes of getting it working again. Two directories became crucial for me: /etc and /home. As time progressed, I learned that making daily backups of those two directories made re-installations a breeze (in addition to what you have learned regarding dpkg).

So, reinstalling isn't much different than cloning. You should be able to get a successful clone by installing on a new machine, replacing the default /etc and /home directories with the backups you have made of them and then running your command:
```

dpkg --set-selections < /home/ins_packages.txt & dselect install
```

I don't know ***exactly*** where the launcher data is stored, But whenever I've followed the procedure I just described, I got all of my launchers back as well as everything else I had custom configured on my desktop.

Best of luck to you,

Crusty

---

### Post by OldManRiver on 2011-05-13
Crusty,

Lucky you I'm not getting that, probably because I have custom hand made launchers that are not part of a package install, so the dpkg command can not process these special launchers.

That is why I need to know where they reside so I can find a way to either copy them out to a resource or autogen them by commands within a script.

I'll keep this out there and hope someone has the information I need.

Thanks!

OMR

---

### Post by Crusty Old Fart on 2011-05-13
My launchers were custom hand made as well.
Have you taken a look in:
```

~/.gnome2/panel2.d/default/launchers

```That might not be all you need to clone them though. Part of the cloning trick would be to have them regenerated on the panels and/or desktop where they belong.
You may find some indication of what else you might need by examining the output from the following command:
```

ls -alR ~ | grep launcher

```

There may be other things to consider, which is why I decided to just backup my home and etc directories, rather than trying to find all the files that contained launcher data.

Good Luck,

Crusty

---

### Post by OldManRiver on 2011-05-19
Crusty,

I was working with something else and noticed that all the launcher defs are in:

/home/user/.gconf

so saving this directory and all it's xml crap saves all the launcher stuff, according to what I see.

Gonna try it.  Think I'll write a script to send it to .tar or .tar.gz.

Thanks!

OMR

---

### Post by OldManRiver on 2012-06-08
All,

Reviewing all my "OPEN" threads and trying to "CLOSE" them and get them solved.  

I'm numbering them.  This is Thread #30 in my series.

Your help in getting them resolved, closed, SOLVED, is appreciated!

On this one the dpkg select/dpkg install worked on versions prior to 10.04 but no longer work on version 10.04 and later.

OMR

---

