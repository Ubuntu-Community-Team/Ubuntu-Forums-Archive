---
title: "AptonCD"
date: 2010-03-19
forum: General Help
---

### Post by Thomas Garman on 2010-03-19
Does any one have any experience using the package AptonCD?  I put Mint 8 into a virtualbox just to explore it a little bit and the only real difference between Mint 8 and Karmic that I found was AptonCD.  I like the idea of AptonCD because my internet connect is awful and it drops all the time so it is hard for me to download updates and large package files at home...
 
But when I make an AptonCD disk with one computer it does not actually work with Synaptic on another computer.  I can, however, install the .dep packages that AptonCD creates.
 
Also, even though I "completely removed" AptonCD from my laptop, whenever I try to use Synaptic, it tells me I have to install the AptonCD disk I made weeks ago to install any package and then Synaptic says it cannot install and package.
 
Is any one else having these sorts of problems?

---

### Post by rahilm on 2010-03-19
i tried aptoncd twice and it failed terribly for both times.. It just refuses to work. I had to resort to other methods to preserve my downloaded .debs..
The biggest disadvantage is that you have to actually burn it to a physical disk to make any use of it.

---

### Post by ajgreeny on 2010-03-19
> i tried aptoncd twice and it failed terribly for both times.. It just refuses to work. I had to resort to other methods to preserve my downloaded .debs..
The biggest disadvantage is that you have to actually burn it to a physical disk to make any use of it.
No you don't have to burn a CD each time, in fact I have never used it that way!
Just copy the .iso file aptoncd makes each time onto a flash drive to do the transfer.  See below for more.

I have a lot of experience of aptoncd and have used it to transfer the apt cache from one ubuntu to another, and also between ubuntu and mint, without any problems of any sort.  You must make sure the versions of ubuntu and mint are the same, of course, ie ubuntu 9.10 and mint 8, ubuntu 9.04 and mint 7, and so on, or it will definitely not work properly.  You will still get a warning about the CD being from another OS, but ignore that as ubuntu and mint both use the same ubuntu repos so no harm can be done.  You also need aptoncd installed on both computers.

Just out of interest, when you say it does not work with synaptic on another computer, are you trying to use the CD as a repository by adding the CD in synaptic?  If so, that is not how to do it.  You need to install aptoncd on the receiving computer and then use the restore facility of aptoncd to add the deb files to the cache.  In fact, I find it easier to just use the iso file that is made and copy that from computer to computer to use in the restore facility.

Try it out that way, it really does work and is extremely easy and effective.

---

### Post by Thomas Garman on 2010-04-05
Thanks for the suggestion.  I haven't got around to trying it the round about way you suggest but I will try it later this week when the BETA 2 releases for Ubuntu 10.04, since I will have to use my aptoncd iso to install a lot of packages faster than it would be possible to do over an internet connection.

---

