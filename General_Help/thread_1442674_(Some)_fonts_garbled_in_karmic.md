---
title: "(Some) fonts garbled in karmic"
date: 2010-03-30
forum: General Help
---

### Post by Elwro on 2010-03-30
Hello, today I started my system (I may have done an update yesterday evening) only to see that some fonts look very, very bad and sometimes are unintelligible. This happens e.g.:

- in JDownloader:

[IMG]http://i197.photobucket.com/albums/aa183/Elwro/czcionki1.png[/IMG]

(as you can see, you can hardly read anything, while the text in system menu and bottom system bar is prefectly fine)

- in both browsers I use (Opera and Firefox):

1) Facebook:

[IMG]http://i197.photobucket.com/albums/aa183/Elwro/czcionki3maly.png[/IMG]

 (notice how the words "Most recent" and "News feed" look as if all letters were too far apart)

2) Other sites: 

[IMG]http://i197.photobucket.com/albums/aa183/Elwro/czcionki2maly.png[/IMG] 

(notice how e.g. the word "wrote" again looks as all the letters are far apart; also, the whole font is stretched vertically.

These are PNGs I made with PrintScrn, so I guess the quality isn't best, but I hope the issues are clearly visible. I already checked the System -> Preferences -> Appearence -> Fonts and everything looks fine there; also, many websites -- including this one -- and programs (Open Office, Emacs etc) display OK. Could anyone help me find a source of the problem?

---

### Post by 3togo on 2010-03-30
goto JDownloader directory.....

cd JDownloader/libs
mv laf laf-bad
cd ..
java -jar JDownloader.jar

---

### Post by Elwro on 2010-03-30
Thank you VERY much. This fixed the JDownloader problem and the program looks a lot better than it did from he start :-) 

Still, I have no idea regarding the other font rendering issue.

Thanks again,

L.

edit: more info: the Adobe Reader 8 for Ubuntu, as well as the plugins for Opera and FF, did not display PDFs properly. Removed the reader and installed version 9.3.1 - the display is now fine. But the problem with fonts persists!

---

### Post by Elwro on 2010-03-30
Alright, found the culprit and fixed the issue.

If someone has similar problems: my issue disappeared after I removed two packages which came with wine 1.2.1 installation: ttf-symbol-replacement and ttf-tahoma-replacement.

---

### Post by la1234uk on 2010-07-06
FANTASTIC !

thanks a lot, I had exactly same problems. In some applications, like scilab, droidDraw and others I had menu's fonts perfectly OK, but submenus too small to read... I really could not solve that, until I found your post. 

just removed ttf-symbol-replacement and fonts were fixed !

Thanks a lot.

I have Ubuntu 10.4.

GR

PS: By the way, how did you find this solution ? By trial and error ?:p

---

### Post by Elwro on 2010-07-06
> **la1234uk said:**
> 
PS: By the way, how did you find this solution ? By trial and error ?:pFirst, it's fantastic that my solution worked for you, I can't even remember how many times I benefited from these forums, so it's nice to see that I've been helpful at least once :-)

And regarding the method: after losing a few hours on dealing with the problem to no avail, I remembered that I had installed a new version of Wine a few days earlier. So I ran Synaptic and chose "History" from the "File" menu. It turned out that these two font packages were installed at the same day when I installed Wine. I thought "Well, OK, perhaps it's worth checking out", uninstalled them... and voila :D

Frankly, I didn't even know before that Synaptic had such a useful menu like "History".

---

### Post by bademeister on 2010-08-11
Elwro,

thanks a lot, this also fixed the issue with jDownloader for me (the trick of renaming the laf directory worked only temporarily (i.e. a few seconds)).

cheers P

---

