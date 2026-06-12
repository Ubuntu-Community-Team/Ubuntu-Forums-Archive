---
title: "Updates need to be controlled better!"
date: 2006-06-16
forum: General Help
---

### Post by T313C0mun1s7 on 2006-06-16
I have been having issues with getting my ATI card to do direct rendering. So when I finally got it working at 4:00am after a solid three weeks of trying I was thrilled. That was until I got up at 7:00am that morning to find out it had reverted back to software rendering.

This evening I see there are about 56 updates waiting, so I do a precursory look to see what is getting updated and see a bunch of Gnome related stuff. I don't see any thing major like a kernel update (I look for that because I have several things that will break if I don't have the kernel headers correct) so I do the updates. I am notified that I need a reboot and I let it do so, only to be greeted with a kernel panic. It seems the kernel WAS updated after all, and my /boot partition was 100% full. I guess the update does not check for that?

Updates should NEVER break things this badly. If Ubuntu wants to be the de facto desktop distro then they can't let go breaking the OS every few update cycles. An inexperienced user would not have known how to recover from a kernel panic. Especially if this was there main computer - as it is mine.

If you are updating the kernel it should be in big red text, up front warning that it is going to do so. I know that the ATI issues are still being hacked out, but I wanted to take a hammer to the computer after the direct rendering broke again (I still have not managed to get it working again) and I understand that others had problems with mice not working and autologin breaking.

I don't know what the current testing cycle is on updates, but it does not seem to be enough. Maybe a testing group of users that volunteer to get updates prior to official release and report on bugs for a week or two prior to going official is in order. I understand that it is hard to test for every possible contingency, but it seems the pool of testing computers is not large enough to be sufficient given the number of bugs introduced my updates.

Rant over.

---

### Post by x64Jimbo on 2006-06-16
I agree. My kernel updated and it caused my VMWare installation to get all fouled up, and I had to reconfigure it. I'd like an option to "Never update kernel unless specifically requested."

---

### Post by glotz on 2006-06-16
Maybe the default install shouldn't come with linux-386 (meta) package but instead with just a (386) kernel package. (the meta package will always update)

---

### Post by RS3York on 2006-06-17
[QUOTE=T313C0mun1s7]I understand that it is hard to test for every possible contingency, but it seems the pool of testing computers is not large enough to be sufficient given the number of bugs introduced my updates.
[/QUOTE]

I agree that it would be wise for the update mechanism to check to see if there's is free space before updating, that would be a great feature.  

Although I wonder how fair it is to say that there needs to be a larger group of testers because of your particular case.  Re-read what you wrote, you concede that "it is hard to test for every possible contingency" but say that the testing can't be large enough because of "the number of bugs introduced [by] **my** updates".  

I know it sucks, but it's not "hard" to test for all contingencies - it's impossible.  Further the "average" user you cite probably doesn't know there's a difference between direct rendering and software rendering.  That doesn't make the behaviour excusable (if you know how to change a setting, that setting should stay) but I think it's hardly accurate to equate yourself with "the average user".  For example, looking at how you ran out of space for the kernal update in your /boot partition: How many "average users" would setup a /boot partition in the first place?  The average user doesn't even know what a partition is, let alone how to create them.  So that particular situation is somewhat artificially created, if you create a /boot partition then are you not responsible to manage that partition?

Still, some good suggestions.

---

### Post by grsing on 2006-06-17
I agree that there should be some sort of better examination or notification or something of kernel updates.  Somehow it managed to break my xorg.conf; luckily I had a working backup, so it only took 5 seconds to fix, but to a newbie, seeing that BSoD from the X server would be pretty off-putting.

---

### Post by T313C0mun1s7 on 2006-06-17
RS3York

Actually the **MY** was suppose to be **BY** and that was a typo. I don't claim to be an average user, I know I am an advanced user. This is just my point, an average user may not have known what to do when they got a kernel panic. Most likely the pool of volunteers would be advanced users, the one that can both benift the most and contribute the most. Putting out updates should [COLOR=#ff0000]NEVER[/COLOR] make the average user assumption, because it is us advanced users that spend large chunks of time getting there system just right that are always burned by that assumption.

