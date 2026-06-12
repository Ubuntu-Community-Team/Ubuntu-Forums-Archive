---
title: "grub menu"
date: 2010-11-10
forum: General Help
---

### Post by charliet on 2010-11-10
My son gave me this gateway comp but couldnt remember the work password. I went on line and ask how to get around work password. I went into grub recovery mode and got root@work:~#. I typed in passwd user name, changed the password and confirmed, then got "root@work~"' again. when i typed in exit,it didnt go back to grub menu to reboot. all i got was a bunch of jibberish and then root@work again. i finally manualy shut it down and turned back on and it boots to work login and when i click on username and type in the new passwrd it says authentication failure. when i reboot to get into grub menu again i dont get a grub loading prompt. what have i done and how do i get past the user passwrd?

---

### Post by coffeecat on 2010-11-10
It sounds as though you were on the right lines, but...

> **charliet said:**
> I typed in passwd user name

That should have been 'passwd *username*, substituting the account name for *username*. Is that what you did?

> **charliet said:**
> when i typed in exit,it didnt go back to grub menu to reboot. all i got was a bunch of jibberish and then root@work again

At the # prompt you need to type 'reboot'.

Anyway, follow this guide:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

It includes how to discover the user account name as well.

---

### Post by charliet on 2010-11-10
I didwhat the link said to do and it would not exit to grub menu. now i cant get into grub menu entering esc or shift either one. if i could get into the grub menu i would try again to enter a new passwd.

---

### Post by coffeecat on 2010-11-11
> **charliet said:**
> I didwhat the link said to do and it would not exit to grub menu.

Where the guide says to type exit, that is not to get to the grub menu. That's a special menu which is part of the recovery mode. The grub menu is the boot menu which you get when you first switch the computer on.

> **charliet said:**
>  now i cant get into grub menu entering esc or shift either one. if i could get into the grub menu i would try again to enter a new passwd.

When are you pressing esc or SHIFT? If you have reset the password you should not have to reset it again. Switch on the computer. You will see something called the POST (power-on self-test) screen. This will either be some text telling you about the hardware or a manufacturer's splash screen. After this you should see the grub menu which gives you a choice of booting normally with a title something like, 'Linux 2.6.xx-y'. booting into recovery mode or booting into the memtest. There may be many more menu entries if there have been several kernel upgrades. Only if the grub menu is set to be hidden will you need to press esc or shift. After this the machine should boot into the first grub menu choice if you don't select anything or whatever you select.

If you switch on the machine and leave it, what do you see? What happens? About how old is the computer? Do you know which version of Ubuntu is installed on it?

---

### Post by charliet on 2010-11-11
The grub menu is hidden. I have always had to press esc when the grub slpash showed, that is until i screwed it up. Now i dont get the grub splash on boot. the comp is an old gateway 32 bit. when i let it boot on its own it boots to a window that says work with two user names and other. the system is ubuntu 9.10. I feel like i may have typed in something wrong when i was in root user. by the way thanks for your responses. you can probably tell i am comp iliterate.

---

### Post by coffeecat on 2010-11-11
If we can get you into recovery mode again, we can sort out all these problems, but first a couple of things.

> **charliet said:**
> The grub menu is hidden. I have always had to press esc when the grub slpash showed, that is until i screwed it up. Now i dont get the grub splash on boot.

If you mean by splash, some sort of design that covers all or most of the screen, that's nothing to do with grub. But if you mean a little text message in the top left that says something like 'Grub loading. Press ESC for menu" or words to that effect, then that will be most useful. Did you ever see a message inviting you to press ESC? That's important. It will help us to determine which version of grub you have, which will help in knowing what to do next. If you were able to get the grub menu with esc then that would be what is known as legacy grub. However, Ubuntu 9.10 when installed fresh came with a later version of grub called grub2. But Ubuntu 9.10 upgraded from an earlier version would have legacy grub. Sorry to bombard you with information, but if we can find out what us going on we might be able to solve this.

Next thing - nothing you did is likely to have "screwed up" grub. Be assured. :)

> **charliet said:**
> when i let it boot on its own it boots to a window that says work with two user names and other.

That sounds like the log in screen. I guess 'work' would be the computer name. The two user names will be two accounts. If we can get back to the recovery console you will be able to reset passwords for both accounts so that you can login.

