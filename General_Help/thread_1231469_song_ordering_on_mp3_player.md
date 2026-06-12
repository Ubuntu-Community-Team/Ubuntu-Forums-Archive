---
title: "song ordering on mp3 player"
date: 2009-08-04
forum: General Help
---

### Post by gadabyte on 2009-08-04
i have an iriver t10 mp3 player that i'm having some trouble with.  when i copy an album folder, or a group of songs to the player, they end up out of order (and always in the same disorder).  however, when i copy them individually (1 then 2 then 3 ... ) they will be ordered properly.

i figured that this nuisance would be a good place to begin introducing myself to shell scripting, but in my research/experimentation, i believe i found a symptom that may be at the base of this problem.  the problem, however, is that i'm in territory that i'm utterly unfamiliar with, and thus at a loss for an explanation/solution.

comparing the results of ls and find, it seems that ls returns the contents in alphabetical order, whereas find returns the results in a jumble (i'd imagine it's in some sort of logical pattern, but i can't discern it).  most interestingly, the order of the list returned by find is the order that the songs are written to my mp3 player.

```
gadabyte@xubox:~/music/Zappa/(1991) Make a Jazz Noise Here$ ls *.mp3 -w 1
(01) Stinkfoot.mp3
(02) When Yuppies Go To Hell.mp3
(03) Fire And Chains.mp3
(04) Let's Make The Water Turn Black.mp3
(05) Harry, You're A Beast.mp3
(06) The Orange Country Lumber Truck.mp3
(07) Oh No.mp3
(08) Theme From Lumpy Gravy.mp3
(09) Eat That Question.mp3
(10) Black Napkins.mp3
(11) Big Swifty.mp3
(12) King Kong.mp3
(13) Star Wars Won't Work.mp3
```

```
gadabyte@xubox:~/music/Zappa/(1991) Make a Jazz Noise Here$ find -name '*.mp3'
./(01) Stinkfoot.mp3
./(12) King Kong.mp3
./(11) Big Swifty.mp3
./(09) Eat That Question.mp3
./(10) Black Napkins.mp3
./(13) Star Wars Won't Work.mp3
./(02) When Yuppies Go To Hell.mp3
./(06) The Orange Country Lumber Truck.mp3
./(07) Oh No.mp3
./(04) Let's Make The Water Turn Black.mp3
./(05) Harry, You're A Beast.mp3
./(08) Theme From Lumpy Gravy.mp3
./(03) Fire And Chains.mp3
```

if anyone could do any of the following for me, i'd be grateful:
[LIST]
[*]explain why find doesn't return results in alphabetical order, while ls does
[*]tell me a way to make find return alphabetized results
[*]offer any solutions for making files get written to my mp3 player in alphabetical order
[/LIST]

xubuntu 8.10, 64 bit
2.6.27-14-generic

---

### Post by martinbaselier on 2009-08-04
**find *** will sort output (alphabetically by filename) 
find * -name '*.mp3' will also do the trick.

**find * -exec cp {} DESTINATION \;**
will copy each file to a destination of your choice. You would of course need to replace DESTINATION with the proper destination. This will make sure the order is correct. I use the same trick on my mp3 player, which sorts files by the date they are put on the player.

---

### Post by gadabyte on 2009-08-04
excellent, thank you.

out of curiosity, do you know what the default sort for find results is?  browsed through the manpage and tried to find a pattern in my own files/results, but came up empty.

---

