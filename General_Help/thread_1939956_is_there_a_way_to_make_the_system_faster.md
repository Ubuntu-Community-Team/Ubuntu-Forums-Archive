---
title: "is there a way to make the system faster?"
date: 2012-03-12
forum: General Help
---

### Post by jekylhyde on 2012-03-12
Hi
is there a way to make the system faster?
in windows for example you could tchoose between better apperance for performance 
[IMG]http://res1.windows.microsoft.com/resbox/en/Windows%20Vista/main/362325ab-443c-4fec-988b-530f0a809cd6_16.png[/IMG]
how to do it in ubuntu? i have 11.10
thanks

---

### Post by josiahrulez on 2012-03-12
> **jekylhyde said:**
> Hi
is there a way to make the system faster?
in windows for example you could tchoose between better apperance for performance 
[IMG]http://res1.windows.microsoft.com/resbox/en/Windows%20Vista/main/362325ab-443c-4fec-988b-530f0a809cd6_16.png[/IMG]
how to do it in ubuntu? i have 11.10
thanks

You can swap between desktop environments, i use ubuntu classic (seems to use less system resources). 
On the log on screen it should have options down the bottom to change the desktop environment.

And I'm not entirely sure about this, but i think i read somewhere that you can install new desktop environments (maybe to one that uses less system resources?)

---

### Post by Gremlinzzz on 2012-03-12
The easy way is to buy a faster computer:popcorn:
But there are a lot of Linux systems that use less resources .
try em out 
[http://distrowatch.com/](http://distrowatch.com/)

---

### Post by gunksta on 2012-03-12
I've not researched it, but I wonder what it is that this Windows option does. It isn't very specific. Is there something that you feel is too slow in your Ubuntu installation? If you have a specific question, the forum might be in a better position to offer ideas.

For example, the CompizConfig Settings Manager (not installed by default) has options to tweak Compiz, the window manager used by Ubuntu. You could try turning off Animations and/or Fading Windows if you feel your computer doesn't have a fast enough 3D card. But, be careful, Unity needs specific things and if you aren't careful, you can bork Unity. Its a good tool, but one that needs to be used with care. Hence my first suggestion.

If you go into the Startup Applications Preferences, you might find something there you can safely disable. For example, I disable the Gnome Login Sound but not because it makes my computer any faster. I just don't like login sounds. They annoy me.

To sum up -- I think this is mostly a bogus trick to make people feel better. _**IF**_ this button does anything, it comes with a cost by turning off functionality that many users may want/need. There ain't no such thing as a fee lunch. I don't know what it disables, but it must do something. It may also prevent the system from cycling down as quickly which might be OK on a desktop but terrible on a laptop where battery performance is often more important than speed. Again, these are just thoughts from a guy who doesn't allow Windows machines to get onto his home network and I usually charge anyone other than my employer for Windows support. I'm not what you could call unbiased.

If you want a faster/lighter desktop, you could try installing the Lubuntu / Xubuntu desktops. Many users prefer these alternatives. Studies have shown that Xubuntu, in real day-to-day use is no more memory efficient than Gnome/Unity, but it does start up faster. Lubuntu uses fewer system resources but these desktops are, to some users, less user-friendly than Unity, the default Ubuntu desktop.

---

### Post by 3rdalbum on 2012-03-12
It doesn't have a lot of relevance for Ubuntu, and it doesn't really speed up your computer - it just speeds up visual effects and animations.

What about your computer seems slow?

On low-end computers the Ubuntu Dash comes up after a delay, but when Ubuntu 12.04 is released you can upgrade to that, which shortens the delay and makes the Dash feel more responsive.

---

### Post by jekylhyde on 2012-03-13
> **3rdalbum said:**
> It doesn't have a lot of relevance for Ubuntu, and it doesn't really speed up your computer - it just speeds up visual effects and animations.

What about your computer seems slow?

On low-end computers the Ubuntu Dash comes up after a delay, but when Ubuntu 12.04 is released you can upgrade to that, which shortens the delay and makes the Dash feel more responsive.

what is slow?
i click & see the reaction after a few seconds
the window dims out a bit & become a bit darker... i guess it's like in win vista that the window is not very responsive & gets a bit brighter ...
a lot of lagging.

---

### Post by gunksta on 2012-03-13
jekylhide - I think people want to know what application(s) you feel are running slowly. You described the behavior, not the application. If you feel your system isn't running as well as it should be, you may well be right.

We need to know what apps are causing problems and the setup/specs of your computer in order to really do much.

---

### Post by jekylhyde on 2012-03-13
> **gunksta said:**
> jekylhide - I think people want to know what application(s) you feel are running slowly. You described the behavior, not the application. If you feel your system isn't running as well as it should be, you may well be right.

We need to know what apps are causing problems and the setup/specs of your computer in order to really do much.

you had to understand by now thati'm describing an environment problem
not an app specific problem
so the answer is - in every app...
any application that i want to run, is reacting slow

---

### Post by gunksta on 2012-03-13
What are the specs (especially graphics) on this machine?

I'm curious to know if Ubuntu/Unity 2D is any faster for you.

---

### Post by Bucky Ball on 2012-03-13
Mini.iso install. Only install what you want rather than a full Ubuntu (or Xubuntu or anything else for that matter). I was getting to the login screen in 12 seconds and the machine flew in every other way. Use a lightweight desktop environment; xfce, lxde, openbox, etc ...

---

### Post by jekylhyde on 2012-03-13
> **Bucky Ball said:**
> Mini.iso install. Only install what you want rather than a full Ubuntu (or Xubuntu or anything else for that matter). I was getting to the login screen in 12 seconds and the machine flew in every other way. Use a lightweight desktop environment; xfce, lxde, openbox, etc ...

what is mini.iso? have a link? thanks

btw, CompizConfig Settings Manager speeded up things a bit
but i installed xubuntu & its much more responsive :)

