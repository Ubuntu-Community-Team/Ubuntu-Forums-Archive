---
title: "What next? -  suspend/hibernation issue"
date: 2009-11-20
forum: General Help
---

### Post by wavery on 2009-11-20
New to Ubuntu and Linux and still learning the ways of the community, so I'm not sure where to turn next on this issue, if anywhere.  Like many others it seems, I'm having suspend/hibernation issues with both a desk top and laptop that I've installed 9.10 on.  After looking for answers, I'm not sure what I'm finding means.  For example, when I search on this topic, I'm usually referred to this thread which is closed: [http://ubuntuforums.org/showthread.php?t=1307618](http://ubuntuforums.org/showthread.php?t=1307618).  Does the fact it is closed mean the issue has been reported to death and it is being worked on?  Or is the solution in there somewhere I should be going through them to see if any of them work, which seems to be hit or miss for the most part (and not an easy proposition given my neophyte status)?

Other posts suggest this is an ongoing problem and don't expect a fix anytime soon. I've read elsewhere that I should report a bug, but I have a hard time believing a new bug report would be constructive given the widespread nature of the problem.  Likewise, it doesn't seem like another posting will be constructive since similar postings are often referred back to the one above.  So...where do I go from here?  Thank you.

---

### Post by wavery on 2009-11-20
Well I spoke a little too soon.  A second thread was opened on the same subject:

[http://ubuntuforums.org/showthread.php?t=1331522](http://ubuntuforums.org/showthread.php?t=1331522)

I'm still curious why the first one was closed.

---

### Post by bodhi.zazen on 2009-11-20
The first thread is in the 64 bit section. If you read the big blue announcement at the top of the 64 bit section you will see it is closed.

I know it can be confusing, but we make announcements for a reason, and as with the stickies, please take the time to read them =)

**Announcement**: [Closure of the x86_64 Forums]("http://ubuntuforums.org/announcement.php?f=343")

In terms of hibernation, the most common problem is that your swap partition is too small. You need a swap partition the is as large as your RAM. So if you have 4 Gb RAM you need a 4 Gb Swap partition.

---

### Post by P4man on 2009-11-20
Im not entirely sure what the point of those threads is as people with vastly different machines and therefore probably root causes are all just posting confirmation they have a problem or posting solutions which may only work for very specific machines.

This is not a single known bug, this is a very complicated issue with countless causes and possible solutions, but problems with suspend and hibernate are usually related to ACPI. IT could be a BIOS issue (you wouldnt believe how many buggy ACPI BIOSes are out there) that may or may not be worked around. It can also be related to videodrivers, sometimes network drivers or kernel incompatibilities. 

Anyway lets fire some questions:

Which machines are we talking about?
Elaborate on the "suspend/hibernation issues". Does it suspend? Does it resume? Does it hibernate? What happens when things go wrong

Posting a bug report is a good idea, but you should first make sure the bug isnt reported already, hence the need to get machine specific information and a more precise description of the problem.

---

### Post by wavery on 2009-11-20
> **bodhi.zazen said:**
> The first thread is in the 64 bit section. If you read the big blue announcement at the top of the 64 bit section you will see it is closed.

I know it can be confusing, but we make announcements for a reason, and as with the stickies, please take the time to read them =)

**Announcement**: [Closure of the x86_64 Forums]("http://ubuntuforums.org/announcement.php?f=343")


Thank you...I thought it had probably been noted somewhere.  Unfortunately if you do a subject search that takes you to the the thread, there is no mention of the announcement that I saw.  But that's why I asked; I didn't know to look at the top of the forum itself.

> **bodhi.zazen said:**
> In terms of hibernation, the most common problem is that your swap partition is too small. You need a swap partition the is as large as your RAM. So if you have 4 Gb RAM you need a 4 Gb Swap partition.

Plenty of swap space. That's not the problem, but thank you.

---

### Post by wavery on 2009-11-20
> **P4man said:**
> Im not entirely sure what the point of those threads is as people with vastly different machines and therefore probably root causes are all just posting confirmation they have a problem or posting solutions which may only work for very specific machines.

This is not a single known bug, this is a very complicated issue with countless causes and possible solutions....

Posting a bug report is a good idea, but you should first make sure the bug isnt reported already, hence the need to get machine specific information and a more precise description of the problem.

This again is why I asked the question.  Yes there were many different machines represented on that thread, and lots of different symptoms mentioned, but no concrete answers...just things to try.  I didn't see why the thread had been closed, which was my primary question...was there a general fix out there that I was missing? Or had the thread grown to the point of no longer being constructive, etc.  I didn't want to post another thread on the subject if it was going to be redundant, and as I mentioned above, it seemed like every search on the subject ultimately lead to the closed thread.

I'm going to try the solution mentioned in the second thread.  If no luck with that, I'll submit a bug report if I don't see that one's been submitted.  Thank you.

---

