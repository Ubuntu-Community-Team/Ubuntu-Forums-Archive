---
title: "How do I open apps not on the application list?"
date: 2010-01-05
forum: General Help
---

### Post by kinkinkijkin on 2010-01-05
I downloaded a WHOLE bunch of linux programs, but I can't open them. How do I open programs such as mupen64 plus? I only signed up to this forum to ask that question.



[SIZE=5][FONT=Century Gothic][SIZE=1]EDIT:[/SIZE]DO NOT ANSWER WITH SOLUTION. I SOLVED.

EDIT:EDIT: OK, UN-SOLVED. Programs no workey in XUBUNTU NOW!
[/FONT][/SIZE]

---

### Post by fancypiper on 2010-01-05
I recommend installing through adding repositories and synaptic (or command line apt-get install <program>).

[How To Install Software in Linux](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html)

[How to install ANYTHING in Ubuntu!](http://amitech.50webs.com/installing/index.php.html)

[Getting the Best Help on Linux Forums](http://www.psychocats.net/ubuntucat/getting-the-best-help-on-linux-forums/)

---

### Post by howefield on 2010-01-05
> **kinkinkijkin said:**
> How do I open programs such as mupen64 plus? I only signed up to this forum to ask that question.

[http://code.google.com/p/mupen64plus/wiki/README](http://code.google.com/p/mupen64plus/wiki/README)

Cheerio now.

---

### Post by 0cton on 2010-01-05
If you mean that you don't know were to find the application in the menu, open a terminal and type the application name. (In case it was installed "correctly" )

---

### Post by kinkinkijkin on 2010-01-05
Ummm..... I'm trying to execute it in the same way I execute files in windows. I MUST EMULATE N64!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by mocoloco on 2010-01-05
Mupen64 downloads just a compressed file, with extension .tar.bz2.  Go to where you downloaded it (usually in your "Downloads" folder), and then right-click on the file called mupen64-0.5.tar.bz2 and click "extract here".  It will create a new folder with the extracted contents.  Open in and double click on the executable to start the app (icon looks like a diamond with gears in it).
You can move it's folder to anywhere in your own home folder, or if you want more than one user to be able to access it you can as administrator move it to a shared location like /usr/local/share.

You can also add it to the menu by right clicking the application menu to bring up the editor.  Adding a new entry in the games submenu should be straightforward. You can drag and drop the icon from your file browser to the menu editor too.

As far as the other "whole bunch" of Linux games you've downloaded, it depends on what they've given you, if it's a zipped file, an executable installer like .sh or .bin, or a package like .deb or .rpm. 
Rule of thumb is, first search in Software Center, if not there see if there's a .deb.

---

### Post by kinkinkijkin on 2010-01-05
> **mocoloco said:**
> Mupen64 downloads just a compressed file, with extension .tar.bz2.  Go to where you downloaded it (usually in your "Downloads" folder), and then right-click on the file called mupen64-0.5.tar.bz2 and click "extract here".  It will create a new folder with the extracted contents.  Open in and double click on the executable to start the app (icon looks like a diamond with gears in it).
You can move it's folder to anywhere in your own home folder, or if you want more than one user to be able to access it you can as administrator move it to a shared location like /usr/local/share.

You can also add it to the menu by right clicking the application menu to bring up the editor.  Adding a new entry in the games submenu should be straightforward. You can drag and drop the icon from your file browser to the menu editor too.

As far as the other "whole bunch" of Linux games you've downloaded, it depends on what they've given you, if it's a zipped file, an executable installer like .sh or .bin, or a package like .deb or .rpm. 
Rule of thumb is, first search in Software Center, if not there see if there's a .deb.I'm obviously wasting my time. I'VE DONE EVERYTHING YOU JUST TOLD ME AND IT SHOWED NO MUPEN, NO NEW WINDOW, NOT EVEN AN ERROR!!!!!!!!!!

---

### Post by howefield on 2010-01-05
> **kinkinkijkin said:**
> I'm obviously wasting my time. I'VE DONE EVERYTHING YOU JUST TOLD ME AND IT SHOWED NO MUPEN, NO NEW WINDOW, NOT EVEN AN ERROR!!!!!!!!!!

Why are you screaming at someone trying to help you ?

---

### Post by mocoloco on 2010-01-05
Patience my son.  I'm guessing you're coming from a Windows background.  Even in Windows however sometimes applications are distributed in a zip file.  If you've ever dealt with that this is the same idea.  If you haven't then you've got a lot to learn about computing in general, and SCREAMING IN CAPS doesn't magically make you learn any faster.

Maybe you've downloaded something different than what I did.  I went to [http://mupen64.emulation64.com/down.htm]("http://mupen64.emulation64.com/down.htm") and clicked the link for "Mupen64 0.5 for Linux".

Start with that and try again.

---

### Post by kinkinkijkin on 2010-01-05
That link was helpful. the only bit of help that came at the right time in the last 3 months.

---

### Post by kinkinkijkin on 2010-01-05
Still not working. Does the 10GB installation have any extra security settings that block any programs not downloaded on that Ubuntu download channel-thingy? (Ubuntu version: 9.10)

---

### Post by mocoloco on 2010-01-05
Before I answer I need to say something.  You need to chill.  Comments like "the only bit of help in the last 3 month" etc etc aren't beneficial to anyone.  I realize it can be frustrating when things don't work as you expect, but take the time to learn instead of getting mad because they don't do what you think they should.
From the way you've phrased things I can tell you're not only new to Ubuntu but to many computing concepts in general. That's ok. But if you don't understand someone's instructions that's not my fault or anyone else's in these forums, it's up to you to learn. I'm not talking about learning advanced programming or anything, but knowing basics of managing files and such is essential.  

Take 30 seconds to read through [this page]("http://mwm.us.mensa.org/carcomps.html"). If any of that made you laugh, know that you may sound like those people when you say things like "that Ubuntu download channel-thingy"  No offense intended, it's just that the isn't completely clear and I'll have to try to guess at what you really mean. :P

So let me take a stab.  No matter what size partition you use when you install (I guess yours is 10 GB) there is no restriction on files you can download.
What happens when you click on the download link for Mupen64 for linux?  [Here's a direct link to the download file]("http://mupen64.emulation64.com/files/0.5/mupen64-0.5.tar.bz2") if you want to try again.  It should ask if you want to save the file, which you should do.

---

### Post by kinkinkijkin on 2010-01-05
> **mocoloco said:**
> .***[SIZE=4]From the way you've phrased things I can tell you're not only new to Ubuntu but to many computing concepts in general[/SIZE]***.I'm not new to computers... just linux in general.

---

### Post by kinkinkijkin on 2010-01-05
Is it my architecture not letting me access the programs? I use an i386.

---

### Post by mocoloco on 2010-01-05
Nope, architecture doesn't matter.  You have yet to answer my basic question, which is why I can't really help you. The question was, what happens when you try to download the link?  Specifically?

---

### Post by kinkinkijkin on 2010-01-06
It downloads the file. A litlle more info might help. I use an acer Aspire 4315, with an Intel Celeron processor of 1.86Gh/z in Ubuntu Karmic, 433Mh/z in Windows Vista and 1.87Gh/z in CMOS computer launcher. More details on processor: 540@1.87Gh/z. RAM: 690MB. VRAM: 500MB. Here's something you need to be a super nerd to understand or find out well: In windows, being it restrictive of my CPU power to less than a quarter, I can use only 3 programming code types at the same time. Linux (ALL OF IT), somewhere around 70. Other stuff (not in english):
Qerwtug pfoe nuhtyukc polnikad<zidelporph cruppa kreip| zoodel pone
Other stuff (in english):
My computer uses OpenGL 1.5.(I don't know) and is compatible with most windows and some windows clone. My computer is compatible with DOS, but I've been given reccomenations never to use it on this computer. My computer has a graphics processor to go with the graphics card, but the graphics processor is slower than a B-ie1r4 flattis graphics processor, which is on the list of the slowest. Though the card is fast, the graphics processor being slow makes my graphics slow.

---

### Post by mocoloco on 2010-01-06
> **kinkinkijkin said:**
> It downloads the file. 

OK, so the file is downloaded. Now just go through the rest of the steps I mentioned in my first post.  If you get stuck on any of them explain how.  Here they are again to make it clear.

[LIST=1]
[*]Go to where you downloaded it (usually in your "Downloads" folder)
[*]Right-click on the file called mupen64-0.5.tar.bz and click "extract here"
[*]That will create a new folder called mupen64, double-click on that folder
[*]Double-click on the executable file called mupen64, which will look like a diamond with gears in it. (it does NOT end with .exe)
[/LIST]

---

### Post by kinkinkijkin on 2010-01-11
Solved while looking for my glasses. It was an improper shutdown, which is also why I cannot update anything. I just need to re-install Ubuntu.

---

### Post by fancypiper on 2010-01-11
fsck should fix an improper shutdown.

---

### Post by kinkinkijkin on 2010-01-11
No, I'll fix it myself with re-installation.

---

### Post by kinkinkijkin on 2010-01-23
Now it's happening in XUBUNTU!

---

### Post by kinkinkijkin on 2010-03-20
I recently found my problem. I'm not linux compatible.

---

### Post by kinkinkijkin on 2010-05-12
I now know the exact reasoning. It's the site where I downloaded the stuff. Zophar's Domain is un-reliable for Ubuntu, Xubuntu and Kubuntu.

---

