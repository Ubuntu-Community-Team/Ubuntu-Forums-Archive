---
title: "Open Office have become unusable"
date: 2011-04-18
forum: General Help
---

### Post by Ghost_Mazal on 2011-04-18
Lo all ,

I am having a big problem with my OO.
It has become completely unusable.

I enter data (in word processor) and it freezes when trying to save the document. It happens whether I try to save in odt or doc.

It has become completely unusable. Can anybody help me fix it please ?

OO 3.2

Thanx

---

### Post by mike555 on 2011-04-18
Before you uninstall it and install LibreOffice , you might try turning flash off, tools>settings> uncheck use flash.

---

### Post by Ghost_Mazal on 2011-04-18
> **mike555 said:**
> Before you uninstall it and install LibreOffice , you might try turning flash off, tools>settings> uncheck use flash.

There's no such option ???

---

### Post by mike555 on 2011-04-18
Sorry , I meant Java ........... just to see if it helps.

while your in there click on memory and set undo down to  20  .that should save some memory.

---

### Post by Ghost_Mazal on 2011-04-18
> **mike555 said:**
> Sorry , I meant Java ........... just to see if it helps.

while your in there click on memory and set undo down to  20  .that should save some memory.

Ok did both. No change.

---

### Post by lhb1142 on 2011-04-18
> **Ghost_Mazal said:**
> Lo all ,

I am having a big problem with my OO.
It has become completely unusable.

I enter data (in word processor) and it freezes when trying to save the document. It happens whether I try to save in odt or doc.

It has become completely unusable. Can anybody help me fix it please ?

OO 3.2

Thanx

