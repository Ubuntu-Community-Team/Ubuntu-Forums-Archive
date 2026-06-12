---
title: "Someone help me before i set fire to my computer"
date: 2009-11-28
forum: General Help
---

### Post by kcirrab on 2009-11-28
ok i like ubuntu but i am a windows pro not a ubuntu pro and i am not used to this terminal crap... i am so frustrated with this thing i am bout to set fire to it... all i want to do it install one damn theme file and i cant and its pissing me off.... im used to being able to do what ever i want when ever i want with windows and using this makes me feel like im going back to dos again sometimes and i have forgotten all my dos.... someone please help me before i set fire to this damn thing.... here is the link to the file i am trying to install...

[http://gnome-look.org/CONTENT/content-files/62176-Blubuntu-Aurora.tar.gz](http://gnome-look.org/CONTENT/content-files/62176-Blubuntu-Aurora.tar.gz)

what the hell is a tar.gz file anyway... i thought this was linux for human beings not alpha geeks....

---

### Post by ed-koala on 2009-11-28
Here's your solution:

[http://ubuntuforums.org/showthread.php?t=1320283]("http://ubuntuforums.org/showthread.php?t=1320283")

---

### Post by Bartender on 2009-11-28
Google search works the same for windows pros as it does for Linux geeks.
Poke around in the "Desktop Environments" section of the Ubuntu Forums...

---

### Post by audiomick on 2009-11-28
And apart from all of that, the terminal is your friend, and it is not dos.
I do everything I possibly can via the gui, but there are some things for which the terminal is just better.

---

### Post by GregBrannon on 2009-11-28
Please post pics of the fire; before, after, and a couple in the middle.

---

### Post by Hamchan on 2009-11-28
.tar.gz is just a compressed file, similar to .zip on windows. Ubuntu comes with a default program to extract this file, so you should just be able to double click to extract it.

---

### Post by kcirrab on 2009-11-28
im goin back to windows im bout to kill this thing

---

### Post by fluffman86 on 2009-11-28
ed-koala's solution is correct.  I tested it and it works for me.  Just drag and drop the file into System > Preferences > Appearance.  That's WAY easier than all the registry hacks I did to skin Windows.  :P  Also check out this link on the post he linked to:
[http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

It's got all kinds of great information, and I particularly like this bit near the end: > The easiest way to help a new user install something is to provide a command that will accomplish it. That is not in my opinion the best way to make a new user understand how Ubuntu works. It's also sad how you can leave the impression that Ubuntu needs to be used through a command-line for the simplest of tasks, when capable graphical tools exist for the same purposes.

This is so true.  There is a graphical equivalent to almost everything you can do in Ubuntu/Kubuntu, or linux in general.  It's just that the command line is 1) easier to give instructions for, and 2), works longer and across more distros.  For example:

A new user posts on the forum and wants to install flash, mp3 support, etc.  I can direct him to Applications > Accessories > Ubuntu software center, tell him to enable extended repositories, click ok, apply, etc, search for ubuntu-restricted-extras, ok, blah blah blah.  Or I can tell him to open a terminal and copy/paste "sudo apt-get install ubuntu-restricted-extras"

Ok, well maybe the second option wasn't *THAT* much quicker.  But what if the user was using Jaunty, and they are confused because Ubuntu Software Center is new to Karmic, and Jaunty had Add/Remove Programs instead?  What if they are using Kubuntu, which (last I checked?) didn't have the Software Center, and if it did it's in a different place.  What if they are using crunchbang or some other debian/ubuntu based distro, which looks very different?  

What if the question that was asked wasn't specific to Ubuntu, but a general linux help question, and somebody found this thread on google, and they were running Red Hat, or Suse?  The command line help would still be applicable...I know I've gotten help from 10 year old Red Hat mailing lists via google, because many of the terminal commands are the same.

Well, I've rambled enough.  Please bear with us as we continue to use terminal commands.  In time, you'll either learn to love it yourself, or you'll recognize that every time we say "apt-get" you'll automatically start searching for stuff in System > Administration > Synaptic.  ;)

Oh, and also bear with Linux.  It's been around nearly as long as Windows, and Unix has been around longer.  It does things differently, but not necessarily better or worse.  [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by elliotn on 2009-11-28
Kill it already instead. Next time ask google

---

### Post by audiomick on 2009-11-28
what fluffman said, with bells on...:p

---

### Post by sloggerkhan on 2009-11-28
All you have to do is drag the downloaded theme onto your appearances preference window and it installs. As it is, you'll be missing the theme engine needed to display the theme properly, installing the theme itself is really easy.

---

### Post by kcirrab on 2009-11-28
Im just sick of running this damn thing from the terminal... i HATE the terminal.... i want it to die... all i want to do is one thing... i tryed your solution and it told me i had to install something else that was missing and now i ****** EVERYTHING up trying to install the other thing.... ubuntulooks or something like that.... this thing pisses me off... why does this have to be so confusing...

---

### Post by scorp123 on 2009-11-28
You're sure you're a "Windows Pro"? ... you definitely don't sound like one. Your current behaviour will get you nowhere. Please try and read what people write to you.

All you have to do is to drag & drop the theme archive into the Theme installer and the rest will happen automagically.

No idea why you're using the terminal for this ??

---

### Post by kcirrab on 2009-11-28
i did drag and drop the file... it installed but then it said i need something else to make it work right and thats how i screwed it up was trying to get that part in.... ubuntu looks or something like that

---

### Post by ed-koala on 2009-11-28
I know what ya mean kcirrab.  I hate gnome themes too, because they are not all "there" usually.  A shame really, but not a really big problem actually.

Most of those themes need a "main" theme.  You are only getting part of the overall look (I think that's how it works). Install that main "look" and the rest show up fine.

I think all themes should have everything needed in one piece, not need anything from somewhere else, but that's my opinion.

---

### Post by scorp123 on 2009-11-28
> **kcirrab said:**
>  and thats how i screwed it up was trying to get that part in.... ubuntu looks or something like that Next time try and write down the precise message. That helps. And what you need is the **"gtk2-engines-ubuntulooks"** package.

You said you don't like the terminal. Even so: Just copy and paste the commands I give you here (when it asks for your password: That's your own password -- type it blindly as there won't be anything echoed back!) :

```
sudo apt-get update
sudo apt-get install gtk2-engines-ubuntulooks

```

Voila. Done.

---

### Post by fluffman86 on 2009-11-28
After reading your 2nd and 3rd post (to this forum overall, HA!, you didn't even ask for help with stuff before complaining!), I think it's appropriate to respond again.

Ubuntu is NOT Windows.  It is free; you did not pay for it (and if you did, you could call Canonical.  See: [http://www.ubuntu.com/support/services](http://www.ubuntu.com/support/services)  It's actually affordable; it costs less than most Windows licenses).

While Canonical *does* employ some staff to work on some things, everyone in these forums are volunteers.  We're users just like you, who started using Ubuntu because we were sick of Windows or because we love Linux/Unix.  For some it was mere curiosity, others closer to necessity (thank you, BSOD!)  :P

That said, none of us *HAVE* to help you.  If you *want* help, ask nicely, and wait at least a few hours (preferably 12-24) for a reply.  

And again, none of us here are paid for what we do here.  So "threatening" to leave Ubuntu does nothing to us.  I laughed, actually.  Wow, you don't want to use Ubuntu anymore because you're unwilling to learn something?  What ever will I do without the $5,000 I get paid for helping you or converting you?  

Oh, wait...

---

### Post by scorp123 on 2009-11-28
More themes here:
[http://www.ubuntugeek.com/nice-themes-for-ubuntu-9-10-karmic-users.html](http://www.ubuntugeek.com/nice-themes-for-ubuntu-9-10-karmic-users.html)

They have a so called "apt" Link for all of them:
[apt://zgegblog-themes](apt://zgegblog-themes)

Just click on that link. The rest happens automatically. Voila. Can't get easier than that. :D

---

### Post by presence1960 on 2009-11-28
> **kcirrab said:**
> ok i like ubuntu but i am a windows pro not a ubuntu pro and i am not used to this terminal crap... i am so frustrated with this thing i am bout to set fire to it... all i want to do it install one damn theme file and i cant and its pissing me off.... im used to being able to do what ever i want when ever i want with windows and using this makes me feel like im going back to dos again sometimes and i have forgotten all my dos.... someone please help me before i set fire to this damn thing.... here is the link to the file i am trying to install...

[http://gnome-look.org/CONTENT/content-files/62176-Blubuntu-Aurora.tar.gz](http://gnome-look.org/CONTENT/content-files/62176-Blubuntu-Aurora.tar.gz)

what the hell is a tar.gz file anyway... i thought this was linux for human beings not alpha geeks....

I would suggest that if you like Ubuntu then be willing to learn from the beginning just as you did with windows. It is like that with everything in life- you must start at the beginning and work your way up. A lot of us felt the same way or had another source of frustration when starting to use Linux for the first time.

You have 2 options: hang in there and learn, which if you are as good as you say with computers albeit windws, you will learn linux...

OR pack it in and go back to your comfort zone. The choice is yours.

---

### Post by scorp123 on 2009-11-28
> **fluffman86 said:**
>  So "threatening" to leave Ubuntu does nothing to us.  I laughed, actually.  To be honest ... me too :D

Normally I would have formulated some flame-posting and posted the "Linux is not Windows!!" link ... but I'm in a good mood tonight :D

---

### Post by scorp123 on 2009-11-28
> **kcirrab said:**
> i am a windows pro  BTW: Being a "Windows Pro" doesn't mean much here. Linux is not Windows. You'll have to accept that. Linux isn't meant to become like Windows. Who'd want that?? One Windows is enough.

And instead of posting stuff about setting your computer on fire you could have formulated an intelligent posting where you simply ask for help?

e.g. Title: "How do I install a theme? (tar.gz file)"

That title that you chose is more likely to attract criticism and harsh reactions than people willing to help you.

And as posted above: Nobody forces you to use Linux. Don't like it? Fine. Don't use it then. Nobody is forcing you. Know what you want and then stick to it. OK? 

And If you have more problems: Please feel free to open new threads and simply ask. Ask. Not whine and threaten and what not. Politely asked questions usually produce politely formulated responses that help to resolve the issues. :)

---

### Post by presence1960 on 2009-11-28
> **scorp123 said:**
> To be honest ... me too :D

Normally I would have formulated some flame-posting and posted the "Linux is not Windows!!" link ... but I'm in a good mood tonight :D

I hear you, imagine what is banging around in the OPs head now. I try to be diplomatic, but sometimes I falter. I think I did good on this one because my instinct was to be abrasive with no mercy. But rather I opted for the truth put in a nice way.

---

### Post by kcirrab on 2009-11-28
i think i pissed it off... i got both installed now and now the theme is not showing up and when i try to reinstall it is says cant over write directory

---

### Post by scorp123 on 2009-11-28
> **presence1960 said:**
>  my instinct was to be abrasive with no mercy.  Well ... he was *seriously* frustrated. You'll have to forgive him that ... this time. He should have asked before he gets so frustrated. That would have been more fruitful.

---

### Post by scorp123 on 2009-11-28
> **kcirrab said:**
>  when i try to reinstall it is says cant over write directory Can you give us the precise error message?

---

### Post by kcirrab on 2009-11-28
i appologize if i came off threatening or the such i am just annoyed with this thing

---

### Post by scorp123 on 2009-11-28
BTW ... what's the name of the theme you try to install anyway? Maybe it is in the repositories somewhere somehow and could be easily installed via the package manager? (... instead of having to mess with local archive files manually and what not ... )

---

### Post by kcirrab on 2009-11-28
Installation for theme "Blubuntu-Aurora" failed.
Can't move directory over directory

---

### Post by ed-koala on 2009-11-28
I understand, trust me.  After 10 tries to install 9.10 and not being able to even boot my PC after any of em, I understand frustration.  I got it fixed though, and I'm still sane.

---

### Post by scorp123 on 2009-11-28
> **kcirrab said:**
> Installation for theme "Blubuntu-Aurora" failed.
Can't move directory over directory 

This one?
[http://gnome-look.org/content/show.php/Blubuntu-Aurora?content=62176](http://gnome-look.org/content/show.php/Blubuntu-Aurora?content=62176)

---

### Post by kcirrab on 2009-11-28
yes

---

### Post by fluffman86 on 2009-11-28
> **kcirrab said:**
> i think i pissed it off... i got both installed now and now the theme is not showing up and when i try to reinstall it is says cant over write directory

Right, that happened to me to, but I only installed the first link you posted, and it didn't show up right away.  You may need to reboot (or just log out/log in) to get the second theme working.  

I got half of the theme working, though, by just clicking "customize..." 

It's in there, even if it doesn't show up in the main window.

---

### Post by kcirrab on 2009-11-28
now it says im missing the theme engine aurora too...sigh... it hate me lol

---

### Post by scorp123 on 2009-11-28
The description says that it also needs the "Aurora GTK Engine". And that sucks because apparently you're supposed to compile that thing from source. That may be a little bit too much for you now ...

Google just gave me this link:
[http://fayaballz.artzz.net/wp-content/uploads/2009/07/gtk2-engines-aurora_1.5.1-2_i386.deb](http://fayaballz.artzz.net/wp-content/uploads/2009/07/gtk2-engines-aurora_1.5.1-2_i386.deb)

That's a *.deb archive (= an installable container package) that contains pre-compiled + pre-made stuff so you won't have to do this yourself.

So I'd suggest you download that package too and then click on it? A program should open and offer you to install that package.

BTW, "GTK Styles" define how window/application will look like. They are not necessarily complete themes. So it could be that in order to activate this widget style you'll have to open the "Appearance" program first:
***System > Preferences > Appearance ***

... and then click on **"Customize"** ... Check the **"Controls"** tab if *Blubuntu* or *Aurora* get listed anywhere. That would be the stuff that you installed and that's how you'd activate it (e.g. my modifying the current theme).

---

### Post by kcirrab on 2009-11-28
i tryed the deb file u gave me and um i got this error 
Error: Wrong architecture 'i386'

---

### Post by ed-koala on 2009-11-28
I still say themes should all be self contained. Download, install and presto.  Why can't this be done? Or at least say what else you need and where/how to get it.

---

### Post by kcirrab on 2009-11-28
i agree... why must windows mac and ubuntu be a pain to install themes... the world may never know haha

---

### Post by expxe on 2009-11-28
to the OP,

i understand your frustrating, **linux is a terrible operating system. period.** but ubuntu is different! it tries to move away from the closed small-minded thinking of linux users and radically change, each release improves usability and comparability. soon users will not have to use the ridiculous command line anymore to run ubuntu and the operating system will be able to take on even windows while being free and open source. 

people put up with linux because they feel that microsoft's control and position in the computing world is not right. but this comes at a cost, currently ubuntu is about 5 years behind microsoft's newest operating system windows 7. so if you want to go back to windows 7 it is understandable, it is truly a great operating system, something MS has come out with that is actually great. but ubuntu gets a new release every 6 months, so if you do decide to leave, come back in april and redownload the next version, you might like it.

---

### Post by fluffman86 on 2009-11-28
> **kcirrab said:**
> i tryed the deb file u gave me and um i got this error 
Error: Wrong architecture 'i386'

Remember what I said about a graphical tool for everything?  That's unless you're running the x64 version of Ubuntu.  Sorry.

Download the .deb file to your desktop.  Then open a terminal and copy/paste:

sudo dpkg -i --force-architecture ~/Desktop/*.deb

Hope that helps!

---

### Post by scorp123 on 2009-11-28
> **kcirrab said:**
> Error: Wrong architecture 'i386' You're on a 64-bit machine. Bummer.

We could force the installation anyway ... but I have no idea how stable the system would be after that.

Did you try the "Blubuntu" theme from the repository? Isn't that theme nearly the same?

Terminal way:
```
sudo apt-get install blubuntu-theme
```

GUI way:
***System > Administration > Synaptic Package Manager***
... and there search for the ***blubuntu-theme*** package ... click on it so it gets marked for installation (should be self-explanatory). Then click the **"Apply"** button on the menu bar.

That should give you a similar theme ... Maybe that would do?

In fact there are dozens and dozens of themes in the repositories. If you search for "theme" you will easily find them all. And installing things this way is way way way easier and less frustrating than messing with such rather obscure themes that require you to compile stuff (I haven't compiled anything myself since at least 1999 ... On Linux you simply shouldn't have to anymore these days ...)

---

### Post by sigurnjak on 2009-11-28
Hi there ! 
Do not reinstall theme . Go  to appearance and choose customise  option , click on blubuntu theme in the list .It is only GTK STYLE .
If that does not work go in to system -administration - synaptic . Put in your password , click on search and type in blubuntu 
There will be a list of stuff, right click on stuff you wish to install, agree if it says in needs this or that . CLICK APPLY .
Go back to appearance and find blubuntu . 
Enjoy !

I see i am not the only one with Synaptic suggestion !;)

---

### Post by scorp123 on 2009-11-28
> **fluffman86 said:**
>  ```
sudo dpkg -i --force-architecture ~/Desktop/*.deb 
```
 Yeap, that would be the command to force the *.deb package to install, "wrong architecture" or not. It may work. Theme files shouldn't be too problematic ...

---

### Post by fluffman86 on 2009-11-28
> **scorp123 said:**
> Yeap, that would be the command to force the *.deb package to install, "wrong architecture" or not. It may work. Theme files shouldn't be too problematic ...

hmm, I've force-installed lots of things.  Never had a problem...

Maybe I'm just lucky.

---

### Post by scorp123 on 2009-11-28
> **fluffman86 said:**
> hmm, I've force-installed lots of things.  Never had a problem... With themes and even codecs, browser programs (e.g. Firefox, Opera) and what not this might easily work, yes. But I wouldn't try that on e.g. kernel drivers. Those definitely need to match the kernel and the architecture. But the rest might indeed work without ever causing hickups, yes.

---

### Post by kcirrab on 2009-11-28
W00T!!! Thanks [fluffman86]("http://ubuntuforums.org/member.php?u=275993")!!! it worked. =D

ahhh... Solved

---

### Post by scorp123 on 2009-11-28
We're morons. All of us. We should have checked Launchpad. Wanna guess what I found?

[https://launchpad.net/~merlwiz79/+archive/aurora](https://launchpad.net/~merlwiz79/+archive/aurora)

Yes, that's the Aurora GTK style. And yes, there's a PPA for it. So OP can forget about forcing the architecture and easily install this stuff with the package manager. Doh.

:D

1-click install:
[ppa:merlwiz79/aurora](ppa:merlwiz79/aurora)

@OP: As it works for you now ... DON'T CLICK ON THIS. Let sleeping dogs lie. I am just posting this in case anyone runs into this thread via Google ...

---

### Post by fluffman86 on 2009-11-28
> **scorp123 said:**
> With themes and even codecs, browser programs (e.g. Firefox, Opera) and what not this might easily work, yes. But I wouldn't try that on e.g. kernel drivers. Those definitely need to match the kernel and the architecture. But the rest might indeed work without ever causing hickups, yes.

Yep, back during Feisty/Gutsy I was running x64 and force-installed flash and firefox 32bit since 64bit flash was not up to par yet.  Now I force install the Amazon mp3 downloader and maybe an old game emulator or something.  

I haven't fiddled around with getting new kernels running with anything other than a repository.  :P

edit: awesome.  a ppa.  now I feel like a genius.  :'(

edit2: </sarcasm>

---

### Post by jrrader on 2009-11-28
> **expxe said:**
> to the OP,

i understand your frustrating, **linux is a terrible operating system. period.** but ubuntu is different! it tries to move away from the closed small-minded thinking of linux users and radically change, each release improves usability and comparability. soon users will not have to use the ridiculous command line anymore to run ubuntu and the operating system will be able to take on even windows while being free and open source. 

people put up with linux because they feel that microsoft's control and position in the computing world is not right. but this comes at a cost, currently ubuntu is about 5 years behind microsoft's newest operating system windows 7. so if you want to go back to windows 7 it is understandable, it is truly a great operating system, something MS has come out with that is actually great. but ubuntu gets a new release every 6 months, so if you do decide to leave, come back in april and redownload the next version, you might like it.

You win the nutty rant award.

---

### Post by stinkeye on 2009-11-29
> **kcirrab said:**
> W00T!!! Thanks [fluffman86]("http://ubuntuforums.org/member.php?u=275993")!!! it worked. =D

ahhh... Solved

Awww .. I wanted to see burning computer pics.;)

---

### Post by scorp123 on 2009-11-29
> **jrrader said:**
> You win the nutty rant award. +1

summa cum laude.

---

### Post by expxe on 2009-11-29
> **jrrader said:**
> You win the nutty rant award.

but i love ubuntu

---

### Post by GepettoBR on 2009-11-29
> **GregBrannon said:**
> Please post pics of the fire; before, after, and a couple in the middle.

I second this motion. Doesn't matter if the problem is fixed.

---

### Post by cowboy7305 on 2009-11-29
I have to admit i don't like terminal ,but i never want to burn my computer, 
toss it out window yes ,so can i third for pics of burning computer

---

### Post by kcirrab on 2009-11-29
youtube burning laptop...its funny lol

[http://www.youtube.com/watch?v=28iItCrApz0](http://www.youtube.com/watch?v=28iItCrApz0)

---

### Post by jrrader on 2009-11-29
> **expxe said:**
> but i love ubuntu

You are obviously very young.  Your post (and a few others) show that you really don't have much knowledge on the subject.  Everyone is entitled to an option but someone who wants to know if BSD is "another obscure distro" probably doesn't know enough to make big sweeping generalizations about the computer industry.  You also keep making these posts about incompetent Linux programmers who can't make a proper GUI - Linux is open source and most programs are written by the people who intend to use the program - for themselves and their friends, not for the general population.  You want something better, learn programming and start contributing.

---

### Post by presence1960 on 2009-11-29
> **jrrader said:**
> You are obviously very young.  Your post (and a few others) show that you really don't have much knowledge on the subject.  Everyone is entitled to an option but someone who wants to know if BSD is "another obscure distro" probably doesn't know enough to make big sweeping generalizations about the computer industry.  You also keep making these posts about incompetent Linux programmers who can't make a proper GUI - Linux is open source and most programs are written by the people who intend to use the program - for themselves and their friends, not for the general population.  You want something better, learn programming and start contributing.

:P The way they got mad, that's how they will get glad again! :popcorn:

If it continues to bother them they can always use a more "advanced" OS, no one is forcing them to use an "inferior" OS like Ubuntu.

---

### Post by running_rabbit07 on 2009-11-29
> **jrrader said:**
>   You want something better, learn programming and start contributing.

+1:popcorn:

---

### Post by audiomick on 2009-11-29
still waiting for the fire pics....;)

---

### Post by expxe on 2009-11-29
> **jrrader said:**
> You are obviously very young.  Your post (and a few others) show that you really don't have much knowledge on the subject.  Everyone is entitled to an option but someone who wants to know if BSD is "another obscure distro" probably doesn't know enough to make big sweeping generalizations about the computer industry.  You also keep making these posts about incompetent Linux programmers who can't make a proper GUI - Linux is open source and most programs are written by the people who intend to use the program - for themselves and their friends, not for the general population.  You want something better, learn programming and start contributing.

and people wonder why after all these years linux still has not caught on as a mainstream OS....

---

### Post by expxe on 2009-11-29
> **fluffman86 said:**
> 
And again, none of us here are paid for what we do here.  So "threatening" to leave Ubuntu does nothing to us.  I laughed, actually.

you shouldn't be laughing, every user that leaves ubuntu will turn to windows (or mac) and that is enough to weaken the linux movement and strengthen theirs. don't laugh our users, instead help them out and send hasty emails to the developers to get their act together to make this OS more user friendly.

---

### Post by jrrader on 2009-11-29
> **expxe said:**
> and people wonder why after all these years linux still has not caught on as a mainstream OS....

No one wonders that.  Windows and Mac are perfectly fine for most people.  I work with Linux, but I had no problem installing Windows 7 on my dad's computer.  


> you shouldn't be laughing, every user that leaves ubuntu will turn to windows (or mac) and that is enough to weaken the linux movement and strengthen theirs. don't laugh our users, instead help them out and send hasty emails to the developers to get their act together to make this OS more user friendly.

sigh... [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by sensay on 2009-11-29
One of my very first posts here was threatening to 'leave' ubuntu for opensuse, not my finest moment. I had a real problem with my internet at first, didnt receive much help and got really wound up.

I'm not exactly young (25) but the stress of moving to a totally new operating system and dealing with the many challenges that presents a virgin user can be a contributing factor to these kind of posts. I was lucky, i had someone be real friendly and helped me out. I didnt get any crap for being moody and i resolved my issues in the end. Subsequently ive spent my time learning more and more about the wonderful world of linux, helping out where i can and am really enjoying it.

My point? Dont flame new users for getting frustrated, be helpful. You know more than them and im sure most of you had the same frustrations when you started out, even if they didnt end up as posts!

---

### Post by audiomick on 2009-11-29
> **expxe said:**
> you shouldn't be laughing, every user that leaves ubuntu will turn to windows (or mac) and that is enough to weaken the linux movement and strengthen theirs. don't laugh our users, instead help them out and send hasty emails to the developers to get their act together to make this OS more user friendly.

There is something in that, but

No one who programs open source takes money of you for a program that ostensibly "just works" that inevitably has problems. They say "we think this is good, try it out. We hope there are no problems."

I have _**never**_ seen the sentence "contact your system administrator" anywhere in Linux documentation. I am my own sys admin, and if I don't know, there's not much point me asking myself. That sentence is the most significant reason for me using Ubuntu.

---

### Post by presence1960 on 2009-11-29
> **expxe said:**
> you shouldn't be laughing, every user that leaves ubuntu will turn to windows (or mac) and that is enough to weaken the linux movement and strengthen theirs. don't laugh our users, instead help them out and send hasty emails to the developers to get their act together to make this OS more user friendly.

I really could not care any less if another person uses linux. Linux is here and fills a need for certain people. It is not for everyone. Although I can see by your signature that you are the type of person who is shouting from the rooftops & preaching about Linux. 

Linux is not anything like Windows and as such it will probably never be mainstream. The reason: The majority of computer users world-wide really does not give a flying you know what about security, customization, freedom, etc. They just want to turn on their computers by pressing the power button and have to do basically next to nothing to accomplish the task they wish to perform. In this respect windows is quite indeed superior to anything else on the market for that type of computer user (which by the way is probably 80%-90% of all users).

This type of thread illustrates exactly what I am talking about. The OP considers himself at least a Windows power user but is so frustrated at what some of us consider a task so simple. Imagine how a basic turn on my machine and it works windows user would feel. Another factor is the human condition. people are lazy. People are naturally resistant to change. When confronted with a new situation a lot of people will just revert back to the old way, even if the old way is not as good or beneficial. At least the old way is familiar and requires no ego shattering of having to learn all over again. That is the main reason some people stay in a bad relationship. it is comfortable to them because they know what to expect and believe they can manage that to a degree. So it is with anything in life including OSs.

Linux does have it's place but I do not think it will ever get much traction mainstream let alone take over the market share.

P.S. Even though I don't care if another person uses linux, I will gladly try to help someone who needs help with linux. Whether they continue to use linux or not is not my concern or responsibility.

---

### Post by audiomick on 2009-11-29
> **presence1960 said:**
> 

Linux does have it's place but I do not think it will ever get much traction mainstream let alone take over the market share.

Be nice if it did though...

btw. You do good posts.

---

### Post by Cytochromec on 2009-11-29
As far as TC setting his computer on fire, well, "[TC], my faith in human nature would be absolutely shattered if you didnt."

> **audiomick said:**
> Be nice if it did though...

btw. You do good posts.

Its classic quality vs quantity. If people like the TC are what it takes to expand this community, then I am happy with with the notion that Linux will never reach the mainstream.

---

### Post by scorp123 on 2009-11-29
> **expxe said:**
> and people wonder why after all these years linux still has not caught on as a mainstream OS.... If "mainstream OS" means "stupid like hell + badly designed" then I am thankful that Linux isn't mainstream. I need a reliable OS. Not one that is so dumbed down that even people can use it who probably shouldn't be using a computer in the first place.

And don't give me the "Don't you want your parents to be able to use Linux?" question. They are already using Linux and happy with it. Heck, my wife's parents are beyond 70 and they are Linux users too now.

Linux is tip top the way it is. Don't like it? Don't use it. :D

---

### Post by running_rabbit07 on 2009-11-29
> **expxe said:**
> you shouldn't be laughing, every user that leaves ubuntu will turn to windows (or mac) and that is enough to weaken the linux movement and strengthen theirs. don't laugh our users, instead help them out and send hasty emails to the developers to get their act together to make this OS more user friendly. **OH YEAH BABY! I'M RUNNING UBUNTU NOW! IT'S SO HARDCORE! LINUX IS GOING MAINSTREAM! HURRY UP AND JUMP ON THE BANDWAGON! TELL ALL YOUR FRIENDS! DITCH WINDOWS! COME BE A PART OF THE NEXT BIG THING!** 

I couldn't help but notice that the only post I have ever seen you use caps, is when the caps lock is on. Linux is not a movement, it is a way of life so to speak. If it is what you like, then you use it, if not, then use what does. It is freedom. Even if Canonical and RedHat went broke and disappeared, Linux would still be hear.

---

### Post by GepettoBR on 2009-11-30
> **running_rabbit07 said:**
> I couldn't help but notice that the only post I have ever seen you use caps, is when the caps lock is on. Linux is not a movement, it is a way of life so to speak. If it is what you like, then you use it, if not, then use what does. It is freedom. Even if Canonical and RedHat went broke and disappeared, Linux would still be hear.

Linux isn't a way of life any more than Android is a way of life. It's an operating system. It makes your computer/toaster/dead badger work. That's it. No more, no less.

---

### Post by running_rabbit07 on 2009-11-30
> **GepettoBR said:**
> Linux isn't a way of life any more than Android is a way of life. It's an operating system. It makes your computer/toaster/dead badger work. That's it. No more, no less.

That is your opinion and you are welcome to it. To me it becomes a way of life when it makes me happy every time I use it, though unlike the person I was commenting on, I do not feel the need to force what is a part of my life onto others.

---

### Post by stinkeye on 2009-11-30
> **running_rabbit07 said:**
> To me it becomes a way of life when it makes me happy every time you use it
I'll agree with that.

---

### Post by GepettoBR on 2009-11-30
> **running_rabbit07 said:**
> That is your opinion and you are welcome to it. To me it becomes a way of life when it makes me happy every time I use it, though unlike the person I was commenting on, I do not feel the need to force what is a part of my life onto others.

That's great. But understand that it's a way of life to you because it's grown into that. To people who are starting out with it, it's just an OS, and the "Linux is a way of life/philosophy/religion/community" speech scares people off and makes us all seem crazy. It's a valid speech, and I do believe it holds true for many people, but it scares off the newbies when we should be trying to help them.

---

### Post by Andy Moon on 2009-11-30
Hey dudes! Thanks people (and Canonical) for your work! you all rock. Been 1 year im on Ubuntu and still rocking;)

BIG THANKS also for placing some jokes on otherwise very technical forums. The ice on the cake so to speak.

Or maybe it's mista Gates who sends us some of his people ? :p

No bad feelings of course..:p

---

### Post by GepettoBR on 2009-11-30
> **Andy Moon said:**
> Hey dudes! Thanks people (and Canonical) for your work! you all rock. Been 1 year im on Ubuntu and still rocking;)

BIG THANKS also for placing some jokes on otherwise very technical forums. The ice on the cake so to speak.

Or maybe it's mista Gates who sends us some of his people ? :p

No bad feelings of course..:p

I love posts like this.

+>9000 beans to Ubuntu Forums.

---

### Post by SteveHillier on 2009-11-30
> **kcirrab said:**
> im used to being able to do what ever i want when ever i want with windows 

No you are not.  You are used to doing whatever Windows lets you do when it thinks you can.

Believe me, there are lots of things I would like Windows to do but I can never get it to do that.

All OS's are the same.  You get used to doing what they will let you and you thsn work within their parameters.  That is not the same thing as your statement!!

---

### Post by SteveHillier on 2009-11-30
> **audiomick said:**
> I have _**never**_ seen the sentence "contact your system administrator" anywhere in Linux documentation. I am my own sys admin, and if I don't know, there's not much point me asking myself. That sentence is the most significant reason for me using Ubuntu.

Oh, how I relate to this post.

---

### Post by camaron1 on 2009-11-30
Does anyone else realize the irony that the OP was just trying to install a theme that **should** have been so easy as a drag-and-drop but was not (as it usually happens, linux or windows), and has all exploded in this funny-as-hell thread?

Cheers everyone ;)

---

### Post by expxe on 2009-11-30
> **camaron1 said:**
> Does anyone else realize the irony that the OP was just trying to install a theme that **should** have been so easy as a drag-and-drop but was not (as it usually happens, linux or windows), and has all exploded in this funny-as-hell thread?

Cheers everyone ;)

just shows that linux needlessly complicated, the programmers are the ones that are incompetent but its the users that suffer.

but despite all the negative press about linux it is still my main OS and i hope more people will use it and pressure the developers to make the OS more user friendly. it has great potential, that is all that can be said right now.

---

### Post by hobo14 on 2009-11-30
> **expxe said:**
> just shows that linux needlessly complicated, the programmers are the ones that are incompetent but its the users that suffer.

but despite all the negative press about linux it is still my main OS and i hope more people will use it and pressure the developers to make the OS more user friendly. it has great potential, that is all that can be said right now.

Why do you persist with Ubuntu, if you find it so painful?

---

### Post by seenthelite on 2009-11-30
> **camaron1 said:**
> Does anyone else realize the irony that the OP was just trying to install a theme that **should** have been so easy as a drag-and-drop but was not (as it usually happens, linux or windows), and has all exploded in this funny-as-hell thread?

Cheers everyone ;) 

Yea I Do, but if the original post had included more detail of the actual problem and less ranting it would have been solved a lot quicker.

---

### Post by manny43 on 2009-11-30
I'm new to UBUNTU too and terminal gets confusing but i love all the research and the learning
experience that comes with it.Already installed firewall libdvdcss2 codecs.

---

### Post by Vince N on 2009-11-30
I don't really have much to add to the thread technically other than what others have posted, I really don't have any issues installing most themes into Ubuntu though sometimes the require an icon set or something that I have to hunt down.

As to your frustrations with Linux and Ubuntu, I understand.  But you'll need to please cool down and realize.  Ubuntu is NOT Windows.  It uses the command line, which once your used to it is much easier and faster than doing some things in the GUI.  If you don't want to use the command prompt that's your choice.  However because it is way easier to explain things in terms of the command prompt if you ask for help 9 times out of 10 command prompt commands is what your going to get.

I recommend reading this
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

It's a good article and helps to show some key differences and common misconceptions about Linux from Window's "Pros"

The simple fact is that Linux is all about choice.  To find software that meets your needs.  You can choose to continue to use Linux, and that may mean retraining and learning to do things a little differently than its been done before, or you can choose to go back to Windows if that better meets your needs.  You can also do as you threatened and choose to burn your computer.  Not everyone needs one.

As to the people who say that we need to kick the developers in the butts and get some usability things.  Linux has progressed more in the last few years than Windows has in it's entire history and with few exceptions Ubuntu gets better and more user friendly with every single release.  Is it perfect?  No but it is loads better than it used to be, and for a product that is completely free (save for time invested) I don't see how we can complain.  That may be the real price of Linux, it takes a little time.  It's a price I for one am perfectly willing to pay.  The OP and some others may not feel that way.  That's fine.  Linux is after all, about choice.

---

### Post by scorp123 on 2009-12-01
> **Vince N said:**
>  I recommend reading this
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

And I recommend you read the thread before you post the same link that was already posted before for like the 10th time ??

OP's problems were solved. So can please everybody move on instead of filling this thread with off-topic stuff?

---

### Post by dmizer on 2009-12-01
> **scorp123 said:**
> And I recommend you read the thread before you post the same link that was already posted before for like the 10th time ??

OP's problems were solved. So can please everybody move on instead of filling this thread with off-topic stuff?

And with that, thread closed.

Thank you all for participating.

---

