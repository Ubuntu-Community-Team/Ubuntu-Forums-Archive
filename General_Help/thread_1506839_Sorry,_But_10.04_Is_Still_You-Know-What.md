---
title: "Sorry, But 10.04 Is Still You-Know-What"
date: 2010-06-10
forum: General Help
---

### Post by oldefoxx on 2010-06-10
Oh man, I go two weeks with Ubuntu 10.04 LTS on a laptop, and it really checks out pretty good.  Better than 9.04 in fact, and there is a version of VirtualBox ready for it, so I take the plunge, trying to get it on a second maching.

I say "trying", because I am into my third method now.  The first was to upgrade 9.04 to 9.10, and then upgrade from 9.10 to 10.04, all by the Update Manager.  Seems with each stage I have two choices.  The first is to either leave certain config file settings as they are or take some change from the packager.  Generally, I choose to stick with what works now.  The second is whether to delete aq bunch of packages at the end of the instal that will no longer be supported.  Don't know what they are, but I say go ahead and get rid of them.

This method works, to a point, but something just seems off.  Don't ask me to elaborate on that, I'm in overload with what has occurred since.  Note that this manner does not involve reformatting or reassigning any of the partitionss.

I decide it might be better to just install from the LiveCD.  I use the manual partitioner mode, and designate just the root (/) and swap- drive.
Can't reformat, because I want my /home directory and contents intact.
It seems to work, to a point, but I get the impression there are config settings somewhere in the /home directory that don't fit with the changed packages.  Hey, I got a right to keep what I've been working with and leave it to you to manage the rest of the upgrade, right?  Or maybe it is not in the /home directory, but in one of the other folder trees that might be left behind.  So how do I check that?

Decide to boot up one one present install, then got to the targeted partition for the next install and delete every folder except /home.  Let's see what that install does then.  Oh boy, that one is really trashy.  The only devices that start with "c" found in the new /dev folder involve chars:  That means the CD drive isn't seen any more.  I guess I will have to try a real install, with a partition formatting, and see how that goes.

Oops!  That is definately the worse.  Seems that the Grub-whatever that Ubuntu is currently using keeps getting an error at the end of the install, and the only choice after retry fails is to abort or do without a bootloader.  Could not ever get around this error occurring, no matter which partition I designated to accept the bootloader, so in desperation I just went without.

And of course I cannot boot up now.  The assumed default, which is the last install, has not been updated to the new UUID code, and since it is the one and only one grub goes with, I can't boot.  But it does drop me into a grub rescue> prompt.  Only nothing works there.  This is suppose to be an early version of grub2 , right?  So I find my way to the Wiki on Grub2, and it tells me all these commands I now have to use with Grub2.  Only trouble is, this isn't Grub2, and I found that only five of the commands are incorpoarted.  These are:

ls
set
unset
root
exit

Now the only thing that ls -l tells you is what drives and partitions that grub sees.  In my case, it is
(HD0) (HD0,3) (HD0,2) (HD0,1) (HD0,0)
(HD1) (HD1,2) (HD1,1) (HD1,0)

But what good is that?  I can't determine the assigned UUID tag for any of them, because that does not work.  I can tell it which partition to use as root, meaning where a working /boot/grub might be, but the boot command does not work, so that goes nowhere.

These people are so proud of the decision to switch to the UUID for each partition as a way of identifying it, but a new UUID will be assigned randomly every time that partiition is reformatted, meaning not only deleted and restored, but resized or moved.  Now if there were just some way to tell the reformat process to retain and reuse the existing UUID, that might help, to to tell it what UUID to substitute, like maybe one that has your user name and today's date embedded in it.

But obviousle grub did load when I booted up, and if the  UUID was bad for one partition, it could have given me a range of choices, like this:

(1) go with the next boot option instead
(2) use this option, but on a temporary basis
(3) replace the UUID in grub's option list, and try again
(4) take the UUID that grub has in it list and replace the UUID in the partition with it.
(5) Have grub defer to the /boot/grub process on a designated partition

Those are just some ideas about how it could be done to prevent the grub rescue> event from occurring, or coming back.

I would also be interested in learning why the 10.04 LiveCD just could not seem to update grub on any partition without an error occurring.
It happens that (HD0,0) is NTFS, with Windows installed.  The other partitions are a mix of ntfs and ext3 intermingled

---

### Post by oldefoxx on 2010-06-10
First, let me correct something stated above.  Grub rescue> does not rMy ecognize exit or quit either.  Seems to be about a dead end, but you can always power off to get out of the sticky spot