I suggest that you install **LibreOffice**. I gather that you will _not_ be upgrading to Ubuntu v. 11.04 (you'd have to first go through 10.10 to do that) so, in my opinion, the easiest way to install **LibreOffice** is to first install **Ubuntu Tweak** < [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) >.

Once **Ubuntu Tweak** in installed, go to its *Source Center* (left side under Applications), click on *Sync* to upgrade, if necessary, and scroll down to *LibreOffice PPA*. This will activate this personal package archive and, once installed, you will receive a notice to install the actual **LibreOffice** program. Check all of the options and proceed.

This will completely remove **OpenOffice** and will replace it with **LibreOffice**.

This method was how I installed **LibreOffice** on my computer. I found that most, but not all, of my previously configured **OpenOffice** preferences carried over. You will want to check, of course.

I had had no problems at all with **OpenOffice** but, having read that it was to be dropped as the default word processing program in v. 11.04, I decided that I wanted to give **LibreOffice** a try prior to the OS upgrade.

I like the new program very much and I hope that this will solve your problem.

---

### Post by mike555 on 2011-04-18
Better to uninstall OpenOffice first , then install LibreOffice .... I didn't and had trouble ,so ended up completely uninstalling and reinstalling ...

 [http://www.webupd8.org/2011/01/install-libreoffice-in-ubuntu-from.html](http://www.webupd8.org/2011/01/install-libreoffice-in-ubuntu-from.html)

---

### Post by Ghost_Mazal on 2011-04-19
Ok thanx guys , will try it tonight when I get home.

So I can't just remove OpenOffice and install Libre with the deb package found on their site ?

---

### Post by Vaphell on 2011-04-19
you can - software installed from debs works but it doesn't update automatically and in case of uninstall you may need to perform some manual labor. Using repositories is recommended because system does everything for you.

---

### Post by Ghost_Mazal on 2011-04-19
IC. Well the updated for it doesn't concern me at this stage. 11.04 is around the corner then I'll be switching to that. And I don't think I will need to uninstall it also before the switch happens.

I basically want a working office till then to get me to 11.04's release.

What I want to do:

Remove OpenOffice.
Then install LibreOffice with the deb package.
Then add that PPA as in that walkthrough.
Then just install the gnome integration and language pack
packages with apt-get

Will that work ?
(The only reason why I am thinking to work the deb package in is because I already downloaded it and don't want to waste bandwidth again to do that part with apt-get)

So basically I want to replace the apt-get of LibraOffice main package in that tutorial with the deb package and still do the last 2 steps with apt-get.

That's my plan now.

---

### Post by Ghost_Mazal on 2011-04-19
Ok I went through the whole process of removing OpenOffice and installing LibreOffice. Everything went well.

However , the problem is still EXACTLY the same in LibreOffice as it was in OpenOffice. When I save a document it freezes up :(

---

### Post by Irony on 2011-04-19
Start libreoffice via terminal and save a document and see what messages terminal gives.

Copy and paste the result here.

---

### Post by Ghost_Mazal on 2011-04-19
Doesn't say anything.

I enter the command

```
libreoffice
```

Libreoffice opens and no messages are outputted in terminal.
It freezes until I eventually force quite it and then the terminal just return to blinking cursor.

No messages in terminal

---

### Post by samacaster on 2011-04-19
Try to install a light word program like Abiword. It uses almost no resources and will use its own configuration. See if the same problem occurs. If it doesn't, the problem is in the initial install of OpenOffice.

When removing OO, use Synaptic as it will remove the program in its entirety. Left-overs will show up in Residual Config. Remove these left-overs and OO will be history.

---

### Post by Irony on 2011-04-19
> **Ghost_Mazal said:**
> Libreoffice opens and no messages are outputted in terminal.
It freezes until I eventually force quite it and then the terminal just return to blinking cursor.

No messages in terminal
So you are saying that libreoffice won't even run?

---

### Post by Ghost_Mazal on 2011-04-19
> **Irony said:**
> So you are saying that libreoffice won't even run?

Nope. It runs perfectly until I save a doc. Then it freezes

---

### Post by Ghost_Mazal on 2011-04-19
> **samacaster said:**
> Try to install a light word program like Abiword. It uses almost no resources and will use its own configuration. See if the same problem occurs. If it doesn't, the problem is in the initial install of OpenOffice.

When removing OO, use Synaptic as it will remove the program in its entirety. Left-overs will show up in Residual Config. Remove these left-overs and OO will be history.

Abiword works and saves without freezing at all.

This is so frustrating. How can a main app like OO just brake down for no reason after working before.

Also , so you are saying that the reason for Libre also not working is because of the initial install of OO. OO worked perfectly before , and I have checked , everything of OO is removed but still Libre is not working.

---

### Post by lhb1142 on 2011-04-19
> **Ghost_Mazal said:**
> Abiword works and saves without freezing at all.

This is so frustrating. How can a main app like OO just brake down for no reason after working before.

Also , so you are saying that the reason for Libre also not working is because of the initial install of OO. OO worked perfectly before , and I have checked , everything of OO is removed but still Libre is not working.

Have you installed any new programs recently? If you installed a new program just prior to the initiation of your OpenOffice problems, that new, otherwise unrelated, program may be at fault, *especially* if it was installed from somewhere other than the Synaptic Package Manager or the Ubuntu Software Center.

When I was first starting out with Ubuntu almost three years ago, similar problems happened to me (not with OpenOffice, but with other programs). My solution? A *complete* re-installation of Ubuntu (which isn't as onerous as it sounds).

I keep a list (on paper!) of everything I install on my computer and it's easy to reinstall everything which was installed previously. I also keep backups on an external hard drive of My Documents (which includes a folder containing my Firefox bookmarks), Music, Pictures, Videos, etc. (backing up several times a week); it is quite easy to restore all of that to my fresh installation.

Rather than 'tear your hair' trying to solve this problem, why not just rely on Abiword (which you say is working fine) for the next couple of weeks and then, when Ubuntu v. 11.04 is released, download the CD, wait a week or two (checking this forum just to make sure there are no unforeseen 'bugs'), 'wipe' your computer (after backing up the aforesaid Documents, etc. folders) - I use [DBAN]("http://www.dban.org/") - and then install the new Ubuntu version. (DBAN takes several hours, depending on the size of your hard drive so I recommend that you 'wipe' your computer overnight.)

That should end your problems. I might mention that I myself had formerly installed some programs from other than the official repositories, mostly with no problems, but, on occasion, with *major* problems such as you have experienced and I reinstalled Ubuntu just as I'm suggesting to you. (I had to do this several times over the course of two or so years; you don't learn anything by doing things 'right' - you learn from your mistakes. At least that's how I've learned! Fortunately for me I have *not* had to reinstall Ubuntu recently.)

I have learned (the hard way!) to be careful and, while this may not necessarily have been the cause for your problems, I hope you will be very careful in what you install.

In any case, I wish you the very best of luck. If someone here (more knowledgeable than I am) can help you and you are able to 'fix' your computer such that LibreOffice works normally, great. But if not, my 'solution' will absolutely work.

---

### Post by Ghost_Mazal on 2011-04-19
> **lhb1142 said:**
> Have you installed any new programs recently? If you installed a new program just prior to the initiation of your OpenOffice problems, that new, otherwise unrelated, program may be at fault, *especially* if it was installed from somewhere other than the Synaptic Package Manager or the Ubuntu Software Center.

When I was first starting out with Ubuntu almost three years ago, similar problems happened to me (not with OpenOffice, but with other programs). My solution? A *complete* re-installation of Ubuntu (which isn't as onerous as it sounds).

I keep a list (on paper!) of everything I install on my computer and it's easy to reinstall everything which was installed previously. I also keep backups on an external hard drive of My Documents (which includes a folder containing my Firefox bookmarks), Music, Pictures, Videos, etc. (backing up several times a week); it is quite easy to restore all of that to my fresh installation.

Rather than 'tear your hair' trying to solve this problem, why not just rely on Abiword (which you say is working fine) for the next couple of weeks and then, when Ubuntu v. 11.04 is released, download the CD, wait a week or two (checking this forum just to make sure there are no unforeseen 'bugs'), 'wipe' your computer (after backing up the aforesaid Documents, etc. folders) - I use [DBAN]("http://www.dban.org/") - and then install the new Ubuntu version. (DBAN takes several hours, depending on the size of your hard drive so I recommend that you 'wipe' your computer overnight.)

That should end your problems. I might mention that I myself had formerly installed some programs from other than the official repositories, mostly with no problems, but, on occasion, with *major* problems such as you have experienced and I reinstalled Ubuntu just as I'm suggesting to you. (I had to do this several times over the course of two or so years; you don't learn anything by doing things 'right' - you learn from your mistakes. At least that's how I've learned! Fortunately for me I have *not* had to reinstall Ubuntu recently.)

I have learned (the hard way!) to be careful and, while this may not necessarily have been the cause for your problems, I hope you will be very careful in what you install.

In any case, I wish you the very best of luck. If someone here (more knowledgeable than I am) can help you and you are able to 'fix' your computer such that LibreOffice works normally, great. But if not, my 'solution' will absolutely work.

Nope , didn't install anything new just before the problems started. This is a case of something just breaking down. VERY disappointing as I always raved about the stability of Ubuntu and one of the main reasons I switched to it. Guess it just isn't so as it let me down now for no reason.

Like I said in an earlier post , I just need a usable office app till 11.04 comes. So yeah , not gonna break my head about it now. Abi solved the word problem , but I have no solution for spreadsheets. Yes , that is also borked.

Problem is , I will have to struggle for quite a while. I never install a new distro version immediately on my main pc. I install on my dev pc and gradually build it up and test it and do the updates until I am happy that it's stable enough to go onto my main pc. So I will still be on this install on my main pc for a while , with no working office app as there doesn't seem to be any fix for it other than re-install.

I'm not gonna consider re-installing my main pc at this stage. Will rather spend the time building up 11.04 when it comes. Apart from all the time wasted to rebuild a proper system with all the apps and support needed too much bandwidth will be wasted with the tons of apt-get installs. Just because 1 app suddenly fails.
Just don't know what I'm gonna do with my spreadsheets.

---

### Post by Irony on 2011-04-20
gnumeric is very fast for spreadsheets.

---

### Post by SeijiSensei on 2011-04-20
Does it still freeze if you use Save As and choose a different name for the document?  OO has some method of document locking that I haven't really taken the time to understand.  Is the document on a network share or on your local hard drive?  The locking issue arises for me from time to time while editing documents stored on my NFS server.

---

### Post by johjeff on 2011-04-20
How much free space do you have in root and home? What about swap space?

---

### Post by Ghost_Mazal on 2011-04-20
> **SeijiSensei said:**
> Does it still freeze if you use Save As and choose a different name for the document?  OO has some method of document locking that I haven't really taken the time to understand.  Is the document on a network share or on your local hard drive?  The locking issue arises for me from time to time while editing documents stored on my NFS server.

Save as also freezes up.
Document is local in my Home folder.

> **johjeff said:**
> How much free space do you have in root and home? What about swap space?
Root has almost 400gig free space
Home has 80gig free space
Swap partition is 4gig , unused as only 28% of my main 4gig RAM is being used. So plenty off free ram and swap and HDD space

---

### Post by Hagar Delest on 2011-04-20
Try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

---

### Post by Ghost_Mazal on 2011-04-21
Will give that a try tonight thanx.

---

### Post by Ghost_Mazal on 2011-04-21
> **Hagar de l'Est said:**
> Try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

Doesn't help either. Still the same.

---

### Post by lhb1142 on 2011-04-21
> **Ghost_Mazal said:**
> Nope , didn't install anything new just before the problems started. This is a case of something just breaking down. VERY disappointing as I always raved about the stability of Ubuntu and one of the main reasons I switched to it. Guess it just isn't so as it let me down now for no reason.

Like I said in an earlier post , I just need a usable office app till 11.04 comes. So yeah , not gonna break my head about it now. Abi solved the word problem , but I have no solution for spreadsheets. Yes , that is also borked.

Problem is , I will have to struggle for quite a while. I never install a new distro version immediately on my main pc. I install on my dev pc and gradually build it up and test it and do the updates until I am happy that it's stable enough to go onto my main pc. So I will still be on this install on my main pc for a while , with no working office app as there doesn't seem to be any fix for it other than re-install.

I'm not gonna consider re-installing my main pc at this stage. Will rather spend the time building up 11.04 when it comes. Apart from all the time wasted to rebuild a proper system with all the apps and support needed too much bandwidth will be wasted with the tons of apt-get installs. Just because 1 app suddenly fails.
Just don't know what I'm gonna do with my spreadsheets.

You say you don't want to effect a complete reinstall on your main computer *but*, from the sounds of it, that's exactly what you're going to have to do.

I recommend that you wait until the new (11.04) CD download is available and then just use it (following my 'wipe & install' instructions in my previous post).

Ubuntu *is* a very stable and reliable platform *but* 'things' can happen to any system. (You may know that problems occur with Windows far more often than they do with Linux - there may be just as many problems with Mac too - but no computer operating system is 100% free from unexplainable glitches.)

I'm pretty certain, from what I've read here, that you are *not* going to be able to 'fix' your computer. At least so far no one has been able to provide a solution and you appear to have tried everything suggested.

Rather than continue to exercise in frustration, consider that 11.04 is coming in just a week; I *recommend* that you wait an additional week or so after the release, checking here on the forum to see if there is any unforeseen problem(s), but then, when you are satisfied that all is well (and it probably will be), and after backing up all of your data (and noting the programs you have installed currently), just 'wipe & reinstall.'

That's my suggestion, anyway. Best of luck!

---

### Post by Ghost_Mazal on 2011-04-21
Yeah not bothered by this at all anymore. (just test things as people suggest them). Abi and Gnumetric works so good I don't think I'll even use Libre in 11.04. Will probably remove it and use Abi and Gnumteric further on in 11.04 as well.

---

### Post by lhb1142 on 2011-04-22
> **Ghost_Mazal said:**
> Yeah not bothered by this at all anymore. (just test things as people suggest them). Abi and Gnumetric works so good I don't think I'll even use Libre in 11.04. Will probably remove it and use Abi and Gnumteric further on in 11.04 as well.

Sorry to keep bugging you but I *strongly* recommend that, if you do upgrade to 11.04 (which you will have to do by installing it from the CD - unless you want to go through a network installation *twice*, from 10.04 to 10.10 and only then to 11.04 - that would be quite time-consuming), you do *not* remove LibreOffice (or any other 'standard' program), even if you do not plan to use it.

I found that, by removing standard programs, I made the OS completely unstable (these program removals evidently taking along some components otherwise essential for correct operation); that was one of the first reasons why I had to effect a complete re-install a couple of years ago.

So if you do install 11.04 from the disc (I recommend wiping the computer first as I had mentioned), leave LibreOffice (which will be standard in 11.04) alone; you can still add and use the other office programs which you prefer. (Of course, after you have effected installation of 11.04 from the CD, LibreOffice will then work correctly.)

If you do not even want to *see* LibreOffice, go into System->Preferences->Main Menu and then, in the Applications list on the left, choose Office and then just uncheck anything you do not wish to see. The program(s) will still be there (and will remain fully functional) but, when you go into Applications, you will not see them listed. (You can do this for *any* program(s) in any of the Applications.)

This works in 10.10. I do not know if this method will still work in 11.04 but I hope it will; there are several programs which will be standard (such as Banshee) which I will not want to even see (I dislike Banshee, much preferring VLC). But I have no intention of removing them; I have learned my lesson!

One of the reasons I keep 'harping' on this subject is something no one else seems to have mentioned: if LibreOffice is corrupted on your computer (and is not easily fixed - as it apparently cannot be), other programs may be affected as well. This could eventually bring down your entire computer. I believe that it is better to do a complete 'clean' reinstall *now* (after backing up all your data) rather then wait until something really bad happens. I'm not saying that it *will* - but it wouldn't surprise me if it *did*. After all, *something* caused LibreOffice to become corrupt. And who knows what that *something* may also do to your computer some time down the road?

I apologize for my keeping on repeating my suggestions on this subject. I certainly hope you are not offended or annoyed. That is definitely not my intention. (I can be *very* annoying - just ask my wife!)

Again I wish you the very best of luck.

---

### Post by Dale61 on 2011-04-22
> **mike555 said:**
> Better to uninstall OpenOffice first , then install LibreOffice .... I didn't and had trouble ,so ended up completely uninstalling and reinstalling ...

 [http://www.webupd8.org/2011/01/install-libreoffice-in-ubuntu-from.html](http://www.webupd8.org/2011/01/install-libreoffice-in-ubuntu-from.html)

I went the other way.  I installed LO first, made sure it did actually run, then uninstalled OO.  I haven't had a single cause for concern with LO.

---

### Post by Ghost_Mazal on 2011-04-22
Don't worry , I'm not new at this. I know how to do new install and have very good double automatic backups. If she crashes completely I will be ready ;) But I highly doubt she will. I see me working quite a while still on this install while I smooth out 11.04 on my dev pc to bring it over.

---

