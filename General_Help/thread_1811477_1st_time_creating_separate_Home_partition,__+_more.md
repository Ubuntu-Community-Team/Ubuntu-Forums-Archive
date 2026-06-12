---
title: "1st time creating separate /Home partition,  + more. Help?"
date: 2011-07-24
forum: General Help
---

### Post by Rasa1111 on 2011-07-24
Hey all, 

I've been wanting to do this for awhile now,
But just got around to having the time/energy to do it. 

Getting a separate /Home partition is my main goal,
But Ive got a couple others as well. 

                                 I've never really done much work manually editing/extending/creating of partitions,
 Soo Im going to need really simple, noob-like instructions if possible.  
 
I'd love to get this on the first try without having to start all over..
 So I come to you first, before I just jump in and start clicking things.  
 
Ok, Heres what I want to do..
 
right  now, I have 3 installs,  
 2 of which I want to keep,  
 and then make a /home partition.
 
My **Main install **is Ubuntu 11.04. [sda1] (want to keep for now~ and shrink)
 **second install** is Ubuntu 11.10 Alpha 2 [sda6] (want to remove)
 **third install** is gNatty 11.04 [sda8] ( want to keep and make larger)
 
gParted shot~ 
 [COLOR=Indigo]**[IMG]http://ubuntuforums.org/attachment.php?attachmentid=198363&stc=1&d=1311562219[/IMG]**[/COLOR]


 So,  
  My thoughts are,  
 
First~ I'd like to delete the 11.10 install (on sda6) , and then give the space back to 11.04 on sda1. (Then I'd need to shrink it)

 Second~ I'd like to extend the gNatty partition on sda8 to make it larger.  
 
Third~ I'd like to create a new, separate /Home partition.  

So I would have 3 partitions, Ubuntu 11.04/ gNatty 11.04/ and /Home. 

 Is this easy enough to do?
 If so, Could anyone give me simple, explicit directions on how to do it?  
 Like, step-by-step? lol
 
I have read multiple web pages explaining how to create a /home partition,  
 but always get confused by other things they add in (like, &#8220;then make another /root partition, and a /usr partition, then edit fstab, etc etc)  
  and they also don't quite address exactly what I need to do here.  
 
If worse comes to worst..
 I guess I can just start all over again,  
 But I would really like to attempt this, and get it to work!  
 
Man, that would be awesome.  
 
Anyone with some extra minutes, a kind heart, and an intelligent mind that would like to help a brother out?  You will be by hero. Lol :)

Last thing, 
I would need/want to make it so that whenever I boot into either OS,
the /Home partition mounts with either one, automatically on boot up. 

 How does it look?
Doable? 

 Thanks in advance, Hope to hear from you soon.

---

### Post by Rasa1111 on 2011-07-24
ohh yeah, Also..

Does 100 GB for /Home, and 30 GB's for each OS sound good? 

HDD is 160 GB. 

So,
 /Home= about 100GB
11.04= 30 GB
and gNatty=30 GB

Does that sound wise? 

is 30GB suitable for each OS if they are both sharing a /home partition?
So the space they would use would simply be for the installed apps/programs, is this correct?

If not, What would be best? lol

---

### Post by Quackers on 2011-07-24
Firstly you should find out which system currently has control of grub and which swap partition that system is using (see /etc/fstab in that system).
If you haven't changed the default order of the grub menu, this will be the first item on the grub menu.
Secondly you can free up almost 4GB of the extended partiton by deleting 2 of your swap partitions - not sure which 2 yet though :-)
Thirdly, a separate home partition can be shared between 2 installations, but separate home folders should be used, with different names. I haven't done it, but others have. I personally have separate home partitions for each installation.
15 to 20GB would probably be alright for each system's root partition.

