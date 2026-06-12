---
title: "Ubuntu screwed up my sister/mom's laptop's Vista."
date: 2010-01-28
forum: General Help
---

### Post by Joey B. on 2010-01-28
OK so it worked fine last night, now, Vista won't start but Ubuntu will, all her documents are gone because my sister stepped on our disk, I can't bring files over to Ubuntu for them because the entire partion for Vista deleted itself automatically.  I seriousely need help otherwise, I'm literally dead because my mom needed that laptop in a week.

---

### Post by Joey B. on 2010-01-28
I need help now!

---

### Post by audiomick on 2010-01-28
Hi Joey.
First of all, clear up a couple of things for me:

> **Joey B. said:**
> OK so it worked fine last night, now, Vista won't start but Ubuntu willthis is a dual boot machine, not a wubi install

> all her documents are gone because my sister stepped on our diskyou have an external drive that you were using to back up or transfer  with. If is dead of mechanical damage.

Am I right so far?

> I can't bring files over to Ubuntu for them because the entire partion for Vista deleted itself automatically. Is this on the dual boot machine? The one you mentioned at the start? 

 > I seriousely need help otherwise, I'm literally dead because my mom needed that laptop in a week. Your mum is not really convinced about this Ubuntu thing, and now she is really on your case...


The first thing I would suggest is to go here
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
read through it, follow the instructions and post the RESULTS.TXT file back here.

This will tell us about the state of the boot loader and the partitions on the hard drive.

I think that the problem is just that the boot loader, grub, has got messed up, and you should be able to fix things fairly easily.

edit: it is bad form to bump so quickly.

---

### Post by Joey B. on 2010-01-28
> **audiomick said:**
> Hi Joey.
First of all, clear up a couple of things for me:

this is a dual boot machine, not a wubi install

you have an external drive that you were using to back up or transfer  with. If is dead of mechanical damage.

Am I right so far?

 Is this on the dual boot machine? The one you mentioned at the start? 

  Your mum is not really convinced about this Ubuntu thing, and now she is really on your case...


The first thing I would suggest is to go here
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
read through it, follow the instructions and post the RESULTS.TXT file back here.

This will tell us about the state of the boot loader and the partitions on the hard drive.

I think that the problem is just that the boot loader, grub, has got messed up, and you should be able to fix things fairly easily.

edit: it is bad form to bump so quickly.

It was a CD everything was backed up on, it is a dual boot, it was through the Places and then the disk mount thing,  and I can not download anything to help it, not allowing downloads.

---

### Post by sailthesea on 2010-01-28
It might help if you told us:

What version of Ubuntu you are using
Is that a dual boot with Vista Or were you doing something else? (Live CD/USB , Wubi?)
When you say "stepped on the disc" What do you mean exactly?

Edit : Go with Joey B     ..So slow...

---

### Post by gradinaruvasile on 2010-01-28
> **Joey B. said:**
> the entire partion for Vista deleted itself automatically

Now thats interesting. How did that happen? And does it have to do with the disk that was stepped on?

---

### Post by Joey B. on 2010-01-28
> **sailthesea said:**
> It might help if you told us:

What version of Ubuntu you are using
Is that a dual boot with Vista Or were you doing something else? (Live CD/USB , Wubi?)
When you say "stepped on the disc" What do you mean exactly?

Edit : Go with Joey B     ..So slow...

She just walked on the disk. I installed with a CD, DUal Boot.

---

### Post by audiomick on 2010-01-28
Yes, what version of Ubuntu is it. Is it Karmic 9.10, and if so was it a fresh install or an updated older version? This is important, because that makes a difference to which boot loader it was.

---

### Post by gradinaruvasile on 2010-01-28
So, you dont see the Vista partition anymore under the "Places" menu?

---

### Post by r_s on 2010-01-28
well if you have not overwritten the partition , you can perhaps use testdisk to recover your deleted partition.

---

### Post by Joey B. on 2010-01-28
Oh sorry I left out Version 9.10 new install.

---

### Post by sailthesea on 2010-01-28
Follow audiomick's instructions first and lets see what your problem might be
 If no one stepped on the Laptop it should be fixable:)

---

### Post by blur xc on 2010-01-28
> **Joey B. said:**
> It was a CD everything was backed up on, it is a dual boot, it was through the Places and then the disk mount thing,  and I can not download anything to help it, not allowing downloads.

Dude- please speak in complete sentences.  I'm trying to understand your problem, but can't make it out.

You tried to dual boot your mom's laptop- but you accidentally installed Ubuntu on the whole drive, wiping out the Vista partition?  Does the Vista partition still exist?

You backed up your data onto a cd, and someone stepped on the disk breaking it?

Partitions don't delete themselves automatically- you had to have done something.

