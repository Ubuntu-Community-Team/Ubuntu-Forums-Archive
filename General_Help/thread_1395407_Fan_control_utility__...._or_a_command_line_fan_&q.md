---
title: "Fan control utility ? .... or a command line fan &quot;OFF&quot; setting  ?"
date: 2010-01-31
forum: General Help
---

### Post by jenaniston on 2010-01-31
I am running a laptop off a full install USB Ubuntu 9.04 pendrive to get at a rescue  of files off the hard drive -
the fan is constantly running -
the hardinfo utility also shows very good cpu benchmark clocking.
 
The hddtemp utility shows the temp at 28 C. when I *very **first ***boot up -
but yet this laptop fan *is already* running.
 
After sitting in sleep mode the fan is still running . . . 
 ***it ***is probably generating all the heat - now up to 34 C. 
 
This fan is on from the start and is constant for this "sick" Sharp AL27 laptop -
and as I am in a campus library - among the nuisance is the constant noise of it whirling - it's pretty loud.
 
While I may be glad the fan works well . . .
Is there any higher level kernel/ architecture command for such an important - but here a nuisance - function ?
 
Or are there any fan utility available to experiment with ?
 
Any suggestions appreciated . . .  Thank you very much.

---

### Post by t4thfavor on 2010-01-31
There is probably a smartfan option of sorts in the bios. As for the fan running all the time, it probably has something to do with missing drivers for some part of the board. There are tons of other threads about similar rogue fans, I have no idea if they fixed anything or not.

---

### Post by jenaniston on 2010-02-01
> **t4thfavor said:**
>  . . . probably a smartfan option of sorts in the bios. 

Uhh . . . well . . . a nice thought . . . 

But this is the lamest bios set-up I have ever seen - by Insyde Software (and on a very decent machine).
 
But I will now never buy another laptop without first going to a store to check the BIOS set-up screen.
I already had to really figure out on my own just how to exactly LAN boot at all -
***without*** any ***LAN boot*** in the bios boot sequence . . .a real chore -  ugh.
Insyde Software "support" was non-existent.

So I would have noticed a fan option on the laptop bios -
(but I'll look on the bios of some of our campus Dells to see what they do in bios).

You are right though in that it should be a pretty high level kernel architecture command or setting - 
that is how far up in the kernel something like this would be I think.

> **t4thfavor said:**
>  . . . it probably has something to do with missing drivers for some part of the board. 
There are tons of other threads about similar rogue fans, I have no idea if they fixed anything or not.

yes, missing drivers . . . or more probably "corrupted" drivers . . . yes that is at some level very likely.

Threads I have seen on other forums have also been kinda inconclusive . . . 
it is hard to say what works.

Thanks for the reply.

---

