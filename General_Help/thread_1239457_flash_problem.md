---
title: "flash problem"
date: 2009-08-13
forum: General Help
---

### Post by Szat on 2009-08-13
I'm having a problem viewing websites that implement flash. I can view Youtube, but everything else doesn't work. I have flash installed, but I still get pop ups saying I need to install it. When I click to install it it says it is already installed. I installed ubuntu restricted extras thinking it would fix my problem, but it still didn't work. Any suggestions?

---

### Post by XCan on 2009-08-13
Are you running 32bit or 64bit Ubuntu? The one in the repo is 32bit. You'll have to download the 64bit from Adobe labs if you need it.

---

### Post by jms1989 on 2009-08-13
are you using the firefox addon "noscript"? that might be the cause.

---

### Post by pums on 2009-08-13
I'm having similar problesm when i try to open the cisco  CCNA Explration Course, i can see videos in other pages, but this page would only come out with a message: "ERROR the chapter requested does not exists"; but it does i have it openned in this same camputer with damn Windows Vista and it worked, i dont know what do i need to make this work, any suggestions? 

Thanks

---

### Post by Szat on 2009-08-14
I'm running 32-bit Ubuntu and I'm not using the noscrpit addon.

---

### Post by psychoelf on 2009-08-14
Try removing all instances of flash in Synaptic and reinstalling from the .deb file from Adobe's web site.

Also, what do you mean by everything else?  There still may be a few things out there you cant use as Flash for Linux
seems to still have a few bugs.

I've been able to use almost everything flash with the exception of one or two flash based games.

And you may want to check the forums to make sure your video card doesnt cause some kind of conflict with flash.

---

### Post by Szat on 2009-08-14
By everything else I mean South Park Studios, Liveleak, even advertisements don't show up. The ads just have a play button and when I click it they play. I have a Nvidia GeForce Go 6800.

---

### Post by psychoelf on 2009-08-14
South Park Studios worked fine for me.  Just watched "Kick the Baby". :)

I would try complete removal/reinstall of Flash.  Just search "flash" in Synaptic and mark any that are installed for complete removal.  Then head to Adobe's site and choose the .deb version from the dropdown menu.

Hope that works!

---

### Post by Szat on 2009-08-14
I uninstalled all Flash files I had and installed the .deb version, but it still doesn't work. Firefox says I don't have Flash in my tools>addons>plugins tab.

---

### Post by zkriesse on 2009-08-14
What flash version did you install? Be exact.

---

### Post by psychoelf on 2009-08-14
Go to synaptic and install "flashplugin-nonfree".

Hope that works.

---

### Post by lovinglinux on 2009-08-14
See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

### Post by Szat on 2009-08-14
I downloaded the .deb Flash Player 10 and "flashplugin-nonfree" is already installed.

---

### Post by zkriesse on 2009-08-14
Ok man. Here's the deal. You got alot of people trying to help you here...at the least try to be more specific....I mean include details.....otherwise don't waste our valuable time because we're willing to help, but we need specifics....please.

---

### Post by psychoelf on 2009-08-14
I would try lovinglinux's thread and see if that works.  If not post back and hopefully someone may have a solution.

Also double check that your flash plugin is enabled in firefox just in case.

And have you tried rebooting/loging out since reinstalling?  Worth a try.

Good luck!

---

### Post by Szat on 2009-08-14
> **Zachk18 said:**
> Ok man. Here's the deal. You got alot of people trying to help you here...at the least try to be more specific....I mean include details.....otherwise don't waste our valuable time because we're willing to help, but we need specifics....please.

How am I wasting your time? You wasted your own time posting on this thread douchebag. 

I told you everything I know so far in the post. I have Ubuntu 9.04 32-bit, Nvidia GeForce Go 6800, I installed Flash from Synaptic, uninstalled it, downloaded the .deb file from Adobe, installed that, still didn't work, uninstalled that, reinstalled Flash from synaptic again, still doesn't work. I have the non-free and ubuntu-restricted-extras. I can't get more specific unless people ask me questions.

> **psychoelf said:**
> I would try lovinglinux's thread and see if that works.  If not post back and hopefully someone may have a solution.

Also double check that your flash plugin is enabled in firefox just in case.

And have you tried rebooting/loging out since reinstalling?  Worth a try.

Good luck!

Firefox says I don't have the flash plugin. Yes, it has been rebooted.

> **lovinglinux said:**
> See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

I entered the codes in the terminal, but flash is still not working. My buddy is a computer engineer and he uses Ubuntu all the time. He couldn't figure it out either.

---

