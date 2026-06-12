---
title: "Ubuntu &amp; Yahoo messenger"
date: 2011-03-23
forum: General Help
---

### Post by J_Wales on 2011-03-23
I realize that yahoo messenger does not work with Linux, not an updated version anyway. I've messed around with Gyachi but its such a cluster imo. The layout is geared towards chat rooms which isn't what i need it for. I tested it out with my windows laptop and I couldn't connect a voice chat easily, it seems too buggy. It wouldn't receive or send voice calls and I couldn't even find a setup for the voice chat options.

anyway
Are there any alternative yahoo clients? What about running yahoo in a virtualbox? or something similar? I need it to communicate with family overseas. So yahoo voice chat and webcam are a must...

unfortunately this could be a deal breaker for me so i'm hoping some people have been through this and know of either some alternatives that work with yahoo chat client supporting the basic webcam and voice chat calls, or running yahoo in other ways.

i'm running ubuntu 10.10 and i have vb ose installed

---

### Post by mastablasta on 2011-03-23
> **J_Wales said:**
> I realize that yahoo messenger does not work with Linux, not an updated version anyway. I've messed around with Gyachi but its such a cluster imo. The layout is geared towards chat rooms which isn't what i need it for. I tested it out with my windows laptop and I couldn't connect a voice chat easily, it seems too buggy. It wouldn't receive or send voice calls and I couldn't even find a setup for the voice chat options.

 
There are two version of Gyache. One is quite old and one more current.
Have a look here:
[http://sourceforge.net/projects/gyachi/](http://sourceforge.net/projects/gyachi/)
 
Now at version 1.2.6
 
But browse through files and you can see 1.2.10 verison also available.
 
> 
anyway
Are there any alternative yahoo clients? What about running yahoo in a virtualbox? or something similar? I need it to communicate with family overseas. So yahoo voice chat and webcam are a must...

 
best compatibility of other messanger with yahoo seems to be with Pidgin, but i don't know about video and voice as i haven't tested it yet. But in other things it ismuch more compatible than empathy.
 
Skype offers web/voice chat. though linux verison is quite old and doesn't support conference calls it works OK in one on one video and voice chat.
 
I use it for phone calls as well. wish my overseas family would have a good internet connection so we could do video as well.
 
 
EDIT: I found even easier to install Gyache-the PPA: [https://launchpad.net/~loell/+archive/ppa](https://launchpad.net/~loell/+archive/ppa)

---

### Post by Lars Noodén on 2011-03-23
+1 for pidgin

---

### Post by Sef on 2011-03-23
>  I need it to communicate with family overseas. So yahoo voice chat and webcam are a must...

The default empathy has voice and video, but I do not know how well they work.

---

### Post by Script Warlock on 2011-03-23
if only you can replace ym for Skype, i have tested ym inside vbox 4 on my laptop slow but usable voice and video is working but because i have a limited system resources i remove and use instead empathy for my gtalk friends and Skype for my family.

---

### Post by J_Wales on 2011-03-23
My gyachi version is 1.2.10, so i will download the latest and check it out.

I  would be happy with it, if it was a simple chat client that just worked  with the yahoo chat client and basic voip and cam features. It is  geared towards chat rooms and has a really wide terribly laid out  interface. What happen to sleek and simple.

Anyway, if it wasn't  for the complication of making it simple for the wife to use and  compatible for all her relatives this wouldn't be a problem. But as it  is, it has to work with yahoo and it has to be simple. Having to start a  conference chat room and invite people to it is a pain. The interface  is to confusing for her, what would appear to make sense does not lol.  I'm really kind of surprised so many people use it, but i guess when  your choice is ym or no ym...

---

### Post by J_Wales on 2011-03-23
I downloaded it, and now I can't figure out how to install it. I unziped it to downloads, opened the directory up in cmdprompt typed ./configure and it spit back "read install.txt"
I tried to run make, it wouldn't work. The install.txt says to do the same 
./configure
make
make install


any ideas?

---

### Post by J_Wales on 2011-03-25
I know its a stupid simple question, but I don't really know much about linux. I read through the install.txt for gyachi 1.2.7 and I did what it said './configure' and it just says 'read install.txt' running 'make' and 'make install' after does nothing but error. Is there a way to get some kind of error message or report of why it didn't configure the package, i'm assuming that is the problem? or could someone tell me what i'm doing wrong?

---

### Post by jcris on 2011-03-25
[http://geny.sourceforge.net/](http://geny.sourceforge.net/)

the updated MeeGo version, cams actually come in crystal clear, and it logs into the Yahoo! servers pretty damn fast. All the features of Yahoo! messenger aside from Voice has not yet been added.

---

### Post by J_Wales on 2011-03-25
I'll check it out for the sake of curiosity. One other option I could maybe do, is find a simple voice/cam program that has a linux and windows release.

---

### Post by J_Wales on 2011-03-25
I found a better option for me. Google has a voice/video feature in igoogle or googlemail that is stupid simple and if you have a browser it basically works as far as i can see. The only problem I am having is my mic. I found out it is not working... I do not know what the problem is or how to even find out.

---

### Post by RingingMaster on 2011-03-25
I have downloaded the MeeGo file so it is in my downloads folder
~./Downloads/geny-0.1.3-meego.tar.bz2
so what do I do next to get it installed?

---

### Post by tech7 on 2011-03-25
+1 pidgin for me, as well.  I believe you can find all the plugins that you could imagine ever needing in the software center.  I believe I have used pidgin for what your looking for, as well.

---

### Post by RingingMaster on 2011-03-25
What I am looking for is to chat and webcam with my friends in an IM program. Have installed several of them - empathy, Pidgin, Kopete, Gyache -  can chat with Yahoo friends in all of them. What I have been unable to do is to get my webcam working with them. The webcam on the computer works just fine. The problem is being able to chat and cam at the same time with my friends on Yahoo. Gyache looks the most promising, but now it is so late all my friends have gone to bed - no-one to test it on until tomorrow.

---

### Post by J_Wales on 2011-03-26
fixed my mic, yay!

gyachi runs my cam fine. I didn't have any issues with that, just the ugly interface. I still can't believe it. Anyway, if you like chatting, i'd go with gyachi its definitely chat oriented. I'd post something about your cam problem to launchpad. It is pretty helpful, first go through the [https://help.ubuntu.com/](https://help.ubuntu.com/) pages. You'd be surprised how much is really in there.

---

### Post by J_Wales on 2011-03-26
Thanks everyone for the suggestions, I really appreciate all the time and help.

---

### Post by RingingMaster on 2011-03-26
Finally got Gyachi working with webcam in Yahoo

sudo apt-get build-essential
sudo add-apt-repository ppa:adilson/experimental
sudo apt-get update
sudo apt-get update  (did it again to clear some errors)
sudo apt-get install gyachi

now go to menu on panel
Applications/Internet/GYache Improved

Add your buddies in the buddies list

Now the key part which I missed before....
In Gyachi use the menu....
Actions / Start My Webcam

the first time I did this I got errors,
the webcam started working but there was an error message, something about 'unable to support capturing'
the solution to this was to close Gyachi, and then restart it

Have just tested this with one of my buddies - IT WORKS!

Its just a pity all the other IM clients can't work with webcam

---

### Post by ProNux on 2011-05-05
> **J_Wales said:**
> I realize that yahoo messenger does not work with Linux, not an updated version anyway. I've messed around with Gyachi but its such a cluster imo. The layout is geared towards chat rooms which isn't what i need it for. I tested it out with my windows laptop and I couldn't connect a voice chat easily, it seems too buggy. It wouldn't receive or send voice calls and I couldn't even find a setup for the voice chat options.

anyway
Are there any alternative yahoo clients? What about running yahoo in a virtualbox? or something similar? I need it to communicate with family overseas. So yahoo voice chat and webcam are a must...

unfortunately this could be a deal breaker for me so i'm hoping some people have been through this and know of either some alternatives that work with yahoo chat client supporting the basic webcam and voice chat calls, or running yahoo in other ways.

i'm running ubuntu 10.10 and i have vb ose installed
I have used Yahoo Messenger in a virtual box, works great for me, even thought I installed VB just for Yahoo. LOL

---

### Post by Randymanme on 2011-07-23
My problem plain and simple (so far):  My eyesight isn't as good as it used to be and Gyahci's fonts are too small for me to make out.  The color schemes on a black background make it worse.

Does any one know how I can make the fonts bigger?  Any help would be much appreciated.  Thanks.

---

### Post by Randymanme on 2011-07-23
[FONT=&quot]I did (on Katya)

sudo add-apt-repository ppa:adilson/experimental
sudo apt-get update
sudo apt-get install gyachi

but it wouldn't install.  I'd get the yes or no prompt, enter Y for yes, and it would abort.  After trying again several times, I went to synaptic package manager.  There i found 5 Gyachi 1.2.10 packages.  I installed all of them except the one with debugging symbols.  1.2.10 includes font tabs in set up.
[/FONT]
[FONT=&quot]
[/FONT]

---

### Post by xx58 on 2011-09-17
> **J_Wales said:**
> I realize that yahoo messenger does not work with Linux, not an updated version anyway. I've messed around with Gyachi but its such a cluster imo. The layout is geared towards chat rooms which isn't what i need it for. I tested it out with my windows laptop and I couldn't connect a voice chat easily, it seems too buggy. It wouldn't receive or send voice calls and I couldn't even find a setup for the voice chat options.

anyway
Are there any alternative yahoo clients? What about running yahoo in a virtualbox? or something similar? I need it to communicate with family overseas. So yahoo voice chat and webcam are a must...

unfortunately this could be a deal breaker for me so i'm hoping some people have been through this and know of either some alternatives that work with yahoo chat client supporting the basic webcam and voice chat calls, or running yahoo in other ways.

i'm running ubuntu 10.10 and i have vb ose installed

Gyachi works very well, but there no voice talk, only write option. Cam works very well too. I use different Gyachi at Ubuntu 8.10 and now have 11.04 Unity. Works like charm. 
Best choise for you are Skype, because there work all options, not different (much) at WINDOWS Skype options. There are Skype download option for Ubuntu, so go to [www.Skype.com](www.Skype.com) and download - option Linux.:rolleyes:

---

### Post by xx58 on 2011-09-17
> **J_Wales said:**
> I found a better option for me. Google has a voice/video feature in igoogle or googlemail that is stupid simple and if you have a browser it basically works as far as i can see. The only problem I am having is my mic. I found out it is not working... I do not know what the problem is or how to even find out.

Yes Googol Phone works well, but if you live outside USD, then need pay 3 USD cents per minute. Client in USD/Canada free on this year and I am very sure at next year it will cost for everybody. 
Skype still best free talking option.

---

