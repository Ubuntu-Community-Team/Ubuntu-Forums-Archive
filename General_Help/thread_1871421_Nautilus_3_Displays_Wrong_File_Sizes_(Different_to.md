---
title: "Nautilus 3 Displays Wrong File Sizes (Different to All Other Apps) Any Hack for This?"
date: 2011-10-28
forum: General Help
---

### Post by OzzyFrank on 2011-10-28
OK, first off, I know this has to do with the Mb vs MiB issue, ie is a megabyte 1000k or 1024k?, and that apparently the Nautilus developers have decided to buck the trend and go contrary to everyone else. Now, while I can respect them sticking by their new philosophy, there is no other way to put it but that this is a huge mistake, at least where I am sitting.

I mean, before I could download a file and in ~/Downloads it would appear as the same size. Now, the file sizes differ wildly. And every other program uses the size convention Nautilus doesn't, so (for example) when I open a "5.8Gb" file in DeVeDe, it actually turns out to be only 5.4. If you're thinking this is trivial, and I should just start using the calculator in my brain to determine the real file size (as shown in every other app than Nautilus), I can verify this situation can lead to "errors" that shouldn't be happening.

A really good example of this is a 4486Mb .iso image I just tried to burn. If you know about discs, 4488Mb is the physical limit of DVDs, so a 4486Mb image is fine, with a couple of meg to spare. Previously, Nautilus would show the file to be 4.4Gb (4.38Gb in Windows terms), but now is the 4.7Gb you see on blank DVD packaging. So, when I went to burn an image I had already burned before the 11.10 upgrade, I was informed the image was well and truly over the capacity of the disc, which it wasn't.

So, as you can see, this is now affecting me in other ways than just a general brainache. I know there's no easy way to change via settings (being given a choice would have been good!), so is there any way to hack this? I'm guessing it's hard-coded, but I'm hoping I'm wrong and editing a config file can rectify this. Thanks.

---

### Post by mjuhasz on 2011-10-29
First thing was to display correct unit sizes, that is, where base-2 sizes are marked with 'i' (MiB, GiB, etc.) and base-10 sizes with the usual SI units (MB, GB, etc.). This goal has been achieved with some exceptions (some command line tools, e.g. df, du, ls).
It also had to be decided where the size is displayed with SI and where with IEC units. Memory makers traditionally use IEC (base-2) units therefore in the System Monitor you'll see that you have 3.9GiB memory (note the 'i'). Hard drive manufacturers  and optical disks traditionally use SI (base-10) units so in the file manager you'll see that a one-layer full size dvd iso is 4.7GB (note that there's no 'i').
You can read more about the unit policy [here]("https://wiki.ubuntu.com/UnitsPolicy").

---

### Post by OzzyFrank on 2011-10-29
OK, so (for example) "Kb" doesn't exist, but can now be either KiB or kB... so does this mean that Ubuntu is adopting both? I guess what I am asking here is whether the uniformity of old is being replaced by apps choosing either IEC or SI, ending up in filesizes being represented differently all over the place? Or are all other apps going to follow suit and display them as base-10 like Nautilus?

And I should ask again, is there any way to change this so Nautilus displays them like EVERY other app I currently have? Or when it drives me nuts do I just start using Thunar or something?

The fact that basically every website out there works in base-2, not to mention other OSes, won't win Ubuntu any fans, especially if we have no control over the matter. This feels somewhat like learning to count again, as before I knew exactly how many Mb (sorry, I mean MiB) could fit onto a disc, etc.

---

### Post by OzzyFrank on 2011-10-29
Quoting the unit policy:

[B]For file sizes there are two possibilities:

    Show both, base-10 and base-2 (in this order). An example is the Linux kernel: "2930277168 512-byte hardware sectors: (1.50 TB/1.36 TiB)"
    Only show base-10, or **[COLOR="Red"]give the user the opportunity to decide between base-10 and base-2[/COLOR]** (the default must be base-10). [/B]

This seems the best option - give users control over how they want filesizes displayed. How hard could it be to slip this into Nautilus's *Preferences*? Hopefully all apps that display filesizes will implement this idea (well, once can dream).

Actually, I'd be quite happy seeing both, as in "**[COLOR="Red"](1.50 TB/1.36 TiB)[/COLOR]**".

---

### Post by OzzyFrank on 2011-11-19
So, there is no answer to this? This not annoying the hell out of anyone else? Simply put: Nautilus is the ONLY program showing me these sizes, so I'd really like to make it comply with the rest of the system. Yes, apparently Ubuntu's unit policy is to blame, but tell that to every single program (besides Nautilus) on my system. Not to mention the millions of websites.

---

### Post by SirWeazel on 2011-11-25
I just wasted more time than i would like to admit trying to download and burn ubuntu's iso file. I thought it was my download. The md5 checks were correct, but when i tried to burn it failed. I looked at the file size listed on the web site, the file reported by my download manager = both check out.  Then the shock!!! this 695MB file jumps to 729.1MB according to nautilus. I couldn't figure out what was going on. I re-downloaded the torrent, downloaded directly from the site, ect... but my file size kept changing after download to 729MB!!!

So after freaking tyring to trouble shoot my problem thinking it was my download, after reading this thread i now know i can begin trouble shooting elsewhere.

This really needs to be fixed, I try and recommend ubuntu all the time. In fact a family member is buying a new pc/laptop (old one is virus infested and several years old). I recommended wiping the old and installing ubuntu to reuse the old computer for awhile as a spare. But little things like this can possible cause me hours on the phone trouble shooting something.

I agree, nautilus is the only program showing incossistant files sizes relative to everywhere else. I can understanding trying to move to a standard, but is it worth the confusion when other polish, finess, and finetuning could be done to make ubuntu a better distro.  Especially if ubuntu is aiming at a simpliar computing option for everyone.

Why show file size one way in nautilus, but everywhere else on the system it is reported in another way?!?!  Not to mention everywhere else on the web it is reported as another way. If a size is listed as "N" on the web, listed as "N" on the download page of my browser, then listed as "N2" in nuatilus just makes life difficult.

Maybe i'm just bitter at the time i wasted (probably partly my fualt), but now i can go on to try other solutions why my cd's are not burning correctly!! - and i'm hoping it isn't related to this issue!

---

### Post by dcstar on 2011-11-26
> **OzzyFrank said:**
> OK, first off, I know this has to do with the Mb vs MiB issue, ie is a megabyte 1000k or 1024k?, and that apparently the Nautilus developers have decided to buck the trend and go contrary to everyone else.
........

There are two issues, the primary one is that Nautilus 3 is incorrectly displaying a MiB value as MB. The second issue is that MiB is not the "standard".

**You** should report this as a bug.

---

### Post by lisati on 2011-11-26
> **dcstar said:**
> The second issue is that MiB is not the "standard".
Exactly: no-one asked my permission for it to be standard either! :D

But on a slightly more serious note, it's only in the last few months that I've noticed people using the "MiB" convention, I'm not sure that it has caught on everywhere yet.

---

### Post by ambdeep on 2011-11-27
So is there a method of showing the value in MiB because it is easier to use since it is much more commonly used.

---

### Post by OzzyFrank on 2011-11-27
I dunno guys... looks like this is just not bothering other people. AMAZINGLY, everyone seems to be OK with Ubuntu's file manager displaying sizes completely different from every other installed program, and of course the zillions of web sites out there. I am well and truly shaking my head in disbelief...

---

### Post by SirWeazel on 2011-11-28
I think the way people are using there computer, no one notices it. It isn't until they need to inspect the size of a file, which probably doesn't happen too often. Most people are probably just searching the web, checking email, installing apps from software center, ect... and never needing to look at a file. If your music plays, pictures display, and people are just draging file around or using the built in applications they problaby wouldn't notice. Its not until a problem arises, or attention to detail until this issue is noticed.

But i am surpised with the amount of ubuntu users that are usaally a bit more tech savy then the norm (i'm just guessing, i have no stats to prove this), that this issue hasn't been noticed/complained about more. Maybe over time the issue will gain more popular with users "doing more?" --- Just my 2 cents, but it is more than annoying. I hope someone can post a simple fix or solution to this issue. I keep watching for an update to silently fix it :)

---

### Post by OzzyFrank on 2011-11-28
Well, I went to the effort of joining the Nautilus Bugzilla group, so now that the account is activated, will file a "bug report"... even though I don't really see this as a bug (but to me is more annoying than most of those, hehe). If Nautilus can be changed to show files as they were, I'm hoping someone will eventually point it out. More importantly, if base-10 is the way it's all going, then having the choice in Preferences would be great... decimal, binary, or both displayed together (I'd probably really like the last option).

---

### Post by OzzyFrank on 2011-11-28
The bug report I filed: [https://bugzilla.gnome.org/show_bug.cgi?id=665005](https://bugzilla.gnome.org/show_bug.cgi?id=665005)

---

### Post by OzzyFrank on 2011-11-28
Seems **g_format_size_for_display** could be the offender... but not sure why non-Ubuntu systems are affected, if this is because of the Ubuntu unit policy change. Even Nautilus developers are getting blamed for deliberately doing this, but I think it is just that it calls on **g_format_size_for_display** for file sizes. Whatever it is, I don't like it, hehe. And it's getting annoying reading Ubuntu developers saying how they made the most sane decision to go decimal, rather than be silly and follow the rest of the world. This has already cost Ubuntu many new (and I suspect quite a few veteran) users, so hopefully we are soon given the freedom to be able to choose, or Ubuntu will end up a laughing stock.

---

### Post by mc4man on 2011-11-28
> **OzzyFrank said:**
> 

A really good example of this is a 4486Mb .iso image I just tried to burn. If you know about discs, 4488Mb is the physical limit of DVDs, so a 4486Mb image is fine, with a couple of meg to spare. Previously, Nautilus would show the file to be 4.4Gb (4.38Gb in Windows terms), but now is the 4.7Gb you see on blank DVD packaging. So, when I went to burn an image I had already burned before the 11.10 upgrade, I was informed the image was well and truly over the capacity of the disc, which it wasn't.


Well then that's an issue with your burning app, if the iso can truly fit on a dvd5. At least here see no issue. Example using 10.04.3 iso in screen

In firefox it's shown as a 688MB iso which fits on a 700MB cd. 
Nautilus, brasero, & ImgBurn show the iso to be 721.1 MB (721,127,424 bytes) & will both burn to the cd whose capacity is greater than that - shown in ImgBurns r. side info - 736,966,656 bytes, 359,847 sectors. (the 688/721 MB iso is 352,113 sectors

I will check on a max size dvd5 iso, am confident of seeing the same thing so  don't really see any practical issue here other than with whatever you are using to burn with.

---

### Post by OzzyFrank on 2011-11-28
OK, the ISO issue was just one example, but it is an issue others have reported. Yes, if worse comes to worse, you can install other apps and go through them till you find one that isn't affected, but this is hardly going to do anything positive for Ubuntu's "just works" reputation, I'm afraid.

My major beef is that up until a few weeks ago, my file manager displayed sizes as **every single other app on my system** does, but most importantly, as the **zillions of web sites** display file sizes.

So now, when I download a "350Mb" file, I don't know if the "368Mb" in my downloads folder is complete or not, whereas before I could tell straight away just by looking at the size.

I think the Ubuntu development team are going to find it hard to convince millions of web sites to fall in line with their great new plan, so this will definitely cause a loss in the uptake of this OS (and I've already seen others dump it in favour of another distro). I mean, "the only OS in the world to display filesizes like this" is not going to be much of an enticement to newbies, hehehe! I think we refer to this as **[COLOR="Red"]Epic FAIL[/COLOR]** these days...

---

### Post by OzzyFrank on 2011-11-28
> **mc4man said:**
> don't really see any practical issue here other than with whatever you are using to burn with.

ZILLIONS of web sites vs Ubuntu trying to be clever...

The discrepancy between files sizes all over the world, on every site, created under every OS, basically makes Ubuntu's file manager look sorely confused. Try explaining base-2 vs base-10, and why it is a great idea to buck the trend the rest of the universe is following, to those who live in the real world.

---

### Post by SirWeazel on 2011-11-28
Couple questions... maybe someone can answer for me. And i still can't believe this isn't a bigger issue. From reading around a little bit... i'm a little confused. Is there a diffinative answer to these questions?

1. Is this a bug or was this change planned?
2. Is this a nautilus issue or ubuntu issue (ie. does nautilus on non ubuntu distro do the same thing)?

---

### Post by mc4man on 2011-11-29
Checking dvd's - your are correct as far as the one linux burning app I tried.
Brasero thinks the capacity of a dvd -r is 4.3X GB which is incorrect. It's actually 4.3X GIB. Whether that's ubuntu's,. gnome's or brasero's fault I wouldn't know though it seems like brasero should adjust.
 Nautilus reports the size of a .iso I tried  correctly - 4.7 GB (4,691,394,560 bytes)

Now a burner like imgburn looks at the byte/sector size of the iso & the available space on the dvd -r, (4,706,074,624 bytes/2,297,888 sectors) & will burn.


As far as brasero, it should use the same method for the source file size & media capacity, then it wouldn't matter which was used.

 I'd file bugs against any app that uses GB incorrectly... as far as dvd burning this is a regression with at least brasero

(- mediainfo does report correctly - 4.37 GIB
Taking a look at k3b - it use MIB & GIB so it also has no problems burning an iso that will fit like the one mentioned here

---

### Post by OzzyFrank on 2011-11-29
> **SirWeazel said:**
> 1. Is this a bug or was this change planned?
2. Is this a nautilus issue or ubuntu issue (ie. does nautilus on non ubuntu distro do the same thing)?

1. Read the bit above about **g_format_size_for_display**. It's what more and more apps rely on for filesize units. Obviously, not all do, hence most apps still reporting 4.38Gb for an iso but Nautilus reporting 4.7Gb.

2. Well, it's Ubuntu's unit policy change, so more apps will end up towing the line, but according to one person in the bug report I filed (link above), Nautilus currently shouldn't be one of them.

Also, one can't really single out Ubuntu as the bad guy here (or lunatic, take your pick), since I'm seeing people using other distros complaining about exactly the same thing. So is it then Nautilus... or Gnome 3... ?

Anyway, apparent Mac is going the same route, if it hasn't already, so seems the computing world at large is moving the clear up the confusion (someone mentioned Windows 7 is already decimal, but I wouldn't know). As long as web sites follow the trend, I'm OK with all that. But for Ubuntu to be leading the charge so early, when basically only the file manager is reporting those sizes, is silly and annoying, and doesn't do much for its reputation.

---

### Post by OzzyFrank on 2011-11-29
From the Nautilus developer, in regards to the question is this Ubuntu's fault or not:

[B][B][COLOR="Red"]I'm responsible for this change.  There is an extensive discussion in bug
554172.

I used to agree with your point of view and I was rather against power-of-10
sizing, but it's becoming increasingly difficult to defend that position.

First: using KB to mean "1024 bytes" is completely indefensible (since there is
no such prefix as "K").  Using MB to mean "1024 * 1024 bytes" is a downright
lie (since "M" means something else entirely: one million).  Either of these
are completely out of the question.  This was our previous behaviour and it was
very wrong.

So the question comes down to using "KiB" to mean 1024 or "kB" to mean 1000. 
That's a legitimate debate, but it's clear which way the wind is blowing on
this one.

Everyone who sells any kind of disk has switched to using base-10 units. 
Download speeds are also reported in base 10 units (and always have been).  The
only thing that's still in powers of 2 anymore is RAM, and Nautilus doesn't
normally report the size of objects in memory...  Add to that the simple fact
that base-10 units make more sense to the vast majority of humans.

The API introduced in GLib actually supports power-of-2 sizes, with the correct
units written.  Nautilus is electing not to use this feature (and correctly, in
my opinion).

I suggest you report bugs against the software in which you spot the
inconsistencies.  As noted, it's in violation of Ubuntu's unit policy, so
Ubuntu should be patching that other software, at least.

I feel our previous behaviour (although I was originally in support of it) was
a bug.  Our change of behaviour is, in my opinion, correct and well-reasoned. 
The change has also received a lot of positive feedback.  There is, therefore,
no chance that we will revert this change.

fwiw, I expect that Thunar will follow suit soon...[/COLOR][/B][/B]

---

### Post by lswb on 2011-11-29
No point in arguing with Gnome or Canonical developers. Right or wrong, they are always right! Or in this case, maybe even when they're right they're wrong? :)

---

### Post by resolv_25 on 2011-12-19
Thanks for pointing this out. I was just about to install Nautilus 3, after reading this, I won't do it.
In the whole debate, I'm not even sure why is this wrong measure adopted.
Hard disk producers are putting this wrong value for a long time (which has always been irritating). 
Will they try to convert the whole binary system into something else ?  :confused:

---

### Post by resolv_25 on 2011-12-19
Well, I see the discussion here: [https://bugzilla.gnome.org/show_bug.cgi?id=554172](https://bugzilla.gnome.org/show_bug.cgi?id=554172)
There is not consistency in measurement between disk space, network bandwith etc.
Still, I don't like this Mib because it is not clear how much space contain 1 Cd in this 'new' 10 base system.

---

### Post by emorkay on 2012-02-05
hi,

I don't understand this whole thing. Is memory a physical quantity? If it's then it completely makes sense to use prefixes conforming with SI standard. If it's not why can't we use base-2 sizes and the same prefixes as SI standard with a different meaning in this context?

But I wonder if there's a way to patch the current nautilus or a workaround to show base-2 file sizes.

Thanks,

---

### Post by MisterM on 2012-05-06
I have read a lot of discussion on SI (base-10) vs IEC (base-2) units and regardless of where one stands on this issue, I have one simple question. Seeing as the new default in Nautilus is to use SI units, **is there any way (setting, hack, whatever,...) to make it use IEC units instead?**

---

### Post by Chikitulfo on 2012-07-20
This is a **huge nonsense!**
In a binary system, the most natural way to show anything is in powers of two. Obviously. If disk manufacturers try to deceive consumers to believe they buy more space than what you really get, they are the ones to blame, not me.
But ok, I can understand that this debate is hard to take anywhere.

What I can't understand is: 
 - Then why the **** is nautilus saying it shows size in GiB but is actually showing it in GB!?  (see attachment, file is exactly 4.0 GiB but nautilus wants me to believe otherwise)

Isn't Ubuntu supposed to be about freedom? Yeah I like the freedom of not being able to choose which unit size my system should use and show me... (When it is a de facto standard).


PS: Since gnome 3 arrived I have much less freedom to use **MY** system as **I** want and personalice it a **I** like. They took away lots of optons and preference tools because apparently no one knows what i need better than the developers...

---

