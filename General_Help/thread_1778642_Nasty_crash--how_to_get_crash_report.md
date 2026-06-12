---
title: "Nasty crash--how to get crash report?"
date: 2011-06-09
forum: General Help
---

### Post by VanillaMozilla on 2011-06-09
I have a nasty crash on OpenOffice.org that terminates the login session.  There's a bug report here:  [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/792841](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/792841) that has been marked invalid because I don't have a crash report for it.

Does anyone know how to get/find a crash report either for OOo or for the login session (Gnome/X whatever)?  There are some incorrect instructions in the bug report on how to do this.  There are an awful lot of logs on the computer, and searching blindly for (possibly nonexistent) crash reports is proving to be a fool's errand.

---

### Post by ianc1 on 2011-06-09
I think Ubuntu's crash reporting is via Apport, see [https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport).

The following is from the web page and is how to turn it on

Apport is not enabled by default in stable releases, even if it is installed. There are two ways to enable it. 

[LIST]
[*]If you want to debug a specific program once, just do: sudo service apport start force_start=1
[/LIST]
Then  you can simply trigger the crash again, and Apport's dialog will show  up with instructions to report a bug with traces. Apport will be  automatically disabled on next start. 
If you are triaging bugs, this is the best way to get traces from bug reporters that didn't use Apport in the first place. 

[LIST]
[*]To enable it permanently, do this: sudo nano /etc/default/apport
[/LIST]
... and change enabled from "0" to "1".

The age states a few reasons for not having it permanently enabled.


I hope this helps.

---

### Post by VanillaMozilla on 2011-06-10
Thanks very much for your reply.  I have one other question.  Do you have any idea where to get debugging symbols for OpenOffice.org in Maverick, or what the packages are called?  This isn't obvious.

---

### Post by VanillaMozilla on 2011-06-10
And there is one other thing for the record.

Your reply was SO much more helpful than the documentation, and I'm very appreciative.  You probably know that the user is presented with massive amounts of incorrect, incomplete, and fragmented information on how to report bugs.

For example, it would be SO helpful if apport would give some hint that you have to start it before the bug.  When you run it, the program gives every indication that a service has been running all along, and that it has collected all the information that it's going to.  Nothing here: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) gives any hints about it either.

I could go on and on about poor documentation, but rants like this go nowhere unless they're written by Eric Raymond.  Sigh.  Thanks again for your help.

I'm within an inch of throwing it in on this bug and never filing another bug report.  But I may write just one more bug report:  hire an editor and give him/her vast power to hire and fire peopl.  I just decided that's what I'm going to do.

---

### Post by ianc1 on 2011-06-10
Sorry I know nothing about the Open Office debugging symbols.  I looked at their wiki and could only see information on building it with debugging options and Non Product Builds.

I only know about Apport because the other day I found an error message in my boot.log.

I'm unsure which documentation you looked at I thought the wiki was OK.  When looking for info I generally search for Ubuntu and whatever as the Ubuntu wiki pages are OK.

To find out about the Open Office debugging you may be better office reposting with that as the specific query and in the title.  Just a thought?

---

### Post by VanillaMozilla on 2011-06-13
Thanks for your suggestion, Ianc, but I don't think I'm going to bother.  I've blown a lot of time on this already, and the likelihood of getting it fixed is looking vanishingly small.  I would have thought that a note in the bug report would suffice to get an answer, but all I got was a nasty reply saying not to ask again.  To me that also says "don't bother with bug reports".

I've always supported open source projects by spending a generous amount of time writing good bug reports, but I just don't think I'm going to bother any more with the large projects.  Some projects, such as Gnumeric, actually fix bugs, and fix them fast.  Those are the ones that will get my time.  I may change my mind if I get a reply, but right now I'm steamed.

Some of the documents do look all right until you actually try to follow them.  I challenge anyone to make their way through the documentation on this case and find a starting point that does not lead to massive amounts of irrelevant, poorly organized, and incorrect information at every step.  No, I'm not going to document all that.

I really thank you for your help.  This rant is not directed at you.  It's a shame you're the only one around to read it.

---

### Post by VanillaMozilla on 2011-06-13
P.S.  Yes, the Apport Wiki looked OK, although I was influenced by the remark that it was turned off by default because they couldn't fix all the crash bugs anyway, so it was better not to know about them.  Unfortunately, this wiki is one of many that one has to navigate to report certain crashes.

---

### Post by ianc1 on 2011-06-13
I appreciate your frustration.  A helpful response on how to file a bug would surely encourage more bug reports and also more accurate bug reports.

I am in the fortunate position of so far only managing to find bugs that have already been reported.  I get stuck at times on actually working out if I've found a bug or just done something stupid when I changed a config setting.

---

### Post by VanillaMozilla on 2011-06-14
Sometimes I have filed bug reports on code that has been abandoned.  Or the problem has already been solved in another (nonoptimum) way.

I swore yesterday that I was going to go to the brainstorm section and write that they need to hire an executive editor for their documentation.  I'm not so sure I'll even do that, as it will take time to do it right, and the chances of success are small.  Alas.

---