My wife mentioned I could just go back, couldn't I?  Yeah, butg that would be a bit of a waste, right?  But then it occurred to me, that if by going back to 0.04 it brought grub into alignment again, maybe I could go from there back directly to 10.04.  As long as I avoid formatting the partitions again, it might straighten itself out.  Won't hurt to try, I suppose.  Better than sitting on my hands and waiting for a reply.

So we will see.  Love it when they get it right the first time around like this. Oh, and from the bit of reading I did, the real grub2 won't be much better.  Some discussion about a grub3 later on.  .

---

### Post by wilee-nilee on 2010-06-10
You could have avoided all this with two methods. #1 a separate home and a fresh install #2 all the important data on a external HD and a fresh install. The problem isn't the OS it is the user.

You may have mentioned something in the post but it is full of irrelevant stuff that makes it a hard read, being that your frustrated rather then getting to the point.

State what you want and where your at.

---

### Post by oldefoxx on 2010-06-11
I'm not sure what you mean by a "separate home", unless you mean to set up a second partition just for /home.  I guess that could work, but why should I have to?  I mean, if they want it to install a certain way, then just make it do that without bothering to ask me what I want. I turned on the PC that I was working on last night, and it booted up, no problems indicated.  Nothing I found to do last night would make a go of it.

Must be grimlins running around here to fix or break things.  I say "breaK", because my notebook with 10.04 on it for more than two weeks, suddenly reported that it could not find a file nammed "work", so it just hung.  Pushing Esc did nothing, but as soon as I pressed the Power button it jumped right on into Ubuntu.  Seems to be doing okay at the moment, but I have no idea of what is causing all this.

I stated with the 9.xx builds that I was having a problem with trying to install more than one copy of Ubuntu on the same PC at once, that there seemed to be some overlap when it came to whether to put some of the root folders on the drive I designate, or use what might be on another partition already.  As far as I know, the critical folder for users is /home, and if you can keep that intact and/or separate, you might be fine with multiple installs.  But that is just a guess on my part.

Anyway to keep it apart, I figured either renaming .home or putting it as a subfolder under another folder might work.  But in order to do this, you almost have to copy /home to some other partition or drive so that you can reformat the intended partition or drive.  I thought of just doing something like this:

mkdir /keep
mv /home /keep

But though quick, it leaves everything on the same partition, meaning you cannot reformat it because you would lose it all.  And moving tgo another drive or partition can take quite a while.  Then of course you have to move it back, and apparently there are settings under user accounts that maybe should not be brought back at this point.  There just is no clear one way to work around these issues.

Ubuntu and Linux, both show a certain heritage from Unix in ierms of command line syntax.  The GUI works pretty good for many file processes like copying with a copy and paste, moving with a cut and paste, and renaming files, or creating new folders.  There is no drag and drop like with windows, but in the command line it is way harder to do.  You have to give the complete source reference and complete destinaton reference to try to do things like copy or move, which means a lot of typing.  Now Windows makes some of this much easier.  If I give a course as c:filename and a destination as just D: then we are taking advantage of a certain feature in DOS and Windows called the Current Directory.  If I only give a drive or partition referencfe, it is always understood that I am referring to the current directory for that drive.  And I can change the current directory on any drive to be the directory or folder of my choice.

While Windows does indeed incur some problems by using letters to refer to drives, it does have the advantage of simplifying many command line statements.

But back to Ubuntu 10.04 LTS.  The desktop and windows that come up are a bit odd, being black, while, and purplish.  Seems they decided to use a Custom Theme for Appearance, under System, and it is not quite right.  Trick is to select a different appearance, and then it will look like you expect it to.  I think it was even keeping the minimize/maximize/exit buttons from showing up on some windows corners.  Although there were often equivalent buttons on the upper left side.

One thing that was emphasized in the coding community years ago was that code must produce expected results.  That means stability over everything else. Speed is important, to a degree, but not if the results cannot be trusted.  Some also refer to the need for stability as an need for reliability, meaning you can trust in what you get if you use it.

---

### Post by doas777 on 2010-06-11
howdy,
"separate home" refers to keeping your home directory on a separate partition and mounting it to /home. that way you can easily rebuild, formatting / but not your /home partition. see more here:
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
and here: 
 [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) 

it will save you from having to go through this again. 

my best advice is get an external drive or net share or something, and back up your user data (just your user files, not the whole profile) off the Pc. then install from livecd, using the first tutorial above to create a separate home in the process. then just copy your backed up files back. 

