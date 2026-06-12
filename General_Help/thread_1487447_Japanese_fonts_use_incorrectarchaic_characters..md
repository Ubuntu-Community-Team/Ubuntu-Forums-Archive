---
title: "Japanese fonts use incorrect/archaic characters."
date: 2010-05-19
forum: General Help
---

### Post by evilestmark on 2010-05-19
I have the Japanese language pack installed and I have ibus and anthy installed for input method management.  It all works fine and dandy.  Except that some kanji aren't right.  Like &#31038;&#20250; the first of the two kanji displayed for me is the archaic version.  I can't seem to figure out why this is happening.  I can only assume it's picking up data from the wrong font package, but I'm not sure how to manage this.  Happens in ibus for my own input and on websites like [www.jisho.org]("http://www.jisho.org") where my input was unrelated.

Using a fairly fresh install of ubuntu 10.04 lucid, I used scim for IM in Karmic but still stuck to the default japanese language support pack.  Worked fine until lucid.

I don't know how font management works in Ubuntu, so go easy on me.

---

### Post by Frantic_Earthling on 2010-05-27
Exactly the same problem here. 

I am using iBus and Anthy, though

---

### Post by Frantic_Earthling on 2010-06-04
Apparently, either no one experiences the same problem or there is no solution?

Have you found one?

---

### Post by UggsY on 2010-06-05
Hi, I have the exact same problem here on Anky.
I've been able to gather some answers but none of it fixed the problem.

[http://swiss.ubuntuforums.org/showthread.php?p=8948627](http://swiss.ubuntuforums.org/showthread.php?p=8948627)
[http://ubuntuforums.org/showthread.php?t=1359987](http://ubuntuforums.org/showthread.php?t=1359987)

I still get wrong (or a more exact word would be old) kanjis such as   p, li { white-space: pre-wrap; }&#31038; being the old japanese form.

(sorry for my poor english)

---

### Post by Frantic_Earthling on 2010-06-12
After a lot of experimenting, I have found a solution.

First of all, please understand that I am using iBus and that I am running 10.04.

I am afraid that I cannot explain what exactly did it, but after uninstalling and reinstalling lots of fonts, I found that the following configuration solved the problem.

You should install exclusively the following:

ttf-umeplus
ttf-kochi-mincho-naga10
ttf-kochi-gothic-naga10
ttf-sazanami-gothic
ttf-sazanami-mincho
otf-ipafont-mincho
otf-ipafont-gothic
otf-ipaexfont-gothic
otf-ipaexfont-mincho
anthy
libanthy0
ttf-takao-pgothic
ibus-anthy
libtext-wrapi18n-perl
acroread-fonts
python-chardet
im-switch

Please note that I am aware that there are no so-called language support files, and that some of the above may actually not be necessary to properly display Japanese. I cannot however be more specific than saying install the above and only the above, remove everything else that has to do with the Japanese language and you should be rid of your problem.

---

### Post by UggsY on 2010-06-21
Hi Frantic_Earthling, so i did all what you said, erased everything related to japanese and installed everything you listed (except acroread-fonts which i did not find) and thanks to you it is now working.

Thank you very much, it sure is a lot easier to learn kanjis with their correct form !

I guess i won't have to switch back to windows whenever i want to learn kanjis anymore...

---

### Post by Frantic_Earthling on 2010-06-22
> **UggsY said:**
> Hi Frantic_Earthling, so i did all what you said, erased everything related to japanese and installed everything you listed (except acroread-fonts which i did not find) and thanks to you it is now working.

Thank you very much, it sure is a lot easier to learn kanjis with their correct form !

I guess i won't have to switch back to windows whenever i want to learn kanjis anymore...

Glad to hear that it worked!

Acroread fonts are required if you want to display Chinese or Japanese PDF documents with Adobe Reader. You do not need these fonts for other purposes.

---

### Post by kmajor on 2010-10-06
Using a fairly fresh 10.04 install, using the gui to install Japanese via the Language support piece.  I ran into the same crappy fonts....  I installed just
ttf-kochi-mincho-naga10
ttf-kochi-gothic-naga10
ttf-sazanami-gothic
ttf-sazanami-mincho

and that got my fonts looking good again, at least in Anki and text editors.  This seems to always be a problem in every version of Ubuntu, though it does seem to be getting easier every version.  

&#12354;&#12426;&#12425;&#12372;&#12392;&#12358;&#12358;&#12358;&#12358;&#12358;&#12358;

---