---

### Post by Mark Phelps on 2012-03-13
Sorry if this is going to sound like nit-picking ... but it's not.

The MS Windows setting only turns off display features that grab some of the video processor's power.  So, in some circumstances, if the screen redraws faster, that can make the PC "seem" faster -- even though it's not.

Most of what is suggested is really disabling stuff that is using processor power, once again, it's not really making the PC any "faster", it's really just disabling stuff that is using resources.

If what you're experiencing is an overall SLOW response on everything you do, that likely to be a combination of the following:
-- Heavily fragmented filesystem and/or failing hard drive
-- Very little available system memory (i.e., running with 512MB or less)
-- Very poor video drivers (i.e., no acceleration at all, not even 2D)
-- Lots of stuff running in the background (i.e., monitors, active desktop graphics, other resident processes you don't need).

Going to an alternative distro that uses less fancy graphics (reduces the GPU demands) and runs less in the background will make your PC seem faster -- but that's because you're giving up stuff that you have now in Ubuntu.

So basically, there is no single "do this and your PC will run like lightning" solution -- even though the TV ads are full of them.

---

### Post by Bucky Ball on 2012-03-13
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Xfce rocks!!! There is a link for minimal install info. ;)

---

### Post by jekylhyde on 2012-03-14
> **Bucky Ball said:**
> [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Xfce rocks!!! There is a link for minimal install info. ;)

is there mini for xubuntu?

---

### Post by Bucky Ball on 2012-03-14
You just install the xfce4 desktop environment and the packages you want from Xubuntu. That's why it's fast. 

The Ubuntu base system is identical for all Ubuntu based systems; xubuntu, kubuntu, edubutu, etc. With the minimal install you add what you want, in your case, for an Xubuntu environment, you would install the xfce4 DE when you get to that part of the install (where you install the packages you want to install). Make sure you install Synaptics or Software Centre to start with and then you can add other things you want once at a desktop.

You will wind up with a very basic system to start with and then add to that as you go (and as required). That is why it is fast. ;)

---

