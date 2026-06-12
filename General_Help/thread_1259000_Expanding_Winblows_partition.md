---
title: "Expanding Winblows partition?"
date: 2009-09-05
forum: General Help
---

### Post by c0mput3r_n3rD on 2009-09-05
Hello all,
  I've been running Ubuntu completely on my computer for some time, how ever I had to install Windows on my computer so that I could webchat.  Since I hate winblows with a passion, I only gave it a 1.5Gb partition, just enough to install AIM, and my drivers, including the webcams.  The only problem is that now I need Visual Studio in order to do Visual Basic .net work for a college course (as there are no good IDE's for Ubuntu), and need about another Gb of space.  Is it possible to expand my winblows partition to give myself more space on my HDD?  I have QtParted, and tried messing around with it (very, very carefully as I've seriously screwed up before messing around with it), with no avail.  If I have to reinstall XP as my only option, what do I have to do to take care of the boot loader, as winblows completely erases it, and boots XP with no boot menu?

Thank you for your time,
Matt

---

### Post by starcraft.man on 2009-09-05
I commend you on the tiny XP partition, ya stripped a lot out with an nLite type app eh? Nice. Standard install with updates would never fit that size.

Have you thought of simply moving the copy of xp over to a VM? No reason ya can't do either thing from inside one, only grpahics intesnive apps give trouble. Like games. VMs with a core or later CPU (or equivalent from AMD) with the virtualization hooks feel almost like regular unless ya do something demanding. One alternative, if interested install VBox, and install with your cd into that, can wipe xp off after if your satisfied.

If ya really want to expand, just boot up a live CD and run gparted from that. See gparted [docs here]("http://gparted.sourceforge.net/documentation.php") (old section better), basically, shrink a partition with too much (has to have free space equal to removed), move it next to partition ya want to expand, then resize.

---

### Post by JC Cheloven on 2009-09-05
@c0mput3r:
It is feasible to start from live cd, shrink your ubuntu partition (or whichever is next to the xp one), and then expand the xp partition by the same size. I did it some times, and didn't have any problems (backup your data first, though).

@starcraft:
Could you please try using standard english writing, so that everybody understands?

---

### Post by NoaHall on 2009-09-05
You don't need the VisualBasic.net app to build apps. Just the knowledge ;) Anyway, do you have ntfs-3g installed? I believe that allowed me to resize my old windows partition

---

### Post by c0mput3r_n3rD on 2009-09-05
Haha thank you starcraft, I really do hate winblows, and would not give it more than a 1/2 Gb's more than what I needed :)  Unfortunately, my cpu on my good desktop shorted out, so all I have is my IBM Thinkpad R40, no where near close enough to virtualize :(.  I will try booting up my computer with the live cd and try gparted, I didn't know that I have to shrink one, move it, and resize.

And noahall, what is ntfs-3g? Is that for winblows?  I would like to check that out as well.

Thank you everyone for your responses.

---

### Post by NoaHall on 2009-09-05
It's for accessing and editing ntfs partitions. You can get it from synaptic, or apt-get.

---

### Post by starcraft.man on 2009-09-05
> **JC Cheloven said:**
> @c0mput3r:
@starcraft:
Could you please try using standard english writing, so that everybody understands?

What are you my English teacher come to haunt me? Geez, it's a forum not one of my 20 page essays or an official wiki page I'm working on. I happen to have seen and replied to far worse English writing here without a word of complaint. 

computernerd: You don't need to install the nfts-3g drivers, they come preinstalled in Ubuntu for quite a long time now, methinks. I know because when I mess with partitions from jaunty liveCD I install nothing, gparted and all drivers are there, just wish Ubuntu installed gparted by default along with standard install.

---

### Post by JC Cheloven on 2009-09-05
> **starcraft.man said:**
> What are you my English teacher come to haunt me? Geez, it's a forum not one of my 20 page essays or an official wiki page I'm working on. I happen to have seen and replied to far worse English writing here without a word of complaint. 
...

I would have a hard time teaching english to anybody, as I think I am in urgent need for some english lessons myself. Please keep in mind that I have a different native language.  In fact, I had real difficulties in understanding your post. As I usually understand posts (more or less), I thought you were using some kind of slang. Sorry to raise the offtopic question here. 

And yes, ntfs-3g is incorporated to most distros since a long time. You can simply assume that ubuntu will cope with ntfs, and forget about the details.

---

### Post by starcraft.man on 2009-09-05
> **JC Cheloven said:**
> I would have a hard time teaching english to anybody, as I think I am in urgent need for some english lessons myself. Please keep in mind that I have a different native language.  In fact, I had real difficulties in understanding your post. As I usually understand posts (more or less), I thought you were using some kind of slang. Sorry to raise the offtopic question here. 

And yes, ntfs-3g is incorporated to most distros since a long time. You can simply assume that ubuntu will cope with ntfs, and forget about the details.

Only slang I used was ya instead of you, been hanging with too many Americans I suppose, fairly common use. I guess can admit a poor choice of words, most people know it though. Rest was simply incomplete sentences, I've repeated instructions for gparted very often... should put a link in my sig to reduce. It is off topic, probably should just leave it be then. I guess I get a bit cranky late at night with lots of posting, sorry for snapping.

---

### Post by JC Cheloven on 2009-09-05
> **starcraft.man said:**
> Only slang I used was ya instead of you, been hanging with too many Americans I suppose, fairly common use. I guess can admit a poor choice of words, most people know it though. Rest was simply incomplete sentences, I've repeated instructions for gparted very often... should put a link in my sig to reduce. It is off topic, probably should just leave it be then. I guess I get a bit cranky late at night with lots of posting, sorry for snapping.

Ah, americans are all fool :D  Now you=ya... I definitely need some lessons.

Keep the good work... and sleep a bit also.

---

### Post by starcraft.man on 2009-09-05
> **JC Cheloven said:**
> Ah, americans are all fool :D  Now you=ya... I definitely need some lessons.

Keep the good work... and sleep a bit also.

Go watch Ali G show, you'll pick up English slang fast :p

I kid, horrible, you'd speak terrible English. Best advice for learning is simply watch half decent TV. My second language teachers always recommended news broadcasts, use a bit more expanded vocabulary then say reality TV like Survivor. Or good drama TV that's scripted, say new Battlestar or classic MASH. Something with variety and half decent writing. Helps when ya see a visual cue with what's being described, makes connections easier than just reading.

Lucky I'm Canadian or might have gotten a bit miffed. Course ya knew that, saying home of Hockey kinda makes it too easy. 

Anyway, I best not reply again or some mod will pop in here and say starcraft.man, stop spamming up the forums. :p

*waits for it*

---

