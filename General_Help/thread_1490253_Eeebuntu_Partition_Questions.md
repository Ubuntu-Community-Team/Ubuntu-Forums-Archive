---
title: "Eeebuntu Partition Questions"
date: 2010-05-22
forum: General Help
---

### Post by Riniel on 2010-05-22
**[B][COLOR=black]Okay, so... I don't know much about linux, but I've been wanting to learn linux since I was about 12. [/COLOR]**[/B]
[COLOR=black] [/COLOR]
**[B][COLOR=black]Anyway, I just bought a new EeePC 1001P. I want to put Eeebuntu 3 on it and I was curious if I could get some help.[/COLOR]**[/B]
[COLOR=black] [/COLOR]
**[B][COLOR=black]I want to dual boot windows 7 starter, and Eeebuntu 3. So, my question is... Or rather a couple of questions. Haha.[/COLOR]**[/B]
[COLOR=black] [/COLOR]
**[B][COLOR=black]Do I need a separate drive for windows installs and Eeebuntu?[/COLOR]**[/B]
[COLOR=black] [/COLOR]
**[B][COLOR=black]Also, can my music and pictures be shared between windows and linux?[/COLOR]**[/B]
[COLOR=black] [/COLOR]
**[B][COLOR=black]This is how I usually have my computers partitioned.[/COLOR]**[/B]
[COLOR=black] [/COLOR]
**[B][COLOR=black]C drive for windows operating system[/COLOR]**[/B]
**[B][COLOR=black]D drive for software installs[/COLOR]**[/B]
**[B][COLOR=black]E drive for data like music, pictures, etc.[/COLOR]**[/B]
[COLOR=black] [/COLOR]
**[B][COLOR=black]I'm not sure what to do... I took my eeepc apart to get to the hard drive to ghost the drive and my warranty has been void because I took the chassis apart and tore a sticker that was covering a screw that was in my way to getting to the harddrive. [IMG]http://ubuntuforums.org/./images/smilies/icon_sad.gif[/IMG][/COLOR]**[/B]
[COLOR=black] [/COLOR]
**[B][COLOR=black]I'm pretty pissed that asus has done this. I own the property so why should it void my warranty to take the hard drive out to protect myself by ghost imaging the hard drive?[/COLOR]**[/B]
[COLOR=black] [/COLOR]
**[B][COLOR=black]Anyway enough with my rant... I'd appreciate any input on how I should set up my linux in conjunction with windows. Pleast let me know if I should keep my windows and linux install drives separate. I read on a website that it's best to have a separate partition for /home incase I need to reinstall eeebuntu.[/COLOR]**[/B]
[COLOR=black] [/COLOR]
**[B][COLOR=black]Sorry if I sound like an idiot, I have zero experience with linux. [/COLOR]**[/B]
[COLOR=black] [/COLOR]
**[B][COLOR=black]-Riniel[/COLOR]**[/B]

---

### Post by jamesisin on 2010-05-22
Pink letters against a white background is not fun to read.  Try black letters against a white background.

---

### Post by Riniel on 2010-05-22
> **jamesisin said:**
> Pink letters against a white background is not fun to read. Try black letters against a white background.
 
