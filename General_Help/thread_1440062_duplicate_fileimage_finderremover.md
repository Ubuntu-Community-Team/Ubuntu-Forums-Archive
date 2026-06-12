---
title: "duplicate file/image finder/remover"
date: 2010-03-27
forum: General Help
---

### Post by varunendra on 2010-03-27
Hi everybody!
Is there any duplicate file finder/remover for Ubuntu as much powerful as "Vistanita Duplicate Finder" (it is for Windows only:()?

I,ve just about started migrating from Windows XP to Ubuntu Studio & amn't very used to it, although I like its looks, performance & stability very much! \\:D/

Best alternatives?

---

### Post by lavinog on 2010-03-27
I used to use a program called fslint...it had different things to help clean up your system, but it included a way to find duplicate files.

I came across a command line version once...but forgot its name.

I have written various scripts for accomplishing the same tasks...basically it compares md5sums of each file.

---

### Post by lavinog on 2010-03-27
Attached is a duplicate file finder I wrote in python a while back.
```

python finddupes.py [basefolder]

```

You can leave basefolder blank and it will start from the current folder.

It skips files larger than 100M
if you need to check larger files, edit the script and change MAXFILESIZE = 100  #Mb to something larger.

---

### Post by Sin@Sin-Sacrifice on 2010-03-27
```
sudo find / -name filename.extension
```

---

### Post by varunendra on 2010-03-27
Thanx lavinog/ Sin@Sin-Sacrifice, appreciate your suggestions.

However, I was basically looking for something which can detect** visual similarity** as well (to find dup. images even if they're differently sized, named)

Have already installed FSlint. seems quite useful but doesn't seem to have that capability. Same looks the case with your python-program lavinog, (haven't tried yet, just guessing based on your description. but thanks anyway!)

I am quite used to Vistanita in Windows & must say that it's extremely powerful in doing its job & has a very friendly & easy-to use interface. (I'm not praising Win... but the program). I also tried installing it over wine but it failed. ](*,)

