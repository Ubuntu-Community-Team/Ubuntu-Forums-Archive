---
title: "32 bit support on 64 bit systems ?"
date: 2010-11-08
forum: General Help
---

### Post by houseworkshy on 2010-11-08
I'm running the 64 bit amd version of Ubuntu 10.04.1lts.  Browsing around I found a deb file for a game which I would like to try out, this one:-  [http://www.energietycoon.de/en/](http://www.energietycoon.de/en/)
It is however a i386 architecture.  I simply wondered if there was some way of making it work in a 64 bit enviroment other than using virtual box or the windows version in wine.  Contrary to my usual habits I want to keep this install simple, stable and alien repository free.  I only want to see what it is like and would rather not go installation mad just for a bit of recreational curiosity.  Years ago, ( for spectrum 48k, commodore and some others of similar vintage ) , some friends and I partially wrote something similar which came to nothing ( inherit big business, beat the competition, don't go bankrupt, don't destroy the world sort of theme ).  So resolutions aside I have a really good excuse ...  well er .. just want to see what they've made of what looks like a similar game .... on a modern machine....ok semi- nostalgic exuse ...it'll do anyway.

---

### Post by searchfgold6789 on 2010-11-08
32 bit packages will work on 64 bit systems.
> Applications found in the Ubuntu archives should however all work out of the box in 64-bit mode.
If those ones work, I would expect others to work as well.

---

### Post by houseworkshy on 2010-11-08
That's what I thought but on this one the deb package manager tells me that it is the wrong architecture ( i386 ) and won't do it.  It says on the site that it is the one for Ubuntu.  Could be a dud I suppose, it's fairly recent.  Thanks for the reply.

---

### Post by wojox on 2010-11-08
You need 32 bit libraries. Look for ia32-libs of getlibs.

---

### Post by houseworkshy on 2010-11-08
Thanks.  I'll close the browser and take a look.  If all works I'll come back and say so.

---

### Post by 3Miro on 2010-11-08
You can install it form the command like with:

```
 dpkg -i --force-architecture your_package_name.deb 
```

The question. however, is whether or not it will run afterwards. You will probably need to install the 32-bit libraries, but I am not sure which ones and how many. Try to run the game and check what errors it gives, that should give you a hint on what you need.

---

### Post by houseworkshy on 2010-11-08
I've just had a quick look in synaptic and I have the ia32-libs already.  There are some others, one which allows foreign code to run, one for fortrain, one for c++ bindings, one for maths and another for something called GOMP.  Would any of those do it?  Also thanks for the new post I haven't tried forcing with dpkg yet so will look at it's man pages as it would be a new proceedure for me and I'd want to know how to undo it afterwards just in case.

---

### Post by dino99 on 2010-11-08
you might have some usefull errors logged

---

### Post by 3Miro on 2010-11-08
> **houseworkshy said:**
> I've just had a quick look in synaptic and I have the ia32-libs already.  There are some others, one which allows foreign code to run, one for fortrain, one for c++ bindings, one for maths and another for something called GOMP.  Would any of those do it?  Also thanks for the new post I haven't tried forcing with dpkg yet so will look at it's man pages as it would be a new proceedure for me and I'd want to know how to undo it afterwards just in case.

You should be able to go to Synaptic and just uninstall the package afterwards. Forcing dpkg means install the package as you would normally, except skip the part where it checks for the architecture.

---

