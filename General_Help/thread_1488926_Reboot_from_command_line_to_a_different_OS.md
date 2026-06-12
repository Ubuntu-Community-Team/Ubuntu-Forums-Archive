---
title: "Reboot from command line to a different OS"
date: 2010-05-20
forum: General Help
---

### Post by anuvnu387 on 2010-05-20
I would like to know if I can reboot my headless ubuntu machine from command line to a different OS on the same disk. To clarify, I want to do this without having to manually choose in GRUB. 

OS1: Ubuntu on sda1- it is the default OS in an always on server. 
OS2: Fedora on sda2 - have to login into this once in a while.

There are no monitors attached with the machine. So I cannot manually scroll through grub and choose Fedora. I want to know if there is a command I can issue remotely to the Ubuntu server to reboot to Fedora. 

Thanks for the time and help!

---

### Post by bodhi.zazen on 2010-05-20
You would configure grub, and change the default OS with sed.

```
sudo sed -i -e 's_set default=0_set default=1_g' /boot/grub/grub.cfg
sudo reboot
```

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by anuvnu387 on 2010-05-20
Thanks for the response. I am sorry, what does your code do actually? 

I know I can change the default OS in /etc/default/grub (Lucid Lynx), update grub and restart to automatically boot into OS2 (Fedora). 

But i want to know if there is a way to do it without playing with grub. For example, the following command reboots my ubuntu machine back to Ubuntu:

sudo shutdown -r now

Is there any argument that I can pass on along with the shutdown command to make it boot to a different OS?

I would like to reboot to OS2 (Fedora) only on need basis and I would prefer not to modify GRUB all the time.

Thank you!

---

### Post by bodhi.zazen on 2010-05-20
No, you have to modify grub.cfg (this file is where the default OS is set). The sed command sets the default os ( 0 vs 1) without editing grub config files and running update-grub.

---

### Post by anuvnu387 on 2010-05-20
Thank You bodhi. I will try that. 

So I edit grub.cfg and reboot. The system boots to fedora. After I am done with fedora and want to reboot into my Ubuntu which is what i use 99% of the time, I edit Ubuntu's grub.cfg from Fedora and reboot the computer. Am I correct?

Sorry. I am not an expert (only been using Ubuntu casually for a year now). Thanks for the patience.

---

### Post by bodhi.zazen on 2010-05-20
> **anuvnu387 said:**
> Thank You bodhi. I will try that. 

So I edit grub.cfg and reboot. The system boots to fedora. After I am done with fedora and want to reboot into my Ubuntu which is what i use 99% of the time, I edit Ubuntu's grub.cfg from Fedora and reboot the computer. Am I correct?

Sorry. I am not an expert (only been using Ubuntu casually for a year now). Thanks for the patience.

Yes. Mount your Ubuntu partition and run a similar sed command.

Of course you will need to watch the numbers, the first OS listed in your menu is "0" , the second is "1".

So the number of the default OS may change, depending on how many kernels you have.

Personally, for what you want, I would write a custom grub.cfg, but take care if you do not have physical access, a (syntax) mistake = system will not boot. Not a big deal if you have physical access and can fix, but from remove, be careful.

If you use 99 % Ubuntu and rarely use Fedora and do not have easy access, quit while you are ahead =)

---

### Post by Axanon on 2010-05-20
Do not edit grub.cfg. If you read the Grub2 documentation it specifically tells you DO NOT EDIT GRUB.CFG. Read the documentation and figure out how to do this using /etc/grub/default instead.

---

### Post by Serpher on 2010-05-20
It means if you edit it and mess it up you can't boot. If you do what he's saying it'll work perfectly. I personally comment out all the boot options I don't use leaving me an uncluttered GRUB menu and nothing bad has come out of it.

---

### Post by bodhi.zazen on 2010-05-20
Why not ? It will not break anything.

The reason they advise that is grub.cfg will be automatically overwritten, so customizations will be lost.

In this case, the customizations are trivial, and so it really does not matter. Certainly much much faster then editing a system file and running "sudo update-grub".

Sure if you make a typo you will have a problem, same as with any other method or any other config file.

---

### Post by anuvnu387 on 2010-05-20
Thanks everyone. I will try it out when I reach home. Based on the replies I assuming there is no command like:

sudo shutdown -r now BootOS2 or something like this just for example.

from Ubuntu command line to boot fedora during reboot. 

If not, then I will probably maintain a custom grub.cfg and write a bash script to swap grub.cfg and reboot the machine.

Thanks once again guys.

---

### Post by -kg- on 2010-05-20
> Based on the replies I assuming there is no command like:

sudo shutdown -r now BootOS2 or something like this just for example.

You are correct.  Each time the computer (re)boots, the first thing BIOS does after posting operations is look for the bootloader section in the MBR.  Only by modifying that can you reboot into another OS, as you are wanting to do.

---

### Post by Serpher on 2010-05-20
You could make add an alias so when you type in a custom command like 'bootfedora'. Just add the following line to .bashrc located in your home folder (Just open up a new terminal window and run 'gedit .bashrc')

```
alias bootfedora="sudo sed -i -e 's_set default=0_set default=1_g' /boot/grub/grub.cfg"
```

---

### Post by anuvnu387 on 2010-05-20
Yes. I was thinking of that as well. Or I could put the following into a bash script say "bootfedora.sh" 

