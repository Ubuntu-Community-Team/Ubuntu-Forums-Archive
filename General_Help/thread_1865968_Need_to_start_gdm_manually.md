---
title: "Need to start gdm manually?"
date: 2011-10-20
forum: General Help
---

### Post by macho on 2011-10-20
I just upgraded to Oneiric and *adore* it. I lost power during the installation and had to resume, though. Normally that kind of thing causes me severe problems, but this time, the only lingering problem seems to be that gdm won't start on its own. I get the graphical "ubuntu" screen for a second, then it drops to a terminal that ends with text something like this (there's more but I'm unable to use my mouse to copy/paste):

```

* Starting anac(h)ronistic cron                        [ OK ]
* Stopping anac(h)ronistic cron                        [ OK ]
* Starting MySQL Server                                [ OK ]
* Checking battery state...                            [ OK ]
* Stopping System V runlevel compatibility             [ OK ]
```

If I Ctrl+Alt+F1, login, and do

```
$ sudo service gdm start
```

things seem to go fine, but this is annoying to do after every reboot. Any thoughts on solutions?

Here's some added info: I'm running on a Thinkpad X220 with an encrypted home folder.

dmesg/syslog give these two lines many many many times in a row:

```
[  931.659926] Valid eCryptfs headers not found in file header region or xattr region
[  931.659930] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
```

Thanks for your help!

---

### Post by dniMretsaM on 2011-10-20
It might have something to do with the fact that Oneiric uses LightDM by default.

---

### Post by goldentony111 on 2011-10-20
> **dniMretsaM said:**
> It might have something to do with the fact that Oneiric uses LightDM by default.

thanks, this is it

---

### Post by macho on 2011-10-20
> **dniMretsaM said:**
> It might have something to do with the fact that Oneiric uses LightDM by default.

Good to know! I have the lightdm package installed, but in bootup-manager I don't see it as an option. Any other thoughts?

---

### Post by macho on 2011-10-21
Turns out it was a dependency problem, installing lightdm-gtk-greeter fixed it.

Some other solutions—which didn't work for me, but may work for others—are [in this thread]("http://ubuntuforums.org/showthread.php?t=1859951").

---

