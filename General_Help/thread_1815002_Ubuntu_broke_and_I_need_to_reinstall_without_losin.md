---
title: "Ubuntu broke and I need to reinstall without losing stuff"
date: 2011-07-30
forum: General Help
---

### Post by Dee_Ann on 2011-07-30
Help!

My Ubuntu is messssssssssed up!

I think, though I am not sure, that I was using 10.04.

For months it's been messing up and getting worse over time.
Lots and lots of problems that make me crazy.

Yesterday it just flat out refuses to boot anymore, it seems to be about the video card now.  I tried to have it boot into the failsafe low graphics mode and it says it can't lock a file or something.

Whatever..  There are so many problems with it that I can't tolerate it anymore.

Here's my super big problem though.  I have a LOT and I mean a LOT of stuff on that drive that I absolutely can not lose.

Lots of email, lots of photos, lots of personal and very important files.  Several terrabytes worth!

How can I reinstall Ubuntu so I do not damage my files and will be able to pick back up where I left off?

A long time ago I was using Suse and I could install a new version and it would find my old home directory and ask if I wanted to use it, I would say yes and bingo, all was well, everything would work as if nothing had changed.

I can not lose my stuff, my firefox stuff (bookmarks, cookies, passwords, etc) and especially my email (thunderbird)..

I don't have any objections to using a newer version of Ubuntu as long as it will still use Gnome as I was before and I don't lose anything in my home directory..

Please tell me what I can do, I'm trippin out over this...

Thank you!  :)

---

### Post by AgentZ86 on 2011-07-30
OUCH !

Well, this statement won't help you now but later it will.

You need Xmarks plugin for firefox so you never EVER lose your bookmarks again. Including any notes that you may put into your bookmark like when you right click the bookmark and you can put a few notes for yourself about that site etc. 

I believe YES that Ubuntu will install and you can keep your home folders but I would not do that as a dependency issue.

I would boot to a live Ubuntu CD copy all your stuff that you want to keep including your emails and images etc to another external USB drive or backup.

It's never EVER a good idea to count on your hard driver never failing because it will and does it's just a matter of time.

I'm sorry I can't answer more specifically because I have a small SME server and put everything on my server with dual mirror drives and external USB backup that is a backup of the server in case of a fire I can grab the drive and run out.

The server is a small desktop with 2 drives and one external usb drive. called SME server.

As I said that won't help you right now but perhaps in the future.

Only thing I know is to boot to a live CD or Flash/pen drive version of live ubuntu and copy all your stuff to some external drive.
Or copy to some online location you could zip up a lot of stuff and move to some either free hosting site or some other source that offers online backups.

But the main thing is that I would not overwrite anything until your sure the data is backed up to another drive so that you can install it or copy it back once you re-install.

Even if it does not overwrite this one day you will lose that computer or hard drive when it wears out and you will have to deal with this either way, sorry to say.

I hope this helps and happy hacking. 

P.S
You could also copy to another desktop once you boot to the live cd or flash drive. Perhaps a friend can let you store something in a folder if they have the space.

---

### Post by .... on 2011-07-30
And your backup is where..? I guess you don't have one, which is not wise.
If you have a separate /home partition, (re)installing Ubuntu and preserving your /home is straightforward. If not, break out your external hard disk, fire up a LiveCD, and extract as much of your data as possible. Let it be a lesson for next time that you should use a separate /home and keep regular backups.

---

### Post by Wim Sturkenboom on 2011-07-30
> **Dee_Ann said:**
> 
Here's my super big problem though.  I have a LOT and I mean a LOT of stuff on that drive that I absolutely can not lose.

Lots of email, lots of photos, lots of personal and very important files.  Several terrabytes worth!

Absolute bull.... if it was that important, you would have had backups.

> **Dee_Ann said:**
> How can I reinstall Ubuntu so I do not damage my files and will be able to pick back up where I left off?

