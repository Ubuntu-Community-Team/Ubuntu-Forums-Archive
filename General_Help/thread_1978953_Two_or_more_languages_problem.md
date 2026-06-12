---
title: "Two or more languages problem"
date: 2012-05-12
forum: General Help
---

### Post by Costas100 on 2012-05-12
I am a long time Ubuntu user and proud of reaching this point at my age (74+). 
Most of the times I am using two languages, US English and Greek (modern). So upon starting a new installation, I am adding Greek as a second language and add also the Greek Keyboard. Most of the times this worked with no problems at all. Only lately (in the last couple of years) I had a problem that the second language, took over the system and all or most menus became Greek. This is not a problem for me, since I am fluent in both English and Greek, but at times it is getting confusing.
In my searches for solutions, I did some experimenting, the most recent is described below:
I installed a third language as well, French this time, in which I am not fluent, but have a basic understanding. When the installation of the two extra languages was complete (edubuntu 10.04) I did a restart and found my menu to be almost entirely in Greek. So I did something that I tried successfully before, I went back to the language support and deleted the Greek language, but left the keyboard as it was with all three languages. Upon next restart, all the menus were in French, so i had no choice I deleted the French language. When I went back, there was no more French menus, but very few Greek menus appeared, one under system/preferences and 7 under system/Administration.  This was great, now I had no problem, so I decided to check on spell checking and to my great surprise both Greek and French enjoyed full spell checking support.
When I was deleting the two languages the screen indicated that many language related packs were being deleted also (related to Greek and French), so I did one more experiment: Using the command
```
dpkg --get-selections
```
I downloaded all the files installed in my computer, first after deleting Greek and second time after deleting French also. To my great surprise there were numerous language files in those two lists and in both languages that were previously installed and when I checked again by typing Greek and French text, it was all corrected properly.

So as you can see, I do not have a problem now, simply perplexed.

One more thing, after installing the two extra languages I placed them in the order: English USA, English Canada, Greek and French followed by the plain English which will not read anything after it and click the button "Apply System Wide"

I have two hopes:
1. That someone has a reasonable explanation for this problem and let me know about, possibly also a better method to install a second and third languages and
2. Someone may have the same problem and he/she may use this method and at least temporarily solve the problem.

All the best to the team

Costas Lazarou

---

