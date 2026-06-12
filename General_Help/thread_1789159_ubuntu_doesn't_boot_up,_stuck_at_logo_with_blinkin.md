---
title: "ubuntu doesn't boot up, stuck at logo with blinking process bar"
date: 2011-06-23
forum: General Help
---

### Post by pxs096320 on 2011-06-23
Dear friends,
I am a novice to ubuntu. I was just curious to learn more about it. I   have currently installed the ubuntu 11.04 natty narwhal edition through  the wubi installer alongside windows 7. I  wanted to just check out what  the kde environment had to offer  differently from the default desktop  environment which is gnome unity  environment. 

I installed the kde environment using some sudo command given by google.   After using kde environment for a few hours, I just began to feel, I   liked the default gnome environment better (in classic mode) as compared   to kde as I was more used to the former. 

So I uninstalled kde with another sudo command which I got by googling.   At the final step of the uninstallation, I admit I am not sure whether   what I did was right or wrong. There was sth related to 'daemon' that   popped up eventually and I chose yes for that and kde was uninstalled   successfully or atleast that's what I thought. 

But to my horror, when i tried rebooting my laptop to ubuntu gnome, the   blue coloured kubuntu logo was popping once again and I had to go back   to the synaptic package manager and delete sth called the 'plymouth'   package to remove the kubuntu logo. 

Now after doing all these, when I tried booting ubuntu, I was not able   to get to the gnome login screen. The screen was just stuck with the  ubuntu  logo and the process bar blinking and gnome never started. 

When I pressed the Esc key to check out what was happening from behind, I   could see that some processes were being checked and there was a [ok]   after everything and there was a [FAIL] next to "starting CPU  interrupts  balancing daemon". And the terminal screen ended with  "stopping system V  run level compatibility". I am not sure if this  might be the root cause  of blocking the boot-up. But I couldn't get a  screenshot of those  intermittent terminal screens as I was not in a  position to type in any  commands such as fbgrab which can be used to  grab a screenshot of the  terminal screen.

Eventually after intense googling, I figured how to manually configure   gnome to start up. I pressed the Cnt + Alt +F1 as soon as the white   ubuntu logo popped up and after logging in into my ubuntu account   through the terminal interface, I typed in the following things.
sudo dpkg-reconfigure gdm
sudo /etc/init.d/gdm start
and then voila I got the gnome login screen. I temporarily heaved a sigh   of relief. (by the way I saw something flash quickly on the terminal   moments before it went to the gnome login screen like "you need not init   this way or sth"..I just couldn't catch sight of it properly as it   flashed only for a few moments)

But I am not satisfied. Obviously there might be a way to set this   problem right isn't it? Kindly someone pls throw some light on this  issue. I want gdm to be automatically  activated during boot. Its a big  pain to manually configure  it everytime I boot. Is it possible to do a  windows restore to set the ubuntu right? But I saw in some forums  mention that something called the boot.ini will botch up if we perform a  system restore in win 7.

Someone pls help me by telling me a method that does not involve   uninstalling ubuntu and reinstalling it. This is because I have done a   lot of tweaks, optimisations and installed lot of apps in it. I do not   have a system image backup as well. So it will be a nightmare to do all   these things over and over again. The mistake or rather the drawback  from my side is I just have my laptop alone and do not have another  standalone desktop to experiment with linux.

---

### Post by jerrrys on 2011-06-23
here is how its done

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

and if its still not right, try

sudo dpkg-reconfigure gdm

this should be safe, but you are running without backup, so use at your own risk.  goodluck

---

### Post by pxs096320 on 2011-06-23
Hi mate!
Thanks for the reply. And that's a strange coincidence because I used the same exact site that you had mentioned to uninstall my kde some 2 days ago. 

So I found myself in this situation after following that sudo command that's given there. So is there any other viable solution buddy?

By the way, I have been manually activating gdm each time the laptop is stuck at the ubuntu logo screen. What I do is I press Cnt +Alt +F1 to enter the terminal mode (tty1), log in and then key in sudo dpkg-reconfigure gdm followed by sudo /etc/init.d/gdm start 
and voila the gnome boots up. 

But this is a bit painful each time I boot. I wish there was a good viable solution to this buddy. Any suggestions to come out of this?:(

---

### Post by jerrrys on 2011-06-23
do you have the same in your default-display-manager?

[ATTACH]195806[/ATTACH]

---

### Post by pxs096320 on 2011-06-23
Hi Jerrys!
Thanks for pointing that out. I checked up my /etc/X11/default-display-manager file. To my horror, the file was blank. Nothing is there. 

So I tried typing out /usr/sbin/gdm as per your screenshot. But it was not allowing me type anything on the file. So I tried copy pasting that from my notepad to that file. But that also didn't work. Then I looked up to find that it was a read-only file. 

Is there a way to edit that file? How do I remove the read only feature of that file to edit it? By the way, just for your info, I am logged in with administrator privileges. So hope that helps you.

Any ideas?:(

---

### Post by jerrrys on 2011-06-23
in terminal **gksudo nautilus**

then you should be able to edit.  be careful what you do while in sudo, you can bork your system with a hasty move

and you need to change to read/write

---

### Post by pxs096320 on 2011-06-23
Hi Jerrys,
Before I saw your reply I did this. Tell me if I am correct. I am scared to reboot my computer until I am dead sure of what I am doing. I got this by googling. Since the default manager file is read only, it appears that we need to use sudo command to edit that file. So this is what I did.

1) I opened the terminal and typed 
sudo vi /etc/X11/[B]default-display-manager

It asked for my password and i keyed it and it sent me into the vi editor 
to edit the file. 

2) I keyed these mentioned below into the file and saved and quit vi editor.
[/B]# FILE : /etc/X11/default-display-manager 
**/usr/sbin/gdm**

Is this alright buddy? It wouldn't botch up the boot up or destroy the 
ubuntu would it? I hope so..KIndly guide me. Just a bit scared of these things. Thats why.

Thanks.

---

### Post by jerrrys on 2011-06-23
that is actually the preferred method among most.

---

### Post by pxs096320 on 2011-06-23
Yippeeeee!!!! So you say what I have done is correct then? Can I go ahead and try rebooting my laptop now? I need the green signal from you. :):)