just as a general rule, almost any post that is more than 3 paragraphs in length will not get read.  refine and revise. use a descriptive title, and try your best to clearly and succinctly state the problem you are having or the question you want answered. a good posting style is important to a good forum experience, and to getting your questions answered.

---

### Post by wilee-nilee on 2010-06-11
I guess what I'm trying to point out is that if you attach a usability to any OS, whether open or proprietary, you will probably be upset with it at some point. It is an inanimate object that does not fit in every set up of the mechanical part=hardware, or user breakage.

Personally I find what works for me, and if it breaks or stops working I find another that does. With 100's of open source possibilities, chances are you will find one that works for you, but this takes work. Some don't want to work at this and want a magicbox,which is okay, but if this is your goal you have to realize this is not really possible and be prepared. I'm not saying that you want a magicbox, but I suspect a majority of users do.

Personally I don't use the separate home method to insure safety with irreplaceable media. I have it off my computer on a external HD so all I have to do is pop in the install media and I am on my way. I don't do backups or clone my OS. I know what I need and I know how to get it and apply it to any OS I choose to use. I only suggested this as a possibility as many people use this method. To devalue it with the argument that "why should I have top do this"? to me makes no sense, there are other methods as the one I use and others as well like cloud computing. You also have to just have a set of precautions that insure the OS viability, and the protection of what you don't want to replace.

I only get upset or get an attitude towards objects that can respond, or at the least a pseudo realization, a thinking object. Getting upset or frustrated with a inanimate object is applying our personal limitations to the object. These personal limitations are also applied to animate objects, but it is the realization of this that may set you free or give you a better understanding of the situation,and yourself.

---

### Post by jerome1232 on 2010-06-11
Along with doas777 line of thought I actually go a step farther than that and keep a separate data partition that contains all of my media (music, pictures, videos etc...)

It contains all of my files that I keep between installs and has no configs what so ever so has no chance of breaking future installs.

Computers being complex things do have a tendency of being subject to gremlins, just keep that in mind and roll with the punches.

---

### Post by stinkeye on 2010-06-11
> I only get upset or get an attitude towards objects that can respond, or at the least a pseudo realization, a thinking object. Getting upset or frustrated with a inanimate object is applying our personal limitations to the object. These personal limitations are also applied to animate objects, but it is the realization of this that may set you free or give you a better understanding of the situation,and yourself.

I had a flashback to the old "Kung Fu" series while reading this.
 Master wilee-nilee: "I seek not to know the answers, but to understand the questions".

---

### Post by wilee-nilee on 2010-06-11
> **stinkeye said:**
> I had a flashback to the old "Kung Fu" series while reading this.
 Master wilee-nilee: "I seek not to know the answers, but to understand the questions".

And my answer would be, the answer is within grasshopper.;)

Edit; and in the quantum state the mass has more free space then solid matter.

Hey I didn't choose the name fur nuthin, we resemble our on line names more then we may realize.

---

### Post by stinkeye on 2010-06-11
So is it...
wily-nilee ......marked by skill in deception; cunning men often pass for wise
willy-nilly....in a random manner
:confused:):P

---

### Post by oldefoxx on 2010-06-11
Unfortunately, it just gets worse.  Isn't that usually the case though.

Grub won't update with 10.04.  It also seems to be undocumented, in that it is neither Grub1 nor Grub2.  That pretty much means you stay at a loss as to how to fix it or get around it.  I decided to try and revert to grub, which I was able to do in part, and that removed grub-pc.  But installing grub did not bring with it stage1 or stage2, so while I have a menu.lst now on one of my parttions, it does not fly.

To me, this just makes no sense.  Why do you want to make things super tough on people you are trying to get to use your software, or at least give it trial.

---

### Post by wilee-nilee on 2010-06-11
> **stinkeye said:**
> So is it...
wily-nilee ......marked by skill in deception; cunning men often pass for wise
willy-nilly....in a random manner
:confused:):P

You don't approve of my pho philosophy, what will I do with myself, now. :guitar:

---

### Post by wilee-nilee on 2010-06-11
> **oldefoxx said:**
> Unfortunately, it just gets worse.  Isn't that usually the case though.

Grub won't update with 10.04.  It also seems to be undocumented, in that it is neither Grub1 nor Grub2.  That pretty much means you stay at a loss as to how to fix it or get around it.  I decided to try and revert to grub, which I was able to do in part, and that removed grub-pc.  But installing grub did not bring with it stage1 or stage2, so while I have a menu.lst now on one of my parttions, it does not fly.

