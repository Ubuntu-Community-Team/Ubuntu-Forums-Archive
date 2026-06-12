---
title: "&quot;mounting aufs on /root failed: No such device&quot; on Remastersys backup failed boot"
date: 2010-10-23
forum: General Help
---

### Post by inameiname on 2010-10-23
I just noticed today my Remastersys backup DVD will not boot into either Live CD or 'install', and the message that interrupts the usual process is as follows:

According to "BusyBox v1.15.3":

"(initramfs) mount: mounting aufs on /root failed: No such device
Aufs mount failed"

Because of this, my backup is a waste. Fortunately, I have prior backups.

Anyway, noticing that the only real update I did prior to my last was to update the kernel to 2.6.36, it's obvious that is the culprit. 2.6.35 does not have this issue. Oh, and that latest kernel came from Ricotz's ppa, which has never given many any trouble in past kernel upgrades. 

I should also note that I've Googled this issue, and it seems it's definitely an issue with the kernel, that there is no longer aufs support or something in the latest one. Can somebody confirm this?

Basically, any help would be greatly appreciated. I'd love to know why it only now pops up as an issue, as I've had 2.6.35 and older kernels, from Ricotz's ppa as well as kernel/ppa as well, and never had trouble with those non-Ubuntu-official ones. Does that mean it's just this version, 2.6.36?

---

### Post by chenxiaolong on 2010-10-23
There's nothing wrong with Ricotz's kernel 2.6.36. The AuFS developers haven't created a version compatible with kernel 2.6.36 yet, so that error will happen on any build of kernel 2.6.36. The only thing you can do right now is to wait for the AuFS release and hopefully have Ricotz include it in the PPA.

---

### Post by inameiname on 2010-10-23
Gotcha. Thanks for the clarification.

