---
title: "windows deleted after ubuntu installation"
date: 2009-09-04
forum: General Help
---

### Post by hairchin67 on 2009-09-04
can someone tell me if i can call windows support and have them reinstall windows if it was overwritten. My computer came with xp and i have the product key #s. I want to partition my hard drive before hand to leave a small space for windows. i need it for college. I love ubuntu and wish to keep like 90% of disc space for linux

---

### Post by doas777 on 2009-09-04
did this just happen? if so you may be able to recover the partition with Testdisk if it is not completely overwritten, but you will need another disk to writ the data too.

no they could not really help you, unless you have the disks, in which case you don;t need their help.
borrow a disk from a friend to use with your legit key.

---

### Post by hairchin67 on 2009-09-04
so u dont think they can do it remotely onto my partition for windows without a disk

---

### Post by doas777 on 2009-09-04
no definitely not. the user needs physical access to the machine to perform an install under most circumstances.

your PC would have to be listening for their connection, in order for them to connect, and then it needs to know how to process their commands. ubuntu certianly isn;t listening for any smuck from MS to connect so that they can delete ubuntu and install windows. they'd do it to all of us if they could.

---

### Post by hairchin67 on 2009-09-04
could i burn a disc off the net

---

### Post by P4man on 2009-09-04
@hairchin67: recovering a (at least partially) overwritten windows partition is a non starter. At best you might be able to recover some files, but never will you manage to get a workable windows again

doas777: you'll need a windows Cd. And not just any windows cd, there are dozens of different types of windows cds (home/pro, oem/retail/msdn, ) and you can't  use your legit key with anything except the exact same version. Even a Dell oem copy wont let you install with your key if its for a Toshiba. Its a royal PITA. More than once I installed a pirated and cracked copy because I couldnt manage to install with my legit key (!) after losing or damaging the cd (or not getting one with a machine).

Dont expect any help from MS either, unless you purchased a retail copy in a store, you'll need to contact your oem. They can send you a cd for a fee, or if you dont have a cd drive, reinstall it for you.. for a fee.

Depending what you need XP for however, consider installing a copy inside a virtual machine under ubuntu. You'll still need a windows cd or iso file, and you'll still need a valid licence number or crack though.

---

### Post by Kristofer Van Orton on 2009-09-04
so you dont have a windows disk anymore?
well you could burn one off the net, but its not exactly legal
you could just buy it, if its xp i dont think it costs that much anymore
now that vista and 7 are out

well whatever you do for lfuture reference if you want to dual boot windows and ubuntu the best way to do it is 
put the ubuntu disk in your computer while windows is running
go to my computer
click on the disk in my computer
a dialog will pop up with three options
choose the middle one that says "install inside windows"
and there should be no problems

---

### Post by hairchin67 on 2009-09-04
the only reason i need windows is because it is required software for a college math lab. how can i get away with this as painless as possible is the 39$ question

---

### Post by geirha on 2009-09-04
> **hairchin67 said:**
> the only reason i need windows is because it is required software for a college math lab. how can i get away with this as painless as possible is the 39$ question

