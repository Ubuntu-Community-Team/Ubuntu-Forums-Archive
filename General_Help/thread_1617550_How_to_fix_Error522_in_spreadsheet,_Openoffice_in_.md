---
title: "How to fix Error:522 in spreadsheet, Openoffice in Ubuntu 10.04"
date: 2010-11-09
forum: General Help
---

### Post by aimwin on 2010-11-09
Ubuntu 10.04 installed on Hard Disk since April 2010, and Open Office 3.2.0
Fully updated and checked on 10 NOV 2010.
----------Edit on 12 Nov 2010 -------Problems solved.
Conclusion
[COLOR="Red"]So if you found any odds errors,

 and you are sure that you have done the correct formula,

 in OpenOffice and Ubuntu 10.04 ???  

To solve the problems, re installation OpenOffice alone
with synaptic "Mark for Complete Removal",
 may not solve the problems.

Synaptic will not remove all configuration files that would effect the errors,
of OpenOffice programs,

You need to manually remove the configuration files your self.[/COLOR]

[COLOR="Blue"]I am just a user, not advance user nor expert on Ubuntu, nor Open Office.
So I just told my experience,
     so if you choose to solve this problem with my method.
I cannot guaranty that it will not effect your Ubuntu installation as a whole.[/COLOR]
[COLOR="Red"]--> Any Gurus please comment if my methods will effect Ubuntu as stable installed or not ??[/COLOR]
-------------------------------------
I start my notebook with live CD of original April 2010 released of Ubuntu 10.04.
And use Openoffice 3.2.0 that come with live CD,
And I found that the Err:522 did not appear as my hard disk installed version.

So it means no bugs in Ubuntu 10.04 nor Openoffice 3.2.0 nor 3.2.1.
But it must be my user configurations some where?

With old notes below,
I trusted synaptic, "Marked for Complete Removal",
and I accidentally found that .openoffice.org folder exist.
While I was backing up home folder for reinstallation of my ubuntu 10.04.1.

So I remove it manually and re-install OpenOffice.
And it fixed the Err:522.
-------------------------------------

So I did,

1. using synaptic to un-install "all" openoffice files "complete removal".
2. Open Nautilus File manager=> Place>Home Folder> [new window File browser]
3. go to folder name => .openoffice.org
4. rename folder name => 3 to something else, (I use 3err522) - or delete that "3" folder.
5. Reinstall office from Ubuntu Software Center.

No more error on "The File".

--------------------
I left the old notes below to tell
 the pain I have for 5 days to get to the simple solution,
 since I was thinking, it was a bug on 10.04 and Ooo3.2.0.
[COLOR="Blue"]
"And" fully trust "synaptic 's Marked for Complete Removal 
(include configuration files)[/COLOR] 
[COLOR="Red"]I will not trust synaptic "blindly" any longer.[/COLOR]

If I have use the Live CD of the April 10.04, 
I would have solve the problems long ago.

-----------edit on 11 NOV 2010---------
update to OpenOffice 3.2.1 (build 9050) 
by setting Synaptic>Setting>Repositories=>[new windows]
Software Sources>Updates>[tick the box]Pre-released updates (lucid-proposed)>Close
Click on Reload icon.
then search for OpenOffice, you will see tick box with marked for update of the old version OpenOffice. ==>apply.

====>I tried mark for complete removal including configuration files
 and re install Oop3.2.1_9505


The new update version still open the file with Err:522 too.
---------------------------------------

It produce one bug Err.522, in spreadsheet when one cell of a calculating group of cells which need to extract value from another file.

I have Error 522 in OpenOffice 3.2.0 please see attached screen shot.

Error 522 - according to help, is
Circular reference
Formula refers directly or indirectly to itself and the Iterations option is not set under Tools - Options - OpenOffice.org Calc - Calculate.

I wasted 2 days of restless searches for reasons why it still produce Err:522. despite it is not Circular reference.

Finally I found that nothing wrong with my formula.

[COLOR="Red"]I use EXCEL, Ubuntu 10.04.1 and 10.10 - OpenOffice 3.2.1,
open the same sheet,in the same diretory,
more than 20 times altogether.

And I find there is no Err:522 at all.[/COLOR]

The error which always come up,
when I open the same file,
and order it to update the data from another file.

So if you have the similar problems,
TRY using other Ubuntu distributions.
and see if it will produce the same bugs or not.

It is look like I have to format and install 10.04.1,
(10.10 has many bugs - by 10 Nov 2010) 
in order to be free from bugs in spreadsheet or bug in the kernel?> [QUOTE][QUOTE][/QUOTE][/QUOTE]

---

### Post by Hagar Delest on 2010-11-09
Try the vanilla version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

If no change, can you upload the file itself?

---

### Post by aimwin on 2010-11-11
> **Hagar de l'Est said:**
> Try the vanilla version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

If no change, can you upload the file itself?

Thanks for reply, I did reinstall using synaptic.
And finally found the solution and update my post.

If you can, please comment on my method, 
if it will destabilized Ubuntu installation?

Thanks.

---

### Post by Hagar Delest on 2010-11-11
If you've reinstalled with Synaptic, then there is no problem.

---

### Post by aimwin on 2010-11-12
> **Hagar de l'Est said:**
> If you've reinstalled with Synaptic, then there is no problem.

I mean the way I rename the folder "3" configuration file in the home-user directory,
which was not remove by synaptic "Mark for Complete Removal".

Dose it mean we should not touch that folder "3",
because if it meant to be removable,
synaptic would have done for us.

So if those Gurus who wrote those program decide to left folder "3" alone,
it means we should not touch it.

Or may be it was a bug in the routine of Openoffice to uninstall in Ubuntu that synaptic just followed it.

Thanks

---

### Post by Hagar Delest on 2010-11-12
Renaming the profile leads OOo to recreate one. If it fix the problem (often the case), then you can delete the old one. If you had customized OOo, then you can recover the configuration files from the old profile and then delete it.

---

### Post by aimwin on 2010-11-12
> **Hagar de l'Est said:**
> Renaming the profile leads OOo to recreate one. If it fix the problem (often the case), then you can delete the old one. If you had customized OOo, then you can recover the configuration files from the old profile and then delete it.

So the answer should be safe work then.
Thank you.

---