OK - that's just the preamble. Let's see if we can achieve something. :)

FIRST. The reason the grub menu is not showing when you press ESC is that you only have a couple of seconds and you have to press it at exactly the correct time. Try this. Switch on the computer and hold the ESC key down immediately. Keep it pressed. If you get the grub menu all well and good. If it misses the grub menu and boots to the login screen, reboot. This time as soon as you switch on, keeping pressing the ESC key repeatedly, a bit like a woodpecker, although not so fast and not so vigorously. Hopefully, that will get you a key press at the right moment.

If you do see the grub menu, choose recovery mode. At the next recovery menu choose 'drop to root shell' and follow that Psychocats guide I linked to reset the password for **both** accounts.

If you can't get the grub menu, the next step is to boot up with a live Ubuntu CD and edit the grub configuration menu so that it is not hidden. Question: do you have an Ubuntu live CD of any version? If not, do you have good broadband? The reason for asking is that you may need to download a CD image (it's free) of about 700MB which is not feasible with old-style landline dial-up. Last question: if you need to download a CD image, what operating system will you be using, Windows or MacOS?

---

### Post by charliet on 2010-11-11
I did get into the grub menu by pressing the shift key. I successfully changed the passwrd. I typed in my user name and new passwd and it booted to [EMAIL="username@work:~$"]username@work:~$[/EMAIL] what do i do now? This the first time I have been into Ubuntu.

---

### Post by coffeecat on 2010-11-11
> **charliet said:**
> I did get into the grub menu by pressing the shift key.

Which means that you have grub 2 and Ubuntu 9.10 must have been installed as a fresh install, not an upgrade from a previous version.

> **charliet said:**
> I typed in my user name and new passwd and it booted to username@work:~$ what do i do now? This the first time I have been into Ubuntu.

You mean you are getting a text screen against a black background with no GUI? Hmmm. I could give you some commands to try but I think it would be best to ask your son whether the system was working when he last used it, and did he know it was broken? Ubuntu, that is, not the computer.

We could spend some time trying to fix it, but not knowing what condition the installation was in when last used might mean we could be chasing moonbeams for a long time. Or it could be easy to fix. It's difficult to say at this stage. So - you might want to think about doing a fresh installation of a more up-to-date version of Ubuntu. That way you'll get a system that works and you'll have the satisfaction of installing it yourself which, believe me, is easier than you might think.

Post back with what you want to do and we'll take it from there.

By the way, I probably won't be able to post again for about 14 hours, but I have got this thread subscribed.

---

### Post by charliet on 2010-11-11
yes i have text against a black background. as far as i know he was using it  when he gave it to me because he said his other one had a virus. I wont get to talk to him until tomorrow afternoon or evening. I downloaded Ubuntu 10.10 to a cd but i cant get it to run. I put the disk in then reboot but the comp dont see it. I put it into my other computer w/windowsxp it doesnt see it either. I go into d drive to open it and it sends me to internet explorer and it sends me back to d drive.. its one big circle. Ill leave ubuntu where its at until we figure somthing out. thanks again.

---

### Post by wilee-nilee on 2010-11-11
> **charliet said:**
> yes i have text against a black background. as far as i know he was using it  when he gave it to me because he said his other one had a virus. I wont get to talk to him until tomorrow afternoon or evening. I downloaded Ubuntu 10.10 to a cd but i cant get it to run. I put the disk in then reboot but the comp dont see it. I put it into my other computer w/windowsxp it doesnt see it either. I go into d drive to open it and it sends me to internet explorer and it sends me back to d drive.. its one big circle. Ill leave ubuntu where its at until we figure somthing out. thanks again.

Make sure you burn the cd as a image and not a data write. In Windows it is just a right click on the ISO and burn to cd.

Also check the md5sum, notice there are instructions on doing this in windows, or linux, or a mac.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Now back to coffeecat's help.;)

---

### Post by coffeecat on 2010-11-12
> **charliet said:**
> I downloaded Ubuntu 10.10 to a cd but i cant get it to run.

When you say you downloaded Ubuntu to a CD, do you mean that you downloaded an ISO file and then burnt that to a CD? If so, wilee-nilee's comment about burning as an image is important. More here,and details of free Windows burning software if you are having difficulty with your burning software:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Also, did you download the 32-bit or 64-bit ISO for Ubuntu? If the 32-bit (it has 'i386' in the filename) then you'll be OK on old or new machines. If 64-bit (with 'amd64') in the filename), this will only work with 64-bit processors. If the computer is more than 2-3 years old, it may have a 32-bit  processor.

