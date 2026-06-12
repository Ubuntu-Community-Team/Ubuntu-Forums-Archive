---
title: "Folding@Home halts with error on 10.04"
date: 2010-01-09
forum: General Help
---

### Post by jimerickso on 2010-01-09
After last nights update to 10.04 Folding@Home halts with the following error:

relocation error: /lib/libnss_files.so.2: symbol __rawmemchr, version GLIBC_2.2.5 not defined in file libc.so.6 with link time reference

will gladly post any requested data. thank you for your consideration in this matter.

---

### Post by HighCommander540 on 2010-01-09
> **jimerickso said:**
> After last nights update to 10.04 Folding@Home halts with the following error:

relocation error: /lib/libnss_files.so.2: symbol __rawmemchr, version GLIBC_2.2.5 not defined in file libc.so.6 with link time reference

will gladly post any requested data. thank you for your consideration in this matter.

Recommendation: Quit using a beta as your normal computer and submit bug.

---

### Post by jimerickso on 2010-01-09
> **HighCommander540 said:**
> Recommendation: Quit using a beta as your normal computer and submit bug.

i have 9.10 on another drive. this is experimental. i have submitted a bug.

---

### Post by HighCommander540 on 2010-01-09
> **jimerickso said:**
> i have 9.10 on another drive. this is experimental. i have submitted a bug.

Then why did you post? This forum isn't a lets spam and tell people about my bug submission.

---

### Post by jimerickso on 2010-01-09
> **HighCommander540 said:**
> Then why did you post? This forum isn't a lets spam and tell people about my bug submission.

i wasn't spamming. i just thought someone here might have experienced this also and have an answer. thats all.

---

### Post by dcstar on 2010-01-10
> **jimerickso said:**
> i wasn't spamming. i just thought someone here might have experienced this also and have an answer. thats all.

As **specifically** stated at the download of Alpha development software, you are to report **all** issues in the development forum and not clog up the forums that deal with release versions.

---

### Post by r_avital on 2010-04-30
Oookayyy....  So this is happening on my end, with the OFFICIAL release of Lucid 64-bit, not beta, exactly the same error, verbatim.  What now?  Is it still spam?

Thanks so much for the useful responses.

---

### Post by r_avital on 2010-04-30
> **jimerickso said:**
> 
relocation error: /lib/libnss_files.so.2: symbol __rawmemchr, version GLIBC_2.2.5 not defined in file libc.so.6 with link time reference

I had the same error, with the 6.29 client.  Probably not what you were looking for, but I installed the "combined" client 6.02, which supports the -smp option on 64-bit OS, working ok now on my 64-bit Lucid (attempting to download and not connecting, but that's likely a temporary problem on the stanford.edu side).

HTH

---

### Post by Devil999 on 2010-05-01
> **r_avital said:**
> I had the same error, with the 6.29 client.  Probably not what you were looking for, but I installed the "combined" client 6.02, which supports the -smp option on 64-bit OS, working ok now on my 64-bit Lucid (attempting to download and not connecting, but that's likely a temporary problem on the stanford.edu side).

HTH

I confirm this. I've been looking for a way of making Folding work in my laptop since my update to Lucid Beta. Never wanted to mess around with libs in my /home, like some guys were talking about in Folding@Home forum.
I'm still waiting for a "final" fix for this problem, but now at least I can fold while I do so.

Thanks! :D

---

### Post by r_avital on 2010-05-03
Reported this today on Launchpad.  Got a reply stating that since this is not an ubuntu package, the ubuntu project can't do anything about it.  Duh.

Responded that the same third-party software (FAH client for Linux v2.69) has a history of performing flawlessly with Jaunty and Karmic, but crashes as described in Lucid.

It might help if anyone having had the same problem, confirms this on the Launchpad site.  Here's the link to the bug report:

[https://bugs.launchpad.net/ubuntu/+bug/574726](https://bugs.launchpad.net/ubuntu/+bug/574726)

(You'll need to log in or register if you are not yet registered, it's free)

Many thanks in advance to all
[U]
**Update:**[/U]
The Ubuntu developers feel they would need additional input from the FAH developers.  Since the client in question is v6.29 which is still in Beta, they have a valid point.  I would like to request that any FAH user having experienced the same problem, report it on [the appropriate FAH forum at this link]("http://foldingforum.org/viewforum.php?f=58") (registration is free if you're not yet a member).

Thank you all in advance.

---

### Post by Circa Lucid on 2010-05-05
I did "affects me too" on LP. I also confirm this problem on client 6.02.

---

### Post by onyxrev on 2010-12-10
What worked for me was:

Install nscd if you don't have it installed:
```
sudo apt-get install nscd
```

[LIST]
[*]Open /etc/nscd.conf with a text editor
[*]find following line: 
enable-cache hosts no
[*]change "no" to "yes"
[*]save & exit the editor
[/LIST]

```
sudo service nscd restart
```

From [https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/574726/comments/21](https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/574726/comments/21)

---

### Post by Niksko on 2011-02-20
Worked like a charm for me. Many thanks. Unfortunately, it's really not that often when you find a simple solution that actually works. More often than not there are posts about the same problem you're having and no solution.

---

