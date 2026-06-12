---
title: "Dual booting problems"
date: 2009-07-24
forum: General Help
---

### Post by Seargentown on 2009-07-24
I installed ubuntu fine, I did everything right, followed every step.

But I cant get vista to work, im not sure if i did something wrong.

When the GRUB dual boot screen comes up it says ubuntu and everything. Than in other OS'S it says windows vista (loader), theres 2 of them. First one starts vista, second one starts recov. So I click first first vista loader. Microsoft screen loads, than it just goes black. Help? :confused: Ubuntu works fine.

---

### Post by rcayea on 2009-07-25
Could you please be more specific about when the screen goes black? Does it go black right before the desktop should appear or another time?

---

### Post by Seargentown on 2009-07-25
Another time, after the microsoft loading screen. Sorry about that. :)

---

### Post by nmaster on 2009-07-25
i don't really know whats wrong (sorry!) but maybe try using this repair disc. 

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by rcayea on 2009-07-25
I am thinking if that was my situation, I would pop in the Windows disk and run repair files (or what they call it). It sounds like an obvious detection issue.

---

### Post by Seargentown on 2009-07-25
Will this let me keep ubuntu? Also will I keep ALL my files? I'm talking from vista and ubuntu.

---

### Post by Seargentown on 2009-07-25
> **rcayea said:**
> I am thinking if that was my situation, I would pop in the Windows disk and run repair files (or what they call it). It sounds like an obvious detection issue. I would of done that, but I was so stupid and threw it away... :(

---

### Post by SoftwareExplorer on 2009-07-25
If you boot the Ubuntu Live CD can you go into Vista's partition? Are all the files you would expect to be there still there?

---

### Post by Seargentown on 2009-07-25
> **SoftwareExplorer said:**
> If you boot the Ubuntu Live CD can you go into Vista's partition? Are all the files you would expect to be there still there?Let me check, 1 sec.

---

### Post by Seargentown on 2009-07-25
What should I do when I put the cd in? Like how do I check vista's partition?

---

### Post by nmaster on 2009-07-25
> **Seargentown said:**
> I would of done that, but I was so stupid and threw it away... :(

thats exactly what this is.  you can't install vista from this disc but you can repair it.
[http://neosmart.net/blog/2008/window...disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

---

### Post by Seargentown on 2009-07-25
> **neal.m.master said:**
> thats exactly what this is.  you can't install vista from this disc but you can repair it.
[http://neosmart.net/blog/2008/window...disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")Alright, burning the iso right now. Thanks for the link. :D

---

### Post by nmaster on 2009-07-25
> **Seargentown said:**
> Alright, burning the iso right now. Thanks for the link. :D

np.  i've never needed to use it, but i've heard that its a good  tool.

---

### Post by Seargentown on 2009-07-25
> **neal.m.master said:**
> np.  i've never needed to use it, but i've heard that its a good  tool.I'll keep just in case lol.

---

### Post by Seargentown on 2009-07-25
Ugh... just burned 32 bit instead of 64... that gets so annoying...

---

### Post by nmaster on 2009-07-25
> **Seargentown said:**
> Ugh... just burned 32 bit instead of 64... that gets so annoying...

there's nothing we can do to help you on that front :)

---

### Post by SoftwareExplorer on 2009-07-26
> **Seargentown said:**
> What should I do when I put the cd in? Like how do I check vista's partition?

I suggested it because it would let you see if the files you would expect to be there are there. For example: /Windows /User /Program Files etc

---

### Post by Nburnes on 2009-07-26
I believe that if you use that Vista Repair disc or whatever then it is going to re-install the entire vista boot loader so then you won't have GRUB anymore?

Then you would need to use EasyBCD to add Ubuntu to Vista bootloader or use something like Supergrub or your Ubuntu LiveCd to re-install GRUB.

---

### Post by SoftwareExplorer on 2009-07-26
> **Seargentown said:**
> Ugh... just burned 32 bit instead of 64... that gets so annoying...

I Admit it. I've done the same thing before except it was 64 bit ubuntu on 32 bit computer. (Which does not work, but a 64 bit computer can run 32 software. Confusing, huh?)

---

### Post by SoftwareExplorer on 2009-07-26
> **Nburnes said:**
> I believe that if you use that Vista Repair disc or whatever then it is going to re-install the entire vista boot loader so then you won't have GRUB anymore?

Then you would need to use EasyBCD to add Ubuntu to Vista bootloader or use something like Supergrub or your Ubuntu LiveCd to re-install GRUB.

@Seargentown Don't worry. Grub isn't that hard to reinstall if you have a Ubuntu Livecd.

---