To me, this just makes no sense.  Why do you want to make things super tough on people you are trying to get to use your software, or at least give it trial.

It's hard to tell where your at, and whats been done. You might state this and post the bootscript in code tags so those that know may help.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

If you have reverted to grub legacy you have to remove all of the grub2 files, if I am understanding you.

---

### Post by oldefoxx on 2010-06-12
Man, I am trashed now.  Caught between grub1 and grub2, this system is no longer bootable, and trying to do anything with grub or grub-install just tells me that I've no bootable drives or they are not block devices.  Trying to read the grub instructions to straighten this out is a nightmare, because everything points off to another place, like a device map file, which might actaally go by that name, but who can tell?  Ubuntu 10.04, which has done fairly well as a single install on the notebook, is bleeding all over if you attempt multiple installs on one PC, and I was just trying to do a second one as sort of a back up if the first one dies,  Last I saw of it, Ubuntu and VirtualBox were apparently slugging it out behind the scenes and the front end was frozen completely.

Meanwhile, if I get back up with the LiveCD, half the partition names are gone or won't display under Places, so I have to guess by size or mount one and see what shows up under /media. Usually just disk, or disk-1 if I left the last one mounted.  I do a search, even use grub's find, and it turns out that there is no /boot/grub/stage1, stage2, or anything akin to them left on any drive.  Fact is, there is no /boot either.

And here I was just telling family and friends what a great move to Ubuntu I had made.  That should show me,  Now let me see, they used to recomment that with new software releases, you never go for the first version that is identified with a .0, but wait for the first round of patches and fixes that will put it up to at least .1.  I'm trying to figure out how many Ubuntu releases to stay back to try and be on the safe side.  Right now I'm inclined to say more than two, like maybe four.
Maybe LTS has some hidden meaning as well, like Lick Their Sores, or in this case, Lick Those Stumps, because that is about all I have left.

Not really funny you know, but a push for a bit of humor at a time like helps us keep going.  And going and going and going?  I hope not.  Sometimes you just want to get there, even if just for awhile.

---

### Post by chayzer on 2010-06-12
Boot off your LiveCD, open your partition in places, when the file browser pops up press ctrl+L and take note of /media/yadda-yadda-yadda.

```
cat /etc/mtab | grep /media/yadda-yadda-yadda
```

That should give you a /dev/something_something

```
grub-install --root-directory=/media/yadda-yadda-yadda /dev/something_something
```

If you have anything bootable left on that hard drive.. that should find it.

---

### Post by wilee-nilee on 2010-06-12
> **chayzer said:**
> Boot off your LiveCD, open your partition in places, when the file browser pops up press ctrl+L and take note of /media/yadda-yadda-yadda.

```
cat /etc/mtab | grep /media/yadda-yadda-yadda
```

That should give you a /dev/something_something

```
grub-install --root-directory=/media/yadda-yadda-yadda /dev/something_something
```

If you have anything bootable left on that hard drive.. that should find it.

Oh really with a mixture of grub-legacy and grub2 and a bunch of tweaking we don't even know about.

Run the bootscript.

---

### Post by oldefoxx on 2010-06-12
[B]Now that us interesting.  I posted, according to the time lapsed indication, just seven minutes ago and someone has already seen fit to delete my choice or use of words.  I would not by chance be someone from the PR department for PB, would it?  And I was being rather nice about the whole thing.  I only mentioned that the PC was now trashed once,

Reason I am back though, is that I decided to go to my VDI client and chekc on email before heading for bed, because I have been too caught up in this mess to bother checking if for nearly a week.  You would never guess what I did not find, so I will just tell you.

My install of the Oracle VM VirtualBox has just vanished from the laptop,  I'm not kidding.  There is nobody here other than me that is capable of doing something like that, and I sure didn't, so I am stumped by another strange thing taking place.  So mow I have three factors to deal with:

(1) Somehow make the PC I've been working on bootable again, because the grub mess has really wiped out its boot capabilities,  Grub cannot find any bootable or block devices to install to.

(2) Whatever mess has been taking place in the background finally came to a fore when the PC just froze,  It was like Ubuntu and VirtualBox locked gears with each otxher.

(3) Now what to do about the sudden vanishing of VirtualBox from the laptop.  I need to do something, just don't know what it will be yet. [/B]

