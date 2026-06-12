---
title: "Using Ubuntu to Defragment a Windows Computer?"
date: 2010-04-12
forum: General Help
---

### Post by GroogFish on 2010-04-12
I've got a laptop that runs on vista (terrible...) that has some 20GB of fragmented hard drive that is mostly system files. I don't know why I'm unable to defragment these files but I think it's probably because I'm using them. I'm wondering if I should try live-booting ubuntu and try defragmenting it from there. The problem I forsee is that it may somehow crash the windows system? If all the system files for the windows system changes under another OS without the knowledge of the windows system, won't that cause problems when I'm trying to boot vista again?

Anyone know?

---

### Post by howefield on 2010-04-12
How do you propose to defragment a Windows installation from an Ubuntu live CD ?

Last time I looked, I don't think this could be done ?

---

### Post by GroogFish on 2010-04-12
I don't know, got any other ideas? :D

---

### Post by Dayofswords on 2010-04-12
can you get a command prompt in vista?
if so just type 
```
defrag -f
```
this forces a defrag

---

### Post by Helkaluin on 2010-04-12
Do you mean a 20 GB partition that is fragmented or do you mean some 20GB of fragmented data that cannot be moved?

If you defrag from a fresh reboot there shouldn't be any major locked up files. If it's a fragmented swap and registry hives you're looking at then it's [this]("http://technet.microsoft.com/en-gb/sysinternals/bb897426.aspx") for you.

---

### Post by GroogFish on 2010-04-12
Here I've got a ss of it.

[IMG]http://img41.imageshack.us/img41/6803/vistasucks.jpg[/IMG]

I tried to defrag with the cmd but it still didn't work. What to do?

---

### Post by Helkaluin on 2010-04-13
Ahh, System Volume Information.

That's the system restore snapshot folder. It's a permissions problem. Apparently not even the administrator can write to that. Only the 'local system' account can.

One possible solution is to run the built-in Windows defrag GUI (not the command-line equiv). That will run the defrag process as a service under 'local system'.

Or, hey, change permissions. But then you risk much more on malicious software writing into your backup data.

<fanboi>Or just switch to the much superior ext4</fanboi>

Edit: Alternatively, if you want to use piriform, look into this: [http://technet.microsoft.com/en-gb/sysinternals/bb897553.aspx](http://technet.microsoft.com/en-gb/sysinternals/bb897553.aspx)
You can treat it like a sudo directed at the 'local system' user when you point it towards your own computer.

---

