---
title: "how to change splash screen??"
date: 2010-07-19
forum: General Help
---

### Post by owners4life5 on 2010-07-19
how do you change the splash screen? i.ve looked all over the internet but common sense tells me to just ask on here (;

any help is greatly appreciated
thanks

---

### Post by oustiti on 2010-07-20
Have you tried using gnome-splashscreen-manager ?

---

### Post by owners4life5 on 2010-07-20
yeah... no go on it though... unless i.m not doing something right

---

### Post by dcstar on 2010-07-21
> **owners4life5 said:**
> how do you change the splash screen? i.ve looked all over the internet but common sense tells me to just ask on here (;

any help is greatly appreciated
thanks

Install one of the various plymouth themes and then select it with the galternatives package.

---

### Post by JackNocturne on 2010-07-21
> **owners4life5 said:**
> yeah... no go on it though... unless i.m not doing something right


Easiest way to do it is to install **Ubuntu Tweak 0.5.4.1, **it can be found in Ubuntu software Centre as **ubuntu-tweak**. From there you change the splash

[IMG]http://i1021.photobucket.com/albums/af334/JackNocturne/ubuntut.png[/IMG]

---

### Post by owners4life5 on 2010-07-21
> **dcstar said:**
> Install one of the various plymouth themes and then select it with the galternatives package.

how do i do that?

> Easiest way to do it is to install Ubuntu Tweak 0.5.4.1, it can be found in Ubuntu software Centre as ubuntu-tweak. From there you change the splash


that only seems to apply to the login screen, not the splash

---

### Post by RabbitWho on 2010-07-21
Hi, related problem with changing the login screen, that part of ubuntu tweak won't unlock no matter how many times I click the button. 

And as to splash screens... Since I installed the lubuntu desktop there's been no splash screen, just black. Suits me fine, I'm allergic to purple!

---

### Post by warfacegod on 2010-07-21
> **RabbitWho said:**
> Hi, related problem with changing the login screen, that part of ubuntu tweak won't unlock no matter how many times I click the button. 

And as to splash screens... Since I installed the lubuntu desktop there's been no splash screen, just black. Suits me fine, I'm allergic to purple!

Right click your Menu bar and select Edit Menus> find the Ubuntu Tweak entry> highlight it and click Properties> change its Command to:

```
gksudo ubuntu-tweak
```

For this to take effect, you'll need to restart your session. Either log out or open a Terminal:

```
sudo restart gdm
```

---

### Post by JackNocturne on 2010-07-21
> **owners4life5 said:**
> how do i do that?



that only seems to apply to the login screen, not the splash

Login screen is a form of splash,called **xsplash/splash screen**, which splash did you want to change?

Do you want to change **grub.splash/bootsplash**?

---

### Post by gnik1 on 2010-07-21
[B]ubuntu-tweak doesn't show up in the software center for me. It's not showing up under installed applications either. 

Has the name of the tweak changed?
[/B]

---

### Post by RabbitWho on 2010-07-21
> **gnik1 said:**
> [B]ubuntu-tweak doesn't show up in the software center for me. It's not showing up under installed applications either. 

Has the name of the tweak changed?
[/B]


You have to get it from the website to download it. 

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) 

It's a deb. Very easy install don't worry.

---

### Post by warfacegod on 2010-07-21
> **gnik1 said:**
> [B]ubuntu-tweak doesn't show up in the software center for me. It's not showing up under installed applications either. 

Has the name of the tweak changed?
[/B]

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

There's been some confusion over whether or not Ubuntu Tweak is in the repos or not. It isn't but I think it should be.

---

### Post by JackNocturne on 2010-07-21
> **gnik1 said:**
> [B]ubuntu-tweak doesn't show up in the software center for me. It's not showing up under installed applications either. 

Has the name of the tweak changed?
[/B]

If it doesn't show up that usually means [B]the source for it is not listed in the software sources.

[/B]Quick way to download it is given below >

[http://launchpad.net/ubuntu-tweak/0.5.x/0.5.4/+download/ubuntu-tweak_0.5.4-1_all.deb](http://launchpad.net/ubuntu-tweak/0.5.x/0.5.4/+download/ubuntu-tweak_0.5.4-1_all.deb)

<
Cheers

---

### Post by owners4life5 on 2010-07-21
> **JackNocturne said:**
> Login screen is a form of splash,called **xsplash/splash screen**, which splash did you want to change?

Do you want to change **grub.splash/bootsplash**?

yes... the bootsplash

---

### Post by JackNocturne on 2010-07-21
Ok , then now comes the interesting part , you have to know which **version of GRUB **you have

```
grub --version
```

If its **Grub-legacy** (The older one) search for how to change it

If its **Grub 2** aka 1.97 or 1.98 , check this guide [http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)  > at the bottom there are explanations

---

### Post by owners4life5 on 2010-07-21
> **JackNocturne said:**
> Ok , then now comes the interesting part , you have to know which **version of GRUB **you have

```
grub --version
```

If its **Grub-legacy** (The older one) search for how to change it

If its **Grub 2** aka 1.97 or 1.98 , check this guide [http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)  > at the bottom there are explanations

maybe i didnt mean that.... i just meant the screen of when you boot... the progress screen it shows..

---

### Post by warfacegod on 2010-07-21
> **owners4life5 said:**
> maybe i didnt mean that.... i just meant the screen of when you boot... the progress screen it shows..

That is now called Plymouth.

---

### Post by JackNocturne on 2010-07-21
im confused a little bit, which part are you looking to change?

Grubsplash- At the beginning where you choose the OS/Kernel

LoginSplash-At the login screen

Usplash- Im not familiar with it but this is when the computer is in the process of booting
> [http://www.google.com/images?hl=en&q=usplash&um=1&ie=UTF-8&source=univ&ei=5v1GTIL-EMuFsAa309y3Aw&sa=X&oi=image_result_group&ct=title&resnum=4&ved=0CC0QsAQwAw&biw=1408&bih=688](http://www.google.com/images?hl=en&q=usplash&um=1&ie=UTF-8&source=univ&ei=5v1GTIL-EMuFsAa309y3Aw&sa=X&oi=image_result_group&ct=title&resnum=4&ved=0CC0QsAQwAw&biw=1408&bih=688) <
 
Are you looking for that?

---

### Post by owners4life5 on 2010-07-21
i.m wanting to change the plymouth screen... i just thought that was called a splash screen... sorry

---

### Post by JackNocturne on 2010-07-21
No problemo, this thread helps everyone. You got me interested in **plymouth**,it looks cool:)

---

### Post by gnik1 on 2010-07-21
> **RabbitWho said:**
> You have to get it from the website to download it. 

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) 

It's a deb. Very easy install don't worry.


Thank you, everything is running so sweet right now. Love it! Ubuntu 64 for 7 months now and no desire to go back!

---

### Post by owners4life5 on 2010-10-06
well it seems this thread has been discussed enough.

ha i.ve finally figured out how to do it elsewhere, and just going through old threads. so marking as solved.

thanks guys.

---

### Post by Zer0Nin3r on 2010-10-18
Mind throwing up the link to the thread you found useful?

---

### Post by owners4life5 on 2010-10-19
> **Zer0Nin3r said:**
> Mind throwing up the link to the thread you found useful?

i believe it was **this:**

[http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html](http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html)

---

