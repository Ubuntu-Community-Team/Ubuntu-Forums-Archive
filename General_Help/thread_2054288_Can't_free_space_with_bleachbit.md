---
title: "Can't free space with bleachbit"
date: 2012-09-07
forum: General Help
---

### Post by Kopkins on 2012-09-07
Tried bleachbit today for the first time and it seems great. Opened it up and tried to clean everything. It estimated that 2.93 GB would be freed. When I go to clean it I get permission denied for most of it. But not to worry because I can run bleachbit as root. When I preview as root 0 MB of space will be freed. 

I want those GB back. Also, screenshots for verification and clarity.

Bleachbit.png is as normal user and bleachroot.png is as root.

Thanks,
Kopkins

---

### Post by uRock on 2012-09-07
You have to run it as root. You can seach for it in Unity or open a terminal and run **sudo bleachbit** to run as root. Also, you will want to check the boxes under APT for much more free space.

---

### Post by Kopkins on 2012-09-07
> **uRock said:**
> You have to run it as root. You can seach for it in Unity or open a terminal and run **sudo bleachbit** to run as root. Also, you will want to check the boxes under APT for much more free space.

Yes I know, I ran it as root and as a normal user. I left out all the other check boxes to better illustrate what I'm trying to get across. As root, bleachbit doesn't recognize that here is space to be freed. Did you look at the screenshots?

Thanks,
Kopkins

---

### Post by mcduck on 2012-09-07
Based on the screenshot, most of the stuff is n your normal user's trash. And when you run bleachbit as root, it's of course lookign at root's trash instead...

---

### Post by Kopkins on 2012-09-07
Gotcha. I followed the path to where they are, as those files are not in my default trash. Then used sudo rm -rf to remove them. 

I posted this thread late last night, so confusion was probably the biggest issue. 

Thanks for your help. Solved.

Kopkins

---

