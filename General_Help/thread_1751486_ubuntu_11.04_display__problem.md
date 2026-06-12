---
title: "ubuntu 11.04 display  problem"
date: 2011-05-06
forum: General Help
---

### Post by gau1992 on 2011-05-06
hello, i am using acer aspire 4736z model,
today i upgarted ubuntu 10.10 to 11.04.
but in 11.04 it does not showing my display,
i tried with nomodeset to search additional drivers, but it is not showing any additional drivers, plz help me about this problem,
thanking you...

---

### Post by flipper T on 2011-05-06
you "upgraded" rather than do a fresh install ?

this may be the problem

i would boot from a live cd and see if problem persists

if live cd is ok, i would back up important files and do a fresh install

---

### Post by BertN45 on 2011-05-06
There are some known problems with some of the Intel integrated video chip sets and Unity. Your PC has an Intel video chipset. I would try the live cd and if the problem persists you have three choices:
- I did see an update of the Intel driver 2 days ago, if you can get in the command line try updating your system from the command line.
- go back to Ubuntu 10.xx
- use Xubuntu 11.04, that I can recommend since it has some great improvements. From here you could re-install and retry the Ubuntu Unity Desktop.

I had the same problem on my desktop and I am using Xubuntu now and I noticed that some of the small glitches in the windows borders have been solved by the new driver.

---

### Post by Blasphemist on 2011-05-06
I found this solution in a post from a month ago.

> I m using acer 4736z and was facing the same problems
after changing the kernel parameters my problem was solved
try adding the line
acpi_osi=linux
and the brightness goes back to normal 100% without any controls

It's post 9 in this thread.

[http://ubuntuforums.org/showthread.php?p=10643420](http://ubuntuforums.org/showthread.php?p=10643420)

It sounds like from other threads that backlight isn't working without this.

---

### Post by gau1992 on 2011-05-07
dear blasphemist, can you tell me how would i change kernal parameters???

---

### Post by Blasphemist on 2011-05-07
I'm going to paste in how to do it for a session to test which change works (start with what I already recommended). The link to another thread is the source of this instruction. You should look at the thread prior to starting.

> How to temporarily set kernel boot options on an installed OS (not wubi)

To set kernel boot options, you must edit your grub configuration. You can do this temporarily for a single boot by entering the grub menu. If you do not get to see the grub boot menu after the bios automatically, you may have to press SHIFT key after the bios logo to get in to grub:



Select the default ubuntu kernel (usually the top one), and rather than pressing enter, press E to edit.

Press DOWN ARROW until you get to the line that starts with

Code:
linux /boot
and press END keys to position your cursor at the end of the that line usually ending with “quiet splash”. 

Now you can type in additional kernel options like nomodeset (please dont make the same typing error I made for this screenshot  ):

[IMG]http://img26.imageshack.us/img26/3509/dgfdgrunningoraclevmvir.png[/IMG]

press control+X to boot the modified grub entry.

Important: setting boot options this way only applies to a single boot. If you reboot the machine, those settings will be lost, unless you make them permanent (see below)


[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by gau1992 on 2011-05-07
dear blasphemist, thanks alot,
its working..
i am very happy now..:)
your last thread is also very useful,
but i want more knowledge about linux grub, grub commands, kernal parameters, etc.
can u give me any pdf to me?
my e-mail id is [email]gau1992@gmail.com[/email].
once again thanks alot..........

---

### Post by Blasphemist on 2011-05-07
Good, I'm glad that information worked.

Here are some useful links that you can learn from, I am.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)
[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)
[https://help.ubuntu.com/community/CategoryBootAndPartition](https://help.ubuntu.com/community/CategoryBootAndPartition)
[https://help.ubuntu.com/community/GrubHowto?highlight=%28%5CbCategoryBootAndPartition%5Cb%29](https://help.ubuntu.com/community/GrubHowto?highlight=%28%5CbCategoryBootAndPartition%5Cb%29)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

And you'll see links to much more on these pages.

Good Luck and enjoy the journey :D

---

### Post by gau1992 on 2011-05-08
dear blasphemist,
thanks for those links.
i am again in trouble now.
if my laptop battery is 100% charged and i started laptop then that display problem again comes
i have to wait to discharge battery & if i again started then it starts normaly...
can you help me in these problem??

---

### Post by Blasphemist on 2011-05-08
I'm not sure I quite understand the issue you have now but I have done more research. I've seen that quite a few people have the issue with your gma. There are a couple things people have tried and some have had success with the nomodeset only. Did you just add nomodeset or did you also add a change for acpi_osi? If you didn't already try this, I recommend you do now.

> acpi_osi=
This option frequently solves problems with LCD backlight, fan control problems and misreporting of thermal events. What I understand it does (but corrections are welcome), is prevent the kernel from reporting to the bios that its any windows version the bios asks for. By default, the kernel pretends to be all windows versions, that way we are certain the bios executes all the code needed to initialize the hardware. Unfortunately, some bioses contain fixes to fix problems with specific windows versions (notably vista) that arent needed or dont work for other OS's. Setting
Code:
acpi_osi=
(nothing behind the = sign) as boot option makes the kernel not respond to osi queries.

If the bios has provisions for Linux, you can also try
Code:
acpi_osi="Linux"
Or you can try 
Code:
acpi_osi="Windows 2006"
To make the kernel pretend its vista and make the bios execute routines on machines that require them.


---

### Post by gau1992 on 2011-05-10
dear i got solution on that...
i am using hibernate instead of shut down....

---

