---
title: "Ubuntu not liking my graphics card?"
date: 2011-08-19
forum: General Help
---

### Post by Julian505 on 2011-08-19
I had a PNY *Verto GeForce FX 5200* (*128MB*, *PCI*) graphics card a while back when I had windows XP. I recently decided to switch to Ubuntu but had many problems while doing it. After Ubuntu was done installing, it would say that i need to restart my computer for it the change to take place. Well, all it did was turn my monitor off but the PC stayed on. I restarted it manually and the pc started up but then came to a stop when it was time for the OS to start up. All it did was show a bunch of white boxes and then to a black screen. I found something that i thought would fix the problem called boot repair. I ran the boot repair but it continued to stop at a black screen. The Live-CD version of ubuntu was working fine but the installed version was not! After a few days I came up with the idea that it could be a graphical issue of some sort. I plugged my monitor into the second input on my nvidia card and i saw a purple screen and quick flashes of pictures. Then i decided to disable my nvidia card and put it back on the Intel card that is built into my computer and Ubuntu worked fine!! I thought Ubuntu recommended Nvidia cards?? Why isn't mine working??

Also, if i try to switch back to the Nvidia card, the screen goes black again... I'm very new to Ubuntu. I've used windows and mac for a long time and Ubuntu is an entirely new thing to me so please be easy on a noob :confused:
[B][SIZE=2][SIZE=1]
[/SIZE][/SIZE][/B]

---

### Post by mastablasta on 2011-08-19
> **Julian505 said:**
>  I thought Ubuntu recommended Nvidia cards??

 
you thought wrong. ubuntu doesn't recommend any card, but it works with nvidia, ATI and intel. not with all models at the same quality.
 
[SIZE=3]> [/SIZE]
Why isn't mine working??
[SIZE=3][/SIZE]
 
we have to backup a bit first after you installed the OS did you also install/enable any drivers? if not then this could be the issue here. if this card (i am not nvidia expert here) is a bit older then it's supposed to use opensource drivers. perhaps here is a bug but with those that has a workarround. but it's hard to say just from description. 
 
and finnally even though the screen is blackk that doesn't mean the computer is not working. if you interrupted the install process by turning it off manually you might have corrupted the install.
 
i would suggest a reinstall, but this time do it propperly. enable the drivers if any in the system - admin - hardware drivers menu. and don't turn it off if its working/doing something.
 
if the card is a bit older it might be that the new interface is not supported in that case try Ubutnu 10.04 and see if that one works. it is supported until 2013 (LTS= long term support) and all version in between are like beta versions, which should be used if you have newer hardware and if 10.04 is giving you issues. and also to try something new ;-)

---

### Post by Julian505 on 2011-08-19
> **mastablasta said:**
> 
 
and finnally even though the screen is blackk that doesn't mean the computer is not working. if you interrupted the install process by turning it off manually you might have corrupted the install.
 
i would suggest a reinstall, but this time do it propperly. enable the drivers if any in the system - admin - hardware drivers menu. and don't turn it off if its working/doing something.
 


I did reinstall. I installed two version of Ubuntu. Like i said, it only worked when i disabled my nVidia card. How can I install the nvidia drivers if I can't see anything on the screen when the card is enabled? Right now my computer doesn't know that there's an nvidia card in it unless I put back as the default card in the system's own setup. I'm downloading Kubuntu right now to see if that will work better.

---

### Post by critin on 2011-08-19
[I]<<all it did was turn my monitor off but the PC stayed on.>>

Some installs also turn my monitor off for a few seconds, but it comes back on.  It was disturbing the first time I noticed it. My screen also stays black until I get to the log-on screen.  I have a Dell with a nividia graphic card.  It does come on eventually and works fine.

Just to let you know it isn't just yours.

critin
[/I]

---

### Post by mastablasta on 2011-08-19
> **Julian505 said:**
> I did reinstall. I installed two version of Ubuntu. Like i said, it only worked when i disabled my nVidia card. How can I install the nvidia drivers if I can't see anything on the screen when the card is enabled? Right now my computer doesn't know that there's an nvidia card in it unless I put back as the default card in the system's own setup. I'm downloading Kubuntu right now to see if that will work better.
 
 
upon boot you can add more boot parameters such as nomodeset (and couple of others) and see if that works (to get to the menu i think you need to hold shift key immediatelly on boot i.e. just after BIOS loaded). you should be able to get at least some VGA mode so that you can later enable the propper drivers.
 
