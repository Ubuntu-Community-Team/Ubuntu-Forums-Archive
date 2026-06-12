---
title: "Problem installing apps through terminal"
date: 2010-09-22
forum: General Help
---

### Post by kabeza on 2010-09-22
Hi
I'm having trouble adding software through terminal.
- I'm behind a proxy
- I've configured proxy in System -> Preferences -> Proxy
- I've configured proxy in Synaptic preferences

[[IMG]http://img6.imageshack.us/img6/6913/screenshot011ez.th.jpg[/IMG]](http://img6.imageshack.us/i/screenshot011ez.jpg/)

- I can browse correctly to this url (through firefox)
[https://launchpad.net/api/1.0/~docky-core/+archive/ppa](https://launchpad.net/api/1.0/~docky-core/+archive/ppa)

===========================================

Problem 2 - derived from above -
I have to reinstall these packages

docky
docky-dbg
exaile
libgio-cil

How should I backup docky config settings (from gconf-editor) so I can restore them back once I fix/reinstall these packages problems?

Thanks

---

### Post by anirudhtomer on 2010-09-22
You might be knowing that all configuration settings are in /etc folder. So search for docky's configuration setting in that and save it somewhere else as a backup.
Since I am not used to gconf-editor I would have searched for docky's config settings file using "find" in that /etc folder.

Edited:

I just saw how gconf-editor gives you access to configuration files. It gives you access to change individual parameter and it makes changes in the background to the config file. 
So its better that you find the config file & save it rather than using gconf-editor.

---

### Post by regala on 2010-09-22
> **anirudhtomer said:**
> 
Edited:

I just saw how gconf-editor gives you access to configuration files. It gives you access to change individual parameter and it makes changes in the background to the config file. 
So its better that you find the config file & save it rather than using gconf-editor.

but user configuration changes on configuration handled by gconf cannot be in /etc, since common users don't usually have the right to directly write in /etc or files in it, without using sudo.
the config files are usually in the user's home directory, mostly "dotted" files (first character of the name is '.'). either ".docky" directory, or in a subdir of ".config".

br, mathieu

---

### Post by kabeza on 2010-09-22
i've previously checked.
Docky doesn't save settings in /etc nor /home/xxx/.xxx dotted folders

PS: does any1 know about the problem of adding repositories in terminal through proxy?

---

### Post by regala on 2010-09-23
> **kabeza said:**
> i've previously checked.
Docky doesn't save settings in /etc nor /home/xxx/.xxx dotted folders


have you search in directory $HOME/.gconf/docky/ ?

> 
PS: does any1 know about the problem of adding repositories in terminal through proxy?

you have to specify a proxy in /etc/apt/apt.conf, if you want apt-get or aptitude commands to use a proxy.
```

man apt.conf

```

---

### Post by kabeza on 2010-09-24
Damn... this is weird

1) there's no $HOME/.gconf/docky/ folder in that place

2) the apt.conf already has a proxy:

```
Acquire::http::proxy "http://10.*.*.1:65**/";
Acquire::ftp::proxy "ftp://10.*.*.1:65**/";
Acquire::https::proxy "https://10.*.*.1:65**/";
```

I'll remove these references to see if it goes through without it, I hope the changes apply without rebooting

---

