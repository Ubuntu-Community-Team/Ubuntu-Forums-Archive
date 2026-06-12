---
title: "Windows Programs in ZIPS with Wine..."
date: 2010-03-02
forum: General Help
---

### Post by x0xl33ah on 2010-03-02
Hey guys!

So I'm new to ubuntu. I've got WineHQ installed, and have seen that the windows programs I had installed on a seperate HD work just fine without anything more needing to be done. However, I am a web dseigner and did not have my Adobe programs on that seperate HD, they were on the HD that I erased to put Ubuntu on. So, I've got the zip file with all my adobe programs, but whenever I extract them, at the end it tells me that the file is corrupt. 

Anyway, when I had installed something previously right after installing wine, I had googled how to do it and the instructions I found said something along the lines of not trying to actually open the zip and extract them because it wouldn't work, but actually going into terminal and telling terminal to extract the files!? Is this just program specific (I can't remember what program it was that did that) and what could possibly be the issue, or is this how I need to unzip my Windows Programs?!

& I'm assuming if I unzip them I probably need to make the destination the little WineHQ program area, correct?

Thanks in advance for your help! :P

---

### Post by Ghost|BTFH on 2010-03-02
You should test them to make sure they're not corrupted or perhaps not a true zip file.

Use:

unzip -tq \*.zip

In the same directory as the files.

Cheers,
Ghost|BTFH

---

