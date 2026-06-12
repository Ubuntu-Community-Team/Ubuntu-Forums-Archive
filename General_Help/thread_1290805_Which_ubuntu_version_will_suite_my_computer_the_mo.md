---
title: "Which ubuntu version will suite my computer the most?"
date: 2009-10-13
forum: General Help
---

### Post by krine11 on 2009-10-13
Hi there, Well I have a old machine which i now need, It has the following spec's :

2 GB of ram
500 GB of hard drive space
ati raedon xpress 200 (64 MB and can not find any driver for 9.04)
1.80 GHz single core processor.

Currentlly i am running Kubuntu 9.04, i like it but not sure if it will suite i like it though. Are there any other ubuntu versions you people might recommend which is also very less laggish type of issues (I had some lag with gnome) so please can you help me out here? 






-Thank-You so much!

---

### Post by renkinjutsu on 2009-10-13
What do you meaaan **you people**?! .. HUH?!

i'm kidding

anyway, there a couple of lightweight Ubuntu derivatives
one being **Xubuntu**, which is very similar to GNOME

Then there's **Lubuntu**, it uses LXDE and openbox as the window manager i think... VERY lightweight.. even lighter than Xubuntu

Is there an icebuntu? .. does anyone know?

---

### Post by QIII on 2009-10-13
Unfortunatley, you won't probably find a driver for Jaunty but the open source driver.

ATI has relegated your card to "legacy" and the old driver will not operate with the version of X that ships with Jaunty.

---

### Post by Lukios on 2009-10-14
You should be able to run gnome just fine, however if you find that its a bit slow you have a few alternatives. You can either use xubuntu or lubuntu (when it comes out) or you can install from mini.iso and install only gnome-core and what ever packages you like and or replace nautilus and metacity with pcmanfm and openbox respectively.

---

### Post by krine11 on 2009-10-14
So now i will never be able to use my driver again with any ubuntu versions + future releases?

---

### Post by tuxxy on 2009-10-14
Ubuntu or Xubuntu

---

### Post by coldReactive on 2009-10-14
Crunchbang or Lubuntu (When it comes out.)

---

### Post by abyrne on 2009-10-14
You could also try CrunchBang Linux. It's based on Ubuntu but it's really lightweight and will probably run really well on your specs.

---

### Post by zkriesse on 2009-10-14
Xubuntu or LXDE

---

### Post by krine11 on 2009-10-14
Well, I hear alot of response on Xubuntu.

Well, If i do use Xubuntu will i still be able to activate my video card driver? Or can i just download the video driver with Kubuntu 9.04? Please respond because this is like my last choice and i really love linux and can not afford to buy those good computers or update mines thats why i choose linux insted of windows.....please help me out here

---

### Post by undecim on 2009-10-14
Since your card was abandoned by ATI, you can't install ATI's driver. Try something less graphically intensitve like Crunchbang or Lubuntu.

If you are feeling adventerous, you could also try Fluxbox (install it in your current installation because I don't know of an Ubuntu variant that uses it). It requires more work to set up, but it is the most lightweight DE I know of. The entier DE (window manager, panel, etc.) is all one lightweight program.

The only downfall to Fluxbox is that there is very little graphical configuration available. You will have to read a lot of documentation and edit some text files to customize it.

---

### Post by coldReactive on 2009-10-14
> **undecim said:**
> Since your card was abandoned by ATI, you can't install ATI's driver. Try something less graphically intensitve like Crunchbang or Lubuntu.

If you are feeling adventerous, you could also try Fluxbox (install it in your current installation because I don't know of an Ubuntu variant that uses it). It requires more work to set up, but it is the most lightweight DE I know of. The entier DE (window manager, panel, etc.) is all one lightweight program.

The only downfall to Fluxbox is that there is very little graphical configuration available. You will have to read a lot of documentation and edit some text files to customize it.

Aren't fluxbox and openbox basically the same when it comes to usage/resources.

---

### Post by jocko on 2009-10-15
> **krine11 said:**
> Hi there, Well I have a old machine which i now need, It has the following spec's :

2 GB of ram
500 GB of hard drive space
ati raedon xpress 200 (64 MB and can not find any driver for 9.04)
1.80 GHz single core processor.

Currentlly i am running Kubuntu 9.04, i like it but not sure if it will suite i like it though. Are there any other ubuntu versions you people might recommend which is also very less laggish type of issues (I had some lag with gnome) so please can you help me out here?
That machine should run gnome  fine without any lag. But the default settings for the open source radeon driver does have some serious lag issues, that you will never be able to fix by changing desktop environment.
I managed to fix this on my machine (similar to your specs, but a radeon 9600 pro) by making a xorg.conf with some tweaks. See [this post]("http://ubuntuforums.org/showpost.php?p=8102590&postcount=6") if you're interested.

---

### Post by krine11 on 2009-10-16
Allright, I will try this lubox as listed. But just a question cant i install the driver with via wine or something?

---

### Post by coldReactive on 2009-10-16
> **krine11 said:**
> Allright, I will try this lubox as listed. But just a question cant i install the driver with via wine or something?

Wine isn't supposed to install drivers. That's what ReactOS is for.

---

### Post by krine11 on 2009-10-16
Well, Ok. Well what do you recommend lastlly that is UBUNTU RELATED or some other linux i guess that has everything installed like ubuntu does? And will work with my driver please respond lastlly this is a great support team :) Oh and last question :

If i install xubuntu will xubuuntu recognise my driver then?

---

### Post by coldReactive on 2009-10-16
> **krine11 said:**
> Well, Ok. Well what do you recommend lastlly that is UBUNTU RELATED or some other linux i guess that has everything installed like ubuntu does? And will work with my driver please respond lastlly this is a great support team :) Oh and last question :

If i install xubuntu will xubuuntu recognise my driver then?

This might help: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Or this: [http://ubuntuforums.org/showthread.php?t=1212509](http://ubuntuforums.org/showthread.php?t=1212509)

---

### Post by mike555 on 2009-10-16
another option might be "Moon OS" it's based on Ubuntu but lighter ..........

---

### Post by cariboo on 2009-10-16
If the manufacturer doesn't support you graphics adapter, you will have to use the open source driver for it. I have an unsupported Ati graphics adapter in my laptop, running Jaunty and using the open source driver, I can use compiz with zero problems.

---

### Post by krine11 on 2010-02-27
Open Source video card drivers, May i know how i can download or install this?

---