I made a few bad assumptions myself I admit. I thought 128Mb would be large enough for a boot partition. Yet because Ubuntu like to add kernels without ever removing the old ones, and because I added a K7-smp kernel myself, I ran out of space after only 6 weeks of having Ubuntu installed.

Overall I like Ubuntu. I made the comment that they should be shooting to be the de facto desktop standard because I think they are the closest to the mark. They even managed to pull me away from Suse Professional. However, I think my point was that the current state of affairs for updates is unacceptable for a major distro jockeying to take a top spot in the Linux community at large. You start by taking over as the primary OS on home computers, but you finish by being the standard [Linux] desktop of business computers. Suse has made a nice try at this and they are doing very well. I think it might be possible for Ubuntu to get a very good share of that, but no IT Administrator will ever keep it around if updates break end users daily workstations. That point is unarguable.

EDIT: I just added a poll to this topic to see what the comunity might be willing to do. Please note the poll is public - people can see your vote. PLEASE explain why you answered the way you did, as the answers carry little relevence without the reason behind them.

I voted no, only because I don't think I have the experience [yet] with Linux to be of much help, and because this is my primary workstation and I can not afford to have it be out of production for any length of time.

---

### Post by RS3York on 2006-06-17
I agree that an update *should not* break another part of a system or cause some undesirable effect.  However, I think that it would be unreasonable to expect that an update will *never* do so.

I also agree that most IT Admins wouldn't put up with breakage in an ideal world, but if breakage never happened why even have in-house admins?  One could out-source the initial setup, and have them setup a script to update the machines every week.  Also if IT Admins left an OS every time an update caused headaches, I'm not sure the OS market share would be the way it is.  Further, IT Admins would likely be switching OS's much more often than they do.  Installing an OS and using it in a corporate space creates an inertia for that OS, making people reluctant to go through a total overhaul.

I'm not saying that an OS should be difficult, but I am saying that it won't be smooth sailing 100% of the time.

It would seem that we're in similar situations - I wouldn't call myself a Linux Pro by any stretch, this computer is my primary one and I can't have it down for many days at a time.  However, those same reasons are why I retain a Windows partition.  I use Ubuntu all the time, but should it break (or should I break it :) ) I can revert to Windows, look up the solution online and get any urgent work done - A FAT32 partition & a ReiserFS tool facilitate that option for me.

As for beta testing updates, I voted yes.  The primary reason being, we sort of do that already - We take updates on good faith that everything will be alright, but knowing that it's possible something could go wrong.  Also, if holding back updates for 2 more weeks can help the community, then why not?  My only concern is that depending on the vulnerability it may do more harm than good - by leaving machines susceptible while we test.  Security through obscurity may work for now, but if Ubuntu (and Linux in general) continue to gain steam it won't be some years down the road.

---

### Post by T313C0mun1s7 on 2006-06-17
[quote=RS3York]I also agree that most IT Admins wouldn't put up with breakage in an ideal world, but if breakage never happened why even have in-house admins?  One could out-source the initial setup, and have them setup a script to update the machines every week.  Also if IT Admins left an OS every time an update caused headaches, I'm not sure the OS market share would be the way it is.  Further, IT Admins would likely be switching OS's much more often than they do.  Installing an OS and using it in a corporate space creates an inertia for that OS, making people reluctant to go through a total overhaul.[/quote]

Ah, but I didn't say ANY OS, I said Ubuntu (or Linux in general). Windows, the OS you are surely refering to already has a 90's plus market share - this is why it stays on the desktop. Linux has to battle its way into the market that is already mostly owned my M$.

As for smooth sailing 100% of the time. Yes, that is a impossible expectation. However, smooth sailing better than 95% of the time is not. Ubuntu is lucky if something does not break close to every time. So how do you fix this? There are two things that you need to do. 1) increase the size of and the variables in the testing pool. 2) Don't make assumtions about who you are deploying to and what there systems are set up like. Yes a few asumptions must be made as there is a fuzzy line of how much customization is Ok before problems are caused by the end user rather than the update. I don't think I crossed that line by getting my Video card to work, by using VMWare, or by adding a /boot partition to play it safe. I might consider it my own fault if I installed all my apps from source, or moved all my configuration files around. People are making reasonable changes to there system and they are not getting tested against. I thing it is unreasonalbe as a user of a free OS to expect the developers to even be able to test against even a freaction of these changes. This is why I suggested what I did as a posible solution.

