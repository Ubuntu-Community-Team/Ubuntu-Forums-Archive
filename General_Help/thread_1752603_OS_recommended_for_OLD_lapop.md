---
title: "OS recommended for OLD lapop"
date: 2011-05-08
forum: General Help
---

### Post by helamsirrine on 2011-05-08
A friend of mine just picked up an old toshiba tecra 510CDT. It has a 2.1 Gb hdd, a pentium processor, and is running win2000 pro nt and that's about all I know about it because I don't have a live disk to boot it, and it win has a user password I can't bypass.

I was wondering if anyone here could recommend a small footprint, low spec linux OS for it. I'll burn a live disc, and wipe it. Not a lot of info to go on, I know, which is why I appeal to the expertise of the forum.

Thanks for any help.

---

### Post by andrew.46 on 2011-05-08
I guess the crucial point will be the amount of ram on this computer. If you were lucky enough to have 1 gig you would be sitting pretty :). If a live ubuntu cd will not run (have you tried this?) perhaps there is a factory sticker on the laptop with this info.

---

### Post by lykwydchykyn on 2011-05-08
wow!  I'm surprised Win2k will run on something that old.  I think your best bet is Slitaz, maybe Puppy if there's enough RAM; and if those fail then TinyCore.

I doubt any *buntu is going to perform on that machine.

---

### Post by andrew.46 on 2011-05-08
Oops... I did not realise this machine was so limited:

[http://www.toshiba-europe.com/bv/computers/products/notebooks/tecra510cdt/index.shtm](http://www.toshiba-europe.com/bv/computers/products/notebooks/tecra510cdt/index.shtm)

A maximum of 144mg ram, quite a challenge :)

---

### Post by sanderj on 2011-05-08
> **helamsirrine said:**
> A friend of mine just picked up an old toshiba tecra 510CDT. It has a 2.1 Gb hdd, a pentium processor, and is running win2000 pro nt and that's about all I know about it because I don't have a live disk to boot it, and it win has a user password I can't bypass.

I was wondering if anyone here could recommend a small footprint, low spec linux OS for it. I'll burn a live disc, and wipe it. Not a lot of info to go on, I know, which is why I appeal to the expertise of the forum.

Thanks for any help.

I googled for "tecra 510CDT", and the first hit (on Amazon) says:

"Toshiba Tecra 510CDT Notebook (133-MHz Pentium, 32 MB RAM, 2 GB hard drive)"

Ouch. CPU en harddrive match your description, so the RAM could match too. If so, you can't use any Ubuntu version on that hardware. Even Tiny Core has higher minimum requirements:

> What are the minimum requirements?
An absolute minimum of RAM is 48mb. TC won't boot with anything less, no matter how many terabytes of swap you have.
Microcore runs with 36mb of ram.
The minimum cpu is i486DX (486 with a math processor).

A recommended configuration:
Pentium 2 or better, 128mb of ram + some swap


So, I myself wouldn't use that laptop at all. 

If you want to use it, I would install Windows 95/98 on it. Reason: Rule of thumb: run an OS of the same 'vintage' as the hardware it's running on. As this Tecra seems to be from 1994, running Windows 95/98 (or Windows NT) on it would be the best choice IMHO.

Other solution if the owner wants to use it: reset the Win2000 password, and give it back to him/her.



HTH

---

### Post by pinballwizard on 2011-05-08
antiX

---

### Post by triceratops on 2011-05-08
Try DSL (Damn Small Linux).  It's a very low profile install that should get in under 100MB easily.  It's debian based, so it has apt-get, dpkg, alien, etc.

You probably won't be able to use a DE with your laptop.  Here are some other fun 'n' cool things to do with your old laptop:

* make a portable hardware router 

* install pine and use text-based email.  Pine ain't all that bad.  The configuration's a bit of a learning curve, but many of us used pine daily for years.  

* Use the laptop as a command-line learning system.

---

### Post by lykwydchykyn on 2011-05-08
Surely if it's running windows 2k it's been upgraded from 32M.  64 is recommended for win2k.

---

### Post by marshag63 on 2011-05-08
DamnSmallLinux will run on that if you make a swap partition for it to use.

I once had damnsmalllinux on a 133 MHz laptop and had somehow managed to dual boot damnsmalllinux with windows 3.1 on an old desktop(dual boot -it has happy accident).

Unfortunately, DSL is not being developed anymore, but its usable.

My other suggestion would be to use it as a learning project for a console only install (ala INX distro), but you would have to use a minimal install CD and build from there.  

Try out INX live CD to see what I mean - its surprisingly usable (I was able to have my shoutcast stream playing, be chatting in IRC and was using elinks text webbrowser to cruise the internet).  

Hope you have fun exploring and learning :)

mdg

---

### Post by debd on 2011-05-08
OMG

[http://www.toshiba-europe.com/bv/computers/products/notebooks/tecra510cdt/product.shtm](http://www.toshiba-europe.com/bv/computers/products/notebooks/tecra510cdt/product.shtm)

Young people like me wonder things like that existed !

---

### Post by Thewhistlingwind on 2011-05-08
CLI install is your best bet, or DOS. (Seriously, your specs appear to be THAT bad.)

---

