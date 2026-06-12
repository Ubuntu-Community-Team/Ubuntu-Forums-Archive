---
title: "Nautilus-Image-Converter crashed my OS, trying to get permissions back."
date: 2011-09-09
forum: General Help
---

### Post by sick-of-ttfmscorefonts on 2011-09-09
First I installed Nautilus-image-converter. I lost all menus and bars... so naturally I uninstalled it. (been through missing stuff and uninstalled Compiz **** fest once before)

I was unaware nautilus-image-converter would try to redo my gnome. 

Now when I boot I have zero permission. I get the following errors.

**Could not update ICEauthority file /home/usar/.ICEauthority**

[B]There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)[/B]

If I try 

sudo chown test:test /home/test/.ICEauthority  Nothing happens, I get "sudo: unable to change to sudoers gid: Operation not permitted"


sudo chmod 600 /home/test/.ICEauthority I have not done because why would I if the first does nothing?

I would just format except when I run 11.04 off disk and try to transfer files they are all locked and there is nothing I can do about it. I would try to copy and paste but they will not do that.

I am going to lose my mind. I have stuff I need, in school, and some serious things to do that the rest of my life literally is balanced on. Either this **** works or I am going to be going through extra overload ******* hell. 

No I do not have another OS, no I can not afford one especially since I need access to pictures to sell things (digital photos on my computer). 

I hate Nautilus-image-converter creators. **HATE.** Give a warning if you can wipe someone's Gnome, and at least make it uninstall safe.

---

### Post by sick-of-ttfmscorefonts on 2011-09-09
Oh yeah firefox, software center, nothing opens.

I tried to install unity

sudo apt-get install unity

I get the Sudo: unable to change sudoers gid: Operation not permitted

I would like to try booting into the menu that lets you select different boot options etc but I have no idea what key gets me there. The only way to do it is somehow catch Ubuntu off guard with a restart or something forced. I have been unable to do that again by tearing the battery out or force restarting.... Nothing can get me back to that screen except the right key. No where on the internet can I find this information, even when I consider it to be one of the like most important piece of information EVER EVER ******* EVER to have, especially since repairing and stuff is done through it. 

I figured maybe in it I could run terminal commands and they might work. Also no internet unless OS is running because it is all wireless everywhere I go. It will connect currently, but no browsing or anything as I said.

I would be more than happy to format if I could just save any of my files.

---

### Post by sick-of-ttfmscorefonts on 2011-09-09
When I look at permissions running Ubuntu off CD, it says "1000" is the owner of all the files I would want to transfer.

I tried to make a new user called "1000" but it has to start with a letter so I am ****** on that.

---

### Post by coffeecat on 2011-09-09
OK, let's pick up a few points. :)

Do you also get an error about gnome-power-manager with this error?

> Could not update ICEauthority file /home/usar/.ICEauthority

There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)

If you do, this could be because your root partition is full. And if your root partition is full, that could explain most of the other problems you are seeing. Post the output of:

```
df -h
```

I very much doubt that nautilus-image-converter is the cause of all this. I've installed it routinely in my several last few installations and it has never caused a problem.

And that thing about user 1000. You UID in your permanent installation is 1000. But in the live CD session, the "ubuntu" account has a UID of 999 and there is no account with the UID of 1000, so when you look at the files on your hard drive, the live session has to report that as user 1000.

---

### Post by sick-of-ttfmscorefonts on 2011-09-09
I do not get that error. 

I will try df -h.

---

### Post by sick-of-ttfmscorefonts on 2011-09-09
df -h

Nothing important


/dev/sda1 53g size, used 39g, available 12g, use % 78, mounted on /
blank, 1.3g, 664k, 1.3g, 1, /dev
blank 1.3g, 168k, 1.3g, 1, /dev/shm
blank 1.3g, 220k, 1.3g, 1, /var/run
blank 1.3g, 0, 1.3g, 0, /var/lock

It was definitely Nautilus-image-converter that broke unity. Just like compiz, it made all the bars and menus go away. The moment I un-installed Nautilus-image-converter I was at the problem I have now.

---

### Post by sick-of-ttfmscorefonts on 2011-09-09
This is all taking a lot of time. If I could just figure out how to backup my stuff I will format...................

---

### Post by coffeecat on 2011-09-09
Yes, your root partition is not full enough to be a problem.

> **sick-of-ttfmscorefonts said:**
> 
It was definitely Nautilus-image-converter that broke unity. Just like compiz, it made all the bars and menus go away. The moment I un-installed Nautilus-image-converter I was at the problem I have now.

Hmm. You were unlucky then. I have nautilus-image-converter installed in 11.04 with Unity - posting from there now - and it didn't break anything.

About compiz making "bars and menus go away". Can you clarify what you mean? Unity is a compiz plugin so compiz itself wouldn't do that. Do you mean that you tried some settings in compizconfig-settings-manager and that broke Unity?

It's very late here and I must log off now. I'll look at this thread in the morning and see if I can think of anything else.

---

### Post by coffeecat on 2011-09-09
> **sick-of-ttfmscorefonts said:**
> This is all taking a lot of time. If I could just figure out how to backup my stuff I will format...................

I think I can answer that before I log off. :) I guess the problem you were mentioning in post #3 was that you got a permission error when you tried to copy your personal data using the live CD. That's because of the ownership issue I mentioned before. Your files in your installation have a UID of 1000 and the live account in the CD has a UID of 999.

The way round that is to open a root nautilus (in the live CD session) with:

```
gksu nautilus
```

Navigate to your home folder on the hard drive and copy your files.

---

### Post by sick-of-ttfmscorefonts on 2011-09-09
One day after an update all the bars with the X - and box went away on all windows that were not maximized (so the top bar becomes its menu bar) so it was impossible to save things or do anything that came up in a smaller window. I read compiz was the issue.

I went through searching stuff, uninstalled compiz and got a blank screen except my background image, no menus, no bars, nothing. And then I did unity --reset (I think) and then everything worked fine, everything came back.

After that I was looking to resize images.... 

After install nautilus-image-converter it would boot to a background image and nothing else what-so-ever. Then I did crtl+f and found software center, and went in and removed nautilus-image-converter which had a few things optionally removed with it. After that I boot into an environment with no background, no permissions, and no mouse unless I kick restart, wait a moment, then it comes up as a black X cursor and I cancel reseting to have a mouse.

To get on here I have to boot off CD.

---

### Post by sick-of-ttfmscorefonts on 2011-09-09
> **coffeecat said:**
> 

The way round that is to open a root nautilus (in the live CD session) with:

```
gksu nautilus
```Navigate to your home folder on the hard drive and copy your files.

Thank you, this is good enough for me!

---

