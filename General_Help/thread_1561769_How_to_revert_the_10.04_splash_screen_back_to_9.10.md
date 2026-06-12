---
title: "How to revert the 10.04 splash screen back to 9.10"
date: 2010-08-26
forum: General Help
---

### Post by andy_blah on 2010-08-26
I really liked the previous splash screen (loading and shutdown ones), this current one is kind of... boring. Is there any way to revert back to it, or to download and install it afterwards?

---

### Post by Cavsfan on 2010-08-26
> **andy_blah said:**
> I really liked the previous splash screen (loading and shutdown ones), this current one is kind of... boring. Is there any way to revert back to it, or to download and install it afterwards?

Use Ubuntu Tweak to change the login screen. Or check out the tutorial in my sig. for how to have a custom GRUB2 boot screen if that's what you meant.

---

### Post by mr clark25 on 2010-08-26
i think he wants to make this [http://www.sucka.net/wp-content/uploads/2010/03/boot.png](http://www.sucka.net/wp-content/uploads/2010/03/boot.png) look like this: [http://www.linuxnewbieguide.org/userfiles/xsplash-3.png](http://www.linuxnewbieguide.org/userfiles/xsplash-3.png)

i kind of want to know how to do this too-- i agree with the thread poster.

---

### Post by Cavsfan on 2010-08-26
> **mr clark25 said:**
> i think he wants to make this [http://www.sucka.net/wp-content/uploads/2010/03/boot.png](http://www.sucka.net/wp-content/uploads/2010/03/boot.png) look like this: [http://www.linuxnewbieguide.org/userfiles/xsplash-3.png](http://www.linuxnewbieguide.org/userfiles/xsplash-3.png)

i kind of want to know how to do this too-- i agree with the thread poster.

Ubuntu Tweak is the only thing I know that can do this. I have a custom login screen.
If you don't have Ubuntu Tweak go to **Applications** > **Ubuntu Software Center** and 
at the top right enter "Ubuntu Tweak" and you will see **config Ubuntu tool**.

Once installed, go to **Applications** > **System Tools** > **Ubuntu Tweak** then it will be 
under **Login Settings. ** You can set it to any picture you want.

---

### Post by andy_blah on 2010-08-26
Well, not exactly, what both me and mr_clark25 wanted to say is that I would want to change the loading screen, not the login screen or the Grub2 menu ^^;
Also just FYI, Ubuntu Tweak isn't available in the Software Center.

---

### Post by Cavsfan on 2010-08-27
> **andy_blah said:**
> Well, not exactly, what both me and mr_clark25 wanted to say is that I would want to change the loading screen, not the login screen or the Grub2 menu ^^;
Also just FYI, Ubuntu Tweak isn't available in the Software Center.

The login screen is what **mr_clark25** posted about changing in his last post. He posted 2 example pictures. 
It is in the **Ubuntu Software Center **it's just called [COLOR=Red]**config Ubuntu tool**[/COLOR].

> **Cavsfan said:**
> Ubuntu Tweak is the only thing I know that can do this. I have a custom login screen.
If you don't have Ubuntu Tweak go to **Applications** > **Ubuntu Software Center** and 
at the top right enter "Ubuntu Tweak" and you will see [COLOR=black]**config Ubuntu tool**[/COLOR].

Once installed, go to **Applications** > **System Tools** > **Ubuntu Tweak** then it will be 
under **Login Settings. ** You can set it to any picture you want.

Here is another way to get Ubuntu Tweak with instructions on what it does:

[[COLOR=blue]_How to install ubuntu-tweak in Ubuntu 10.04(Lucid Lynx)_[/COLOR]]("http://www.ubuntugeek.com/how-to-install-ubuntu-tweak-in-ubuntu-10-04lucid-lynx.html")

(look for the **Login Settings screen**)

And if you also want to change the boot menu (GRUB2) check the tutorial in my signature.

---

### Post by Cavsfan on 2010-08-27
No, I was wrong. You are wanting to change the Plymouth screen.

Here is a link to get you started [[COLOR=blue]_here._[/COLOR]]("http://www.google.com/webhp?as_q=#hl=en&q=ubuntu+10.04+plymouth&aq=0&aqi=g10&aql=&oq=ubuntu+10.04+plymo&gs_rfai=&pbx=1&fp=7db4f7af4a13aa89")

I have never messed with that particular screen myself.

---

### Post by andy_blah on 2010-08-27
[This]("http://ubuntu-tutorials.com/wp-content/uploads/2009/03/ubuntu-jaunty.png") is how a login screen looks like and [this]("http://linuxnewbieguide.org/userfiles/xsplash-3.png") is what mr_clark25 showed. I tried installing Ubuntu Tweak 9by downloading the deb from it's official site) and that feature can just change the background of the login screen, it's not really useful since I'm automatically logged in =P

EDIT: Nevermind, I didn't notice you replied ^o^;

---

### Post by andy_blah on 2010-08-27
Hmm, I can't seem to install that suggested rpm package, I can't either convert it with alien or run it in any way, plus that I'm not sure if xsplash themes work with plymouth X.X

---

### Post by Cavsfan on 2010-08-27
> **andy_blah said:**
> [This]("http://ubuntu-tutorials.com/wp-content/uploads/2009/03/ubuntu-jaunty.png") is how a login screen looks like and [this]("http://linuxnewbieguide.org/userfiles/xsplash-3.png") is what mr_clark25 showed. I tried installing Ubuntu Tweak 9by downloading the deb from it's official site) and that feature can just change the background of the login screen, it's not really useful since I'm automatically logged in =P

EDIT: Nevermind, I didn't notice you replied ^o^;

I've looked into changing the Plymouth screen and it appears a bit more complicated than it first appears.
The screen that appears is actually a theme. 

Here is a link that might help:

[[COLOR=blue]_http://ubuntuguide.net/howto-change-plymouth-themes-initial-splash-screen-in-ubuntu-10-04_[/COLOR]]("http://ubuntuguide.net/howto-change-plymouth-themes-initial-splash-screen-in-ubuntu-10-04")

---

### Post by Cavsfan on 2010-08-27
In **Synaptic** you can enter **plymouth-theme** and see what Plymouth themes are available directly from the repositories.

Edit: However, it says this on each of the non-default themes:
[B]These theme may not correctly display messages from filesystem
decryption, checking or error handling.[/B]

---

### Post by mr clark25 on 2010-08-28
looks like its not as hard as i thought it was going to be. thanks for helping. i will probably test this on a different computer just to make sure i know what im doing. that how-to makes it look pretty simple.

---

### Post by Cavsfan on 2010-08-28
> **mr clark25 said:**
> looks like its not as hard as i thought it was going to be. thanks for helping. i will probably test this on a different computer just to make sure i know what im doing. that how-to makes it look pretty simple.

You are welcome! :D
If you are referring to my GRUB2 tutorial. It's pretty straight forward. I have a nice GRUB2 picture 
and a nice logon picture, but I am not going to mess with the Plymouth screen that **andy_blah** was 
talking about changing. There just seems to be too much at risk. The default theme is supported with 
updates, but anything you do to customize it will not be. It doesn't bother 
me to see that screen for a few seconds at bootup.

---

### Post by andy_blah on 2010-08-28
The problem is that I actually wanted that specific boot-up screen from 9.10, but for that I would need to purge Plymouth (that isn't working at all at the moment) and to set Ubuntu to use xsplash/usplash, unfortunately after some research I found out that's next to impossible, since Plymouth is now completely integrated with it. I don't like that because it doesn't give me the freedom of choice (same thing with the buggy PulseAudio over straight to Alsa -- had to disable it, now some Ubuntu sound features aren't even available, but had to do it due to some issues with Skype), this piece of software doesn't even want to work after I installed the proprietary nVidia drivers. I hope those at Canonical plus the developers take a different path into making this OS, because this isn't fun at all, but then again there are other distros out there.

But nevertheless, I thank you Cavsfan for your help.

---

### Post by mc4man on 2010-08-28
> Is there any way to revert back to it, or to download and install it afterwards?
no
> 
looks like its not as hard as i thought it was going to be
If you wished to see what you had/have in karmic in lucid/maverick you'd need to create a new theme, have it added to  alternatives, ect.
Not an easy undertaking at all.

plus also if using nvidia account for diff's from nouveau and restricted
(plus as mentioned due to increased boot times may only be there for several sec.'s


(I really did like it in karmic - was a bit disappointed it wasn't expanded upon as a plymouth theme, though do use the .png as my desktop in maverick, works well @ 1920x1080, quite mellow, fits good with the orig ambience theme ( not the current 'orange' based ambience

---

