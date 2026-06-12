---
title: "MS .net 3.5 Ubuntu 9.10"
date: 2009-12-20
forum: General Help
---

### Post by patryn150 on 2009-12-20
Hello to those who are much smarter than I with this wonderful OS called Ubuntu.  :)

I have been searching through forums for the last few days trying to find a way to make the MS .net 3.5 framework function on Ubuntu 9.10, unfortunately all to no avail.  I have seen people mention that they have it working, but apparently my own knowledge of Linux is not great enough to understand what they have done.

Can anyone here assist me with getting this to work?  While I do have access to Virtualbox with a Win XP installation, I would rather be able to run my D&D 4e character creator native (yes...I'm a dork...) or as native as possible. 

I currently have Wine 1.1.35, Winetricks and Mono 2.4 installed.  I also have Crossover to use as well.  

If you can help, please advise to any pre-req applications that may also be needed to get this working.  While I've been using Ubuntu for the last....9 months now?... I'm still learning.  

Thank you!

---

### Post by Mark Phelps on 2009-12-21
Well ... since you're still learning, one thing you really need to learn is how to check the WineHQ site to see which versions of MS Apps work with Wine.

The link below is to the .Net Framework page at their site, and as you can see, every version since 3.5 is rated Garbage: 

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2586]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2586")

---

### Post by doas777 on 2009-12-21
ok, I think I see the problem here.
mono IS the dotnet framework for ubuntu. if you app won't work via mono, it probably won't work at all. 

what application did you want to run through the .net framework?

---

### Post by patryn150 on 2009-12-21
@daos - 

It's the D&D 4.0 Character Builder.  I've seen several people throughout miscellaneous D&D forums mentioning that they have it running under Linux, but as to yet no one has mentioned how they got it to do so.  

@Mark -

Even though that site states that, I've seen other references that people have managed to get it to function.  Thus my reason for posting here, maybe someone who is more seasoned can help me out with making it work.

---

### Post by doas777 on 2009-12-21
have you tried installing it via wine?

---

### Post by madmax.santana on 2009-12-21
> Hello to those who are much smarter than I with this wonderful OS called Ubuntu.  :smile:
I have an objection. Why hello to only those who are smarter than you? You should say hello to all so that dumbos like me are not discriminated just for being in learning phase!!!
:D
Have a good time...


P.S. I meant it the lighter way.

---

### Post by patryn150 on 2009-12-21
@daos -

I have.  It errors out saying something about not being able to extract msvcr80.dll.  I've tried it with both Wine & Winetricks (latest version actually incorporated the dotnet35 verb).  Neither one would complete the installation after about 12% in.

Crossover does the same.

@madmax

:)  *wave*  Hello those of you who are in the same boat as me...

Thanks again!

---

### Post by doas777 on 2009-12-22
> **patryn150 said:**
> @daos -

I have.  It errors out saying something about not being able to extract msvcr80.dll.  I've tried it with both Wine & Winetricks (latest version actually incorporated the dotnet35 verb).  Neither one would complete the installation after about 12% in.

Crossover does the same.

@madmax

:)  *wave*  Hello those of you who are in the same boat as me...

Thanks again!

never used winetricks, but iirc, it helps automate dll overrides. did you create a native override for your vc++ dll?

---

### Post by patryn150 on 2009-12-22
daos -

No, I have not.  Not exactly familiar with what you are speaking to there either, but that would be my newness to both Linux & even moreso Wine.  Please explain.

Thank you for continuing to assist me.  I really do appreciate it!

---

### Post by doas777 on 2009-12-22
well, a dll override, occurs when you place an actual MS dll file in your apps folder, and tell wine to use it instead of the wine version of that dll. 

here are some instructions for creating overrides:
[http://www.winehq.org/docs/wineusr-guide/config-wine-main](http://www.winehq.org/docs/wineusr-guide/config-wine-main)

---

