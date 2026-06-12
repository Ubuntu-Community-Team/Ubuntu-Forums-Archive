---
title: "Recovery Mode Prompts me for Root Password (I don't have one)"
date: 2006-02-19
forum: General Help
---

### Post by jjn1056 on 2006-02-19
Help!

I installed Postgresql 8.1 yesterday onto my 5.10 Kubuntu desktop which doesn't seem to work very well because it locks up during boot.  I can Cnrl-Alt-Del to reboot it so it's not a total lockup, jus halts at the "starting Postgresql 8.1".

So I figured to start into recovery mode and uninstall the offending package.  However when I try this I get prompted for a Root password, or to hit Control-D to continue.  Since I never created a root password (just always found using sudo worked well enough) I get stuck here.  Hitting control-D just resumes normal boot which get's stuck at the Postgresql entry each time.

I tried to "Control-C" to get around the Postrgresql problem but that doesn't work.

So I am not sure what to do.

Seems other people have a similar problem, getting prompted for a root password in recovery mode, but I can't find a solution.  Supposedly the kernel has been patched to bypass this, but my kernel is not doing that.  Maybe I can edit the grub configuration to point to some other, more failsafe kernel?

I didn't update the kernel, AFAIK, this is a fairly new Kubutu installation, just about 2 weeks old.  I was just playing with it to see if I could get Postgresql 8.1 working, but I guess that was not a good idea :)

I know this question has been asked a lot, but I can't find any good answers to it, so please help me out.  I'd rather not reinstall Kubuntu at this point, since I have already installed a lot of software and got it set up the way I really like it.  Thanks!

--john

---

### Post by jjn1056 on 2006-02-19
Hey,

If you all think this isn't the right forum for this post, I'd appreciate being properly directed.  I'm totally stuck with this problem, my machine can't do anything except sit stuck at the line about postgresql in the startup.

If anyone knows how to edit the startup config from the GRUB console so that I can skip it that could also help me.  There doesn't seem to be so much help for this, but I imagine it must be a common problem, to install something that locks up the boot process.

thanks again!
john

---

### Post by jjn1056 on 2006-02-19
Okay, I'm getting the impression I might need the liveCD so I can get back into my installation.  So I am starting to download that now, although it looks like it's going to take 2 days :(  Anything ideas about what to do with that when I get it would be appreciated.

---

### Post by rattking on 2006-02-19
one way to get back into your system would be to boot from a live cd
mount your root partition somewere then
chroot /mnt/whereever
that will put you into your partition like you had booted it
then youll want to stop Postgresql from starting at next boot
chmod -x /etc/init.d/postgresqlsomething 
should do 
i am not sure of the exact file name but it will be in /etc/init.d
exit
from chroot 
and reboot
hope that helps

---

### Post by jjn1056 on 2006-02-19
I'm going to try that ASA I can download a liveCD.  Does it matter which live CD I use?  Right now it's going to take 23+ hours to download the ubuntu live cd (I have a crappy internet connection in Beijing china) and I would rather not wait.  y guess is that it doesn't matter, as long as I can mount the filesystem and edit the files to stop postgres from loading.

---

### Post by codejunkie on 2006-02-19
[QUOTE=jjn1056]I'm going to try that ASA I can download a liveCD.  Does it matter which live CD I use?  Right now it's going to take 23+ hours to download the ubuntu live cd (I have a crappy internet connection in Beijing china) and I would rather not wait.  y guess is that it doesn't matter, as long as I can mount the filesystem and edit the files to stop postgres from loading.[/QUOTE]
you can use any linux live cd, if you have one handy. you can even do it with your ubuntu install cd, but if you use your ubuntu install cd it is command line only so if you feel comfortable with the command give it a whirl just insert your install cd and type rescue as the boot option.

---

### Post by jjn1056 on 2006-02-19
Wow, I didn't know you could start a recovery console from the install disk.  That is a great feature.  I wish it were mentioned in the boot instructions somewhere.  I actually looked for that a few hours ago, but I didn't think to justr try typing 'rescue' and experimented.

I was able to solve the booting problem.  Now I have to figure out how to solve the 'Postgres 8.1 can't start' problem :)

thanks!!

---