Now to your partition changes.
If you aren't 100% sure which system has grub control I would recommend that you boot into your 11.04 system on sda1 and run```
sudo grub-install /dev/sda
``` Now you know that 11.04's grub has control. 
Have a look in /etc/fstab in that system and see which swap partition it uses.

I would then run gparted and right-click on any swap partition that's locked and select "swapoff".
Delete the 2 swap partitions that the 11.04 system is not using.
Delete the sda6 partition.

Close gparted and run sudo update-grub.

This will simplify your partition setup for the moment.

You can then resize sda1 if you want, from gparted run from a live cd.
I would leave 11.04 with an integrated home folder. If you want to create a separate home partition for 11.04 you can, but you will then need to move your current home stuff to that new partition and mount it automatically by editing /etc/fstab in 11.04 (with the new home partition's UUID). There are guides on how to do this but as I haven't done it I would hesitate to give advice on that :-)
The same steps can be used to adjust your sda8 installation and/or create a separate home partition (or the same home partition shared) for that. The home folder in sda8 could then be moved to your new (shared) home partition (using a different user name) and /etc/fstab adjusted to reflect the new home partition's UUID AND the new swap partition's UUID which will probably have changed because you have now deleted 2 swaps.

It's a lot of work.

I would leave your current installations as they are (except for the 2 swap partitions and sda6 deletion) and make the new arrangements for new installations only - but that's just me :-)
See what you think.

---

### Post by Rasa1111 on 2011-07-25
Crap, man..
Big, giant... CRAP!

Well I've already screwed something up. 

 Thanks for the reply Quackers. 

Being the idiot I am, 
I decided to go on ahead and open gParted,
and then proceeded to "delete" the 11.10 partition so that it was "unallocated". 

I read something that said I could do that, and then extend/resize the smallest partition to use it's unallocated space. 

Welp, Now I can't even boot / can't get to GRUB menu. 

This is what I get for being impatient and screwing with things Im unsure of. 

So, Now when i boot the machine, it gives me some "unknown" error, and then a command line to type something in, but i have no idea what. 

 I guess I'll reboot and find out what it says, then post it back here. 

Gahh.  
Right about now I'd say forget the /Home partition for the moment
if I could simply resize my gNatty install to use those 20+ GB of now "unallocated" space. 

IF I could even boot into my 11.04 or gNatty installs. 

man, it sucks being a r3t@rd. i swear. :(

---

### Post by Rasa1111 on 2011-07-25
Alright, This is all I get when booting the machine~

a black screen with~ 
> [B]error: unknown file system
grub rescue> _ [/B]Any way to save this? :???:

or should I just say to hell with it and do a fresh install of gNatty? (and maybe a /Home partition?
damn-it. 

I _*do*_ have all my data saved and backed up. 
thats about all I have going for me right now. lol :???:

---

### Post by Quackers on 2011-07-25
Sadly Rasa1111, that's how most of us learn stuff :wink:
It may be that you deleted the partition that had control of grub and therefore grub  will need re-installing. If it does, from the 11.04  live cd desktop run ```
sudo mount /dev/sda1 /mnt  
sudo grub-install --root-directory=/mnt /dev/sda
``` and hopefully it should boot again.

---

### Post by wildmanne39 on 2011-07-25
Hi, you need to reinstall grub using the livecd here is a guide to do that.
[http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html](http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html)

---

### Post by Miljet on 2011-07-25
> First~ I'd like to delete the 11.10 install (on sda6) , and then give the space back to 11.04 on sda1.

Although this can be done, it will be exceedingly difficult. You do understand that sda5 through sda9 are all included inside of sda2, don't you? You can't just trade space between primary and extended partitions.

---

### Post by Rasa1111 on 2011-07-25
> **Quackers said:**
> Sadly Rasa1111, that's how most of us learn stuff :wink:
It may be that you deleted the partition that had control of grub and therefore grub  will need re-installing. If it does, from the 11.04  live cd desktop run ```
sudo mount /dev/sda1 /mnt  
sudo grub-install --root-directory=/mnt /dev/sda
``` and hopefully it should boot again.


 Oh thanks!

Yes, you are right man. I guess that is how we learn.  ;)

Ok, *some* good news..
Got my GRUB back, and now booted into my 11.04 install, No problem! 
Thanks man!  Props to you. <3

Now, When I choose sda1 (11.04) from GRUB, it boots up fine..

But, when I select sda6 (which is now gNatty), I get this~

> error: no such device
error: no such disk
error: you need to load the kernal first

press any key to continue..

lol, what? :confused:

wildmanne, thanks for the link. :) <3

> Although this can be done, it will be exceedingly difficult. You do  understand that sda5 through sda9 are all included inside of sda2, don't  you? You can't just trade space between primary and extended  partitions. 	

No man, I'm sorry, I did not know. :(

 thanks for the replies guys. 
Much appreciated. <3

---

### Post by Quackers on 2011-07-25
Lol :-) Did you delete just sda6?
In 11.04 have you run sudo update-grub? Try that, it may fix gnatty. If not we can take a look.

---

### Post by cbowman57 on 2011-07-25
@Rasa1111;

I guess I'll weigh in with an opinion as well.  Trying to share a /home partition between 2 installations is asking for trouble.

Now if you're thinking of starting from scratch, or want to shuffle partitions with GParted, I'd suggest not sharing a home but either link or bind a separate partition that contains your Downloads, Music, Pictures, etc.. whatever folders that require a lot of space.  I share those, and a couple other partitions between about 6 installations & it does not cause me problems.  The actual space used by an Ubuntu or Debian installation once those are relocated is roughly 5Gb  so 10Gb for an installation is more than adequate.

You decide how you want to approach this, there are already a bunch of really sharp people that responded to this thread so if you choose a path somebody can walk you through it.

---

### Post by Rasa1111 on 2011-07-25
> **Quackers said:**
> Lol :-) Did you delete just sda6?
In 11.04 have you run sudo update-grub? Try that, it may fix gnatty. If not we can take a look.

 haha!
Yes, I believe I did. *hides face*

Ok, That worked! Now booted into gNatty! 
Man, you rock soo hard! :guitar:  lol
Thank you!! 

Now,
Would it be too much work for a simpleton like myself to make my gNatty partition larger? (and clean up whatever is on the HDD that I don't need?)
If I can manage that.. I'll be set for awhile without feeling the need for a separate /Home I guess. lol :o

**@ Chuck**, Thanks man, 
That is good info, and sounds like what I've been wanting to do..
I may take you up on some more info in the *possibly near* future.
I appreciate it.  :KS

**Now~** Should i load up GParted again so you guys can have a peek and tell me what needs to be done to give gNatty some more space?  lol

Really want to give it that 20+GB's of 'unallocated" space if possible. 

You guys have been a huge help,
Specially you Quackers!
Can't thank you enough man, really.
Thanks!

You guys :guitar:

<3

p.s.. my grub screen is purple now instead of black, i like it! lol

---

### Post by wildmanne39 on 2011-07-25
Hi, here is a guide by the master for resizing partitions.
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by Quackers on 2011-07-25
'Tis nothing :-)
Yes, please post screenshot of current gparted screen and tell us what your new requirements are :-)

---

### Post by Rasa1111 on 2011-07-25
haha, :)
Ok, Here is my mess.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=198370&stc=1&d=1311571262[/IMG]
What I'd like to do , 
is ;   First~ to be able to clean up all those unused "swaps", 
Then~  take all the "unallocated" space that I have, and give it to sda7 (gNatty).
That's it. 

That would make me happier than a pig in mud! lol

Can "we" do it? 

What says you, Guru Quackers? lol :) 
Possible? ???

 thank you. 

good link wildmanne, thanks!  :)

---

### Post by JASONFUSARO on 2011-07-25
[http://ubuntuforums.org/showthread.php?t=1807616&page=4](http://ubuntuforums.org/showthread.php?t=1807616&page=4)

last post #73 I think explains how I do it step by step, I started a thread about a week ago trying to accomplish the same thing.

I don't know if you seen it when you searched, but you may wan't to take a look just for the fun of it.

I have Arch, CtkArch, Chakra and Toorox sharing a partition, I have not added my others yet I have been doing other things but at least my process is  set, so when I continue moving them I simply can.

---

### Post by Quackers on 2011-07-25
Firstly, what did you delete? You still have 2 ext4 partitions in the extended partition and their numbers have changed!.
Second, whilst booted into sda1 system, have a look at /etc/fstab entry for swap and note the UUID given, or the sdaX designation.
Then in gparted right-click on all swap partitions and select "swapoff" then delete the 2 swap partitions not mentioned in /etc/fstab.
Then delete the ext4 partition you don't want any more, if you can find it.
Right-click on the remaining swap partition and choose "swapon".
Close gparted.
Run sudo update-grub - the deleted system should be gone.
Reboot to check things are still ok and check out the new menu.

Boot back into sda1 system and post screenshot of screen :-)

---

### Post by wildmanne39 on 2011-07-25
Hi, your very welcome,I am going to let Quackers the expert have it from here I just wanted you to have the link so you could read and get a better understanding of what you can and can not do with partitions with out causing damage.

---

### Post by Quackers on 2011-07-25
I've just learned through the (costly) mistakes I've made in the past :-). I'm definitely not an expert, just somewhat experienced in this area :-)
Since my new dog has kept me awake for most of the night I'm due for a sleep soon :-)

---

### Post by Miljet on 2011-07-25
That looks entirely "do-able". First you need to know which swap partition your install is using. You can find that information with this code in the terminal: ```
cat /etc/fstab
```
It should look something like this:```
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=a2d227ef-24a1-4709-a402-ecddeab87455 /               ext4    errors=remount-ro 0       1
# swap is on /dev/sda5
UUID=05e1293a-f0a0-474a-b781-d54e9808ab66 none            swap sw  0    0

