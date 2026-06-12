---
title: "Compiz and 11.04 - Enabling desktop cube screwed up Unity"
date: 2011-04-28
forum: General Help
---

### Post by wheelern on 2011-04-28
Hey guys, just upgraded to the stable LTS today. Was loving it, until I messed something up :/

I installed with the image, running alongside Windows 7 on my desktop. I hadn't been in Ubuntu on my laptop for awhile, and hadn't experienced the 11.04 alpha's yet, so I didn't know there would be substantial changes. Obviously, Unity instead of Gnome surprised me a bit, but I have liked it so far.

But here lies the problem. I installed Compiz and ccsm through the software center, then went to enable the desktop cube and rotating cube. I clicked enable/disable on everything that popped up, but I think I must have disabled Unity (whoops). The whole desktop basically disappeared; that is, the dock on the left was gone and the window borders disappeared. I was able to close the windows with Alt+F4, but then couldn't open anything back up. The Super key didn't activate the dock, so it's not like it was hiding. I thought no problem, it'll start back up when I reboot. No dice. Still just the background, nothing to interact with. Only way to do anything is to reboot into with Ctrl+Alt+Dlt.

So...how do I fix this? Ha sorry for not reading forums beforehand, as I could've avoided this problem. Haven't found any threads on how to fix it, so I decided to start my own. Thanks in advance for any help.

---

### Post by Blasphemist on 2011-04-28
I did the same thing a while back. I had to login to classic, set up ccsm like it should be for unity, including enabling the unity plugin, reboot and login to unity.

---

### Post by wheelern on 2011-04-28
How do I do that? As soon as I boot into Ubuntu, all it asks for is  my login keyring. Once I put that in, I can't do anything. I guess I haven't tried a Ctrl+T yet to get into the terminal, but I wouldn't know how to fix it once there even if it worked... How do i boot into gnome2?

---

### Post by Blasphemist on 2011-04-28
Do you get to the graphic login screen? If so, as soon as you start entering your password you'll see at the bottom of the screen some boxes activate in the panel. Included is the option to login to classic and other options.

---

### Post by wheelern on 2011-04-28
Nah, cause I enabled automatic login. It's not the universal login screen, it's just a popup that asks for my login keyring for some reason other than the initial login...

---

### Post by coldbluesteel on 2011-04-28
Thanks Blasphemist, that helped me get unity back.

Now, how can I get both bars on the bottom of the screen where I like them?

I hate them where they are and see no option to change them.

---

### Post by mc4man on 2011-04-28
> **coldbluesteel said:**
> Thanks Blasphemist, that helped me get unity back.

Now, how can I get both bars on the bottom of the screen where I like them?

I hate them where they are and see no option to change them.

Then just run the gnome-panel login (Classic) and put your panels wherever and how many you wish

---

### Post by coldbluesteel on 2011-04-28
Looks like that is what I am going to have to do. If there is no way to configure the panels, my vote is Unity sucks rocks.

Back to Gnome I guess. Unity was neat for all of 5 minutes....

How can I make it always boot to the classic menu?

---

### Post by VanR on 2011-04-28
> **coldbluesteel said:**
> Looks like that is what I am going to have to do. If there is no way to configure the panels, my vote is Unity sucks rocks.

Back to Gnome I guess. Unity was neat for all of 5 minutes....

How can I make it always boot to the classic menu?

System>Administration> Log In Screen is how I did it. Change to Classic then Log out and then Log back in.

---

### Post by Blasphemist on 2011-04-28
> **wheelern said:**
> How do I do that? As soon as I boot into Ubuntu, all it asks for is  my login keyring. Once I put that in, I can't do anything. I guess I haven't tried a Ctrl+T yet to get into the terminal, but I wouldn't know how to fix it once there even if it worked... How do i boot into gnome2?

Oh that auto login. I don't know how to kill auto login without being able to get in, in your case to the blown up environment. You may have to reset gnome somehow. Sorry wheelern I don't know how to help now at least.

> How can I make it always boot to the classic menu?

Natty remembers your last choice, unity/classic/etc., and defaults to that for the next login.

---

### Post by U235master on 2011-04-29
if you can get to a terminal, type in gconf-editor

when that gets up go to
/apps/compizconfig-1/profiles/unity/general/screen0/options/

edit the key and remove cube rotate and then add unityshell and wall

