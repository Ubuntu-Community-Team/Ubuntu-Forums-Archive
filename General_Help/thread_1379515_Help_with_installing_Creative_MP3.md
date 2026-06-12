---
title: "Help with installing Creative MP3"
date: 2010-01-12
forum: General Help
---

### Post by Gutterboy on 2010-01-12
Hi. I am a new ubuntu user with ubuntu 9.10. I don't have much knowledge of computer systems in general and was wondering if anybody could give me some advice with a small problem I am having. 

I recently got a Creative Zen Mosaic EZ100 MP3 player, however when I dock it to my computer and try to install it by clicking the 'set-up.exe' file in the Starter Pack folder, Archive manager gives me this message/Command Line output:

[FONT=Georgia][B]Archive:  /media/My ZEN/Starter Pack/setup.exe
[/media/My ZEN/Starter Pack/setup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/My ZEN/Starter Pack/setup.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/My ZEN/Starter Pack/setup.exe or
          /media/My ZEN/Starter Pack/setup.exe.zip, and cannot find /media/My ZEN/Starter Pack/setup.exe.ZIP, period.

[/B]Wondered if there are some settings I need to tweak somewhere or something a bit more involved.

I'd greatly appreciate any help and explanations, 

Cheers.

 [/FONT]

---

### Post by michy99 on 2010-01-12
The set-up.exe file is for Windows; it will not work on linux. You can install Gnomad2 instead.```
sudo apt-get install gnomad2
```

---

### Post by Gutterboy on 2010-01-12
Thanks. I've installed Gnomad 2 and will mess around with this.Problem being I never had an MP3 player before even when using Windows so am new to this too ! 

So basically I won't be able to open the exe file to install the Zen on my computer? And Gnomad 2 is a way around this without having to 'install' in this way because the Zen is designed for Windows and nothing else?

Forgive me.. corner of the classroom for me.

Cheers.

---

### Post by michy99 on 2010-01-12
That's basically it. Unfortunately, some manufacturers just don't take Linux into account when setting up their software. The webpage for Gnomad2 is here:

[http://gnomad2.sourceforge.net/](http://gnomad2.sourceforge.net/)

---

### Post by Gutterboy on 2010-01-12
Thanks for the link. It appears that my device isn't listed in 'Working Devices' column as it is a Creative Zen Mozaic EZ100. Should I go ahead and try to set it up anyway. There is an article listed on the page as a guide to setting up the Zen with Linux but it seems it was written in 2004! 

[http://gnomad2.sourceforge.net/?section=article](http://gnomad2.sourceforge.net/?section=article)

---

### Post by granny6989 on 2010-01-12
FYi gutterboy - If you get Gnomad up and running (which should be no problem now through synaptic), you may notice that it never 'sees' your Zen. Due to some internal Gnome changes, you should plug in your Zen, wait for it to mount, and then go unmount it. You do this by either right click it on the desktop and then unmount, or find it under 'places' and hit the eject icon there. After you do that you should open Gnomad and it should fire up straight away.
Good luck.

S*

---

### Post by Gutterboy on 2010-01-12
Thanks michy99 and granny 6989 for the helpful replies so far!

granny6989 - I tried this but nothing happened. Wonder if there is some software I am missing. In the article [http://gnomad2.sourceforge.net/?section=article](http://gnomad2.sourceforge.net/?section=article) I mentioned in earlier post *libusb *and *hotplug *are mentioned. I can't find them on my list of installed software and can't find in the 'Get new software' option either, so wouldn't have a clue what to do if I required them.

Will keep trying and let you know. Would probably have taken me a month to get to this point without the help of you both!

---

### Post by michy99 on 2010-01-12
I found a possible solution here:

[http://ubuntuforums.org/showthread.php?p=8581513](http://ubuntuforums.org/showthread.php?p=8581513)

---

