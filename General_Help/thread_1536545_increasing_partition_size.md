---
title: "increasing partition size"
date: 2010-07-22
forum: General Help
---

### Post by wcutrombonekid on 2010-07-22
so, i started with only like 25 GB in my partition with ubuntu in it.  I just wanted to test it out and see how i like it, now I have outgrown this and want to increase the size of my partition.

I have a live cd and have already created about 100 more GB of space that i would like to allocate to ubuntu.  Problem is, that when i go to unmount the linux partitions, it wont let me.  The keys symbol appears on gparted, but when i go to unmount it, the option is not available.  What is happening?  Am I missing  a step?

ps.
I am running 9.10 
I am using a live cd to try and make these adjustments

thanks
chris

---

### Post by mikewhatever on 2010-07-22
This is odd. Partitions aren't mounted by default when running from cd. Have you mounted the Ubuntu partition manually?

---

### Post by wcutrombonekid on 2010-07-22
> **mikewhatever said:**
> This is odd. Partitions aren't mounted by default when running from cd. Have you mounted the Ubuntu partition manually?
I don't know, its been a while since i've messed with this and i don't remember what i did

---

### Post by bumanie on 2010-07-22
Suggest you go to the [gparted site]("http://gparted.sourceforge.net/livecd.php") and download the live gparted cd and read the documentation from [here]("http://gparted.sourceforge.net/documentation.php"). Post back if things still aren't working after that.

---

### Post by mikewhatever on 2010-07-22
> **wcutrombonekid said:**
> I don't know, its been a while since i've messed with this and i don't remember what i did

So, you are not trying to increase the partition size at present?

---

### Post by wcutrombonekid on 2010-07-22
> **mikewhatever said:**
> So, you are not trying to increase the partition size at present?

no, i am, i was then too, but just didn't really have the time and didn't have the knowledge, so i don't know what i did then, but i never actually got it enlarged, and now i have to because i'm out of space.

there are a few glitch-ish things that its been doing for a while anyway, i'd like to upgrade to 64 bit, and i'd like to upgrade to 10.04, so i'm contemplating just taking all my personal files off and starting from scratch, does that seem like the best option?

---

### Post by mikewhatever on 2010-07-22
> **wcutrombonekid said:**
> no, i am, i was then too, but just didn't really have the time and didn't have the knowledge, so i don't know what i did then, but i never actually got it enlarged, and now i have to because i'm out of space.

there are a few glitch-ish things that its been doing for a while anyway, i'd like to upgrade to 64 bit, and i'd like to upgrade to 10.04, so i'm contemplating just taking all my personal files off and starting from scratch, does that seem like the best option?

Well, how is it all relevant to editing partitions now? Why don't you boot from a live cd and see what happens, and I don't mean a while ago.

---

### Post by egalvan on 2010-07-22
> **wcutrombonekid said:**
> 

I have a live cd and have already created about 100 more GB of space that i would like to allocate to ubuntu...
 when i go to unmount the linux partitions, it wont let me.
  The keys symbol appears on gparted, but when i go to unmount it, the option is not available.
  What is happening?  Am I missing  a step?

Highly likely that the liveCD is finding a Linux swap partition.
post a screenshot of the liveCD gparted that is giving you the problems.


> I am running 9.10 


Any *specific* reasons to use an older release?

reasons such as these:

You like it better
it has specific hardware support
I have the CD already
etc


Mind you, there is nothing wrong with 9.10, 
if it works for you, that's great...
CHOICE is King here in Linux-Land :p

I'm just curious as to *why*

---

### Post by wcutrombonekid on 2010-07-23
> **egalvan said:**
> Highly likely that the liveCD is finding a Linux swap partition.
post a screenshot of the liveCD gparted that is giving you the problems.




Any *specific* reasons to use an older release?

reasons such as these:

You like it better
it has specific hardware support
I have the CD already
etc


Mind you, there is nothing wrong with 9.10, 
if it works for you, that's great...
CHOICE is King here in Linux-Land :p

I'm just curious as to *why*

laziness mostly, when 10.04 came out exams were in full swing and i simply didn't have time.  so i've been putting off messing with it until now, i'd like to try the new version anyway, so i think i'll just upgrade and pull all my important stuff off, theres not much of it

---

### Post by wcutrombonekid on 2010-07-23
> **mikewhatever said:**
> Well, how is it all relevant to editing partitions now? Why don't you boot from a live cd and see what happens, and I don't mean a while ago.

its not really, i'm just thinking aloud.  It is related in that i would like to upgrade and need the space to really continue using it, since its being difficult and i'm going to have to do a fresh install anyway if i want to upgrade to 64 bit (i recently added more ram) why not just reformat the whole thing and make it larger then instead of screwing with it.

---

