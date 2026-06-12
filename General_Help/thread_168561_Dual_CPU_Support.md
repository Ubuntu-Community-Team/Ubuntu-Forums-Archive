---
title: "Dual CPU Support?"
date: 2006-04-30
forum: General Help
---

### Post by Damogill on 2006-04-30
Hey all,

Firstly like to say hello, I am fairly new to the GNU world but so far so good. I was recommended Ubuntu by a fellow Linux friend and I have been nothing but impressed so far.

I first installed on VMWare in windows on my laptop but am now installing it on a desktop machine, my query is a simple one. Does Ubuntu support Dual CPU? I am sure it does but to be honest as im new to this I dont know how to even check lol.

I am running Ubuntu 5.1 on a dual PIII 750Mhz system.

Any help on this would be greatly appreciated :)

---

### Post by DrBair on 2006-04-30
Linux can run on a LOT more than two processors, Ubuntu is no different.  If you use Breezy (the current stable release) you will need to install a SMP kernel (a painless task). If you are using Dapper (the current development release) the kernels are all SMP capable, however you may wish to install a 686 kernel to take fuller advantage of your processors architecture.

---

### Post by Ramses de Norre on 2006-04-30
Oh yes it does ;) Just run ```
sudo apt-get install linux-i686-smp
``` in terminal (applications > system tools > terminal).
And choose the smp kernel in grub on reboot (will be set to default).

---

### Post by JohanSwe on 2006-05-20
[QUOTE=Ramses de Norre]Oh yes it does ;) Just run ```
sudo apt-get install linux-i686-smp
``` in terminal (applications > system tools > terminal).
And choose the smp kernel in grub on reboot (will be set to default).[/QUOTE]
What smp package do I need to install for Dual MP 2800+ processors?
And is there something more I need to do?

---

### Post by Ramses de Norre on 2006-05-20
Is that AMD? If so the k7-smp kernel.

---

### Post by JohanSwe on 2006-05-20
[QUOTE=Ramses de Norre]Is that AMD? If so the k7-smp kernel.[/QUOTE]
Actually there's a guy at the Swedish Ubuntu forum that I'm trying to help, and I would like to learn more about this myself as well.

I guess it's a AMD processor because of the name, 2800+. He have not confirmed that yet.

How can we find out about the kernel?

And also, how can I found out about the speed of the processor in Ubuntu?

---

### Post by Ramses de Norre on 2006-05-20
I made my guess that it's amd for the same reason;)

What do you mean finding out about the kernel? The k7 kernels are optimalized for amd, so it may run faster with a k7 (though the difference may be very small).

And by speed, do you mean the clock frequency? If so: less /proc/cpuinfo will show you a lot of information, and one of the lines shows the frequency.

---

### Post by JohanSwe on 2006-05-21
> What do you mean finding out about the kernel?
Never mind, it was I that couldn't read. My mistake..

I guess my friend will manage to get both of the processors running now with that package. Thank you for your help :)

---

### Post by Damogill on 2006-05-21
Hey, back again been away for a bit.

I did give the code below a go but it didnt work.. sorry I didnt get any log msgs or anything to help anyone else.

I ran into other issue with getting the NIC to boot up properly. My dual CPU system has been such a pain ive ended up opting to run ubuntu from another single CPU system instead.

[QUOTE=Ramses de Norre]Oh yes it does ;) Just run ```
sudo apt-get install linux-i686-smp
``` in terminal (applications > system tools > terminal).
And choose the smp kernel in grub on reboot (will be set to default).[/QUOTE]

Your help is mucho appreciated. Cheers :D

---

### Post by JohanSwe on 2006-05-22
[QUOTE=JohanSwe]Never mind, it was I that couldn't read. My mistake..

I guess my friend will manage to get both of the processors running now with that package. Thank you for your help :)[/QUOTE]

Now both of the processors are running :)

---

### Post by FrankVdb on 2006-10-18
Could you tell me for which applications Ubuntu is using both processors? I have a workstation with a double 1.6Mhz Xeon setup currently running W2K, but the only software optimised for dual CPU processing is Adobe's... This means that under Windows, a CPU-intensive programme will only use one processor (except for Adobe software), the other processor being available for other threads but not for the most important one, which is a shame. Evidently, it's for the labour-intensive stuff that I'd like to combine the power of my Xeons... 

Therefore, since Windows is not using my processors efficiently, I was wondering if Ubuntu would to a better job. I'am willing to try, especially because my W2K system is fairly outdated...

---

