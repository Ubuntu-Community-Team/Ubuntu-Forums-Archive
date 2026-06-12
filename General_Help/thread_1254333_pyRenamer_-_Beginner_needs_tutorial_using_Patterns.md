---
title: "pyRenamer - Beginner needs tutorial using Patterns"
date: 2009-08-31
forum: General Help
---

### Post by nomnex on 2009-08-31
pyRenamer>Patter>Original file name pattern (wich I do not understand).

Please explain with detail and in plain English.

If I take the example of an avi split in 10 parts:

Title: "Two English friends cruising on a party boat.www.sample.com.avi.001" (~avi.010)

What is the correct pattern to achieve the following name: "Friends.avi.001" (~avi.010)

I get the first part: English{X}, then I get lost. No matter what I try, I don't get the expected result.

Thanks for helping out.

---

### Post by nomnex on 2009-08-31
One more question:

For a files set: gra_hikari-k002.jpg (from 001 to 020)
what's the pattern to have hikari_001.jpg, hikari_002.jpg, etc.

I really would like to understand the {...} options and their correlation with the file name, so far the only step I succeeded was to remove the gra_ : _{C}. The preview returns "hikari_002.jpg" and I don't know how to remove the rest for all the photos from 001 to 020.

Thanks

---

### Post by nomnex on 2009-09-07
Bump

The questions has not been answer yet. Anyone to explain me the pyRenamer patterns. See my questions and examples in the posts above, many thanks.

---

### Post by nomnex on 2009-09-22
Thread view 60 times and anybody to help with patterns?!? Really?

---

### Post by Shujah on 2009-09-22
> For a files set: gra_hikari-k002.jpg (from 001 to 020)
what's the pattern to have hikari_001.jpg, hikari_002.jpg, etc.
Pyrenamer > Substitutions > Replace
we want to rename gra_hikari_k002.jpg  to hikari_002.jpg
so in first box: replace > gra_hikari-k 
in second box: with > hikari_
in preview you,ll see the replaced text which will be hikari_002.jpg, now click rename [under preview] to change the filename. You can select all 20 files and make the same changes as we are only changing the name before the number sequence starts so you can change all of 'em in one go.

---

### Post by nomnex on 2009-09-22
Finally, one answer :) Thank you Suja, but that's out of topic.

I put it in bold and large characters. With a bit of luck it will flash someone's eye?


*[SIZE=2]Topic: Tutorial or explanation in plain English (with examples) for a complete beginner willing to master the:[/SIZE]*

[CENTER]
[/CENTER]
 [CENTER][SIZE=5]**Rename files with patterns**[/SIZE]


[LEFT]I don't know if the pattern in pyrenamer are related to **Perl** language or simple **Regex** (or none of them)?

There is a video tutorial on pyrenamer web site, but it lacks basic explanations as "what does what" to help me clearly understand the patterns and reproduce them with different files names.

Thanks in advance.
[/LEFT]
[/CENTER]

---

### Post by Shujah on 2009-09-23
Since you are such a sweetheart about it here is a somewhat detailed response to your query.

As in the tutorial:
```
{X} = Numbers, letters **and** spaces. [Includes all the characters from the point onward (letters, numbers & spaces)]
{C} = Numbers, letters **not** spaces. [Includes all the characters except spaces from the point onward (letters & numbers)]
{L} = Letters **not** numbers or spaces
{#} = Numbers **not** letters, spaces or characters
{@} = Trash
```

Now the first example: 
> Title: "Two English friends cruising on a party boat.www.sample.com.avi.001" (~avi.010)

What is the correct pattern to achieve the following name: "Friends.avi.001" (~avi.010)

```
File Name > Two English friends cruising on a party boat.www.sample.com.avi.010]
Original  > {L} {L} {L} {L} {L} {L} {L} {L}.{L}.{L}.{L}.{L}.{#}
Renamed   > {3}.{12}.{13}
Result    > friends.avi.010
```

Example 2:
> For a files set: gra_hikari-k002.jpg (from 001 to 020)
what's the pattern to have hikari_001.jpg, hikari_002.jpg, etc.

```
File Name > gra_hikari-k001.jpg
Original  > {L}_{L}-k{#}.jpg 
Renamed   > {2} {3}.jpg
Result    > hikari 001.jpg

```
 If you want to add numbers in the beginning or the end of the name you can add [num] for 1,2,3.. [num2] for 01,02,03... [num3] for 001, 002 and so on. Plus you can use any number by using {num1+2} {num3+11} etc. In first example {13} was 010 you can change it to [001] by using:
```
Renamed > {3}.{12}.{num3+1}
Result  > friends.avi.001 

``` 
Changing cases [lower to upper or vice versa] is not supported in patterns so you'll have to use Replace function for that.

[Update: I'm sorry I thought [X} meant any charachetrs including spaces, letters or numbers, did not realize it meant **_all_** of them. I'll post in a while about rest of your queries and the diff b/w {X} & {C}]

---

### Post by nomnex on 2009-09-24
Shujah, you are of a tremendous help. I am not good at math/logic. You came down my level and I appreciate the effort.


**1. If I keep the example (probably the dumbest title ever...). I have worked on it a bit.**

Tow English friends cruising on a party boat.[www.sample.com.avi.010]("http://www.sample.com.avi.010")