> **charliet said:**
>  I put the disk in then reboot but the comp dont see it. I put it into my other computer w/windowsxp it doesnt see it either. I go into d drive to open it and it sends me to internet explorer and it sends me back to d drive.. its one big circle.

There's certainly something wrong with the CD. Even if you had burnt it as a data write, Windows XP would see it and show you one big ISO file.

Check that you've got the correct ISO file - it should be 'ubuntu-10.10-desktop-i386.iso' and is about 690MB. Check the md5sum according to wilee-nilee's link, and if that is correct burn a new CD following the link I've given. You may now have to set the BIOS in the Gateway to boot from CD first. The POST screen, when you first turn on, should tell you which key to press to get into the BIOS. It could be delete or F2 or almost anything. In the BIOS you can set the machine to boot from the CD before the hard drive. Then you'll be able to boot into an Ubuntu live desktop with the CD you've burnt. This will not affect anything on the computer at all. It will leave your Ubuntu 9.10 untouched unless you start the installer. This will give you an opportunity to explore the Ubuntu 10.10 desktop before committing yourself to an install. Be aware that from the live CD it will feel very sluggish. It will be much brisker when installed.

---

### Post by charliet on 2010-11-12
I have not been able to get ahold of my son so lets go on the assumption that it was working when i got it. i believe that is what he told me. as far as the cd it is an image cd. after sitting in the same window for 24hrs a command came after [EMAIL="username@work:~$"]username@work:~$[/EMAIL] *reloading common unix printing system: cupsd.

---

### Post by coffeecat on 2010-11-13
> **charliet said:**
> after sitting in the same window for 24hrs a command came after username@work:~$ *reloading common unix printing system: cupsd.

Before I give you some commands to try to get the GUI up, when you are confronted with the 'username@work:~$' prompt and you want to shut the machine down, use this command:

```
sudo shutdown -h now
```Be careful not to make any typos. You have to be 100% correct when typing terminal commands. It will prompt you for your password, and nothing will seem to happen when you type it in. The password is going in. I give you this because it is safer than doing a hard shutdown by simply switching the power off.

Anyway, to try to start the GUI. Try this first:

```
startx
```If nothing happens, one of these might work. Try each in turn.

```
sudo service gdm start
sudo /etc/init.d/gdm restart
sudo start gdm
```The first time you use a command prefaced with 'sudo', you will be prompted for your password.

---

### Post by charliet on 2010-11-13
Startx worked. I got a brown screen w/a whit bar @ top words applications   places  system the world and a ?. On the screen is firefox browser  a star  brasero. @ the bottom update mngr. I will probably need somekind of on line tutorial. This is new to me. Will i use the cmd u gave me to shut dwn?

---

### Post by coffeecat on 2010-11-13
That's the Ubuntu desktop you're describing, so good news that startx worked. The white bar at top is the upper panel and the Applications/Places/System set is the main menu, sort of akin to the Windows start button where you can find all your applications and system utilities. However, I don't know why Firefox and Brasero were both open on the desktop. There should be no open applications when you first get into the desktop. If this persists we can investigate further.

If you still have the desktop up, to shutdown or reboot there should be an icon at top right (the standard on/off switch design). Click on that with the mouse and you should be presented with a shutdown, restart, etc choice. The command I gave is to use at the terminal.

What is still unexplained is why the system didn't boot into the graphical desktop to start with and you had to do the command 'startx'. Close Firefox and Brasero by clicking on the X buttons (just like in Windows) and try booting up again. If you get the command line again, do the 'startx' command again, but we might be able to fix that.

---

### Post by charliet on 2010-11-13
I clicked on shut down and it didnt completely shut down. it went back to my [EMAIL="username@work:~$"]username@work:~$[/EMAIL]. text w/black background. also what is the little brown box that moves around the screen?

---

### Post by coffeecat on 2010-11-14
> **charliet said:**
> also what is the little brown box that moves around the screen?

I have no idea. Can you describe it some more? Does it move with the mouse, or does it move on its own?

---

