---
title: "mini project, help me get started"
date: 2009-11-11
forum: General Help
---

### Post by Absolute Noob on 2009-11-11
I hope i'm typing this in the proper area, as the name states I'm an absolute noob when it comes to ubuntu, i've been reading about it over the years, tested it once a few years back but never really had to live with it.

recently my home PC gave up on me, rather 1/2 of the ram is no longer being read (which of the 2 module, i still have to figure out lol)

what i'll end up with though is an old motherboard, 512mb ram, amd 3000+(i think it's 64 bit), geforce 7600 (agp), 500watt power supply, i used to run vista if that's any help...

my question is, **if i want to make a home server/sort of a NAS which version of ubuntu do i download/install?**

as i do not know anything about ubuntu i felt i needed to ask first, i'm in no rush as this is a mini project of mine, over the holidays i'm targeting about 2-3 1TB drives initially, hopefully by Q2 of next year I should get that number up to about 5-7.  I want to be able to run it 24/7 but not necessarily have it on the whole time.  right now I already have a popcorn hour downloading all my torrents but the internal drive for that will get full soon, so I was hoping to get it to store the files in a separate storage system.

I also plan on ripping my entire DVD/Music Collection into the server so that I can have it centralized.

I think I follow instructions pretty well so if anyone can point me to a resource that'd help too :)

*I also read about NAS specific software, but I kinda like the GUI of ubuntu, and want to learn a little bit more about it as I set up my machine.

TIA

---

### Post by MichealH on 2009-11-11
Try and get the Sever version and if you can 9.04 as 9.10 is **very unstabl**e and because it is unstable you cant really use it as a server as long as you install 9.10 right give 9.10 a try

---

### Post by 3rdalbum on 2009-11-11
> **Absolute Noob said:**
> my question is, **if i want to make a home server/sort of a NAS which version of ubuntu do i download/install?**

My home server runs regular Ubuntu. I'd recommend setting up Samba with the "system-config-samba" program from the repositories (it's easier than manually editing smb.conf). Also, install "ssh" for remote administration, and maybe turn on Gnome's Remote Desktop feature as well.

---

### Post by 3rdalbum on 2009-11-11
> **MichealH said:**
> Try and get the Sever version and if you can 9.04 as 9.10 is **very unstabl**e and because it is unstable you cant really use it as a server as long as you install 9.10 right give 9.10 a try

That's not exactly a clear, unambiguous statement. Besides, my server runs 9.10 and its core functionality is fine.

I would advise you to run 9.04 on your home server, because its DNLA and DAAP servers actually work (unlike 9.10's...) and you can use the Ksplice service to apply kernel updates without having to reboot.

---

