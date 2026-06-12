---
title: "can not install ia32-java-6"
date: 2009-11-10
forum: General Help
---

### Post by lordofduct on 2009-11-10
So I've just recently upgraded to 9.10 64-bit from 9.04 64-bit.

I've had Eclipse ganymede 32-bit installed for quite some time. Now since I've upgraded I can't create new projects for anything, or create new files. Any time in a window I hit buttons for 'next' or 'finish' that would create anything, nothing happens... just sits there like I never pressed the button.

Now I have to jvm's on the machine, a 64-bit one and a 32-bit one. I need the 32-bit jvm for my Eclipse 32-bit. But for somereason ubuntu isn't showing my 32-bit jvm anymore, though I can see it in /usr/lib/jvm

So I open synaptic and it's marked as installed there... but there is no option to reinstall it. So I uninstall it, with the idea that I'll install it again. I then go and install it again and get an error back...

> 
ia32-sun-java6-bin:
  Depends: sun-java6-jre (=6-15-1) but 6-16-0ubuntu1.9.04 is to be installed


what the? Ok... ummm.... I need this. I can't do my job with out it. Yeah I can boot into windows and do it, but I prefer it over here. Any help please!? Most of the software I use is on linux, the only reason I even have windows is for Adobe products.

I'm starting to regret upgrading to 9.10, it's been nightmares since I got here. I like the new look and feel, and a lot of cool little features over 9.04... but in the end all the functionality I had in 9.04 is completely gone. I guess this is what I get for upgrading so early. Question if a tarred my entire root folder (except for the home and mnt directories) would just overwriting that all back to the root put me back on 9.04? Or is that just a really bad idea.




on a second note, medibuntu servers are really slow tonight. I wonder what's up.

---

### Post by lordofduct on 2009-11-10
So ok

I uninstalled everything java related... and then reinstalled everything.

I can get most of Eclipse to work now... still some buttons when clicked don't work, but if I hit enter instead it acts the same as if I had struck the button (the way it usually works, as long as the button in question is the prime button in question).

So uh yeah, I think it's now down to Eclipse to locate what the hell this issue is.

---

### Post by lionstone on 2009-12-02
I'm having the same issue here on 64bit 9.10 - Eclipse has been all screwy since upgrade to 9.10 . I have the same problem with the buttons not working correctly on-click, but if you give them focus with the mouse and then use the spacebar or enter keys, it will work. Ugly trick but knowing that saved me :)

I'm noticing the same issue as you trying to install ia32-sun-java6-bin :
```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ia32-sun-java6-bin: Depends: sun-java6-jre (= 6-15-1) but 6-16-0ubuntu1.9.04 is to be installed
E: Broken packages

```

---

### Post by QIII on 2009-12-02
There is something to consider here, 32 or 64 bit aside:  Canonical has decided to move away from Sun's Java in favor of OpenJDK.  (Not a good move, IMHO).

The most recent version available in the repos is Update 15, which has a number of security flaws.

I believe Sun's most recent JRE is u17.

Here is a good article on getting the latest, and you can just install the 32 bit version if that is what you need for Eclipse.

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by lionstone on 2009-12-02
Hey thanks for the reply. I'm trying to do it except that now Synaptic is dead - sudo synaptic at a shell will just put the system in a hold, even after removing the dpkg lock. Uhh... once I fix that I'm going to try to follow that tutorial on the link. Many thanks for the help. Seems like others have a similiar problem but no great help. 

I am really disappointed with Ubuntu about this - there is no reason to be spending a day fixing Java, which was working fine before upgrade. I love OSS to death but I'm fine with using Sun if it'll let me get something done....

---

### Post by lionstone on 2009-12-05
OK. So for anyone else having this issue.

I encountered it upgrading Flex builder linux to alpha 5, on 64-bit Ubuntu 9.10:

- The first time I tried this I screwed up my entire 64bit distro bad enough to just give up and moved to 32-bit rather than re-install. ( Turned out to be a worthwhile decision overall, as I finally have the Flash 10 debug player working properly. But took way too much time.

- The second time I figured it out. There's actually a pretty quick painless solution.

I first removed sun-java6-jre in synaptic. 
Then I installed ia32-sun-java6-bin.

That's it. Solved the error mentioned here.

Then to upgrade Flex Builder: 
[http://benl.com/node/32](http://benl.com/node/32)

---

