---
title: "system can not be loaded"
date: 2011-10-13
forum: General Help
---

### Post by farus.pri.ee on 2011-10-13
Hello everybody...
During update installation which are doing automatically ubuntu PC has stopped responding so I needed to restart it. And then it can't mount system... I have grub windows with three choises but everywhere is same picture that you can see (attachmen&#1077;)
Ok I tried to rescue it with Ubuntu Alternate installation disk but at the last moment when it offered to mount root dir it can nnot mount it...
NExt step was loading live-cd and it said me also that can't mount root logical drive.
Other logical disk  (not root) loaded successfully
I even can't load command line interface...

By the way this pc stop responding very offen and my opinion is NVIDIA driver something wrong... IT stopped in sleep mode.. it stopped just simply... it stopped in screen saver... 
Why I think it is nvidia? because I have other computer with absolutely same system except integrated INTEL video and works perfect.

So... what to do? 
[IMG]http://forum.ee/index.php?app=core&module=attach&section=attach&attach_rel_module=post&attach_id=152649[/IMG]

---

### Post by Rubi1200 on 2011-10-13
Hi and welcome to the forums :-)

You could try using nomodeset.

See here for more details:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by farus.pri.ee on 2011-10-13
What is it? You thing I have issue with nvidia but it is my general suggestion why it is stopped working.
Main problem to mount main logical(root) drive because you can see at the picture it has just grub and can't do nothing with drive
I even can't mount it with live cd 
Gparted can't see this root drive
is it possible that it is encryptet so it can't mount because of crypting?
Is it possible to mount if I know password?

May be it was sooo... disk was crypted but some reason ubuntu was crashed and no it can't see key... is it possible using live cd to check was it encrypted or not?

---

### Post by alphaamanitin on 2011-10-13
Hmm, did you use the alternate install disk to install Ubuntu?  Do you remember setting up any encryption scheme?  If so you need more specialized recovery steps than I can tell you.  That is the type of errors I would expect to get if you did encrypt your hd.


AlphaA

---

### Post by farus.pri.ee on 2011-10-13
Hi,,,
As I remember I did not install any crypting choises but my friend saw this picture and heard my explanation of situation said me about password protected hdd but he said he can look this PC just one month later... so I asked here and just offering ideas for solution

One more detail about this situation.... this ubunto was installed about 6 month ago and update was standart update. So it was stop responding as usual and i decieded to restart it pushed CTRL+AL+DEL the systems showed me killing processes and it stopped responding with ubuntu splash screen... where dots are blinking. So I used power button to shut down pc... then appeared this screen which I attached in the first

---

### Post by farus.pri.ee on 2011-10-14
new dates...

I have knoppix disk.. adriane and knoppix... sooo... knoppix shell give me chance to mount this logical hard disk and I can see al file structure and can copu it under the shell.... buuut graphical interface gives me error... 
WHY????
what is it?
I did fsck it gives me many errors...it fixed some.. but main os still did not load...

Is it possible to copy some information from live cd ubuntu to root os partition?? but how to mount this partition under the ubuntu?

---

