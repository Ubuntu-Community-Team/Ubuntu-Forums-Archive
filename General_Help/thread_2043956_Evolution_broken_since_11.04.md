---
title: "Evolution broken since 11.04"
date: 2012-08-17
forum: General Help
---

### Post by Manyette on 2012-08-17
I feel like the guy who just didn't get the memo! But if I may, I'd like to ask 3 questions.

I upgraded from 10.10 to 12.04. I found Evolution broken in all the releases since 10.10 This seems to be true lubuntu as well and also in some other distro's.

1 - Can someone tell me if there is something I am missing?

2 - If not, can someone recommend a mail client with calendaring, since for my usages, Thunderbird and Lightning an not workable.

3 - If none of the above, then can someone recommend a calendaring app that will run standalone with pop up notifications.

---

### Post by Manyette on 2012-08-19
<bump>  Anyone?

---

### Post by garyzw on 2012-08-19
I tried it the other day and found it was buggy on 12.04 but it worked. I went back to Thunderbird.

---

### Post by qamelian on 2012-08-19
What seems to be broken? Evolution is working fine for me and has done on every Ubuntu release. If you can provide more detail, maybe someone can provide a more helpful response.

---

### Post by Manyette on 2012-08-19
Hi garyzw. Well I guess you could consider it buggy, but it's buggy to an extent that makes it totally unusable. Send spooling doesn't work at all. Edit functions also do not work, along with many other more subtle bugs. I thing "broke" is a better description. And of even more interest is that it is broken this way in many other *buntu distro's as well.  All, as near as I can determine.

---

### Post by Manyette on 2012-08-19
> **qamelian said:**
> What seems to be broken? Evolution is working fine for me and has done on every Ubuntu release. If you can provide more detail, maybe someone can provide a more helpful response.

