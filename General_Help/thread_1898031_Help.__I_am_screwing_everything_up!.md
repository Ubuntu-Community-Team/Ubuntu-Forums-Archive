---
title: "Help.  I am screwing everything up!"
date: 2011-12-20
forum: General Help
---

### Post by lintlicker on 2011-12-20
Hi,

I'm posting here because I am confused, and I'm getting myself deeper into trouble in my attempts to fix myself.  I am TRYING to run Dream Studio with it's packaged low latency kernel.  I've somehow managed to end up with Ubuntu 11.10 with a new kernel.  Also, my hard disk is getting partitioned into ever smaller pieces and I have probably 15 different kernels AND windows on my startup grub screen.  I've attempted to remove these other entries from that list, because due to a failed install of Ubuntu Studio, they no longer function, but I've been unable to.

Can you please guide me through untangling myself.  I just want to run Dream Studio with its kernel.  I also want to fix my partition situation so I just have 1 windows partition and 1 linux.  Also, if you could offer any guidance about how I can reduce the size of my windows partition, that would be great.  My windows is broken, so I can't boot it, but I would like to have the option to try and fix it again if in the future I decide to do that.

Thank you in advance,

Lintlicker

---

### Post by Megaptera on 2011-12-20
Hi,
Could you post a screenshot of your current partion set up? That'll probably be helpful. Are you able to boot in to both Ubuntu & Windows when you choose at start up?

---

### Post by lintlicker on 2011-12-20
Sorry, I don't know how to post a screenshot (and frankly, i'm too drunk to figure it out right now.  I'll try harder tomorrow I promise).  But I will communicate via text.

I used to have a 200-something gig windows partition, and the rest was linux.  Back when I had Malicious-Meercat (or whatever 10.04 was called) I knew how to look at drive info.  This new 11.10 has hidden these things from me.

Now I have a 167 gig file system, a 89 gig filesystem, and whatever my current install is running from.  The 167 gig is my windows partition, and my 89 gig is my old ubuntu 10.04 stuff.

I am unable to boot from windows because my MBR is totally and completely FUBAR.  I broke it trying to fix some kind of malware/virus and paying $10 for an iso of a windows boot cd is exactly $8 more than I'm willing to spend, especially when linux is equally powerful (but you spend more with the steep learning curve, i'm finding anyway).

I'm loving linux, and I want to make it work.  I'm only posting here because I think I'm starting to really mess some stuff up.

Long live PBR
</obnoxious rant>

---

### Post by QIII on 2011-12-20
I once got really drunk.  Wound up married.  Go to bed.  Call for th:lolflag::lolflag:e cavalry in the morning.

---

### Post by blackbird34 on 2011-12-20
To post a screenshot of your partition table, you need an application called GParted Partition Editor. If you haven't got it, then:

```
sudo apt-get install gparted
``` Once installed, open it (it will prompt for a password) and press on the button on your computer keyboard "print screen", (or use a screenshot app), you can save the image and then when you wish to post it on the Forum, under "Additional Options" at the bottom of the text box, there is a "manage attachments" button. 

All the additional kernels you say you have will still be only for one Ubuntu install if you only have one Ubuntu partition. There are ways of removing them:

