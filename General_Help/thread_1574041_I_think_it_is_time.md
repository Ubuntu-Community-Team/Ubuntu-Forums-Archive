---
title: "I think it is time"
date: 2010-09-13
forum: General Help
---

### Post by Lejirl on 2010-09-13
Hello
I am so very tired of Window crashes and blue screens and windows just plain giving me errors that I have to research constantly to resolve. I have read recently lots of people making the switch to Linux and the Ubuntu name always comes up as the most easiest to setup. But before I make the change I just have a few questions I was hoping I could get answerd.
 
1/ I play World of Warcraft, I have read in game people play it with Linux. I was wondering how diificult it would be to set this up. Are there walkthroughs to do this?
 
2/ My Wife also uses the computer to surf and read email, would this be hard for her to adjust to. She needs to be able to see an icon and double click like in windows.
 
3/ I have read there is no need for anti virus and firewalls for Linux, is this true, hype or is this something you should have. I assume a firewall at least.
 
I figure I am going to need to read and learn and thats fine I like to learn. I am not a novice in Windows, but I can drive a car and not control a plane so wondering if I am venturing that way. I am excited to get home and try this. Any responses would be great.
 
Thank You for your time.

---

### Post by Rubi1200 on 2010-09-13
> **Lejirl said:**
> Hello
I am so very tired of Window crashes and blue screens and windows just plain giving me errors that I have to research constantly to resolve. I have read recently lots of people making the switch to Linux and the Ubuntu name always comes up as the most easiest to setup. But before I make the change I just have a few questions I was hoping I could get answerd.
 
1/ I play World of Warcraft, I have read in game people play it with Linux. I was wondering how diificult it would be to set this up. Are there walkthroughs to do this?
 
2/ My Wife also uses the computer to surf and read email, would this be hard for her to adjust to. She needs to be able to see an icon and double click like in windows.
 
3/ I have read there is no need for anti virus and firewalls for Linux, is this true, hype or is this something you should have. I assume a firewall at least.
 
I figure I am going to need to read and learn and thats fine I like to learn. I am not a novice in Windows, but I can drive a car and not control a plane so wondering if I am venturing that way. I am excited to get home and try this. Any responses would be great.
 
Thank You for your time.
The most important thing to remember is that Linux is not Windows; it works differently, but if you hang out here on the forums and are willing to accept a learning curve the rewards are there for the taking.

1. as far as I know it is possible; look in the WINE sub-forum for answers.

2. yes she can; there is Firefox and Evolution

3. no need for antivirus; firewall depends on whether your router has one; if yes no need.

4. some useful links:
[http://sites.google.com/site/easylinuxtipsproject/Home](http://sites.google.com/site/easylinuxtipsproject/Home)
[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)
[http://ohioloco.ubuntuforums.org/showthread.php?t=801404](http://ohioloco.ubuntuforums.org/showthread.php?t=801404)

Good luck and welcome :-)

---

### Post by snowpine on 2010-09-13
Welcome to the forums! I think you will find Ubuntu is a fun adventure, and that most of your questions can be answered by searching these forums and the [Ubuntu wiki]("http://wiki.ubuntu.com"). :)

I would encourage you to keep your existing Windows install. The easiest way to do this is to run Ubuntu for a while as a Live CD with no change to your computer (just as you would test drive a car). Once you are satisfied Ubuntu is something you want to commit to, you can install it in a "dual boot" configuration with Windows by creating a separate partition or by using WUBI. 

Whatever you do, read the instructions and ask lots of questions here on the forums. 

To quickly address your specific questions

1) No idea, sorry

2) Let her use Windows if she likes it! :)

3) Linux is very secure. Most of the world's supercomputers and web servers run Linux. This does not, however, mean you can do whatever you like with no risk. We have [an entire sub-forum]("http://ubuntuforums.org/forumdisplay.php?f=338") for discussing this topic! So give the "sticky" topics a read and you'll be off to a good start.

---

### Post by s.fox on 2010-09-13
Hello and welcome to the forums,

I would also like to point you to the [Ubuntu Manual Project]("http://files.ubuntu-manual.org/manuals/getting-started-with-ubuntu/10.04e2/en_US/screen/Getting%20Started%20with%20Ubuntu%2010.04%20-%20Second%20Edition.pdf").

It is a handy resource for users to have, especially people new to Ubuntu.  Well worth a flick though for the basics.  If you have any more questions then please do post back :)

-Silver Fox

---

### Post by Lejirl on 2010-09-13
Thank you both, I am keeping XP on another partition for now.  My Wife Actually wants to make the switch also, she just wanted to make sure it would be easy to surf and read mail.  I am making the switch as Windows 7 and XP keep blue screening!  All hardware has been confirmed as having no issues.  I am jumping in with both feet on this one, but my Daughter will have Windows on her system so there will be access to it if needed.
 
Thank you for all the links to read and I will utilise the search functions :)

---

### Post by coffeecat on 2010-09-13
> **Lejirl said:**
> 3/ I have read there is no need for anti virus and firewalls for Linux, is this true, hype or is this something you should have. I assume a firewall at least.
 

