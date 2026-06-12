---
title: "How to find out what's using SWAP?"
date: 2009-10-06
forum: General Help
---

### Post by solitaire on 2009-10-06
How do i find out what is using my swap?

Recently my swap is hitting +25% and my ram is around +50% (i've 1Gb of ram and 1Gb swap partition). This is only happened in the past week or so, usually my swap is only 5% max! Now my system start to get VERY slow (I have to drop the swap partition and remount it for things to speed up again), I need to find out what's using the swap partition so i can remove  the program or see if there's a fix.

---

### Post by c0mput3r_n3rD on 2009-10-06
learn assembly

---

### Post by Meow27 on 2009-10-27
> **c0mput3r_n3rD said:**
> learn assembly

at least tell us why..... -_-

---

### Post by akakingess on 2009-10-27
Yeah, at least try to help a little rather than just throw some single or double word answer out there. Personally, I would look at Top or HTop first and see if it tells you in there what is taking up all of your resources. It (HTop anyway) will show you what services are running and how much RAM/CPU they are using, like right now one of my CPUs is at 100% because of beagle indexing.

---

### Post by solitaire on 2009-11-21
Hi thanks for the reply [akakingess]("http://ubuntuforums.org/member.php?u=814426") 

I think it's TweetDeck (might be Adobe Air programs in general) but i can't be 100% sure.

I've installed htop but can't get it to show what is using the swap rather than memory...

i've got top set up in conky to show me the top 6 programs using memory but does not tell me if that's ram or swap! at the moment i've only got: conky, Firefox & Thunderbird running and my memory and swap are as follows:
Ram: 582MiB out of 992Mib (58% in use)
Swap: 258Mib out of 1.00Gib (25% in use)

every so often i need to turn swap off and start it again (usually if the machines been on for longer that 2 days without a reboot) 

Anyone got any other idea? (except for you [c0mput3r_n3rD]("http://ubuntuforums.org/member.php?u=865844") i'll be diplomatic and ask you NOT to reply unless you have HELPFUL information)

---

