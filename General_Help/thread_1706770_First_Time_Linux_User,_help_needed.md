---
title: "First Time Linux User, help needed"
date: 2011-03-14
forum: General Help
---

### Post by X10A on 2011-03-14
Ok, so I've selected ubuntu as my first Linux experience. And while I want to stay with ubuntu, it's getting rather frustrating.

1) The Evolution mail client doesn't seem to allow multiple, separate email accounts. It just lumps all my emails into one folder, the "inbox" which is really messy. Can anyone advise me how to correct this?

2) It seems that ubuntu has a noticable lag in starting programs, an issue which it is supposed to better windows. My computer is brand new. Does this mean open source isn't as efficient as it is said to be?

3) How do I access the program that controls which OS is chosen on start-up?

4) Is there a way for me to change my user name?

---

### Post by mastablasta on 2011-03-14
> **X10A said:**
> Ok, so I've selected ubuntu as my first Linux experience. And while I want to stay with ubuntu, it's getting rather frustrating.
 
1) The Evolution mail client doesn't seem to allow multiple, separate email accounts. It just lumps all my emails into one folder, the "inbox" which is really messy. Can anyone advise me how to correct this?
 
you need to make new account. and also on the creation you can set where the acocund emails go etc. i have 4 or 5 of them. thoguh now i switched to Thunderbird as it has a bit more options. or at least it has the ones i need.
 
> 
2) It seems that ubuntu has a noticable lag in starting programs, an issue which it is supposed to better windows. My computer is brand new. Does this mean open source isn't as efficient as it is said to be?

this can be for a number of reasons. Linux may have problems compared to Windows, but slowness is not one of them. 
What graphics card do you use? Are propper drivers for it installed? Are the linux drivers for this card good?
 
How did you install your linux? is it via Wubi? If so then that may be causing the slowdown.
 
> 
3) How do I access the program that controls which OS is chosen on start-up?

 
config data is done in grub.cfg. :  
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
 
What are you trying to do?
> 
4) Is there a way for me to change my user name?
 
Yes. i believe it is done in user management.

---

### Post by milindo on 2011-03-14
Someone, please move it to absolute beginner talk(i think.)

> 2) It seems that ubuntu has a noticable lag in starting programs, an issue which it is supposed to better windows. My computer is brand new. Does this mean open source isn't as efficient as it is said to be?

This is weird. Check the System Monitor under System > Administration, and kill any haywire processes. Also, are you using 64bit or 32bit? How much is the ram and cpu?
> 3) How do I access the program that controls which OS is chosen on start-up?
  
This is not clear. Are you running a dual boot with windows? Install StartUp-Manager from the Ubuntu Software center, and try and set the time interval to a larger value in the StartUp-Manager.
> 4) Is there a way for me to change my user name? 
 [http://ubuntuforums.org/showthread.php?p=2845188](http://ubuntuforums.org/showthread.php?p=2845188) is goo. Go to System>Administration>Users and Groups and change the name. 


That's all I can say :P
EDIT: @mastablasta, sorry for any repeats, I was typing  when you posted

---

### Post by btindie on 2011-03-14
> **X10A said:**
> 4) Is there a way for me to change my user name?

Open a terminal and type:
```
$ sudo -i
# sed 's/old_username/new_username/g' /etc/passwd /etc/group /etc/gshadow /etc/shadow
# mv /home/old_username /home/new_username
# exit
$ exit

```log out and back in again.

---

### Post by Kirboosy on 2011-03-14
Welcome to the Forums! :D

> 1) The Evolution mail client doesn't seem to allow multiple, separate  email accounts. It just lumps all my emails into one folder, the "inbox"  which is really messy. Can anyone advise me how to correct this?Under "Edit" in Evolution there should be "Filter Rules". From here you should be able to setup the program accordingly.

> 2) It seems that ubuntu has a noticable lag in starting programs, an  issue which it is supposed to better windows. My computer is brand new.  Does this mean open source isn't as efficient as it is said to be?Open Synaptic Package Manger (System-->Admin-->Synaptic)

In the quick search box type in "preload"

