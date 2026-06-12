---
title: "can gimp use  8 gb of ram?"
date: 2009-09-01
forum: General Help
---

### Post by llex_paul on 2009-09-01
i wope here is the right place to put this question....
i have a ubuntu 9.04 on x64 bt... 3 gb of ram for the moment and i want to get to 8 gb.  i have another 500 mb of dedicated ram on my nvidia graphic card and 750 mb shared. and i want to change my hard drive to a one with 7200 rpm, now i have 5200. I want to do this because i work on gimp with large images and brushes have a delay when i work on big filles. on gimp prefferces i see that is a ''swamp fille'' and there maximum is 4 gb of ram...now, if i do that changes it will gimp use my ram?

---

### Post by HiImTye on 2009-09-01
are you running 64 bit Ubuntu? if not you're at about the max ram you can use

---

### Post by jocko on 2009-09-01
> **llex_paul said:**
> i wope here is the right place to put this question....
i have a ubuntu 9.04 on x64 bt... 3 gb of ram for the moment and i want to get to 8 gb.  i have another 500 mb of dedicated ram on my nvidia graphic card and 750 mb shared. and i want to change my hard drive to a one with 7200 rpm, now i have 5200. I want to do this because i work on gimp with large images and brushes have a delay when i work on big filles. on gimp prefferces i see that is a ''swamp fille'' and there maximum is 4 gb of ram...now, if i do that changes it will gimp use my ram?
I can see nothing in gimp that limits the amount of ram it can use. I only have 2 Gb so I can't say for sure that it can really use more than 4, but it would be weird if there was such a limit for a 64 bit application.
The swap file option in gimp just lets you choose where in the filesystem it should store the things it *can't* fit into ram, so just set it to somewhere where you have free space (but the more ram you have, the less need for this option, I guess).

---

### Post by jocko on 2009-09-01
> **HiImTye said:**
> are you running 64 bit Ubuntu? if not you're at about the max ram you can useAs he said in the post, he's using 64 bit.

---

### Post by Lavaeagle on 2009-09-01
What do you need 8 gigs of RAM for? Blowing up a ship?

---

### Post by Bear Knuckle on 2009-09-01
Since x64 Linux supports address spaces up to 140,737,488,355,328 bytes - that's about 128TB - there should be no problem with Gimp using your huge RAM.

Anyway, from Gimp's point of view, if a computer program can even have one, it sees the whole virtual address space, not matter you have 1GB or 1EB of physical RAM. The question is not "can gimp use 8 gb of ram", it should rather be "can my os use 8 gb of ram", and with a 64Bit Ubuntu the answer clearly is: Yes, you can!

The OS controls the allocation of the physical RAM. The linux process - a running Gimp is nothing more - is always convinced to have the fully possible address space  for it's disposal. That's about 128TB IIRC. At least it's more than the regular linux user can afford to install in physical RAM.

@Lavaeagle: What's your comment good for?

---

### Post by anujpathania on 2009-09-01
There is no limitation of RAM a application can use. Its the limit of the operating system. And with 64 Bit OS, I don't see anything from stopping you using entire 8 GB Ram.

IMHO ... 8 GB is so cool. I can't consume half of my 2GB Ram most of the time though.

---

### Post by llex_paul on 2009-09-01
10x all! i use gimp for digital painting, and when i use a few layers, large canvas size (a2...or even bigger) and a custom high resolution brush it's need of more ram, believe me. now on a3 canvas i have problems and i hope that after my upgrade to have results. now...that file swap i was talking about it is there, it's called tile catch and maximum is 4 gb. and another thing...in photoshop it was an advanced option that lets you use graphic card (openGL enable...or something like that), is gimp using my graphic card?

---

### Post by sanderj on 2009-09-01
> **jocko said:**
> As he said in the post, he's using 64 bit.

Strictly spoken, he only says his CPU is 64-bit: "i have a ubuntu 9.04 on x64 bt." Nothing about the bit-ness of his OS. And as the OP has only 3GB, it could be a 32-bit OS ...

---

### Post by P4man on 2009-09-01
Find out how much ram gimp is using, just run gnome-system-monitor. If you see significant swapping there, then more ram will help, but Im guessing you'll see none, or very little. An A3 poster @300 DPI is still only ~130Mb. 

I dont know how gimp manages the tile cache, but it might "swap" there regardless how much ram you have.

As for gpu acceleration; I don't think gimp can do that at this point. (You can cheat a bit though, and use compiz for zooming. If you enable compiz you can use windows key + scroll wheel to zoom in on your desktop, and that is gpu accelerated. But it doesn't increase the pixel zoom, so its not as good as photoshop's). Its being worked on though..

---

### Post by llex_paul on 2009-09-01
yes i use ubuntu on 64 bit, sanderj.

p4man- so gpu acceleration is for PShop...but how do you explain the fact that if i use a high resolution brush my brush have a loop, a delay...? and that's on a3 canvas size and 300 dpi.

---

### Post by Bear Knuckle on 2009-09-01
> **anujpathania said:**
> There is no limitation of RAM a application can use.

Of course there is a limit an application can use. AFAIK linux processes can use 128TB of virtual RAM, which is an address space addressed by 47 Bit addresses.

Correct me, if I'm wrong.

---

### Post by P4man on 2009-09-01
Open system monitor and find out. It may just be that your cpu is too slow ?
Or perhaps you really do not have enough ram, but I doubt it.. just have a look in system monitor. Or maybe indeed you drive is too slow if gimp wants to write undo info to disk, its hard to say from here. You can try running iotop in a terminal and see if its reading or writing a lot to disk while its slowing.

---

### Post by anujpathania on 2009-09-01
> **Bear Knuckle said:**
> Of course there is a limit an application can use. AFAIK linux processes can use 128TB of virtual RAM, which is an address space addressed by 47 Bit addresses.

Correct me, if I'm wrong.

You are absolutely right. Also 128TB is huge isn't it?

What I meant was most application like GIMP doesn't put limit on ram they can use, OS and System Architecture does. More RAM they have more merrier they are :).

---

### Post by llex_paul on 2009-09-01
i installed iotop but i don't know when is used the hard drive too much. all this test must be done when i try to use big brushes and layers wright?

---

### Post by Bear Knuckle on 2009-09-01
> **anujpathania said:**
> You are absolutely right. Also 128TB is huge isn't it?

What I meant was most application like GIMP doesn't put limit on ram they can use, OS and System Architecture does. More RAM they have more merrier they are :).

That's correct. :-)

Sorry, got you wrong.

---

