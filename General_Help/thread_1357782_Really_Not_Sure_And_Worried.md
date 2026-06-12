---
title: "Really Not Sure And Worried"
date: 2009-12-17
forum: General Help
---

### Post by Lee3155 on 2009-12-17
Hey Guys This Is my first time posting here and I'm kinda worried.

The reason for that is:

I recently found out about Wubi- Installer and ever since I heard about Ubuntu I wanted to install it on my laptop but I didn't want to wipe out windows.

Since I heard about Wubi I want to know if it is safe enough to run on my Laptop.

I am 15 and I only got my Laptop 2 weeks ago and I dont want to ruin it or get any errors or Bluescreens ect..

Here Is Some Info About My Laptop:

Make: Sony Vaio VGN-NS20E

Operating System: Windows Vista Home Premium

I Have 117GB Left Out Of 223GB

Processor: Intel(R) Pentium(R) Dual  CPU T3400 @ 2.16GHz  2.17GHz

Memory(RAM): 3.00GB

System Type: 32-bit Operating System

Emm It's Rating By Microsoft Is 3.5

Oh And It Is Service Pack 1

I Hope I Can Get An Answer

Thanks I Just Don't Want Anything To Happen To My New Laptop.

Also My Friend Was Installing It Last Week And The Writing In The Installer Kept Going Really Dark Then Really Bright Do You Know What Happened??

 Thanks Guys 

- Lee

PS: Is It Safe Enough To Dual Boot?? Thats What I Am Really Worried About!!

---

### Post by Darael on 2009-12-17
I've used Wubi on wide and varied hardware, both better and worse that what you're using, with no problems whatsoever. You should be fine. Wubi is ever so slightly slower than a normal install, but that's all. You will encounter no problems at all, and I say this with as close to absolute certainty as it's possible to get.

---

### Post by Lee3155 on 2009-12-17
Thanks It's Just My Brother Thinks That Dual-Booting Is Not Safe And Has Got Me Really Worried

---

### Post by staf0048 on 2009-12-17
Make sure you've got your back-up cd handy just in case something goes terribly wrong (which I'm 99.9% sure it will not) and go for it.  If something bad does happen, just re-install windows.  No harm, no foul.

---

### Post by Lee3155 on 2009-12-17
Yeah Becuase I Said To Myself If Anything Goes Wrong I Really Want Windows 7 So I Will Just Go Buy It And Do A Clean Installation And BTW I Didn't Make A Back-up Disk As For I Can Only BackUp My Files Not My OS :( Anyways I'll Go For It And Hopefully The Next Time I'm Posting I Will Be Using Ubuntu Not Windows

---

### Post by Darael on 2009-12-17
First off, please ask all support questions where everyone can see them! To quote your PM:
[QUOTE=Lee3155]Thanks For Answering My Question.

The One Piece Of Info I Left Out Is The Biggest Problem Which Seems To Happen To Everyone.

DUAL BOOTING!

Since My Brother Said Not To Use Wubi Cause Of Dual Booting I Am Really Worried.

Do You Think I Will Be Ok With Dual Booting And Of My Laptop Is Up To The Standards Of Dual Booting?

Thanks

- Lee[/QUOTE]
Dual booting is not unsafe, especially with Wubi. Contrary to popular belief, system specs have little effect on whether a computer is capable of a dual-boot setup. The only real possibility of damage when setting up a dual-boot is when partitioning the hard drive, and Wubi doesn't do that. It uses disk image files, instead. So you should be fine, and as staf0048 says, you have a way out in the event of trouble.

---

### Post by wkulecz on 2009-12-17
> The only real possibility of damage when setting up a dual-boot is when partitioning the hard drive, and Wubi doesn't do that

Not true.  Most dual boot issues are grub problems, magnified this release by the introduction of grub2 with little notice.  While most can be fixed, its too easy to do real harm in a misguided attempt at a quick solution.

While playing with the Windows7 RC, installing Kubuntu 9.04 wiped my ability to boot into Windows 7.  I had to reinstall Windows 7 which wiped grub) and then re-install grub to be back to zero.  Fortunately I was just playing, but if you've got a lot invested in your Windows 7 setup, I'd strongly suggest buying a separate computer for Ubuntu and then you have a a way to learn about networking :)

--wally.

---

### Post by Darael on 2009-12-17
> **wkulecz said:**
> Not true.  Most dual boot issues are grub problems, magnified this release by the introduction of grub2 with little notice.  While most can be fixed, its too easy to do real harm in a misguided attempt at a quick solution.

While playing with the Windows7 RC, installing Kubuntu 9.04 wiped my ability to boot into Windows 7.  I had to reinstall Windows 7 which wiped grub) and then re-install grub to be back to zero.  Fortunately I was just playing, but if you've got a lot invested in your Windows 7 setup, I'd strongly suggest buying a separate computer for Ubuntu and then you have a a way to learn about networking :)

--wally.
Fair enough - but my point still stands, as Wubi chainloads GRUB from the Windows bootloader, meaning that it can't damage anyone's Windows bootability!

---

### Post by davec64 on 2009-12-17
Just to add to what everyone has said, you could also try the Live CD.
This boots the operating system from a CD and doesn't do anything on your Hard Disk.

Just another option you could try! :)

---

### Post by ST3ALTHPSYCH0 on 2009-12-17
Do make sure that your Windows install is defraged before installing WUBI

---

### Post by Darael on 2009-12-17
> **ST3ALTHPSYCH0 said:**
> Do make sure that your Windows install is defraged before installing WUBIGood point, it'll make sure the Wubi install runs as fast as possible.

---

### Post by sdowney717 on 2009-12-17
why bother with wubi?
just do a regular install and resize the partition.
It will run better.

---

### Post by wkulecz on 2009-12-23
Its the chainloading with the Windows boot loader where things can break.  Wubi broke the Windows boot of the first system I tried it on, but this was a while ago (6.10 or 7.04, can't really recall, it first I'd heard of wubi and I accidently used it on Windows2000 :(  ), hopefully its been fixed.

Unfortunately the LiveCD is just too slow to give a favorable impression of Linux, better than nothing I guess.  

But I have had issues where the  LiveCD working great (7.04 if I recall), but the installation left a broken Xserver that could do nothing but 640x480 which is close to unusable since many dilogs exceed this and the buttons end up unclickable.

There is just too much hardware variance out there to make blanket "it will work" statements.  If you will be harmed by breaking your windows system, dual boot is not for you!  Play it safe and get a second system.

Otherwise, it usually works, but would the crying you do if it doesn't and your Windows system breaks be worth the risk?  Only you can make the choice.

If you've still got your old computer, its a great place to try Linux for the first time.

--wally.

---

