---
title: "New user"
date: 2012-01-27
forum: General Help
---

### Post by HOUSEE on 2012-01-27
Hi everyone.

I've been a Windows user for 12 years now, and I'm getting sick of it and I want to change to linux. What distribution do you recommend? I have a few doubts, specially if I'll be able to find alternatives to the software I use in Windows. Here is a list:

aimp2
messenger
steam
nonamescript + mirc
photoshop
convertxtodvd
internet download manager
Jdownloader
daemon tools
winrar
ashampoo burning studio
itunes
klite codec pack (includes Media Player Classic)

Another big issue is the games. I haven't been playing on my PC for some time know, but I wanted to know which alternatives do I have if I want to play games every now and then, specially recent ones.

And what about virus? Should I get an antivirus? What would you recommend? 

Thanks a lot for any help.

---

### Post by westie457 on 2012-01-27
Hello welcome to the Forum

Take a look [here]("http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software") for a list of Windows programs and their Linux equivalents.

As for games take a look at [http://www.winehq.org/](http://www.winehq.org/) for games that are likely to run. For these you will need to install Wine or PlayonLinux.

For those games that will not run on Linux or in Wine the best choice is to set up a Dual-boot system.

As for antivirus it is not strictly necessary in a non-Windows operating system. Many around here only use antivirus when sharing files with non-Linux users.


Most of the software you are likely to use is available from the repositories at a cost of nothing.

---

### Post by drmrgd on 2012-01-27
Hi and welcome!

In regard to the distribution you chose, everyone is going to recommend something different based on their preferences and tastes.  I would recommend sticking to those that are a little more user friendly for new users like Ubuntu or Fedora.  In the case of Ubuntu, you can download the .iso and make a CD, which can then be used to demo the operating system without having to install and commit to it.

Software is always going to be a tricky business.  For many of the applications you list below there is a linux equivalent that will do just what you want (with or without a slight learning curve to get used to the fine differences between what you're used to and the equivalent package).  You might just Google search for those applications to see what you can find that will do what you'd like to do.

For me, gaming has been a been struggle in Linux.  I have not had a lot of success running many of the games that I've played in Windows on Linux.  It's really hit and miss.  So I decided to dual boot Ubuntu and Windows, and I just switch over to my Windows partition when I want to game.  That being said, though, there are some great strides being made in this arena, and I'm very hopeful that before long, there will be a larger base of gaming under Linux.

Finally, many people say that Linux is a much more secure environment than Windows, and viruses are not a major concern.  I would agree with the caveat that poor system management habits and browsing in unsafe places is not smart using any OS.  I have found, though, that my computer has been infection free for a long time (much, much longer than when I ran Windows solely) despite similar browsing habits and not having installed any kind of antivirus on my Ubuntu system.  

So, in short, I would say make a Live CD of Ubuntu, and check out what you can and can't do with it.  If you like it, dual boot with Windows just in case you can't find replacement software in Ubuntu to suit your needs.  And finally...have fun with it!

---

### Post by SuaSwe on 2012-01-27
Hello HOUSEE,

Considering you're on the Ubuntu Forums, you can probably guess what distro I'm going to recommend. ;)

Looking at that list, I can name good alternatives available in Ubuntu for all of the ones I'm familiar with; this is easy enough to research anyway, in some cases (such as Photoshop) you may find that the features differ from or are not quite up to what you are used to, however this all depends on what your usage level is in the first place, so again some research may be necessary!

If you're not completely sure whether you are ready to make the switch immediately, why not try [dual-booting]("https://help.ubuntu.com/community/WindowsDualBoot") until you are sure? Then you have the benefit of both Windows and Linux and can try the latter until you know whether it will work for you.

As for antivirus, I would personally say that you don't need it in Linux, at least I never have; its structure and built-in security features makes it much less vulnerable than Windows.

---

### Post by HOUSEE on 2012-01-27
Thanks a lot guys, you have been a big help. What about the 32/64 bits? I have 4GB of RAM so i'll be needing the 64 bit version, right? Can I find problems by not using the 32 bit version?

---

### Post by Mark Phelps on 2012-01-27
As a FIRST step, strongly suggest you go to the WineHQ website, their application compatibility database page, and look up EACH of the Windows apps you want to run.

As you will see, some are rated GARBAGE -- meaning, they're NOT going to work, no matter what you do.  Some are rated Bronize (minimal functionality -- not usefull), some are Silver (some useful functionality).

If you rely on a particular Windows app on a day-to-day basis, any rating less than GOLD is going to frustrate you -- due to lack of needed functionality.

For example, photoshop, convertXtoDVD, and Ashampoo Burning Studio are not going to work for you in Linux.

Also, successful Windows 3D gaming relies not just on Wine, but also on the 3D acceleration and DirectX support available in Linux drivers for your video chipset. Without the 3D acceleration, and DirectX support, you will find gaming (with Windows games) to be a frustrating experience in Linux.

Once you do all of this, you need to make a PERSONAL assessment regarding whether switching to Linux is the right thing for YOU.

---

### Post by HOUSEE on 2012-01-27
Ok thanks. I still need help about the 64 bit thing and I have another question.

How does it work with drivers? Is it easy to get them as it is for Windows?

---

### Post by nothingspecial on 2012-01-27
It is much easier if your hardware is supported. Things will just work because the drivers are included within Ubuntu. If some of your hardware is not supported things can be tricky. The best thing to do is boot a live cd or usb and see if everything works.

---

### Post by HOUSEE on 2012-01-28
Thanks @nothingspecial.

Can anyone help with this question about the 64bits?

> **HOUSEE said:**
> Thanks a lot guys, you have been a big help. What about the 32/64 bits? I have 4GB of RAM so i'll be needing the 64 bit version, right? Can I find problems by not using the 32 bit version?

---

### Post by oldos2er on 2012-01-28
General consensus is if you have 64-bit hardware, make the most of it by using 64-bit software.

---

