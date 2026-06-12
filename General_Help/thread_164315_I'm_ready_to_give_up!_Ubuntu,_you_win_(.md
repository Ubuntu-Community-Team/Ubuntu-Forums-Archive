---
title: "I'm ready to give up! Ubuntu, you win :("
date: 2006-04-22
forum: General Help
---

### Post by Binny45 on 2006-04-22
Howdy folks

I've been trying, and trying, and trying and trying, to get Ubuntu working, at least to the best of my abilities (Ubuntu and Linux newb here).

I've tried 64 bit, I've tried 32 bit and I keep getting the same error each time.  It's to do with the X Server, and how my graphical interface can't load due to an error.

Everything installs fine (or seems to anyways), but then when I load up the OS, I get a blue screen with all these weird characters around with the X Server error.

My system is as follows:

AMD Athlon 64 S939 3500+
2GB Geil DDR400 RAM
Western Digital 250GB SATAII 16 MB cache hard drive
Sapphire ATI X800 GTO Fireblade edition 256MB Graphics card
ASUS A8N-E Motherboard
480W Antec Neo-Power P/S

Folks, I REALLY want to see what this has to offer.  I had a taste of it at work, however I've had nothing but grief trying to get this working at home.  The live CD's don't work, the install CD's don't work.  Not just the 64 bit, but the 32 bit as well.  I really don't know what else to do.

---

### Post by Face1 on 2006-04-22
Could you be more specific about what the error says, please?

---

### Post by Binny45 on 2006-04-22
It's something along the lines of my X Server didn't load right, therefore my GDM (whatever that is) won't load.  It asks me if I want to see all the information on X Server, but it's all greek to me.  It tells me to go to wiki.x.org if I have any questions, but all that place seems to do is create more than get answered. ](*,)

---

### Post by IYY on 2006-04-22
Don't worry about not understanding the error message, this is what we're here for, so tell us the message in more detail.

But most likely you'll need to reconfigure Xorg, and select a different driver.

To do this, run:

sudo dpkg-reconfigure xserver-xorg

Also, try changing your driver to vesa or vga (the ATI drivers are very often the cause of the problem).

---

### Post by Binny45 on 2006-04-22
Is there a way I can screen shot the error so I can copy/paste it here?  I'd love to tell you what the error is exactly, but I might as well be speaking Japanese (Boy I wish I could speak Japanese!).  If you have any questions about anything in the error screen, please feel free to ask, I'll gladly keep rebooting until you have the info you require.

---

### Post by IYY on 2006-04-22
Ok... How about you just try replacing the driver (it works often enough).

