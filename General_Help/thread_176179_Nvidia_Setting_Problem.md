---
title: "Nvidia Setting Problem"
date: 2006-05-14
forum: General Help
---

### Post by muffinhead on 2006-05-14
Hello, I just installed the Nvidia Drivers for my Geforce FX car in Ubuntu, and Have Tried downloading the "Nvidia Settings" Program.

The problem is, when I downloaded the nvidia settings with wget, It shows up on the  Applications menu under system tools, but when I go to execute, or click on it, it says, "Cannot Launch Entry"

Details: Failed to execute the Child Process "nvidia-settings" (No Such File or Directory)

I also notice when getting updates via Synaptic, or Automatix, In the terminal, A Website url named: [http://koti.mb.net](http://koti.mb.net) , Fails to download some Updates, and Packages, Returning a 404 error, in the Terminal.

Any Help, or a solution is Greatly appreciated, as I am a Linux Newbie, and recently Just started using Linux. Thank You:)

---

### Post by muffinhead on 2006-05-14
[B]:Edit: Accidental Double Post:lol:
[/B]

---

### Post by Ramses de Norre on 2006-05-14
You download something with wget and it appears in your application menu? Did you install it with dpkg after downloading it? Why not use ```
sudo aptitude install nvidia-settings
```
I think it's in universe or multiverse.

---

### Post by muffinhead on 2006-05-14
I just tried that and it gave this following output, 

"0 packages upgraded, 1 newly installed, 0 to remove and 160 not upgraded.
Need to get 0B/504kB of archives. After unpacking 1020kB will be used.
Writing extended state information... Done
W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var /lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)"

As you can see the Package from: koti.mbnet.fi , returns an error that says either "No Such File or directory, or returns a 404 error in the terminal, because it can't find the specified Package/Website, or the Website may not be in service. Thus Resulting in the package not being fully downloaded, or Installed, making it useless

If anyone could let me know an alternative, besides it using koti.mbnet.fi , to download packages , because the koti.mbnet.fi , seems to be out of service, or does'nt have the needed pakages in it's database.

If you could help me and let me know, I'd appreciate it, Thank You:)

---

### Post by muffinhead on 2006-05-14
**:EDIT: Problem with the forum, accidentally made a double post.**

---

### Post by muffinhead on 2006-05-14
I'm bumping this Thread, so hopefully someone else can see it, It's already got bumped over to the third page, 

The Problem is when I try to download a package, Synaptic is trying to look for it on [http://koti.mbnet.fi](http://koti.mbnet.fi) , and Synaptic can't find it at that url, resulting in a : No Such file or directory, or a 404 error in the terminal.

Is there an alternative, besides Synaptic using koti.mbnet.fi , for certain Packages, Like an alternative url, that I can add, and remove koti.mbnet.fi , from the list since it does'nt work correctly?

Thank You if you could let me know:)

---

### Post by muffinhead on 2006-05-15
Sorry to bump this, yet once again, but this seems to be getting bumped over to the third and fourth pages really quick, without anyone seeing it. It seems Like this sub-forum, has quite alot of posters with alot of problem.

My problem is listed above about the koti.mbnet.fi Url for getting packages. 

Again sorry for any inconvieniences of me bumping this thread.;)

Btw, I downloaded GCC, G++, CPP, and the Libraries Via Synaptic, and they didn't install, How can I Install them? I don't think Synaptic Automatically Installs them for you. Thanks if you can help me:)

---

### Post by Ramses de Norre on 2006-05-15
Why don't you use the normal ubuntu repos?[U] [http://www.psychocats.net/linux/sources.php]("http://www.psychocats.net/linux/sources.php")

[/U]

---

### Post by muffinhead on 2006-05-15
Thanks for replying, I didn't realise there was other repositories, I was asking on this forum, to make sure if I deleted koti.mbnet.fi from the Synaptic repository list, if it would, or would not affect downloading/installing certain packages, or messing up already installed packages.

---

