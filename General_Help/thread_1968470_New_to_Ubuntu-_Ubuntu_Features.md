---
title: "New to Ubuntu- Ubuntu Features"
date: 2012-04-29
forum: General Help
---

### Post by jbonetwo on 2012-04-29
Hi,
I'm considering installing Ubuntu on one of my home PCs. There're a couple of features I'd like to ask about.

Firstly can I play my favourite games on Ubuntu that I played on windows? I'd like to mount my backup dvd games and install and play them. How would I go about doing this?

Secondly I use windows 7 homegroup called 'HOME' with homegroup password 'password' to share entire drives on my home networks. I'd like to copy, move and delete files on any pc in the network, from any pc in the network. My windows systems are configured for this but can Ubuntu be configured to work with windows 7 homegroup?

All input appreciated!

---

### Post by Hungry Man on 2012-04-29
> Firstly can I play my favourite games on Ubuntu that I played on windows? I'd like to mount my backup dvd games and install and play them. How would I go about doing this?
Any program designed for Windows can't run on Linux unless you use WINE. [http://www.winehq.org/](http://www.winehq.org/)

Results may vary in terms of performance and stability.

Not sure about homegroups. Someone else might now.

---

### Post by 3rdalbum on 2012-04-29
> **jbonetwo said:**
> Hi,
I'm considering installing Ubuntu on one of my home PCs. There're a couple of features I'd like to ask about.

Firstly can I play my favourite games on Ubuntu that I played on windows?

You might have limited success using Wine, but it might not be worth it as most games wouldn't run. Why not have Windows and Ubuntu installed simultaneously as a dual-boot?

> Secondly I use windows 7 homegroup called 'HOME' with homegroup password 'password' to share entire drives on my home networks. I'd like to copy, move and delete files on any pc in the network, from any pc in the network. My windows systems are configured for this but can Ubuntu be configured to work with windows 7 homegroup?

There seems to be no consensus on the internet. Some people say "it doesn't work", some say "It works exactly like a normal Windows share" - I suspect the latter people have missed the magic word "Homegroup".

But yeah, that's the problem with tying yourself to a file type or protocol that's only supported on one operating system. It limits what you can do.

Why not just turn it into a simple, straight sharing situation where each computer has its own network share? That way you can have Linux and Mac clients, and TV media boxes, and other kinds of devices that can access eachother.

---

### Post by blitzit on 2012-04-29
The games might not work that well on ubuntu. You could use VirtualBox and install Windows as a Virtual-Machine for your games.

For the networked storage, you could use Samba. It is a great protocol for shared storage on the network. I use it for a Windows based NAS Server and access it at all times through my Ubuntu workstation.

---

### Post by jbonetwo on 2012-04-29
> **3rdalbum said:**
> You might have limited success using Wine, but it might not be worth it as most games wouldn't run. Why not have Windows and Ubuntu installed simultaneously as a dual-boot?



There seems to be no consensus on the internet. Some people say "it doesn't work", some say "It works exactly like a normal Windows share" - I suspect the latter people have missed the magic word "Homegroup".

But yeah, that's the problem with tying yourself to a file type or protocol that's only supported on one operating system. It limits what you can do.

Why not just turn it into a simple, straight sharing situation where each computer has its own network share? That way you can have Linux and Mac clients, and TV media boxes, and other kinds of devices that can access eachother.

Thats a shame about the games being incompatible. I've tried using wine on ubuntu several years ago but it was beyond me and the reason i went back to windows.

Not sure what you mean by each computer having its own network share. How ive set up windows shares is each computer's c: and d: are shared so that there's unlimited access rights for any hard disk on the network no matter which pc im using. I'm just wondering if i can implement this same solution using ubuntu on one of the pcs.

Its disappointing as i really liked the look n feel of ubuntu. After my initial attempts with linux i swore id switch to it as soon as it improved in terms of compatibility. Guess i'll jus have to wait longer as wine as i remember it was just too complex for me.

Thanks for the help!

---

### Post by troysos on 2012-04-29
It seems like people go through a lot of headaches to get Windows games working on Ubuntu. If you think about it running games for a different OS doesn't make since. Xbox, Ps3, Wii, Windows, Mac, non of these are compatible.

---

### Post by Lindexter on 2012-04-29
> **jbonetwo said:**
> Hi,
Firstly can I play my favourite games on Ubuntu that I played on windows? I'd like to mount my backup dvd games and install and play them. How would I go about doing this?


PlayOnLinux and Wine. I still play all my games on Linux.

---

