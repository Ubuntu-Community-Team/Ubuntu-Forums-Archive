---
title: "win 7 just shut down during loading !!!!!  help"
date: 2010-02-17
forum: General Help
---

### Post by the black on 2010-02-17
I am new in ubuntu but it looks nice
but there is a small problem
I have installed the ubuntu 9.10
and the pc already have 2 win 7 OS and 1 win xp
I installed the ubuntu from win xp
every thing go just fine
but in win 7 boat loader it detects the 2 win 7 OS , previous windows ( the xp )and the ubuntu which fails to load from win7 boot loader ( the first problem ) but it is present also in win xp boat loader so when choosing older windows the win xp bootloader let me choose between windows xp and ubuntu which works fine when choosing it the ubuntu bootloader appears with ubuntu\ubuntu safe mode\win7 bootloader   etc
the second problems that choosing win 7 after restarting the pc from ubuntu fail to open  it begin loading with the windows logo and then just shutdown the whole pc as if i have unplugged it !!!!!!!!!  the only way to let it open is to choose older windows>>> ubuntu >>>> ubuntu bootloader >>> where there is win 7 bootloader option  it returns me again to win 7 bootloader but this time the windows load complete ( mostly but may shut down also !!!! )
any help
?????

thanks

---

### Post by the black on 2010-02-18
any help please
??

---

### Post by Jackzor on 2010-02-18
> **the black said:**
> I am new in ubuntu but it looks nice
but there is a small problem
I have installed the ubuntu 9.10
and the pc already have 2 win 7 OS and 1 win xp
I installed the ubuntu from win xp
every thing go just fine
but in win 7 boat loader it detects the 2 win 7 OS , previous windows ( the xp )and the ubuntu which fails to load from win7 boot loader ( the first problem ) but it is present also in win xp boat loader so when choosing older windows the win xp bootloader let me choose between windows xp and ubuntu which works fine when choosing it the ubuntu bootloader appears with ubuntu\ubuntu safe mode\win7 bootloader   etc
the second problems that choosing win 7 after restarting the pc from ubuntu fail to open  it begin loading with the windows logo and then just shutdown the whole pc as if i have unplugged it !!!!!!!!!  the only way to let it open is to choose older windows>>> ubuntu >>>> ubuntu bootloader >>> where there is win 7 bootloader option  it returns me again to win 7 bootloader but this time the windows load complete ( mostly but may shut down also !!!! )
any help
?????

thanks

It would help if I could read this without going crosseye'd. How about retyping it so I can read it better? Then maybe I'll understand what you are talking about

---

### Post by the black on 2010-02-18
ok
1 minute please

---

### Post by the black on 2010-02-18
> **the black said:**
> [SIZE="6"]I am new in ubuntu but it looks nice
but there is a small problem
I have installed the ubuntu 9.10
and [COLOR="Red"]the pc already have 2 win 7 OS and 1 win xp[/COLOR]
I installed the ubuntu from win xp
every thing go just fine
[COLOR="red"]but in win 7 boat loader it detects the 2 win 7 OS , previous windows ( the xp )and the ubuntu which fails to load from win7 boot loader [/COLOR]( the first problem )

 but it is present also in win xp boat loader so when choosing older windows [COLOR="red"]the win xp bootloader let me choose between windows xp and ubuntu which works fine[/COLOR]
 when choosing it the ubuntu bootloader appears with ubuntu\ubuntu safe mode\win7 bootloader   etc

the second problems that choosing win 7 after restarting the pc from ubuntu fails to open  [COLOR="red"]it begin loading with the windows logo and then just shutdown the whole pc as if i have unplugged it !!!!!!!!![/COLOR]

 [COLOR="red"] the only way to let it open is to choose older windows>>> ubuntu >>>> ubuntu bootloader >>> where there is win 7 bootloader option  it returns me again to win 7 bootloader but this time the windows load complete ( mostly but may shut down also !!!! )[/COLOR]
any help
?????

thanks[/SIZE]

here is the complain
thanks in advance

---

### Post by tom4everitt on 2010-02-18
Do I understand you correctly:

You had three (!) windows systems running. Then you installed ubuntu (wubi) from one of the systems. Now you have trouble booting some of the windows systems?

Your boot loader description needs a bit improvement, I'm afraid. Do you have a separate boot loader with multiple options for each OS?

---

### Post by the black on 2010-02-18
[SIZE="6"]yup
three :D
and I instaled ubuntu from win xp
yes the problem now is in loading win 7 after restarting from ubuntu
i know 3 win is too much
but this problem did not appear except after ubuntu install
I used to have these same 3 windows with mandriva and this problem doesn,t appear 
it only begins to appear after ubuntu install
[/SIZE]

---

### Post by tom4everitt on 2010-02-18
You may choose a normal font ;) 

Sounds a bit odd...

I think this is the case:
Your Mandriva was installed as a normal OS, your ubuntu is installed as a wubi one. I think this is the reason it doesn't work. 

Install your ubuntu as a normal OS on its own partition, and remove the wubi one. It will, if nothing else, be a cleaner setup less prone to errors.

---

### Post by the black on 2010-02-18
[SIZE="4"]but i have uninstaled the mandriva 2 days ago
but the problem is still present
the odd thing that when I choose ubuntu from win xp bootloader
many options appear
when i choose from them win 7 boot
it returns me again to win 7 bootloader screen
but this time it works
too odd
!!!!![/SIZE]

---

### Post by the black on 2010-02-18
[SIZE="5"]by the way ubuntu is working from win xp bootloader
but ubuntu option is not working in win 7 bootloader
really this is not a major problem now
but the annoying thing is that win 7 autoshutdown !!
any ideas
?
thanks for your concern
[/SIZE]

---

### Post by tom4everitt on 2010-02-18
I'm sorry, but I don't know what might be causing that. I do know that windows is not designed for being on anything but the first partition on the first hard drive. Hence several windows systems like this will be prone to error. So I think its actually more luck when it works, rather than necessarily something wrong when it doesn't :)

So the recommended way to do a dual boot is to install windows to the first partition of the hard drive, and ubuntu (and other) to the rest of the partitions. Several linux systems is generally not a problem.

---

### Post by the black on 2010-02-19
thanks very much for help
:P

---

### Post by uRock on 2010-02-19
Back up data and reinstall Windows. Even though the Windows 7 will not boot, you should be able to mount its partition with one of the other Windows or with the Ubuntu LiveCD and copy the needed data from it. You should use a VirtualBox for testing OSes that way it doesn't mess with the bootloaders.

---