### Post by charliet on 2010-11-14
its a little square brown box when u click on a command it turns white over part of the cmd u just clicked on. I have another problem now. after I posted my last thread I was going to bed for the night so I thought this would be a good time to install updates so I clicked on update mgr and then install updates. the screen turned dim and a square white box poped up in the middle of the screen and now it is locked up. do I dare do a hard shut dwn. although I dont see any other choice. oh the white bow is probably 3 X 4 inches in size.

---

### Post by coffeecat on 2010-11-14
> **charliet said:**
> its a little square brown box when u click on a command it turns white over part of the cmd u just clicked on.

I really don't know what that is. I don't believe I've seen anything like it.

> **charliet said:**
>  I have another problem now. after I posted my last thread I was going to bed for the night so I thought this would be a good time to install updates so I clicked on update mgr and then install updates. the screen turned dim and a square white box poped up in the middle of the screen

Was the white box prompting for a password? You have to authorise updates and some other things with your password. However, the account you are using must have administrative rights. I remember you said that there were two accounts. It is quite probable that one was the administrative account and one did not have administrative rights. You might need to try both accounts. And, of course, you'd need to have reset the password for both in the way we covered early in the thread. Did you reset the password for just one account or both?

> **charliet said:**
>   and now it is locked up. do I dare do a hard shut dwn. although I dont see any other choice. oh the white bow is probably 3 X 4 inches in size.

A hard shutdown risks damaging the filesystem. Indeed, I wouldn't be surprised if something isn't already damaged already because a normal installation of Ubuntu should take you to the graphical login window, not to a text $ prompt where you have to do 'startx'. Which was why I was earlier suggesting a clean install of a later version.

If you are confronted with a completely locked system which doesn't respond to either mouse or keyboard, try this. Hold down the Alt and the PrintScreen/SysReq keys and keep them held down while you press the following sequence of keys one after the other about a second or two apart: R E I S U O. That will cause the system to close all processes, unmount filesystems and shutdown gracefully. On some systems Alt+PrintScreen doesn't work and you have to use the AltGr key to the right of the space bar. That's AltGr+PrintScreen.

---

### Post by charliet on 2010-11-14
I have reset the passwds for both accts. I shut dwn with the alt print screen and typed reisuo then turned back on it went to work window with both user names. I selected one and typed in its passwd and it went straight to desktop. I tried upgrades again and the same thing happened. It doesnt ask for any passwd. I havnt tried upgrade yet.

---

### Post by coffeecat on 2010-11-14
> **charliet said:**
> I selected one and typed in its passwd and it went straight to desktop.

That's good news.

> **charliet said:**
>  I tried upgrades again and the same thing happened. It doesnt ask for any passwd. I havnt tried upgrade yet.

Try logging into the other account. If it doesn't ask for a password when you try to update, that account probably doesn't have administrator privileges.

By the way, don't try an upgrade to 10.04 just yet. The update manager might prompt you for this. An upgrade to a later version usually works OK but just occasionally things go wrong. It might be as well to acquaint yourself with the system and be sure it is working properly before you do an upgrade to a newer version. Routine updates for now only - I suggest.

---

### Post by charliet on 2010-11-14
I logged in as other user and on the bottom left it said untitled window instead of update mgr.

---

### Post by coffeecat on 2010-11-15
> **charliet said:**
> I logged in as other user and on the bottom left it said untitled window instead of update mgr.

If you mean after you started update manager from the System window then that shouldn't happen. 

Going back to when you tried to run update manager from the first account, you didn't confirm whether or not the white box was prompting for a password. Whatever - the other thing to check is whether you are connected to the internet. Update manager cannot work without an internet connection. Having said that, the freeze you described is not what happens when update manager tries to work without an internet connection.

A final thought: we've solved the original problem of the grub menu and you can now boot into a graphical desktop. You are encountering a number of issues for which you need help, but the thread title refers to the grub menu. It would be best if you started a new thread with a descriptive title for the problems you are now encountering. This will attract several forum members all of whom may be able to help and give different perspectives. Also, you may find this useful:

[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

It describes the version of Ubuntu that was released after yours, but it will still be helpful. Much will be the same.

Good luck!

---

### Post by charliet on 2010-11-15
ok thanks for all your help. u got me farther than i evr thought i would. I do have other issues. I try to runa klamav virus scan and it says it cant acces denied. ill try another thread. thanks again.

---

