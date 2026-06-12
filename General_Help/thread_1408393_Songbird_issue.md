---
title: "Songbird issue?"
date: 2010-02-16
forum: General Help
---

### Post by {Synapse} on 2010-02-16
I recently made the jump to Ubuntu 9.10 from Windows XP, and am absolutely loving it. This operating system is so much more customizable, and just overall more enjoyable, than WinXP ever was.

Even when I was still on Windows, I heard mumbling about an upcoming music player called Songbird and, being a rampant hater of Apple, was more than ready to look for a new music player. I tried to install it on Ubuntu recently and ran into a weird problem.

I used the instructions given here ([http://www.jonathanmoeller.com/screed/?p=1228](http://www.jonathanmoeller.com/screed/?p=1228)) in an attempt to install the program, but it doesn't install on the system. I can navigate to the executable in terminal and run it from there, but I was wondering why it wouldn't run like other programs do and if I was doing something wrong. I'm rather new to the operating system, so I'm not entirely sure how to go about properly installing programs yet.

Thanks for help!
~Synapse

---

### Post by howefield on 2010-02-16
Those instructions say to start it

> Next, you’ll need to run Songbird for the first time by either double-clicking on the Songbird file in the Songbird folder or by running this command from within the Songbird directory:

./songbird

If it created a shortcut for running it, it would likely have mentioned it, you could create one via System > Preferences > Main Menu and adding one into Sound & Video.

---

### Post by {Synapse} on 2010-02-16
Oh, so installing programs from a .tar.gz archive is different than installing a package in Synaptic or using apt-get? I figured they all means of doing the same thing; I didn't realize they ended up doing different things.

So I should just link to the executable on the Desktop/Application Menu/wherever else? Works for me.

---

### Post by howefield on 2010-02-16
> **{Synapse} said:**
> Oh, so installing programs from a .tar.gz archive is different than installing a package in Synaptic or using apt-get? I figured they all means of doing the same thing; I didn't realize they ended up doing different things.

Sometimes it will work/install the same way, depends on the application and packager, I guess, 

> So I should just link to the executable on the Desktop/Application Menu/wherever else? Works for me.

That would work.

---

### Post by warp99 on 2010-02-16
If installing Songbird the best thing is to set up the repository at [Getdeb.net]("http://www.getdeb.net/welcome/") so you can install that application through the package manager and have the latest updates available when released.

---

### Post by {Synapse} on 2010-02-17
howefield: Sounds good to me. Thanks for the help!

warp99: Would that be a more effective means of using Songbird than the method described above? I tried installing the getdeb package on the link you posted, but it didn't show any new packages in Synaptic. Was that what you were implying?

---

