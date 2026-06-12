---
title: "HELP. I think I have made a big one! :o("
date: 2010-09-22
forum: General Help
---

### Post by cino on 2010-09-22
Working on getting Wine, word and endnote working...
I had some serious problems with installations and after removing everything from wine and starting again, I now have a perfect working copy of word and EVERYTHING else on my hard drive is gone. 

Of course I did not back anything up.

I did a sudo apt-get autoremove.

I'm pretty sure I have lost everything.

Is there anyway to recover / roll back [I am very sad] to a day ago?

Oh dear. All my fault but any help?

---

### Post by Bucky Ball on 2010-09-22
sudo apt-get autoremove shouldn't have caused that kind of damage. Open System->Administration->Partition Editor and check what is on there re. partitions. Boot from a live disk and have a look. 

If EVERYTHING else on your hard drive was gone Word wouldn't be working as there would be no OS. Be more specific; what exactly is missing?

---

### Post by Bucky Ball on 2010-09-22
ps: Why not just leave a partition for Windows and use Word and Endnote there? I use Open Office and Zotero (bibliography/referencing app) in Ubuntu and covers all bases for me. Try to find alternatives or why not just use Windows?

---

### Post by WorMzy on 2010-09-22
```
I now have a perfect working copy of word and EVERYTHING else on my hard drive is gone.
```

I'm confused by this statement. It's impossible for you to run Word with wine if everything else is gone. Some clarification is needed, I think.

Have you been using "sudo" with wine? Don't do that. Wine should be run as *your* user, and everything it installs should be installed to ~/.wine/

---

### Post by cino on 2010-09-22
ok so, ummm, cough....

rm -rf james .wine

did not remove wine, but james, didnt it. 

partition shows 1. unallocated, 2.dev/sda1 - ext4, dev/sda2 - extended, dev/sda5 - linux-swap

---

### Post by cino on 2010-09-22
> **Bucky Ball said:**
> ps: Why not just leave a partition for Windows and use Word and Endnote there? I use Open Office and Zotero (bibliography/referencing app) in Ubuntu and covers all bases for me. Try to find alternatives or why not just use Windows?

dealing with the fact that I wiped everything...

Zotero and open office was what I was trying to do but had trouble with office integration. Guess I have time for fiddling now.

A little embarrassed with the rm -rf james .wine...

---

### Post by WorMzy on 2010-09-22
That command shouldn't have done anything too disastrous. At worst, if you ran it inside /home, it should only have removed your home folder; but I don't think it should have even done that, I get a "permission denied" error when trying to delete directories from /home, despite me being the owner of the folders in question.

If you did delete your home folder, then you can recreate it by running
```
sudo mkdir /home/james
sudo chown james:james /home/james
cp /etc/skel/* /home/james
```

Then log out, and log back in.

---

### Post by cino on 2010-09-22
> **WorMzy said:**
> That command shouldn't have done anything too disastrous. At worst, if you ran it inside /home, it should only have removed your home folder; but I don't think it should have even done that, I get a "permission denied" error when trying to delete directories from /home, despite me being the owner of the folders in question.

If you did delete your home folder, then you can recreate it by running
```
sudo mkdir /home/james
sudo chown james:james /home/james
cp /etc/skel/* /home/james
```

Then log out, and log back in.

mkdir: cannot create directory `/home/james': File exists

Thanks anyway, but that did not work.
Ubuntu does say that it was last updated 11hrs ago but what I think I have done is removed james, somehow... sorry for the lack of code, I did not really know what I was doing.

Cino

---

### Post by WorMzy on 2010-09-22
This means that you haven't deleted your home folder. (Assuming that you are james)

Can you describe exactly what is making you think that you've deleted everything on your disk, because I'm having difficulty understanding what the problem is.

---

### Post by cino on 2010-09-22
> **WorMzy said:**
> This means that you haven't deleted your home folder. (Assuming that you are james)

Can you describe exactly what is making you think that you've deleted everything on your disk, because I'm having difficulty understanding what the problem is.

Ok - yes, I have deleted my home folder, not my entire disk. Apologies.

---

### Post by WorMzy on 2010-09-22
There's no need to apologise, you just need to be more clear about what the problem is, and not blow things out of proportion. Giving us clear and accurate information helps us to help you find a solution to your problems much faster.

Since you've marked this topic as solved, I assume you've got everything working again?

---

### Post by Bucky Ball on 2010-09-23
Enjoy the learning curve and take a little thinking time. 

The 'rm' command you mentioned earlier shouldn't have removed anything as it did not have 'sudo' in front. As mentioned you would not have had permission to do much.

---

