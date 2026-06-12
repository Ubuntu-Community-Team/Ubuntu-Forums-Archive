---
title: "Can't install Skype"
date: 2009-07-19
forum: General Help
---

### Post by preston326 on 2009-07-19
Hello, I've just installed Linux Ubuntu (my very first time using linux) and I'm experiencing some problems.
When I try to install Skype I get the following error: Wrong architecture 'i386'
I did some researching but I don't understand those tutorials (first day I'm using Ubuntu), can some one give me simple step by step tutorial how to install 32-bit apps?
Thank you.

---

### Post by garrynigel on 2009-07-19
he hi
just go to applications -->accessories-->terminal

den type dis command
sudo-apt-get install skype
after dat type ur sudo password and get it installed


i386 is for a pentium pocessor..u mite have an amd processor or some oder processor

actually sorry i forgot

before typing the command in d terminal go to system --> administration -->  software sources and click third party software and den add dis line in d field area
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
i think u should be done

---

### Post by preston326 on 2009-07-19
> **garrynigel said:**
> he hi
just go to applications -->accessories-->terminal

den type dis command
sudo-apt-get install skype
after dat type ur sudo password and get it installed


i386 is for a pentium pocessor..u mite have an amd processor or some oder processor
Thanks for help but i get:
bash: sudo-apt-get: command not found

Yes I do use AMD processor

---

### Post by TeoBigusGeekus on 2009-07-19
It should be
sudo apt-get
and not 
sudo-apt-get

---

### Post by garrynigel on 2009-07-19
sorry typin error..its 
sudo apt-get


[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

check dis link out i guess ul find evryting here dat u need

in case u cant understand evryones here to help u :D

---

### Post by preston326 on 2009-07-19
Oh i tryed command sudo apt-get install skype and it did worked, but... Now i get 
E: Couldn't find package skype
Where is my E drive? I can't see drive letters in my Computer.. thing

---

### Post by preston326 on 2009-07-19
> **garrynigel said:**
> sorry typin error..its 
sudo apt-get


[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

check dis link out i guess ul find evryting here dat u need

in case u cant understand evryones here to help u :D
Oh, haven't seen this one, thanks I'll read it :)

---

### Post by garrynigel on 2009-07-19
did u add d repository in d sources should have worked den

---

### Post by preston326 on 2009-07-19
> **garrynigel said:**
> did u add d repository in d sources should have worked den
Err I didn't understood what you said but hey that tut is really nice it seems I solved my problem, sort of. Thanks for help.

---

### Post by Yellow Pasque on 2009-07-19
Search around for threads with Skype in the title on this site's x86-64 subforum. I know the Medibuntu repository has Skype .deb's packaged specifically for easy installation on amd64.

---

### Post by michy99 on 2009-07-19
> **garrynigel said:**
> did u add d repository in d sources should have worked den

Do you expect anyone to take you seriously with that baby talk?

---

### Post by garrynigel on 2009-07-20
cos he was new to linux so i tht i talked baby..or wer u being sarcastic im confused...:confused:
Hey bdw dis was my first reply ...so im learnin rite

---

### Post by 3rdalbum on 2009-07-20
> **garrynigel said:**
> cos he was new to linux so i tht i talked baby..or wer u being sarcastic im confused...:confused:
Hey bdw dis was my first reply ...so im learnin rite

Might be a good idea if you double-check your commands by running them, before posting them to others :-)

I would have suggested adding the [Medibuntu]("http://www.medibuntu.org") repository; that also helps for a number of other useful packages that new users generally want to install.

---

### Post by p0cky84 on 2009-07-20
> **preston326 said:**
> Err I didn't understood what you said but hey that tut is really nice it seems I solved my problem, sort of. Thanks for help.

No wonder you didn't understand that fool.

@[garrynigel]("http://ubuntuforums.org/member.php?u=729595")
Goddamnit you're worse than me. Learn to spell, please.

---

