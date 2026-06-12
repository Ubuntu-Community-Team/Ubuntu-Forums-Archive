---
title: "New To Ubuntu - Not What I Expected"
date: 2009-10-30
forum: General Help
---

### Post by PaulyWally on 2009-10-30
I've been using Debian for a few years now.  I would in no way classify myself as a "knowledgable Linux user".  But I know enough to get around and use the CLI.

I jumped to Ubuntu [Studio 9.04] so that I could have more immediate access to certain multimedia apps that aren't quite supported on Debian.  I chose 9.04 instead of 9.10 on some recommendations.

In the last 24 hours, I reinstalled the OS 3 times.  When I ran some updates, some of them wouldn't install.  Later on, the update manager broke the system.  I tried to install OpenOffice and that turned into a busted install that destroyed Gnome.  Now, on my 3rd install, I finally figured out a way to get all of the updates installed, but now my computer won't do something as elementary as a shutdown or restart.  Over 70% of the time, Ubuntu hangs up on a shutdown.  The other 30% of the time it seems to work fine.

I'm not here to trash Ubuntu... but I'm left with a feeling of, "what the heck??"

I just want to know if this is normal for Ubuntu?  Maybe I am doing something wrong?  Is 9.04 just not that stable?  What the heck?

---

### Post by Iowan on 2009-10-30
Maybe I've just been lucky (so far), but I haven't had an update trash my system (though I've been a li'l shy to let my laptop update Jaunty). I did a distribution upgrade from Feisty to Gutsy (a while back...) that worked fine - upgrades are rumored to be more problem-prone that fresh installs. Maybe the big brick wall is waiting at the next install (I need to get Karmic on a machine), but so far, so good - for me, anyway.

---

### Post by P4man on 2009-10-30
> **PaulyWally said:**
> 

I just want to know if this is normal for Ubuntu?  Maybe I am doing something wrong?  Is 9.04 just not that stable?  What the heck?

If those problems would be "normal" then they would occur with the majority of the estimated 10M users, and somehow I dont think there would be 10M ubuntu users putting up with such issues. Then again if no one ever had any issues, there would probably be far more than 10M :)

Anyway your description of problems are rather vague, try and be a bit more precise and perhaps start by telling us what computer you are using.

---

### Post by shaggy999 on 2009-10-30
You mentioned you installed Ubuntu Studio and I do not believe that is managed by Canonical... Ubuntu Studio is based on Ubuntu and is downstream from the official ubuntu distro... so whatever changes have been made downstream may be the cause of your problems. You might want to talk to Ubuntu Studio people specifically.

The other thing you mentioned is that you tried to install OpenOffice... that seems strange as OpenOffice is included in the CD by default with regular Ubuntu. (K/X)ubuntu is another matter, and Ubuntu Studio as well.

---

### Post by red33m on 2009-10-30
I don't know mate...I use Ubuntu for qite a time now and they didn't leave me down even once...Of course I had to reinstall the OS when  I first installed it because I was taking the big step..From Windows  to Ubuntu...But when I learned how to work with it I didn't have many serious problems...so I think you just got unluvky..

---

### Post by P4man on 2009-10-30
> **shaggy999 said:**
> You mentioned you installed Ubuntu Studio and I do not believe that is managed by Canonical... Ubuntu Studio is based on Ubuntu and is downstream from the official ubuntu distro... so whatever changes have been made downstream may be the cause of your problems. You might want to talk to Ubuntu Studio people specifically.


Good point. Also studio by default uses the realtime kernel which is known to be buggy in combination with a lot of hardware (think its mostly bios incompatibilities)

To the OP; grab yourself a regular ubuntu, or install a regular kernel if you dont really need the RT capabilities. I even think studio provides non RT kernels by default, right in your grub menu, but I could be wrong. If a regular ubuntu works okay, you can just install all the studio apps on top by installing the ubuntu-studio metapackage.

---

