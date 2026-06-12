---
title: "something other than Brassero??"
date: 2010-04-29
forum: General Help
---

### Post by drumkitcat on 2010-04-29
Hi,
I'm running UbuntuStudio 9.1 on my Toshiba Satellite laptop, and all other aspects of the operating system and software are fantastic - absolutely love it!

I am having a serious problem with Brassero though for recording to CD.   I can erase any of my re-writable cd's just fine using it, but when it comes to trying to burn a cd with it - Brassero goes through all the motions of putting the info onto CD, finalizing and then briefly displays the box saying "completed" but then immediately goes into "creating image checksum" and keeps busy doing that into forever - last time I stopped it after 35 minutes! that's absurd.

Maybe it's because the laptop has a CD/DVD combo drive, not sure, but I need CD burning software, and that is for sure.

Can someone recommend a different software package that I can use to burn CD's covering everything from data to music?

(or possibly help me fix whatever is wrong with Brassero?)

Thanks!!

Paul

---

### Post by sunnyengineeer on 2010-04-29
Why don't you give a try to Nero 3 for Linux...
It works perfectly on Ubuntu & will definitely cater to ur need.

Try this link.
[http://www.google.co.in/url?sa=t&source=web&ct=res&cd=2&ved=0CA4QFjAB&url=http%3A%2F%2Fwww.nero.com%2Fenu%2Fsupport-linux3.html&ei=D4bZS7rWDsmvrAesxeDjDw&usg=AFQjCNHuvrIBQLZgGWO4_KB4k5aNCX8HYA&sig2=rPHSsYXu6c4GOtDhXhC2hQ](http://www.google.co.in/url?sa=t&source=web&ct=res&cd=2&ved=0CA4QFjAB&url=http%3A%2F%2Fwww.nero.com%2Fenu%2Fsupport-linux3.html&ei=D4bZS7rWDsmvrAesxeDjDw&usg=AFQjCNHuvrIBQLZgGWO4_KB4k5aNCX8HYA&sig2=rPHSsYXu6c4GOtDhXhC2hQ)

Thnks
Sunny Sharma

---

### Post by ghostborg on 2010-04-29
I use Nero and K3b.
Brasero for some reason has never worked for me other than a wonderful coaster maker. I have tried it with several distro's, computers and burners.
I can't believe that Brasero would still be around if it did this for everyone so I figure I must be doing something wrong. I just figure it should work since it's Ubuntu's default burner. Silly me, what was I thinking? I burn 3-6 discs a week average and almost always use Verbatim brand.

---

### Post by ajgreeny on 2010-04-29
Never mind Nero, try gnomebaker, k3b (probably the best app there is for burning in spite of being KDE), xfburn.  These are open source and therefoe fit into the linux philosophy better than Nero, in my opinion.

However, the question is, why does brasero not work for you?  Try removing or renaming the brasero configuration folders in ~/.config and ~/.gconf/apps to see if a new configuration helps you overcome this problem.  If it doesn't, I can recommend k3b wholeheartedly; it's what I always used until karmic, when I found brasero so much improved at everything, so it is what I now use.

---

### Post by anv on 2010-04-29
I considered to open new thread but noticed this one, which I feel can hold my question too: can some of these burn several disks at same time? If I have several CD/DVD burners in one machine I could copy one original with other drives: drive 1 holds original and drives 2-4 burn copy of it or I have one image which those 4 drives burn or maybe image 1-4 which drives 1-4 burn

---

### Post by drumkitcat on 2010-04-29
> **ajgreeny said:**
> Never mind Nero, try gnomebaker, k3b (probably the best app there is for burning in spite of being KDE), xfburn.  These are open source and therefoe fit into the linux philosophy better than Nero, in my opinion.

However, the question is, why does brasero not work for you?  Try removing or renaming the brasero configuration folders in ~/.config and ~/.gconf/apps to see if a new configuration helps you overcome this problem.  If it doesn't, I can recommend k3b wholeheartedly; it's what I always used until karmic, when I found brasero so much improved at everything, so it is what I now use.

Good points, thanks... I don't know if it's because my CD drive is a CD/DVD combo or not - which may or may not be causing the problem.  I am interested in something else that's open source or free... I use Nero on my Windows pc but if it's a cost to use it for linux, I don't know that I'm interested - partially because I'm cheap but partially because there are other options available that are free... I'm cheap but practical about it..

I will try the configuration folders for Brassero and see if that helps - I know it's fairly integrated into Ubuntu so if I can get it working then great.

---

### Post by ghostborg on 2010-04-29
I was using Nero because in the past I was having UDF version problems with discs going between Windows and Linux with multi-session discs.

---

### Post by philinux on 2010-04-29
K3b is very polished now.

---

### Post by drumkitcat on 2010-04-29
> **philinux said:**
> K3b is very polished now.

I had used K3b on Kubuntu 9.1 and it worked fine on my laptop - and I liked the interface, etc.

Can I use that in Ubuntu, or do I have to also install all kinds of Kubuntu libraries to use it?

I like Nero - it's a good software suite for sure, very comprehensive... just trying to explore some free options first.

---

### Post by SlugSlug on 2010-04-29
another k3b user on gnome here

---

### Post by MysticGold04 on 2010-04-29
When you install k3b, it will pull in the correct libraries for operation if you are running Gnome, or any other window manager for that matter... :guitar:

---

### Post by akakingess on 2010-04-29
@anv - personally, I think that you might be better off trying to burn one and make sure it is of good quality and then using that as your source burning/copying the several of the other drives. not sure which if any will burn to several different drives at once (I'm sure some or a few may do it, but you further risk errors when 'burning' rather than copying (in my humble opinion). I have always had better luck burning one good copy and then using it as source to copy to all of the others. Sorry if that's not what you wanted to hear, but just offering my advice. Also, depending on how many copies you are going to need, you could take that 'good' copy to a local industrial duplication/AV business and just telling them that you need x number of copies, it may turn out to be cheaper and they can do sometimes up to 50 burns per session and maybe get it done a little more quickly. That's what I have done in the past with some of my films. Good Luck!!

---

### Post by drumkitcat on 2010-04-29
Ok, I installed Gnomebaker - tried it out and it worked right away.

For my purposes, Gnomebaker does everything I need a cd burner software to do, so I'll stick with it.

Thanks everyone for your input!

Paul

---

