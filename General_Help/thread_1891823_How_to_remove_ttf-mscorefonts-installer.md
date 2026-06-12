---
title: "How to remove ttf-mscorefonts-installer ?"
date: 2011-12-06
forum: General Help
---

### Post by dcpking on 2011-12-06
I have just started using a System76 Bonobo and want to virtualise an older Windows machine (I work with SQL Server). So I used Parallels to make a usable image of the machine and tried to install Parallels Workstation on the Linux machine (Ubuntu 11.10). It ran for about 12 hours and then we suffered a power cut, so I had to kill the process and close down (I think 12 hours is a little long!).

Anyhow, I've subsequently tried installing VirtualBox and received this error immediately:

[FONT="Courier New"]There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.


Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.[/FONT]

I tried to remove and then re-install the core fonts package, but get this during removal:

[FONT="Courier New"]installArchives() failed: dpkg: error processing ttf-mscorefonts-installer (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 ttf-mscorefonts-installer[/FONT]

It seems that I need to repair the Source Fonts before VirtualBox will install, but I can't re-install it (the installer offers removal only). 

Have I reached a black hole that only re-installing the whole OS will fix :(  :confused:

Mike

---

### Post by phidia on 2011-12-06
Well you can remove vb and then install it again you don't need to reinstall ubuntu to do that. You could also try > sudo apt-get update --fix- missing but I'm not sure that will help just allow the package manager to remove virtual box and then install it again.

---

### Post by blackbird34 on 2011-12-06
What about reinstalling through Synaptic?

---

### Post by 73ckn797 on 2011-12-06
Did you try:
```
sudo apt-get clean
``` in terminal. That will clean out all downloaded packages. They are stored on your computer. Possible that one of the packages is corrupted. Try installing again and see what happens.

---

### Post by dcpking on 2011-12-06
Thanks for the suggestions - 

phidia: it was trying to install VBox that surfaced the problem - VBox just gave up trying to install (so far as I know)!
        I have tried "sudo apt-get fix-missing". Did you mistype something? I get "E: Invalid operation fix-missing" in return and don't see anything obvious in the help ...

73ckn797: yes, I did try "sudo apt-get clean". I tried it after VBox failed, and it still failed :(  

My problem seems to be that the install of the ttf-mscorefonts-installer seems to be munged up somehow. If I could get rid of it I could try replacing it and then maybe VBox would like what it finds again ...?



I have to confess: I'm a noobie to using Linux as my main system. I've had a Ubuntu 9.04 system on an eeeBox for a couple of years and enjoyed what I could do with it, so wanted more power! Maybe I wished for too much! 

Thanks to you both for the suggestions: do you have any more ... please!

---

### Post by dcpking on 2011-12-06
OH, and thanks too to you, blackbird34. However, Synaptic is what U11.10 uses as the System Software Center (at least, it comes up looking the same!), and it also only offers "Removal", which still doesn't work! The message is:

[FONT="Courier New"]installArchives() failed: dpkg: error processing ttf-mscorefonts-installer (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 ttf-mscorefonts-installer
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
[/FONT]

Which may be great advice, but how do I _install_ it when all Synaptic will offer is Removal? What does dpkg do?

I hate software (been writing it since school, so I should know better by now!)  :confused:

---

### Post by mc4man on 2011-12-06
It shouldn't hurt to try 
```
sudo dpkg --configure -a && sudo apt-get update
```

---

### Post by phidia on 2011-12-06
My bad the command is > sudo apt-get update --fix- missing
Not sure it would help in this situation but corrections are good :)

Fixed in my initial response this thread too.

---

### Post by dcpking on 2011-12-06
Thanks, mc4man. it didn't do any harm to run "sudo dpkg --configure -a && sudo apt-get update", but unfortunately removing the corefonts installer still fails - same error message as before.

I tried looking at the installed packages and found this:

rHR ttf-mscorefonts-installer    3.3ubuntu4     (no description available)

and the HR mean "Half-installed. Re-install required".

So how do I get rid of this pesky package? Anyone got any suggestions? Or ideas of where I should ask, even?  

--  tia  --  Mike              :confused:

---

### Post by dcpking on 2011-12-06
So I decided to believe the message ... and did 
           apt-get install ttf-mscorefonts-installer
and I get a MS EULA page up on my Terminal (what a horrible sight!)

It seems to want me to do something - it has "    <Ok>    " at the bottom as I scroll through it - but how do I accept the thing? I suspect that this might be why I had to kill off the Parallels installation in the first place - it was just sitting waiting for the "ok" from the EULA. 

But how, for heavens' sake ?!!!

---

### Post by phidia on 2011-12-06
Apt commands and explanations [here]("https://help.ubuntu.com/community/AptGet/Howto").

You could try > apt-get purge <your offending package>

---

### Post by phidia on 2011-12-06
> **dcpking said:**
> So I decided to believe the message ... and did 
           apt-get install ttf-mscorefonts-installer
and I get a MS EULA page up on my Terminal (what a horrible sight!)

It seems to want me to do something - it has "    <Ok>    " at the bottom as I scroll through it - but how do I accept the thing? I suspect that this might be why I had to kill off the Parallels installation in the first place - it was just sitting waiting for the "ok" from the EULA. 

But how, for heavens' sake ?!!!

Is there a url somewhere in that that you can click on or copy paste into a browser-there should be a link.

---

### Post by mc4man on 2011-12-06
> **dcpking said:**
> So I decided to believe the message ... and did 
           apt-get install ttf-mscorefonts-installer
and I get a MS EULA page up on my Terminal (what a horrible sight!)

It seems to want me to do something - it has "    <Ok>    " at the bottom as I scroll through it - but how do I accept the thing? I suspect that this might be why I had to kill off the Parallels installation in the first place - it was just sitting waiting for the "ok" from the EULA. 

But how, for heavens' sake ?!!!

Try using the tab or right arrow key till it highlights, then press enter..

---

### Post by dcpking on 2011-12-06
Phidia, mac4man:  you guys are so brilliant!! It's been 1991 or before since I used a character-based GUI, and I'd totally forgotten how!

So I used the <tab> keys, answered the questions, got the EULA finished, and VBox installs! Now to install a copy of Windows and get my email back up and running (RitLabs don't make a Linux copy of TheBat! yet :)  )


So thanks to both of you, and all the others who offered help! If I could send you gold stars then I would, for sticking with me and pointing me in the right directions. 

Mike

---