I feel that anyone can complain, but a complaint with out a suggested solution is just bitching.

Sorry if there are typos I am in a real hurry.

---

### Post by Doytch on 2006-06-17
I wouldn't beta test something like a kernel for the same reasons as Communist.  I don't have enough experience and I can't have my computer out of commission.

---

### Post by mlind on 2006-06-17
I think that update-manager is bugged if it didn't force you to accept some sort
of warning first. I don't use update-manager, but aptitude updated kernel only
after using dist-upgrade option.

---

### Post by RS3York on 2006-06-18
[QUOTE=T313C0mun1s7]Ah, but I didn't say ANY OS, I said Ubuntu (or Linux in general). Windows, the OS you are surely refering to already has a 90's plus market share - this is why it stays on the desktop. Linux has to battle its way into the market that is already mostly owned my M$.
[/QUOTE]

Windows stays on the desktop for a number of reasons: familiarity, ignorance to alternatives and lack of choice at retail, availability of support, availability of software and TCO among others.  A lack of update headaches is not a major reason for the maintenence of Windows' market share, if it was how many businesses (& people) would have jumped ship when Service Pack 2 hit Windows XP?  

I still stand by my point in my last post about IT Admins: If computer administration was so painless in any particular OS (Windows included) why doesn't every business move to that OS and remove the redundant IT admins from their full-time payroll?  Their skills would no longer be needed on a daily basis after all.

You claimed a few posts ago "the current state of affairs for updates is unacceptable for a major distro", but what is the current state of affairs?  
The majority of people don't seem to have problems with their updates and a few do, additional time is spent repairing the few - another day in human endeavour of computing.

[QUOTE=T313C0mun1s7]
As for smooth sailing 100% of the time. Yes, that is a impossible expectation. However, smooth sailing better than 95% of the time is not. Ubuntu is lucky if something does not break close to every time. 
[/QUOTE]

Ok let's take 95%, that's a good number.  Out of 100 updates downloaded, we need 95 properly functioning, successful installations or more.  As for this quote - "Ubuntu is lucky if something does not break close to every time" - I'd like to see a poll on who experiences breakage with Ubuntu's updates "close to every time".  Would that be breakage with 95% of updated packages?  That's the sort of statement that makes me critical of the test case.

[QUOTE=T313C0mun1s7]
So how do you fix this? There are two things that you need to do. 1) increase the size of and the variables in the testing pool. 2) Don't make assumtions about who you are deploying to and what there systems are set up like. 
[/QUOTE]

I already said I thought you made some good suggestions.  More testing is good, although the irony is even if these updates were delayed for a few months and tested more broadly - but broke your system - you'd still be suggesting more testing...which brings me back to my core point: *There's only so much testing that can be done because somebody's system will likely misbehave once it's released and while that security update is held back everybody's system is at risk*.

[QUOTE=T313C0mun1s7]
Yes a few asumptions must be made as there is a fuzzy line of how much customization is Ok before problems are caused by the end user rather than the update. I don't think I crossed that line by getting my Video card to work, by using VMWare, or by adding a /boot partition to play it safe. I might consider it my own fault if I installed all my apps from source, or moved all my configuration files around. People are making reasonable changes to there system and they are not getting tested against.
[/QUOTE]

What is reasonable in the term of user customizations is subjective I suppose.  Although as a side, the merits of the statement is interesting because if you considered this issue your fault, everything else sort of falls down doesn't it?

[QUOTE=T313C0mun1s7]
 I thing it is unreasonalbe as a user of a free OS to expect the developers to even be able to test against even a freaction of these changes. This is why I suggested what I did as a posible solution.

I feel that anyone can complain, but a complaint with out a suggested solution is just bitching.
[/QUOTE]

