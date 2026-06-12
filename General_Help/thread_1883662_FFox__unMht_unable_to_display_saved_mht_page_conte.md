---
title: "FFox / unMht unable to display saved mht page contents"
date: 2011-11-19
forum: General Help
---

### Post by thaitang on 2011-11-19
A curious problem just occurred recently. I save a lot of webpages for offline reading and I prefer to save mht's and so I have long-used FF with unMHT with success. Recently, however, I have noticed many of my saved mht files do not display the pages content, neither text nor pictures, nor anything else for that matter. When the page opens it is basically a scrolling series of blank pages in which sometimes there appear some box outlines, but again no page content.

I have the ubuntu flavour FF 3.6.23 with unmht 5.7, which I have since uninstalled, re-installed, uninstalled again and tried mozille archive format that supposedly supports rendering mht files as well, but with the same problem.

I am running ubuntu, actually my desktop of preference is xubuntu 10.10, but I do have ubuntu desktop installed also.

Now I just copied a few mht files over to a pen drive and opened them fine in a laptop running xubuntu 10.04, FF 3.6.18 and unmht 5.6.9.

It almost seems as though it is a FF problem, but I had no success googling to see whether other peeps might be experiencing similar issues.

Here is another odd thing I found. When I open the mht file and am looking at blank pages, if I ctrl+A and select all I can view the page source details fine, copy and paste them using gedit saving as an html file and the page's contents can then be viewed.

I have never had issues with mht files so i have never needed to take notice about permissions, but the mht files I save are 644, but even if I make them exe in case they need to be exe'd by unmht it makes no difference and they open fine as 644 using my laptop.

I wonder if anyone has ever had some similar issue, perhaps I have inadvertently enabled/disabled something without realizing it? 

Any ideas or suggs would be great since I rely daily on reading the mini library I have acquired for my studies.

BTW, my internet connection is dial-up and I have therefore resisted dloading FF that is not in the repos nor opera's browser for the moment until I see if I have to go that agonizing route or not just to test.

cheers,
tt

---

### Post by lovinglinux on 2011-11-19
Not sure why you get such issue. I would think it could be a cache issue, but the fact that you can see the page sourceis really weird. Try starting Firefox in safe mode:

```
firefox -safe-mode
```

If the problem persists, try a clean profile:

```
firefox -P
```

However I would recommned upgrading to Firefox 7. [Firefox 7 & Beyond Mega Thread](http://ubuntuforums.org/showthread.php?t=1712247) and getting the latest unMHT.

---

### Post by thaitang on 2011-11-21
Hey I appreciate the advice. Unfortunately neither solution altered the problem.

> However I would recommned upgrading to Firefox 7. Firefox 7 & Beyond Mega Thread and getting the latest unMHT.
I would really like to try rolling back to an unMHT add-on that is known to be working for me, as it is on my laptop. Is there any way when installing add-ons to install older versions?

If nothing else, then next time I have access to high speed I will try FF7, and also d/load opera to see if that can view the files on this computer. The computer is fairly new, about 2 months, but definitely this problem is very recent, int he past few days; so all was hunky dory on this computer before that.

cheers,
tt

---

### Post by thaitang on 2011-11-22
Ok so I am just on the brink of pulling out some hair here now.

I went to my wife'w work for some high speed download action and was looking for FF7 but finding no love. All I could seem to download from mozilla's webpage was V8 and now V10 and the unmht addon is not available for either of these releases.

I also d/loaded Opera, and the MHT files open up and display, but gawd the text is all bunched together and basically unreadable. But the text is now visible.

Something I did about a week or two ago was d/loaded rekonq just for s&giggles, and I got to wondering if something might have gone kafooey on me. I just uninstalled but it made no difference.

A couple of days ago this was annoying, but I need to read different MHT files daily for uni courses and now this is becoming a bit of an issue. Like I said above the files are fine on my laptop with an older version of FF and unmht, so I think something is borked with the versions of FF and unmht on this desktop, that is so much nicer to work on than my laptop.

if anyone has any advice I would really appreciate it. Like I also mentioned above I only have dial-up at home and so d/loading large files is a PITA. One temporary gay workaround I can do in the meantime is open the mht files in gedit and save them as HTML and they open and display fine in FF8 that I now have installed as my default. But it really is not the fix I want.

Actually the saving MHT to HTML with gedit messes up all of the links and some of the text formatting likely because the gedit cannot access the page's css or something like that details? Anyways, like I said crude temporary fix to give me access to the files I need, but not a solution by any means.

cheers,
tt

---

### Post by thaitang on 2011-11-23
I could really use some advice or suggestions on this one if anyone's got ideas?

---

### Post by lovinglinux on 2011-11-24
> **thaitang said:**
> I would really like to try rolling back to an unMHT add-on that is known to be working for me, as it is on my laptop. Is there any way when installing add-ons to install older versions?t

Yes:

[https://addons.mozilla.org/en-US/firefox/addon/unmht/versions/](https://addons.mozilla.org/en-US/firefox/addon/unmht/versions/)

Don't forget to disable automatic udate in the add-ons manager.

---