### Post by houseworkshy on 2010-11-08
I shall have a look at the logs and play around with the ideas above.   It will have to be later though as I have to get on with other things.   Looking st the site again it could be that I have the wrong hardware,  onboard nvidia rather than radeon.  Whatever happens thanks for all your  help, if I can get the thing to run I'll return and say so.  It could  also be that my machine is getting flaky with age.  Freecol has never  worked for me and I also get stalls in video playback ( though the sound  doesn't stall ) and tracking errors in totem, in the last install the  10.04.1 this also happens with vlc which wasn't the case in previous  ubuntus.  So it could relate to hardware though as usual puppy linux is  perfect( suggesting the hd perhaps, it's five years old now ).  None of  this matters much as long as open office works which it does.  When I  next have time I shall give the machine a good clean and bang my head  against the errors which only really affect things which distract me  from what I should be doing anyway.  Don't bother about all that lot,  except as symptoms, as I'd post specific question in relevant places if I  should need help.  Just felt like a quick play but times up. 
Thanks to all of you for your very fast responces.  I haven't been on  the forums for quite a while and it's good to see it's as friendly as  ever.  Also a familliar name ( good to see you again dino99, I hope life  is treating you well.)  Take care folks.  Signing off for a while, I'll  post in a few days with errors or success.

PS took to long writing the above and got signed out.  Forcing dpkg is less dangeroud than it sounds then.  I'll give it a try this evening. Thanks.  Bye for now.

---

### Post by houseworkshy on 2010-11-08
I've tried the dpkg force.  This is what I did in the terminal.[ATTACH]175049[/ATTACH]

This put a link to the game in my menu.  However when I tried to use it all it did was open a terminal.  That was the first time, just tried again and nothing seemed to happen.  So I opened a terminal and tried energytycoon, which seemed a good guess as it knew what I was trying to do because it gave me 

energytycoon: error while loading shared libraries: libOgreMain-1.6.4.so: cannot open shared object file: No such file or directory

Then I tried reinstalling the libOgreMain-1.6.4.so to be told that I had the lastest version.

---

### Post by 3Miro on 2010-11-08
> **houseworkshy said:**
> 
Then I tried reinstalling the libOgreMain-1.6.4.so to be told that I had the lastest version.