```

As long as it is not using sda8, you are in good shape. If it is, you will need to edit the /etc/fstab file to change it first.

Then delete sda8 and sda9 so they will now be unallocated. Then expand sda7 to the right to include all unallocated space. 

It is better to do this from a live CD to make sure that nothing is mounted. You might have to turn swap off to be able to delete sda8.

As always, be sure that all important files are backed up before adjusting any partitions. Chances of losing anything is very small, but it does happen.

Otherwise it should be smooth sailing.

---

### Post by Rasa1111 on 2011-07-25
@ Jason~ Thanks man, I appreciate it. 
But I feel like Ill mess something else up if I follow that right now. lol :???: 

> Firstly, what did you delete? You still have 2 ext4 partitions in the extended partition and their numbers have changed!.lol, I know! 
I wondered why they changed numbers..
That doesn't usually happen, or what? 

The only thing I deleted was the original "sda6" that had the 11.10 install on it. 

I have *no idea* what that "sda9, 1.64 GB" is. :???: O_o
and what do you mean..* "if you can find it"* ?

So all I need to keep is sda1,  sda7, and whatever ?swap they need"? lol, I don't know. 
grr..

Ok, I'm going boot into sda1 and do the rest of that right now. thanks

edit:
Miljet, thanks! that will be useful Im sure! 
k brb. :)

---

### Post by Quackers on 2011-07-25
Once you delete the swaps and the other ext4 partition the numbers of the remaining partitions will change. This shouldn't be a problem if you're using 11.04 as grub 1.99 uses UUID's.
Post a screenshot after and then we can extend the remaining ext4 partition to fill the extended partition if that's what you want. Although that should probably be done from the live cd gparted, as Miljet says. That will take a while to run - maybe 2 hours or more.

---

### Post by Rasa1111 on 2011-07-25
> **Miljet said:**
> That looks entirely "do-able". First you need to know which swap partition your install is using. You can find that information with this code in the terminal: ```
cat /etc/fstab
```It should look something like this:```
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=a2d227ef-24a1-4709-a402-ecddeab87455 /               ext4    errors=remount-ro 0       1
# swap is on /dev/sda5
UUID=05e1293a-f0a0-474a-b781-d54e9808ab66 none            swap sw  0    0

