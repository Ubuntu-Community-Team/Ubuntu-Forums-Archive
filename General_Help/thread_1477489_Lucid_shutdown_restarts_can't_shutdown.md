---
title: "Lucid shutdown restarts can't shutdown"
date: 2010-05-08
forum: General Help
---

### Post by stumped on 2010-05-08
I just updated to 10.04 today and everything is working great except the shutdown. I have looked in these forums and tried everything I found. Nothing is working. Every time I try to shutdown, the computer restarts instead.
I have tried the following:

sudo shutdown -h now
sudo halt
sudo shutdown -P now
sudo poweroff

sudo gedit /etc/default/grub
change : GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to : GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
sudo update-grub
Also tried removing the word splash.

None of these will shut down my computer. The only way to shutdown is to hold in the power button for a few seconds.
This is driving me nuts lol.
Any suggestions?

---

### Post by stumped on 2010-05-08
Anyone:?:

---

### Post by TheNerdAL on 2010-05-08
I seen a lot of people on the forums with this problem. I don't think there is a fix yet but I think it's in the works. 

Just shutdown via terminal until a fix is released. :)

---

### Post by ranch hand on 2010-05-08
Welcome to the wonderful world of plymouth.  Removing splash from your menu entry will probably help boot a little bit.

As for shut down, good luck.  Remember Alt+SysRq+b will send you into reboot and if you wnat to shut down you can hit the power button when the menu comes up.

I hope this is fixed soon.  File a bug;
```

ubuntu-bug libplymouth2

```
You need a Launchpad account that is easy to set up when you are redirected there by the above command.  Be sure to check the listed bugs carefully, I am sure one will fit your conditions.

The more bugs filed the sooner it will be fixed or plymouth replaced.

---

### Post by stumped on 2010-05-09
Thanks guys. I can not shut down with the terminal, or any other way at all, except for holding in the button for a couple seconds. I will file a bug report.

---

### Post by leona on 2010-05-09
Well I updated this week.
I did my notebook first, as I wanted to test it before I did my main machine, if it trashed it, it wouldn't matter, but no it seemed to go ok.
I still notice a few problems, wifi isn't perfect, it seems to come and go as it likes, yet if I boot into Windows XP its stable, so still Wireless problems, when will LInux ever have this sorted?
Anyway I thought it was stable enough to update my mahine machine.
Did this the same way, ie clean install, after a backup, all goes well.
I noticed a few icons broke, like Firefox.  There seems to be a bug when trying to switch users, if I try to do so, it locks up, if I log out, it locks up, so that's not good.  I was on 8.04 before, the Log out button used to give me 6 options, Log out, shutdown, etc, now I only get shut down, no log out option, I have to use a different 'Applet' to give me these option (that don't work anyway). oh well. I'll see if I can file a bug, though this system seems incredibly complicated!

---

### Post by stumped on 2010-05-09
I have filed a bug report. I can't shut mine off no matter what I try, except for the main button. If so many people have this problem, then I would hope there would be a fix soon.

---

### Post by Locke2053 on 2010-05-14
I had this problem, but it went away after I updated this morning and restarted (from console).

I have had a LOT of problems (bluetooth, nvidia, etc.) coming and going with every update to Lucid so far. I think that for the next version of Ubuntu, I'm not going to upgrade until a few weeks after the release. It seems there is still a boatload of QA going on.

---

### Post by stumped on 2010-05-15
I have done all the updates. I even did a complete reinstall, and all the updates again. I still have this problem. If I do "sudo shutdown -H now" It will shutdown to the ubuntu logo and freeze there. I still have to hold in the power button to shutdown completely. Everything else with Lucid works great.

---

### Post by Rusty~ on 2010-05-18
Press Ctrl+Alt+F2, login as super user (sudo su) and execute 'poweroff'.

It should fix the problem.

Rusty~

---

### Post by stumped on 2010-05-22
> **Rusty~ said:**
> Press Ctrl+Alt+F2, login as super user (sudo su) and execute 'poweroff'.

It should fix the problem.

Rusty~