Nah, I was definately wrong about the eliminated post this time.  When I wrote the above, ir was not posted.  After this got posted, I went back and it was there. So between the two of these, you pretty much have the whole of it.

The partitions still hold stored data.  But it now seems I have a mix of grub1 ahd grub2 intertwined, and don't even see all of either, at least not where portions of grub1 are concerned, and have consistently failed to get beyond the stage of reinstalling Ubuntu 9.04 or 10.04, Some definitive instructions may help at this point.  Some have already been offered, and I will return to this tomorrow.  So goodnight, and thanks.

Caught another reply, something about run the bootscript.  Don't know anything about that, hasn't come to my attention before .  And I am bugged by the fact that trying to install the LiveCD of 10.04 consistently reported an error, no matter what partition I might designated.  No, I know that only  one partiton is for booting, but I was just trying to see if I could get that message to change, and it remained fhe same for all six partitions with three on two separate drives.  Now why would that be?

Oh, abd if someone would c how are to explain how to convert the boot process after grub1 to substitute a drive reference in place of a UUID,
I intend to revert to the old method of drive designation and forget the mess that happens when this or that partition is reformatted.

---

### Post by wilee-nilee on 2010-06-12
Well I know I give up trying to help you, good luck in all your endeavors.:lolflag:

---

### Post by oldefoxx on 2010-06-12
I haven't the time right now to read through all the responses, bu I will.  I guess my only choice at this point is a clean sweap of all the partitions by reformatting, then going with Ubuntu 9.05 again.  zzi'll forego 9.10 which seemed problematic and too unstable, and give up on 20.04 LTS for many more months.

Why condem 10.04 LTS?  I took a close look at my notebook with it on there, and guess what?  It's completely clean.  The only thing that has been done to the notebook in some time was to allow the updates to run.  Now I suddenly have nothing left.  It is like a brand new install, with all added folders, foles, cookies, icons, and refererences to other partitions completely wiped.wiped out.  My VDI for Windows is gone too, which means years of emails and much of my development software.

I do have a backup.  The 250 GN internal hard drive that I removed and replaced with a 750 GB one for about &111.  I can swap that back in, get to what I had, see about backing the whole thing up on an external drive, then swap back again.

I might mention that Western Digital makes such drives, and the model number always begins with WD7500xxx.  They are likely the makers of the one named White Label as well, which is a few dollars cheaper, but only has a 1 year warrantt, not 3.

Some of you are going to think I am absolutely kidding about my current experiences with 10.04 LTS, but I assure you I am not.  This is really happening, and unless malware has slipped in somewhere, I don't know what to think.  And purging an installo back to its original install state?  What would be the point of that?  

Now as I said, on bootup I get a mystery error whith something about -work not being found.  And there is a known problem with this laptop or noteboot, whichever you choose to callo it, and that is...

Me.  I've typed most of my adult life, and the funky way that Toshiba laid out these keys is frustraiting to deal with.  Sometimes I hit a wrong key or wrong key combination, and strange things cah follow.  But I don't know any key combo that is going to put you right back to an As Initially Installed State.

And it is strange to note, but forums like this, they way they are organizaed, are some of the most challenging places for someone not able to type will to deal with.  You hit a wrong key, the whole message may suddenly run off the top of the screen and out of sight.

Enough fussing for now/  There is work to do/  Plenty of it.

---

### Post by oldefoxx on 2010-06-12
The PC is coming along now.  Wiped out all the partitions save one, the last one on the second hard drive, and kept it because it harbors the VDI files to use later.  Reformatting of course gets rid of all files in a partition, and a fresh install of 9.10 on two partitions went without a hitch.

Sort of reminds me of a different conflict, with this comparison in mind:

