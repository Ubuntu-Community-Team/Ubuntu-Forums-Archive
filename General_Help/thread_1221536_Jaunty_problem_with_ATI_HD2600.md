---
title: "Jaunty problem with ATI HD2600"
date: 2009-07-24
forum: General Help
---

### Post by bleyz on 2009-07-24
I've just installed Jaunty on my computer and installation process worked like a charm. Though things have changed when the Jaunty starts for the first time. Computer was slow to crawl at the beginning, which was the same with my notebook computer with integrated Nvidia gpu. That notebook worked great when I installed video drivers from Nvidia, so I tried to do same thing and installed the latest driver for my HD2600 Pro from the section called "Hardware Drivers". The result was disappearing top panel and a nonfunctional problem. Then I've made some research on net and read some people succeed with installing the driver from ATI website. I've just tried the same thing, though with no luck. I've made some serious search in forums, though I couldn't find an exact solution for my problem. So I've decided to ask for help. Thanks in advance to everyone who shared time to read all the way to here :D

---

### Post by jbrown96 on 2009-07-24
Unfortunately, ATI makes horrible drivers. They have cut off support for your graphics card on the newer drivers. I believe that you will have to get <=9.5 (the may release). 

The version that Ubuntu provides in the Hardware Drivers section should work. Could you elaborate some more on what happened when you installed those drivers? Did the desktop come up, login screen?

---

### Post by bleyz on 2009-07-24
Thanks for the reply friend. :popcorn:To be honest I'm aware of the fact that my gpu card doesn't belong the the latest generation, though it's not reasonable to consider it as legacy. So if ATI excluded the support for my gpu from their driver, I find it very odd.

As I've said, when the system is newly installed it was a torture to browse between programs and windows, it was very laggy and slow. I find it very normal, 'cos same thing happen at my notebook computer with Nvidia gpu before I install proper display drivers. After installation it works like charm now. I've hoped it will be the same with my desktop computer too, though it seems fate had other plans (and maybe ATI too :D ). 

Firstly I've tried "Hardware Drivers" in option built in ubuntu, and it said that I have to restart the computer for new ATI drivers funtion properly. After rebooting the computer, I have discovered that Ubuntu's perception of "proper" is very different than mine : computer was extremely laggy, it was impossible to execute a program and screen was flashing up a little bit from time to time. Then I've disabled that driver and installed the original driver from ATI's website. That slow and laggy situation continues on, also disappearance of top panel and program panels came as a bonus. Then I've decided that I need some help and started this thread. I suppose you know the rest of the story :D

---

### Post by Yellow Pasque on 2009-07-24
The RadeonHD 2k (R6x0) series is still supported in the latest Catalyst drivers. It is the support for R500 (Radeon X1k) and older cards that have been discontinued.

---

### Post by bleyz on 2009-07-24
> **Temüjin said:**
> The RadeonHD 2k (R6x0) series is still supported in the latest Catalyst drivers. It is the support for R500 (Radeon X1k) and older cards that have been discontinued.

It's nice to hear that, thanks for the information friend :). Any ideas why my video driver is malfunctioning? I really want to use my Jaunty as soon as possible.

---

### Post by jbrown96 on 2009-07-25
Sorry about the bad info on your card. I thought they cut off support for cards below the 3000 series. 

What do you mean that the drivers from the ATI website didn't work? Did they install? If so, what happened on the next boot -- black screen? How did you install the drivers? 

I have a computer with a HD3200, and I've never had problems installing drivers, so I'm trying to figure out where the problem occured.

---

### Post by bleyz on 2009-07-25
It just doesn't work. I can login to the system, though no panels or program bars are visible and the system is terribly laggy. It seems that there's no problem with installation of video drivers, because catalyst is there and it acts like it's functioning well. This ATI video driver problem is a known issue and is not unique to me ([http://tech.shantanugoel.com/2009/05/04/ubuntu-904-jaunty-jackalope-upgrade-graphics-problem.html](http://tech.shantanugoel.com/2009/05/04/ubuntu-904-jaunty-jackalope-upgrade-graphics-problem.html)). I am really surprised the issue isn't still resolved by Ubuntu :confused: Isn't this distro meant to be for masses?

---

### Post by jbrown96 on 2009-07-25
I think you've answered your own question. ATI won't support the Xorg version in 9.04. There's nothing that Ubuntu can do about it; they don't have access to the driver code.

---

### Post by bleyz on 2009-07-25
> **jbrown96 said:**
> I think you've answered your own question. ATI won't support the Xorg version in 9.04. There's nothing that Ubuntu can do about it; they don't have access to the driver code.

I get your point. But they could work together with ATI to fix the situation. If Ubuntu claims to be the linux distro for masses it has to be different than some distros. If your OS has some serious problems with ATI's products, which is one of two serious players in discrete graphic cards market, you have to think about the overall user experience of the OS again. I know most of the time ATI is the one to blame for the bad drivers for Linux, but for kernel's sake, does a regular user has to think about it's whose fault when a primary part of his/her computer doesn't work. If it doesn't work, it isn't useful for regular user. By the way, does Ubuntu puts a warning on their pages about the Jaunty incompability with the latest ATI cards? Such a big issue must have been mentioned on the download page as a warning for users, not just as a line in the "known issues" page. If Ubuntu thinks something makes it different than the many other distros for average computer user, it must act like that all the time. Average user doesn't really care about the problems (and doesn't really have to) that drivers create for the most basic computer parts. Maybe it's not a right approach, but it works just this way. I just remember all the times that regular users blame Windows for problems caused by bad or faulty drivers, why shouldn't it apply for linux?

---