Hi Gamelian,
The most obvious problem is that the send message is not spooled to the outbox, but instead stays on the desktop until the send is complete, and never goes into the outbox. Also, the calendar function does not pop up reminders. The edit functions (font size, color selections, and cut and paste functions either do not work at all, or are erratic. If the send message is large, or contains graphics, it obscures the desktop for a time before you can see the destop again. There are others that are too numerous to mention.

Can you advise what version os the OS and Evolution you are currently usisng? It would be a huge help if I could get it to run as you do. Thanks.
Don

---

### Post by qamelian on 2012-08-19
I'm currently testing 12.10 on my test box and 12.04 on my main desktop. In 12. 10 I'm currently running 3.5.5, while in 12.04, I'm running 3.2.

---

### Post by Manyette on 2012-08-19
Hi qamelian,
Well, I guess I'll have to learn how to build it, because the repos's are still only up to 2.8 or thereabouts. And I just don't understand why, beause the same problems are still in Mint, Mint XFCE, and several other *buntu distros. But I do thank you for the info.  I'll try to do a build.and hope that fixes the problem.

---

### Post by Manyette on 2012-08-19
Hi qamelian,
Ooopa! I just checked and found that I'm running version 3.2.3, and the send spooler not working is still at fault in this version with 12.04.  I'm assuming the rest of the problems are still there as well, but Ill check further, so I don't understand how 12.04 with 3.2 is working for you.

---

### Post by qamelian on 2012-08-20
> **Manyette said:**
> Hi qamelian,
Ooopa! I just checked and found that I'm running version 3.2.3, and the send spooler not working is still at fault in this version with 12.04.  I'm assuming the rest of the problems are still there as well, but Ill check further, so I don't understand how 12.04 with 3.2 is working for you.
I don't know what to tell you. I've been using evolution since before I started with Ubuntu 4.10 and I don't recall ever having any issues with it, except for minor glitches when I'm running a development version. From other threads I've seen though, you don't appear to be the only one, so maybe i've just been lucky!

---

### Post by dcstar on 2012-08-20
> **qamelian said:**
> I don't know what to tell you. I've been using evolution since before I started with Ubuntu 4.10 and I don't recall ever having any issues with it, except for minor glitches when I'm running a development version. From other threads I've seen though, you don't appear to be the only one, so maybe i've just been lucky!

It's amazing how some people declare Evolution is "broken" while others have few - if any - issues at all.

I run Evolution with multiple mailboxes - POP, IMAP & Exchange 2003 - and have no issues at all. I also have been using it since 4.10.

Most of the Evolution "it's broken" threads seem to eventually get resolved when people actually outline the DETAILS of their problem.

---

### Post by Manyette on 2012-08-20
Hi David,
Well, I don't have an answer for you.  I too have been using evolution, since it is my favorite, and I really do need the calendaring function, for my memory isn't what it used to be. However I listed the problems I am seeing after a couple of downloads, and trying it with Mint, Mint LXFE, and several other distro's. All have exhibited the problems I've listed to some degree or another.  In Mint, which has two of those problems, while Mint LXFE has only one of the majors I've listed, all of the *buntu's have had most of them. Believe me, I wish I didn't. And to be honest I could easily live with the fact that it doesn't spool to the outbox even if annnoying, but not having the calendaring popups is a killer for me. Worse yet, people are telling me that they have no problems with the same version of 12.04 and Evolution version that I am using.  I am baffled, but it is not workin.

---

### Post by garyzw on 2012-08-20
One issue I had was that every time I re-booted my computer and then started Evolution was I had to enter the keyring password again another was I would have to manually change the fonts each time I sent an email as it would not save the font selection from one time to another.

---

### Post by Manyette on 2012-08-20
Hi garyzw, Well, I noticed when I was trying various distro's, trying to find one in which Evolution wasn't broken, that some of them asked for the keyring password, and others did not.  For that reason I was convinced for a while that it was other distro's who had stripped out unity or other things that affected that, but finally concluded that I was in error, since 12.04 also had different problems, and still the "standard" of 12.04 also would not spool the send messages into the outbox.

To be honest, what disturbs me the most is that Evolution version 3.2.3 seems to perform differently on the various *buntu distrobutions.  For example two of the major problems, (Not spooling send msgs, and no calendar pop-ups) both appear in Mint 13, but only one of them appears in Mint 13 XFCE. I filed bug reports on these in launchpad, and as of a day or so ago they are still marked as new and unassigned, yet some were filed prior to the release version. I begin to that only Thundebird is going to be supported.

---

### Post by garyzw on 2012-08-20
I read that development for Thunderbird was going to be discontinued--have you heard this?

---

### Post by Manyette on 2012-08-20
Hi garyzw, Yes that was announced that they will no longer develop Thunderbird, even though some on the forums claim there are still bugs in it. When they announced no more development, they also said that support would have to come from the community. I really don't care for Thunderbird, so it is not an options for me, since their calendaring function just isn't up to the task for my purposes.That's why I prefer Evolution.  If it isn't available at some point soon, I'm going to have to consider SuSE or one of the other distro's, where Evo still seem to work.  Not a choice I'd prefer.

---

### Post by Manyette on 2012-09-03
Hi Gamelian,
Well, I'm beginning to think that this only affects the 2D and 3D versions of *buntu.  As I'm running on an I7 laptop, those are my only options in 12.04, and of course the same problem exists in mint to some degree as well. I've given up and gone back to 10.10 Maverick until some other viable option arises.

---

### Post by dcstar on 2012-09-04
Still no DETAILS from the OP on how this "broken" Evolution is actually set up.

Is it using an IMAP/POP/whatever mail server, is it set up to use a local SMTP server or and external server that requires a login etc.? How was it initially set up, does it behave the same on a different user account? Was it migrated as part of an ongoing cycle of "Upgrades" from before the last working system instead of fresh installations?

No one in this thread has any idea about these details, except the OP.

No wonder people can't get things addressed.

---

### Post by Manyette on 2012-09-04
Hi DCSTAR,
Mostly because I don't know what will help but for your questions, it's simple POP/SMTP, and in all cases is a fresh install of one of *buntu 12,04 or one of it's derivatives, such as Mint, and I've tried most if not all of them, all fresh installs. And as I said before, Evolution version 3.2.3 seems to perform differently on the various *buntu distrobutions. For example two of the major problems, (Not spooling send msgs, and no calendar pop-ups) both appear in Mint 13, but only one of them appears in Mint 13 XFCE. I filed bug reports on these in launchpad, and as of a day ago they are still marked as new and unassigned, yet some were filed prior to the release version. (Bugs 1001430 & 1006596) And of course I would happily answer any questions asked. For info it's on an I7 laptop and only the 3D and 2D versions are available on that machine. Same problem exists on my wifes HP machine. Does this help at all?
- Don

---

### Post by newb85 on 2012-09-04
Manyette,
What email service are you using?
Are your calendars local, or hosted on a server?

---

### Post by Manyette on 2012-09-04
Hi newb85,
E-Mail is server is from Cox Cable and Calendar is strictly local. Keep in mind that all works well with previous distro's. I'm back to Maverick to keep it working. Anything beyond that fails.

---

### Post by Manyette on 2012-12-11
This problem has been solved.  For information for others, Evolution will not run on a Toshiba P755 I7 machine.  Works fine on other machines, in particular an ACER and a HP. I do not know why, but this was the problem.

---

### Post by dsmithnc on 2013-02-16
I am using Evolution 3.4.2 on Peppermint3.0.  I have solved all of the receive problems for email except for Evoltuion not remembering passwords when all those selections are checked.

Sending email from Evolution is a continuting nightmare. I have not been able to sucessfully send email.  I keep getting "service not connected" or "TCP connection reset by peer."

I like Evolution, especially the calendaring function, which by the way wouldn't work with Evoltuion 3.2 but works fine with 3.4.  However, the email difficulties with it seem to be insurmountable.

Fortunately, my Thunderbird installation is still intact.

****

---

### Post by Manyette on 2013-02-22
A final post on this subject.  Of interest to those who need Evolution.  I can now state positively that the Evolution "problem" is in the Kernel of the releases since 11.04.  I have moved to Sabayon 11, where Gnome 3 is used and all of the Evolution functions work perfectly on the same machine which has not had it working on any distro between 11.04 and current 12.10 of *buntu or derivative, as well as many other distro's. In Sabayon all functions work with this machine, just as they did in 10.04 and 10.10.
It's a good solution if you need Evolution.
Goodbye *buntu
- Don

---

