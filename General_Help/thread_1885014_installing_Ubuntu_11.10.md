---
title: "installing Ubuntu 11.10"
date: 2011-11-22
forum: General Help
---

### Post by solringel on 2011-11-22
hi i am new to linux and could use some help

i installed ubuntu 11.10 on my LG R380 laptop i installed with the CD at it all went fine and the instillation finished and when it tries to boot it just stays on the purple screen with a pointer that i can use with the mouse i don't know much about linux and need help thanks 

Sol

---

### Post by pixiq on 2011-11-22
.

---

### Post by hg088 on 2011-11-22
does the boot loader appear? something similar happened to me when i installed oneiric on my new desktop. the problem was that ubuntu had some compatibility issues with my video card. the fix was to manually set the framebuffer on the boot loader (grub2)

try to look for your cards framebuffer and how to set it in grub ([https://wiki.ubuntu.com/FrameBuffer](https://wiki.ubuntu.com/FrameBuffer))

---

### Post by sudodus on 2011-11-22
If that does not work, try 11.04. It works for me, and it looks very similar during the live session and after installation. By the way what graphics chip is it?

---

### Post by Mark Phelps on 2011-11-22
> **pixiq said:**
> Maybe I can also get some ideas from here. I'm thinking about USB booting, but it looks a little hard to get Ubuntu running. What version of Ubuntu is easiest to get running?

Please don't hijack the original poster's thread with your own, very different, question.  It makes it very difficult to provide help when folks mix up different problems.  Please start your own thread.

---

### Post by Mark Phelps on 2011-11-22
How long does it stay on the purple screen? Depending on the specs of your PC, it could take several minutes to get to the logon screen.

---

### Post by pixiq on 2011-11-22
.

---

### Post by pixiq on 2011-11-24
Hello again solringel

Sorry for the hi-jacking. I'm new and didn't understand how to behave. Anyway, here are some tips from another newbie:

Ubuntu 10.04 LTS is fine for my desktop and laptop. My laptop is older than yours (I googled and found yours has core2duo and nvidia graphics, maybe it is as powerful as my desktop or slightly faster). Also 11.10 worked on my desktop (tested only live).

---

### Post by machdohvah on 2011-11-24
Hello all... So here is my story.

I finally decided to try 11.04 and it installed just fine and I was willing to live with the differences that I complained about earlier for 10.10 is going bye bye in April 2012.

Then I upgraded to 11.10... There were many things that I need to mention to the ptogrammers...

1. There were many warnings that were in the category of "This process cannot run for a dependency process has not been installed". This means that the installation steps were in the wrong order.

2. I also noticed that there were several processes that duplicated each other. Sloppy!

3. Then 11.10 failed to re-boot. I had to go on to a cold boot.

4. Immediately there was a message "Waiting for network configuration". That timed out.

5. Then it failed to continue. Therefore it failed to cold boot.

I would like to note that I finally was able to boot on the 1st partition where my DOS 6.20 resides. THANK YOU!

So, I re-installed 11.04 only to find that it also FAILED TO BOOT.

I had to install 10.10 and erase the partition in the process. This succeeded and is the only reason I am able to report all of this on-line.

PS. I wish there was a way to erase the grub information on a disk with no partitions with a history of having GRUB there. Currently, I cannot find a way to do that so that the HD may be used with Systems that need that to be cleaned off such as Windows 98, and DOS 6.20

PPS: I again installed 11.04 cleanly and found the classic login which solved all of my previous objections, but I still question 11.10 as above.

---

### Post by sudodus on 2011-11-24
@machdohvah
If you browse the link
[https://help.ubuntu.com/community/Grub2 ]("https://help.ubuntu.com/community/Grub2")
you will find several tips how to update and tweak grub on your computer

@solringel
After reading machdohvah's post I suggest again, that you try Ubuntu 11.04. It might be nice on your computer

---

### Post by sudodus on 2011-11-24
@machdohvah once more

I think it would be enough to overwrite or re-write the master boot record, the first 512 bytes of the disk. Browse the internet for MBR tools to do it in a more user-friendly way!

---

### Post by internetprofiles1 on 2011-12-02
After like 3 days trying methods of rewriting the MBR with ubuntu 11.10 i have come to the conclusion the the booter loader for that version is defective. First i had a dualboot then i desided to erase and go completely with ubuntu 11.10 but like most i would get a failed install with the busybox error,i reinstalled windows tried it and it worked fine tried dual boot installed again but this time 11.10 did not even recognize my windows partition. So i Wiped the drive clean reinstalled 11.10 and it so would not load. When i tried the live cd it reported my drive having only free space no partitions. I tried all the reinstall grub methods and none worked. Last night i just decided to revert to 10.04lts version in 30 mins i was up and running and during install it even detected i had version 11.10 installled but for some reasion i guess the grub got messed up. I was not worried about datd as i already made backups. Anyways that was my fix. I see some people reported success with 11.04, maybe i will give that a try and see what happens but i will not do the upgrade to 11.10

I was wondering, maybe i had a bad iso burnt, but with so many reports of the same problem, i doubth it. Could i have used the grub from the 10.04 version to repair my mbr? Then reload 11.10?

---

### Post by machdohvah on 2011-12-04
I have successfully installed 11.10 and it is wonderful. Many of my issues have been addressed. I regret that the "Classic Login" has been dropped. I would like it back. Specifically, I would like to have a status bar on the bottom like Windows. If there is a skin download that would make this version look like Windows Vista, I would be happy.

PS: I forgot to mention that I downloaded an ISO image and burned that to a CD and installed from there.

---

### Post by WasMeHere on 2011-12-05
> **machdohvah said:**
> I have successfully installed 11.10 and it is wonderful. Many of my issues have been addressed. I regret that the "Classic Login" has been dropped. I would like it back. Specifically, I would like to have a status bar on the bottom like Windows. If there is a skin download that would make this version look like Windows Vista, I would be happy.

PS: I forgot to mention that I downloaded an ISO image and burned that to a CD and installed from there.

Try this one:[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showpost.php?p=11508479&postcount=91_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11508479&postcount=91")
Or this one: [[COLOR="RoyalBlue"]_http://ubuntuforums.org/showpost.php?p=11508520&postcount=93_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11508520&postcount=93")
*Edit: Or even better this thread:*
[[COLOR="RoyalBlue"]_Oneiric Classic (No effects) Tweaks and tricks_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1886799")

---

### Post by machdohvah on 2011-12-06
An update that I just downloaded installed a Gnome Classic login option. Thanks!

---

