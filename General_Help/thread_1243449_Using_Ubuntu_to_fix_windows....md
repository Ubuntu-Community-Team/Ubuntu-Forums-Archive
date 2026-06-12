---
title: "Using Ubuntu to fix windows..."
date: 2009-08-18
forum: General Help
---

### Post by joemofo619 on 2009-08-18
Ok, so recently I did something to get this particularly nasty malware Windows Antivirus Pro on my windows machine. It has blocked me from every program, every thing I try to do, cmd, task manager, cannot do anything. So, of course, I'm safe on my Ubuntu side of the machine, but its going to bother me, knowing that I couldn't fix this one. How can I fix this nasty problem using ubuntu? Ubuntu is on here, courtesy of wubi. Whenever I try to delete to program, I get this [http://img24.imageshack.us/img24/6748/screenshotpou.png](http://img24.imageshack.us/img24/6748/screenshotpou.png)

And whenever I try to run a spyware program from wine, it simply just won't start... So, what are my options to get rid of this? Keep in mind, reformatting is the very last, dire, drastic step I want to take. Please help, I've battled this thing for 3 days now.

---

### Post by howefield on 2009-08-18
> **joemofo619 said:**
> And whenever I try to run a spyware program from wine, it simply just won't start... So, what are my options to get rid of this? Keep in mind, reformatting is the very last, dire, drastic step I want to take. Please help, I've battled this thing for 3 days now.

Have you tried booting windows in safe mode, then installing and running malwarebytes ?

If I were you, I'd boot with an Ubuntu Live CD, and backup everything from windows that I needed, then do the reformat, 4 hours of pain sure beats 3 days and counting...

---

### Post by joemofo619 on 2009-08-18
> **howefield said:**
> Have you tried booting windows in safe mode, then installing and running malwarebytes ?

If I were you, I'd boot with an Ubuntu Live CD, and backup everything from windows that I needed, then do the reformat, 4 hours of pain sure beats 3 days and counting...

I did try safe mood, and malwarebytes, and the installer wont even run anymore in safe mode... its not really that I won't reformat.... its that I can't, haha. I've lost all my Windows XP cds, and, yea, don't have a burner

---

### Post by jerrrys on 2009-08-18
been using it for years, it kicks virus butt.

[http://www.emsisoft.com/en/software/free/](http://www.emsisoft.com/en/software/free/)

use in safe mode and use with care

if you can't use safe mode thats ok.  but you will have to do it again to clean out recovery partition in safe mode

---

### Post by AmerNewbieInDE on 2009-08-18
boot windows in safe mood, run regedit, 
 
warning, careful what you delete, if your not sure what it is, look on the internet. i recommend [http://www.liutilities.com/products/wintaskspro/processlibrary/](http://www.liutilities.com/products/wintaskspro/processlibrary/) . On the right side (process search) put the name of the process in, it will tell you about it and what it does. Ok back to regedit.
 
on the left side..goto
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Run
and
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run
 
On the right side it shows the stuff that starts automatically, alot is unneeded and sloows the pc down, but as i said before, know what is is before you delete. Look for the process that starts your "particularly nasty malware Windows Antivirus Pro" click on it, delete it. you can also delete other stuff you dont want to start up automatically.
Guess i should also say this, BEFORE YOU DELETE ANYTHING; BACK UP YOU REG SETTING: How? easiest way is, after you get to HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Run, right click on `Run` then export, somewhere you can find it. Then on the right click and delete. And do the same when you get to HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run
when all is done, restart your PC and now the process is not running and you should have your control back. HINT... uninstall it..
 
Oh, before restarting, also look at Start>programs>startup.. see if it is there... 
 
then restart

---

### Post by balaknair on 2009-08-18
Chances are that if it's a well-written virus(or more likely a Trojan), by now it's probably infected multiple files or folders on your system and is probably buried in the registry, so that even if you delete the file, it will still be able to restablish itself when you next run Windows. It could also have created backdoors that will remain open after deleting the file and allow other malware to download and install on your PC.
So the **safest option** is to wipe your Windows partitions and reinstall Windows(but of course you need a Windows CD for this), install a decent Antivirus program(I'd recommend Avira Free AV) and update your Windows install with all patches from MS(painful, I know). Download and install patches-reboot-repeat till the updater tells you your install is up-to-date.

Alternate Suggestions:

1) Try running a scan with an AV on Ubuntu(like BitDefender for unices) either n a Live CD session or from the Wubi-installed Ubuntu and see if it can fix this virus
[http://tombuntu.com/index.php/2009/07/07/download-and-install-bitdefender-antivirus-on-ubuntu-with-1-year-free-license/](http://tombuntu.com/index.php/2009/07/07/download-and-install-bitdefender-antivirus-on-ubuntu-with-1-year-free-license/)

2) BitDefender has a GUI Knoppix-based LiveCD that you can use to run an AV scan without starting Windows. I've used it in the past on friends' PCs. 
On booting it updates itself, and can scan for rootkits as well.
Download it here(around 245 MB)
[http://download.bitdefender.com/rescue_cd/](http://download.bitdefender.com/rescue_cd/)

Other vendors like Kaspersky and F-Secure also offer rescue CDs, but IMO bitdefender has the one with the most complete set of features(easy to use GUI, automatically updates in the Live Session, does a deep scan of the hard drive including for rootkits).
You will still need to boot in safe mode after this and run another scan from within Windows(safe mode) to clean up your system.

3) Many commercial AV vendors offer free online scans, like Trend Micro, Bitdefender and Kaspersky. The problem here of course that many malicious programs also block access to these websites, so you might not be able to do it logged into Windows. I don't know how well these will work from within a LiveCD session or logged into Ubuntu, since they usually require a small app installed on the local hard drive first.

If reinstalling Windows:
1- disconnect from the internet till you have the basic protection(an antivirus app) in place.
2- When you do connect to the net, the first thing to do is update your AV program.
Next, launch IE to connect to Windows update and install all security(high priority) patches.
3- Install drivers, other apps you need (like an Office suite etc), Firefox(and get the NoScript addon), scan each file you download with your installed AV.

Remember, antivirus can do VERY little to protect you from malware. the best defense is intelligent computing(Don't run as administrator unless it's to do system maintenance or install TRUSTED apps, avoid shady websites, don't download/install 'warez', and always update your system).
I'd also recommend the Secunia Personal Software Inspector(a must have for Windows), a great little app that will scan your drive and tell you which apps are out-dated or insecure, and usually will provide links to update them. This is especially useful for common non-MS sotware like Flash which have such a bad reputation for security.

---

### Post by Fenris_rising on 2010-02-19
I helped my brother-in-law out last night with one of these 'security' virus type programs on their XP PC. I tried booting with a live cd and managed but couldn't remember how to get RW permission to drop the Malwarebytes exe file from my USB stick onto the HDD. (Still a lot to learn =D )

But booting in safe mode (lucky guess) allowed me to install the app and kill 125 infected instances =O

Koobface was the main issue listed amongst a lot of other crap.

They had Norton, up to date and running but I explained to them you still need to be aware of what sites your visiting and what links your clicking as you can still circumvent your security. Norton wanted to charge them a lot of money to sort it. It took me 4 hours, next time I will be faster, but a lot of that was removing norton and installing Avira, spybot, Firefox with ABT. Then cleaning their file system and defragging the drive.

I got £20 forced on me for doing it but I just hope what I said about careful browsing sticks!

regards

Fenris

---