A long time ago I was using Suse and I could install a new version and it would find my old home directory and ask if I wanted to use it, I would say yes and bingo, all was well, everything would work as if nothing had changed.
If you created a separate home partition when you installed Ubuntu, you can re-install without loosing the data in your home partition; in that case, make sure that you don't format that partition.

I would install the same version first so you will not encounter any compatibility issues where e.g. a newer thunderbird can't read the older mail files. From there create backups the 'official way'. I'm using evolution and just copying directories files does not seem to do the trick when restoring and one seems to have to use the built in backup/restore functionality; might be the same for thunderbird.

Having said that:
Use a live CD and external harddisk to first get your data backed up before you start with other things.
Next make sure that your hardware is OK; from your description you seem to have had plenty warnings that disaster was going to strike and you ignored them and as a result you're in the current situation (yes I keep on rubbing it in so you will make backups in future). This might indicate hardware that is on it's way out.

---

### Post by akakingess on 2011-07-30
Also, this is exactly why I use "Dropbox", it's only free for the first 2 GBs, but I can store at least my critical stuff there and it's available for Windows and Linux, kind of like a "cloud" drive that behaves like Xmarks. If you want, you can sign up [here]("http://db.tt/VvfE0SO")! At least it's a free 2 gigs, and you can upgrade from there.  Just a suggestion.

---

### Post by Dee_Ann on 2011-07-30
And just how do you backup TERABYTES?  Certainly not on CD's or even DVD's.

I didn't asked to get slammed for not having backups of terabytes of stuff, I just need some advice on how I can get Ubuntu working again without losing my home directories which contain a LOT of stuff that I absolutely can not lose.

I do not have an external disk.

I am able to boot from a DVD into live mode and see all of my stuff.

When I installed Ubuntu last year I set up partitions.

they are as follows:

sda1 - 200mb - fat32, it says this is the boot partition and is labled EFI, what ever that means.
sda2 - 750gb - ext4, files from years past I can not lose.
sda3 - 8gb - swap
sda4 - 50gb - /
sda5 - 1.1tb /home/[mystuff]


The problems I was having before were not hardware problems.  It was that the keys for installing any and everything were somehow broken and nothing I did would fix them.  It would tell me that all the software sources were unvalidated and it wouldn't let me update or install anything.  I found out I could go into synaptic and force installs and updates despite the warnings so I did that for a few months.

Then when I tried to update the Nvidia drivers it quit loading the graphics drivers.  So everytime I booted it would just come up in text mode.  I would have to try to kill the X server which was a pain, then reinstall the nivida drivers, they would complain that things were missing but it would still finish.  At that point I could type startx and it would start working.

It was a giant pain so I would just leave the machine running for weeks and months.

Then I tried to upgrade the kernel and it said it did but when I rebooted it it had deleted all the old kernel choices it used to show at boot and was only showing one really old kernel from last year.  I had no choice but to select it and then it would have a stroke over the graphics.  Nothing I would do would get it to work then.  It wouldn't even go into failsafe low graphics mode, it was complaining about a lock file or something.

Whatever...  The old stuff was messed up, software wise, not hardware.  I need to reinstall Ubuntu.  I'm going to get another hard disk to copy it all to next week but right now I'm really hurting by not being able to use my system.  I'm having to use a crummy old windows home theater system to get online here and it's garbage!

Please stop with trashing me for not having backups.  That doesn't help me at all, I need advice, not abuse.  

Thank you...

---

### Post by .... on 2011-07-30
Calm down. It's friendly advice to back up your stuff. You have a separate /home, so why not do a reinstall if you're having multiple problems that are beyond your ability to troubleshoot? Just make sure you do custom partitioning, select sda4 as the / partition, and select sda5 as the /home, but make sure the format box is not checked for sda5.

---

### Post by .... on 2011-07-30
Here's some screenshots. The guide is a bit outdated, as we now have ext4, but you get the idea.. [https://wiki.ubuntu.com/komputes/HowToUbuquityPreserveHome](https://wiki.ubuntu.com/komputes/HowToUbuquityPreserveHome)