that should work, but i haven't tested it. i did the same thing, disabling unity on accident but i didn't close ccsm, so i immediately enabled it

---

### Post by solaria on 2011-05-01
Yep, did the same thing here.  Seemed like a reasonable thing to do, to bring back some of the functionality of compiz...

What worked for me, to get Unity working again, was to type:

```
unity --reset
```

in a terminal window.  Restart gdm, and everything was back the way it was. 

Does this mean that you can't use Compiz options with Unity?  or only certain ones?

So far, Unity is rock sucking plenty.  Unfortunately, Ubuntu Classic is coming up blank for me... so it's either Unity or FluxBox.

---

### Post by Krytarik on 2011-05-01
> **solaria said:**
> 
Does this mean that you can't use Compiz options with Unity?  or only certain ones?Some of its plugins may not work correctly at any system. And if you change major options in CCSM, like enabling/disabling plugins, you may need to relogin to make Compiz work properly.
> **solaria said:**
> 
Ubuntu Classic is coming up blank for me
Create a launcher for the command "gnome-panel" at your desktop and launch it to get the panels. We have to investigate to figure why it's not run at login.

---

### Post by teh8bits on 2011-07-15
Sorry to bump this but the same thing happened to me after i tried to enable the cube. I could still right click so i hit create launcher and entered the following: type application, name: logout, command: gnome-session-save --kill
That command logs you out so you can get to the desktoo environment selection/login so you can boot into classsic and fix the problem. Speaking of fixing the problem, what all needs to be enabled/disabled for unity to work? I still can only login to classic mode.

---

### Post by Blasphemist on 2011-07-15
Try this to see if you get back to where you can login to unity.

```
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
sudo reboot
```

Then use this link to set up the cube.
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

---

### Post by Krytarik on 2011-07-15
teh8bits, please see this troubleshooting guide:
[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

It includes this guide, to enable the Cube:
[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

Greetings.

---

### Post by Gwaro on 2011-07-15
Did the same and i wished i was here before that.I didn't know what to do till i reinstalled!Damn!..i mean one command could have done it all!!

---

### Post by teh8bits on 2011-07-15
I feel bad admitting this but reading the post about using unity --reset fixed the problem. Im keeping the logout command in my desktop though it's a quick way to logout. I will also try following the guides to enable the cube to see if that works. Im so obviously new to ubuntu so i havent ever seen the cube in action before but it seems useful. I really wish they hadnt done the whole side bar thing though. And i dont want to use classic as i want to get used to this sidebar thing before it becomes the standard.

EDIT: Also Krytarik that guide wasnt very useful because I couldnt use run or anything of the sort. Its a macbook keyboard and the run shortcut doesnt always work well anyways.

---

### Post by Krytarik on 2011-07-15
> **teh8bits said:**
> 
EDIT: Also Krytarik that guide wasnt very useful because I couldnt use run or anything of the sort. Its a macbook keyboard and the run shortcut doesnt always work well anyways.
Talking about shortcuts, yeah, there might be issues with MacBooks in that aspect, as you say, but this has obviously nothing to do with those guides, instead it's really a general issue that you will encounter recurringly when you try to use shortcuts, if you don't fix it.

---

### Post by teh8bits on 2011-07-15
To be honest I looked at it after I used unity --reset so I kind of skimmed it just to see what it had in it. Sorry for not reading things through Im bad about that, that's the reason I dont reallly contribute to forums more because I akways double post solutions and what not.

EDIT: Followed the cube guide you provided Krytarik and viola it's working, thanks so much!

---

### Post by wildmanne39 on 2011-07-15
> **teh8bits said:**
> I feel bad admitting this but reading the post about using unity --reset fixed the problem. Im keeping the logout command in my desktop though it's a quick way to logout. I will also try following the guides to enable the cube to see if that works. Im so obviously new to ubuntu so i havent ever seen the cube in action before but it seems useful. I really wish they hadnt done the whole side bar thing though. And i dont want to use classic as i want to get used to this sidebar thing before it becomes the standard.

EDIT: Also Krytarik that guide wasnt very useful because I couldnt use run or anything of the sort. Its a macbook keyboard and the run shortcut doesnt always work well anyways.
Hi, if you find you have problems using the other guide to set up the cube and effects you might look at this link it has pictures for every step.
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

---

### Post by pritam_par on 2011-07-18
Open terminal and type

metacity --replace and
unity --replace

---