Again, I think that testing is a good thing.  But I still maintain that security patches have to get out in a timely manner.  I've already commended you on presenting a solution, but if we're going to analyze the OS for things to improve...shouldn't we also analyze the suggestions, weigh and refine them?

[QUOTE=T313C0mun1s7]
Sorry if there are typos I am in a real hurry.[/QUOTE]

That's fair :) .

---

### Post by T313C0mun1s7 on 2006-06-18
[quote=RS3York]Ok let's take 95%, that's a good number. Out of 100 updates downloaded, we need 95 properly functioning, successful installations or more. As for this quote - "Ubuntu is lucky if something does not break close to every time" - I'd like to see a poll on who experiences breakage with Ubuntu's updates "close to every time". Would that be breakage with 95% of updated packages? That's the sort of statement that makes me critical of the test case.[/quote] 

We could of course go back and forth on this forever and never come to an agreement, and since this is just a friendly discussion and will probably nerver catch the attention of Ubuntu administration, I feel I have vented my frustration enough. I do have a couple a quick points however. 1) This was not prompted by just my experience, but the large numbers of new threads I found after the update when I went looking to see what was happening to others. I felt lucky I was not having some of their problems. 2) My percentage of updates does not refer to packages, but update instances. If I see 65 updates available and let it perform the updates, that is one instance. That is based on the user perception of "how often something breaks". If I perform updates in this way 4-5 times a month and it break things 3 of those times, that justifies my numbers. If I have to re-do my vido card to get direct rendering, or fix my Firefox and Thunderbird icons every time there is an update cycle then it just jumps to "breaking something" 100% of the time.

[quote=Doytch]I wouldn't beta test something like a kernel for the same reasons as Communist. I don't have enough experience and I can't have my computer out of commission.[/quote] 
Actually I am not a communist, I am a FAR right wing conservative. So far right that I see republicans as hypocritical on the gay marriage and abortion issues because they are wanting to add laws and government in areas that are only of moral concern. This stands against the basic premise of the conservative small government idea.

My pseudonym is Tele-communist (for the most part) and refers to the open sharing of technology and ideas in the telecommunications world. It was rooted back at Berkley when people sat around in hot tubs eating brownies and talking about their projects. The Free Software Foundation rose out of such ideals and they are still alive today. Since it is one of the things that I really like about the computing community at large, I ended up with the username I did. Well, that and I was pretty much guaranteed no body else would be using it.

---

### Post by Mr. Picklesworth on 2006-06-18
I'm in a bit of a hurry so I have only skimmed this thread, so I'm writing this assuming the topic hasn't changed.

I just want to add my 2 cents.