[QUOTE]Windows XP        Ubuntu 9.04
Vista             Ubuntu 9.10
Windows 7         Ubuntu 10.04 LTS[/QUOTE

Some would say that XP was the best of this lot.  I go with that. Vista was overreach. and I go with that as well.  And maybe Windows 7's time has come,
but I can't really see a reason for it myself.  But obviously there is effort there to make each go further than done previously, and that seems sort of like what seems to be happening in the Ubuntu development community now.  That is what makes me see a parallel, I guess.

Something to really report though,  I think I see a cause for part of the disruption after going to 10.04 on the laptop.  It involves the touchpad.  All notebooks are presumed to have touchpads without buttons.  That means that the touchpad is set so that any lingering pressure on the keypad serves as one or two mouse clicks.  Now since this notebook has a crammed keyboard with a small-and-set amidst-the-other-keys style space bar.  Now there is a reason a regular typewriter or keyboard has a large and low set space bar, which is that it is the short and humg back thumb that normally presses it.  So here is the problem.

If you have a palm rest,you have little problem keeping your hands positioned over the keys.  If you don't you normally have a large and set low spacebar that your thumb's edge can touch and help you hold position.  But with a keyboard like this, you have neither.  So your hand wants to drop slightly to be in touch with the surface below.  But the touchpad is between your hands then, meaning you might touch it and cause the mouse position to shift.

Held there too long, and it might cause a single or double mouse click to be reported.  This comes as an enabled feature, simply because some OEMs make use of this feature to do away with the need for mouse buttons altogether.

Even just trying to press the space bar is a problem, because the hands have to move forward in order for the leading edge of the thumbs to make contact with the space bar.  Trying to bring your hands back afterwards or simply not going far enough forward, and you thumb might come down on the touchpad instead of the space bar.  That could count as a move and a click, and the effect would depend on where the mouse cursor was at that precise moment.

I noted today that in just trying to range through some folders, that suddenly a document moved, then disappeared.  I think it was actually following whatever signals it thought it was getting through the touchpad. That meant inadvertently, I could be causing changes to my system just jy trying to use the keyboad, which is so close to the touchpad.  You can turn off a part of this aspect my settings under mouse, but to get completely away from it, I guess you have to use an external keyboard and mouse.  Now portable is not so portable any more.

So yes, it looks like I could have been doing myself great harm in this manner, but actually, I cannot see what I could have done by key presses that would explain the problems that have come up.  And I am particularly concerned with the unresolved incompatibilitgies between grub1 and grub2.

---

### Post by oldefoxx on 2010-06-12
I've gotten half the job done now.  Cut down number of partitions on reformat, and first one is set up under 9.04 with 'VirtrualBox amd fpir clones of the VDI in place.  Thought I had taken necessary steps to get second partition halfway set up, but grub says no, it can't find the partition. I guess you have to assume that for some reason, the UUIDs don't match up.

Well anyway, I am halfway home.  It did flit briefly through my mind that I could still use 10.04 on the second partition, but that would have been really stupid on my part.  They don't match up in the grub boot process, and that would just foul things up again. The only way you could support that approach is a manual install of a single unifying grub method, or for one grub to call the other, withe the other being on a different partition. meaning two boot stages. I guess nobody really considered the ins and outs of mixed boot methods with basic incompatibilities, or they just though nobody would even be involved enough to do something like that.

Thing that now bothers me is there should be an easy way to tak a full install from one partition and clone it to another, and have it so that either works.  Can't do that with Windows, because 
Windows is drive-letter oriented, and the cloned copy would have a different drive letter associated with it.  Now the administrator can shift around drive letters to some extent, and create drive letter associations, but this does not extend to the %SYSYEMROOT% drive, which is the critical one.  For the cloned drive to work, it would have to be swapped out with the drive that was cloned.

---

### Post by oldefoxx on 2010-06-13
Oh boy, just not my time it seems.  On the laptop, caught a document moving in accordance to touchpad movement.  Document then disappeared.  Had no intention of moving document anyway.  Checked mouse settings.  The touchpad had it set where pausing a breath too long on the touchpad counted as a click, and a tad longer as two clicks.  Fact is, get one click as you move on the keybad and you drag along whatever is under the mouse pointer at the moment.  Because they stick touchpad where both thumbs typically have a rest, you engage in mouse activities without intending or even knowing it,  The alternative for the thumb rest area is light contact with the space bar, but on these compressed keyboards, the space bar is too far up with the rest of the keys and too small as well, so that your thumbs are left to float about as you use your palms to maintain condition.  But the thumbs do have one task, which is to press the spacebar, and since it is to far beyond the tip of the thumbs, you can often miss and end up hitting the touchpad with the side of your thumb.

I never thought of myself as a laptop type, and in some ways I never will be. But there are advantages too,like hearing ligntening roll in and just unplugging the charger and keep on trucking without fear of an electrical jolt coming in on a wired connection.

You have to have the click enabled in Ubuntu by default, because it is the only way to create a mouse click in machines that do not have the mouse buttons as well

---

### Post by stinkeye on 2010-06-13
Do you know this is a general help section.... not a personal diary?

---

### Post by wilee-nilee on 2010-06-13
> **stinkeye said:**
> Do you know this is a general help section.... not a personal diary?

:lolflag:

---