What I would do first, to check is the Vista partion is still there, boot to the live cd, open a terminal and enter ```
sudo fdisk -l
```, and post the output here.  That will give a list of all drives and partitions on your system.  I say to use the live cd because if you did mess up the partition table, under some circumstances you can recover it (but don't ask me how).  One thing is to not use that hdd because if you do, you might reduce the chances of being able to recover the partition.

BM

---

### Post by audiomick on 2010-01-28
joey, slow down a bit. If you panic, you'll mess it up even more.;)

---

### Post by sailthesea on 2010-01-28
> **audiomick said:**
> joey, slow down a bit. If you panic, you'll mess it up even more.;)

Again Seconded!;)

---

### Post by Joey B. on 2010-01-28
There is still a Vista partion, it loads up to the Welcome splash screen and then freezes up. I don't know what a Live CD is.  Use sudo fdisk - l on what? Vista Safemode or Ubuntu? My sister did download something which could have deleted the partion's data. But I still see it on the GRUB menu. Other than that I think I'm just screwed.

---

### Post by blur xc on 2010-01-28
> **Joey B. said:**
> There is still a Vista partion, it loads up to the Welcome splash screen and then freezes up. I don't know what a Live CD is.  Use sudo fdisk - l on what? Vista Safemode or Ubuntu? My sister did download something which could have deleted the partion's data. But I still see it on the GRUB menu. Other than that I think I'm just screwed.

The live cd is the Ubuntu install disk (could be on a usb stick too though).  Insert the disk, and boot up the disk as if you were installing it, but when you get to the first menu, select "Try Ubuntu without installing", and when you get to a desktop (might take a while, cd's boot slow) go to applications -> accessories -> terminal, enter the command there.

Highlight the text w/ the mouse, right click copy (or shift-ctrl-c), and paste it here in the forum.

BM

---

### Post by Joey B. on 2010-01-28
"User lauren password |"
It won't let me type in the password either.

---

### Post by blur xc on 2010-01-28
> **Joey B. said:**
> "User lauren password |"
It won't let me type in the password either.

it's letting you type the password.  It doesn't look like it's doing anything, but it is waiting for the password.  Just type it and press enter.

BM

---

### Post by lisati on 2010-01-28
> **Joey B. said:**
> There is still a Vista partion, it loads up to the Welcome splash screen and then freezes up. I don't know what a Live CD is.  Use sudo fdisk - l on what? Vista Safemode or Ubuntu? My sister did download something which could have deleted the partion's data. But I still see it on the GRUB menu. Other than that I think I'm just screwed.

OK Joey, I second the suggestions to slow down! Many of us here have had moments where we get really frustrated and want to panic.

A "Live CD" is another name for the the regular installation disk. One of the options it has lets you use Ubuntu without touching your computer's hard drive. If this is the disk that was accidentally stood on, don't panic, you might be able to get hold of another one somehow.

The "fdisk -l" thing is something you run from Ubuntu. On Ubuntu's main screen, look for the Applications menu. One of the options is for "accessories", and one of the accessories is "terminal". If you open up "terminal", you will be able to type in:
```
sudo fdisk -l
```
That's a little "ell", not the number one. It will probably ask for your password. If it does, your password won't show on the screen. Just type it in as normal.
Copy the output back to this discussion, and let us know how you get on.

Good luck!

---

### Post by kelvin spratt on 2010-01-28
Just a quick question did you shut down correctly or has the system frozen and been forced to shut down. if its the second vista may have hidden the drive to protect it
Please post as Vista has 2 partitions the boot which is woking and the second which has failed.
 If that is the case its simple to unhide the partition with a live cd.

---

### Post by Joey B. on 2010-01-28
Like I said in my post, it won't let me type in the password, I know what a terminal is, I've been a Ubuntu user for a month.

---

### Post by Joey B. on 2010-01-28
> **kelvin spratt said:**
> Just a quick question did you shut down correctly or has the system frozen and been forced to shut down. if its the second vista may have hidden the drive to protect it
Please post as Vista has 2 partitions the boot which is woking and the second which has failed.
 If that is the case its simple to unhide the partition with a live cd.
Damn it, that's what she did. It also froze.

---

### Post by Joey B. on 2010-01-28
We're just buying a Windows 7 disk and upgrading now.

---

### Post by audiomick on 2010-01-28
So let us know what happens. I think that will overwrite your grub, i.e. windows will boot, but you wont be able to boot Ubuntu anymore. That can be easily fixed. As I said, let us know.

---

### Post by User0123 on 2010-01-28
> We're just buying a Windows 7 disk and upgrading now.
No need to do that...

>  I know what a terminal is, I've been a Ubuntu user for a month.Don't get techy when people are trying to help you, the fact that you didn't know whether fdisk -l was a Windows or Linux command, and you didn't know that your password isn't shown when you enter it in terminal are why people are explaining things slowly for you...

Remember people aren't paid to help here.

Luckily it seems like you haven't deleted the partition or anything disastrous like that. Please slow down and listen to, and do, what people are trying to help you with... the output of fdisk -l would be a good start.

---

