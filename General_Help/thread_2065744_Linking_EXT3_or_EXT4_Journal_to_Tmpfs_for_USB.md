---
title: "Linking EXT3 or EXT4 Journal to Tmpfs for USB"
date: 2012-10-02
forum: General Help
---

### Post by thevillage88 on 2012-10-02
I think the title is pretty much self explanitory, but here goes...


Predicted question #1:  "Why on earth would you want to do this?"

I'm looking to create a series of pre-installed environments for USB/SD based on Ubuntu Mini(Who uses CDs nowadays anyway?) that can quickly be dd'd(lol) back to the USB in case I scew something up.  The problem that I'm having trouble deciding on a filesystem to use.

I know that ext2 is recomended to save the USB from constantly being written to, however, the risk of corruption is higher than I'm comfortable with since these, in my book, would be considered semi-production systems for development and demonstration.  What I would like to do is create a Tmpfs (64M, 128M, 256M?) on boot, touch a new journal file to it, and ultimately replace the original journal with a static(dynamic?) link.

Predicted question #2:  "Why don't you do XXXXXXX instead?"

while XXXXXXX may or may not be easier or more practical, I think this method will be easy and practical enough to be read and modified later if need be.

Predicted question #3:  "That's just not possible."

First of all, that's not a question.  Second, Bu115hit! :)
...
Anyway, I'm sorry if this question has already been discussed, but I couldn't figure out which search terms to use.

---