Get to a command line (if you're not in one already, Ctrl+Alt+F1). After logging in type:

sudo nano /etc/X11/xorg.conf

Type your password, enter, and then find the line

```
Driver "ati"
```

and change it to

```
Driver "vesa"
```

Then save and restart.

---

### Post by Binny45 on 2006-04-22
IT WORKED! THANK YOU THANK YOU!

I'm actually posting this inside Ubuntu :)

I guess from here it's now working on getting some of my programs over.

Now that this is up and running, is there a way to get my video card drivers (ones that will work with Ubuntu)?  Main reason being is for installing WINE so I can play World of Warcraft hehe.

I guess that brings me to my next question:

Where do I get WINE and how do I install it?

Wow, to be a newb again, it's kinda refreshing :)

---

### Post by Dr Gonzo on 2006-04-22
Here's the [Wine homepage.](http://www.winehq.org/)

Ubuntu also comes with Wine in the repositories, so you could install it using Synaptic, although you're likely better off if you get the latest and greatest version.  There'll be fewer bugs running WOW.

As for your video card, there's lots of people on here who've gotten ATI cards to work correctly.  Try a search.  I'd help, but I'm an nVidia guy...

---

### Post by Binny45 on 2006-04-22
Wow! Found Wine and am installing it as we speak.  Thanks guys!

I was wondering, for someone like myself (who's head is full of microsoft crap) who wants to start from the ground up and truly get head and eyes into Ubuntu and eventually Linux in general, is there a guide out there that you would recommend I pick up?

Something that will introduce me to the terminology, how the OS works and basically show me how the guts of it works.  I do appreciate you guys helping, however I feel guilty coming here everytime I can't do something that I would assume is fairly simple. :)

---

### Post by Dr Gonzo on 2006-04-22
No need at all to feel guilty. :D

The one thing I would suggest would be to make extensive use of the search feature of the forums.  In my time here, I've discovered that most problems have been encountered by someone before me, and often, solutions are offered.  There's also lots of good information on the ubuntu wiki.

As far as basics, there are tons of books out there.  But, the new version of Ubuntu, Dapper Drake, has many upgrades to the help system.  Most of what you need to understand is in there.

---

### Post by z_diver on 2006-04-22
[QUOTE=Dr Gonzo]the new version of Ubuntu, Dapper Drake, has many upgrades to the help system.  Most of what you need to understand is in there.[/QUOTE]
I second that.  

I went through Yelp last night and although the search feature doesn't seem to work(yet), and you have to press [COLOR="Red"]F1 twice[/COLOR] to start it, I can't recalll ever coming accross better written documentation for linux(or any other OS).  So if you are using Dapper, by all means, start there!  And if not, you might consider upgrading to Dapper -- yeah, Yelp 2.14 is that good.  It's going to end up saving people a LOT of UbuntuForums searches.  :D

Edit: Breezy's yelp is not something that can be used as a measuring stick.  Dapper's is 10+ times better.

---

### Post by graigsmith on 2006-04-22
> I was wondering, for someone like myself (who's head is full of microsoft crap) who wants to start from the ground up and truly get head and eyes into Ubuntu and eventually Linux in general, is there a guide out there that you would recommend I pick up?

i think the best thing i did, was just to start playing with things.  if you don't like something try to figure out how to make it better. ask questions on this forum, this forum made it possible for me to become a linux user.  a year ago i used windows.  And this forum helped me tackle every problem i have run into.

---

### Post by AndyCooll on 2006-04-22
The nearest starter guide for Ubuntu that I can think of is this:
[Unofficial Ubuntu 5.04 Starter Guide]("http://ubuntuguide.org/")

Of a more general nature these might be of interest:
[Linux Knowledge Base and Tutorial]("http://www.linux-tutorial.info/index.php")

[linuxnewbieguide.org]("http://www.linuxnewbieguide.org/")

:cool:

---

### Post by DE Retiree on 2006-04-22
I am also a newbie to linux and ubuntu - about one month of experience.  I found the book "Beginning Ubuntu Linux" by Keir Thomas (I got from Amazon.com) extremely helpful as well as searching this forum for info.  The book was worth every penny in my opinion.  Saved me hours of wasted time.  And, the folks on this forum are wonderful.

Best regards in learning.  

DE Retiree

---

### Post by dralaroc on 2006-04-22
Hey Benny,

That screen that you are talking about.  I have seen that thing numerous times.  Each time it popped up I would do a new install, because I did not know how to get out of it, I know silly me.  I found out about "sudo dpkg-reconfigure xserver-xorg"  &  "startx" just yesterday!!  I have been playing with Ubuntu for two months now.  Anyway, hang in there man this os is truly a nice piece of work.  I am running Dapper Beta now and its running like a champ.  Fwiw what I did was copy & paste every script,cmd,forum thread # etc. that I thought that I would need/use at a later time and sure nuff, I still use alot of it and saved my butt a bunch of times.

---

### Post by DonS on 2006-04-24
[QUOTE=z_diver]I second that.  

I went through Yelp last night and although the search feature doesn't seem to work(yet), and you have to press [COLOR="Red"]F1 twice[/COLOR] to start it, I can't recalll ever coming accross better written documentation for linux(or any other OS).  So if you are using Dapper, by all means, start there!  And if not, you might consider upgrading to Dapper -- yeah, Yelp 2.14 is that good.  It's going to end up saving people a LOT of UbuntuForums searches.  :D

Edit: Breezy's yelp is not something that can be used as a measuring stick.  Dapper's is 10+ times better.[/QUOTE]

The pressing F1 twice thing: Are you sure?  Yelp does take a long time to load the first time its run (Don't blame us, its really firefox's fault).  If it really doesn't load on pressing F1 once, please file a bug in Malone.

The search bit: Are you running beagle?  If so, theres a couple of bugs with yelp / beagle integration in Dapper:
[https://launchpad.net/distros/ubuntu/+source/yelp/+bug/39458](https://launchpad.net/distros/ubuntu/+source/yelp/+bug/39458)
Try stopping beagle and you'll fall back to using the "basic" search.

---

### Post by jpkotta on 2006-04-30
[QUOTE=graigsmith]i think the best thing i did, was just to start playing with things.  if you don't like something try to figure out how to make it better. ask questions on this forum, this forum made it possible for me to become a linux user.  a year ago i used windows.  And this forum helped me tackle every problem i have run into.[/QUOTE]

That's exactly the best way to learn.  

Here are some more online guides that focus more on the CLI and Linux in general (i.e. not just Ubuntu):
[http://linux-newbie.sunsite.dk/index.html](http://linux-newbie.sunsite.dk/index.html)
[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)

---

### Post by blackjack6.21.91 on 2006-04-30
try ubuntuguide.org

it's a real help, as is the ubuntu wiki

wiki.ubuntu.com

and thanks for being patient with ubuntu!

once you get everything down it really is a fantastic OS!!

blackjack

---

