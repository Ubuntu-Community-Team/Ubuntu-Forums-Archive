---
title: "screen shuts down after booting..."
date: 2012-03-14
forum: General Help
---

### Post by karkra on 2012-03-14
Hi everyone , nice forum ;)

I just installed ubuntu 11.10 and after that it booted normally and loged in . After that i installed and activated the video driver , downloaded studio packages and rebooted . 

I have a triple boot ( win7, ubuntu 11.10 and debian 6 ) i choose the ubuntu but after some seconds the monitor shuts down and says that its out of range .

This is not the first time i've got this problem , before installing ubuntu 11.10 i tried to install ubuntu studio 11.10 and i had the same problem ( actually it never loged in ... ) .
I had a lot of errors during the installation when i was choosing to mark for instalation extra softwere so i thought that installation was in a mess and removed it , to try installing the default 11.10 version and put the studio packages after installing the base system . 

Is the problem caused by studio packages ? Or just the driver doesnt work ? How can i change the driver to the default generic driver via console (safe boot etc...)  ? 

thank you !

ps : sorry for my bad english !

---

### Post by karkra on 2012-03-14
my computer : amd athlon x2 64 6400 black edition
                      3GB Ram 
                      ECS Elitegroup mobo with ATI onboard graphics card ...


any help ? :(

---

### Post by 2F4U on 2012-03-14
Here is some info on how to remove the fglrx driver:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

If it worked before without problems, chances are that the fglrx driver is the root of the problem.

---