Would greatly appreciate any help regarding that, even if it includes using a bunch of apps !! [-o<

---

### Post by lavinog on 2010-03-27
How often is a file similar but not a copy?
How fast is that program you mentioned

Does it find images that are lightly a different size?
Just curious.

---

### Post by varunendra on 2010-03-27
> **lavinog said:**
> How often is a file similar but not a copy?
How fast is that program you mentioned

Does it find images that are lightly a different size?
Just curious.
What I meant was "**visual similarity**" which strictly relates to image or picture files (photos, wallpapers, etc.) And encountering_ that kind of similarity is **very frequent** in my case_ since I keep swapping my data across multiple hard disks dumping wallpaper collections copied from various sources as well as copying my own valuable home images every here & there.

_Now for speed part_: I can't give any reasonable comparison but to me it looked surprisingly fast. It took only about 20 odd minutes on an Intel Xeon 3GHz machine with 2GB RAM & WinXP to search a total of 10+ GB of images/walpapers (more than 200,000 images) spread across various partitions of a 160GB HDD (which was almost full of these & other kind of data & I selected the whole hard disk to search)

_For size-difference issue_: It provides a slider to choose the level of similarity (0 to 100%) & this feature is simply great! **Size (either resolution or filesize in bits) is no issue**. It picks the duplicates_ entirely based on their visual appearance just like human eyes would do_.
Practically speaking, with 85% similarity chosen, it grouped images ranging from 200x150 to 1280x960 pixels (2-4Kb to 2-3Mb), but were visually (& only Visually) same (just what I needed!).

Having explained all of this, I'd like to mention that this is only one of its four modes of searching.
All the four modes are:
1. True Duplicate: *Looks for files that are bit-by-bit same, maybe with different names.*
2. Duplicate Pictures: *The one I've explained above*
3. Duplicate Music: *Files similar based on Genre, Bit-rate, Title,...etc. tags (not very reliable though)*
4. Duplicate Names: *Name suggests everything.*

If you wish, I can post the screenshots, or you can check it out yourself on [http://www.vistanita.com/](http://www.vistanita.com/)

Thanx for your time.

---

### Post by varunendra on 2010-03-27
Just installed "Visual Similarity Duplicate Image Finder" (again, for Windows only) over Wine.
After some errors, it got installed & currently seems to be working 'almost' correctly (filters aren't working, maybe a demo version limitation).

But it isn't nearly as good as Vistanita. Not suitable for working over large collections (displays only one pair at a time).

Still looking for some Linux alternative.

---

### Post by varunendra on 2010-03-28
Well...... 16hrs. since my last post & still...... ........  . . I thought it was a minor issue ...!:^o
:lolflag:
Maybe isn't *that small *an issue or maybe I'm expecting too much or maybe.... maybe ....maybe................:-k

Whatever! Life does go on & so would I with my dear lil Ubuntu setup. But would keep coming back to see if something like a real solution comes up.

I'm a small office network admin (the stupid type- in the initial stages of learning) & was planning to do something with Ubuntu+CentOS+VMware+Untangle to come up with some Active Directory type solution....... but that in some other thread, meanwhile I'm trying to come up with a fool-proof client side setup for users............ :-$.. ok.. not off the topic.

But this is just one of my users requirement as well (this original thread's question)

Mine is a media office & a couple of PC's are full of mismanaged duplicate images as well as other types of duplicate files.

---

### Post by xeddog on 2010-04-27
I don't know if this is too late, but I just downloaded the Vistanita Duplicate Finder demo and installed it in Wine 1.1.42 on Linux Lucid.  It has not completed running just yet, but it installed and appears to be working.

xeddog

---

### Post by switch10 on 2010-04-27
fslint!!!

```
 sudo apt-get install fslint 
```

I use it all the time to clean up my Music folder..  It works great..

---

### Post by varunendra on 2010-04-28
> **xeddog said:**
> I don't know if this is too late, but I just  downloaded the Vistanita Duplicate Finder demo and installed it in Wine  1.1.42 on Linux Lucid.  It has not completed running just yet, but it  installed and appears to be working.

xeddog
Thank you bro! IMHO, it's never too-late for answering an unsolved problem as long  as efforts & reasonable progressions are in place, and I am glad to see the  progress you brought to this issue.
Me too installed vistanita over  crossover & it worked "almost" perfectly except for lacking one  important functionality- Saving The Session! This feature was very  useful, sometimes necessary, in my case while dealing with huge array of  dupes spread all over the HDDs. The ones you have to be careful with  and sorting gonna take more than a working day.

Although this  workaround brought much relief to me, I still feel a bit disappointed  about not being able to find a native linux app yet!

Nevertheless,  it's about 2 months now using Ubuntu for my works - regularly &  intensively - and I'm much more happier than I used to be with Windows.
With  the help of this forum, never felt a need to switch to Windows to  accomplish a task.
But I must admit, I'm still not confident enough  to make my network users switch to it.
I'm waiting for SAMBA-4, and  of-course, native solutions for Vistanita, DaemonTools.....etc.:lolflag:
> **switch10 said:**
> fslint!!!

```
 sudo apt-get install fslint 
```I use it all the time to clean  up my Music folder..  It works great..
As I stated earlier, I tried it. It's undoubtedly a great application  and seems perfect at its job! But isn't meant for Visual Similarity  based search for duplicate images.

Anyhow, I really appreciate  your effort of trying it over wine & sharing your experience here.  I'd certainly update this thread whenever I make any significant  progress. Meanwhile, wine/crossover is the way to go.

Thanx  again!

---

### Post by lavinog on 2010-04-28
> **Bonfiglio111 said:**
> Try Duplicate Finder from Ashisoft, to [find file duplicate]("http://www.ashisoft.com")

Does it work with wine?
How is it different from fslint?

---

### Post by varunendra on 2010-04-28
> **lavinog said:**
> Does it work with wine?
How is it different from fslint?
Me too have doubts.

Just checked out the link and their screenshots. Can't say about speed but the lack of thumbnail previews gave me impression that for "image search", it isn't as good as Vis.... (sigh), you people must be thinkin' I'm crazy about it.

Moreover, if I have to rely on something from windows world, then Vistanita over crossover isn't bad.

Thanx for the try though.

---

### Post by switch10 on 2010-05-02
f-spot has a duplicate photo detector built in.  it can be found under Tools.

It checks the MD5, so this should work perfectly for you, and without using wine...

---

### Post by lavinog on 2010-05-03
> **switch10 said:**
> f-spot has a duplicate photo detector built in.  it can be found under Tools.

It checks the MD5, so this should work perfectly for you, and without using wine...

if it is checking the md5 it is looking at exact duplicates...the op is wanting something to find similar, and not necessarily exact copies.

I have a couple of ideas on how to implement such a tool, but it will be a while before I can tackle it.

---

### Post by varunendra on 2010-05-03
> **lavinog said:**
> if it is checking the md5 it is looking at exact duplicates...the op is wanting something to find similar, and not necessarily exact copies.
Exactly !

> **lavinog said:**
> I have a couple of ideas on how to implement such a tool, but it will be a while before I can tackle it.
Are u planning to develop a new app for this? If so, do you have any similar source code available? I'm not a programmer (as you might have already guessed by now), just curious.

---

### Post by lavinog on 2010-05-03
> **varunendra said:**
> 
Are u planning to develop a new app for this? If so, do you have any similar source code available? I'm not a programmer (as you might have already guessed by now), just curious.

I don't know yet.
It might be a fun challenge...I just don't know how to make it useful.
There are many ways to determine if an image is similar...one way may be more useful than another.  I could match photos with similar backgrounds so that it can be assumed that they were all taken at the same place.  I can match photos with the same faces (I don't know how to do this though).  Match photos with similar colors, or patterns...etc

A basic way to find similar images is to scale each image down to a small thumbnail (the smaller, the more tolerant) then take the difference between two images...if the difference is small...the images are similar.

---

### Post by varunendra on 2010-05-03
> **lavinog said:**
> I don't know yet.
It might be a fun challenge...I just don't know how to make it useful.
There are many ways to determine if an image is similar...one way may be more useful than another.  I could match photos with similar backgrounds so that it can be assumed that they were all taken at the same place.  I can match photos with the same faces (I don't know how to do this though).  Match photos with similar colors, or patterns...etc

A basic way to find similar images is to scale each image down to a small thumbnail (the smaller, the more tolerant) then take the difference between two images...if the difference is small...the images are similar.
Glad 2 c u! Don't know 'bout pro logics, but I had (don't know since when) an impression that it is some how done by dividing the image into defined blocks, then, in each block, determining the average RGB values of 'similar' pixels.
Also, I've experienced that vistanita doesn't work well when searching among images of very small resolution (say, 4x4 pixel) even if they're much different in colour or pattern.
It also makes a lot of mistakes while searching among normal thumbnail sized colour patterns that are often used as backgrounds.
Here, by mistake I mean that it places very different looking images into one group.

And..... if u can make it, it is already useful !!;)

---

### Post by RedRat on 2010-05-03
> **switch10 said:**
> f-spot has a duplicate photo detector built in.  it can be found under Tools.

It checks the MD5, so this should work perfectly for you, and without using wine...
Be careful using fspot and digiKam in looking for duplicates. I have found that digikam duplicate finder is not too great on some files, it shows the thumbnails and the two supposedly duplicate files did not look even remotely similar. Further it cannot give you a thumbnail for files over 1Mb, and that is all too common nowadays with large pixel cameras. 

the only tool I have found that can find similar and duplicate files is ThumbsPlus for Windows, Ya gotta buy it, but it is worth it. I found that it works under Wine quite well. Check out the Wine pages for some addons that are needed.

sound like ThumbsPlus is what you need.

---

### Post by varunendra on 2010-05-03
> **RedRat said:**
> The only tool I have found that can find similar and duplicate files is ThumbsPlus for Windows, Ya gotta buy it, but it is worth it. I found that it works under Wine quite well. Check out the Wine pages for some addons that are needed.

sound like ThumbsPlus is what you need.Welcome my freind. Just checked out ThumbsPlus description page. Seems dedicated to editing of pics, finding similars being a tiny add-on.
Once again, as I've repeated many times, Vistanita is much more useful & dedicated at finding similar images. Especially when you are dealing with large numbers.

As a matter of fact, you might also have realised by now that ThumbsPlus isn't the only tool for that purpose. There are others (None for Linux:() and are also better at this.

And yes, it is working 'almost' perfectly over crossover. As told by Xeddog, it also worked on Wine 1.1.42.

You really need to see the entire first page of this thread.
Thanx for your try.

---

### Post by mastermindg on 2010-11-07
I think before you shoot down a quality application like ThumbsPlus you might want to use it for a while and maybe you will realize that it is exactly the tool for this purpose.

Just because it isn't exclusively developed for duplicate image resolution does not discount it's functionality. It is by far the best batch processing application for images that I have ever used on ANY OS. No doubt that an application could be developed for Linux but it hasn't been yet.

You should really read the first page as well. Your request was for an application that will recognize differences in "visual similarity" as well as file name. ThumbsPlus does this.

I'm using it under Wine 1.2 right now and all functionality is present. Vistanita might work for you but that does not mean that there are not other programs that are capable of doing the same (and more).

Thanx for your time.

---

### Post by swejap on 2010-12-03
Allot of different opinions on application to handle this work of finding and deleting duplicates. I read allot about fslint and tested it my self with other similar duplicate finding applications. But what I would like to know, if anyone can answer here, is how safe it is to delete the results and if the results are the duplicates or both duplicate and originals?

I have around 10000 pictures that are duplicates. Don't ask me how I messed up to get this, but I wanna know for sure that I am deleting the right files and leave behind the ones I want.

As you can understand, going trough 10000 manually is not something I feel to excited about.

Appreciate any answers.

---

### Post by RedRat on 2010-12-03
> **swejap said:**
> Allot of different opinions on application to handle this work of finding and deleting duplicates. I read allot about fslint and tested it my self with other similar duplicate finding applications. But what I would like to know, if anyone can answer here, is how safe it is to delete the results and if the results are the duplicates or both duplicate and originals?

I have around 10000 pictures that are duplicates. Don't ask me how I messed up to get this, but I wanna know for sure that I am deleting the right files and leave behind the ones I want.

As you can understand, going trough 10000 manually is not something I feel to excited about.

Appreciate any answers.
Look, if you have 10,000 images that you think are valuable, I would not rely on any automatic removal. You have little choice but to do this manually. As I state earlier, ThumbsPlus is a good tool. The sort by similarity is not a small addon. The only Ubuntu program that has this capability is DigiKam. However, I found that it failed to find many duplicates and you still had to go through the list by hand. Unless it has been updated recently, it wouldn't show thumbnails for pictures larger than 1Mb, today that is not an uncommon size. 

You have an enormous task ahead of you here. But perhaps you can divide and conquer. Perhaps break up the 10,000 into file folders with only a few hundred pictures. Run similarity on that folder and delete the duplicates. ThumbsPlus can show both the file size and image size, which helps your decision making process.

---

### Post by swejap on 2010-12-12
> **RedRat said:**
> Look, if you have 10,000 images that you think are valuable, I would not rely on any automatic removal. You have little choice but to do this manually. As I state earlier, ThumbsPlus is a good tool. The sort by similarity is not a small addon. The only Ubuntu program that has this capability is DigiKam. However, I found that it failed to find many duplicates and you still had to go through the list by hand. Unless it has been updated recently, it wouldn't show thumbnails for pictures larger than 1Mb, today that is not an uncommon size. 

You have an enormous task ahead of you here. But perhaps you can divide and conquer. Perhaps break up the 10,000 into file folders with only a few hundred pictures. Run similarity on that folder and delete the duplicates. ThumbsPlus can show both the file size and image size, which helps your decision making process.

Thanks for the reply and information. It is very valuable. I actually found that Adobe bridge have a very useful tool for searching and remove duplicates by entering meta-data information. FOr example in my case I had a folder with allot of images that I edited in Adobe Lightroom. All images got a tag with Adobe Lightroom in the meta-data, so it is easy for Adobe Bridge to sort these images out and from there I can start deleting those I am sure of is edited and not originals.

But as you said it is a big task ahead of me. Just for fun of it I made a backup of the image folder and tried fslint. Here is the result:

> Before using fslint: 33,729 items, totalling 129.5 GB

After using fslint and deleting files: 23,150 items, totalling 75.9 GBhehe its a bit different but dont feel safe with that result so will sort out manually :P

---

### Post by naklinaam on 2011-04-26
Google search yielded findiamgedupes. This looks like exactly what you are looking for. I have just installed it. Will update this post with the usage experience and results once I have played with findimagedupes. The nest thing is that it is available in standard repository and can be added using synaptic package manager.

[http://manpages.ubuntu.com/manpages/natty/man1/findimagedupes.1p.html](http://manpages.ubuntu.com/manpages/natty/man1/findimagedupes.1p.html)

---

### Post by Britmonkey on 2011-08-28
Just to add to the info here, I use unique filer for finding images.
 
its a specialist image duplicate finder (nag-ware) but seems to work fine under wine 1.3, just runs slower than in windows.

---

### Post by okaar on 2012-10-04
GQview is the most amazing, simple and fast image manager that I have ever tried. I was trying to do the same and this thing makes miracles. Just filtered +3000 of images :p

[http://gqview.sourceforge.net/docs/5_2_finding_duplicates.html](http://gqview.sourceforge.net/docs/5_2_finding_duplicates.html)


Quite easy to use use drag the files, select Similarity(high) and I would recommend you to select thumbnails.

---

