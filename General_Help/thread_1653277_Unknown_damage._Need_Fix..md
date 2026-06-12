---
title: "Unknown damage. Need Fix."
date: 2010-12-26
forum: General Help
---

### Post by CowboyIrving on 2010-12-26
Well about a month or so ago I decided to go into Package Manager and delete the files that I don`t use. I thought I was only deleting the unimportant ones that I had downloaded before hand for gameséprograms that I didn`t really need.
 
Now it doesn`t even really log in. It doesn`t go into the Ubuntu purple screen of loading all the time. If it does though it just sits there and doesn`t get past it. The times it doesn`t go there it will load directly to(What I assume is) the command prompt. The whole window goes black and it`s like I have one of those terminals open, but the whole screen is it. 
 
I went through and checked some random files using cd -whatever- then `l` and it looked like I still have all of my files that I need and the like. But I assume I have a major file missing.
 
Any help would be greatly helpful! I don`t have the original OS CD for Ubuntu so I can`t really reload it. I do how ever have a Windos XP OS that I tried to load up from a CD. But for some reason my comp isn`t even comprehending that it is within the CD-ROM.
 
Basically it won`t try to load the OS so that I can get XP loaded up. Once again, any help would be greatly appreciated.

---

### Post by oldos2er on 2010-12-26
Kind of difficult to offer help without knowing what packages you removed. If you can boot into recovery mode, try running ```
apt-get update && apt-get install ubuntu-desktop gdm
```

---

### Post by CowboyIrving on 2010-12-27
I tried to do that and it came back saying some random things. But what I noticed the most is that `plymouth`wasn`t installed(I looked through the various lines which make next to no sense to me and saw it has something to do with text and visuals or the like.)
 
When I went and did sudo apt-get install plymouth. It came back saying more lines and then. `Could not resolve ùs.archive.ubuntu.com`So I`m thinking I have something major missing that won`t allow me to actually get new updates or the like.

---

### Post by CowboyIrving on 2010-12-27
I went through and tried to find the source.list in etc/apt/source.list but it apparently isn't there.
 
I can us cd etc/apt and then use 'l' and see that it is infact in the list. But it is gray and it doesn't have an / at the end like the other ones in the list.

---

### Post by 3rdalbum on 2010-12-27
You need an internet connection. Plug your computer into an Ethernet port on your router and type:

```
sudo dhclient
```

---

### Post by CowboyIrving on 2010-12-27
Tried that twice now. Each time it went through the cycle of checking the ports or what ever but came back with 'No DHCPOFFERS received' and 'No working leases in persistent database - sleeping'

---

