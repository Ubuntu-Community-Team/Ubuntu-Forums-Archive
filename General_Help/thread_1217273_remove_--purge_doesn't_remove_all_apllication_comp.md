---
title: "/remove --purge/ doesn't remove all apllication components/files !"
date: 2009-07-19
forum: General Help
---

### Post by credobyte on 2009-07-19
I was in need of a Wine support and made a temporary install ( to uninstall in a few minutes ), but when trying to remove it, a few folders were left on my PC.
$HOME/.wine folder was still there, containing a few mysterious files, /usr/share/wine wasn't removed as well.

How do I get apt to remove ALL files related to what I'm going to remove ? --purge should remove all configuration files, etc. - am I wrong ?

---

### Post by wojox on 2009-07-19
I use :

```
sudo apt-get --purge remove <application>
```

Then it takes all your config files as well.

---

### Post by credobyte on 2009-07-19
> **wojox said:**
> I use :

```
sudo apt-get --purge remove <application>
```Then it takes all your config files as well.

Well, that's exactly the way I do it, however, not everything gets removed. Not to complain as much as about Wine, than the whole idea in general. How I can ensure that I've removed everything, not just some part of my application ?

---

### Post by raymondh on 2009-07-19
I really am uncomfortable with suggesting rm commands so I'll just link you to a [blog post]("http://www.nyutech.com/2009/03/how-to-install-and-completely-remove.html").  Read and decide.

Good luck.

---

### Post by credobyte on 2009-07-19
> **raymondhenson said:**
> I really am uncomfortable with suggesting rm commands so I'll just link you to a [blog post]("http://www.nyutech.com/2009/03/how-to-install-and-completely-remove.html").  Read and decide.

Good luck.

Oh, looks like there are a few more directories left on my PC ( according to this blog post ) :( Anyway, I've finally completelly removed Wine, tough, I would be more interested on finding an answer to another question - is there a way to remove application and all it's components/configuration files ( not made by me ) and be sure that there's nothing left ? 
Do I really need to go through all common directories, search for related files and delete them manually ?

---

### Post by Shpongle on 2009-07-19
i dont know if this is the same as purge but what about the completely remove option in synaptic?

---

### Post by credobyte on 2009-07-19
> **DillByrne said:**
> i dont know if this is the same as purge but what about the completely remove option in synaptic?

Will take a look at it, thnx ( haven't used Synaptic for months ).

---

### Post by lswb on 2009-07-19
In general, the purge command will remove system files but will not delete files in a user's home directory. any ~/.whatever config files created in a user home directory by the program being removed must be deleted by the user.

The purge command *should* remove all system files installed by a package. However, the removal scripts can sometimes be incorrect and fail to identify all files that should be removed. This would be a bug in the package, it probably does not happen too often, but it is possible that an old config file here or there may not be removed when a package is purged.

---

### Post by credobyte on 2009-07-19
> **lswb said:**
> In general, the purge command will remove system files but will not delete files in a user's home directory. any ~/.whatever config files created in a user home directory by the program being removed must be deleted by the user.

The purge command *should* remove all system files installed by a package. However, the removal scripts can sometimes be incorrect and fail to identify all files that should be removed. This would be a bug in the package, it probably does not happen too often, but it is possible that an old config file here or there may not be removed when a package is purged.

Is there a way to configure aptitude to remove files from my home directory ( if any ) as well as from other places ? VirtualBox does the same thing .. uninstalling doesn't remove virtual hdd's and a few more config files.

---

### Post by wojox on 2009-07-19
Cool blog. I just went through all my hidden folders in HOME and found a few things I uninstalled months ago. I might need to create a bash script to purge HOME directory of obselete files after uninstall? hmmmmmmm...

---

