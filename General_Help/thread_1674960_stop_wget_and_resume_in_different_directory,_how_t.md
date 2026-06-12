---
title: "stop wget and resume in different directory, how to?"
date: 2011-01-24
forum: General Help
---

### Post by LewRockwellFAN on 2011-01-24
I started wget in a folder in a partition that I didn't realize didn't have enough room. So can I copy the results to another directory on a partition with adequate room and resume with the -c switch or do I have to edit the logs or is it just impossible and I have to start over, wasting what I've already done?

In other words:
How does wget -c tell where it left off? Does it just look at what is in the download tree already or does it go by the logs or something else altogether? Is there any way to tell it to resume in another directory?

---

### Post by mobilediesel on 2011-01-24
> **LewRockwellFAN said:**
> I started wget in a folder in a partition that I didn't realize didn't have enough room. So can I copy the results to another directory on a partition with adequate room and resume with the -c switch or do I have to edit the logs or is it just impossible and I have to start over, wasting what I've already done?

In other words:
How does wget -c tell where it left off? Does it just look at what is in the download tree already or does it go by the logs or something else altogether? Is there any way to tell it to resume in another directory?

Wget tells where it left off just by the file size. Just stop wget, move the partial file to the new location, use wget -c in the new directory and it'll continue.

Edited to add: It still depends on the server being able to handle resuming downloads. Most can so it's not usually a problem.

---

### Post by LewRockwellFAN on 2011-01-25
Thank you, mobilediesel. How elegant! I hadn't even progressed to the point of thinking about the partial files. When I run it and watch the output I can see it checking the tree step by step and skipping files that are already there. Cool! I haven't had this much fun since I abandoned 4dos! :)

---