---

### Post by IWantFroyo on 2011-07-30
I agree with .... (that's a nice username, by the way).

You can reinstall Ubuntu, manually partitioning it to use your old /home. Just tell it to mount it as your /home and not to format. Change the rest into free space, and make it your swap and /.

EDIT: Beaten by ....
That guide should work.

---

### Post by Megaptera on 2011-07-30
Hi Dee_Ann,
Could you buy external drive(s) or borrow external or borrow from friends/family?
Looking on Mr.Google it seems that 1tb externals are $80-$90 dollars or so. Not too much if you could use the live DVD to copy the important data across.

Richard.

---

### Post by Dee_Ann on 2011-07-30
The live 11.04 DVD lets me see all my files but it will not let me copy them.  I tried to copy the .mozilla and .thunderbird folders over to the windows theater machine and it tells me I don't have permission to read those files/folders.

I started nautilus from a terminal window using sudo so I should have root access and it still tells me I don't have permission.

I do have full read/write/create access to the windows share on the home theater.  I created a folder on it from the Ubu system.


Anyway..  So if I do an installation over the old system I don't have to worry about losing /home?

Back in the Suse 8/9 days I would reformat the boot, swap and / partitions but leave /home alone (lol @ */home alone* !).

It would ask me if I wanted to transfer ownership of the existing files there to me the new owner (duh), I would say yes and everything was cool.

I have never done that with Ubuntu and I'm really worried about messing it up.  It's a shame there's no write protect you can use..  

But really, backing up, yeah, I know I need to but there is so much I would have to use other hard drives.  And there is NO WAY I'm backing up to any online options.  That's not happening.  Ever.  There's just too much stuff and I do not trust the internet.  Way too many bad people out there..

Thank you...

---

### Post by Wim Sturkenboom on 2011-07-30
**This is what you want to hear:**
OK, you seem to have a separate home directory and another directory with important data; so you're reasonable safe with a re-install. I strongly advise that you invest the money and buy at least one BIG external HD and backup the data using a live CD before you start fiddling with the system; things CAN go wrong.
Next re-install as said before.

**And this is what you don't want to hear (no bashing or trashing):**
Yes, you can make backups of terabytes of data if you set your mind to it. What would you have done if you had a serious HD crash instead of this 'small' problem?

External drives ain't that expensive anymore. It's time consuming but you can start it at night.

Buy a second BIG external HD and rotate your backups. Store one off-site (bank, work, ...) in case your place get robbed (or worse) and bring the other one home for the next backup. After the backup is made, swap them again.

Good luck.


PS:
Validate your backups. It would not be the first time that somebody wants to restore backups and finds that they are (partially) corrupted for some reason. I'm familiar with one case where the head of an IT department got fired because of it (lost 10 years of email of 50% of the employees).

---

### Post by zero244 on 2011-07-30
Have you tried to boot in failsafe mode.

Its the second line down from the kernel line your booting from now.
Select failsafe and when the menu comes up select the failsafe video.
You could then go in and at least check things out.

You were smart to create a second partition for your home folder.......just make sure the format check box is unselected and your pictures and stuff should remain intact.

---

### Post by walt.smith1960 on 2011-07-30
The thought I'm having is we know what **size **the partitions are.  What % of the data partitions (SDA2 & SDA5?) are actually being used?  Unless you have a lot of DVD length videos, 10 GB is quite a bit of text/spreadsheet/email data.  I'd personally want to get backups by whatever means before screwing around too much.  You don't know how fragile the file systems may be.

Would something like this be helpful? SATA hard drive dock
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817153071](http://www.newegg.com/Product/Product.aspx?Item=N82E16817153071)

---

### Post by Dee_Ann on 2011-07-30
To answer the question immediately above, the partitions are pretty much ~full~.....

To answer another question, as I previously stated, yes, I tried to boot in failsafe mode and got error messages such as "Could not update ICEauthority file /var/lib/gdm/.ICEauthority" and it then locks up.  It would give me a graphics screen displaying the machine "name" and I could do absolutely ~nothing~ else.  It had also given me other error messages during boot in direct relation to the nvidia and gdm stuff.


I am running the 11.04 live dvd on the machine now and I can see all my stuff.  I tried to copy some of the important things like .mozilla and .thunderbird and it refuses to allow me, it tells me I do not have permission to access the files. :(


It will let me view the folders and their contents but that is all I can do.


So, all I can do is attempt a re-installation and just hope that nothing bad happens.  

But now I'm confused.  I do not know which version of Ubuntu I had installed.

My unreliable memory is telling me that I had 10.04 LTS installed.  But some message came up earlier and was telling me that I had 10.10

I have no memory of installing version 10.10
I dug through my stuff and found two 10.10 DVD's and I can find no 10.04 DVD's.

[B]So is there a way that I can boot from the live 11.04 DVD and examine the system I have and determine what version of Ubuntu I was actually running _without guessing_?  I want to reinstall the same exact version I had been using so that there is less chance of disaster.
[/B]


Thank you...

---

### Post by Dee_Ann on 2011-07-30
> **walt.smith1960 said:**
> The thought I'm having is we know what **size **the partitions are.  What % of the data partitions (SDA2 & SDA5?) are actually being used?  Unless you have a lot of DVD length videos, 10 GB is quite a bit of text/spreadsheet/email data.  I'd personally want to get backups by whatever means before screwing around too much.  You don't know how fragile the file systems may be.

Would something like this be helpful? SATA hard drive dock
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817153071](http://www.newegg.com/Product/Product.aspx?Item=N82E16817153071)


The drive is very near full.

And that gadget, looks very promising.  My pc does have esata ports so I could use this.  I'm assuming that you simply drop a hard drive into the gadget, backup then store your drive elsewhere.  I would love to see photos of it in use or even better a video.  But I think I understand it's use and I really think this would be a good investment.  2tb drives are less than a $100 so I could save up and buy a few of them to store my most important stuff on and rotate them every other month.  I have a fireproof safe I could keep them in.

Thank you for pointing this gadget out to me, I'm pretty sure I'll be seeing one of these in the near future sitting on my desk..  :)


edit: I found this gadget on Amazon and they had more and better photos of it actually in use.  Yes, I am definitely getting one of these and a few extra 2tb disks!  :D

---

### Post by Wim Sturkenboom on 2011-07-31
With regards to thunderbird, I found this [this thread](http://ubuntuforums.org/showthread.php?t=1815137) and it should be possible to simply copy the data.

---

### Post by Megaptera on 2011-07-31
Dee_Ann,
Glad to see things moving in the right direction.

Richard

---

### Post by walt.smith1960 on 2011-07-31
Re permissions. I've run into that.  I've typed in a terminal```
gksu nautilus
```  Then I was able to copy all files/folders/directories. I assume this would work on a liveCD session as well.  You do have root privileges when doing that you can delete or change things that will render your system even more unusable than it is now so think before you click.

Re the dock gadget yes it seems like a nice alternative for backing up larger quantities of data.  The thing you'd have to work out is how to safety handle and transport bare drives. Blocks of anti-static foam with cutouts for drives fit into a hard sided case?  I don't know if your eSata port would be active on a liveCD session.  I'd suspect it would be but I have no experience.  If the port(s) is active, eSata is WAY faster than USB2 and on a par with USB3.

---

### Post by .... on 2011-07-31
> **walt.smith1960 said:**
> Re permissions. I've run into that.  I've typed in a terminal```
gksu nautilus
```  Then I was able to copy all files/folders/directories. I assume this would work on a liveCD session as well.  You do have root privileges when doing that you can delete or change things that will render your system even more unusable than it is now so think before you click.
Better yet...
```
sudo apt-get install nautilus-gksu
```

---

