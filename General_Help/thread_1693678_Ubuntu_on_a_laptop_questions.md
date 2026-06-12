---
title: "Ubuntu on a laptop questions"
date: 2011-02-23
forum: General Help
---

### Post by rsmedude on 2011-02-23
Good Morning everyone,
 
I have a project I am about to do. I need to setup a laptop for at my model railroad club. The link to them is [http://www.rsme.org](http://www.rsme.org). I figured to help them avoid licence issues I would use Ubuntu. This laptop only needs to run one program and that program is the JMRI. Here is the link [http://jmri.sourceforge.net/](http://jmri.sourceforge.net/).
 
What we plan on doing is using a laptop hooked up to our train layout so that we can use our smart phones to run the layout. 
 
My questions now:
 
1. What are the diffrences between the diffrent flavors of Ubuntu?
2. Which flavor does the community think will work the best for my minimal requirements?
 
 
My Laptop:
IBM Think Pad T22
Pentium 3 900MHZ
256 MB Ram (Can be pushed up to 1GB)
NO WIRELESS (The laptop will be hardwired to a router on location)
 
I do not need this up and running till April so I do not have a super rush but I do need time to get familiar with everything. I will appriciate any and all help on this project.
 
Respectfully,
RSMEDUDE

---

### Post by nothingspecial on 2011-02-23
The different flavours of Ubuntu are merely a matter of the default apps they use, you can switch between them using the package manager or build your own custom ubuntu.

Lubuntu will run fine on your laptop but you may have a few issues running your software, maybe not.

The souceforge page of the software you would like to run says it works on Ubuntu but Ubuntu will not install with that little ram (it will run slowly but you need more ram for an easy install).

As you said you can up the ram to 1gig, I would do that and install Ubuntu.

If you don't mind the possibility of a little tinkering leave it as it is and install lubuntu

---

### Post by khelben1979 on 2011-02-23
I would recommend the latest version of Ubuntu if you upgrade the memory to 512 MB or 1 GB.

Otherwise go for a less memory hungry variant of Ubuntu or go for an older version than 10.10. [Different Ubuntu variants]("http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Variants").

---

### Post by mastablasta on 2011-02-23
does the porgramme need a GUI to run or is it someting that runs in command line? if no then you can easilly use Ubuntu.
 
still more ram is always better (at least 512 MB in this case).
 
Different flavours use different applications and desktop environments. Various desktop enviromnets handle things in a different way and also they diverse on how much system resources they need. they all use the same language in the terminal (command line interface).
 
i would say the easiest way is to download the one you like and make a liveCD of it and then just try it. see how it goes.
 
and add a bit of ram to the computer :-)

---

### Post by Bucky Ball on 2011-02-23
> **khelben1979 said:**
> I would recommend the latest version of Ubuntu if you upgrade the memory to 512 MB or 1 GB.

Otherwise go for a less memory hungry variant of Ubuntu or go for an older version than 10.10. [Different Ubuntu variants]("http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Variants").

Latest is least stable and this setup sounds like it needs to be rock solid (not broken by an errant update). Therefore 10.04 LTS is a better choice with longer support life. ;)

It wouldn't make much diff trying to run 10.04 LTS or 10.10 on this machine with current specs and any older than that will not have much support left (8.04 LTS, the last long term support release, runs out April of this year).

If it were me I would go the minimal install and just add a desktop and the software you want to use and need to use to run it and that's it. As pared back as you could get. But I have some idea what I'm doing ... 

Good luck with it, sounds like an interesting challenge.

---

### Post by nothingspecial on 2011-02-23
> **Bucky Ball said:**
> 

Good luck with it, sounds like an interesting challenge.

And when you get it set up can we all come to Reading for a ride on the trains? [-o<

---

### Post by khelben1979 on 2011-02-23
> **Bucky Ball said:**
> Latest is least stable and this setup sounds like it needs to be rock solid (not broken by an errant update). Therefore 10.04 LTS is a better choice with longer support life. ;)

I would disagree to some extent since 10.04 does not have all the latest hardware supported by the Linux kernel. Remember, he might be interested in connecting modern USB hardware to it (or how does that look like?).

> It wouldn't make much diff trying to run 10.04 LTS or 10.10 on this machine with current specs and any older than that will not have much support left (8.04 LTS, the last long term support release, runs out April of this year).

I would disagree here as well, because I have run Linux on older hardware than what he has, and I got no problems with it, other than it was "a bit slow". I do understand your reasoning though, because there are cheap hardware available which would make a lot more use than Ubuntu than what he has at the present, giving him a better experience.

> Good luck with it, sounds like an interesting challenge.

Agreed. :)

---

### Post by rsmedude on 2011-02-24
Hey guys,

Thanks for all the great info... I will be trying this all out this weekend and into next week! I will post results and let you all know how things go with this project!

---

### Post by rsmedude on 2011-02-25
Hey everyone,

I have a little problem... I am trying to install Ubuntu 10.10 on this system. Good news is it looks like it is going to work. Bad news is I can not get past the who you are part. I am just stumped as to what I am missing! 

Here is what I have stuff set as:

Your name: RSME (green check mark)
Your computer's name: DCC-SERVER (green check mark)
Pick a username: EXPLORER (no check mark)
Choose a password: Trains#01 (good password)
Confirm your password: Trains#01 (green check mark)
Require my password to log in selected


Any help I can get I would greatly appreciate!

---

### Post by rsmedude on 2011-02-25
> **nothingspecial said:**
> And when you get it set up can we all come to Reading for a ride on the trains? [-o<
 
Sorry I am slow in replying to everyone. 
 
As for your comment about comming to the Reading Area to ride the trains I would encourage it! :)

---

### Post by patchwork on 2011-02-25
A possible cause: 
The username must be all lowercase letters.

---

### Post by Bucky Ball on 2011-02-26
> **patchwork said:**
> A possible cause: 
The username must be all lowercase letters.

+1. That could be the cause ...

---

### Post by rsmedude on 2011-02-26
[COLOR=black][FONT=Verdana]Yea that did it guys. It came to me after I posted that I was having an issue. Sorry about that I have only ever setup one other Ubuntu machine before and that one I pretty much just setup with whatever it wanted to do because I was new to Ubuntu and LINUX in general.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]This is all a learning experience for me. :)[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Thanks for the help though I do appreciate it![/FONT][/COLOR]

---

### Post by Bucky Ball on 2011-02-27
Great it worked out. Enjoy the learning curve and the new OS. There's a lot to like as I guess you're discovering ... ;)

All the best with it. Mark as 'solved' if it is to help others . :)

---

### Post by rsmedude on 2011-03-01
> **Bucky Ball said:**
> Great it worked out. Enjoy the learning curve and the new OS. There's a lot to like as I'm use you're discovering ... ;)

All the best with it. Mark as 'solved' if it is to help others . :)

Hi there everyone,

Bucky... I am not totally new to Ubuntu I am just new to installing it on a laptop. However I am finding that this little 900 MHZ system has some kick left in her. As for marking this solved I am going to hold off till tonight because I want to get some final notes and thoughts together so that if someone does run into similar issues there will be (to the best of my ability) full notes here. Hopefully that will help out the next person coming down the road!

---

### Post by Bucky Ball on 2011-03-02
Sounds good.

---

