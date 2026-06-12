---
title: "How to run clipgrab?"
date: 2012-09-17
forum: General Help
---

### Post by rjshen43 on 2012-09-17
Hello:
I just upgraded to ubuntu 12.04 from 10.10.  I'm trying to install clipgrab 3.2.0.9. I extracted clipgrab-3.2.0.9.bz2. in a folder called clipgrab.  It gives me one extracted file, "clipgrab-3.2.0.9."  What do i do to get clipgrab to run?  When I click on it I get, Could not open "clipgrab-3.2.0.9" Archive type not supported.

I take it something else has to be done.  Another version of clipgrab worked in ubuntu 10.10 by clicking in the exracted clipgrab file.

I downloaded clipgrab via PPA but that version would run but would not download any clips.  When I launched clipgrab from PPA it directed me to another web site where I downloaded ver 3.2.0.9.  Now I don't know how to install it.

Thanks alot for any info on this matter. :)

---

### Post by critin on 2012-09-17
Go back to the site where you got the ppa (where is this?)  and look for instructions.  I've searched and can't find a version for ubuntu (linux)

---

### Post by critin on 2012-09-17
Okay, I found the download for linux.  Is this what you used?

[http://clipgrab.de/en](http://clipgrab.de/en)

Did you extract r just try to install first?  You'll need to extract, I extracted in my download page, (but I'm not going to install.)

The archive manager will need to search and install the** proper apps to run exe apps**.  I would choose whatever it recommends, but if you know, you can choose what you think best for you.

After its done it should work.

---

### Post by AndyOpie150 on 2012-09-17
I just researched for a similar problem, so I downloaded clipgrab-3.2.0.9.bz2. Moved it to the home folder and extracted. Left it in the home folder and right clicked on the .exe and chose properties. Clicked on permissions, then clicked on the box to allow executing the file as  a program. Clicked out and then double clicked on the .exe and it opened up the program. Looks like an interesting program.

---

### Post by rjshen43 on 2012-09-17
Andy:
Thanks for the quick replies everyone.

I did exactly what you did, marked it executable, Set all permissions to read and write, but when I double click it nothing happens, not even a flicker.  Buy the way I'm using gnome (classic) in ubuntu 12.04 would that make a difference?  I don't know what else to do..... :(

---

### Post by AndyOpie150 on 2012-09-17
I'm on Gnome classic myself (to many hassles with Unity). I just clicked on the Exacute box, I didn't change any of the permissions.

I do have Wine installed, but I don't know if that is what is making the difference or not.

---

### Post by rjshen43 on 2012-09-17
OK...I haven't installed wine yet, when I do I'll get back to you,Thanks

---

### Post by rjshen43 on 2012-09-17
I installed wine and still no difference??????

---

### Post by AndyOpie150 on 2012-09-17
Did you try rebooting and then checking with the Update Manager for any Updates, I just got an update for Wine. I would download a fresh clipgrab-3.2.0.9.bz2

Once downloaded I extracted the .exe and moved it to the Home folder. I did not put it into any other folder. 

Let me see if I can remember where I got the version I downloaded from.

---

### Post by AndyOpie150 on 2012-09-17
OK try downloading the .exe from here: [http://clipgrab.de/](http://clipgrab.de/)

If you don't have google translate then just click on the baby blue download box.

You might: sudo apt-get remove --purge the other version first.

---

### Post by ImNotSteven on 2012-09-20
I'm having similar issues with Clipgrab.

It wasn't doing anything when I'd double-click on it even after allowing it to open as an executable file.

To find out what the problem was, in Terminal, I navigated to the folder where Clibgrab was located and did:
```
./clipgrab-3.2.0.9

```

That returned the following error:
[HTML]error while loading shared libraries: libQtWebKit.so.4: cannot open shared object file: No such file or directory[/HTML]

After searching, I've found that some users were able to fix this by installing qtwebkit, but I don't know how I'd go about installing that in 12.10.

Edit: OK, so I figured out that what I needed was libqtwebkit4, however I still get the same error when trying to run Clipgrab. So, what is the issue here? Since it's already installed, is the installer just unable to locate libQtWebKit.so.4?

---

### Post by ImNotSteven on 2012-09-20
Yay! I got it working. :p

I had to install it from the source code. For anyone who doesn't know how to do that:

First, make sure you have both libqtwebkit4 and qt4-dev-tools installed.

In Terminal:
```
sudo apt-get install libqtwebkit4 qt4-dev-tools
```

Then, download the source code here: [http://clipgrab.de/download/clipgrab-3.2.0.9.tar.bz2]("http://clipgrab.de/download/clipgrab-3.2.0.9.tar.bz2") into your home folder.

Then, unpack it:
```
tar -xvf clipgrab-3.2.0.9.tar.bz2
```

And navigate to that folder in Terminal:
```
cd /home/**your username here**/clipgrab-3.2.0.9
```

Now, you can install it with: 
```
qmake clipgrab.pro && make
```

Almost done. When that finishes, make it executable:
```
chmod +x clipgrab
```

Next, open up the Main Menu application. Click on "Sound and Video" on the list and then on the "+New Item" button. Name it "Clipgrab" and for "Command", choose "Browse" and select the "clipgrab" file from your "clipgrab-3.2.0.9" folder.

Now, you can start Clipgrab as you would any other app in Unity or whatever you use. :)

---

### Post by JWACKED on 2012-09-21
Hi, just got following all the instruction on how to make clip grab run in my Ubuntu system, read all the comments, no luck. Needs some serious help here, this is annoying the "!!!!!!' out of me. This is a good program that expired on me this week and so far.........NO LUCK. I have Ubuntu 12.4, any suggestions would be deeply appreciated.

Thank You

---

### Post by anies2 on 2013-08-08
Hi, here is what I did to get it running on ubuntu 13.04:

download clipgrab-3.2.0.11.tar.bz2 from [http://clipgrab.de/download/](http://clipgrab.de/download/) and extract it.

install theese libraries:

```
sudo apt-get install build-essential libqtwebkit4 qt4-dev-tools ffmpeg lame libavcodec-extra-53
```

then follow the instructions in the README to compile and run the programm.

---