This also does not work. It just restarts, instead of shutting off.:(

---

### Post by Rusty~ on 2010-05-28
> **stumped said:**
> This also does not work. It just restarts, instead of shutting off.:(

Did you do that from console (Ctrl+Alt+Fx) ?

---

### Post by stumped on 2010-05-29
> **Rusty~ said:**
> Did you do that from console (Ctrl+Alt+Fx) ?

(Ctrl+Alt+Fx)??
I have done (Ctrl+Alt+F2) then loged in as super user (sudo su) and executed 'poweroff'

I have tried everything I have found posted on the net. No matter what I do it just restarts and does not shut off unless I hold in the power button.
I have even done a fresh install twice, with no change.

---

### Post by Georgia boy on 2010-05-31
I too am having this problem. It seems to be a hit and miss with my system though. I was having the shut down problem the it went away so I thought that maybe one of the many updates had fixed it. Wrong. Started again today. Had to force shutdown by using the power button. So far I've only had two real problems with Lucid. One is this shut down problem that comes and goes and the other is that I have to do a Sudo service cups start to get my printer to reappear again so I can do some printing. I don't have a webcam nor anything like that to give me problems. Just a simple Desktop PC. But these two problems are enough to P*** off the pope at times. Especially when you're in a hurry and want to print something and wind up doing the sudo service cups start or if you're wanting to go somewhere and try doing a shut down only to have it want to do a restart instead no matter how many times you tell it to shut down, you wind up doing a "push the button" routine.
I know that a great many others have been having these problems and that many bug reports have been filed. I know that the printing problem has been moved from medium to high. Don't know about the shutdown. Probably the same thing has happened with it too. I'll be happy when a fix comes out for them and we get the updates for them.

Tom

---

### Post by simplematix on 2010-06-03
Hi When i saw the new Lucid update i was thinking lets do it after a few weeks, but my temptation was to upgrade straight away. Eventually i succumbed and updated, and 'am now stuck with a few problems. I cannot logout,restart or shutdown. wicd-client does not start on login, so i have to go to a terminal window, and start wicd-client. Funnily i have another account for my son, and every thing works fine from his account. My only guess is that since i upgraded from my account i am having all the shutdown issues. Howeever, as some of you had suggested, i  can go to a console login ctrl+alt+f2, and do a poweroff, which powers down the system.

---

### Post by Georgia boy on 2010-06-08
Still no fixes for this problem is there? It's been an on and off problem with me lately. Sometimes it works like a champ and others I have to hit the power button to do a shut down. 
Guess they're still working it?

Tom

---

### Post by sanso on 2010-06-12
This is the same on my gf's Toshiba Equium. 
Any news here would be highly appreciated.

:)

Richard

---

### Post by stumped on 2010-06-30
Almost 2 months now and I still have this problem. :cry: :confused:

---

### Post by jglen490 on 2010-07-04
Bad edit.

---

### Post by jglen490 on 2010-07-04
I have filed a bug (598674) on this same problem.  Pile on, if you'd like :D. The more people with the same problem, the more likely it will get the attention this problem deserves.  It's not right for a "poweroff" to behave the same way as a "reboot".

I use alt+sysrq+reisuo to shutdown to a powered off state after using the K->Leave->Shutdown menu selection in KDE.  I've tried all the other combinations of ctl+alt+del, sudo shutdown -P now, sudo init 0, and others.  None of them work except the so-called magic key sequence alt+sysrq, etc.

---

### Post by stumped on 2010-07-07
I also filed a bug. Still nothing. ](*,)

---

### Post by salaba on 2010-07-17
I also have this problem. And even worse. When I hand on the power button to shut it down. Then when I release the power button, it will restart.

---

### Post by swalker23 on 2010-07-17
Just to add to the topic I too have this problem.  Started during launch and after a several updates it started to work properly.  Then down the road more updates and its back.  Have to shutdown via console.

---

### Post by stumped on 2010-08-01
salaba,
hold the button in for a couple seconds. If I just push it and let go, mine will just restart also. Just hold it in until it is shut down completely.

Still not fixed yet. :mad:

---

### Post by getglenn on 2010-08-29
I have been tracking this thread for a while, but i have the opposite problem...

i can shutdown using the desktop icon, but choosing 'restart' just causes a 'shutdown'

[which sometimes seem to be 'unclean' in that when i reboot there are some error messages and checking done before the system mount correctly]

---

### Post by stumped on 2010-09-12
I re-downloaded 10.04 on to a disk and installed it on a friends computer.
Just for fun I also re-installed it on my computer.(fresh install on both)
My computer still has this shutdown problem.](*,)
My friends computer shuts down perfectly like it should.:smile:
Why would it work perfect on one computer and not the other? 
Does this mean that its not the program (ubuntu 10.04) thats the problem, but the computer itself? 
Does this mean that all of us that have the shutdown problem have the same problem with the computer itself?

---

### Post by stumped on 2010-10-31
I can't believe nobody has found a solution to this problem.
If they have, please point me to it as I still need to hold in the power button to shutdown.

---

