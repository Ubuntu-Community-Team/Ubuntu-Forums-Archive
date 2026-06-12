---
title: "just upgraded: help me get my mozilla back!"
date: 2006-06-27
forum: General Help
---

### Post by ChrisC on 2006-06-27
I just upgraded (via synaptic) from breezy to dapper.  The first serious problem is that I don't have my Mozilla install anymore.  It's not on the menus, and synaptic does not recognize it as installed, although it might still be lurking on the hard drive somewhere.  I do not want to use Firefox, for reasons described below.

I'd ask on IRC, but my IRC was hooked in through Mozilla, and further it seems that my XIRC install has disappeared too.  Man, I am dead in the water!  Now I'm afraid to start Thunderbird up, because that wasn't an official ubuntu app either ...

When I went through the upgrade I specifically did not allow it to actually remove any of the packages, but anyway I think it killed the mozilla install well before that prompt because I started getting "missing mozila.png" popup alerts early in the install process.

I can see that my profile files still exist, thank god, because the number one thing I don't want to lose is all my cookie preferences (I block most cookies).  I am NOT yet ready to move to Firefox, because there are lots of things about it that I don't like and thus I would need to research all the extensions and configs required to finally get it to behave the way I like (like Mozilla!)

Can someone help me recover mozilla so that it's using my existing profile?

---

### Post by zxee on 2006-06-27
I don't know for sure but can you try and install moz "by hand" i.e. not from apt but just download it and use the mozilla installer. I don't know if that will find your preferences. You should be able to point mozilla to those, provided you know where they're kept.

---

### Post by ChrisC on 2006-06-28
Anyone else?  If I re-install Mozilla via synaptic, is there a way to re-associate it with my existing profile?

---

### Post by FredB on 2006-06-28
Mozilla will find it without problem.

Look at the profiles.ini in your profile. And verify it is pointed to the real location.

And if you like Mozilla, why not trying SeaMonkey 1.0.2 (or 1.0.1) which is based on Gecko 1.8.0, like lastest firefox.

And by the way, Mozilla (1.7), Firefox 1.5.0.x and Thundebird 1.5.0.x are official ubuntu apps in Dapper Drake.

---

