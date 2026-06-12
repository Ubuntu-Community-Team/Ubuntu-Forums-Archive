---
title: "installation problem"
date: 2011-07-01
forum: General Help
---

### Post by monte001 on 2011-07-01
Hello, new to the community.

I tried linux 4 days ago and had the following installation problem.

Probably same question had been asked. but appreciated if can point to places where I can search for solution.

cpu is amd athlon 64X2 dual
MB is magic pro mp-a2am-hd+

I had tried ubuntu 9.04 10.04 10.10 11.04
red hat and mint 11

But all freeze during installtion or frozen mouse pointer or no key board response.

Monte

---

### Post by CaptainMark on 2011-07-01
can you run a livecd with no problems?? this is an odd problem to have with all these distros, as usually a freeze on installation means a badly copied cd. Try using a liveusb instead if you have a spare usb stick, alternatively try burning a cd at the lowest possible write speed or better still use someone else pc to burn a disc

---

### Post by Rubi1200 on 2011-07-01
Hi and welcome to the forums monte001 :)

I assume you are currently using Windows; is that correct?

If yes, take a screenshot from the Disk Management utility of the drives and post it here.

If no, use the LiveCD and take a screenshot of how GParted sees the disk.

Thanks.

---

### Post by monte001 on 2011-07-01
thank you all for your replies.

I had been using linux for the last 4 days.

the cds that I used can install on other machines but not the magic pro, so bad cds should not be an issue.

yes, I was using windows before trying out the linux.

but I will take your advice and try the liveCD.

will report on the update tomorrow.

Monte

---

### Post by monte001 on 2011-07-01
same problem with liveCD.

if I may try to explain further:

trying ubuntu without installation is fine, but with installation, all steps can be performed until restart.

after restart, the desktop with frozen mouse pointer cannot be further any more.

I had tried to install the program with other machine and put the finished program on this machine,

the result was the same desktop with frozen mouse pointer after restart.

fresh installatiion or along side with windows resulted the same.

any suggestion ?

monte

---

### Post by Rubi1200 on 2011-07-02
Take a look in BIOS and see if there is a setting for the mouse and keyboard that you can change.

Also try with another mouse and see if that is the issue.

---

### Post by monte001 on 2011-07-02
thanks rubi12000.

I tried changing the mouse and keyboard setting in the bio, still no luck.

just a silly question for all who want to help me because I do not want to spend further time on experimenting.

"can ubuntu be installed on nfts format or it must be installed on ext4 ?"

monte

---

### Post by monte001 on 2011-07-04
quick follow-up

after few days of reading and fooling around with the os, I found the solution by chance.

the problem lies in, which are mentioned again and again in this forum, that linux is not working well with ATI.

to make a short story long, I did a fresh installation of windows,

followed by a fresh installation of ubuntu so that I can have a grub page at boot up,

then at the grub page, I select recovery boot and then select the FailsafeX.

it worked so far, may be I don't know what I have missed by not loading the full program.

without the windows installation, my linux knowledge does not permit to boot to failsafeX.

I will continue to try linux furhter before making up my mind.

monte

---

### Post by wildmanne39 on 2011-07-04
> "can ubuntu be installed on nfts format or it must be installed on ext4 ?Hi, the answer to this question is that the system files can not be on ntfs it has to be on ext3 or ext4, you can have a home partition ntfs so you can access like pictures and music from windows or ubuntu.

---

### Post by monte001 on 2011-07-04
> **wildmanne39 said:**
> Hi, the answer to this question is that the system files can not be on ntfs it has to be on ext3 or ext4, you can have a home partition ntfs so you can access like pictures and music from windows or ubuntu.

thanks w-39.

is there a difference between ext3 and ext4 ?

monte

ps I thought i solved my machine problem, but after working for a while, it hangs with mouse pointer frozen.

---

### Post by mastablasta on 2011-07-04
> **monte001 said:**
> thanks w-39.
 
is there a difference between ext3 and ext4 ?
 

 
yes: 
[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)
[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)
 
> 
ps I thought i solved my machine problem, but after working for a while, it hangs with mouse pointer frozen.
 
 
well you never posted exactly what kind of graphics card you have. did you install additional drivers (proprietary drivers)?
 
Also try 10.04 LTS maybe you will have more luck.

---

### Post by monte001 on 2011-07-16
to report on update of progress.

disappear from the forum for some time because i was still struggling with ubuntu.

i would not say that i am on the verge ot giving up, but rather consider this as a challenge.

my problem is not solved yet and it seemed that there were lots of similar complains on the forum.

to those that really wanted to help me, please read on...

my computer was approx 5+ years old.

it is:

cpu is amd athlon 64X2 dual
MB is magic pro mp-a2am-hd+
all others are on board ie Lan, Sound and video
the lan, I belief, is realtec
the sound, also realtec
the video, ati radeon x 1200
ram 2 gb

i tried installation with acpi=off, noapic, nolapic, nomodeset and the other 2 options which i forgot their names.

but i could not even pass the language selection page because of frozen mouse, key board had no response.

i finally had ubuntu installed on a hd from another machine, and took that hd to this magic pro machine.

the boot up went on, automatically log on, but monitor had frozen mouse pointer, no key board response, when finished.

don't know if it hangs or not, but seems that way.

had to hard boot again, with same result.

after many days of fooling around and reading, having tried all the suggested solution from the forum, still no luck.

lone behold :

may be some one can explain this strange phenomenon,

if i tapped any key, mainly the left shift key, continuously for the whole minute during booting until it is finished, most if not all the time, the mouse pointer then can be moved and  i can run ubuntu 11.04.

now that i found this way, i dare not move anything on the computer, but sit stupidly for one minute and tapping the shift key frantically until the booting was finished, only to find i may be able to run ubuntu.

but have to add that once i have it started, i can use it for 2 days without trouble, ie slags or hang ups.


Hope some friends can give me further assistance.

monte

---

### Post by wildmanne39 on 2011-07-16
Hi, I am a little over my head on this one but is sounds like a hardware issue with ubuntu, like maybe the keyboard possiblely.

Are you using any of the nomodeset parameters when you have a successful boot?

Also after you boot look at your dmesg log file and boot file with log file viewer and see if it tells you have any errors.

---

### Post by monte001 on 2011-07-17
thank you w-39

at first, i just thought that this was only a small matter that nobody would have noticed or worth the while of reporting,

then after one day, i received your response.

i don't know how to use dmesg or view log file, but i will certainly try to learn that in order to tackle the problem.

after at least 50 to 60 hours of working and testing ubuntu with this old machine, i can report for some certainty that the mouse and keyboard are not the issue.

i had tried : ubuntu 704, 804, 904, 1004, 1010, 1104, mint11 and red hat fedora.

all ubuntu installation with testing on all different option at f6.

the best i can report on this machine was ubuntu904 with the option at f4 for safe mode (i can't remember the exact name).

but the downside was there was no further update to keep the version current.

now i am trying ubuntu1104 with nomodeset and the self made manuvre that i had described above, with all updates installed.

if the self made manuvre was not good, then i had to hard boot the machine.

if it is successful, then all runs the same except one small difference. there should be an appelet at left lower panel for the ongoing running program so that you can bring it up to the desktop after you have the program mininized.

it disappeared on this old machine. so after i mininized a running program, i don't know where it went or how to bring to back to the desktop.

monte

ps i don't know how to report this as a bug or may be it is not worthwhile to trouble the developing team.

---

### Post by monte001 on 2011-07-18
w-39

i looked at the 2 files.

there was nothing logged on the boot file.

the dmseg was very long and i don't know what to look for.

can you help me please.

monte

---

