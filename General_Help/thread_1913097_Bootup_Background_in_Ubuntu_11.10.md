---
title: "Bootup Background in Ubuntu 11.10"
date: 2012-01-21
forum: General Help
---

### Post by memristor on 2012-01-21
I have set my Grub2 background to an image which is also my desktop background. I was able to get rid of gdm and default to lightdm and set my login screen background to same image i am using for desktop and Grub 2. 

Now this is my boot sequence
1) Grub 2 boot screen with the background that i set shows multiple boot options. The only issue here is that it seems there is a black frame encasing the background image. I have checked the resolution settings for Grub 2 and it seems to be same as my desktop resolution (1366 X 768 )

2)Once selection is made for Ubuntu from Grub 2, the options disappear and i only see background without any messages which is great (quiet mode)

3) After a short wait the screen goes dark and then there is a flicker which shows for a split second a purple background screen which was there as default in 11.04 and then my login screen loads up with the background image i had chosen.

It seems to me that right before the login screen loads somehow a blank purple screen is loaded for a brief moment. It just might be a left over from my earlier settings in 11.04 before i upgraded to 11.10.

So here is what i need to know
1) what could be causing that brief loading of a purple background before lightdm login screen loads up ?
2) How can i remove the black frame from my Grub 2 screen?

---

### Post by raja.genupula on 2012-01-21
Hi man actually the easiest way for dealing with Grub is moving with Grub customizer(see my signature) . for any appearance settings and for all grub related operation you can use that..

For the thing you wanna do , after installing Grub -customizer,open it.Then click at preference and then at appearance you can set background Image for your Grub .

all the best.

---

### Post by memristor on 2012-01-23
> **raja.genupula said:**
> Hi man actually the easiest way for dealing with Grub is moving with Grub customizer(see my signature) . for any appearance settings and for all grub related operation you can use that..

For the thing you wanna do , after installing Grub -customizer,open it.Then click at preference and then at appearance you can set background Image for your Grub .

all the best.

Thanks for your tip and kind words. I did install Grub Customizer and it seems to be a quick and easy way for customizing Grub2. However it does not solve the problem of purple screen flicker right before the login screen appears.

Also i ran vbeinfo in Grub2 console at bootup and it showed me the available resolutions which are less than what i have for my desktop, so that explains the black frame on the Grub2 screen.

However i would still appreciate it if someone can point me to the right direction for fixing that purple background flicker right before the login screen is loaded.

---

### Post by xyzzyman on 2012-01-23
There's going to be the delay as you're switching from a framebuffer to an actual modern accelerated video driver. Unfortunately it's purple.

---

### Post by memristor on 2012-01-23
Thanks for your reply!

The only reason i raised it up here was because it is different from my earlier experience on 10.10 and 11.04

On 10.10 i used to get Grub2 screen followed by a black screen and then the login screen. But there was no flicker

When i upgraded to 11.04 (by far the best experience i had on ubuntu!), i had a plymouth theme which went from boot screen to the login screen to the desktop. All that happened without any flicker .

In 11.10 i have this 
Grub2 background -> Black Screen -> Purple Screen flicker -> Login Screen

I was wondering if it is just some setting left over from my previous versions. Are you getting this flicker as well?

---

### Post by xyzzyman on 2012-01-23
> **memristor said:**
> Thanks for your reply!

The only reason i raised it up here was because it is different from my earlier experience on 10.10 and 11.04

On 10.10 i used to get Grub2 screen followed by a black screen and then the login screen. But there was no flicker

When i upgraded to 11.04 (by far the best experience i had on ubuntu!), i had a plymouth theme which went from boot screen to the login screen to the desktop. All that happened without any flicker .

In 11.10 i have this 
Grub2 background -> Black Screen -> Purple Screen flicker -> Login Screen

I was wondering if it is just some setting left over from my previous versions. Are you getting this flicker as well?

I only get flickers when I put grub2 into higher resolutions instead of text formats. It overrides plymouth, so when the normal switch from plymouth to X takes place there'd be a flicker.

Now I just use a regular text grub2, and I use an animated plymouth: [http://www.plymouth-themes.org/ubuntu-sunrise](http://www.plymouth-themes.org/ubuntu-sunrise). As over 9 times out of 10 I am booting into my regular 11.10 install I am thinking about disabling the grub2 menu anyways so I'll just have to hold shift that 1 time a week I'm doing something else.

EDIT: Unrelated but it got me off my *** to make the simple change in my grub.cfg and reboot to test it. :)

---

### Post by memristor on 2012-01-23
Thanks again for your feedback.

It is actually not a big deal at all and i can live with it. Fortunately after a very bad start with 11.10 i have finally been able to fix almost all my issues. 
Internal Mic which never worked is working now, Bluetooth is working too and i have made the switch to Gnome Shell which has become very much usable thanks to some decent extensions. My shutdown had become slow due to some networkmanager issue and thankfully i was able to fix that too :)

I really don't mind a flicker or too now :P

---

