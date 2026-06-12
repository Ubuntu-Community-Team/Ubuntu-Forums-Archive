---
title: "How to file a bug report in Launchpad?"
date: 2012-05-24
forum: General Help
---

### Post by scottbomb on 2012-05-24
I know this sounds ridiculously simple, and I've done it before, but now I cannot find ANYTHING on launchpad.net that will allow me to simply report a bug. I cannot find a "Report a Bug" link anywhere.

---

### Post by irv on 2012-05-24
Go to this link for howto file a bug report.
[https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs")

---

### Post by grahammechanical on 2012-05-24
You go to here:

[https://launchpad.net/ubuntu]("https://launchpad.net/ubuntu")

and at the top and just under the word Ubuntu you click on Bugs.

and on the next page at the top and on the right you click on Report a bug. You sign in and you get to this page:

[https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs")

and it seems that there is no where to actually report a bug.

So, go down to heading 4 Collect information about the bug. In other words use Apport.

If that don't work go down to Filing bugs at Launchpad.net and click on the link to Launchpad's own bug report form. You will get to here:

[https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect]("https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect")

and take it from there.

From all this we can see that an attempt is being made to refine the bug reporting process so that only bugs that are actually bugs get reported and that when Apport is used all the necessary information needed to assess and assign the bug to a developer is also reported.

And about time in my opinion.

I used 12.04 during its development cycle and Apport would detect crashes and then open the default web browser at the launchpad page so we could report the bug. But things are different with the 12.10 development release.

Apport detects the crash and asks permission to report it but it does so without opening browser page to launchpad.

This is to prevent some of us from making multiple bug reports every time the same program crashes before the problem has been fixed.

In a way bug reporting of the development release has become a little bit automated.

Look at this page

[https://wiki.ubuntu.com/Apport/DeveloperHowTo]("https://wiki.ubuntu.com/Apport/DeveloperHowTo")

> Apport can suppress reports for bugs which have already been reported. Sometimes a bug affects so many people that we get hundreds of duplicates in a matter of days, which both creates a lot of needless reporting, triaging, and retracing work. In those cases, and when the bug can be uniquely identified with regular expressions on the apport report keys or file attachments, a "bug pattern" should be created which will prevent Apport from reporting the bug in the first place, and instead guide the user to the already existing bug page.

To often on this forum we see people saying that they have a problem and someone says: Report it as a bug. In some cases it is simply that the person did not know how Ubuntu has changed from one version to the next. It was not a bug.



Regards.

---

### Post by Paqman on 2012-05-24
+1 for using the ubuntu-bug tool. It does rely on your knowing the right package name to report, so if you don't know that then you can temporarily [enable apport]("https://wiki.ubuntu.com/Apport#How_to_enable_apport") if it isn't already. Then next time the package acts up apport should snag it and let you raise the bug.

---

### Post by scottbomb on 2012-05-24
Thanks for the replies! I went to [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
I read that page earlier, but never found the link until now. One has to scroll down quite a bit to find it. [My bug is not related to a crash so apport doesn't help].

---

