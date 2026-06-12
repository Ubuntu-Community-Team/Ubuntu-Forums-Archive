---
title: "MS Office &amp; Wine, VMWare ThinApp etc"
date: 2011-12-23
forum: General Help
---

### Post by crashed111 on 2011-12-23
Hi All

I have had some compatibility problems between Powerpoints between LibreOffice and MS Office. Looks like I am going to need to run the MS Product on my Ubuntu installation. 

I dont really fancy using a Windows VM for this as I would like everything to just run out of Ubuntu

This has left me with 3 options -


[LIST]
[*]Try to run Office 2007 in Wine (There seems to be a lot of stability issues)
[*]Try to run Office 2007 in Crossover (There seems to be a lot of stability issues)
[*]Try to run Office 2007 in VMWare ThinApp or Novell ZenWorks Application Virtualization and then run the virtual exe under Wine (Apparently people have been able to do this but I have had no luck when I try to run the virtual apps under Wine nothing happens)
[/LIST]


I am not sure if anyone else has had any luck with any of these methods that they could report back on as I am interested in getting Office going (The ThinApp / ZAV method looks interesting but does not seem to like Wine) 


Thanks in advance

---

### Post by ugm6hr on 2011-12-23
Which version of Office do you have?
I would recommend "PlayOnLinux" - it makes using wine easy. I've got Office 2007 - which I use purely for Powerpoint (similar reasons as you) - which works fine, apart from the odd visual glitch when moving objects, and parts of the menu being white on black rather than black on white.
I gather 2003 works even better.
PS: I haven't tried embedding video.

---

### Post by crashed111 on 2011-12-23
Hi 

I am trying to run 2007 Ultimate (Fully legit). I have just tried PlayOnLinux however the Office install file has been distributed to me as an .exe from the IT dept rather than as a CD. PlayOnLinux is refusing to do this as I do not have the CD.

Do you have any idea as to how I can fix this?

Thanks

---

### Post by drmrgd on 2011-12-23
Here's a thread that might help you.  Due to plain laziness, I have not yet had a chance to try it out.  Looks very promising, though!

[http://ubuntuforums.org/showthread.php?p=11482458#post11482458]("http://ubuntuforums.org/showthread.php?p=11482458#post11482458")

---

### Post by Mark Phelps on 2011-12-23
You might read through some of the test results in the link below to see if any of them address the problems you're having:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=13]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=13")

---

### Post by crashed111 on 2011-12-23
Thanks guys for your help.

I now have Office working (Except PowerPoint :( ).

I want to try the install again as I installed it using "Vista" as the Windows version which apparently can cause problems. 

If I delete my .wine directory is it the equivalent of doing a format / re-install in a Windows machine so I know if I try again I know I am starting from scratch?

And also how does everyone place the updates on their systems is it a case of downloading them manually and running the .exe?

Thanks

---

### Post by BC59 on 2011-12-23
> **crashed111 said:**
> 
If I delete my .wine directory is it the equivalent of doing a format / re-install in a Windows machine so I know if I try again I know I am starting from scratch?

And also how does everyone place the updates on their systems is it a case of downloading them manually and running the .exe?

Thanks

1st question: yes
2nd question: very difficult, usually it's not working. Better to install programs with all the updates already installed.

Look here as well I started a thread about installing MSOffice 2010 with Wine.
[http://ubuntuforums.org/showthread.php?t=1885051](http://ubuntuforums.org/showthread.php?t=1885051)

---

### Post by sgage on 2011-12-23
> **crashed111 said:**
> Thanks guys for your help.

I now have Office working (Except PowerPoint :( ).

I want to try the install again as I installed it using "Vista" as the Windows version which apparently can cause problems. 

If I delete my .wine directory is it the equivalent of doing a format / re-install in a Windows machine so I know if I try again I know I am starting from scratch?

And also how does everyone place the updates on their systems is it a case of downloading them manually and running the .exe?

Thanks

I've been running Office 2007 under Wine with success. As far as updates, you can download the latest service pack (3, I believe), and just run the exe - worked fine for me.

PowerPoint works fine - there's a gimmick to making it load, though. You have to use Configure Wine to set riched20.dll to 'native' vs. 'builtin'. After that, no problemo.

The only issues I've experienced are some rendering/refresh issues, but just scrolling or min/maxing the window clears it up.

My use of Office under Wine is very occasional and for trivial files, so YMMV.

---

### Post by crashed111 on 2011-12-26
Well I have tried this and I have finally got it to install fine. I just had to put in the dll fix mentioned above for Powerpoint and now everything works perfectly!

Thanks everyone for their help and I am impressed ... Wine has come a long way!

---

