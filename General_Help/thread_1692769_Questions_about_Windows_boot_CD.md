---
title: "Questions about Windows boot CD"
date: 2011-02-21
forum: General Help
---

### Post by JohnnyDohable on 2011-02-21
Hey everyone, I have a DELL that allows one to boot into Ubuntu or Windows.  Lately, my Windows has not been working.  It has the blue screen of death.  Anyways, my OpenOffice program won't run when I use Ubuntu, and I really need to use a word processor for school.  So my idea was to reinstall Windows on my computer.

Whenever I put in my Windows XP CD, I made my computer boot from the CD.  The problem is that after it told me that it was starting Windows, it failed and gives me an error message.

Anyways, I was wondering if there is any way to replace my WINDOWS files that are already on my computer with the boot files on the CD?  I don't know if that is even possible actually, I'm looking for help here.  If someone could also help me get my OpenOffice working on Ubuntu that would also help.  Thank you.

---

### Post by Hedgehog1 on 2011-02-21
> **JohnnyDohable said:**
> Hey everyone, I have a DELL that allows one to boot into Ubuntu or Windows.  Lately, my Windows has not been working.  It has the blue screen of death.  Anyways, my OpenOffice program won't run when I use Ubuntu, and I really need to use a word processor for school.  So my idea was to reinstall Windows on my computer.


Johnny,

Don't you hate it when the 'puter is acting up?

Here is the thing - because you are having issues in both Windows (BSOD - Blue Screen Of Death) and Open Office in Ubuntu, my first reaction is a hardware issue (Specifically - Memory issue).  

So if you would do three things for me:

1) From the Grub boot menu - please run a memory test.  This way if I am completely wrong about that, it is out of the way.

2) If your system passes the memory test, please describe he issue you are seeing in Open Office, so we can see if that can be fixed.

3) If all else fails **please** don't tell your instructor that **"Ubuntu ate my homework"**.  They **Never** believe it!

Post what your memory test shows and we will go from there!

:KS

---

### Post by JohnnyDohable on 2011-02-22
> **Hedgehog1 said:**
> 
1) From the Grub boot menu - please run a memory test.  This way if I am completely wrong about that, it is out of the way.

2) If your system passes the memory test, please describe he issue you are seeing in Open Office, so we can see if that can be fixed.

3) If all else fails **please** don't tell your instructor that **"Ubuntu ate my homework"**.  They **Never** believe it!

Post what your memory test shows and we will go from there!

:KS

Well first, I thank you for the quick reply.  Second, the memory test I allowed to run twice and both times did not report any errors.  My initial boot menu has two Memorytest options, I don't know if that is normal, but I chose the first one that reads, "Memory test (memtest86+)" (or something similar to this).

OpenOffice:  When I attempt to start it, the loading screen of OpenOffice Word appears, but nothing loads and nothing happens.  Eventually, the loading screen goes away and nothing happens.  So basically, nothing happens... heh.

---

### Post by Hedgehog1 on 2011-02-22
Well, the memory seems OK and that is good.
 
I think a reinstall of OpenOffice makes sense as the next step.
 
However, if you are running Ubuntu 10.04 of 10.10 - this is a perfect time to move on the the new LibreOffice that is carried in 11.04.
 
This link explains how to load it (and the load will uninstall the current OpenOffice)
 