### Post by MorrisLL on 2010-11-06
Me too.
Dell Latitude D600.
Some added info:
Panel speaker icon has "---" instead of "))".
System/Administration/Users and Groups: can't change "Account Type" and "Advanced Settings" button will not bring up the list.
System/Preferences/Sound: "Hardware" tab shows no devices.

Seems to be a 'rights' issue?

Also this issue seems to be intermittent irregardless of 'updates'.
:popcorn:

---

### Post by MorrisLL on 2010-11-06
Also: Running Lucid Lynx 10.04, dual boot with WinXP.
Another sign of this condition was the lack of 'bongos' sound at startup.

---

### Post by MorrisLL on 2010-11-06
Folks,
This seemed to fix this condition for me, so far. This is what I did, and what transpired;
1. held PWR button till off.
2. on grub restart, I selected 2nd option "Repair".
3. ran 'dpkg'
4. after 'dpkg' completed selected 'resume normal'.
5. my machine 'hung' on "Checking battery state". After a few minutes, used <CTRL/ALT> DEL to bug out.
6. machine proceeded to boot normally (grub).
7. let timeout to Ubuntu.
8. system sound (bongos) back, and Ubuntu is working just great. Every thing is back.
Hope this helps you folks, and may help support gurus if this is a persistent problem, or a freak occurrence (?).

---

### Post by MorrisLL on 2010-11-08
Did it again this morning.
I repeated the same steps as in previous post, with the addition of 'Grub Update' after 'dpkg'.
Note: This time it did not hang on 'Checking Battery State'.

All seems well at the moment. :P

---

### Post by stumped on 2010-11-10
I just tried your idea MorrisLL, but no luck.

Went to recovery mode, ran dpkg, ran grub update, then resume normal.
Everything went smooth with no hang ups, but didn't work.
It still just restarts instead of shutting off. :cry:

---

### Post by robert shearer on 2010-11-10
I am assuming you have seen and tried rseiub
[http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/](http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/)

This, however, reboots a system.

So instead try the sequence but substitute O for B  ('**O**ff' instead of '**B**oot')       = **rseiuo** and post back the result.

---

### Post by stumped on 2010-11-11
I have not seen that before but just tried it.
The rseiuo method did not work.
All it did was restart instead of shutdown. (yes I used O instead of B)

---

### Post by stumped on 2010-12-11
Wow!
7 months and still no fix.
Thanks to all that tried, but I'm still having this problem.

---

### Post by robert shearer on 2010-12-11
> **stumped said:**
> Wow!
7 months and still no fix.
Thanks to all that tried, but I'm still having this problem.

just out of curiosity,
 in your BIOS what is set for "action after power off" (or some such option) ??.
If it is RESTART then maybe change it to OFF ???

---

### Post by stumped on 2010-12-13
The closest setting to "action after power off" that I have is "auto turn on" and it is disabled.
There is nothing else in the BIOS that I can see that would affect the shutdown or turn on. Also I have not had this problem with previous versions of Ubuntu. It only started with 10.04.

---

### Post by MorrisLL on 2010-12-14
Well for the record with this Dell D600 and LL10.02:
My problem with restart instead of shutdown has resurfaced multiple times, since my last post. Each time I would 'fix it' only temporarily.

However, after the last program updates from ubuntu, it seems to have moved the right bytes into alignment. It's been days now and appears to work as intended.
For what it's worth.:)

---

### Post by hedgefighter on 2010-12-23
I have the same problem with Ubuntu 10.04 and 10.10. I even reinstalled both. With a fresh install I cannot suspend, hibernate, or shutdown. The instant the computer shuts down, it powers back up again. No error messages or anything. I know it's an Ubuntu problem because it shuts down from Windows just fine. It's immensely frustrating!

---

### Post by stumped on 2011-01-16
Anyone else with any suggestions?

---

### Post by stumped on 2011-01-16
Anyone else have any suggestions?

---

### Post by saraSupernova on 2011-02-15
> Anyone else have any suggestions?Hi. 
I assume you're using notebook as I had this problem recently.
This problem happened after resetting my 10.10 to default as a change is made 
and I don't know how to undo it.
What I did was unplug the power plug while the battery remain inside, then shutdown normally.
and . . it shuts down.
I'm dying to know why though

---

### Post by stumped on 2011-02-26
No again. I am using a desktop. Not a laptop.

---

### Post by Tech-me on 2011-02-28
Same problem here. I have 10.10 on Gateway laptop, fresh install from USB stick. No other OS on the machine. I have to hold power to fully shut off. Doing some updates now to see if that helps.

---