1) Open Synaptic package manager (if you don't have it, ```
sudo apt-get install synaptic
```)

2) Search for linux-image as per my screenshot (attached). There may be a lot of them. I've got the 2.6.38-11 , 2.6.38-12 and 2.6.38-13 kernels , yours may be different. You can remove the ones you don't want, but keep at least one, of course:P

Hope this helps.



EDIT: +1 to QIII. The cavalry will come ;)

---

### Post by lintlicker on 2011-12-21
With the clarity of morning, I had the patience to punch "screenshot" into the unity app search field.  Here's the result

[IMG]http://i1036.photobucket.com/albums/a443/crazytbone/partitions.png[/IMG]
It's so pretty, and there's LOTS of partitions.  Too many.  Can I eliminate some of them?  How do I see how much free space is available on my drive?  Can I access my windows recovery partition to produce a recovery cd?  (If I can do that, I can uninstall all kinds of crazy crap from windows).

As far as removing kernels goes, I've done the search for linux images, but it does not give me the option to uninstall.  It only gives me the option to install, which is clearly the opposite of what I want to do.

When I booted this morning, my low latency kernel was gone, but there's still a ton of all kinds of other kernels beneath my windows boot option.

Thank you for your help.  I'm so confused.  I just wanna :guitar:

lintlicker

*edit
also, Firefox is VERY unstable now.  It's frozen and required force close at least 5 times in the last half hour.  Always in the middle of standard browsing activities, like clicking links.

---

### Post by grahammechanical on 2011-12-21
@lintlicker

Hi. I am not the cavalry. I do not even have a horse. I am beginning to like your style.

Let us try and get some order here.

1) Are you prepared to re-install your Linux/Ubuntu operating systems?

2) You do not need to have two swap partitions.

3) What Ubuntu operating systems do you want? Do you want Ubuntu 11.10 or an earlier version? Do you want to install Dreamstudio?

[http://distrowatch.com/table.php?distribution=dreamstudio]("http://distrowatch.com/table.php?distribution=dreamstudio")

4)I am guessing that the Ubuntu 11.10 is on sda7 = 39.51 GiB and that sda5 is the Dreamstudio OS = 83.35 GiB. Am I correctg? Or is it the other way around? Can you help here?

5) Keep in mind that whenever you recover Windows you will mess up the boot loader and may not be able to boot Ubuntu. So, we need advice on recovering the Grub boot loader after fixing Windows. I think that this is first priority.

Now, I must go shopping with my wife. Others will prove to be the cavalry.

Regards.

---

### Post by QIII on 2011-12-21
Are you particularly emotionally attached to any files in your Linux monstrosity?

(I suggest that before you do anything at all, you should use the Ubuntu Live CD to get to all of the files you want to keep and put them somewhere for safekeeping.  Always back up what you can't afford to lose before launching into something.)

I agree with the poster above that you should first get the mbr fixed in Windows.

---

### Post by lintlicker on 2011-12-21
*edit* I found my low-latency kernel!  I'm running it right now, and linux 11.10 still seems to be running.  I'm confused, but happy, because my sound works again.

graham:
1)  I am prepared to take any steps necessary to achieve a correctly configured stable machine.  I think my problem has arisen from me installing too many different versions of linux.

2) I do not know what a swap partition is or why I have 2 of them.

3) I like Dream Studio.  It seems to do what I want.  I just want a stable version of Dream Studio.

4)  Um......i dunno.  I'm not quite sure how to find the answer to that question.

5) Oh no!  I like linux!  I don't want to lose it!  I'd just like to recover windows so I can continue to use *one* program that doesn't seem to want to run in linux.  (And I have my reasons for not wanting to install it for wine)

QIII

I have exactly zero files in linux that I care about.  You could nuke my linux partitions from orbit, and I wouldn't shed a tear.

Bottom line:  I want to move away from windows.  If fixing windows is going to require any kind of real strenuous effort (or money) I'd rather just let sleeping dogs lie.  Linux seems to have WAY more to offer in terms of applications, security, and community.  I'm just trying to summit Mt. Linux-Learning-Curve and I'm getting a little tangled up.  I consider myself relatively savvy in Windows, but I'm finding Linux to be COMPLETELY different (but problems seem to be WAY easier to solve).

I might stick xPud or Puppy Linux on one of my flash sticks so if I brick my system (again) I can get on here and cry for help.

Thanks for the advice!

---

### Post by QIII on 2011-12-21
The Windows mbr (master boot record) can be easily fixed with a utility called fixmbr, which you can download.

That, however, trashes GRUB, so you have to use a Live CD to reinstall GRUB.

Fun, eh?

If you really only want Dream Studio (and Windows for that one program), you might best be served by collecting any files you might want (I bet if you look you will find some you do want to save, both in Windows and your Linux partitions), getting rid of your Linux partitions altogether, using the utilities in Windows to defrag, consolidate and resize your Windows partitions and then do a side by side install on the space on the disk that is left over.

But that is a pretty destructive route, so consider carefully before you go there.

(By the way, long ago when I was an Army Officer, I knew many other Officers who were Boot Lickers.  Are you related to them? :razz: )

---

### Post by lintlicker on 2011-12-21
No, unfortunately I cannot claim the honor of serving in the military.  Lintlicker is merely something that struck me as fun.

I do have many files in windows that I want to preserve.  I have lots of school documents, mp3s, pdfs, etc.  I'd like to restore windows merely to use that one program.  Everything else can just live on the windows partition until I need it.

So, reading over your post again, you're advising to fix windows, dump linux, defrag and reinstall.  The only thing that makes me nervous is that windows got broken in the first place by using an MBR repair program.  I seem to have some sort of infection that was sending spam to people, and my efforts to eliminate the infection led to a problem in the MBR, and the remedy for the MBR killed windows.

Did that make sense?  I can't remember the program I used, but I'll check out fixmbr, but won't run it quite yet.

--------
Didn't realize I didn't post  yet.  I can't seem too find fixmbr.  Lots of sites recommend using the Windows install cd (but I'm fresh out)  Can I make a recovery cd from my recovery partition?
Whee!

---

### Post by QIII on 2011-12-21
That doesn't sound pretty.  You may want to put it on the floor, pat it on the head, pull out your revolver ...

If your Windows is compromised, it may be best to make it go away as well and reinstall it.  Or, if you can get it up and running long enough to install several virus scanners and bot removers and malware exterminators you might be able to clean it up.

You may want to check the disk for rootkits, too.  There is a utility called chkrootkit (I think) that will do that.  I don't remember if it available on the Live CD, and I don't remember right off hand if it only works on the mounted drive.

But put your wanted/needed files in a lifeboat before you scuttle the SS Windows.  Do that first from the Live CD so if something more breaks you won't be even more frustrated.

First thing to do in any case (after backing up!) is to try to get the mbr fixed and fire up Windows to make an assessment.  If it rises and acts like a bot, you'll have to go through the drill of scouring it for malware.

---

### Post by lintlicker on 2011-12-21
chkrootkit found nothing.  I don't know if it scanned every partition, but it at least didn't find anything this time.

Still unable to locate any packages named fixmbr.  I'm debating ignoring my windows issue for the time being.  How do I go about cleaning up my partitions?  I'm going to sniff around for a while, but I'm getting the impression that this is something that should be straight forward, but I'm still confused.


__________________________________________

I've been screwing around, and I've located my windows recovery partition.  It's /dev/sda2.  Is there a way to create a windows recovery disk while in ubuntu?  I cannot find any tutorials or anything about this (I think I'm not asking the right questions)

---

### Post by lintlicker on 2011-12-21
*Still looking for help fixing my weird partitions.  Reward offered!*

If you help me fix my screwy partitions, I will write and record you a song.  That's right.  Your own song!  You can put it on your ipod and walk down the street to your own groove.

How bout them apples?

---

### Post by lintlicker on 2011-12-22
I'VE MADE AN IMPORTANT DISCOVERY!

Apparently, booting my windows recovery partition (/sda2) is THE SAME as running a recovery cd.  I had no idea it was that simple!  I didn't run the repair because I didn't want to trash Grub, but now I know that I can!

Is fixing my partitions equally stupidly simple?  Here's a pic to remind you.
[IMG]http://i1036.photobucket.com/albums/a443/crazytbone/partitions.png[/IMG]

And here's another pic.
[IMG]http://i1036.photobucket.com/albums/a443/crazytbone/imaginationcac.jpg[/IMG]
My photoshop skillz are mad good, yo.:guitar:

---

### Post by lintlicker on 2011-12-22
Ok, I'm pressing on in my battle against the partitions.  I used Disk Utility to delete some partitions, but Gparted seems to have disappeared.  Check it out:
[IMG]http://i1036.photobucket.com/albums/a443/crazytbone/gpartedisgone.jpg[/IMG]
As you can see, the ever helpful Ubuntu App Center is telling me to look for Gparted in a location that does not seem to exist.  Is this yet another stupidly easy problem to solve?

Also, I ran some kind of disk check using Disk Utility, and it informs me that my windows partition is NOT clean.  Heh, no **** Sherlock  \\:D/

I think I'm getting closer to my goal........I still have a messy boot menu and I'm not sure my partitions are better.  Any input is still welcome/requested.  

Thank you.

---

### Post by Ms. Daisy on 2011-12-22
First of all, you are a riot.

Second, I would recommend (like some others did) that you fix windows first. Using that recovery partition you discovered would be the easiest, although I think it would wipe everything else out.  Trying to hunt down all the viruses is a difficult chore and it's hard to know you got them all.

Third, to run gparted, you can type in a terminal
```
sudo gparted
```
If you don't know, you can open a terminal with the key combination ctrl + alt + T

---

### Post by lintlicker on 2011-12-22
First of all, why thank you.  I'm charmed. :)

Secondly <tantrum> BUT I DON'T WANNA FIX WINDOWS!!!  IT'S OBNOXIOUS AND I DON'T LIKE IT AND I'M SICK OF INSTALLING UBUNTUS!!!!  I JUST WANNA USE THE WINDOWS PARTITION AS DATA STORAGE!!!!!</tantrum>

For real though, I'm so sick of fighting with windows on this machine.  I think I just want to leave whatever's going on in that partition alone for now and just enjoy me some Ubuntu.  I have access to a few other machines that are running windows and have the applications I want on them.  Besides, as I meander through the applications on this machine, I'm finding other open source apps that will do the same job.

Anyway, gparted.  Duh, I keep forgetting that in Linux you can just punch in commands like that.  I'm still used to DOS where you need to be in the correct directory.  This is going to take getting used to.  Anyway, lookie here:
[IMG]http://i1036.photobucket.com/albums/a443/crazytbone/gpartedisback.png[/IMG]
As you can see here, sda1 is my windows hell pit, sda2 is the recovery partition, and sda3 is my linux, which contains sda5 for some reason with a good dose of unallocated space.  Oh, and see that extra little chunk at the end, that's unallocated too.  Gparted doesn't want me to grow my sda5 to take up that unallocated space though.  For some reason, it gives me a fun little non-nondescript error.  It might as well have said "Nah, Don't feel like doing that right now.  Why don't you try again tomorrow?"

---

### Post by Ms. Daisy on 2011-12-22
LOL
I guess what I'm suggesting is that you decide now how you want to move forward with Windows on this machine. If you want to repair it, now's the time to do it.  If you get the partitions sorted out & get a new snazzy Ubuntu and dreamy Dream Studio up & running, then it will be much harder to fix the Windows partition later IMO.  

Someone confirm this please: if you run Windows recovery it will automatically take up the whole disk, won't it?

---

### Post by lintlicker on 2011-12-22
I can confirm that running the recovery program does not wipe out the entire disk.  I can also confirm that deleting partitions all willy nilly is not a great choice.  I have successfully repaired my windows installation.  It was stupid easy.  It took probably 15 minutes for windows to do its scans and reboot.  It didn't even mess up grub.

I did discover that I totally broke Grub when I deleted some partitions, so I used a live usb and followed some youtube tutorial to restore grub.  Then I ran the recovery, and here I am, back in ubuntu making this post.

I'm debating going into windows and completely eradicating the linux partition.  I think I just need to start fresh.  I've already got a live usb of dream studio, and I've got a LOT of experience in setting up new installs.

There's also the problem that windows is infected with *something*.  I'd rather use it as little as possible until I get it clean.

---

### Post by lintlicker on 2011-12-23
So there's no shortage of tutorials about removing viruses using ubuntu, but it seems that most of them are obselete.  So, what would yall recommend for virus stompin?

---

### Post by haqking on 2011-12-23
> **lintlicker said:**
> So there's no shortage of tutorials about removing viruses using ubuntu, but it seems that most of them are obselete.  So, what would yall recommend for virus stompin?

It is better to do from a pure AV removal environment such as booting to a rescue disk.

[http://support.kaspersky.com/viruses/rescuedisk](http://support.kaspersky.com/viruses/rescuedisk)

Try that

---

### Post by Z06Gal on 2011-12-23
> **qiii said:**
> i once got really drunk.  Wound up married.  Go to bed.  Call for th:lolflag::lolflag:e cavalry in the morning.


lol!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by critin on 2011-12-23
> **lintlicker said:**
> 
[IMG]http://i1036.photobucket.com/albums/a443/crazytbone/gpartedisback.png[/IMG]
As you can see here, sda1 is my windows hell pit, sda2 is the recovery partition, and sda3 is my linux, which contains sda5 for some reason with a good dose of unallocated space.  Oh, and see that extra little chunk at the end, that's unallocated too.  Gparted doesn't want me to grow my sda5 to take up that unallocated space though.  For some reason, it gives me a fun little non-nondescript error.  It might as well have said "Nah, Don't feel like doing that right now.  Why don't you try again tomorrow?"


Actually, sda/3 is your extended partition, linux **is sda/5, which is inside** **sda/3**. (like an envelope)   You can put as many logical partitions inside of an extended partition as you have room for and want.

Did you try to delete the unallocated partition and then extend sda/5 into the larger space? 
That little bit of unallocated at the end isn't enough to worry about--I'd leave it alone if it was mine.  It's tiny and very close to your recovery.

---

