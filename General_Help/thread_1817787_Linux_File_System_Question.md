---
title: "Linux File System Question"
date: 2011-08-03
forum: General Help
---

### Post by OverlordYertle on 2011-08-03
I'm hoping that I must be mistaken or missing something and so I have posted this threat in the hopes that someone would help me, and possibly others, to understand the current set up.

I've heard from a lot of friends who try Ubuntu or other linux distros that the Linux file system is very confusing. I've also heard the other argument that at first it seems sort of complicated but it does start to make sense once you know what all the folders mean. My question is more should this still be the way?

From what I understand the linux file system was developed with respect to a common problem in the early days of computers and that was due to space. Certainly even today people are looking for more space but in the early days the problem was more for the fact that the programs themselves took up a lot of space rather than today when media and content generation are the real hogs of the hard drive. As far as I've been able to find the linux file system is set up so that programs can easily share resources. 

An installed application spreads itself in lots of different places on the hard drive so that the system and other applications can access common parts of the programs in order to save space. But when you start browsing through the file system folders are strewn all over the place and a basic user looking for something, the file system provides no help for them to know where to go.

The other problem is that there seems to be a certain number of standard folders that pop up in the root directory such as etc and lib among others. Now I don't have much issue with that. I understand they're 3 letters due to saving space, especially when they come from a time when characters could add up to take up lots of space. And perhaps a certain bit of speed may go into it, I'm not sure. However my real confusion with this matter comes from the fact that in your etc folder you may find another group of these folders of etc and lib and the others and they seem to sprawl out like a tree of confusion. They compound themselves so looking for something becomes exponentially more difficult due to the multitude of repeat files. Why would they simply not be in the root file structures, why be in etc sub lib verses simply lib?

Resource sharing today saves mere megabytes. A small percent of what it took up in yesteryears, yet even today the new Unity browser seems to be an attempt to match what others in the industry are doing in an effort to be more centered around applications and help users get to where they want to go faster. However it seems that it would be so much more intelligent to simply have all applications be in a folder. All the applications could have their own folder in the root directory sub App or something.

Linux's file system seems a tad bit more anarchistic than Mac or Windows. Though mac seems to share some of the repeat file systems as linux. And windows still sticks with the .DLL resource sharing from the days of computer yor. But more and more that appears to be out of having a better handle on piracy when all the resources of an application are not contained within it's own folders but imbedded in files systems. 

Yet linux mythos and ideology always seems to revolve around the spreading of information and the enhancement of freeing computers. And the humongous opensource community seems to all reflect this nature. So the anti-piracy measures built in to Windows seem to not completely apply to concerns with Linux.

It seems to be more beneficial or make incredibly more sense if a program was self contained inside of a folder and perhaps dependent only on resources that would come with a version of Ubuntu or some other version of linux. The reason for this is the drastic simplicity that would come with it and users would be very understanding of where to find applications. 

But most radically and I feel most importantly is there are times when my neighborhood is out of internet. Or I'm visiting with a friend and we're hanging out at a place without internet access. If I were to simply put in a USB stick to my computer, go to the App folder and drag the program I want to give to him on the drive then give him the drive and have him copy that folder to his drive and then it would just work.

That seems to follow the spirit of linux more than anything else because the ease of such a "feature" would be so radical compared to how everyone else does it. I feel like I have to be missing something for it to not already be initiated. There must be some large benefit other than how it's always been done for it to still be this way after so long. And so if someone could please explain it to me I would very much appreciate understanding the benefits that the current system have.

Thank you so much for reading this and I appreciate and look forward to any replies.

---

### Post by CatKiller on 2011-08-03
It's not to save space.

Files are organized based on their function, rather than how they got there. This has the side-effect that you can use more optimised filesystems for different parts of the tree because you know how large the files are likely to be and how often they are likely to be written to, but that is not the primary reason.

It goes back a very long way. No one is going to change it now. You'll almost never need to know anything about it.

---

### Post by haqking on 2011-08-03
i think when you say file system you refer to the FHS or file heirarchy standard which has been around for a long time works very wel.

It is not hard, it is different to people coming from systems such as windows thats all.

It is a familiarity issue thats all.

---

### Post by gordintoronto on 2011-08-04
If you want to give your friend a program, give him the DEB.

Note also that there are quite a few "portable apps," which work the way you want, and then some. (You can run them from a flash drive.) You can find them at portablelinuxapps.org

As for the basic file structure, if it were changed, many gigabytes of documentation would need updating.

---

### Post by bodhi.zazen on 2011-08-04
The linux file system is as logical as Windows, it is more a matter of familiarity.

while you can get lost in the technical details:

[http://www.faqs.org/docs/linux_intro/sect_03_01.html](http://www.faqs.org/docs/linux_intro/sect_03_01.html)

**[SIZE="6"]A picture is worth 1,000 words[/SIZE]**

[img]http://techbu.com/wp-content/uploads/2009/06/filesystemhierarchyhb8.jpg[/img]

---