### Post by PaulyWally on 2009-10-30
> **P4man said:**
> If those problems would be "normal" then they would occur with the majority of the estimated 10M users, and somehow I dont think there would be 10M ubuntu users putting up with such issues.

My thoughts exactly!

> Anyway your description of problems are rather vague, try and be a bit more precise and perhaps start by telling us what computer you are using.

When OpenOffice install failed, I could no longer access any menus in Gnome. Clicky clicky?  No worky.

Update Manager froze at least twice in the middle of unpacking & installing updates (the downloads had completed).

As for the shutdown problem, it's as random as it gets.  Shutdown hangs whenever it feels like it.  Sometimes it hangs with the GUI still up... sometimes with a blank screen and a flashing cursor... and sometimes, the PC speaker just beeps endlessly at me until I do a hard reset. :-k

As for the hardware, it's a home build:

ASRock P43Twins1600 Motherboard (Intel chipsets)
Intel Core 2 Duo E8400 Wolfdale 3.0GHz (socket 775)
2GB DDR2 1066 RAM
GeForce 8500GT 512MB 128-bit GDDR2 PCI Express x16
1TB SATA2 7200RPM Western Digital Cavier HDD
VIA OHCI Compliant 1394 Controller
Realtek 81xx series onboard Gigabit LAN
Realtek Onboard audio

...and that's about it.  My (outboard) DAW is not compatible with Linux so I don't have that on a perpetual connection to the PC.

Also, if it matters... I'm using the i386 install.

> grab yourself a regular ubuntu, or install a regular kernel if you dont really need the RT capabilities. I even think studio provides non RT kernels by default, right in your grub menu, but I could be wrong. If a regular ubuntu works okay, you can just install all the studio apps on top by installing the ubuntu-studio metapackage.

This was my next thought... but I've grown tired of all the reinstalls.  I feel better now that you've also recommended it. :)

[quote=shaggy999]You might want to talk to Ubuntu Studio people specifically.[/quote]

They keep sending me over to Ubuntu.com.  Go figure.  :)

And yeah, OpenOffice doesn't seem to be included with a default Ubuntu Studio install

---

### Post by ElTimo on 2009-10-30
Just out of curiosity, are you running 32 bit or 64 bit Ubuntu? I'm not sure if that will make a difference, but you never know.

---

### Post by sloggerkhan on 2009-10-30
You probably did something innocuous but wrong.
For example, with a fresh install of 9.04, there will be more updates than you can install at once because some of them may depend on previous updates, so you may have to run update a couple times to get them done.

That said, you experience sounds bizarre and reminds me of how one of my computers behaved when it had some memory start going bad. ACPI problems can also cause some weirdness. Might look into either of those things. So maybe it could be hardware thing, too.

---

### Post by PaulyWally on 2009-10-30
> **ElTimo said:**
> Just out of curiosity, are you running 32 bit or 64 bit Ubuntu? I'm not sure if that will make a difference, but you never know.

32 (i386)

---

### Post by ppirilla on 2009-10-30
That is a 64-bit processor, correct?

Did you get the x64 or the i386/i686 system?

You mentioned Debian.  Did you install Ubuntu on top of the Debian install, or onto a fresh partition?

---

### Post by simartem on 2009-10-30
i always install ubuntu on a fresh partition.. i never had a need to install any drivers for my hardware.. i solved and learned most of the things for my needs in ubuntu 9.0.4 and i never can compare it with MS.. Here is a screenshot from my paradise :) I never had a problem with any update or software.. It never locked up or refuse to shutdown, etc..
 
[img]http://img196.imageshack.us/img196/9572/desktopra.jpg[/img]

---

### Post by PaulyWally on 2009-10-30
> **ppirilla said:**
> That is a 64-bit processor, correct?

Did you get the x64 or the i386/i686 system?

It is 64-bit capable, but I installed i386.

> You mentioned Debian.  Did you install Ubuntu on top of the Debian install, or onto a fresh partition?

Nope.  I formatted the Debian partitions during install.

---

### Post by D1ZZ4ZZT3R on 2009-10-30
hey, simartem, what theme are you using, and where did you get it?