You need the 32-bit version of that library. Go to Synaptic and make a search. Look for the 32-bit one (as in multilib). I am not on Ubuntu right now, I will check tomorrow (if you cannot find the library, you can PM me so I don't forget to look for it).

---

### Post by houseworkshy on 2010-11-08
Thats very kind of you thanks.  I'll stop browsing and try that now.  Then come back tomorrow.  What was going to be a going to be a quick recreational glimpse seems to be turning into a bee in the bonnet, wish I had more time.  I like dpkg, tells one what is missing very nice, bound to be useful again so I'm not really wasting time.

---

### Post by houseworkshy on 2010-11-08
I've just tried to get the file in synaptic and couldn't find it.  So, feeling rash, I searched all for multilib and put in everything which canonical support.  Still no go.  Then tried reinstalling it with dpkg and still no go.  I don't have backports enabled and my repositories are as when fresh with cannonical lucid partner enabled.  I've also tried putting OGRE ( it is written in OGRE ) in from the software manager and will try synaptic in a moment for 32 bit versions. 
   
If the game is as good as the review and video of it and Ubuntu pass it as clean and the developers are happy about it then this one may be a good candidate for the repositories IMO (small file too).    The sort of thing people who like freeciv, city management and simutrans type games would probably like.  I know that it works on someones machine as there is a video of it here.

 [http://freegamer.blogspot.com/2010/09/energy-tycoon.html](http://freegamer.blogspot.com/2010/09/energy-tycoon.html) 

Maybe this one is currently only for 32bit users though Exactly the sort of game I end up taking of my system because I play it too much, ah well maybe it's just as well.  Shall try for 32 bit OGRE and see what that does if I can find it.

Update.

I've dug around and it looks like I'd have to add a ppa for the 32 bit OGRE things, so perhaps I'll leave it for a while unless the gameing itch gets too strong.  Though if anyone has done this and found that all is well or not well then let me know as I can throw away some time this weekend and playing energy tycoon may be a rather nice way of doing it.  If it causes problems then I'd rather not if it means fiddleing around haveing to mend things. 

[https://launchpad.net/~ogre-team/+archive/ogre](https://launchpad.net/~ogre-team/+archive/ogre)  has the details

Thanks to all for your help.  It may be the case that 32 bit users can just play it so if anyone has wouldn't mind knowing if the game is really as good as it looks.

---

### Post by spiritofreason on 2010-12-31
Don't you like Debian's way of doing multilib?

They've compiled and packaged all these nice libraries for 32-bit systems, but you can't use them because they decided to put them in /usr/lib32 instead of /usr/lib on 64-bit systems. So now, they have to create separate packages to enable 32-bit support on 64-bit (and naturally, they don't bother giving you more than a pretty minimal subset).

So much wasted effort... Something needs to change.

---

### Post by bruno9779 on 2011-01-13
I have spent already one hour looking for Ogre 32 bit.

I suspect it would have been much faster to compile it from source

---

### Post by spiritofreason on 2011-01-13
Compiling the game from source would probably be easier.

If I weren't so lazy, I'd do it for you and post the 64-bit package somewhere, but making a package would mean I'd have to write the control file, take responsibility, provide some support, etc. Too lazy. ;-)

---

### Post by bruno9779 on 2011-01-13
It won't compile on 64bit. 

I got it running by installing 4 32bit .debs:

[http://packages.ubuntu.com/maverick/i386/libogremain-1.6.4/download](http://packages.ubuntu.com/maverick/i386/libogremain-1.6.4/download)

[http://packages.ubuntu.com/maverick/i386/libois-1.2.0/download](http://packages.ubuntu.com/maverick/i386/libois-1.2.0/download)

[http://packages.ubuntu.com/maverick/i386/libzzip-0-13/download](http://packages.ubuntu.com/maverick/i386/libzzip-0-13/download)

[http://packages.ubuntu.com/maverick/libfreeimage3/download](http://packages.ubuntu.com/maverick/libfreeimage3/download)

I had already all the 64bit versions, I guess 64bit is not taken in the slightest consideration here...

EDIT: Doing the above has got the game running, but has made my system unstable.

When I run apt-get install -f the 32bit dependencies I have installed have been removed automatically

---

### Post by bruno9779 on 2011-02-08
The problem here is not with ia32libs. 

The game installs fine (with --force-architecture obviously) but then doesn't run because it expects Ogre to be the 32 bit version. (OGRE wrong ELF Class x64, or something in the lines)

If you install a 32bit .deb of Ogre your system becomes unstable.

---

### Post by houseworkshy on 2011-02-25
Wow this tread came back to life while I wasn't around.  Thanks for your efforts Soy.  Was the game good to play?  I've got a duel drive pc so may put 32 bit 10.10 on the other ( to replace 9.04) whilst sticking to the current 64bit amd lts on my main working drive.  As 64 bit is clearly not as compatable with 32 bit programs as I'd have expected I may do it for more than the sake of this game.  As I darn't risk an unstable system ( I also work on this machine ) it may be the only safe way for truculent 32 bit programs.

---

### Post by tgm4883 on 2011-02-25
> **houseworkshy said:**
> Wow this tread came back to life while I wasn't around.  Thanks for your efforts Soy.  Was the game good to play?  I've got a duel drive pc so may put 32 bit 10.10 on the other ( to replace 9.04) whilst sticking to the current 64bit amd lts on my main working drive.  As 64 bit is clearly not as compatable with 32 bit programs as I'd have expected I may do it for more than the sake of this game.  As I darn't risk an unstable system ( I also work on this machine ) it may be the only safe way for truculent 32 bit programs.

I see the source is available, perhaps you could compile it for 64-bit?

---

### Post by houseworkshy on 2011-02-25
I'm not at the compileing level.  Someday when I have a lot of free time I may grab a step by step guide for idiots and have a go.  Quite some time away yet.  Many years ago I enjoyed playing with spectrum basic and later used dos and but that's it.  There was a taste of cobal and pascal at college which didn't regester somehow, nor did fourth ( white lightning ) which a friend told me was really easy....not for me.  Don't have a computer wizz type mind.   
I have been playing with a bit of python and from what little I've seen so far it looks like one that I can get my head round so learning that is my next computer learning task.  Despite having used Ubuntu for a while and not being *quite* a beginner I've still a lot to learn about linux itself.

---