```
{C} {C} friends{@}.{#} = {Two} {English} {friend cruising on a party boat.www.sample.com.avi} {010}.

If {1} {2}.{4} = Two English.010
```I could archive the result, but without understanding the 'friends{@}.' part.
A. - {@} stands for trash, but if I do {1} {2} {3}, then it will appear (i.e. my initial mistake)
B. - why do I need 'friend' in front of {@} and why {C} {C} {@}.{#} is not suitable?


**2. I still have difficulty to understand {X} vs {C} when a title has spaces in it**

Let's take a new example: Steve John Mike01 / {3} {2} {1}

```
if {C} {C} {C} = Mike01 John Steve
if {X} {X} {X} = Mike01 John Steve (same, why?), however
if {X}{X}{X} =  Steve John Mike01
```**NB:** {C} for me would be {Steve} and {X} would be {Steve+space} since 'X' = letters+space. With this reasoning {X}{X}{X} = {Steve+space}{John+space}{Mike01+space} i.e. Mike01 John Steve; so obviously there is something I do not understand.


**3. Misc questions**

I have seen on pyRenNamer that '/.folder' could create a folder? Someone's question was about changing mymusic/album-artist.jpg to mymusic/album/artist.jpg. That's interesting. There is all but little doc with pyRenamer and a web search for pyRenamer "pattern" tutorials did not return anything. How/where can I learn about these patterns through examples, knowing that my level is elementary.

---

### Post by Shujah on 2009-09-27
Here is the updated info after your friendly reminder :).

**1. Difference between {X} & {C}**
I assumed that {X} meant any character i.e. number, letter or space. But it means every character including number, letter & space. So when you use {X} it includes all the characters which exist beyond that point, unless you stop it by issuing a specific string or {@}.
{C} is same as {X} but it does not include spaces, so {C} stops whenever a space occurs beyond that point.
Example
```
Name     > Two English friends cruising on a party boat.www.sample.com.avi.010
Original > {X}
Rename   > {1}
Result   > Two English friends cruising on a party boat.www.sample.com.avi.010

```
{X} pasted the whole string because it catches all characters 

If we Use {C}
```
Original   > {C} 
Rename     > {1}
Result     > Two 
```   
{C} stopped once there was a space in string, if the name did not include any spaces e.g. Two_English_friends.. {C} would have pasted the whole string.
We can utilize {C} & {X} in many scenarios e.g.
```
Name     > Two English friends cruising on a party boat.www.sample.com.avi.010
Original > {C} {C} {C} {X}.avi{#}                    ***1** 
Rename   > {1} {2} {3}.avi.{5}
Result   > Two English friends.avi.010

Name     > jack & jill -s01-ep01- Went to the hill.avi
Original > {X} -s{C}-ep{C}- {X}                      ***2 **           
Rename   > {1} - {2}x{3} - {4}
Result   > jack & jill - 01x01 - Went to the hill.avi
```

***1 & *2** > *We used {X} when we need to copy many characters but stopped it with character strings, in the above mentioned examples by using s{C} & .avi{#} we made {X} pattern to stop before these characters. Also note that -s and -ep are removed by excluding them from the patterns*


**2. Using Trash {@}.**

Trash is used to remove character strings also to stop {Patterns} string. 
```
Name     > Two English friends cruising on a party boat.www.sample.com.avi.010
Original > {X} cruising{@}.www.{C}.avi.{#}
Rename   > {1} {3}.avi-{4}
Result   > Two English friends sample.com.avi-010

Name     > this is a file name used for example in Pyrenamer.rtf
Original > {X} used{@}.rtf
Rename   > this is a filename.rtf
```

{@} Trashes to the end of string unless stopped by issuing characters further on in the string like .avi.{#} stopped the {@} pattern (same as {X} in this regard}. Don't include the {@} number in rename. The charachter you want removed initiate before {@} like I wanted to remove the part of string starting from 'used' so 'used{@}'.

**3. Misc Questions.**

> I have seen on pyRenNamer that '/.folder' could create a folder? Someone's question was about changing mymusic/album-artist.jpg to mymusic/album/artist.jpg

Yes, thats possible but use '/folder' instead of '/.folder' unless you want a hidden folder. Lets say we want to change the name of a file which is at ~/Music/Smashing Pumpkins - Beginning of the End.mp3 

```
Name   > Smashing Pumpkins - Beginning of the End.mp3
Original > {L} {L} - {X}                        ***3**                 
Rename   > {1} {2}/{3}
Result   > Smashing Pumpkins/Beginning of the End.mp3
Or
Rename   > {1} {2}/{1} {2} - {X}                ***4**        
Result   > Smashing Pumpkins/ Smashing Pumpkins - Beginning of the End.mp3
Or 
Rename   > Albums/{1} {2}/Batman OSD/{X}        ***5**
Result   > Albums/Smashing Pumpkins/Batman OSD/Beginning of the End.mp3 

```

*** 3** > *I've used {X} when no further modifications are required in the filename from that point onward, in other words {X} simply copies the rest of characters including spaces.*
*** 4** > *Once the characters have been catched i.e. they have respective patterns like {C} or {L} they can be used any number of times like repeat of {1} & {2} in this example.*
*** 5** > *Adding some modifications to Path*

Since you want to master this application, keep in mind that once we catch characters in strings they can be manipulated in any way plus you can add any modifications in the 'Rename' part. {X} & {C} will be used most often but for more complex filenames you will have to use {#} & {L} e.g. when filenames are like 987wer34d6.jpg or character strings where numbers are not separated from letters. Another thing to remember is that you can stop the {X}, {C}, {#}, {L} or {@} patterns by giving a character which exists further on in the string (unless that character is used more then once and can be applied before your required location).


P.S. {@} still beats me I fail to see how can it come in handy when you can simply ignore characters in rename. Maybe it has some other additional functionality which I'm not familiar with.

---

