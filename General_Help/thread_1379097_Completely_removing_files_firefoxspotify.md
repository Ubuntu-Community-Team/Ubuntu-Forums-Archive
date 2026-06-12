---
title: "Completely removing files firefox/spotify"
date: 2010-01-12
forum: General Help
---

### Post by ewan86 on 2010-01-12
Wine was giving me problems so I tried reinstalling. Depending on whether I launched it with gnome do or the main menu I got a different 'version' of spotify, I could tell this because it had different searches remembered. I tried removing wine and spotify and gnome do via synaptic and completely remove and then the option to remove configuration files left over. I did a search and there were loads of wine files left so I just deleted. When I reinstalled wine, spotify and gnome do the same problem occurred. 

Also Firefox started crashing ubuntu, just freezing it, so I tried to uninstall completely, but when I restarted it kept the same add ons and still crashed. So I uninstalled again and tried to delete all firefox folders but I can't work out how to do it as root!!

Any ideas? :confused:

---

### Post by audiomick on 2010-01-12
> **ewan86 said:**
> ... but I can't work out how to do it as root!!

Any ideas? :confused:

Either "sudo" and a space before a terminal command, or open the file browser as root with
```
gksu nautilus
```

In both cases you will be asked for your password. The one you log in with is the one you need. When you type your password in the terminal, you wont see what you are typing.

**Make sure you know what you are doing with this**. Giving yourself root privileges allows you to break your system.

---

### Post by ewan86 on 2010-01-12
> **audiomick said:**
> Either "sudo" and a space before a terminal command, or open the file browser as root with
```
gksu nautilus
```

In both cases you will be asked for your password. The one you log in with is the one you need. When you type your password in the terminal, you wont see what you are typing.

**Make sure you know what you are doing with this**. Giving yourself root privileges allows you to break your system.

Thank you, I will give this a go and see if it I can do it. I'm assuming if synaptic says wine and firefox are not installed it is safe to remove files with that name? I'm thinking there is files in filesystem in etc/firefox and in usr/lib under firefox as well.

If I do break the system my files are backed up so I'm not too worried, experimentation is the best way to learn :D

---

### Post by audiomick on 2010-01-12
> **ewan86 said:**
> I'm assuming if synaptic says wine and firefox are not installed it is safe to remove files with that name?

I guess that this is true, but it is a guess...;)

---

### Post by ewan86 on 2010-01-12
well gksu nautilus worked a treat and I searched the filesystem and removed all traces of Firefox that I could find, when I reinstalled it and started it up it not only still had my add ons but it had a list of the pages I had open when I last closed it down!!!:rolleyes:

---

### Post by howefield on 2010-01-12
> **ewan86 said:**
> when I reinstalled it and started it up it not only still had my add ons but it had a list of the pages I had open when I last closed it down


Did you delete the .mozilla folder in your /home ?

---

### Post by ewan86 on 2010-01-12
> **howefield said:**
> Did you delete the .mozilla folder in your /home ?

Oh my flippin hec!! I have been reading about people saying about config folders in their home directories for ages and I have been really confused as I only have documents and pics and suchlike in their, so I thought I had the home folder confused or my comp was set up differently somehow!!

But when you just said I had a brain wave (for a computer illiterate like me) and clicked view and marked show hidden files and lo and behold there was .mozilla!!!

Unfortunately I haven't got time to see if it works now but will post here to say how it went.

Thank you all for help today learnt some good stuff :D

---

### Post by howefield on 2010-01-12
> **ewan86 said:**
> I had a brain wave (for a computer illiterate like me) and clicked view and marked show hidden files and lo and behold there was .mozilla!!!

Nice one, the period before the file/folder name makes it hidden, and Ctrl + H will show any hidden files/folders. (Or the nautilus menu option that you used, View > Show Hidden Files)

---

### Post by ewan86 on 2010-01-12
Superb!!! Managed to completely remove all the Firefox and Wine files including the config ones in home when uninstalling,(though I couldn't find any gnome-do ones but it doesn't seem to be a problem).

Reinstalled them all now working so far as planned and no Firefox freeze up as of yet. Best of all though the fresh install has got my spotify in wine working excellently now, was very ropey before so I am dead chuffed :D

Thank you both!!:D

---

