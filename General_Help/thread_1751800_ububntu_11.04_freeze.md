---
title: "ububntu 11.04 freeze"
date: 2011-05-07
forum: General Help
---

### Post by gaizman on 2011-05-07
hi,
i have upgraded from ubuntu 10.10 to 11.04 few days ago, and my computer freezes ones or twice a day.
it freeze with no clear reason, no connection to blank screen or something else, just freeze in the middle of any work.
the screen freeze and no mouse or keyboard reaction.
i tried using classic desktop but the same freeze happen here too.

my computer is dell latitude d520 core due t2400, 2.5 GB ram, intel on board screen adapter.

i would like any idea or advice what to do, thanks.

---

### Post by timgood on 2011-05-07
There is some evidence that this might be related to a Kernel problem with the default install. Upgrading the kernel has been reported to work and details can be found here: [http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0](http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0) but I can't vouch for this as I don't have the problem. 

Hope this helps.

---

### Post by gaizman on 2011-05-07
thanks, 
the kernal is upgraded as suggested.

i'll give it a day or two and come back with answers if it works.:D

---

### Post by leon_chame on 2011-05-07
Im curious on the update of this.

I have a freezing problem too, maybe two or so times a day the desktop just freezes.  You can move the mouse OK but there is no response to  anything though with the exception of going out to another virtual terminal which I have been doing (Crtl+Alt+F1) to shutdown.

@tim - Ive looked at the link you passed on but it seems this page specifically calls out that this is an issue while using Unity - which I am not as I running classic GNOME 2 - kernl 38.

Would be curious to hear if any other users not using Unity have the same problem...?

BTW,

I am running 11.04 base 64 bit install on a quad cpu IBM Thinkpad 410 - 4GB RAM, 400GB of disk space...I got lots of free resources...as for the most part I am running firefox, geany, terminal and evince thats pretty much it and all I have installed on this machine besides flash player and GIMP.

---

### Post by gaizman on 2011-05-08
hi,

the freeze happens also when i didnt used unity, but now i think that its gone.
so try to upgrade the kernel as he suggested.

---

### Post by apoorvumang on 2011-05-08
I am having the same problem. I'll try upgrading the kernel.

---

### Post by leon_chame on 2011-05-08
@gaiz - thanks for the feedback...Ill give the upgrade try also!

---

### Post by apoorvumang on 2011-05-11
Upgrading didn't work for me, there are still occasional freezes. :(

---

### Post by racie on 2011-05-12
Just bumping in to say that I have the same issue... except my screen becomes distorted until I switch to a virtual terminal and back again.  Happens in both Unity and Gnome Classic.  I haven't tried the update above.

---

### Post by Foxheadz on 2011-05-12
I had the same problem, so just to tried I did i fresh install and since then ive only had like 1 crash, that was a week ago.

---

### Post by racie on 2011-05-13
Sounds like good news.

I have my system back on now after numerous crashes, so I can try out the kernel update now.

I'll report back my observations later.

---

### Post by gaizman on 2011-05-13
hi,

i had a freeze or two since my last response so i guess it didnt work after all.
any way, i have heard that people that install it from scratch dont have that problem so maybe i'll just submit to that.

---

### Post by racie on 2011-05-14
Sorry for the delay in my response.

I found no luck after updating the kernel also.  It still freezes, but now the screen doesn't get corrupted when it does.

My install was "from scratch," with the exception of my /home partition.

I think I might head over to the LTS or switch distros.

*edit* Also... when was this marked as "solved?"

---

### Post by racie on 2011-05-15
Out of curiosity, I popped in the LiveCD to see if it would freeze after I used it long enough.  Sure enough, it did and I tried it multiple times.  Again, I could switch to a console using ctrl+alt+f1 and use that.

Right now, I'm testing the Kubuntu LiveCD and it hasn't appeared to freeze yet.  (The PC has been on all day.

I forgot to test the integrity of the ISO for Ubuntu, so that may have had something to do with it...

Anyway, just throwing that out there.

---

### Post by NormanFLinux on 2011-05-17
I've had no problems since I upgraded the kernel. The desktop no longer freezes solid when I connect to a wireless network.

Everything is updated on 11.04 and its rock-solid.

---

### Post by gaizman on 2011-05-28
hi,
i'm trying now the ubuntu classic (no effects) desktop and i think its better, no freeze yet, two days now.
not the regular classic, the no effect classic.

---

### Post by pamepros on 2011-06-06
I have the same problem on a dell inspiron 1525 it freezes a couple of times a day.
I did a fresh install except the /home dir. I'm thinking of going back to 10.10 or another distro. I was giving them time to solve it but it's been more than a month, usually they solve this things with updates but nothing yet. I waste a lot of time working with one crash an hour.
Someone has a different alternative for this problem?

---

### Post by Oxwivi on 2011-06-06
> **gaizman said:**
> hi,
i'm trying now the ubuntu classic (no effects) desktop and i think its better, no freeze yet, two days now.
not the regular classic, the no effect classic.
If disabling Compiz helps in anything try resetting it and go back to Unity to see if it helps:
```
gconftool-2 --recursive-unset /apps/**compiz**-1
unity --**reset**
```

---

### Post by linuxinstalledfromhdd on 2011-06-06
> **pamepros said:**
> I have the same problem on a dell inspiron 1525 it freezes a couple of times a day.
I did a fresh install except the /home dir. I'm thinking of going back to 10.10 or another distro. I was giving them time to solve it but it's been more than a month, usually they solve this things with updates but nothing yet. I waste a lot of time working with one crash an hour.
Someone has a different alternative for this problem?

I decided to do the same thing after I tried 11.04..  I'm running 10.10..  Here is guide to get your 10.10 up and running again pretty quickly:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

You should be ok after that.

---

### Post by gaizman on 2011-06-06
hi,
running classic desktop no effects dosn't work, still have freezes.

---

### Post by wissamshaar on 2011-08-31
> **timgood said:**
> There is some evidence that this might be related to a Kernel problem with the default install. Upgrading the kernel has been reported to work and details can be found here: [http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0](http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0) but I can't vouch for this as I don't have the problem. 

Hope this helps.


Updating Kernel solved the problem for me

---

### Post by TweFoju on 2011-10-01
that's weird

i tried kernel 2.6.39, even kernel 3.0.0.0300

still occasional crash

i am using Asus u36sd

i will try to go back to 2.6.38-8, see if it's more stable

---

