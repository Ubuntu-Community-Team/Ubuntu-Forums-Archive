---
title: "Ubuntu 10.10 Bootup Screen"
date: 2010-10-12
forum: General Help
---

### Post by schworak on 2010-10-12
I just installed Ubuntu 10.10 and all went well.

I don't really see any real changes from 10.04. At least not anything that jumps out and grabs my attention. Well, with one negative exception and totally cosmetic I might add.

The boot screen. It is a crappy bit of text that says Ubuntu 10.10 with the . . . . (dots) below it. And if any messages need to be displayed, they appear just to the right of the dots instead of on their own line below the dots.

I don't know of any way to change that boot screen myself but if anyone has advice that would be great. I am not sure why the more polished boot screen from 10.04 was tossed. I can't imagine it consumed much memory for a tiny bit of flash and polish. At a minimum, why did no one notice that the messages are in the wrong place on the boot scree making them very hard to read.

Anyway, just thought I would see if anyone had any suggestions for fixing the annoying boot up screen.

---

### Post by Bent Axle on 2010-10-12
I just noticed this myself.

Clean install 10.10 x64.

I'm also curious about a solution for this.

---

### Post by thenick on 2010-10-12
Same here. This is sooooo NOT 10 out of 10! :( The bootup screen when I install the Ubuntu 10.10 desktop was what I expect.

---

### Post by DogMatix on 2010-10-12
I don't see this during 10.10 boot everything looks pretty much as it did with 10.04.

---

### Post by schworak on 2010-10-12
> **DogMatix said:**
> I don't see this during 10.10 boot everything looks pretty much as it did with 10.04.

I don't imagine so... Unless in 10.04 you some how changed the rather nice looking boot screen to look rather cruddy and plane-jane. And the messages (such as checking your hard drive) was nicely placed centered on the screen well under the dots . . . . under the UBUNTU text.

This is all just before the login screen comes up.


Ubuntu 10.04 Boot Screen
[IMG]http://www.hackourlives.com/wp-content/uploads/2010/05/Ubuntu-10.04-Lucid-Lynx.png[/IMG]


Ubuntu 10.10 boot screen
[IMG]http://www.liberiangeek.net/wp-content/uploads/2010/09/perfect_desktop_mav_thumb.png[/IMG]

ICK! ICK! ICK!

---

### Post by Bent Axle on 2010-10-12
^^^ Yup. This is the same boot screen as I'm getting.

BTW... I'm running the NVidia drivers out of the repos.

BA

---

### Post by jpepin on 2010-10-14
I'm having the same issue.  10.04 looked fine.  10.10, clean install with nvidia drivers, and the boot screen looks like the bottom picture above (text with dots).  

Looks like it's probably a video driver issue.

---

### Post by BlazeFire247 on 2010-10-14
> **schworak said:**
> Ubuntu 10.04 Boot Screen
[IMG]http://www.hackourlives.com/wp-content/uploads/2010/05/Ubuntu-10.04-Lucid-Lynx.png[/IMG]


Ubuntu 10.10 boot screen
[IMG]http://www.liberiangeek.net/wp-content/uploads/2010/09/perfect_desktop_mav_thumb.png[/IMG]

ICK! ICK! ICK!

I don't know how you got that boot screen 0.o, I'm seeing the one on top. The bootup screen should be changed. I don't really like the purple on it mostly.

---

### Post by Megaptera on 2010-10-15
I think this Plymouth fix also works in 10.10

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by mickeoliver on 2010-10-15
No it doesn't - there is no* /etc/default/grub (Atleast I don't have it)*[COLOR=Black][COLOR=#008080][/COLOR][/COLOR]

---

### Post by Megaptera on 2010-10-15
Sorry 'bout that! How about this?

[http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html#more](http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html#more)

Hope this helps?

---

### Post by Claus7 on 2010-10-15
Hello,

had the same problem with ubu 10.10 64 bit after installing the proprietary drivers. Chose to install sunrise sunset plymouth boot screen from gnome look org the one which fixes also the resolution issue. My boot screen is looking very nice. Also I changed my login screen.

The only problem I get is a red screen just before entering my desktop and just after the typing of my password for a couple of seconds, yet is just a minor issue.

I do agree that the Ubuntu 10.10 text boot screen is really bad looking compared to the default one. 

Could I ask how do you paste a pic on ubuntu forums, without attaching it?...

Regards!

---

### Post by schworak on 2010-10-15
> **mickeoliver said:**
> No it doesn't - there is no* /etc/default/grub (Atleast I don't have it)*

I don't have that directory either. I am not sure that changing the screen resolution would help either. I really don't care that the text looks cheap. It is only there for a moment. I am more worried about how hard it is to read any text that pops up because it wraps around the screen instead of being located in a readable location under the . . . . marks.

---

### Post by schworak on 2010-10-15
Did I mention that I am running a 64bit version of the OS? In case that makes a difference.

---

### Post by Claus7 on 2010-10-15
Hello,

> **schworak said:**
> I don't have that directory either. I am not sure that changing the screen resolution would help either. I really don't care that the text looks cheap. It is only there for a moment. I am more worried about how hard it is to read any text that pops up because it wraps around the screen instead of being located in a readable location under the . . . . marks.

yes it makes a difference, the resolution issue that is. And that, because no matter how many times I had configured plymouth I was not able to get rid of the simple text-ish Ubuntu 10.10. I was not able to see any other plymouth theme during boot process. About the messages that pop up I think that you can rid off them from the login screen menu. There is somewhere an option about enabling or disabling text during boot.

> **schworak said:**
> Did I mention that I am running a 64bit version of the OS? In case that makes a difference.

Same as yours.

edit1: Having tested both on 32 and 64 bit with the same results.
edit2: Why do you care about the text being wrapped around since you do not care about the visual result? You can check any errors logs during boot from System-> Administration -> Log File Viewer afterwards...

Regards!

---

### Post by masaibana on 2010-10-16
Hi all.. I'm purely new in linux. Please help. :-D
I'm using ubuntu 10.10 amd64.
I dont like the default bootscreen and want to change it. So what should I do..?

At first I installing ubuntu, it shows me my another os which end up by 10 second. Than I install kubuntu desktop and StartUp-Manager. Now it move to use the kde bootscreen.
I have the etc/default/grub file, but I dont know how to change the boot screen and the boot animation. Can somebody help me where to go next..?? :cry:

---

### Post by schworak on 2010-10-17
Sorry for the delay in replying but the problem is solved for me.

After thinking about it, the screen resoultion issue seemed to make sense. I still think it is a bit of a bug but being that it is only cosmetic I don't expect to see it fixed any time soon.

With a low boot screen resolution, the system drops to a text mode boot screen and it looks really ugly.

But kick the resolution up and the system goes to a graphic screen (like the top picture in my previous post) and the text it displays during boot (some times) looks fine again. It appears that attention was given to the graphic version of the boot screen but not the text version.

Anyway, to change the resolution, click the system menu, administration, startup-manager. Then change the resolution up until it works for you. I like the look of 1024x768 but you might like another setting. 640x480 is the default and causes the text-only screen and the issue. I also set the color depth to 16 bit.

I like the "show boot splash" and "show text during boot" checked. This way I can see why the system is delaying (if it does) such as checking disks or other messages that may come up.

---

### Post by masen on 2010-10-20
Thanks for the tip, that did the trick for me!

---

### Post by Claus7 on 2010-10-24
Hello,

> **schworak said:**
> Sorry for the delay in replying but the problem is solved for me.

After thinking about it, the screen resoultion issue seemed to make sense. I still think it is a bit of a bug but being that it is only cosmetic I don't expect to see it fixed any time soon.

With a low boot screen resolution, the system drops to a text mode boot screen and it looks really ugly.

But kick the resolution up and the system goes to a graphic screen (like the top picture in my previous post) and the text it displays during boot (some times) looks fine again. It appears that attention was given to the graphic version of the boot screen but not the text version.

Anyway, to change the resolution, click the system menu, administration, startup-manager. Then change the resolution up until it works for you. I like the look of 1024x768 but you might like another setting. 640x480 is the default and causes the text-only screen and the issue. I also set the color depth to 16 bit.

I like the "show boot splash" and "show text during boot" checked. This way I can see why the system is delaying (if it does) such as checking disks or other messages that may come up.

glad you solved your problem! And your solution is expressed in much detail. So indeed it was a resolution issue after all. Think a lot of people would benefit from this... 

Regards!

---

### Post by M1ke on 2010-11-15
> **schworak said:**
> Anyway, to change the resolution, click the system menu, administration, startup-manager. Then change the resolution up until it works for you. I like the look of 1024x768 but you might like another setting. 640x480 is the default and causes the text-only screen and the issue. I also set the color depth to 16 bit.

I like the "show boot splash" and "show text during boot" checked. This way I can see why the system is delaying (if it does) such as checking disks or other messages that may come up.
This worked for me too, thank you so much! 1024x768, 24 bit colour depth looks gorgeous.

Just in case it's not obvious to anyone else trying to fix this issue, grab startup-manager from the repo. Took me a minute or two of confusion!

---

### Post by celldweller1591 on 2011-01-12
Try this :

- Open up a Ternimal and install the Startup-Manager
> sudo apt-get install startupmanager 
-Launch the Startup Manager from "System>-Administration->Startup-Manager"
-In the "Boot options" tab, change the resolution to something your monitor can handle (1024x768 is usually enough for the boot screen to look nice).
-Change the color depth to "24 bits" and Press the "Close" button.Followed by a reboot to check that it is fixed.

---

