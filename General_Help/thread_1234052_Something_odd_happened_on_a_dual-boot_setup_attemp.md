---
title: "Something odd happened on a dual-boot setup attempt."
date: 2009-08-07
forum: General Help
---

### Post by cptrohn on 2009-08-07
Ok, I am currently setting up a friends laptop for a dual boot after a complete HDD wipe (and thanks to the folks that suggested ```
man shred
``` from a live CD yesterday it worked great) there was  quite a bit of malware on the Vista machine so we decided to just wipe the HDD and start over.. So we used the Vista rescue discs to put the machine back into factory specs got the windows updates and then got rid of all the extras from the manufacturer and it is just running vista and Avast anti-virus right now..

So she likes Kubuntu 9.04 after using a few different live CD's so we went to set up her laptop for a dual-boot, so I took the installation process up to partitioning the disc to dual boot Vista and Kubuntu and resized the NTFS partion pretty much right in half giving about 180GB to each OS... I had to run to the store real quick to pick up a USB memory stick to put Kubuntu on that for her so she could have it handy and somehow while I was away the installation stopped. (I suspect her kid stopped it playing around and pushing buttons because there was no crash and restart)

So I attemted to restart the installation and now when you get to what should be the partitioning section of the installation you don't have the option of resizing the NTSF partition and adding an ext3 partition.. I put in a gparted live CD to see f that could tell me anything at all, (like something went wrong earlier) but it only shows the Windows partitions and nothing for ext3 at all....

So is it screwed up and we would have to start completly over with another HDD wipe and then reinstalling Vista and then going for the Kubuntu install again?  Or is there something else going on?  I've done a few dual-boot set-ups and this is the first time this has happened..

---

### Post by NightwishFan on 2009-08-07
I have some suggestions.

Use the built in Vista partitioner to resize the disk, that way Windows never complains about it. To access it, right click on My Computer and choose Manage.

You can also try to install using Wubi, unless they really want a full installation. Wubi is much safer than a dual boot.

---

### Post by michy99 on 2009-08-07
Are you able to boot into Vista?

---

### Post by cptrohn on 2009-08-07
> **michy99 said:**
> Are you able to boot into Vista?

Yes, it boots into Vista with no problems at all.

---

### Post by cptrohn on 2009-08-07
> **NightwishFan said:**
> I have some suggestions.

Use the built in Vista partitioner to resize the disk, that way Windows never complains about it. To access it, right click on My Computer and choose Manage.

You can also try to install using Wubi, unless they really want a full installation. Wubi is much safer than a dual boot.

And then after that I can just install ubuntu into the free space that is available on the disc right?

Sorry, this is really the first time I have ran into this.

---

### Post by NightwishFan on 2009-08-07
Yes. That is how I dual boot Vista systems. If you use a 3rd party (non microsoft) partitioner there is a chance that Windows will complain and cause problems.

---

### Post by cptrohn on 2009-08-07
and she wasn't interested in Wubi.... she is looking for other options for an OS and was talking about buying a Mac and I told her about Ubuntu and she is open to trying it out futher to see if it is an option for her...I'm just trying to help her out because money is tight for her right now.

---

### Post by cptrohn on 2009-08-07
> **NightwishFan said:**
> Yes. That is how I dual boot Vista systems. If you use a 3rd party (non microsoft) partitioner there is a chance that Windows will complain and cause problems.

Ahh ok... I will try the Vista partioner then and it sounds like it will fix this little problem..

thanks for the help!

---

### Post by michy99 on 2009-08-07
> **NightwishFan said:**
> Wubi is much safer than a dual boot.

In what sense? It seems to me that the disadvantages of a Wubi install far outweigh the advantages.

---

### Post by cptrohn on 2009-08-07
> **NightwishFan said:**
> Yes. That is how I dual boot Vista systems. If you use a 3rd party (non microsoft) partitioner there is a chance that Windows will complain and cause problems.

Thanks for the help!  That was the problem, got Kubuntu 9.04 dual booting like a champ now..

(she was also impressed that I could just come to this forum for help and the issue was taken care of that fast... LOL )

Hopefully it works for her, the major issue she is worried about is Open Office vs. MS office....  So she will truly get to see them working as they should and make her final decision from there.

---

### Post by NightwishFan on 2009-08-08
Windows actually stores settings on the disk geometry in the registry I believe. If it does not match up problems can occur. So it is safer to calm to beast of Redmond and use its tools. (just a funny phrase not an insult) :D

I like openoffice, it is fairly solid. It is even getting support for macros which I will likely never need even. Also it is lets say not $300usd in price.

For users who say, do not know what partitioning is, it might be desirable. Partitioning has a real chance of causing major problems for users, so wubi can be a good option. It also means you can coexist Windows and Ubuntu perfectly, even using the Windows bootloader, so to remove Ubuntu is a snap. I used to use it on a school computer, so I could actually configure the thing. Then removed it when I no longer went to there.

---

