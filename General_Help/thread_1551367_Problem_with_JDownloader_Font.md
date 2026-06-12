---
title: "Problem with JDownloader Font"
date: 2010-08-12
forum: General Help
---

### Post by TuxIsCute on 2010-08-12
I just wanted to get this in quick before work so that there might be replies afterword so here goes:

I installed the Ubuntu version of JDownloader on my system last night and it has unreadable fonts.  I'm currently using the sun-java with java fonts and all that but I have tried it on openjre too with the same results.  I don't know how to make it be right.

Any help would be nice.  Also, has anyone else got this problem!?

There is an image attached here of the problem.

---

### Post by lykeion on 2010-08-13
Hi
I've never tried JDownloader before, so I downloaded jdownloader_0.1-0jd1~lucid1_all.deb from jd-team PPA.
It worked fine for me, no strange fonts.
I don't know if that's the version you are using, but my guess is you've selected some strange language at installation to get the funny looking font you have.

You could try to select another language like this (guess it'll be a little tricky without a readable font):
* select the third tab
* at left: select "User interface" (with a monitor icon)
* at right: the first dropdown list is the language setting

Another solution would be to reinstall the application```
sudo apt-get remove jdownloader
rm -rf ~/.jdownloader
sudo apt-get install jdownloader
```Note that you need to remove the .jdownloader directory manually. Neither complete removal in synaptic nor using aptitude --purge will remove it.
At installation you'll be asked for your language again.

Hope this helps...

---

### Post by TuxIsCute on 2010-08-13
Thanks for the the UI information.  I was able to solve the problem.  Turns out the style that it was using at the time was the error.  (It was already set on English.)  The style was so off that even now I can set it back to other font thing.  Nasty it is!  I couldn't reset the style because I didn't know where the UI settings were.  So again, thanks for that.

If you do a massive amount of downloading like I do, then JDownlaoder is the program for you!  I loved it in Windows and now, thanks to you, I'm sure I'll love it in Linux too.

---

### Post by terezam on 2010-10-26
Thanks, Solved.

---

