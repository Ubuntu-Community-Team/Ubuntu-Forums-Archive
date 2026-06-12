---
title: "Several questions about kubuntu,and High CPU Load problem"
date: 2009-09-17
forum: General Help
---

### Post by GrfyGrumpyBear on 2009-09-17
Hi,

Just moved to kubuntu from windows,and i have some problems and questions to solve.

I use kubuntu 9.04 with kde,and the problem is that no matter what i do,i'm getting 100% CPU Load.
If i move a window the cpu load goes 100%,if i press a link on the browser,the cpu load goes 100% again.

I use screenlets and i have a gadget that shows the cpu load and how much memory is in use,and i NEVER have seen cpu load lower than 60%.

I have an Celeron 1.7ghz on an old laptop,but on windows i have 100% load only if i run really heavy applications,so this is problem for me.

There is any probably solution? Is this a bug or something?

Ok let's go to the questions now...

My downloads goes to "Desktop" but i don't see them on my desktop,i can only find them on the home/deskop folder,how can i fix that? I deleted a panel of the desktop,like a square with gray transparent background,this is the problem?

Also if i watch a video on youtube,the screen stucks,there is any alternative flash plugin,can i do something about that? On windows it's fine.

And the final question:

I downloaded from kde-look.org some "Native kde 4 window decorators" and i don't know how can i install them.I searched for answer and i found dozens solutions like some commands,but i'ts just a mess,nothing worked.

Thanks,i hope that i'll find solution to my problems/questions here. :)

---

### Post by undecim on 2009-09-17
> **GrfyGrumpyBear said:**
> Hi,

I use kubuntu 9.04 with kde,and the problem is that no matter what i do,i'm getting 100% CPU Load.
If i move a window the cpu load goes 100%,if i press a link on the browser,the cpu load goes 100% again.

I use screenlets and i have a gadget that shows the cpu load and how much memory is in use,and i NEVER have seen cpu load lower than 60%.

Use the system monitor (or the "top" command from a terminal) to see what app(s) is/are using the CPU. It could also be that you need to install proprietary graphics drivers because you are leaving the CPU to do the work that your graphics card doesn't have the drivers for. (Sorry, but haven't used Kubuntu much, so I'm not sure where to find this via GUI. Try using KDE's search from the menu or going to the KDE control panel. You can also look up what the package name for your drivers are (based your graphics card as listed by running "lspci | grep vga" from Konsole) and run "sudo apt-get install [package name]" in Konsole where [package name]" is the name of the package/)

[/quote]> **GrfyGrumpyBear said:**
> 
My downloads goes to "Desktop" but i don't see them on my desktop,i can only find them on the home/deskop folder,how can i fix that? I deleted a panel of the desktop,like a square with gray transparent background,this is the problem?


I believe this is the "Folder View" widget or similar name. (again, haven't used Kubuntu/KDE much recently). Add this to your desktop and you may need to change the settings on the widget (the wrench button next to it) to get it to display the folder you want

> **GrfyGrumpyBear said:**
> 
Also if i watch a video on youtube,the screen stucks,there is any alternative flash plugin,can i do something about that? On windows it's fine.


Install kubuntu-restricted-extras. Either through the add/remove programs, or by running "sudo apt-get install kubuntu-restricted-extras" in Konsole. This will install flash player (I believe the default is swfdec? I could be wrong)

Although this could also be because of a graphics driver issue (if installing the driver fixed your CPU usage issue, check this one again)

> **GrfyGrumpyBear said:**
> 
  I downloaded from kde-look.org some "Native kde 4 window decorators" and i don't know how can i install them.I searched for answer and i found dozens solutions like some commands,but i'ts just a mess,nothing worked.


This one, I just don't know. I'll take a look at Google and report back here if I figure it out.

Though post reminds me... I've been meaning to install KDE 4.3, because i've heard some pretty good things about it, and I would like to be able to better help Kubuntu users.

---

### Post by GrfyGrumpyBear on 2009-09-17
Thanks for your reply.:)

I fixed the desktop problem,i must keep running the "Folder View" widget.

About the cpu load now... You won't believe me but on the system monitor i don't see any application which uses 100% the cpu,the higher load is from the Xorg,it's allways about 30%.

My graphics card is an SiS 661fx,the drivers are installed but it doesn't have 3d acceleration on linux drivers,maybe this is the problem for the high cpu load and the youtube problem,i don't know but i will try to change the gpu's drivers with other driver package to see what's happens,also the adobe flash player has been installed with the ubuntu extras.


Again,thanks for your reply.):P

---

### Post by GrfyGrumpyBear on 2009-09-18
I have installed the xserver-xorg-video-sis package,i can't find any other drivers for the gpu,what's the alternatives?

Heeeeeeeelp i can't see youtube videooooosssss,it really bother me hard. ](*,)

---