Does that mean aufs support is no longer a standard with a basic, standard, generic (I don't compile it myself with such support) kernel? Or merely this aufs support just happens to not yyet be included in the latest kernel, possibly because the kernel was merely release before the aufs folks who do that support for the kernels just haven't had a chance to update it yet? I'm just curious how this all works. Hopefully it's just something that sometimes occurs because not everyone can update everything for a kernel at the same time.

Thanks again.

---

### Post by chenxiaolong on 2010-10-23
You're welcome :D!

AuFS is not part of the standard kernel from [http://kernel.org](http://kernel.org). Many distros (such as Ubuntu, Fedora, Arch Linux, Sabayon Linux, etc.) include it in their kernels because it's efficient for live CD's. The default Ubuntu kernel (2.6.35) has AuFS included in it and Remastersys takes advantage of that to make backups. Since AuFS hasn't been updated for kernel 2.6.36 yet and Remastersys requires AuFS, you get an error when you boot the live CD. You are correct in that not everyone can update everything for a kernel at the same time. It's pretty hard to make something for a kernel before it's released :D.

---

### Post by inameiname on 2010-10-23
Awesome. Thanks for clarifying things for me. I understand now. Seeing as how I've primarily used Ubuntu, and Remastersys, and only using kernels built for it, official and whatnot, I'm used to Aufs support being a standard thing. Now I get it.

Thanks again. Guess I must just wait. Not an issue.

---

### Post by chenxiaolong on 2010-10-23
Glad to be of help :D!

I'll post here whenever AuFS is update for kernel 2.6.36.

---

### Post by inameiname on 2010-10-23
Awesome.

---

### Post by reqqq on 2011-07-08
any new answer about this problem i have also ?i did  a backup iso image of my 11.04 distro with remastersys ,tried to install on virtual box on windows from usb(using attach physical disk to vm so as to boot up )  & from dvd & have the same problem.tried also to do this on a v.box on my ubuntu distro & had the same thing .if any answer to solve this problem or other way to make a bootable cd or usb of my system as it is now with all stuff installed (programms updates everything) for installation if my system broke or installation on other pc  -any option acceptable 
thanks

ps besides the above problem i have the mdio-gpio error which i dont think creates this problem -if so please give me a solution if something

thanks again

---

### Post by inameiname on 2011-07-09
> **reqqq said:**
> any new answer about this problem i have also ?i did  a backup iso image of my 11.04 distro with remastersys ,tried to install on virtual box on windows from usb(using attach physical disk to vm so as to boot up )  & from dvd & have the same problem.tried also to do this on a v.box on my ubuntu distro & had the same thing .if any answer to solve this problem or other way to make a bootable cd or usb of my system as it is now with all stuff installed (programms updates everything) for installation if my system broke or installation on other pc  -any option acceptable 
thanks

ps besides the above problem i have the mdio-gpio error which i dont think creates this problem -if so please give me a solution if something

thanks again


I'm afraid I don't really know how to help you. This is an old thread, and it just fixed itself long ago, presumably what needed updated, was updated. And as for on Natty, I haven't noticed any issues using Remastersys to make a custom live cd.\

Have you first verified that the Remastered Custom CD/USB image is good by running it on the computer at startup? Maybe its an issue between it and Virtualbox within Windows.

---

### Post by reqqq on 2011-07-09
> **inameiname said:**
> I'm afraid I don't really know how to help you. This is an old thread, and it just fixed itself long ago, presumably what needed updated, was updated. And as for on Natty, I haven't noticed any issues using Remastersys to make a custom live cd.\

Have you first verified that the Remastered Custom CD/USB image is good by running it on the computer at startup? Maybe its an issue between it and Virtualbox within Windows.


you mean my friend outside of virtual box on my already ubuntu system ?maybe i am wrong but i created the remastersys iso & did a startup disk creator which verified me that i can use this usb to startup my system on another pc anywhere,tried & i have the issue ,also i did an iso dvd  /usb & also the same thing . i am wrong in any step maybe?i did lots of alchemies trying to boot up .i think i do something wrong but what ?besides i follow the steps from tutorials exactly 
thanks

---

### Post by inameiname on 2011-07-09
> **reqqq said:**
> you mean my friend outside of virtual box on my already ubuntu system ?maybe i am wrong but i created the remastersys iso & did a startup disk creator which verified me that i can use this usb to startup my system on another pc anywhere,tried & i have the issue ,also i did an iso dvd  /usb & also the same thing . i am wrong in any step maybe?i did lots of alchemies trying to boot up .i think i do something wrong but what ?besides i follow the steps from tutorials exactly 
thanks

Yeah, I just meant after you've created the Remastered ISO, and put it on a disc/usb, you tried to boot it up your already Ubuntu-made system, try starting it inside the disc into live cd mode on your machine and verifying it failed there too, along with trying to boot it up inside Virtualbox. I think you got it. Anyway, as I haven't noticed the issue with it on mine, nor most others according to Remastersys website lately, it has to be something on your machine that is conflicting with how its being made. 

What kernel are you using? Perhaps its having the same sort of issue mine was having last year when this issue came up for me. FYI, mine is linux-image-2.6.39-0-generic. It is from ppa:kernel-ppa, however, looking at the PPA, is seems to not be there anymore. So you'd have to get it elsewhere.

---

### Post by reqqq on 2011-07-10
> **inameiname said:**
> Yeah, I just meant after you've created the Remastered ISO, and put it on a disc/usb, you tried to boot it up your already Ubuntu-made system, try starting it inside the disc into live cd mode on your machine and verifying it failed there too, along with trying to boot it up inside Virtualbox. I think you got it. Anyway, as I haven't noticed the issue with it on mine, nor most others according to Remastersys website lately, it has to be something on your machine that is conflicting with how its being made. 

What kernel are you using? Perhaps its having the same sort of issue mine was having last year when this issue came up for me. FYI, mine is linux-image-2.6.39-0-generic. It is from ppa:kernel-ppa, however, looking at the PPA, is seems to not be there anymore. So you'd have to get it elsewhere.

i had already installed [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc4-natty/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.39-rc4-natty/") cause i had wifi issues -i did that to boot up from usb outeside v.box & the same thing -i dont know how to search if there is an issue with rc4 -it starts & brings the screen with the choices to install live cd etc & then mounting aufs failed again-i m really pissed off cause i cant find a solution without bothering someone in here :))
thanks

ps i read somewhere that if virtual box is installed and try to remastersys your system could cause a problem -removed virtual box & give a try again -if this is a known problem pls post else i ll inform about my results after removing v.box

---

### Post by reqqq on 2011-07-10
> **reqqq said:**
> i had already installed [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc4-natty/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.39-rc4-natty/") cause i had wifi issues -i did that to boot up from usb outeside v.box & the same thing -i dont know how to search if there is an issue with rc4 -it starts & brings the screen with the choices to install live cd etc & then mounting aufs failed again-i m really pissed off cause i cant find a solution without bothering someone in here :))
thanks

ps i read somewhere that if virtual box is installed and try to remastersys your system could cause a problem -removed virtual box & give a try again -if this is a known problem pls post else i ll inform about my results after removing v.box

sorry i write again about this problem but i did everything i think & i cant make a bootable usb or cd of my system so as to boot up on a virtual machine or in any pc ,something goes wrong but i cant realise what?????????

maybe the appropriate use of remastersys is firstly to copy some hidden folders from home to skel directory that i didnt do!!!!! and then start remastersys????? is it possible this be the problem i found in a tutorial???i ll try also but which are the folders u have to copy if this is a step i forgot -we ll see
sorry again i bother with my questions 
thanks

---

### Post by reqqq on 2011-07-10
> **reqqq said:**
> sorry i write again about this problem but i did everything i think & i cant make a bootable usb or cd of my system so as to boot up on a virtual machine or in any pc ,something goes wrong but i cant realise what?????????

maybe the appropriate use of remastersys is firstly to copy some hidden folders from home to skel directory that i didnt do!!!!! and then start remastersys????? is it possible this be the problem i found in a tutorial???i ll try also but which are the folders u have to copy if this is a step i forgot -we ll see
sorry again i bother with my questions 
thanks


hear again -nothing happened the same problem -if someone knows how this can be resolved pls help
thanks

---

### Post by inameiname on 2011-07-11
> **reqqq said:**
> hear again -nothing happened the same problem -if someone knows how this can be resolved pls help
thanks

Yeah, I don't really know what would be the issue. I don't use Virtualbox, so I have never tried to make a Remastersys backup with Virtualbox installed.

On that note, have you tried to post your issue on Remastersys's main website? Whenever I've had issues like this, which obviously I did when I posted this thread, and I always post on Remastersys's website as well, as the creator of tends to be a bit more familiar with the program and why something is causing errors. He's a pretty cool guy, and has helped me more than once to resolve any issues I've had. So if you haven't, you should.

---

### Post by inameiname on 2011-07-11
> **reqqq said:**
> i had already installed [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc4-natty/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.39-rc4-natty/") cause i had wifi issues -i did that to boot up from usb outeside v.box & the same thing -i dont know how to search if there is an issue with rc4 -it starts & brings the screen with the choices to install live cd etc & then mounting aufs failed again-i m really pissed off cause i cant find a solution without bothering someone in here :))
thanks

ps i read somewhere that if virtual box is installed and try to remastersys your system could cause a problem -removed virtual box & give a try again -if this is a known problem pls post else i ll inform about my results after removing v.box


Maybe there is something with that kernel. I don't use that version of 2.6.39, but the one that used to be in the actually kernel-ppa on Launchpad, with isn't the one you use. Mine is 2.6.39-0.5~20110427. 

One thing you could try is downgrading your kernel to see if thats causing all the trouble. Best to try the default Ubuntu Natty kernel as found in the official repos.

---

### Post by reqqq on 2011-07-11
> **inameiname said:**
> Maybe there is something with that kernel. I don't use that version of 2.6.39, but the one that used to be in the actually kernel-ppa on Launchpad, with isn't the one you use. Mine is 2.6.39-0.5~20110427. 

One thing you could try is downgrading your kernel to see if thats causing all the trouble. Best to try the default Ubuntu Natty kernel as found in the official repos.

thank you my friend i ll give a try with the official kernel & i ll see:D
thanks a lot

---

### Post by inameiname on 2011-07-11
> **reqqq said:**
> thank you my friend i ll give a try with the official kernel & i ll see:D
thanks a lot

Sure. Feel free to let me know if it works for ya.

---

### Post by rajesh.kalapura on 2011-07-14
> **reqqq said:**
> you mean my friend outside of virtual box on my already ubuntu system ?maybe i am wrong but i created the remastersys iso & did a startup disk creator which verified me that i can use this usb to startup my system on another pc anywhere,tried & i have the issue ,also i did an iso dvd  /usb & also the same thing . i am wrong in any step maybe?i did lots of alchemies trying to boot up .i think i do something wrong but what ?besides i follow the steps from tutorials exactly 
thanks

Hi reqqq:- I had also same problem with remastered cd of Ubuntu Natty. Recompiling the Natty kernel with aufs2 is the only fix for this.Anyway I have successfully recompiled kernel with aufs2 and now it booted successfully.:P:P:P

---

### Post by inameiname on 2011-07-14
> **rajesh.kalapura said:**
> Hi reqqq:- I had also same problem with remastered cd of Ubuntu Natty. Recompiling the Natty kernel with aufs2 is the only fix for this.Anyway I have successfully recompiled kernel with aufs2 and now it booted successfully.:P:P:P

If you have successfully compiled the kernel with aufs2, could you possibly upload it somewhere for reqqq and those who have had this issue? Only if its easy for you, thanks.

---

### Post by reqqq on 2011-07-15
> **rajesh.kalapura said:**
> Hi reqqq:- I had also same problem with remastered cd of Ubuntu Natty. Recompiling the Natty kernel with aufs2 is the only fix for this.Anyway I have successfully recompiled kernel with aufs2 and now it booted successfully.:P:P:P

thanks my friend about your time but firstly you had the same kernel as i mention above?2.6.39 or the official kernel? if you had the same kernel  plz give some instructions somewhere how you did that as inameiname              says 
thanks in advance

maybe you did that with module-assistant?? i tried yesterday i think but i did nothing

ps i think i am gonna use previous updated kernels 2.6.38.11 in which i can locate aufs ,couldnt do that in 2.6.39, so as to see if i can create a bootable remastersys iso

---

### Post by reqqq on 2011-07-15
guys thanks for the help 
finally my remastersys iso ,booted up in virtual box , using previous updated kernel 2.6.38-11 i used(i did the iso while my pc booted up with  2.6.38 ) -it seems that kernel i used  2.6.39 had issues ,missing aufs mainly .i prefered use official kernel as inameiname says ,besides i wanna try if i have a solution how to do it , recompiling kernel 2.6.39  with aufs if it works.also with the official updated kernel 2.6.38 i have no wifi issues as i used to when i first installed natty .probably solved these issues 
thanks again

and i have a silly question for most of you ,how can i choose which kernel i wanna use permanently in my linux pc,because it boots up with 2.6.39 

thanks again

---

### Post by inameiname on 2011-07-15
> **reqqq said:**
> guys thanks for the help 
finally my remastersys iso ,booted up in virtual box , using previous updated kernel 2.6.38-11 i used(i did the iso while my pc booted up with  2.6.38 ) -it seems that kernel i used  2.6.39 had issues ,missing aufs mainly .i prefered use official kernel as inameiname says ,besides i wanna try if i have a solution how to do it , recompiling kernel 2.6.39  with aufs if it works.also with the official updated kernel 2.6.38 i have no wifi issues as i used to when i first installed natty .probably solved these issues 
thanks again

and i have a silly question for most of you ,how can i choose which kernel i wanna use permanently in my linux pc,because it boots up with 2.6.39 

thanks again


All you have to do is get to the boot menu, to change the default kernel booting from 2.6.39, to the older one, 2.6.38. Unfortunately, I cannot remember which button you push, <ESC>, <F1>, <F2>, <Shift>, ? What I do actually is to use startupmanager (sudo apt-get install startupmanager). It allows you to designate with kernel you want booted.

Also, using a program called 'dpkg-repack', I repackaged the 2.6.39-0-generic kernel version I use that used to be found in the kernel-ppa PPA. Having used 'dpkg-repack' before, I've never had a problem with installing the repackaged debs onto other systems, so it should work for you. Its just I've never tried repackaging kernels before. But again, I don't see why not it wouldn't work.

FYI, here is what "aptitude show" outputs about 'dpkg-repack":

> 
me~ $ show dpkg-repack
Package: dpkg-repack                     
State: installed
Automatically installed: no
Version: 1.33ubuntu2
Priority: optional
Section: admin
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 69.6 k
Depends: perl
Description: puts an unpacked .deb file back together
 dpkg-repack creates a .deb file out of a package that has already been
 installed. If any changes have been made to the package while it was unpacked
 (ie, files in /etc were modified), the new package will inherit the changes. 
 
 This utility can make it easy to copy packages from one computer to another, or
 to recreate packages that are installed on your system, but no longer available
 elsewhere, or to store the current state of a package before you upgrade it.
Homepage: [http://kitenet.net/~joey/code/dpkg-repack/]("http://kitenet.net/%7Ejoey/code/dpkg-repack/")


Anyway, here is the repackaged debs for you to use. I didn't modify anything the kernel (as the 'aptitude show' above mentions the new package will inherit the changes), so they should be the same as the ones I originally installed:

[http://www.2shared.com/file/S4YeY8Cm/linux-kernel-2639-0-generic_26.html](http://www.2shared.com/file/S4YeY8Cm/linux-kernel-2639-0-generic_26.html)

---

### Post by reqqq on 2011-07-15
> **inameiname said:**
> All you have to do is get to the boot menu, to change the default kernel booting from 2.6.39, to the older one, 2.6.38. Unfortunately, I cannot remember which button you push, <ESC>, <F1>, <F2>, <Shift>, ? What I do actually is to use startupmanager (sudo apt-get install startupmanager). It allows you to designate with kernel you want booted.

Also, using a program called 'dpkg-repack', I repackaged the 2.6.39-0-generic kernel version I use that used to be found in the kernel-ppa PPA. Having used 'dpkg-repack' before, I've never had a problem with installing the repackaged debs onto other systems, so it should work for you. Its just I've never tried repackaging kernels before. But again, I don't see why not it wouldn't work.

FYI, here is what "aptitude show" outputs about 'dpkg-repack":



Anyway, here is the repackaged debs for you to use. I didn't modify anything the kernel (as the 'aptitude show' above mentions the new package will inherit the changes), so they should be the same as the ones I originally installed:

[http://www.2shared.com/file/S4YeY8Cm/linux-kernel-2639-0-generic_26.html](http://www.2shared.com/file/S4YeY8Cm/linux-kernel-2639-0-generic_26.html)


thanks man for the help
i ll give a try & i ll be back if problem is found again \\:D/

---

### Post by rajesh.kalapura on 2011-07-16
> **reqqq said:**
> thanks man for the help
i ll give a try & i ll be back if problem is found again \\:D/

Hi reqqq : My way of patching the kernel with aufs, you can download from [COLOR="Red"][[COLOR="Red"]**here**[/COLOR]]("http://ubuntuone.com/p/14jc/")[/COLOR]. I don't know this one is the correct way or not?.Anyway remastered dvd is booting and installed also,except the live cd shows some error like "stdin error:0,unable to load random state "etc ..That also if we press "esc" key only. Anyway don't forget to keep the old kernels after installation,if anything happens.
                                              Use @ your own risk..:guitar:

---

### Post by reqqq on 2011-07-16
> **rajesh.kalapura said:**
> Hi reqqq : My way of patching the kernel with aufs, you can download from [COLOR=Red][[COLOR=Red]**here**[/COLOR]]("http://ubuntuone.com/p/14jc/")[/COLOR]. I don't know this one is the correct way or not?.Anyway remastered dvd is booting and installed also,except the live cd shows some error like "stdin error:0,unable to load random state "etc ..That also if we press "esc" key only. Anyway don't forget to keep the old kernels after installation,if anything happens.
                                              Use @ your own risk..:guitar:

thanks friend ,it worked fine with the older kernel -for now it looks ok -i ll try to patch newer kernel with aufs to see-thanks again:)

---

### Post by inameiname on 2011-07-16
> **reqqq said:**
> thanks man for the help
i ll give a try & i ll be back if problem is found again \\:D/


No problem. Either way, my debs or Rajesh's method to make them, as he said, use at your own risk and be sure not to delete the old ones. At least until you know one or the other works. 

Regardless, if the older kernel is working for you, that is probably good enough. Unless there is something new in the latest kernel that is important enough to try one of our 'custom' kernels with Aufs. Eventually there will be a newer version out anyway with the latest kernel with Aufs support built-in.

---

