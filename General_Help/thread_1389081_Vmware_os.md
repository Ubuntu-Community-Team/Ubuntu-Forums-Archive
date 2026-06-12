---
title: "Vmware os?"
date: 2010-01-23
forum: General Help
---

### Post by giuseppe105 on 2010-01-23
Hi i don't know if this is in the right spot but is there a Linux operating system like vmware. So you boot it up and you can choose ether you want to run windows or Linux?

---

### Post by jamesisin on 2010-01-23
Well, VMware deals with virtualization.  There is VirtualBox (there is a version in the repos but I prefer to add a different repo/version) for that.

You may be interested in creating a dual-boot system.  They are different.  You can see a bit here:

[http://ubuntuforums.org/showthread.php?t=1388429](http://ubuntuforums.org/showthread.php?t=1388429)

---

### Post by HermanAB on 2010-01-23
If you have suitable hardware, then you can use KVM, which is in the Linux kernel distribution.

Otherwise, you can use VMware Player, or Virtualbox, which are less picky about hardware requirements.

---

### Post by steveneddy on 2010-01-24
> **giuseppe105 said:**
> Hi i don't know if this is in the right spot but is there a Linux operating system like vmware. So you boot it up and you can choose ether you want to run windows or Linux?

VMware is not an operating system.

Most computers are able to have Windows and Linux installed at the same time and you decide at boot by using  boot loader, like Grub is used when you install Linux.

If you want a "dual boot" system, install Windows first, then Linux. Most Linux distros will install Grub or some other boot loader so that you can choose either Windows or Linux at boot time.

From one of the links in my sig:

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

You should read the links in my sig and bookmark them. They will help you understand what you are getting into much better and be a source for answers in the future.

---

### Post by giuseppe105 on 2010-01-24
Thank you for the posts but i understand dual booting and how to do it i know what boot loaders are i was hopeing that there was an os that would allow me to run multipul os's i dont want to have to reboot the computer whenever i want to play a game. i could just run windows and not need to reboot. i would like to be able to boot virtual comps so when i want to browse the ubuntu forums i would boot linux and when i wanted to play crysis i could boot windows. and when i am going to be away for a while i could leave it at the vm os.

---

### Post by jamesisin on 2010-01-24
Which is why I recommended running VirtualBox under Ubuntu.

---

### Post by pirateghost on 2010-01-24
> **giuseppe105 said:**
> Thank you for the posts but i understand dual booting and how to do it i know what boot loaders are i was hopeing that there was an os that would allow me to run multipul os's i dont want to have to reboot the computer whenever i want to play a game. i could just run windows and not need to reboot. i would like to be able to boot virtual comps so when i want to browse the ubuntu forums i would boot linux and when i wanted to play crysis i could boot windows. and when i am going to be away for a while i could leave it at the vm os.

this doesnt exist.

if you want a VM you still have to have a HOST OS.  whether that host os be a hypervisor like esx/esxi/xenserver or an actual OS like ubuntu.  you cannot install a hypervisor that will allow you to select which OS you want to BOOT to.  you install a host os, then install a virtualization technology (virtualbox is recommended if ubuntu is your host os) then run your vm.  what you are looking for does not exist AT THIS TIME, however there is a lot of innovation making its way into the virtualization world and i would expect something similar in the next few years.

---

### Post by giuseppe105 on 2010-01-25
Is there a small lightweight Linux OS that i can install virtual box on like dsl or puppy Linux?

---

### Post by blur xc on 2010-01-25
> **giuseppe105 said:**
> Is there a small lightweight Linux OS that i can install virtual box on like dsl or puppy Linux?

I'm using crunch bang #! linux in vbox as I'm typing this right now.  It's a small, light, fast, easy on resources distro that's 100% ubuntu underneath.

BM

---

### Post by J V on 2010-01-25
> **giuseppe105 said:**
> Thank you for the posts but i understand dual booting and how to do it i know what boot loaders are i was hopeing that there was an os that would allow me to run multipul os's i dont want to have to reboot the computer whenever i want to play a game. i could just run windows and not need to reboot. i would like to be able to boot virtual comps so when i want to browse the ubuntu forums i would boot linux and when i wanted to play crysis i could boot windows. and when i am going to be away for a while i could leave it at the vm os.Unfortunately, mike is good at keeping his windows shut, you can't get hardware acceleration on windows Vbox (even though vbox is better than vmware) so 3d games won't work, dual boot, kvm, or bust!

If you want a super light-weight OS optimized for speed to run vbox... tiny core? 

Ooh! With extra modifications to remove all apps but vbox too! (Now that sounds like a project!)

---

### Post by giuseppe105 on 2010-01-25
k now that i figured this all out. whats the point of dual boot why have 1 os for games and 1 for an os?

why not just use the game one and when you need to use the computer just run it?

I ran ubuntu for a while but found it more of a bother to run my apps wouldent work and i couldent play games. when i was in ubuntu i felt like i was traped in a box with littel toys.

i may be bashing here but linux is awsome too. I will be going to colledge soon and i will be useing it daily.

this is strictly opinion. Linux is like mac it is only usefull for non home stuff. Mac is buizzness and linux is buizzness too. when you want to do things like games or apps such as voice or webcam you are restricted to 1 app.

K if your still here after my rant.

I need a nice os to work on for colledge. Do you have a Nice low cpu and ram os that can be run and is up to date. Ubuntu is awsome but its going toward vista it takes 500mbs ram and cpu hovers around 20%.

thanks ahead of time...

I looked at the crunch bang website i looked at the screen shots and it was at 3% cpu and 111mb ram in idol.  too bad i didn't know the specs of the computer that was running it.

---

### Post by jamesisin on 2010-01-25
My first computer was an Apple IIc, then a Mac Plus.  I started using Windows machines around the release of 98.  I began using (Red Hat) Linux in 1999.  That being said, I disagree that Linux is 'buzz' or that there are restrictions for its use.

My main machine is Ubuntu 8.10 (and will likely upgrade to 10.04 or 10.10 when they come out).  I still use those other operating systems (especially Windows because I support them), but I do what I want on the Ubuntu systems and only use the others when something someone else is doing requires it (like helping someone fix a Windows machine).

I build Ubuntu machines for folks around here who might not be able to get a computer otherwise:

[http://www.soundunreason.com/InkWell/?page_id=313](http://www.soundunreason.com/InkWell/?page_id=313)

I will quote from my own page because I think it's absolutely true:

> I believe that anybody can use Linux and get by just fine, doing all they want to do.

So, give Ubuntu a shot as your OS of choice when you head off to college.  I would, however, recommend preferring the LTS releases (8.04 or 10.04 depending on how long you want to wait).

(I find that 8.10 is sufficiently stable and represents enough improvement to warrant using it over 8.04.  Other opinions may differ.)

---

