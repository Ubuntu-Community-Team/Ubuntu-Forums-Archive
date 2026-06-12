---
title: "Basic help for new Ubuntu user"
date: 2010-03-22
forum: General Help
---

### Post by Rubi1200 on 2010-03-22
Well, I took the plunge and installed Karmic Koala on my laptop. I have to say that I am very pleased and impressed with what I have seen so far. On to the questions:
1. Is it advisable to install a firewall if my wireless router firewall passes online tests such as GRC Shields Up etc?
2. Is it possible to install third-party antivirus programs from vendors such as Avira and Avast (both offer Linux packages) and is it advisable to do so?
3. Are there programs available for Ubuntu such as Nirsoft's CurrPorts? (sorry for being such a Windows looooser ;))
4. How problematic is it in Linux to install and uninstall programs; I am referring to the kind of problems encountered in Windows such as hardware/software conflicts etc?
I really appreciate all responses.
Oh, and btw, I don't think I will be hurrying back to Windows anytime soon!

---

### Post by lotharmat on 2010-03-22
Hi, and welcome to the forums,

Unless you plan on running a server that allows Windows machines to connect to it; you do not need a firewall or antivirus.

Getting programs in Ubuntu is as easy as clicking on Applications --> Add / Remove Software. All the software in there is in the Ubuntu repositories and will have been thoroughly tested with the version of Ubuntu that you are using!

---

### Post by Rubi1200 on 2010-03-22
Thanks, I appreciate the quick response!
I do not plan on running a server and will take your advice not to install security software such as a firewall and antivirus.
Another quick question:
As I understand it, when the new version (Lucid) is released as a stable version, it will be possible to upgrade without a complete re-install. Is this correct?

---

### Post by sandyd on 2010-03-22
> **Rubi1200 said:**
> Thanks, I appreciate the quick response!
I do not plan on running a server and will take your advice not to install security software such as a firewall and antivirus.
Another quick question:
As I understand it, when the new version (Lucid) is released as a stable version, it will be possible to upgrade without a complete re-install. Is this correct?
yes, this is correct. You can upgrade from the update-manager.
It will automatically notify you of a new release when one exists.

you can manually run the update manager to upgrade the system through
```
update-manager -d
```

---

### Post by lotharmat on 2010-03-22
It is worth bearing in mind though, that some people have had issues when upgrading.

If you have only just installed Ubuntu it *may* be worth treating this as a dry run and not getting too attached to it.

Personally, I'd go for a re-install when Lucid pounces!

It would also be a good idea to create a separate /home partition that way reinstallation is not painful and settings are preserved! (you will still have to reinstall your programs again but I'm a bit OCD and keep a list of what I install so I can quickly get it back after a reinstall!)

---

### Post by Rubi1200 on 2010-03-22
Thanks guys!!
This kind of support makes the experience all the easier.
I only installed a few days ago and will probably stick with what I have for the moment because I want to get used to the way things work.
Again, many thanks.

---

