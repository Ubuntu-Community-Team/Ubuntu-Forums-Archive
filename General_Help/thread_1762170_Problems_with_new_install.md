---
title: "Problems with new install"
date: 2011-05-18
forum: General Help
---

### Post by Ghosthaven on 2011-05-18
I just recently put together a box to use as a home server,
but I'm having problem after problem and I can't seem to track
them down.

First, how I set everything up:
All hardware is new and seems to work fine.
I installed Ubuntu Server 10.10
I then updated everything (sudo apt-get update, sudo apt-get upgrade)
Then I installed the GUI (sudo apt-get install ubuntu-desktop)
Then I updated everything again, including upgrading to 11.4.
Now I'm having a couple problems.

I want to run a full SMART test on this drive since its new. I'm
using the standard Disk Utility that comes with Ubuntu. When I
run the brief tests, it all works fine... drive reports good.
But when I attempt an Extended test, it starts the test then just
sits there at 0% forever. I let it sit 3 hours thinking that it
was just taking extra time due to the fact its a 2TB hard drive,
but no go.

Next, I have a problem with Virtualbox. I want to run a windows
VM but whenever I attempt to create a new virtual drive, it,
again, sits there at 0% forever.

Does Ubuntu have some kind of problem with 2TB drives? Or is
there a problem with 11.4? Or is my 2TB drive just messed up
somehow even though basic SMART tests say its good?

These are my major problems, if I can get these worked out I'll
bug you guys for the others in other threads.

Thank you in advance.

---

### Post by wildmanne39 on 2011-05-18
> **Ghosthaven said:**
> I just recently put together a box to use as a home server,
but I'm having problem after problem and I can't seem to track
them down.

First, how I set everything up:
All hardware is new and seems to work fine.
I installed Ubuntu Server 10.10
I then updated everything (sudo apt-get update, sudo apt-get upgrade)
Then I installed the GUI (sudo apt-get install ubuntu-desktop)
Then I updated everything again, including upgrading to 11.4.
Now I'm having a couple problems.

I want to run a full SMART test on this drive since its new. I'm
using the standard Disk Utility that comes with Ubuntu. When I
run the brief tests, it all works fine... drive reports good.
But when I attempt an Extended test, it starts the test then just
sits there at 0% forever. I let it sit 3 hours thinking that it
was just taking extra time due to the fact its a 2TB hard drive,
but no go.

Next, I have a problem with Virtualbox. I want to run a windows
VM but whenever I attempt to create a new virtual drive, it,
again, sits there at 0% forever.

Does Ubuntu have some kind of problem with 2TB drives? Or is
there a problem with 11.4? Or is my 2TB drive just messed up
somehow even though basic SMART tests say its good?

These are my major problems, if I can get these worked out I'll
bug you guys for the others in other threads.

Thank you in advance.
Hi, I am not an expert, so I will just talk about virtualbox, that I have used for several years. First it it best to use virtualbox from virtualbox.org and you need to read there manual it tells you everything you need to know from start to finish for basic install. I have not installed server in a vm, I have used minimal installs and the livecd. This link should help. [https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=004599128559784038176%3Avj_p0xo-nng&ie=UTF-8&q=server+install&sa=Search](https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=004599128559784038176%3Avj_p0xo-nng&ie=UTF-8&q=server+install&sa=Search)

---

### Post by Ghosthaven on 2011-05-19
Thank you for your advice but I've used virtualbox for about 2
and 1/2 years now, on both linux and windows.

I think that my problem may be in some way related to the hard
drive, but I can't see anything wrong with it... that's why
I'm wondering if Ubuntu has problems with drives over 2TB.

I see several posts on the 'net about people having problems
with the 2TB limit, but they are almost all quite old, I don't
know if that means there are still problems or not.

---