Mark the package for installation and hit "Apply"

That should help with the lag some. 

It also might be a drive issue...If you go to "System-->Admin-->Additional Drivers" Does it ask you to install a proprietary driver?


>  3) How do I access the program that controls which OS is chosen on start-up?For changing GRUB2 to default boot Windows (Since I'm guessing thats what you want)

Open Synaptic Package Manger (System-->Admin-->Synaptic)

In the quick search box type in "Startupmanager"

Mark the package for installation and hit "Apply"

After it installs (shouldn't take to long on your new computer) open it up by going to System-->Admin-->Startup Manager from here you can change the default timeout and the default OS to boot.


Extra side-note since you are new to Ubuntu. I would install [Ubuntu Tweak]("http://ubuntu-tweak.com/") It makes managing some aspects of Ubuntu easier. :)


~Caboose

---

### Post by X10A on 2011-03-14
Ok, thanks to everyone who offered their advice, appreciate it. I guess it's about getting used to ubuntu since this is my first time other than playing around on LiveCD.
 
I'm running on a Lenovo Edge 14, supposedly certified for ubuntu 10.1, i5 processor, 4 GB RAM, 32-bit.
 
I installed ubuntu via a LiveCD.
 
When I say user, I'm referring to the name that is next to the shut down button? That can be changed with those methods?
 
And one more question, I find the ubuntu interface a little cramp. While my resolution is 1300+ x 700+, the ubuntu GUI doesn't look and feel as spacy as the window's one. Is it just me? Or can I adjust that? I've tried tweaking with the display settings but it doesn't seem to help.

---

### Post by Kirboosy on 2011-03-14
> **X10A said:**
> Ok, thanks to everyone who offered their advice, appreciate it. I guess it's about getting used to ubuntu since this is my first time other than playing around on LiveCD.
 
I'm running on a Lenovo Edge 14, supposedly certified for ubuntu 10.1, i5 processor, 4 GB RAM, 32-bit.
 
I installed ubuntu via a LiveCD.
 
When I say user, I'm referring to the name that is next to the shut down button? That can be changed with those methods?

Yes that will change your user name...

> And one more question, I find the ubuntu interface a little cramp. While  my resolution is 1300+ x 700+, the ubuntu GUI doesn't look and feel as  spacy as the window's one. Is it just me? Or can I adjust that? I've  tried tweaking with the display settings but it doesn't seem to help.

You can try changing the Panel Properties (right click on your bar and select properties) You can make the panels slightly smaller.

Are you sure that your display is right because if its slightly off you could feel cramped...

---

### Post by Spyderkid on 2011-03-14
If you are new(ish) to computing or not an expert I Strongly Recommend you leave GRUB alone unless its absolutely necessary....

---

### Post by X10A on 2011-03-15
[QUOTE=Caboose885;10559056]Yes that will change your user name...

 I'm referring to the name under the name in bold, which is slightly transparent.  Another thing is that I've just noticed that after syncing my hotmail account with evolution, my inbox is totally transfered to my computer leaving nothing in my web based account. How do I un-do that.

---

### Post by mastablasta on 2011-03-15
Yes that is your user name - upper right corner next to off button. As suggested, install Ubuntu Tweak it will make things more easier to see and change using a graphical interface.
 
As for Hotmail you should have set it up to leave messages on server. apparently this also needs to be done when you run outlook express in windows for example. It's how POP servers work. to have only image it's best to use IMAP, but hotmail doens't have IMAP.
anyway, what's done is done, so read through this thread for possible solutions:
[http://ubuntuforums.org/showthread.php?t=1458697](http://ubuntuforums.org/showthread.php?t=1458697)

---

### Post by X10A on 2011-03-15
Thanks.  Now I'm trying to install the BOINC client. However, I'm unable to run the shell script to install it.  I get this message:  "gedit has not been able to detect the character encoding. Please check that you are not trying to open a binary file. Select a character encoding from the menu and try again."

---

### Post by X10A on 2011-03-15
Thanks to everyone that answered. I'm getting the hang of ubuntu and liking it more and more.

---

### Post by Kirboosy on 2011-03-15
> **X10A said:**
> Thanks.  Now I'm trying to install the BOINC client. However, I'm unable to run the shell script to install it.  I get this message:  "gedit has not been able to detect the character encoding. Please check that you are not trying to open a binary file. Select a character encoding from the menu and try again."

How are you trying to run the script?

---

### Post by oldos2er on 2011-03-15
> **X10A said:**
> Thanks.  Now I'm trying to install the BOINC client. However, I'm unable to run the shell script to install it.  I get this message:  "gedit has not been able to detect the character encoding. Please check that you are not trying to open a binary file. Select a character encoding from the menu and try again."

Run the shell script in a terminal.

---

### Post by X10A on 2011-03-16
I have no idea how that works. Still very unfamiliar with the back end arrangement of linux. But I got boinc installed already.  Another question which has cropped up is how do I customise my start-up programs? For instance, I want skype to launch on start-up, I know I could use the start-up applications program, but I have no idea how to obtain the program location like in windows we have the address bar at the top of a window.  I've also removed evolution and replaced it with thunderbird. But the envelop icon doesn't seem to have replaced the association and now it doesn't respond. Evolution still appears under applications>office> mail and calendar. Same thing for the chat function under the user name since I've replaced empathy with emesene.  And could someone refer me to a guide to the synaptic package manger. I still feel that ubuntu is rather laggy compared to windows 7. I have the latest drivers and this speed issue still persists.

---

### Post by mastablasta on 2011-03-16
> **X10A said:**
> I have no idea how that works. Still very unfamiliar with the back end arrangement of linux. But I got boinc installed already. Another question which has cropped up is how do I customise my start-up programs? For instance, I want skype to launch on start-up, I know I could use the start-up applications program, but I have no idea how to obtain the program location like in windows we have the address bar at the top of a window.
 
Location is all over the place :-) In linux libraries are shared in windows each porgramme usualyl brings in it's own. thta is why Linux porgrammes are much smaller. Anyway i think if you install **Ubunut tweak** application (found in software center) it will give you more options to set up things via GUI.
> 
I've also removed evolution and replaced it with thunderbird. But the envelop icon doesn't seem to have replaced the association and now it doesn't respond. Evolution still appears under applications>office> mail and calendar. Same thing for the chat function under the user name since I've replaced empathy with emesene.

 
Not sure about Empathy, but evolution (and it's calender) is integrated a lot into the system. so removing it might require a special procedure if that is even possible (it probably is). Since it does't take so much space i just leave it on and mark thunderbird as default e-mail appplication. 
 
> 
And could someone refer me to a guide to the synaptic package manger. 

Guide is in ubuntu documentation or gnome documentation. anyway it seems preety logical to me so i never really went for a guide.
[http://www.nongnu.org/synaptic/](http://www.nongnu.org/synaptic/)
 
note the last picture here: [http://www.nongnu.org/synaptic/action.html](http://www.nongnu.org/synaptic/action.html)
 
Also don't mess too much with individual packages as you can mess up the system. it's better to use software manager if you are nto familiar with packages. or to chekc the packages you plan to uninstall or install on internet first.
> 
I still feel that ubuntu is rather laggy compared to windows 7. I have the latest drivers and this speed issue still persists.
 
It could be the graphics drivers are poor. did you try turning off special effects?
also open the terminal and put in this command:
 
```
top
```
 
you can then post the out put here or see for yourself if any process is taking too much CPU.

---

### Post by Kirboosy on 2011-03-16
> I still feel that ubuntu is rather laggy compared to windows 7. I have the latest drivers and this speed issue still persists. 	

About how long does it take for your computer to start up under Ubuntu?

---

### Post by X10A on 2011-03-17
-ThinkPad-Edge:~$ top  top - 19:49:10 up  1:11,  2 users,  load average: 5.29, 5.47, 5.33 Tasks: 203 total,   2 running, 201 sleeping,   0 stopped,   0 zombie Cpu(s):  6.1%us,  1.8%sy, 83.0%ni,  8.8%id,  0.0%wa,  0.0%hi,  0.2%si,  0.0%st Mem:   3911360k total,  3556712k used,   354648k free,    56252k buffers Swap: 12285948k total,        0k used, 12285948k free,  2060728k cached    PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND              1519 boinc     39  19  776m 745m  612 R  334 19.5 222:17.76 roqs_0.15_i686-      5546 ezeit  20   0  558m 205m  30m S    9  5.4  10:23.50 firefox-bin         20765 ezeit  20   0  433m 114m  21m S    6  3.0  13:13.39 plugin-containe      1151 root      20   0  108m  45m  21m S    4  1.2   5:29.96 Xorg                 2554 ezeit   9 -11  222m 9724 8456 S    4  0.2   1:17.16 pulseaudio          25772 ezeit  20   0  151m  31m  21m S    3  0.8   0:06.73 vlc                 25843 ezeit  20   0 91720  13m  10m S    2  0.4   0:00.71 gnome-terminal       6032 ezeit  20   0  160m  45m  19m S    1  1.2   1:17.10 emesene             25622 ezeit  20   0  204m  50m  22m S    1  1.3   0:28.54 skype                1200 boinc     39  19  9340 4044 3004 S    1  0.1   0:04.12 boinc                  73 root      20   0     0    0    0 S    0  0.0   0:04.75 kondemand/3           548 root      20   0     0    0    0 D    0  0.0   0:00.51 ips-monitor          2559 ezeit  20   0 74936  26m 8464 S    0  0.7   0:57.63 compiz               3271 ezeit  20   0 44224  20m 4768 S    0  0.5   0:08.65 ubuntuone-syncd         1 root      20   0  2880 1748 1248 S    0  0.0   0:00.76 init                    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                3 root      20   0     0    0    0 S    0  0.0   0:00.06 ksoftirqd/0         ThinkPad-Edge:~$

---

### Post by X10A on 2011-03-17
Is there a list that explains the function of each package and which are the appropriate packages to optimise computer performance?  I've gotten ubuntu tweak, but there doesn't seem to be an option to customise start-up programs.  Is there also a program that enables me to limit download speeds on multiple computers on my home network?

---

### Post by nikefalcon on 2011-03-17
> **X10A said:**
> Thanks.  Now I'm trying to install the BOINC client. However, I'm unable to run the shell script to install it.  I get this message:  "gedit has not been able to detect the character encoding. Please check that you are not trying to open a binary file. Select a character encoding from the menu and try again."
It's easier to install BOINC from the official repositories. Just open Ubuntu Software Center and search for and install BOINC Manager.

> **X10A said:**
> 
1) The Evolution mail client doesn't seem to allow multiple, separate  email accounts. It just lumps all my emails into one folder, the "inbox"  which is really messy. Can anyone advise me how to correct this?

As for the email client...I personally prefer Mozilla Thunderbird; maybe you should give it a try. 

> **X10A said:**
> 
3) How do I access the program that controls which OS is chosen on start-up?

Install StartUp-manager, you'll find it in the software center.

---

### Post by Kirboosy on 2011-03-17
> **X10A said:**
> Is there a list that explains the function of each package and which are the appropriate packages to optimise computer performance?  I've gotten ubuntu tweak, but there doesn't seem to be an option to customise start-up programs.  Is there also a program that enables me to limit download speeds on multiple computers on my home network?

You shouldn't really need to install any extra program to control your startup programs. System-->Preferences-->Startup Applications.

Simply uncheck the box on the programs you don't want to start. IE if you don't use Ubuntu One then I would uncheck that box. You can also make custom startup programs from here as well.

---

### Post by SeijiSensei on 2011-03-17
I'm going to make a pitch for dumping Evolution and installing Thunderbird instead.  (sudo apt-get install thunderbird)  I've never liked Evolution; it just feels clunky and designed as an Outlook clone.  Adding multiple accounts in TBird is quite straightforward, and each account has a separate inbox.

As for leaving your mail at Hotmail, there's usually an option in the POP3 configuration that allows you to leave your mail on the server.  (Thunderbird definitely supports this option.) That creates a separate copy of the message in your local inbox, marks the one on the server as read, but doesn't delete it from the server.  Some POP3 servers ignore this option to keep user storage demands under control.  You'll just have to try it out and see if it works with hotmail.

---

### Post by X10A on 2011-03-18
> **X10A said:**
> -ThinkPad-Edge:~$ top  top - 19:49:10 up  1:11,  2 users,  load average: 5.29, 5.47, 5.33 Tasks: 203 total,   2 running, 201 sleeping,   0 stopped,   0 zombie Cpu(s):  6.1%us,  1.8%sy, 83.0%ni,  8.8%id,  0.0%wa,  0.0%hi,  0.2%si,  0.0%st Mem:   3911360k total,  3556712k used,   354648k free,    56252k buffers Swap: 12285948k total,        0k used, 12285948k free,  2060728k cached    PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND              1519 boinc     39  19  776m 745m  612 R  334 19.5 222:17.76 roqs_0.15_i686-      5546 ezeit  20   0  558m 205m  30m S    9  5.4  10:23.50 firefox-bin         20765 ezeit  20   0  433m 114m  21m S    6  3.0  13:13.39 plugin-containe      1151 root      20   0  108m  45m  21m S    4  1.2   5:29.96 Xorg                 2554 ezeit   9 -11  222m 9724 8456 S    4  0.2   1:17.16 pulseaudio          25772 ezeit  20   0  151m  31m  21m S    3  0.8   0:06.73 vlc                 25843 ezeit  20   0 91720  13m  10m S    2  0.4   0:00.71 gnome-terminal       6032 ezeit  20   0  160m  45m  19m S    1  1.2   1:17.10 emesene             25622 ezeit  20   0  204m  50m  22m S    1  1.3   0:28.54 skype                1200 boinc     39  19  9340 4044 3004 S    1  0.1   0:04.12 boinc                  73 root      20   0     0    0    0 S    0  0.0   0:04.75 kondemand/3           548 root      20   0     0    0    0 D    0  0.0   0:00.51 ips-monitor          2559 ezeit  20   0 74936  26m 8464 S    0  0.7   0:57.63 compiz               3271 ezeit  20   0 44224  20m 4768 S    0  0.5   0:08.65 ubuntuone-syncd         1 root      20   0  2880 1748 1248 S    0  0.0   0:00.76 init                    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                3 root      20   0     0    0    0 S    0  0.0   0:00.06 ksoftirqd/0         ThinkPad-Edge:~$

 Is there anyone that can tell me what this means?

---

### Post by Kirboosy on 2011-03-18
All that stuff is simply what processes are running on your computer. Think of it as the Process Manager of Windows. It allows you to see what is currently active and using resources on your system.

---

### Post by X10A on 2011-04-03
> **milindo said:**
> Someone, please move it to absolute beginner talk(i think.)


This is weird. Check the System Monitor under System > Administration, and kill any haywire processes. Also, are you using 64bit or 32bit? How much is the ram and cpu?
  
This is not clear. Are you running a dual boot with windows? Install StartUp-Manager from the Ubuntu Software center, and try and set the time interval to a larger value in the StartUp-Manager.

 
    Ok, I've gotten start-up manager. Among the options, I see two different ubuntu versions, 2.6.35- 28 and 2.6.35- 27. Why is that and what's the difference?

---

### Post by btindie on 2011-04-03
> **X10A said:**
> Ok, I've gotten start-up manager. Among the options, I see two different ubuntu versions, 2.6.35- 28 and 2.6.35- 27. Why is that and what's the difference?
They're different kernel versions. In this case they're both the same version (2.6.35) but the package release number is different indicating that something would have been changed within the packaging of it, probably just a minor change. You can view the package information under synaptic.

---

### Post by PinUpGeek on 2011-05-22
I'm also a first time user and I'm running into ridiculous errors when i comes to using empathy. I forgot my default password or at least it thinks I have. I cannot locate the folder I need to turn it off, because of this empathy has stopped showing my chat lists.


SHould I just uninstall and reinstall it altogether? If so, any walkthroughs on how to do so?

---

