---
title: "Folder Moving Permission Denied"
date: 2009-10-19
forum: General Help
---

### Post by airplanes18 on 2009-10-19
im new to the forums but not to ubuntu. been with it since 8.04

i try to move my songs into the frets on fire songs folder and no matter what configuration of permission i place myself, it still denies me permission. no password prompt, nothing.

id like to know what obvious thing i miss. if this is in the wrong place, please move it. as i said, im a nub to these forums.

---

### Post by p0cky84 on 2009-10-19
If you seriously expect a serious answer, I suggest you learn to spell. Also, you might want to include some of the errors?

---

### Post by cariboo on 2009-10-19
@p0cky84

If you aren't willing to help. please don't post.

Press Alt-F2 and type:

```
gksu nautilus
```

Enter you password when asked. The above command will start the file manager as root, which will allow you to move the files to anywhere you want.

This really isn't a security question, so I'm going to move it to General Help.

---

### Post by airplanes18 on 2009-10-19
yeah thanks for the BS help there pocky/

and i did the command already. still denied. pocky, i think i spelled just fine so back off. first impressions must mean jack to you. i could easily own you in the face regardless of my rank. im a seasoned forum poster, and i dont back down from nobody. i am a member of psp.brewology.com and im pretty well know for ranting anyone till they beg me to stop. dont make this mistake. if you want my error, heres all i get.
@ cariboo
i try to move the file. it pops up a window with two options.one is cancel, the other is a rety button. after opening the arrow that hides what happened, it just says permission denied, although im admin. seriously stupid.

---

### Post by Dr_Bobby on 2009-10-20
Why not do:
 
```
sudo mv /original/folder/path /new/folder/path
```
 
And post the errors (if any) that arise.

---

### Post by QLee on 2009-10-20
[QUOTE=airplanes18]yeah thanks for the BS help there pocky/
[/QUOTE]
I know how frustrating it can be when one is trying to solve a problem and not getting anywhere yet.

While I agree that calling someone on their spelling, especially when the text is understandable, even if spelled incorrectly. I want to mention that sometimes spelling correctly does help one get the best, most useful answers and this forum checks my spelling. Please don't let your ego stop you from seeing any part of an answer that could turn out to be useful advice, including the exact text of an error message can often be the fastest way to a solution. Even giving the exact command you tried can help point to a solution. Wear a "thick skin" in forums, ignore any perceived or real insults and please don't threaten to fight back. A thread may become amusing for readers yet have very little technical content to assist the community.

In this case you could have told us where the directory (folder) is and what permissions were on it. Often, stating why you want to do something can be helpful, perhaps there could be an easier way to accomplish the actual goal. Since you have been using the distro for a while you probably understand that users can only move or change files and directories that they are authorised to deal with. As cariboo907 told you, as root you should be able to move any folder (though, it might not be a good idea in some cases).

---

