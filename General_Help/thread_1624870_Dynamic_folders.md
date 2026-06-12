---
title: "Dynamic folders?"
date: 2010-11-18
forum: General Help
---

### Post by power78 on 2010-11-18
Is it possible to create a folder like the Smart Playlists of iTunes? For example, I could say that this folder should contain every files in directory X that has a modified date within the last two days. Then this folder would contain not copies, but links of the files that match in the same directory structure. 

I could create a "Recently Added" folder to contain my recently added music but don't have to remove them from their organized structure.

If this does not exist, I might consider writing it. What do you think?

---

### Post by nothingspecial on 2010-11-18
I don`t know of any app that does that, but if I go on a cd buying spree, I do something like this

eg, I know I ripped this album a week ago - Oh Calcutta ! - a week ago, but what have I ripped since?

```
~/Music$ find . -type d -newer mp3/The\ Lawrence\ Arms/Oh\!\ Calcutta\!/ 
.
./mp3
./mp3/NOFX
./mp3/NOFX/NOFX/Punk In Drublic
./mp3/NOFX/NOFX/White Thash Two Heebs And A Bean
./mp3/Strike Anywhere/Exit English
./mp3/Strike Anywhere/Change Is a Sound
./mp3/Strike Anywhere/Chorus Of One
./mp3/Strike Anywhere/Dead FM
./mp3/Strike Anywhere/To Live in Discontent
./mp3/The Lawrence Arms
./mp3/The Lawrence Arms/Cocktails & Dreams
./mp3/The Lawrence Arms/A Guided Tour Of Chicago
./mp3/The Lawrence Arms/Apathy And Exhaustion
./mp3/The Lawrence Arms/Ghost Stories
```

---

### Post by power78 on 2010-11-18
Now if we could make a Cron job out of that, and add mkdir and ln to it, we might be good! Any help?

> **nothingspecial said:**
> I don`t know of any app that does that, but if I go on a cd buying spree, I do something like this

eg, I know I ripped this album a week ago - Oh Calcutta ! - a week ago, but what have I ripped since?

```
~/Music$ find . -type d -newer mp3/The\ Lawrence\ Arms/Oh\!\ Calcutta\!/ 
.
./mp3
./mp3/NOFX
./mp3/NOFX/NOFX/Punk In Drublic
./mp3/NOFX/NOFX/White Thash Two Heebs And A Bean
./mp3/Strike Anywhere/Exit English
./mp3/Strike Anywhere/Change Is a Sound
./mp3/Strike Anywhere/Chorus Of One
./mp3/Strike Anywhere/Dead FM
./mp3/Strike Anywhere/To Live in Discontent
./mp3/The Lawrence Arms
./mp3/The Lawrence Arms/Cocktails & Dreams
./mp3/The Lawrence Arms/A Guided Tour Of Chicago
./mp3/The Lawrence Arms/Apathy And Exhaustion
./mp3/The Lawrence Arms/Ghost Stories
```

---

