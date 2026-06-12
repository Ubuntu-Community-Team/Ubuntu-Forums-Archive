---
title: "Removed Graphics - Boots to tty1"
date: 2011-07-01
forum: General Help
---

### Post by TheCadaver on 2011-07-01
After months of another problem, which I blame on fglrx driver's issues with ubuntu, I removed my graphics card and sold it on ebay, I'm now going to buy an nvidia. however, after the removal, rather than booting into a login screen, it boots to a screen saying

```
Ubuntu 10.10 Neptune tty1

Neptune login:
```

Obviously, neptune is what i named my computer. upon logging in with my username and password,

```
Last login: Fri Jul 1 12:59:35 EDT 2011 on tty1
Linux neptune 2.6.35-28-generic-pae #50 SMP Fri Mar 18 20:43:15 UTC 2011 i686 GNU/Linux
Ubuntu 10.10

Welcome to Ubuntu!
 *Documentation: https://help.ubuntu.com/

New release 'natty' available.
Run 'do-release-upgrade to upgrade to it.
```

I've tried a few commands and generic updates, but I definetely do NOT want natty narwhal. 11.04 was terrible in my opinion, the unity setup simplifying everything fun about ubuntu... sickens me. Anyways, what to do? 

Also, I forgot to remove the fglrx driver before taking out the graphics card. may have been the source of the problen...

---

### Post by collisionystm on 2011-07-01
have you tried running

sudo service gdm start

---

### Post by knutschr on 2011-07-01
You can choose Ubuntu classic in the login screen after updating.
So there is no problem doing it :-)

---

### Post by TheCadaver on 2011-07-01
@knut

...have you seen what classic mode does to compiz? :p

it basically destroys it, and without compiz, I'll die

@collision yep.

---

### Post by TheCadaver on 2011-07-02
Bump

---

### Post by wildmanne39 on 2011-07-03
> **TheCadaver said:**
> @knut

...have you seen what classic mode does to compiz? :p

it basically destroys it, and without compiz, I'll die

@collision yep.Hi, I have a link that will fix the problem with compiz in classic, and I have another with a guide to install the cube and effects in natty with out breaking unity, I will give you a link for both.
[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html)
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

---

### Post by TheCadaver on 2011-07-03
> **wildmanne39 said:**
> Hi, I have a link that will fix the problem with compiz in classic, and I have another with a guide to install the cube and effects in natty with out breaking unity, I will give you a link for both.
[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html)
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

Well, I've also found natty to be slower, and I'd much rather have a legitamate 10.10 than a branched off classic version of 11.04. And why would I want  a "fake" 10.10 desktop with an outdated compiz when I could have the actual maverick meerkat?

I just want a Solution to this problem, No new OS, but as a last resort, Could I just re-install ubuntu 10.10?

---

### Post by TheCadaver on 2011-07-03
Well, I removed my graphics card (and sold it) without uninstalling the driver. Stuck on tty1 screen every time I log in, what now?

---

### Post by TeoBigusGeekus on 2011-07-03
Do you mean that the pc has no graphics card now?

---

### Post by prodigy_ on 2011-07-03
> **TheCadaver said:**
> I removed my graphics card (and sold it) ... what now?
Time to buy a new one? ;)

---

### Post by wildmanne39 on 2011-07-03
> **TheCadaver said:**
> Well, I've also found natty to be slower, and I'd much rather have a legitamate 10.10 than a branched off classic version of 11.04. And why would I want  a "fake" 10.10 desktop with an outdated compiz when I could have the actual maverick meerkat?

I just want a Solution to this problem, No new OS, but as a last resort, Could I just re-install ubuntu 10.10?Hi, sure you can re-install, I was just giving you options because the next release there will not be a classic mode at all.

---

### Post by TheCadaver on 2011-07-04
Currently buying it, but it won't solve the problem as I am moving from ATI to nvidia. Need to solve this and uninstall ATI fglrx driver I suppose, but how?

---

### Post by TheCadaver on 2011-07-04
> **wildmanne39 said:**
> Hi, sure you can re-install, I was just giving you options because the next release there will not be a classic mode at all.


Really? That's depressing... Honestly, after this, I might move from ubuntu to, I guess, some other Linux OS with gnome.

---

### Post by TheCadaver on 2011-07-04
Is there a way to simply re-install 10.10 through terminal commands? Or do I have to go through the trouble of creating a live disk?

Been without a computer for over a week because of this, it's painful :/

---

### Post by drs305 on 2011-07-04
Threads merged.

---

### Post by drs305 on 2011-07-04
> **TheCadaver said:**
> Is there a way to simply re-install 10.10 through terminal commands? Or do I have to go through the trouble of creating a live disk?

Been without a computer for over a week because of this, it's painful :/

