---
title: "Question about CD / DVD ?"
date: 2006-06-06
forum: General Help
---

### Post by victorche on 2006-06-06
First of all, sorry if this is not the right place for my question. Second... I've tried to find an answer here on these forums, but I didn't...

My question is really simple:

What's the difference between Ubuntu-Desktop-CD and Ubuntu-DVD ?
On the main download page there isn't a link for DVD dowload yet... It says something like "Check back later"...
And on:
[http://releases.ubuntu.com/6.06/](http://releases.ubuntu.com/6.06/)
there are links for CD versions only...
But on:
[http://cdimage.ubuntu.com/releases/6.06/release/](http://cdimage.ubuntu.com/releases/6.06/release/)
There are links for DVD versions...

So I guess these DVDs are final?
And what's in there? Are they Live or for Installation? Do they have some extra packages? Or they contain both Ubuntu with Kubuntu?
Can I use those DVDs the same way as I can use the CD version?
Is there an Espresso Installer in those DVD versions?
I would like to have a link where the contents of those DVDs are described...

Thanks in advance!

---

### Post by deja2004 on 2006-06-06
AFAIK they're exactly the same just with additional packages (so you won't have to download them from the repos)

---

### Post by victorche on 2006-06-06
[QUOTE=deja2004]AFAIK they're exactly the same just with additional packages (so you won't have to download them from the repos)[/QUOTE]
Thanks, but this doesn't give me answers to all my questions...
At least a link to a wiki page or something? Please?
:roll:

---

### Post by victorche on 2006-06-07
Bump!

Sorry for posting again, but... I still have no answer :-\
I really want to know the differences... And the CD is almost 700 MB, the DVD is... 3215 MB... So the differences should be huge ;]

i need to know what will I get if install it from the DVD... In the .list file I can see that we have kde also in there... So I will have what? Ubuntu or Kubuntu? Or both?

And the iso images are there... But are they official? As on the main download page it still says... "DVD Version - Check back later" or something like that...

---

### Post by exclipy on 2006-06-07
I just looked at the list file.  It looks like it's like the alternate CD, but with more packages.  There are about 4000 packages on the DVD.  There are about 4700 packages in the main repository.  I'd hazard a guess and say that the DVD contains *almost* all the packages in the main repository.  I'd say that if you installed it, you'd get an Ubuntu desktop.  From there, you'd be able install the kubuntu-desktop package to get Kubuntu as well if you want.

---

### Post by victorche on 2006-06-08
[QUOTE=exclipy]I just looked at the list file.  It looks like it's like the alternate CD, but with more packages.  There are about 4000 packages on the DVD.  There are about 4700 packages in the main repository.  I'd hazard a guess and say that the DVD contains *almost* all the packages in the main repository.  I'd say that if you installed it, you'd get an Ubuntu desktop.  From there, you'd be able install the kubuntu-desktop package to get Kubuntu as well if you want.[/QUOTE]
Thank you! So you think these DVDs are final and official? Strange then that these are not announced on the main download site...

Ann maybe someone who installed those can tell me what's the result from installing 6.06 from a DVD?
:roll:

---

### Post by scxtt on 2006-06-08
no matter how "final" a cd or dvd is, it's never up-to-date - that's what the repositories are for (not patronizing your w/ that comment) ... either way you slice it you're in for a large download if you want to be immediately up to date after install (be it from a large dvd download or a repo update) ...

to be honest, i wouldn't even spend time thinking about "is the dvd better than the cd?" -- if i want to get installing quick, i'd get the cd -- if i want a nice, shiny dvd to put my dvd-burner to dvd-buring use - i'd get the dvd ...

otherwise i think it's a moot point to attempt to get to the bottom of the apples-and-oranges differences b/t the two ...

if you can get a live cd experience w/ the DVD (and it has more programs "installed" when you boot off of it) that's about the only way i'd think it has an advantage ...

---

### Post by exclipy on 2006-06-08
[QUOTE=scxtt]if you can get a live cd experience w/ the DVD (and it has more programs "installed" when you boot off of it) that's about the only way i'd think it has an advantage ...[/QUOTE]

Well, I think the DVD would be a good option for someone who isn't always connected to the Internet.

---

### Post by victorche on 2006-06-08
[QUOTE=exclipy]Well, I think the DVD would be a good option for someone who isn't always connected to the Internet.[/QUOTE]
Anyway... The answer is still far away...
1. Do we have Espresso Installer in the DVD?
2. Will we have Ubuntu or Kubuntu installed? /as there are KDE packages also in the DVD/
3. Is this final, official, etc... ? As on the main download page still says "For DVD - check back later" /Or something like that/

Hope this time someone can say a few words...

---

### Post by kinalus on 2006-06-08
Hi,
I installed 6.06 from DVD so I'll describe my experience in short.

The DVD boots a live Ubuntu from where you get an icon on your desktop to launch the installer. The only problem with the boot process was that it set my desktop resolution to 800x600 which I couldn't change using GNOME, so I had to change the xorg driver from nv to vesa to get 1024x768 resolution.

The installation process is pretty standard and doesn't have many differences to previous versions of Ubuntu.

Once you boot your newly installed system you get the usual set of applications without KDE (so I guess there aren't any differences from the CD version thought I didn't tried the CD so I can't be sure). If you put the DVD in your reader, Ubuntu detects the extra package lists and adds the DVD to the list of repositories. Almost all the additional software I had to install was in the DVD including some KDE apps. I didn't installed a full KDE desktop but I guess it's possible.

The DVD seems pretty up to date but once you go online you get some updates.
I hope I helped, have a nice installation.

Cheers

---

### Post by victorche on 2006-06-08
[QUOTE=kinalus]Hi,
I installed 6.06 from DVD so I'll describe my experience in short.

The DVD boots a live Ubuntu from where you get an icon on your desktop to launch the installer. The only problem with the boot process was that it set my desktop resolution to 800x600 which I couldn't change using GNOME, so I had to change the xorg driver from nv to vesa to get 1024x768 resolution.

The installation process is pretty standard and doesn't have many differences to previous versions of Ubuntu.

Once you boot your newly installed system you get the usual set of applications without KDE (so I guess there aren't any differences from the CD version thought I didn't tried the CD so I can't be sure). If you put the DVD in your reader, Ubuntu detects the extra package lists and adds the DVD to the list of repositories. Almost all the additional software I had to install was in the DVD including some KDE apps. I didn't installed a full KDE desktop but I guess it's possible.

The DVD seems pretty up to date but once you go online you get some updates.
I hope I helped, have a nice installation.

Cheers[/QUOTE]
Thanks!!! Perfect! The final question is... You said "boot a live Ubuntu"... With an icon for installation... Is this the Espresso Installer? A graphical one?

---

### Post by kinalus on 2006-06-08
[QUOTE=victorche]Thanks!!! Perfect! The final question is... You said "boot a live Ubuntu"... With an icon for installation... Is this the Espresso Installer? A graphical one?[/QUOTE]


Yes, it's Espresso installer with a nice GUI :D

---