---

### Post by simartem on 2009-10-30
> **D1ZZ4ZZT3R said:**
> hey, simartem, what theme are you using, and where did you get it?
 
well.. actually its not a complete theme.. i use gnome-color-chooser to set the panel colors.. i use mashup icons. and wallpaper from gnome-look.org..
The screenlets are built-in.

---

### Post by faical117 on 2009-10-30
beautiful theme and icons simartem

---

### Post by PaulyWally on 2009-10-30
> **faical117 said:**
> I think that the problem in your machine :(

Could you expound on that?  If it is true, I'd like to know why you think so.  Because I never had any problems with any other OS I've run on this machine.  And I'm in WinXP right now and it's all hunky dory.

So, if you think there's something in my hardware list that isn't quite kosher, let me know.  And if so, is it the piece of hardware?  Or maybe it's a device that Ubuntu just doesn't like.

---

### Post by P4man on 2009-10-30
> **PaulyWally said:**
> Could you expound on that?  If it is true, I'd like to know why you think so.  Because I never had any problems with any other OS I've run on this machine.  And I'm in WinXP right now and it's all hunky dory.

things are rarely as simple as blaming the OS or the hardware. The same OS works great on other machines, other OSs work great on your machine. So who is to blame?

However, bios bugs often play a role in problems with linux, more specifically acpi implementations that are either incomplete or  compiled with microsofts known bugged acpi compiler and therefore only work properly with a windows OS that *expects* those bugs; unless those same quirks are implemented in linux. I talked to some linux devs a while ago who explained to me they had to reverse engineer bios's and or windows drivers to find those bugs and implement them in linux. Go figure.

Anyway, I dont believe you will run in to as much trouble if you stay away from the experimental rt kernels, but find out :)

---

### Post by PaulyWally on 2009-10-30
> **P4man said:**
> things are rarely as simple as blaming the OS or the hardware. The same OS works great on other machines, other OSs work great on your machine. So who is to blame?

I understand all that and that's why I was asking for clarification.  Like I said, I'm not here to trash Ubuntu.  But if someone says, *"I think that the problem in your machine"*... that doesn't help me.  What does help me is if someone said, *"Ah yes.  ASRock.  The BIOS in those M/B's are known to be buggy with Ubuntu."*

At this point, I'm just trying to get information from regular users so I'm not throwing darts blindly anymore.  Running a normal kernel, and staying away from updates (for Ubuntu Studio) are my two next steps.

We'll see.

---

### Post by simartem on 2009-10-30
> **faical117 said:**
> beautiful theme and icons simartem
 
thanks m8

---

### Post by P4man on 2009-10-30
> **PaulyWally said:**
> I understand all that and that's why I was asking for clarification.  Like I said, I'm not here to trash Ubuntu.  But if someone says, *"I think that the problem in your machine"*... that doesn't help me.  What does help me is if someone said, *"Ah yes.  ASRock.  The BIOS in those M/B's are known to be buggy with Ubuntu."*


FWIW I got an asrock board. And its a pretty crappy board which cost next to nothing, bios releases are like once every 4 years, but it runs ubuntu and other distro's just fine. Not that that guarantees anything.

> At this point, I'm just trying to get information from regular users so I'm not throwing darts blindly anymo

Sure. Just keep in mind the ones still posting here are probably the ones who havent ditched ubuntu so it probably works for them. Not the most unbiased crowd :) doesnt mean they cant help of course.

> re.  Running a normal kernel, and staying away from updates (for Ubuntu Studio) are my two next steps.

I just came across this:
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=18169](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=18169)

seems to confirm both our suspicion about the rt kernel as well as your trouble with installing OO. Grabbing a regular ubuntu cd should tackle both issues.

---

### Post by PaulyWally on 2009-10-30
> **P4man said:**
> seems to confirm both our suspicion about the rt kernel as well as your trouble with installing OO. Grabbing a regular ubuntu cd should tackle both issues.

Bonus!  [/crossingfingers]

---