If your computer is fairly powerful, you could install windows in a virtual machine with [virtualbox](https://help.ubuntu.com/community/VirtualBox) and run the windows programs in there. Some windows programs will also work with [wine](https://help.ubuntu.com/community/Wine). Lastly, if you need windows to run matlab or maple for the math lab, then you should be aware that there are linux versions of those applications as well ...

---

### Post by doas777 on 2009-09-04
> **Kristofer Van Orton said:**
> its not exactly legal
you could just buy it, if its xp i dont think it costs that much anymore
now that vista and 7 are out


it's only illegal on your end if you do not possess a license to use it (which the op has stated he has). the poster of the Disk has usurped the distribution right, but that is not the accessors problem. 
XP is no longer available for sale in most locales.

---

### Post by hairchin67 on 2009-09-04
what would be the linux versions of this math lab software to allow me to get by with linux and not have to mess with windows

---

### Post by doas777 on 2009-09-04
> **hairchin67 said:**
> what would be the linux versions of this math lab software to allow me to get by with linux and not have to mess with windows

you haven't mentioned the app you need by name yet. what is it?

---

### Post by hairchin67 on 2009-09-04
> **doas777 said:**
> you haven't mentioned the app you need by name yet. what is it?

by app what do u mean please bear with me im learning as i go

---

### Post by hairchin67 on 2009-09-04
by app what do u mean please be patient with me im learning do u want the name of the software or what???

---

### Post by hairchin67 on 2009-09-04
ok these r the required plug ins  mathxl player, interact math plug in
test gen plug in adobe reader apple quick time
real player/real one player macromedia flash player java virtual machine
 can i get these from linux or alternate ones to do the job

---

### Post by QIII on 2009-09-04
hairchin --

I don't have an answer to your question, but I will say this:

Even the hint of doing something illegal or unethical to restore an OS that is someone's intellectual property, even if that property belongs to the Evil Minions of Redmond, is inappropriate for a forum like this and patently illegal for you.

You have one choice only if you want Windows back:  reinstall Windows using your legitimate product key.

This thread may disappear momentarily.

If it does, post your issue again.

---

### Post by doas777 on 2009-09-04
> **QIII said:**
> hairchin --
You have one choice only if you want Windows back:  reinstall Windows using your legitimate product key.


that is exactly what we have advised. You've made a number of assumptions here, so i urge you to reread the thread an brush up on section 17 of the US copyright code.

---

### Post by egalvan on 2009-09-04
> **QIII said:**
> hairchin --

I don't have an answer to your question, but I will say this:

Even the hint of doing something illegal or unethical to restore an OS that is someone's intellectual property, even if that property belongs to the Evil Minions of Redmond, is inappropriate for a forum like this and patently illegal for you.
[B]
You have one choice only if you want Windows back:
**[COLOR="Red"]  reinstall Windows using your legitimate product key[/COLOR]**.
[/B]


Excuse my ignorance, but isn't this ***[COLOR="Red"]exactly[/COLOR]*** what the OP is asking help with?

QUOTE from OP post #1
[I]can someone tell me if i can call windows support and have them reinstall windows if it was overwritten.
** My computer came with xp and [B]i have the product key #s**[/B].[/I]

---

### Post by P4man on 2009-09-04
> **hairchin67 said:**
> ok these r the required plug ins  
mathxl player

First one I checked, and might be a problem already:
[http://www.mathxl.com/support/system.htm](http://www.mathxl.com/support/system.htm)

I tried the browser check with a random course, and it failed on my ubuntu. How they manage to make a **browser** app incompatible with linux is .. well. beyond words :s.

The rest of the list would be fine AFAICT.
And perhaps the mathxl thing can be worked around using IE4linux.

---

### Post by doas777 on 2009-09-04
> **egalvan said:**
> Excuse my ignorance, but isn't this ***[COLOR=Red]exactly[/COLOR]*** what the OP is asking help with?

QUOTE from OP post #1
[I]can someone tell me if i can call windows support and have them reinstall windows if it was overwritten.
** My computer came with xp and [B]i have the product key #s**[/B].[/I]


you are not the one being ignorant. thanks for speaking up.
cheers!

---

### Post by P4man on 2009-09-04
update, it seems this guy got it working with IE4linux:

[http://matthewpoer.freehostia.com/wordpress/2007/09/21/activex-for-linux/](http://matthewpoer.freehostia.com/wordpress/2007/09/21/activex-for-linux/)

Id still keep a plan B at hand though (prepare a virtual machine with windows in it).

---

### Post by egalvan on 2009-09-04
To the Original Poster...

If your computer is a Dell or HP, then I suggest  you call the 
tech support line.

Have your computer in front of you, so you can give them the Serial numbers off the machine.

Ask to buy the XP reinstall disks.
Both Dell and HP charge for these...
HP usually charges from $15-$20 per set.
Dell charged me $25 for one.

Compaq is similar, but rather more expensive.
They charged $42 for the same XP Media Center that
HP charged $16.

I have no recent experience with other manufactures.

---

### Post by doas777 on 2009-09-04
this somewhat dated thread may help you get mathXL going on ubuntu. it does look like it may not support firefox.
[http://ubuntuforums.org/archive/index.php/t-385282.html](http://ubuntuforums.org/archive/index.php/t-385282.html)

---

### Post by egalvan on 2009-09-04
> **P4man said:**
> 

I tried the browser check with a random course, and it failed on my ubuntu.
 [COLOR="Red"]How they manage to make a **browser** app incompatible with linux is .. well. beyond words :s.[/COLOR]


THIS IS MY OPINION ONLY

but I think this is money well-spent by Microsoft.

THIS IS MY OPINION ONLY



Notice...
Reading my posts may cause angst.

---

### Post by QIII on 2009-09-04
> **egalvan said:**
> Excuse my ignorance, but isn't this ***[COLOR=Red]exactly[/COLOR]*** what the OP is asking help with?

QUOTE from OP post #1
[I]can someone tell me if i can call windows support and have them reinstall windows if it was overwritten.
** My computer came with xp and [B]i have the product key #s**[/B].[/I]

Yes.  Exactly.  I didn't say it wasn't what the OP asked for.  

But someone did bring up "pirated".

---

### Post by QIII on 2009-09-04
> **doas777 said:**
> that is exactly what we have advised. You've made a number of assumptions here, so i urge you to reread the thread an brush up on section 17 of the US copyright code.

Using a valid copy of another person's disk with your product key is entirely legitimate and legal.  The product key establishes your right to have the OS installed, not physically having the disk itself.

 However, a "pirated" copy of a disk, legitimate product key or not, it still a violation of US Code.   And yes, it is the "accessor's" problem.  *Knowingly* receiving stolen intellectual property is also theft.  It has been successfully prosecuted -- at the consumer's expense.

You are welcome to have a look at my profile and have a look at what I do for a living.  You may understand my dismay at the words "pirated" and "cracked".

"Do not make illegal copies of this disk"

And no, I have not made any assumptions.  I read your posts.  You are entirely within bounds.

---

### Post by hairchin67 on 2009-09-04
craig@craig-desktop:~$ apt-get install wine cabextract
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
craig@craig-desktop:~$ 

how do i fix this issue

---

### Post by hairchin67 on 2009-09-04
> **QIII said:**
> A "pirated" copy of a disk, legitimate product key or not, it still a violation of US Code. 

Yes it is the "accessor's" problem.  *Knowingly* receiving stolen intellectual property is also theft.  It has been successfully prosecuted.

You are welcome to have a look at my profile and have a look at what I do for a living.  You may understand my dismay at the words "pirated" and "cracked".

"Do not make illegal copies of this disk"

And no, I have not made any assumptions.  I read your posts.  You are entirely within bounds.

possession is nine tenths of the law

---

### Post by QIII on 2009-09-04
Let me come by and pick up your car.

Not trying to be a horse's back side.  But I work in the industry.

And I understand you were not asking for illegal help.  Someone mentioned "pirated".

Many software vendors recognize the problem, understand people receive illegal or pirated software, but have valid licenses.  There is usually a remediation process.

Knowingly receiving the pirated intellectual property is illegal. You are not absolved by saying that you got it from someone else who did the pirating.  

Doing so unwittingly is a PITA, but it happens.  Case in point is the recent incident with the Kindle.  Those who unwittingly downloaded a book that was still protected had that book removed.  After an outcry, the book was restored.  The error was unwitting on the part of the consumer.  

Having a product key written on a piece of paper is often not enough.  Often the original packaging with a foil seal is generally required.  Disks get ruined.  We know this.  Computers fail and need to be rebuilt.  We know this.

Using someone else's legitimate disk with your legitimate license is generally legal.  That was given as an example and my purpose was to agree, not to start a flame war.

---

### Post by QIII on 2009-09-04
> **hairchin67 said:**
> craig@craig-desktop:~$ apt-get install wine cabextract
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
craig@craig-desktop:~$ 

how do i fix this issue


Do you have Synaptic open?

---

### Post by QIII on 2009-09-04
Just took a closer look.

Use

sudo apt-get ...

---

### Post by doas777 on 2009-09-04
> **QIII said:**
> Using a valid copy of another person's disk with your product key is entirely legitimate and legal.  The product key establishes your right to have the OS installed, not physically having the disk itself.

 However, a "pirated" copy of a disk, legitimate product key or not, it still a violation of US Code.   And yes, it is the "accessor's" problem.  *Knowingly* receiving stolen intellectual property is also theft.  It has been successfully prosecuted -- at the consumer's expense.

You are welcome to have a look at my profile and have a look at what I do for a living.  You may understand my dismay at the words "pirated" and "cracked".

"Do not make illegal copies of this disk"

And no, I have not made any assumptions.  I read your posts.  You are entirely within bounds.

thank you. sorry for my end of the miscommunication. 
best regards,
Franklin

---

### Post by QIII on 2009-09-04
Sorry for mine, as well.  It is often difficult to discern intent on a forum like this.

You'll have to forgive me for my sensitivity to the whole issue...

---

### Post by hairchin67 on 2009-09-04
how can i be recognized as root to get file permissions

---

### Post by fluffman86 on 2009-09-04
> **hairchin67 said:**
> how can i be recognized as root to get file permissions

Prefix any command with "sudo."  So if a tutorials says something like:
> as root, type "apt-get install some-package"
Then you should should type "sudo apt-get install some-package"

If you need to browse the file system as root, then press alt+f2 and type "gksu nautilus"

---

### Post by egalvan on 2009-09-08
> **QIII said:**
> **...a valid copy of another person's disk with your product key is entirely legitimate and legal.**
  The product key establishes your right to have the OS installed, not physically having the disk itself.

...a [COLOR="red"]"pirated" copy of a disk, legitimate product key or not, it still a violation of US Code. [/COLOR]

I find this hilarious at best...
ingenuous at worst.

So...
In the *specific* case of the OP questioning XP installs,
on a computer that he purchased,
 that came with XP installed,
 and with the XP keys on a sticker on the machine...
what differentiates a **valid copy** of an XP CD from a [COLOR="Red"]pirate copy[/COLOR] of an XP CD?

and please note the emphasis on this particular situation, as I also have no intention of starting "flame wars"

ErnestG
(although as a fireman, I have no problems with "flames" :lolflag: )

---

