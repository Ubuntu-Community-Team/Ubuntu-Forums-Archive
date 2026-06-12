---
title: "10 failed installs"
date: 2006-05-29
forum: General Help
---

### Post by krypt0r on 2006-05-29
hi 

i am having trouble with installing ubuntu 5.10, i have an old machine limited space 4 gigs, is there anyway i can decide what programs to install, i won't use half of what gets installed, please advise as how to do this

---

### Post by the_tiger on 2006-05-29
I am not sure how to remove the packages at install. You might well be better off installing xubuntu. It is specifically designed to run better on older machines.

---

### Post by az on 2006-05-29
[QUOTE=krypt0r]hi 

i am having trouble with installing ubuntu 5.10, i have an old machine limited space 4 gigs, is there anyway i can decide what programs to install, i won't use half of what gets installed, please advise as how to do this[/QUOTE]
What problems do you have, exactly?

The default install takes up just over 2 gigs of space, so your hard disk is not your problem (unless you have another OS on it, taking up two or more gigs...)

---

### Post by zhoux on 2006-05-29
i suppose you can install ubuntu as a server, and then install software separately.  But for the details, some one else need to help.  I'm only a noob.

---

### Post by krypt0r on 2006-05-29
wow such quick responses

ok, firstly might have found a prob (read more of the forums) burnt 3 disks so far and they all have errors with one file or other, so am now burning another one from a different mirror, hopefully this is the answer

again thanks for the replies

---

### Post by EmmEff on 2006-05-29
Also, be sure to use 'md5sum' to check the images before you burn them...  if the md5sum checks out and the images don't work, you have bad hardware.

---

### Post by az on 2006-05-29
Try burning slowly, too.

---

### Post by krypt0r on 2006-05-29
thanks for the tip azz,

but using k3b i set it to 1x and noticed it bumped it up to 8x, nevertheless the cd-check was successful and am now going thru the install process, so shortly i hope to post a successful install

thank-you

---

### Post by krypt0r on 2006-05-29
nope
gets thru the base install then when copying remaining files it fails

---

### Post by zhoux on 2006-05-29
What does the error return?
I had trouble installing as well, it had something to do with the partitioner.  It seems that you have to allow the partitioner to totally repartition your HDD in order for the items to install correctly.  So check the partitioner and make sure that it will totally format your disk

---

### Post by az on 2006-05-29
[QUOTE=krypt0r]nope
gets thru the base install then when copying remaining files it fails[/QUOTE]


You don't need those extra packages.


If grub is not installed, try again with

linux archive-copier/copy=false

to install breezy without copying (cacheing) the extra packages after the system is installed.

It sounds to me like your optical drive is at fault.  I had that problem once or twice.  It would run fine for about a half hour and then crap out....

Is it an older optical drive and can you temporarily replace it?

---

### Post by krypt0r on 2006-05-29
thanks for that tip, trying it now, but just before that i thought i was golden when i hit 100% copied only to have a warning pop-up blabbing about apt and if i wanted to add another site or something along that line

also am thinking of swapping cd as per suggested

---

### Post by krypt0r on 2006-06-07
what a bunch of crap, have re-installed way too many times to no joy, and that is after having to dowdnload 4 different iso images (absolutely unacceptable) to finally get one that checked out, but it still won't install. i have never ever had to do so much for so little, i am totally p'd with this OS and am certainly not going to recommend it to anyone

---

### Post by EmmEff on 2006-06-08
Don't be so immature...  you've got hardware problems whether you want to believe it or not.  If you cannot download a valid ISO, you have a problem somewhere.

---