```As long as it is not using sda8, you are in good shape. If it is, you will need to edit the /etc/fstab file to change it first.

Then delete sda8 and sda9 so they will now be unallocated. Then expand sda7 to the right to include all unallocated space. 

It is better to do this from a live CD to make sure that nothing is mounted. You might have to turn swap off to be able to delete sda8.

As always, be sure that all important files are backed up before adjusting any partitions. Chances of losing anything is very small, but it does happen.

Otherwise it should be smooth sailing.

Ok, Mine only says what swap "was on", not "is on". 
hmm.. ```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=6f3490d5-1ab4-4f10-a3ae-165158d2ab86 /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda5 during installation
UUID=8f936ec7-28c0-4b6b-a175-177c74cd0e16 none            swap    sw              0       0

```:confused:
What you think? 
 thanks :)
go to go re-read last page..

---

### Post by Quackers on 2011-07-25
Ok, keep the sda5 swap partition and dump the other two :-)
Also delete the 11.10 ext4 partition as well.
Then run sudo update-grub.

---

### Post by Rasa1111 on 2011-07-25
Alrighty, here I go. lol :P
brb. :D

you guys are awesomer than awesome. <3

> Also delete the 11.10 ext4 partition as well.

oh wait, you mean the "unallocated"  20+ GB's? 
or the 1 GB ext4 on sda9?

---

### Post by Quackers on 2011-07-25
Everything you don't need.
Just save the gnatty ext4 partition and sda5 swap.

---

### Post by Rasa1111 on 2011-07-25
Ok, I've done all you said but close gparted and run update grub.
Justr want to check first.. lol
Look good?
[ATTACH]198374[/ATTACH]
That "unallocated" still confuses me...O_o
sorry

---

### Post by Quackers on 2011-07-25
That's fine :-)
The unallocated will soon be part of sda6 :-)

---

### Post by Rasa1111 on 2011-07-25
ok thanks.

I ran sudo update-grub
and got this~
```
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot stat `aufs'.
```hmm
or am i not supposed to be in live session to run that :confused:

