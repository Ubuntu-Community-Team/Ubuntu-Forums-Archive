---
title: "how to install downloads"
date: 2011-03-09
forum: General Help
---

### Post by btf18 on 2011-03-09
Hey all,

tbh i understand the terminal more than the GUI xP I want to know how to download something from the internet. I just downloaded firefox 4 BETA from the mozilla site. Now i want to install and run it. When i click download it says "what should firefox do with this file? and i have the option to open with archive manager or save. I open with archive manager as this has worked for me before but i can't remeber how. Then it downloads, and shows it downloading in a box called downloads. then a folder called firefox-4.Orc1tar-1.bz2 [read only] opens and within that is another directory called "firefox", and within that is numerous other directories such as components, dictionaries etc etc etc. nothing says install. They mainly contain read only files. How do i install and use? plz help xP

Thanks

---

### Post by lithopsian on 2011-03-09
The directory contains a binary called firefox.  Run that after you've extracted the tarball somewhere.  I suggest into /opt.

---

### Post by wiggly81 on 2011-03-09
i have just downloaded firefox 4 to see if i can offer some help and i think maybe i can extract the firefox folder from the archive then cd to the folder
```
cd Downloads/firefox
```
then run firefox lik this worked for me 
```
./firefox
```


hope this is of some help

---

### Post by btf18 on 2011-03-09
Thanks guys. I seem to have got it working. I just dont think i understand the process though, if i wanted to download something else from a random website and do it again. Basically all i did then was go to the directory wiggly gave me in the terminal and typed the code and it worked. Im sure you do have to do some extraction before this step, but i had already mucked around with it a lot and extracted it even though i didnt know what i was doing. I fear i will have to ask on hear again next time i want to download something. If anyone has time enough to explain the process of downloading a file to a noobie like me, that would be great. So i always choose open with archive manager, then maybe right click the directory and click extract and that will cause the directory to show up in my downloads folder? then once its there i can locate it in the terminal and type a command to open it? (what will the command be with the next random thing i decide to download?) And im not sure what extracting really is. I just know to do it. I didnt really understand lilthopsian as im not sure what tarball is, and the code at the end, is that a command for the terminal?

---

### Post by wiggly81 on 2011-03-09
firefox 4 that you downloaded does not need to be installed to run.
other applications that you download could need to be installed via terminal commands this could include having to find and install dependencies for the application so the long and short is this is not always the way things work but 99% of the time there will be a file in the archive that explains how to install which could include things like
```
./configure
make
make install

```

again this is not always the way its done so its always a good idea to read any documentation included that will explain the process or if you do have a particular application you need to install and cant figure it out come back here im sure one of the many helpful people will be only too happy to help you

---

### Post by leeshaub on 2011-03-09
I just tried but the one thing is firefox-bin then i tried to run it and it opens in firefox??

---

### Post by leef on 2011-03-09
> **leeshaub said:**
> I just tried but the one thing is firefox-bin then i tried to run it and it opens in firefox??

Well it is firefox, so of course it will open firefox?

---

### Post by wojox on 2011-03-09
Don't open it with Archive Manager, just save it. In a terminal run

```
tar xjf firefox-*.tar.bz2
```

The installation file provided by Mozilla in .tar.bz2 format does not contain sources but pre-compiled binary files, therefore you can simply unpack and run them. There is no need to compile.

---

### Post by lithopsian on 2011-03-09
Installing in Linux is not a magical event, hidden from the prying eyes of the unworthy as it is in Windows.  Installing is just placing program files in a certain place, and perhaps adding some configuration files elsewhere.  You could do that manually but usually you don't.

For Firefox, it is as simple as placing all the files that come into one place.  The first time you run Firefox, it will create some configuration files in your home directory.  A tarball is just a Linux way to bundle up a whole bunch of files arranged in directories into a single file to make it easier to download.  /opt is a location on your hard drive.

Other programs may have more complicated arrangements.  They may even need to be compiled in a way that matches your system.  This is often controlled using makefiles.  The make command does this for you, and will usually also install everything in the correct place afterwards.

Linux has special ways of bundling programs into packages.  These include all the files that need to be installed, but also instructions about what other packages need to be installed first, and exactly which versions.   In Ubuntu these are deb files.  Most of them are stored on websites called repositories and can be downloaded and installed all in one step using the package manager or certain commands like apt-get.  These are regularly updated and these updates can be detected automatically and applied.  You can also download your own to get special versions, and these are installed using the dpkg command.

---

### Post by btf18 on 2011-03-09
Thanks guys. Im having a hard time understanding that xP maybe if i read it 100 times i will have knowledge of such things xP I just coded ps and saw firefox running and didnt think firefox should need to be a running process as its never been before so kill -9ed it xD now its back to the old version of firefox when i click the desktop icon. And even when i type the code wiggly suggested that first worked for me. Im gonna try some stuff in the gui i guess as ive tried the other codes suggested on here to no avail. From what lith said, i just need the program files to be in my hard drive. Im sure they are though. I'll try a restart xP



I just redid everything and typed the code at the top of the thread that wiggly suggested and it now just opens the old firefox :-S

---

### Post by leeshaub on 2011-03-09
it opens *in* firefox not opens firefox and there is a file named firefox then it asks do you want to run in terminal or run 
lee

---

### Post by oldos2er on 2011-03-09
> **btf18 said:**
> I just redid everything and typed the code at the top of the thread that wiggly suggested and it now just opens the old firefox :-S

To run the new Firefox, you would need to specify the absolute path to firefox, e.g. /home/user/Downloads/firefox/firefox. Otherwise you'll get the version of Firefox that was installed with Ubuntu.

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885) (this link is old, but the information is still relevant).

---

### Post by btf18 on 2011-03-10
I think i understand now. I downloaded it again, and then extracted the tarball, then opened the directory and double clicked on the binary file called simply "firefox" and the could either view or run and i clicked run, and it open the web browser. Is this how it should work? One problem...The web browser it runs is version 3.6. I really dont care as im not doing it to have the new firefox, im doing it to learn, and as long as i have the right idea that is all i want. I believe this is the correct way, and the fact that its version 3.6, is not due to the way im doing it. Something has mucked up along the way but the binary file "firefox" is inside the firefox-4 folder i just downloaded so i did good yeah? xP

---