You are correct to assume a firewall at least but if you've read that there is no need for a firewall in Linux and that Ubuntu does not have one, then you have read something misleading.

The Linux firewall is called iptables, a part of the kernel, and is included in Ubuntu. By default, Ubuntu has no open ports on public interfaces which is just fine for most users. If you do need to configure iptables for special rules there are a number of GUI interfaces for this. People coming from Windows tend to confuse these GUI tools with the actual firewall. You will see a lot of this misunderstanding on this forum. You simply open up the GUI interface to do your configuration and then close it down while iptables continues to do its work in the background.

If you want a GUI interface, gufw from the repository is a good bet. You'll often see Firestarter recommended. It looks good, has a user-friendly interface, but has one big drawback. It is buggy and unreliable and this is because it has been  unmaintained for too long and is suffering from bitrot. A pity.

---

### Post by wainbee on 2010-09-13
Lejirl, it was time for me too. I'm a 20 year veteran of Windows who recently switched after the horror of Vista and the continuing update and security hassles with XP.  Windows now just looks downright unfriendly.  

I'm loving Ubuntu; I hold the mouse over the speaker icon and adjust the sound volume with the mousewheel... I hold the mouse over the MP3 file in Ubuntu's file manager and the song plays!  So simple, so intuitive, so brilliant!

Your letter implies that you expect to wrestle learning Ubuntu and your wife may prefer Windows.  I found the opposite: Ubuntu EXCELS with web browsing, email and multimedia.  As soon as I placed the Google Chrome (browser) and Thunderbird (email) icons on the Desktop, my wife and kids were up and running with Ubuntu and now WILL NOT SWITCH BACK!

Here's my answers to your questions:
1. There are not many game applications ported to Linux.  This will change as more people move over.  Wine or Virtual Box may provide interim solutions.

2. Your wife and family will choose Ubuntu for all online activity because they don't have to rely on virus checker subscriptions and updates.  Plus Ubuntu is much more multimedia friendly.  You'll be watching DVD movies and video content in no time.

3.  It sounds like you have more than one computer in your household... may I suggest you purchase a router ($50 to $75) to provide internet distribution with the added security of a firewall.

Personally, I recommend Windows users set up a dual boot installation from the forum tutorials. WUBI is not adequate and has let many beginners down when kernel updates damage the boot files.  With a dual boot installation, you can keep your Windows personal data in place and read and write to it with Ubuntu.  When you master Ubuntu, getting rid of Windows altogether is easy.

Good luck and have fun!

---

### Post by v1ad on 2010-09-13
i heard wow can be played on Linux also.

---

### Post by Chris1274 on 2010-09-13
I might recommend that before you install Ubuntu you first try it out by running a live session off the CD. That will allow you to check if there are any hardware compatibility issues before making any changes to your system.

---

### Post by cloyd on 2010-09-13
I second what many say here. 
1. Try the live cd
2. Dual boot. 
When you have decided you don't need windows any more, you can simply delete the partition and format it for your Ubuntu system. But you'll have the safety of being able to go back to something familiar if you need to, and if you have trouble with Wine and WOW, then you can still use windows. Personally, it didn't take me long to decide I didn't need Windows on my system.  At first, it was nice to keep it around, but I'm proud it is gone. If I were a gamer, I may want to keep Windows just for that.

---

### Post by Lejirl on 2010-09-14
Well I decided to just jump in, I was planning on reinstalling windows so figured if it was to difficult I will just put xp or win 7 back in.  So this is how it went.

I downloaded and burned the disk.
Installed Ubuntu 10.04, was asked to update it.  I needed remote software, I did not want to mess to much with guide for logmein, researched on here and Google and Team-viewer was mentioned, installed in minutes.  All the other tools I needed were there already.  So  really all I installed was Team-viewer and Chrome, oh adobe flash also.  O/S was installed before I finished dinner and the rest was 20 min @ most of reading and config. While I was doing something else my Wife went on the pc, seen the icon for internet on top bar, when I came out she asked "did you change the layout of windows" and that was that.

I was very, very impressed with the ease of install and how quickly I was offered advice and things to read.  It is late so I will tackle WoW tomorrow. 
 
:popcorn:

---

### Post by Kir_B on 2010-09-14
Hey.

Approximately one year ago, I too decided that it was time.

I can measure in minutes (+/- 240 minutes), the time I've spent in my Windoze system and that time was spent trying to help a friend with his wife's laptop! I don't seem to have a need for M$ anymore and am seriously considering a complete removal, which will be a happy day, possibly resembling a good old fashioned book burning celebration, without the crazies, but with plenty of the rhetoric!

I've, at times felt like I've been in way over my head, but it always ends well and the rewards are well worth the efforts, thanks in no small part to the wonderfully helpful community here and elsewhere.

I wish you all the luck in the world, as I believe that you'll be well rewarded, as I have been.

Peace! Kirby

P.S. If you plan on setting up a dual boot, PerfectDisk has a trial offer that is excellent for defragging your windows **_during boot_**, which will make it much safer to resize the partitions safely.

---