You can boot the ISO from the Grub 2 menu (if you can get to it) and install from there if you don't want to burn a disk. Here is a guide on how to do it:
[http://ubuntuforums.org/showthread.php?t=1599293]("http://ubuntuforums.org/showthread.php?t=1599293")

---

### Post by wildmanne39 on 2011-07-04
> **TheCadaver said:**
> Really? That's depressing... Honestly, after this, I might move from ubuntu to, I guess, some other Linux OS with gnome.Hi, I was just answering your question, you asked if you could re-install and the answer is yes you can if that is what you want to do, I gave you the possible answer to your problem with a link but you did not say you even considered it, you just said
> Originally Posted by TheCadaver View Post
Well, I've also found natty to be slower, and I'd much rather have a legitamate 10.10 than a branched off classic version of 11.04. And why would I want a "fake" 10.10 desktop with an outdated compiz when I could have the actual maverick meerkat?

I just want a Solution to this problem, No new OS, but as a last resort, Could I just re-install ubuntu 10.10?

The link I gave you the possible solution, without the need to reinstall, I was trying to help you.

---

### Post by TheCadaver on 2011-07-04
> **wildmanne39 said:**
> Hi, I was just answering your question, you asked if you could re-install and the answer is yes you can if that is what you want to do, I gave you the possible answer to your problem with a link but you did not say you even considered it, you just said
The link I gave you the possible solution, without the need to reinstall, I was trying to help you.

You gave me the links to Compiz in 11.04 and proper Compiz in 11.04 classic mode. I want neither. I really, truly want to stay with 10.10, though or at least 10.04, that's LTS, right? Don't want 11.04, even on classic mode with all it's fixes, and especially if they're removing classic mode in future releases.

---

### Post by TheCadaver on 2011-07-04
> **drs305 said:**
> You can boot the ISO from the Grub 2 menu (if you can get to it) and install from there if you don't want to burn a disk. Here is a guide on how to do it:
[http://ubuntuforums.org/showthread.php?t=1599293]("http://ubuntuforums.org/showthread.php?t=1599293")

Followed the instruction in the "display menu" section, nothing happened.

---

### Post by gbestrada on 2011-07-05
Hi ,I hope you have not reinstalled yet, have you tried to switch to graphics mode whit ctrl+alt + f7 though you will get in low graphics mode ,then you can install your cards driver and avoid the trouble of reinstalling everything.:)

---

### Post by TheCadaver on 2011-07-05
> **gbestrada said:**
> Hi ,I hope you have not reinstalled yet, have you tried to switch to graphics mode whit ctrl+alt + f7 though you will get in low graphics mode ,then you can install your cards driver and avoid the trouble of reinstalling everything.:)

:o I'm burning a cd right now, good thing i haven't reinstalled yet :P

---

### Post by TheCadaver on 2011-07-05
> **gbestrada said:**
> Hi ,I hope you have not reinstalled yet, have you tried to switch to graphics mode whit ctrl+alt + f7 though you will get in low graphics mode ,then you can install your cards driver and avoid the trouble of reinstalling everything.:)

well, tried that, and it's been stuck on "checking battery state...", and stays on that each time I do ctrl+alt+f7.

So..?

---

### Post by TheCadaver on 2011-07-07
Bump

---

### Post by hawthornso23 on 2011-07-07
You don't have a graphics card. So you have onboard graphics. You should be able to get yourself functional by changing options in grub to tell it  to boot without loading the graphics driver.

---

### Post by TheCadaver on 2011-07-08
> **hawthornso23 said:**
> You don't have a graphics card. So you have onboard graphics. You should be able to get yourself functional by changing options in grub to tell it  to boot without loading the graphics driver.

Yes, I have integrated graphics ...but, I haven't the slightest clue how to do this. How would I manage this?

I don't quite understand grub.

---

### Post by TheCadaver on 2011-07-10
Bump

---

### Post by drs305 on 2011-07-10
> **TheCadaver said:**
> Yes, I have integrated graphics ...but, I haven't the slightest clue how to do this. How would I manage this?


I don't know if this is your issue or not, but to prevent modules from loading you can modify the kernel options in the boot menu. 

When the Grub2 menu appears (hold down the SHIFT key if it doesn't), highlight the desired Ubuntu entry and enter the 'edit' mode by pressing 'e'. 

Cursor to the end of the 'linux' line, remove **quiet splash** and whatever else is at the end of the line and add **nomodeset**

Press CTRL-x to boot. 

If this solves things, you have to make it permanent by opening /etc/default/grub and adding **nomodeset** to the "GRUB_CMDLINE_LINUX_DEFAULT=" line. Save the file and update grub. (sudo update-grub)

---

### Post by TheCadaver on 2011-07-18
thanks, I'll try that when I get back home.

otherwise, bump.

---