[https://wiki.ubuntu.com/LibreOffice](https://wiki.ubuntu.com/LibreOffice)
 
The folks who created OpenOffice broke off and have done LibreOffice - your exsisting documents should work just fine.
 
If you are unsure about upgrading to LibreOffice, then a complete uninstall and then reinstall of OpenOffice using the Software Center is fine, too.
 
:KS

---

### Post by howefield on 2011-02-22
> **JohnnyDohable said:**
> OpenOffice:  When I attempt to start it, the loading screen of OpenOffice Word appears, but nothing loads and nothing happens.  Eventually, the loading screen goes away and nothing happens.  So basically, nothing happens... heh.

Try opening from the terminal, you might get a clue as to what's up in the terminal output if it fails.

```
ooffice -writer
```

---

### Post by Hedgehog1 on 2011-02-23
> **howefield said:**
> Try opening from the terminal, you might get a clue as to what's up in the terminal output if it fails.
 
```
ooffice -writer
```
 
_OH sure_ - if you want to do it the ***right way***; you can do what howefield said and learn why OpenOffice is failing.
 
Wait - that is actually a really good idea (doing it the right way) :D
 
I will add this to my books of 'tricks-I-should-have-thought-of-already'.
 
Thanks howefield!
 
:KS

---

### Post by JohnnyDohable on 2011-02-24
> **howefield said:**
> 

```
ooffice -writer
```

Ok, excellent idea.  

I typed the code into terminal.  I hit enter and waited a long time--perhaps 1 or 2 minutes.  Then I am given a "Bus error" on the Terminal screen.  I wait another maybe 2 minutes and, finally, the OpenOffice loading screen comes on.  This event is accompanied by the following lines in Terminal:
"javaldx: Could not find a Java Runtime Environment! 
Please ensure that a JVM and the package openoffice.org-java-common
is installed.
If it is already installed then try removing ~/.openoffice.org/3/user/config/javasettings_Linux_*.xml
JohnnyDohable@JohnnyDohable-laptop:~$ "

The open office loading screen behaves exactly as it does when opening open office through the normal method...  It shows up and nothing happens.

---

### Post by Hedgehog1 on 2011-02-24
> **JohnnyDohable said:**
> 
"javaldx: Could not find a Java Runtime Environment! 
Please ensure that a JVM and the package openoffice.org-java-commonis installed.
**If it is already installed then try removing ~/.openoffice.org/3/user/config/javasettings_Linux_*.xml**


Well, It looks like trying the highlight suggestion from the error message is a good first step.

If that doesn't solve it (our you are uncomfortable doing the above step), then loading LibreOffice: [https://wiki.ubuntu.com/LibreOffice]("https://wiki.ubuntu.com/LibreOffice") which will reload that package is a good choice.

It's up to you now - Keep us updated, please!

:KS

---

### Post by JohnnyDohable on 2011-02-24
I tried removing that file.  I don't know if I did it correctly.  I typed this:

"rm ~/.openoffice.org/3/user/config/javasettings_Linux_*.xml"

This line is what I got back:

"JohnnyDohable@JohnnyDohable-laptop:~$ ", or the normal input line or whatever.

I tried to start up open office, but the same thing is happening...

---

### Post by Hedgehog1 on 2011-02-24
> **JohnnyDohable said:**
> I tried removing that file.  I don't know if I did it correctly.  I typed this:

"rm ~/.openoffice.org/3/user/config/javasettings_Linux_*.xml"

This line is what I got back:

"JohnnyDohable@JohnnyDohable-laptop:~$ ", or the normal input line or whatever.

I tried to start up open office, but the same thing is happening...

This means the java run time is, indeed, missing.

So you can un-install and re-install open office, or upgrade to LibreOffice using this link as a guide: [https://wiki.ubuntu.com/LibreOffice]("https://wiki.ubuntu.com/LibreOffice")

Either way, it will reload the java run time.

Were you able to get you school work done?

:KS

---

### Post by JohnnyDohable on 2011-02-25
"
JohnnyDohable@JohnnyDohable-laptop:~$ sudo apt-get install libreoffice-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libreoffice-gnome: Depends: libreoffice-core (= 1:3.3.0-1lucid1) but it is not going to be installed
                     Depends: libreoffice-gtk but it is not going to be installed
E: Broken packages
JohnnyDohable@JohnnyDohable-laptop:~$ 
"

Yeah, the thing's shot...  I don't know why, though, exactly, since I can still use Chromium and connect to the internet fine.

And yeah, sort of...  Never forget to actually add an attachment to an email though when you email something.  Oh man

---

### Post by Hedgehog1 on 2011-02-26
I think they were rebuilding the LibreOffice packages right about then.

Perhaps it is best to uninstall and reinstall OpenOffice for now using the Ubuntu Software Center.

:KS

*p.s. I have noticed that once I get stressed, then I start making silly mistakes (like not attaching the document to the email).  I happens to us all...*

---

### Post by JohnnyDohable on 2011-02-28
I can't, because my SoftwareCenter is one of the programs not working right now.

---

### Post by Hedgehog1 on 2011-02-28
Johnny,

The fact that both sides of you PC are not working (Windows and Ubuntu) is rather disturbing. :frown:

Did you want to try to rebuild the PC's OS?

Or, perhaps, it is time to look for a newer PC. :D

I will leave that up to you.

If you opt to rebuild the OS, please start a new thread for that; that way folks can help.

---

### Post by JohnnyDohable on 2011-03-02
> **Hedgehog1 said:**
> Johnny,

The fact that both sides of you PC are not working (Windows and Ubuntu) is rather disturbing. :frown:

Did you want to try to rebuild the PC's OS?

Or, perhaps, it is time to look for a newer PC. :D

I will leave that up to you.

If you opt to rebuild the OS, please start a new thread for that; that way folks can help.

I was fearing that that indeed was the step to take.  Now... the OS to start with is Windows, do you think?  Or should I just start with Ubuntu?

---