The last update killed wireless for me, as well as many other people. These numbers of people for whom it has broken are presumably all the people who did not rely on public wireless access points (hey, it's possible; I know someone who lives across from a public library and uses their AP all the time... and wireless public Internet is becoming a more and more popular idea). Not only that, but I think it hurt my ability to reinstall ndiswrapper and reconfigure wireless in the old kernel, too. This means much wasted energy as I haul the brick that is my other computer into this room to plug it into the network in a desperate attempt to fix the wireless that I had previously spent ages nursing to life.
I admit that it's a bit selfish of me to complain about something so petty as a wireless network connection when I still have wired Internet, but I do see it as a bad omen and I'm sure lots of people looking into Ubuntu at this very moment think the same.

Now, this was easily fixed by acquiring the new linux-headers package, but it's scary to think what would happen had I no longer had an internet connection to do so... especially since the download for the new files at packages.ubuntu.com still gives me error404 and wasn't available until a day after the update. Besides, ndiswrapper should have been updated with a recompiled version for the new kernel.

Any update to something as Important as the kernel should undergo the following:
-Significant testing for any remotely important aspect. Networking, especially, should work as well as it did previously 100% of the time (no exceptions), since the Internet is effectively the only way to get an update to fix other problems that may have cropped up. Same goes for anything that may mess up and kill startup.
-Testing for these important aspects should be confirmed using web forms or the like to ensure that they actually do work. My experience with forums and bug trackers says that things can get lost, and some people get scared away by crowded bug trackers so just dump their problems on forums.

All updates that may change something significant should be documented along with the update. This documentation should include possible problems and possible fixes, since it is possible that said problems can disable one's access to the forums.

Now, it's obvious that such a ridiculous request is practically impossible, so take it primarily as a hyperbolic suggestion sort of thing; that is how far it would go in the perfect world, and we should try to get as close to that as possible.
I'm still dreaming in technicolour, but really: The last update gives the distinct flavour of being Very untested. There are loads of people reporting problems of all sorts as a result of it.
There are solutions:

First, Ubuntu has a huge community! Open up, guys; perhaps big upcoming updates could be talked about on something like the development release forums and tests released in the same "use at your own risk, but please tell us if it messes up" way... maybe a bit more prominently since it's really important to get these tested. Broken updates are a pain.

...And the reason why I do not believe this is a totally ridiculous claim: Dapper has 6 years of support; these things do not need to be rushed!
(Well, unless they're security updates :) ).

---

### Post by Quirky on 2006-06-18
Recent updates have been a bit odd - "code clean ups" being the main changes in most packages :confused: I'd have preferred to see just kernel updates, then just gnome updates a few days later, rather than changing 50 odd packages all on the same day.

However, if you are worried that an update may break things: don't update! No one is forcing you.  Edit /etc/apt/sources.list and comment out dapper-updates. Problem solved. Security fixes are not altered.

If you have a non-standard install, then you have to be aware that updates could "break" your changes. Be prepared for that. I've patched nautilus and libgtk to fix 2 bugs that annoyed me ([keys]("http://bugzilla.gnome.org/show_bug.cgi?id=105895") and [drops]("https://launchpad.net/products/fileroller/+bug/33707")) and I realise that updating nautilus and libgtk will break these again, but it's something I have to live with since I am 'non standard'.

---

### Post by Kilz on 2006-06-18
[QUOTE=T313C0mun1s7]I have been having issues with getting my ATI card to do direct rendering. So when I finally got it working at 4:00am after a solid three weeks of trying I was thrilled. That was until I got up at 7:00am that morning to find out it had reverted back to software rendering.

This evening I see there are about 56 updates waiting, so I do a precursory look to see what is getting updated and see a bunch of Gnome related stuff. I don't see any thing major like a kernel update (I look for that because I have several things that will break if I don't have the kernel headers correct) so I do the updates. I am notified that I need a reboot and I let it do so, only to be greeted with a kernel panic. It seems the kernel WAS updated after all, and my /boot partition was 100% full. I guess the update does not check for that?

Updates should NEVER break things this badly. If Ubuntu wants to be the de facto desktop distro then they can't let go breaking the OS every few update cycles. An inexperienced user would not have known how to recover from a kernel panic. Especially if this was there main computer - as it is mine.

If you are updating the kernel it should be in big red text, up front warning that it is going to do so. I know that the ATI issues are still being hacked out, but I wanted to take a hammer to the computer after the direct rendering broke again (I still have not managed to get it working again) and I understand that others had problems with mice not working and autologin breaking.

I don't know what the current testing cycle is on updates, but it does not seem to be enough. Maybe a testing group of users that volunteer to get updates prior to official release and report on bugs for a week or two prior to going official is in order. I understand that it is hard to test for every possible contingency, but it seems the pool of testing computers is not large enough to be sufficient given the number of bugs introduced my updates.

Rant over.[/QUOTE]

I just reinstalled from a backup. I have a Radon x200 and it has problems. I couldnt get the old drivers to work with the new kernel. The update just started, I looked, The Kernel update is labled as a kernel update. I didnt install it, but it is labled, you must have missed it in the long (93 items) list of updates.  They are listed as linux-<platform> and the platform is your platform. Also linux-modules.
Its also possible to lock the versions in synaptic and then they wont be upgraded unless you unlock them. The present update is for a local attack, thats low on my list of worries. But I can always unlock them if I need to.

---

### Post by skyboy on 2006-06-20
Yea, fast .... I think same as Quirky, if you have a working system, freeze the source.list and only do security updates. So you leave time for other non-standard people to fixe non-standard updates ! dirty work for those who have time : ) !! hehe

---