---

### Post by jerrrys on 2011-06-23
you are cleared for launch

---

### Post by pxs096320 on 2011-06-23
Hahahhaa..ROFL.....Thanks a ton jerrys for helping me out in this...I will reboot and get back to you to inform if the mission was successful.;):D

---

### Post by pxs096320 on 2011-06-23
Er Jerrys!!
Am afraid the problem is still not solved. I am still stuck at the ubuntu log screen with the blinking process bar and I am still having to manually go to the terminal to configure the gdm to start.

Why is this still persisting? Beats me. :(

---

### Post by jerrrys on 2011-06-23
hummm...**/usr/sbin/gdm **its there right?

---

### Post by pxs096320 on 2011-06-23
yes i opened and checked the file manually again. Yes those 2 lines are in tact and indeed there. 

But beats me as to what the root cause of this problem might be.

Drop in anymore ideas. I will check it up tomorrow. Its pretty late night here and a bit sleepy buddy.

---

### Post by jerrrys on 2011-06-23
no, look here

[ATTACH]195813[/ATTACH]

---

### Post by pxs096320 on 2011-06-23
oh ok i will check this up and tell you. Give me a few minutes buddy.

---

### Post by pxs096320 on 2011-06-23
Yes that file is the same as what you have shown in the screenshot for me. I have an idea. Shall I check this file as well? ---> /etc/init.d/gdm  ?

Because while manually starting gdm, I usually sudo to this file and say start. 

So I have a feeling I need to check it too. What do you say?

---

### Post by jerrrys on 2011-06-23
i say right now i need to do a little research.  let me get back to you in a while.  or maybe someone else will step in and give us a hand.  either way, hang in there; there is another launch window comming up

---

### Post by pxs096320 on 2011-06-23
alright i will wait for a few more minutes for you to give the launch window before hitting the sack...eyelids are partially closed...LOl..:D

---

### Post by jerrrys on 2011-06-24
well, found the problem.

when you removed plymouth, you also removed a good portion of the gnome desktop.  you can try to reinstall plymouth and it may even work. but there will still be many other packages broke or missing.

---

### Post by pxs096320 on 2011-06-24
I had already cleaned up all broken packages. So I am sure there aren't any broken packages around. But I will try installing plymouth again and let you know now.

---

### Post by pxs096320 on 2011-06-24
In the meantime, can you list me some of the packages apart from plymouth that might be needed for the proper booting up and functioning of gnome?

Or is there some link mentioning a comprehensive list of packages responsible for booting gnome?

---

### Post by jerrrys on 2011-06-24
no, my package list is different from yours.  just looking at it.  on mine, i would have to reinstall a 100+ packages.  it would be faster to reinstall ubuntu.

---

### Post by pxs096320 on 2011-06-24
As I was waiting for your reply, I just made sure I have all the plymouth packages installed. I rebooted the lap again. But doesn't help still.

Will this problem be set right if I install kde packages once again?

---

### Post by jerrrys on 2011-06-24
no. kde has nothing to do with the problem

---

### Post by jerrrys on 2011-06-24
want to reinstall gnome? it may do the trick.

---

### Post by pxs096320 on 2011-06-24
sorry I didnt see your latest reply. So reinstalling gnome will do the trick? Gosh. How do i do that? Can you just give me some few brief steps so that i will follow it when I go about reinstalling my gnome rather than me doing it in my own haphazard way?

---

### Post by jerrrys on 2011-06-24
just use synaptic pm and use the reinstall option.  you want to reinstall anything labeled [B]gnome-desktop

EDIT  [/B]REINSTALL THE ONES THAT ARE ALREADY CHECKED

---

### Post by pxs096320 on 2011-06-24
Alright i will reinstall gnome desktop related things through synaptic package maanger. But i hope it doesn't cause any new problems or damage to the existing scheme of things

---

### Post by jerrrys on 2011-06-24
it should not remove your personal files, but will probably due away custom system settings.

---

### Post by pxs096320 on 2011-06-24
alright let me try it now.

---

### Post by pxs096320 on 2011-06-24
@Jerrys,
No installing all the gnome-desktop packages did not solve the problem. Each time at boot up it gets stuck at logo screen. When I press Esc at that point to check out what is happening behind the screens, here is what I get. Check out the screenshot.

[IMG]http://i55.tinypic.com/34pclyr.jpg[/IMG] or click this direct link [http://tinypic.com/r/34pclyr/7](http://tinypic.com/r/34pclyr/7).

You can see a list of processes going on at boot and there is a [ok] mentioned after each process on the right side which is not clearly visible from the photo i took. But I can tell you that there was a [ok] after every process but a [fail] after the process by the title "STOPPING AUTOMATIC CRASH GENERATION" says [FAIL] and it ends by saying "Stopping system V run level compatibility"

Hope that gives some idea about the troubles at boot up.

---

### Post by jerrrys on 2011-06-24
reinstall **gdm**

---

### Post by pxs096320 on 2011-06-24
But I just reinstalled the gnome desktop packages right. So wasnt that kind of a reinstallation? Can you tell me a safe way of reinstallation of gdm? Do i do it through the sudo aptitude command or sudo apt command? Briefly tell me the steps.

---

### Post by dino99 on 2011-06-24
please read this howto first:

[http://ubuntuforums.org/showthread.php?t=1205372](http://ubuntuforums.org/showthread.php?t=1205372)

into a terminal:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure -phigh -a
(can be long, so wait it end itself, dont abort it)

---

### Post by pxs096320 on 2011-06-24
Thanks I will try it.

---

### Post by pxs096320 on 2011-06-25
Thanks to everyone who helped me in this thread. I got the gnome clean.

---

### Post by jerrrys on 2011-06-25
glad to hear that, what was the solution ?

---

### Post by pxs096320 on 2011-06-25
I unistalled wubi ubuntu and reinstalled it and reinstalled all the packages and apps again. But I atleast got the gnome back. :)

Thanks for your involvement in this thread all along jerrys. I guess reinstalling was the only straightforward option in the end to clean up the mess and I did just that. :P

---

### Post by jerrrys on 2011-06-25
[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

happy trails :)

---

### Post by pxs096320 on 2011-06-25
wow this link would have been useful for me. But I guess even now, this maybe be useful for me sometime in the future. Thanks anyways.

---

### Post by pxs096320 on 2011-06-25
@Jerrys
If you are free, I would appreciate if you could have a look at my another thread [http://ubuntuforums.org/showthread.php?p=10980375#post10980375](http://ubuntuforums.org/showthread.php?p=10980375#post10980375) and pour in your thoughts in case you have some ideas on it.

Its related to taking a mountable system image of wubi ubuntu and also points like whether a win 7 system restore will affect wubi ubuntu and so on.

---

### Post by jerrrys on 2011-06-25
sorry, its been years since i have ran windows and i have never ran wubi. besides, i have read that thread and your in good hands.  although i do run [something that resembles wubi]("http://www.virtualbox.org/"), may want to give it a try. later

---

### Post by pxs096320 on 2011-06-26
@Jerrys, no problem. Thanks anyways for having a looking at that thread. And yes I have heard of virtualbox. But for the moment, I would want to stick on to wubi. Maybe I will look at virtualbox sometime later.:)

---

