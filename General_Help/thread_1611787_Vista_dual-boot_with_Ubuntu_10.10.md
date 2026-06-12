---
title: "Vista dual-boot with Ubuntu 10.10"
date: 2010-11-02
forum: General Help
---

### Post by philferrar on 2010-11-02
A friend's Fujitsu Siemens Esprimo laptop was running Vista [slowly] from a 120Gig HD set up with 'him' and 'her' user-id's. I got him to try loading Ubuntu 10.10 from a LiveCD but when taking the 'install' command there was no option to install alongside Vista. I saw in the forum that you should use a Vista utility [after a de-frag] to shrink the Vista partition. We did this and freed up 40+ Gig. During the next LIveCD load we opted to use 'advanced' for partitioning and made a 35 Gig [/ Ext 4] and a 5 Gig [Swap] before completing the installation without any errors. Ubuntu now loads from the 1st grub entry but the sis graphics card limits resolution to 800 x 600 [I'll look into this further later]. Enties 5 and 6 on grub are for Vista and Vista Recovery options. Entry 5 goes through a few screens but will not load properly and loops back on itself. Entry 6 loads Vista o.k. but at a point where only one of the two users ['his'] is visible but it does run o.k.
Question 1: Is there something I can do to get the 5th grub entry working properly so that Vista loads as normal and displays the two user-id icons ? 
Question 2: As there seems to be a lot of issues with Ubuntu on this particular laptop would you advise running another distro like Mandriva or Mint that I've read may handle the sis graphics better ?
Question 3: If we did install one of the above distros over the Ubuntu image on the 35 Gig partition would that have a good chance of creating a grub where Vista and Mandriva [or Mint] ran happily together.
Thanks for any help, Phil

---

### Post by Joeb454 on 2010-11-02
*Thread moved to **General Help**.*

---

### Post by Sickpuppy87 on 2010-11-02
> Entry 5 goes through a few screens but will not load properly and loops back on itself.Any error messages ?  What screens does it show before it reboots?

---

### Post by philferrar on 2010-11-02
There were no error messages as such. Taking the normal Vista load option gave a black screen with a white bar at the bottom with some words like "Windows is loading" being displayed but what happened then was that another screen / pop-up mini menu appeared with about 4 options on it - I'm sorry I'm working from memory here as I don't currently have access to the laptop in question to tell you exactly. However Opt 1 was something like "fix or repair" - following this didn't do anything or provide further help and after just a few seconds came back to the mini menu. Opt 2 was to rebuild Vista from it's back-up partition [?] to factory issue state, which is not what we wanted. The remaining Opts were probably referring to something more drastic and inappropriate or simply to do a cold re-boot. My point was that the main grub menu entry to run Vista didn't work as expected. This is the first time I've dual booted Vista, but I've done many XP dual-boots [with 2, 3 or more O/Ss installed on the same drive] and all have worked perfectly. Do you think that the normal Vista load option is recoverable, and if so, how would I go about it ?

---

### Post by Sickpuppy87 on 2010-11-02
My guess is that something wasn't happy after you resized the partition....


Take a look here let me know if this helps.....


[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20Windows%20Vista%20/%207%20Partitions]("https://help.ubuntu.com/community/RecoveringWindows#Resizing%20Windows%20Vista%20/%207%20Partitions")


Mostly this section:

**Resizing a Windows Partition in Linux**

 In the GPartEd or QTPartEd Partition Editors the tick-box **align to cylinders** must **NOT**  be ticked because Windows 7 and Vista partitions usually start in  sector 2048 instead of the normal standard sector 63.  The Windows  boot-loader needs Windows to start misaligned from the cylinder  boundaries. 
 
**How To Recover**

 To recover from this boot problem, you can either; 

[LIST=1]
[*]Boot from your [Windows Recovery Cd]("https://help.ubuntu.com/community/WindowsRecoveryCd") and select "startup repair". 
[*]Download. 
[LIST]
[*]For Vista : [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/) 
[*]For Windows 7 : [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/) 
[/LIST]

[LIST=1]
[*]Burn the ISO to a disc 
[*]Boot up from it 
[*]Select Startup Repair.
[/LIST]
[/LIST]

---

### Post by wilee-nilee on 2010-11-02
Post the bootscript in my signature run on that computer. **Post the text in code tags this is very important there is a description in my signature.**

Also please post in paragraphs it is very difficult to read otherwise and get to the heart of the problem.;)

---

### Post by philferrar on 2010-11-02
Thanks for the info. I'd have thought that as I shrank the original Vista partition using the Vista utility and received no errors then that bit went o.k. - do you agree, or have I missed something ?
If we get Vista to load under the last grub option [recovery] and then run 'fixmbr' is that going to 
[a] make Vista boot normally 
[b] leave the current partitions unaltered 
[c] make Ubuntu / grub menu disappear ?
If the answer to all 3 is 'yes' then would we best move forward by running LiveCD, deleting the 35Gig [/ Ext4] and 5Gig [Swap] partitions and closing down.
Then re-boot from LiveCD and attempt another Ubuntu install - this time taking the "use largest amount of free space" option ?

---

### Post by wilee-nilee on 2010-11-02
I would post that bootscript there may be problems that show up with it. use it for yourself it is a excellent tool.

You have messed around enough to just stop where your at, and post the script and get some qualified help. **Any answers without seeing the script are assumptions at best.**

---

### Post by philferrar on 2010-11-03
Hi Wilee-Nilee, Thanks for your posts. I'm not familiar with bootscript but will do as you ask next time I get access to my friends laptop. I read the links you provided and downloaded the script and had a quick read - may have to wait until the weekend before I get a chance to run it on his kit.

---

### Post by cpickeri on 2010-11-16
Hi,

I am experiencing the same issue on my laptop.
Vista home premium edition dual boot with ubuntu 10.10.

Anytime I try to log into vista the OS starts to load with the loading bar that displays in the middle of the screen...after a few seconds it just reboots. 

Sometimes it successfully boots into vista but usually it fails and automatically reboot. I did this 5 times in a row before giving up.

Not sure what the issue is with vista.

---

### Post by oldfred on 2010-11-16
cpickeri
Because everyone's boot script results.txt is different you need to start a new thread and post the results.txt, so we can see the details of your system.
Did Vista boot after the resize? It usually wants to run chkdsk. Other repairs may be required, but it is best to review your system from the boot script output.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by cpickeri on 2010-11-16
Thanks for the response. I also wanted to mention that I am a big fan of Ubuntu and think it is a fantastic OS. I have a half dozen or so of my friends using it now and they all love it.

Back to the issue....I would suspect it is a bug with the Grub bootloader based on finding a similar issue when searching on google. 

Alternative solution is to use another boot manager:

- boot into vista
- install easyBCD (gui boot management tool)
- start easyBCD
- click on bootloader setup and click the "write MBR" (make sure you have the correct version of OS selected
- then click add new entry
- choose linux tab and type (grub 2 for ubuntu 10.10)

Done

This boot manager has no qualms with vista or any other OS and it will allow for you to boot up into Linux automatically.

Hope that helps solve the problem.
-

---