#!/bin/bash
sudo sed -i -e 's_set default=0_set default=1_g' /boot/grub/grub.cfg
sudo shutdown -r now

and just execute the script. 

Thanks everyone for your suggestions. I like how the linux community helps out the new people like me. I should say I have discovered a new ocean for me to explore when I stepped into linux late 2008.

---

### Post by Serpher on 2010-05-20
Or you could have teh alias like this...sorry messed up

```
alias bootfedora="sudo sed -i -e 's_set default=0_set default=1_g' /boot/grub/grub.cfg && shutdown -r 0"
```

---

### Post by anuvnu387 on 2010-05-20
Hmm...this is even better. I did not know about the the AND (&&). Great! 

Thanks

---

### Post by ryan858 on 2010-05-20
'&&' is basically an *if* type thing... It checks that the previous command returned 0, before moving on to the next one, or anything after it. If the command returns non-zero, then && cuts the chain there and exits without executing the rest of the commands. You could also use ';' to make a chain on a single line, but it generally safer to use &&, unless you want the rest of the chain to be executed regardless of what happened to the previous command.

So for example, you could do:
```

cd ~ &&
mkdir test &&
touch test1 &&
echo 'This is a test' >> test1 &&
echo 'Success'

```or 
```
cd ~ && mkdir test && touch test1 && echo 'This is a test' >> test1 && echo 'Success'
```and || does the opposite, only executing the rest of the chain if the command returns non-zero, so you could:
```

mkdir test || echo 'An error occurred'

```

Generally you can do stuff like
```
cd ~ ; ls -a 
``` pretty safely though.

---

### Post by anuvnu387 on 2010-05-20
Actually I could use ";" for one of my applications. I have a bash script for backing up directories:

```
rdiff-backup directory1 directory2
rdiff-backup directory3 directory4
sudo shutdown -r now
```

 Can I combine the commands to one line with ";" so that even if one backup encounters error the script can move forward to backing up the next directory? Something like this:

```
rdiff-backup directory1 directory2 ; rdiff-backup directory3 directory4 ; sudo shutdown -r now
```

---

### Post by ryan858 on 2010-05-20
Yep. You can even do both at the same time, by putting one in the background. Like so:
```

rdiff-backup directory1 directory2 & rdiff-backup directory3 directory4 ; sudo shutdown -r now

```This is what they mean when they say "Linux is a true multitasking OS" (or UNIX)

But they won't be in order using '&'. So don't use it when things need to be in specific order. In fact, more than likely the second command will finish before the first, because it has higher process priority, unless you put it in the background as well, but that'd be slower.

---

### Post by drs305 on 2010-05-20
There is a very easy way to do this if you have Grub 1.98, which ships with Lucid.

Change /etc/default/grub:
> GRUB_DEFAULT=saved
Update grub:
```
sudo update-grub
```

Now use the command
 ```
sudo grub-reboot X
```
with X being either the menuentry number (starting with 0 for the first menuentry), or the exact title (the title within the quotes of grub.cfg)

Ubuntu will boot once from the specified entry above, and then revert to the previously saved OS.

See "man grub-reboot". 

You may also be interested in "grub-set-default".

---

### Post by ryan858 on 2010-05-20
Nice!

---

### Post by anuvnu387 on 2010-05-21
Wow!!! that is neat. One small thread so many new things learned.

---

### Post by anuvnu387 on 2010-05-21
> **ryan858 said:**
> Yep. You can even do both at the same time, by putting one in the background. Like so:
```

rdiff-backup directory1 directory2 & rdiff-backup directory3 directory4 ; sudo shutdown -r now

```This is what they mean when they say "Linux is a true multitasking OS" (or UNIX)

But they won't be in order using '&'. So don't use it when things need to be in specific order. In fact, more than likely the second command will finish before the first, because it has higher process priority, unless you put it in the background as well, but that'd be slower.
One question how to run something in the background?

---

### Post by bodhi.zazen on 2010-05-21
> **anuvnu387 said:**
> One question how to run something in the background?

The & puts the process in the BG.

See: [http://www.museum.state.il.us/ismdepts/library/linuxguides/abs-guide/x5514.html](http://www.museum.state.il.us/ismdepts/library/linuxguides/abs-guide/x5514.html)

---

### Post by dcstar on 2010-05-22
> **drs305 said:**
> There is a very easy way to do this if you have Grub 1.98, which ships with Lucid.

Change /etc/default/grub:

```
GRUB_DEFAULT=saved
``` 

Update grub:
```
sudo update-grub
```
........

You also have to add this to make saved entries work:

```
GRUB_SAVEDEFAULT=true
```

---

### Post by ryan858 on 2010-05-22
> **bodhi.zazen said:**
> The & puts the process in the BG.

See: [http://www.museum.state.il.us/ismdepts/library/linuxguides/abs-guide/x5514.html](http://www.museum.state.il.us/ismdepts/library/linuxguides/abs-guide/x5514.html)

Yes, and not to be confused with '&&'.

---

### Post by drs305 on 2010-05-22
> **dcstar said:**
> You also have to add this to make saved entries work:

```
GRUB_SAVEDEFAULT=true
```

The GRUB_SAVEDEFAULT line is actually a different 'animal'. It allows you to always boot the last booted entry, which is a bit different than how GRUB_DEFAULT=saved combined with grub-set-default/grub-reboot work.

Since these commands appear not to be well-known I will add an explanation of them in my Grub Basics thread when I get the time.

---