edit: here is some more informaiton on various boot options: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
boot commands are also explained. 
 
i would try nomodeset
and maybe vga=771 
to give you some basic VGA mode so oyu can then enable drivers.
 
another option is to use the console you can reach it by hitting crtl+alt+F1 (up to F7 i believe). i don't know the commands here. however if you plann to use the latest driver from nvidia site the install instructions are in the driver file or on the site.
 
sorry i can't be of much help as i am not nvidia user.

---

### Post by realzippy on 2011-08-19
Don't forget your 5200 is EOL.
Maybe you stay with 10.04 LTS where the 96.xx driver should still work.

---

### Post by grahammechanical on 2011-08-19
I think I understand you. Forgive me if I get it wrong. Let me restate a few things for clarity.

1) You have a built-in Intel graphic adapter and Ubuntu works fine on that.

2) You want to put in this Nvidia FX 5200 graphic card. It has two VGA ports (I checked the PNY web site). Ubuntu does not work when this card is set in the BIOS as the default video adapter. Or the Intel adapter is disabled, to be more accurate.

May I suggest?

a) Install Ubuntu with the Intel adapter or if it is already installed, run Ubuntu with the Intel adapter.

b) Use the Ubuntu Software Centre if you have it or Synaptic Package Manager and search for NVidia. Make sure that You have Nvidia Common installed.

You will also see other, older Nvidia drivers that you can install. Choose one. Install it and shutdown and restart this time with the Nvidia card plugged in and the default adapter. 

I do not know if this will work. It is just something that I would mess around with if I had your problem.

Ubuntu running on the Intel adapter will not offer (under Additional drivers) to activate an Nvidia driver. It will not see the need.

One more thing, please confirm that you installed Ubuntu with the Nvidia card connected and the default? If the Ubuntu install process detected an Intel adapter but not a Nvidia adapter then Ubuntu (X-server) may not have a correct configuration.

Regards.

P.S. I have found that it is best to deactivate (uninstall) one Nvidia driver before installing another.

---

### Post by Duncan Williams on 2011-08-19
Don't want to bum you out, but.
I gave up on my nvidia fx5200 video card (128mb).
It would never work correctly in ubuntu.
It was originally a direct-X 9 card (as in windows) and amongst other things the 128mb was never recognised, it worked in software rasterise mode, but very limited (used the vga driver). never worked properly with nvidia drivers.
I replaced it with this card (geforce 6200 - 512mb) (cheap as they come) and installed latest nvidia drivers (280) and it flies...

---

### Post by haresear on 2011-08-19
I have a machine with an Nvidia fx5200 graphics card which has been working fine with Ubuntu 10.04 and Xubuntu 11.04. It uses the proprietary Nvidia hardware drivers version 173, although I think it also worked ok with the free drivers. I didn't experience the problems you are having, so I don't know what to suggest to fix it.

---

### Post by Duncan Williams on 2011-08-19
i would say that you are lucky.  There are a lot of versions of the fx5200 and mine was `winfast'.
There are also a lot of posts re/ ppl having problems with this card and linux. (link on next post)

---

### Post by Duncan Williams on 2011-08-19
[http://ubuntuforums.org/search.php?searchid=82555583](http://ubuntuforums.org/search.php?searchid=82555583)

---

### Post by Julian505 on 2011-09-05
Well I was able to get the video card to work by installing the drivers from the software center but whenever I restart my computer it goes back to the same thing. I find myself having to constantly switch cards just to get the nVidia one to work. Is the computer not saving the options?

---

### Post by 3rdalbum on 2011-09-05
The older Nvidia cards are a bit of a nightmare. Their drivers were written back in the Olden Days when you needed to modify a text configuration file to get your graphics to work. While the drivers have been updated so they continue to work on today's Linux distributions, they haven't actually been made smarter. They still sometimes cause some hassles due to the lack of auto configuration features.

Newer Nvidia cards (7000-series and later) work with the newer drivers, which are fully updated with new features and should do all of the configuration automatically for you.

Unfortunately you're a little bit stuck in the Olden Days, unless you get a newer card. Even something basic like a GTX420 would be fine.

---

### Post by Julian505 on 2011-09-27
Well it doesn't matter now. I'm getting windows 7 soon. Not because of the graphics issue but simply because Ubuntu isn't for me. But it was quite a mission trying to solve these problems and I thank everyone who helped. Bye guys

This thread can be locked if you want

---