---

### Post by Quackers on 2011-07-25
Are you booted into Natty? Or the live cd? Looks like the cd.

---

### Post by Rasa1111 on 2011-07-25
yeah, in the CD, Cause i just got done using gparted. 
that not right? lol

---

### Post by Quackers on 2011-07-25
Can't update grub from there.
Nevermind, carry on.

---

### Post by Rasa1111 on 2011-07-25
Ok, New Grub menu is good, :)
Thank you. 
Booted into sda1 now. 

So, Now is when I go back to live cd/Gparted to do what Miljet said right?  lol
Ive been switching back and forth from live USB to my installs.

---

### Post by Quackers on 2011-07-25
Yes. You won't need to extend to the left so that's good.
You may find that gparted insists on leaving 1MB before and after the extended sda5 partition. Logical partitions can need that. Don't worry about that.
Just turn swap off if it's locked and then right-click on sda5 and select Resize/move and change the figure in the last box to 1 (or try 0) and hit enter. The numbers in the other boxes should change so that the middle box has all the available space, or nearly.
Then apply the change and go for a sleep, or a cup of tea or two :-)

---

### Post by Rasa1111 on 2011-07-25
Ok, it's resized!
[ATTACH]198375[/ATTACH]
How's that look?
proper? 
(man i hope) lol

(didnt take long like you thought)
not sure if thats good or bad. 
:o

---

### Post by Quackers on 2011-07-25
Very nice :wink:
That was fast because no move to the left was required. That's good :-)
Ok, reboot and choose sda1, then just to be sure run sudo update-grub again and if that's ok reboot and try gnatty.

---

### Post by Rasa1111 on 2011-07-25
ok, thanks a ton man!
*Men*! 
you've  been awesome. 

Gonna go check it out. :D <3

---

### Post by Quackers on 2011-07-25
You're welcome :-)
It should be good.

---

### Post by Rasa1111 on 2011-07-25
> **Quackers said:**
> You're welcome :-)
It should be good.

Wow!
Soo good! :o
Amazing! haha!
Everything is perfect now! 

Man, I'm impressed!
Not surprised, but definitely impressed.  lol :KS

I honestly thought i was going to have to do 2 new installs and get everything 'just so' again,
and was not looking forward to it. 

You are my heros! 

You beat 'windows support' that people have to pay for, any day! lol
Crazyness.

 Many, many thanks! 
I'm set!  soo cool. lol

The Ubuntu Heros :guitar: :D

Can't believe people make posts saying how "the support sucks" "i can't get help" O_o

what!?!? :lol:

<3

---

### Post by Quackers on 2011-07-25
Lol, I'm glad you are happy!
Have fun. I'm going to sleep now :-)

---

### Post by Rasa1111 on 2011-07-25
I'm happy you're glad that I'm happy! :D lol
thanks. 
G'night Quackers, sweet dreams,  pleasant journeys! 
 [IMG]http://i77.photobucket.com/albums/j64/1sexytigress/Decorated%20images/th_CougarSleepingDuck.gif[/IMG]zzzzzzzzzzzzzz

---

### Post by Quackers on 2011-07-25
Dog woke me up again!
Nice sleeping baby, Rasa1111 :-)

---

### Post by Miljet on 2011-07-25
Good on you Rasa! Told you it would be smooth sailing. Feels good when a plan works as planned, doesn't it?

Don't forget to mark thread as solved.

---

### Post by Rasa1111 on 2011-07-25
> **Miljet said:**
> Good on you Rasa! Told you it would be smooth sailing. Feels good when a plan works as planned, doesn't it?

Don't forget to mark thread as solved.


haha, Yes! 
Very good!
Can't believe it went soo flawlessly once I got yourself and Quackers involved! 
:KS

 Thanks soo much man! 
you guys are :guitar: :KS's  !

 Thread already marked 'solved'. ;)

---