**[COLOR=black]To be honest, I don't really care if you don't like my pink font... If you don't like it, don't read it, and don't even bother saying anything. [/COLOR]**
[COLOR=black] [/COLOR]
[COLOR=#ff0080]**[COLOR=black]I came to this forum to get help, and I get some rude snidey remark.[/COLOR] **[/COLOR]

---

### Post by jamesisin on 2010-05-22
I am trying to help.  You are certainly more likely to get proper assistance on this (or any forum) by creating posts which are clear, legible, and comprehensible.  Sorry if that bothers you.

---

### Post by Riniel on 2010-05-22
> **jamesisin said:**
> I am trying to help. You are certainly more likely to get proper assistance on this (or any forum) by creating posts which are clear, legible, and comprehensible. Sorry if that bothers you.
 
**[COLOR=black]My posts are clear, legible, and comprehensible... It's just my font colour that you don't like, and in all honesty, it's just an opinion. Some people have no problem with my pink text. Furthermore, it did not seem like you were trying to help me, it seemed like to me you were just criticizing my text colour. I didn't get any real help on any of the questions that I asked. Maybe this colour will appeal to you? Or is this still too bright for you?[/COLOR]**

---

### Post by jamesisin on 2010-05-22
Maybe my use of the word fun threw you, but I was merely stating that if you use black letters it will make it easier for other forum members to read your post.  Thus far no one has responded to your post.

I speculate that merely changing your font color to black (or more accurately not changing it to begin with) is likely to garner more positive results.

It is difficult to read light colored letters against a light colored back ground.  That is a fact and no opinion of mine.

On my systems I use yellow letters against a black back ground--not because I am in love with those colors but because it is a fact of our color vision that it is easy to acquire and read yellow against black.  Regardless, I don't foist that color scheme on forum users from which I am attempting to garner interest.

There are likely many folks here who can help you with your Ubuntu issue.  Perhaps I'm even among them.  But I suspect that folks are opening the post, seeing it is difficult to read the lettering, and moving on.

---

### Post by Riniel on 2010-05-22
> **jamesisin said:**
> Maybe my use of the word fun threw you, but I was merely stating that if you use black letters it will make it easier for other forum members to read your post. Thus far no one has responded to your post.
 
I speculate that merely changing your font color to black (or more accurately not changing it to begin with) is likely to garner more positive results.
 
It is difficult to read light colored letters against a light colored back ground. That is a fact and no opinion of mine.
 
On my systems I use yellow letters against a black back ground--not because I am in love with those colors but because it is a fact of our color vision that it is easy to acquire and read yellow against black. Regardless, I don't foist that color scheme on forum users from which I am attempting to garner interest.
 
There are likely many folks here who can help you with your Ubuntu issue. Perhaps I'm even among them. But I suspect that folks are opening the post, seeing it is difficult to read the lettering, and moving on.
 
**There I changed it to black... Happy now?**

---

### Post by jamesisin on 2010-05-22
I was never unhappy.

---

### Post by Riniel on 2010-05-22
> **jamesisin said:**
> I was never unhappy.
 
**It seemed like it to me.**

---

### Post by jamesisin on 2010-05-22
What you want to do is pretty basic, so you should be able to set it up without too much trouble even if you don't know a lot about Linux yet.

I don't see a need to keep your Windows software on a separate partition from your Windows operating system, so I would probably partition your drive as follows:

[LIST][*]Windows OS and software — NTFS
[*]Ubuntu OS — ext3 or ext4
[*]Ubuntu swap partition — swap
[*]Data storage area — FAT32[/LIST]

Ubuntu (for the full version, there are netbook versions) needs only about 2.5 GB for installation; I would give it maybe 20 GB if possible.

The swap partition I usually make about twice the size of my RAM (2 GB RAM means 4096 MB swap).

Windows XP might need about 10 GB so also maybe give it 20.  Vista or 7 you should probably double that.

The rest can be your FAT32 data partition.

This isn't the only way to get there, but it's a pretty good one.

---

### Post by Riniel on 2010-05-22
> **jamesisin said:**
> What you want to do is pretty basic, so you should be able to set it up without too much trouble even if you don't know a lot about Linux yet.
 
I don't see a need to keep your Windows software on a separate partition from your Windows operating system, so I would probably partition your drive as follows:

[LIST]
[*]Windows OS and software — NTFS
[*]Ubuntu OS — ext3 or ext4
[*]Ubuntu swap partition — swap
[*]Data storage area — FAT32
[/LIST]
Ubuntu (for the full version, there are netbook versions) needs only about 2.5 GB for installation; I would give it maybe 20 GB if possible.
 
The swap partition I usually make about twice the size of my RAM (2 GB RAM means 4096 MB swap).
 
Windows XP might need about 10 GB so also maybe give it 20. Vista or 7 you should probably double that.
 
The rest can be your FAT32 data partition.
 
This isn't the only way to get there, but it's a pretty good one.
 
I like to keep my windows software separate from the operating system because software can corrupt the operating system.
 
I have windows 7 starter, and the hard drive is 250GB... I might uninstall and put windows XP on it because it's smaller, plus I like windows XP better. 
 
What is a swap partition? (I'm sorry to ask this, but I'm so familiar with windows, that anything to do with linux is new to me)
 
So, Windows and Linux can access music and pictures from one data drive? That's good news, I was afraid I'd have to have a separate drive for each operating system for music and pictures.
 
Also what is ext3 and ext4?

---

### Post by QLee on 2010-05-22
Riniel,
To me jamesisin's comments didn't seem either rude or snide, when I read it I believed he was trying to help you get an answer.

Since you are interested in eeepc, you might want to consider checking out this site which is specifically for your computer. That is probably a good place to get the information you seek because they probably have experience that you would want to tap with your exact hardware. 

[http://wiki.eeeuser.com/](http://wiki.eeeuser.com/)

[http://forum.eeeuser.com/](http://forum.eeeuser.com/)

---

### Post by Riniel on 2010-05-22
> **QLee said:**
> Riniel,
To me jamesisin's comments didn't seem either rude or snide, when I read it I believed he was trying to help you get an answer.
 
Since you are interested in eeepc, you might want to consider checking out this site which is specifically for your computer. That is probably a good place to get the information you seek because they probably have experience that you would want to tap with your exact hardware. 
 
[http://wiki.eeeuser.com/](http://wiki.eeeuser.com/)
 
[http://forum.eeeuser.com/](http://forum.eeeuser.com/)
 
Well, the "it's not fun" comment is what made me think he was being rude.
 
Anyway, thank you very much for the link to the eeeuser.com forums, and the wiki. I appreciate it very much, and I'll create an account and ask some people about it over there. :)

---

### Post by jamesisin on 2010-05-22
I have supported Windows environments for more than a decade.  I have never seen the presence of software corrupt the operating system.  You should be fine to keep them together.

Windows 7 is fine.  Stay away from Vista.  XP is smaller and lighter but not as feature rich or secure.  And Vista just blows.

Are you familiar with the page file in Windows?  Swap is similar.  It's where the operating system stores information it needs to swap out of RAM temporarily (hence its relationship to RAM size).

Yes, they can share a data drive.  FAT32 is convenient because any OS can access it.  It has limitations:

[http://www.soundunreason.com/InkWell/?p=39](http://www.soundunreason.com/InkWell/?p=39)

But they are not likely to be important based on what you stated.

There are all sorts of different file systems: ext2, ext3, ext4 (all 3 Linux based), FAT16, FAT32, NTFS (Windows), and many more.  You can read about any of them over at wikipedia.  The first paragraph should be enough to give you a basic understanding.  After that it will get exponentially duller.

---

### Post by QLee on 2010-05-22
[QUOTE=Rinie]I like to keep my windows software separate from the operating system because software can corrupt the operating system.[/QUOTE]

I don't see how keeping them on separate partitions would make any difference in this.
 
[QUOTE=Rinie]I have windows 7 starter, and the hard drive is 250GB... I might uninstall and put windows XP on it because it's smaller, plus I like windows XP better.[/QUOTE]

If so, I suggest doing whatever Windows install you want first and after you get windows working then install the next OS.
 
[QUOTE=Rinie]What is a swap partition? (I'm sorry to ask this, but I'm so familiar with windows, that anything to do with linux is new to me)[/QUOTE]

Been a while since I used Windows but don't they sometimes call it "paging file" too

---

### Post by Riniel on 2010-05-22
> **jamesisin said:**
> I have supported Windows environments for more than a decade. I have never seen the presence of software corrupt the operating system. You should be fine to keep them together.
 
Windows 7 is fine. Stay away from Vista. XP is smaller and lighter but not as feature rich or secure. And Vista just blows.
 
Are you familiar with the page file in Windows? Swap is similar. It's where the operating system stores information it needs to swap out of RAM temporarily (hence its relationship to RAM size).
 
Yes, they can share a data drive. FAT32 is convenient because any OS can access it. It has limitations:
 
[http://www.soundunreason.com/InkWell/?p=39](http://www.soundunreason.com/InkWell/?p=39)
 
But they are not likely to be important based on what you stated.
 
There are all sorts of different file systems: ext2, ext3, ext4 (all 3 Linux based), FAT16, FAT32, NTFS (Windows), and many more. You can read about any of them over at wikipedia. The first paragraph should be enough to give you a basic understanding. After that it will get exponentially duller.
 
Thank you Jamesisin... I appreciate the information.
 
My dad was a computer engineer at Intel for over 20 years, and he always taught me to have a separate install drive for installing software. He told me that software installed on the C drive can slow down the computer, and also corrupt the registry and the operating system files.
 
I will look up ext3 and ext4 on the internet. Thank you again.

---

### Post by jamesisin on 2010-05-22
Computers have changed a lot since your dad was with Intel.  Those old concerns have been replaced with new exciting concerns!

Seriously though, I wouldn't bother separating the software from the OS.  Drives are much faster today, and I just don't see how separating them might prevent any level of corruption today.

---

### Post by Riniel on 2010-05-22
> **jamesisin said:**
> Computers have changed a lot since your dad was with Intel. Those old concerns have been replaced with new exciting concerns!
 
Seriously though, I wouldn't bother separating the software from the OS. Drives are much faster today, and I just don't see how separating them might prevent any level of corruption today.
 
Actually he just retired not even a year ago... lololol.

---

