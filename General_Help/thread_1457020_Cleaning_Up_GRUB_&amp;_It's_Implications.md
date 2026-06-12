---
title: "Cleaning Up GRUB &amp; It's Implications ?"
date: 2010-04-18
forum: General Help
---

### Post by chrisqck on 2010-04-18
Hi Everyone, 

Would like to ask for some advise regarding GRUB. 

I have been using Windows for a long time and recently have finally decided to switch to Linux. A good friend recommended Ubuntu and I have installed it on an 8GB USB thumbdrive for test drive. Nowadays, I mainly boot from this thumbdrive for my personal computing use. [*I am a supporter of the "Immersion Learning" school. The only way for me to really learn is to force myself to use the system* :D]

Anyway, as I frequently updates my Ubuntu 9.10 via the Update Manager, I found my GRUB screen now have multiple entries like below: 

"Ubuntu, Linux 2.6.31-20-generic"
"Ubuntu, Linux 2.6.31-20-generic (recovery mode)"
"Ubuntu, Linux 2.6.31-16-generic"
"Ubuntu, Linux 2.6.31-16-generic (recovery mode)"
"Ubuntu, Linux 2.6.31-14-generic"
"Ubuntu, Linux 2.6.31-14-generic (recovery mode)"


I would like to remove the last 4 lines but: 

1. I'm not sure how to do it?

2. And do i just delete the entries or do i also have to delete some system files? *{this is important as i am running this on a USB thumbdrive and would like to remove any files that are no longer necessarily and keep the installation as lean as possible}*.

Thanks in advance for any advise given. It has been a great experience personal computing Sans-Windows and I hope some where in the future to be fully weaned of Windows ;) 

cheers, 

Christos

---

### Post by wilee-nilee on 2010-04-18
Generally keeping at least two kernels installed is suggested, in case one has problems you can boot with another. Since you are new at this and deleting kernels can cause problems, you might install Ubuntu Tweak it will remove kernels and cache stuff and do other useful things.
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

So did you do a full install to the USB or a unetbootin or other loader?

I believe that sudo apt-get autoremove will remove the headers from grub, you can also look in synaptic at autoremove it will probably have the 14 and 16 kernel there ready to be removed.

---

### Post by chrisqck on 2010-04-18
hi wilee-nilee, 

thanks you for the reply & recommendations. i've tried "sudo apt-get autoremove" but it didn't find anything to remove. so i gave ubuntu tweak a try. it seems to find the entries so i asked it to remove. i followed your advise of keeping current & current-1 kernel though so only removed 2.6.31-14. i will restart the computer in a moment to confirm everything is fine. 

ubuntu tweak seems like a very cool app, btw. i'm gonna explore more of it after this. Thanks again for the recommendations :D


regards, 

Christos

---

### Post by ed-koala on 2010-04-18
If everything is working in your current kernel you can probably delete the other also, if you *really* need the room.

It is advised to keep 2 just in case something goes crazy on ya, especially when the kernel gets upgraded.

---

### Post by oldos2er on 2010-04-18
You can use Ubuntu Tweak to remove kernels, but it's not necessary. Open Synaptic Package Manager, search for linux-image, mark the 2.6.31-14-generic kernel for removal, click Apply. Your grub menu will be automatically updated.

---

### Post by chrisqck on 2010-04-20
**@ ed-koala :** thanks. i was thinking along the same line, especially with 10.4 LTS now in Beta 2 stage already. planning to do an in-place upgrade when it's finalised instd of a fresh install. 

**@ oldos2er :** thanks for the alternative method. i guess Ubuntu Tweak is kinda like TweakUI for windows then? I'll keep this tip in mind when it's time to remove 2.6.31-16-generic.

---

