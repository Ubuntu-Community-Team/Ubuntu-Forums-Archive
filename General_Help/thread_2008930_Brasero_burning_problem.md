---
title: "Brasero burning problem"
date: 2012-06-23
forum: General Help
---

### Post by GreatDanton on 2012-06-23
As title says I have problem with Brasero. Several times I tried to burn an Iso image to cd, however without luck. I threw many cd's into thrash and I thought it was bad quality cd's. Today I tried another burner (K3b) which I downloaded from Ubuntu software center. I tried to burn iso image, and yes no problems.

So my question is-does anybody has the same problem like me, or Brasero burner works for you?

---

### Post by cortman on 2012-06-23
Brasero's been working fine for me so far (only burning ISO CDs).
Always helps to check the md5sum of any image you download.

---

### Post by GreatDanton on 2012-06-24
Bump! Anyone else experienced the same problem?

---

### Post by dbuday on 2012-06-25
I do.

CDs and DVDs too. They just became crap. Nothing on them. I get burning error warning every time.

First i thought i got bad CDs.

I got it worked different way. Since i got Gnome installed too, i switched to Gnome (from Unity/Ubuntu), and Brasero works.

How can it be? - same software, same system, same OS - other GUI - and it works

There is problem with Brasero in Unity.

---

### Post by tealflame on 2012-06-25
Same problem here.  I cannot burn any cd or dvd, they end up in the trash.  I tried K3b and that seems to work better.  K3b is almost like an old Nero clone from 10 years ago but it works.  

Of course, Windows 7 burns cds and dvds no problem.

---

### Post by nipunshakya on 2012-06-25
Seeing such problem with brasero, i started using k3b and rest is history... no more throwing of disks in the gutter now...

---

### Post by Rob7734 on 2012-06-25
Yes, I've also had problems with Brasero and like the rest of you, I thought I had bad discs. Sure ended up making my share of coasters. Thanks for bringing this up, Danton.

Rob

---

### Post by GreatDanton on 2012-06-26
> **dbuday said:**
> I do.
Since i got Gnome installed too, i switched to Gnome (from Unity/Ubuntu), and Brasero works.


With Gnome did you mean Ubuntu 2D or something else?

---

### Post by dbuday on 2012-06-27
I mean Gnome.

You can install it from USC - just type "gnome" in search field.
It will take some time to install. After restart you will find 3 new login options (Ubuntu, Ubuntu 2D, Recovery + Gnome, Gnome Classic and Gnome Classic (No Effects)).

I`m using Gnome Classic without effects (Compiz disabled), when i want to rest my processor.

Brasero works there.

I don`t know is there problem with Compiz or just Unity plugin.

It is unclear what is the right address for reporting this bug.
This MUST NOT be.

Brasero is standard Ubuntu application, and it MUST work in standard Ubuntu GUI.

---

### Post by mwclark4453 on 2012-06-27
I'm having the same problem as well.

---

### Post by GreatDanton on 2012-06-27
So, where and how can we write bug report for brasero?

---

### Post by nipunshakya on 2012-06-27
[https://www.launchpad.net](https://www.launchpad.net) .... you need to have an account there.... surf the site a bit and you'll know how to file a bug report..

---

### Post by Randymanme on 2012-06-27
> **GreatDanton said:**
> As title says I have problem with Brasero. Several times I tried to burn an Iso image to cd, however without luck. I threw many cd's into thrash and I thought it was bad quality cd's. Today I tried another burner (K3b) which I downloaded from Ubuntu software center. I tried to burn iso image, and yes no problems.

So my question is-does anybody has the same problem like me, or Brasero burner works for you?

Same here.  I could have written your post myself, except that I got sufficiently  nonplussed over the one failure that I immediately installed and used K3b. 

When I was using older, low-resource, computers, I avoided KDE like the plague (too much bloat).  But now, I feel free to go ahead and use KDE apps. 

By definition (as noted by Synaptic Package Manager), Brasero is "CD/DVD burning application for GNOME."   True, Unity (as I think I've read) sits on top of Gnome 3 in place of Gnome Shell, but I think it's reasonable that some things Gnome aren't going to fair well being filtered through Unity.

Cheers

---

### Post by BBQdave on 2012-06-27
> **GreatDanton said:**
> As title says I have problem with Brasero. Several times I tried to burn an Iso image to cd, however without luck. I threw many cd's into thrash and I thought it was bad quality cd's. Today I tried another burner (K3b) which I downloaded from Ubuntu software center. I tried to burn iso image, and yes no problems.

So my question is-does anybody has the same problem like me, or Brasero burner works for you?

Brasero gave me coasters. K3b is reliable. **Xfburn** is the best I have ever used, and you pull in less dependencies when you install.

If you are in KDE land, go with K3b. If you are using Gnome (Unity), I highly recommend **Xfburn** :D

---

### Post by nipunshakya on 2012-06-28
> **GreatDanton said:**
> So, where and how can we write bug report for brasero?
The following will teach you how to file a report:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by Alcidious on 2012-07-09
Brasero works for me when im just burning files... however, tonight Im trying to burn a working dvd from an iso file.  I received an error message:

"All required applications and libraries are not installed. Please install the following manually and try again:
 mplex(GStreamer plugin)
 dvdauthor(application) "

I searched the forums and found a user with the same problem, but the post is from 2010; I think he was using Ubuntu 10.4? I am using 11.10, you guys think the solution would be similar?

---

### Post by vasilbelarus on 2012-07-18
I am not often use disks and disk burning applications, but almost every time I tryed to use brasero it wasn`t working properly.(I trashed a lot of new disks).

---

### Post by kurt18947 on 2012-07-18
I think it also depends on your drive. I have an internal Phillips DVD-RW that offers limited speed choices - I prefer slower burn speeds.  I burn .iso s and occasionally the burn does not complete.  I have a Samsung USB burner - bought for a netbook - and it is much more reliable, offers more speed choices and the burned disks work in most drives.

---

### Post by Rob Glenn on 2012-07-20
Yes, I'm observing numerous issues.  The most serious are:

1)  Brasero burns corrupt images to disc.  Workaround is to uncheck option to burn direct.

2)  On a single machine, the burn options (burn direct, leave session open, use burnproof) have completely disappeared from the dialog.  No workaround (log out, reboot, reinstall, complete removal, log in as different user, etc.) works, this is by far the most serious to me because it renders Brasero pretty much useless on that machine.

This program worked great in Ubuntu 10.04.  I'm disappointed.

---

### Post by pakguru on 2012-09-10
The best way I have found  to burn a downloaded, Ubuntu operating system iso file to a blank CD is  not to use Brasero, it never seems to work and always tells me that my  blank disc has insufficient space. 
  I use GnomeBaker CD Writer/Burner, which can be installed from Ubuntu  Download Centre. After opening GnomeBaker be careful NOT to select one of the three tabs  in the 'Make new project' section - otherwise you will just copy the iso  file. You need to go to 'Tools' in the top menu bar and select 'Burn CD  Image' - that way you will get all the other files that you need to  install your new version of Ubuntu.
  Good Luck

---

