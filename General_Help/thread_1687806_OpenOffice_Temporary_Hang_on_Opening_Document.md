---
title: "OpenOffice: Temporary Hang on Opening Document?"
date: 2011-02-14
forum: General Help
---

### Post by linux4me on 2011-02-14
I'm using Ubuntu 10.10 64-bit with all the current updates. It was a clean install, but I did import my previous home folder. The only things I can think of that depart from a standard installation are that I'm running an encrypted drive with LVM and I've installed some extra fonts.

Whenever I open an OpenOffice document (write or calc) for the first time in a session, I get a 5-7 second hang that locks up only OpenOffice. It can be an existing document or a fresh document. The hang doesn't occur until I can actually see the document. In Write, I can actually type the first few letters of a sentence before the program hangs. Once the 5-7 seconds elapses, everything in OpenOffice seems to work just fine, and the remainder of the sentence I typed appears. This happens whether I start OpenOffice from the command line, by double-clicking a file, or from a launcher. There are no error messages in Terminal. Once OpenOffice has been opened in a given session, even if I close it, any documents subsequently opened open fine without the hang.

According to [this thread]("http://ubuntuforums.org/showthread.php?t=1512422"), the problem seems to have existed in Lucid, too, though I don't recall experiencing it then. I tried adding the recommended line to my /etc/hosts file as described [here]("http://ubuntuforums.org/showpost.php?p=9677665&postcount=51"), but it didn't help. One of the posters filed an issue with [OpenOffice.org]("http://www.openoffice.org/issues/show_bug.cgi?id=112546") that includes some technical explanation for the issue that's way over my head. The other solution offered in the above thread, using OpenOffice open/save menus, doesn't seem to apply in my situation, but I tried it anyway and it made no difference.

It looks like the issue isn't limited to Ubuntu, as I found [this post]("http://forums.opensuse.org/english/get-technical-help-here/applications/446041-openoffice-3-2-1-hangs-opening-document.html") on the openSuse forums that describes the same problem I'm having. Unfortunately, no solution for me there, either.

I have tried renaming the .openoffice.org and .openoffice.org2 folders, rebooting, and retesting, but that didn't work.

As annoying as it is, I could easily live with it since once I've opened OpenOffice it's not a problem, except for one thing: I'm running a bash script using unoconv to automate processing some documents, and it will fail due to the hang if I don't open OpenOffice first, even though the script itself opens a headless session of OpenOffice. It seems like the 5-7 second lag trips it up. I guess I could come up with a workaround in the script, but I'd like to try to fix OpenOffice, first.

Does anybody have any ideas?

---

### Post by upptown on 2011-02-14
Have you tried disabling Java?

Tools> Options> Java: Uncheck "Use Java Runtime environment.

---

### Post by linux4me on 2011-02-14
> **upptown said:**
> Have you tried disabling Java?

Tools> Options> Java: Uncheck "Use Java Runtime environment.

No, I hadn't tried that, but I just tried disabling it, restarted, and tested Write, and it still hung. Thanks for the suggestion, though.

---

### Post by Hagar Delest on 2011-02-16
Try first to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

If no change, try the vanilla version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

Do you have or have had a networked printer?

---

### Post by linux4me on 2011-02-16
> **Hagar de l'Est said:**
> Try first to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

If no change, try the vanilla version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

Do you have or have had a networked printer?

Thanks for the reply. 

I already tried resetting my profile as described in the original post. I'd like to try fixing the Ubuntu version of OO rather than installing the generic version if I can. That is a good suggestion as a last resort, though. It seems like there must be something particular to my install since not everyone is having this problem. I have tested it on two machines, both of which use the same /home folder but with vastly different hardware, and have the same issue on both.

No, no network printer. Just one connected directly via USB. I have tested with the printer both off and on (after restart) and it made no difference.

---

### Post by flanz on 2012-06-14
I'm having this exact issue in Kubuntu 12.04. Please let me know if you find a work around.

---

### Post by Hagar Delest on 2012-06-14
Try to upgrade to AOO 3.4. And reset your profile as said above, it may help.

Else, what file format? Native ODF or external format?

---

### Post by linux4me on 2012-06-14
The problem went away for me when I upgraded to 11.04 and hasn't recurred with 11.10 and 12.04 (Ubuntu, not Kubuntu). I never found a fix when I had 10.10.

---

