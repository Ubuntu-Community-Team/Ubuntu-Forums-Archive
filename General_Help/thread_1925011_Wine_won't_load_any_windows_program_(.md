---
title: "Wine won't load any windows program :("
date: 2012-02-13
forum: General Help
---

### Post by nasroo7 on 2012-02-13
Hello everyone! 

   I've been visiting this forum few times and found answers many time!
But last week I installed Lubuntu on an old Laptop, because (In this forum) people said that it was a good one for old computers, as it doesn't require a lot of performance.
But after I tried to run Windows softwares, I couldn't... [ Installed wine 1.2, and all the dependencies that the software manager asked me for... but kept having the error: Desktop2-Gnome is missing... even after installing it... ]

So, I just gave up, and reformatted the HDD, and installed Ubuntu 11.10.
(Because I found more threads about Ubuntu that Lubuntu... I assumed it would be easier for me to start with it)

Now, here is my problem:
 I installed all the 362 updates required.
 I installed Wine from the "Ubuntu Software Center"
I typed "Wine" in the research bar, and installed "Wine windows program loader (wine 1.2)"

install successful, and then I went in the Terminal and wrote "winecfg" (as said in this forum, to solve the error user/home/??something...  folder missing)
It did it successfully!

I checked "Allow executing files as program" in permission (as said in this forum, to solve the error "is not marked for execution")

I selected "Open with : Wine > set as default" (as said in this forum also! :D I came many times here before I registered =P )

but now... When I execute it, there is an icon that pops up on the left task-bar "Wine windows program loader" ... stays here for 5 seconds, and then disappear... and nothing happens!

I'm trying to install Windows Live Messenger, that I downloaded from here : [http://www.microsoft.com/download/en/details.aspx?id=26685](http://www.microsoft.com/download/en/details.aspx?id=26685)

It's the first windows software I'm trying to install...

Does anybody have an idea?

Every single post I find about "Wine won't work" or similar, is because of errors mentioned on the top, that I already solved... 

I need your help! 
Thank you in advance

PS: I'm NOT kind of new users that post to ask for help, and never reply back! (I hate that!)

---

### Post by HiImTye on 2012-02-13
wine programs are best run using the command line (usually shell scripts)

if you want to use MSN then install aMSN
```
sudo apt-get install amsn
```
or for just messaging use Empathy. Empathy has problems connecting to MSN with the default setup sometimes, if it does then remove the butterfly
```
sudo apt-get remove telepathy-butterfly
```
but if it works as is then no need to mess with it

if you want to know how to launch a file with WINE then here is an example:
```
WINEPREFIX='/home/<yourusername>/.wine/<Program Name>/' wine "<Drive Letter>:\<path>\<file>.exe"
```
make sure you configure your drives in winecfg for each prefix (or just use C: if you dont want the hassle).

---

### Post by nasroo7 on 2012-02-13
THank's for the quick reply :D

is aMSN a different software that is compatible with MSN ? or the same ?

---

### Post by HiImTye on 2012-02-13
its an MSN clone. it seems to work best for features like webcam and whatnot

and also it has the same familiar MSN interface

---

### Post by nasroo7 on 2012-02-14
Thank's ! :D

So I finally installed aMSN, and it works good.

I will try the Terminal next time then

Thank you for your help!

---

