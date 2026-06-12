---
title: "I just installed Ubuntu for the first time..."
date: 2009-12-22
forum: General Help
---

### Post by jimbojones666 on 2009-12-22
I made it with 4 partitions (all primary): First, windows; Second, Free Space (Fat32?); Third, Ubuntu; And Fourth, Swap (4 gigs, 2 gigs of ram)

I'm on windows xp now, but I've also been on Ubuntu, and I can't see the free space. What's going on? Why can't I see the free space?:(

---

### Post by manco on 2009-12-22
> **jimbojones666 said:**
> I made it with 4 partitions (all primary): First, windows; Second, Free Space (Fat32?); Third, Ubuntu; And Fourth, Swap (4 gigs, 2 gigs of ram)

I'm on windows xp now, but I've also been on Ubuntu, and I can't see the free space. What's going on? Why can't I see the free space?:(
I don't think Windows can see your Ubuntu partitions. (Not 100% sure)

Can you see all the partitions in Ubuntu?

---

### Post by synapsys on 2009-12-22
What do you mean you can't 'see' the free space, where are you looking? disk management?

Use **gparted **in Ubuntu. If you don't have it installed, then open up a terminal 

Applications >> Accessories >> Terminal

and type 

```
sudo apt-get install gparted
```

---

### Post by jimbojones666 on 2009-12-22
> **yellowsnow4free said:**
> I don't think Windows can see your Ubuntu partitions. (Not 100% sure)

Can you see all the partitions in Ubuntu?I can't see Ubuntu, I know - Windows can't read that file type, or whatever. But I'm on XP - I was on Ubuntu and I got the same response - and I can see the HDD that's supposed to be used by both OS', but there's nothing there. It's just empty.

---

### Post by jimbojones666 on 2009-12-22
> **synapsys said:**
> What do you mean you can't 'see' the free space, where are you looking? disk management?

Use **gparted **in Ubuntu. If you don't have it installed, then open up a terminal 

Applications >> Accessories >> Terminal

and type 

```
sudo apt-get install gparted
```Ah, ic. I just went into Windows Management and it is there. Am I supposed to format it? Mark Petition as active? These are things I can do when I 'right click' it.

---

### Post by synapsys on 2009-12-22
If you format it as ntfs, you will be able to use with both ubuntu and windows.

---

### Post by jimbojones666 on 2009-12-22
> **synapsys said:**
> If you format it as ntfs, you will be able to use with both ubuntu and windows.Excellent. Aye, thanks for the quick help - from Western Canada.

---

### Post by synapsys on 2009-12-22
> **jimbojones666 said:**
> Excellent. Aye, thanks for the quick help - from Western Canada.

No problem, that's why we're here.

Welcome to Ubuntu.

---

