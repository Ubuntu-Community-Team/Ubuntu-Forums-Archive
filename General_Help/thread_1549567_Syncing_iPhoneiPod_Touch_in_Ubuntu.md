---
title: "Syncing iPhone/iPod Touch in Ubuntu"
date: 2010-08-09
forum: General Help
---

### Post by lalilulelo on 2010-08-09
So this seems like such a dumb question that a million answers should come up when I google it - but surprisingly not. My question is how do I sync my iPod Touch on Ubuntu? I know that Ubuntu 10.04 natively supports the device and that you can manually copy music to and from an iPod Touch in Rhythmbox, but how do I *sync* it? By sync I mean automatically copy all music from your music library, ignoring songs already stored on the iPod (and also deleting any files you have removed from the library). I have tried several different music organization programs, and the only one that even recognizes my iPod Touch is Rhythmbox - and it won't sync the device. Why would they go to all the trouble to get iPhones/iPod Touches working in Ubuntu when there is not a single program (to my knowledge) that will actually *sync* the damn thing? It seems like such a simple feature to have. Am I missing something here?

---

### Post by lalilulelo on 2010-08-12
Anyone?

---

### Post by earthpigg on 2010-08-12
> **lalilulelo said:**
>  Why would they go to all the trouble to get iPhones/iPod Touches working in Ubuntu when there is not a single program (to my knowledge) that will actually *sync* the damn thing?

Because one of the core tenets of Linux is "*Release early, Release often*."

I have an alternative question for you:

Who would write software to sync an iPod, when there is no demonstrated iPod connectivity at all?

If Ubuntu machines could not even communicate with iPods until very recently, how where Ubuntu & Rhythmbox coders supposed to write software to *sync* them? That would be like trying to translate a book into a different language *without being able to read the book*.

Now that 10.04 demonstrates that we can at least *talk* to it, someone hopefully has motive (& ability) to write software to *sync* it.

Does that make sense?

edit: i found [this]("http://blog.robbychen.com/2010/06/06/use-rhythmbox-to-sync-with-ipod-touch/"). i (naturally) shun Apple products, so i cannot verify it works. i found it by google-searching "rhythmox ipod sync 2010".

---

### Post by lukeiamyourfather on 2010-08-12
As far as I know Apple doesn't make any documentation available about how to interact with those devices. Its all reverse engineered by end users and developers. My guess is nobody cares enough to invest the time. Maybe use a virtual machine in VirtualBox or similar and install Windows and iTunes.

---

### Post by earthpigg on 2010-08-12
> **lukeiamyourfather said:**
> nobody cares enough to invest the time.

well, lots of people do. they just aren't devoted open source volunteer coders.

how many of those types do we think even *own* a single apple product?

you need someone that...

1) knows how to program
2) knows how to reverse engineer this stuff, and is either not American or is American and willing to potentially violate the our fascist [DMCA]("http://en.wikipedia.org/wiki/Dmca") laws.
3) cares about open source software and is a volunteer developer (or a Canonical employee)
4) is willing to purchase from apple


The list of people that are the first 3 **and** #4 is not exactly the largest list of people on the planet. Apple isn't exactly loved by Open Source coders, as I understand it. It may take money to accomplish this. 

Canonical's money, perhaps.

But Canonical doesn't make money off of individual iPod owning consumers. They make their money in corporate environments.

---

### Post by bapoumba on 2010-08-12
[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)
[http://www.libimobiledevice.org/](http://www.libimobiledevice.org/)

I use google to sync calendar, contacts and other things. Hmm, do I love big corporations :/
I use iPods because they are the only ones I've owned or tried that suit my ears..

---

### Post by lukeiamyourfather on 2010-08-13
> **earthpigg said:**
> well, lots of people do. they just aren't devoted open source volunteer coders.

how many of those types do we think even *own* a single apple product?

you need someone that...

1) knows how to program
2) knows how to reverse engineer this stuff, and is either not American or is American and willing to potentially violate the our fascist [DMCA]("http://en.wikipedia.org/wiki/Dmca") laws.
3) cares about open source software and is a volunteer developer (or a Canonical employee)
4) is willing to purchase from apple


The list of people that are the first 3 **and** #4 is not exactly the largest list of people on the planet. Apple isn't exactly loved by Open Source coders, as I understand it. It may take money to accomplish this. 

Canonical's money, perhaps.

But Canonical doesn't make money off of individual iPod owning consumers. They make their money in corporate environments.

That's pretty much what I meant to say. ;)

---

### Post by lalilulelo on 2010-08-28
Hm... well it's things like this that make me think maybe I shouldn't even bother with Ubuntu. I was under the impression that Ubuntu was supposed to be the "linux that anyone can use," but the more I tinker with it the less that seems true. If there's no way to sync an iPod or iPhone - devices that a huge portion of the population uses on a regular basis - then I don't see how Ubuntu can claim to be an OS for the common user. Maybe I misunderstood the purpose of this OS.

---

### Post by d3v1150m471c on 2010-08-28
gtkpod. i think it's in the repositories and i use and recommend it.

---

### Post by lalilulelo on 2010-08-28
I tried gtkpod and it didn't recognize my iPod Touch.

---

### Post by Mark Phelps on 2010-08-29
> **lalilulelo said:**
> Hm... well it's things like this that make me think maybe I shouldn't even bother with Ubuntu. I was under the impression that Ubuntu was supposed to be the "linux that anyone can use," but the more I tinker with it the less that seems true. If there's no way to sync an iPod or iPhone - devices that a huge portion of the population uses on a regular basis - then I don't see how Ubuntu can claim to be an OS for the common user. Maybe I misunderstood the purpose of this OS.

Obviously, if you think the purpose of this OS is to provide compatibility with the most closed-source computer company on the planet (Apple), they you DO misunderstand the purpose of this OS.

You gave hundreds of dollars of your money to Apple -- go complain to Steve Jobs about his folks NOT writing open source applications for Linux distros to synch Apple devices.

---

### Post by ccleanerfan on 2010-09-01
iPod touch apps that require jailbreak such as mewseek and pwntunes have two separate methods that could sync. Closed source and they're paid apps though. =/ They allow syncing within the iPod, no computer required.

---

