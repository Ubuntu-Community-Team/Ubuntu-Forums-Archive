---
title: "New kernel = wireless adapter gone?"
date: 2006-02-17
forum: General Help
---

### Post by Robor on 2006-02-17
I upgraded my kernel through apt-get update/upgrade yesterday and when I rebooted my wireless adapter was not available.  Before that sometimes I'd boot up and it will not pull an IP but just doing a deactivate/activate fixes that problem so no biggie.  But with the new kernel if I went to 'System | Administration | Networking' the adapter (eth1) wasn't even listed.  I rebooted and used the previous kernel in the Grub menu and it worked fine.  

My adapter is an Intel Pro 2200BG and was supported 'out of the box' when I installed Ubuntu.  Anyone else have the kernel upgrade break their 2200BG adapter?  Thanks for any suggestions/help!  :)

---

### Post by Ginger The Cat on 2006-02-17
Yes it's annoying isn't it!

Last time I updated my kernel the same happened to me. You need to recompile ipw2200.

There is a [very long thread about it]("ubuntuforums.org/showthread.php?t=26623")

I can tell you what I did if you can't work your way through the above.

Of course it might not be the same problem.

Mike

---

### Post by Robor on 2006-02-17
I see that thread but it deals with WPA encryption and I'm using simple WEP encryption on my Linksys router.

---

### Post by Strife on 2006-02-17
I've had a similar problem. What I find very strange, though, is that I actually have to (for now) manually unload ieee80211 and ieee80211_crypt, then reload ieee80211 before I can finally use modprobe to load ipw2200.

Of course this is (mostly) solved in that I have suspend2 working on my laptop, so I only have to actually do this in the event that suspend2 crashes while trying to go into hibernate (which happens occassionally, though not so often that I need to worry about it so much).

Still, it would be nice to get the modue loading automatically... Unfortunately I have no idea where ieee80211 is loaded, or else I'd be able to figure something out.

---

### Post by Robor on 2006-02-17
I guess it's time to do some reading and hope someone's got a similar issue with the ipw2200 and the new kernel patch.

That said - and please remember that I'm an Ubuntu/Linux fan when I say this - can you imagine how much flack Windows would take if a simple 'Windows Update' broke wireless drivers like this kernel patch just did?  I had the same thing happen to my Fedora Core 4 'server' with a Promise IDE RAID controller in it.

As a tech/tweaker I don't mind a little bit of troubleshooting as it helps me learn more about the OS and how it works.  Regular users don't care about that though.  They just want their computers to work.  Unfortunately, it's things like this that hold Linux back in the desktop arena.

---

