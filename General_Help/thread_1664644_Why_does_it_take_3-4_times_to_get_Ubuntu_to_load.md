---
title: "Why does it take 3-4 times to get Ubuntu to load???"
date: 2011-01-11
forum: General Help
---

### Post by CP2 on 2011-01-11
Good morning all. I've been using Ubuntu for about a week. Every time I reboot then I have to restart the computer 3-4 times in order to get Ubuntu to load. When it doesnt load I usually get stuck at the point right after the GRUB screen. The cursor just stays blinking. 
When I am successful at getting it to load then say "Too many connections" but still load successfully. Any idea whats going on and how to fix it?

---

### Post by TeoBigusGeekus on 2011-01-11
Are you using Maverick?

---

### Post by CP2 on 2011-01-11
10.10 is maverick right? (I'm new)

---

### Post by TeoBigusGeekus on 2011-01-11
It must be a bug in maverick, as I've found it on some of my friends' pcs, as well as in many threads in ubuntuforums.
No known solution (at least to me).
If you haven't done much customization in your system, I'd suggest that you switch to Lucid (10.04, long term support version, much more stable).
This problem is bound to be solved in the future with an update or something, but until then...
IMHO, Maverick is a disappointing release - there, I said it.

Sorry for not being particularly useful...

---

### Post by Quackers on 2011-01-11
If you would rather troubleshoot than re-install please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I can't promise a happy outcome but it may show something amiss.

---

### Post by piquat on 2011-01-12
Don't get hung up on the "Too many connections" error.  It probably has nothing to do with your problem.  I have it as well as many others and don't have any problems booting.  It may be actually related to HD audio.

Read post #12 in this thread:

[http://ubuntuforums.org/showthread.php?t=1635278&page=2](http://ubuntuforums.org/showthread.php?t=1635278&page=2)


Is the hard drive old?  I wonder if it's spinning up too slowly?  If it doesn't spin up in a certain amount of time it will give up detecting it, which *usually* gives an error about not finding the drive.

---

### Post by CP2 on 2011-01-12
I'm new to Ubuntu so I wouldn't know about 10.10 being a "disappointing" distro lol.
I did do quite a bit of customization, but I could easily do a back up of all important things and then import then if i do decide to go to 10.4 right?

And all of the parts in my computer are brand new and you just might be right about the HD audio, because the mobo I installed utilizes HD audio. I'm not at home right now, but when I get there I can display the error log results and see if anyone can make any sense of it.

On a similar note, in 10.10 I've noticed a few bug for sure. Like when I do a few things at once then certain windows will go GREY and freeze for about 5 seconds then resume.

My password protected screen saver magically got turned off by itself.

In desktop nova (wallpaper manager) I set it to start on startup, but I usually have to start it manually then delete the pointer to the file folder because it says that I have no files there when there are TONS! 

So hmmmmm, maybe 10.4 could be the way to go.

---

### Post by muteXe on 2011-01-12
10.04 yes. Personally if it's not a LTS I don't go anywhere near them, after some bad experiences with 9.04 and 9.10.

---

### Post by CP2 on 2011-01-12
> **muteXe said:**
> 10.04 yes. Personally if it's not a LTS I don't go anywhere near them, after some bad experiences with 9.04 and 9.10.

Alright, so then I have some questions:

1. What exactly is long term support? Is it basically what it says? sustained support until the next BIG release?

2. What features in 10.10 are missing in 10.4? I don't know much about Ubuntu, but I did a little ready. Is Gnome 3 is 10.4?

---

### Post by matt_symes on 2011-01-12
Hi

> **CP2 said:**
> Alright, so then I have some questions:

1. What exactly is long term support? Is it basically what it says? sustained support until the next BIG release?

LTS is supported for 3 years on the desktop with updates (5 years with the server edition). It is intended to provide stability.

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)
[http://tech.shantanugoel.com/2008/05/21/ubuntu-what-exactly-does-lts-mean.html](http://tech.shantanugoel.com/2008/05/21/ubuntu-what-exactly-does-lts-mean.html)

> 2. What features in 10.10 are missing in 10.4? I don't know much about Ubuntu, but I did a little ready. Is Gnome 3 is 10.4?

The main difference is Unity, but there are others such as the newer kernel. The differences are not huge.

Have a look at this.

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_10.04_LTS_.28Lucid_Lynx.29](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_10.04_LTS_.28Lucid_Lynx.29)

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1607517](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1607517)

Kind regards

---

### Post by Roasted on 2011-01-12
> **CP2 said:**
> I'm new to Ubuntu so I wouldn't know about 10.10 being a "disappointing" distro lol.


It's not a disappointing release. At all. It's been one of the better 6 month releases in the last 5 years that I've used Ubuntu.

But to be completely frank, LTS's are the way to go if you want stability. Each time I install a 6 month release, I install it knowing I MIGHT run into an issue. Rarely I do, though. But it happens. Less frequently with LTS's, of course.

---

