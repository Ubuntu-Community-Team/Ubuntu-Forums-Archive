---
title: "Please help me get back into my 11.04 install. :("
date: 2011-05-21
forum: General Help
---

### Post by Rasa1111 on 2011-05-21
Man... 
 Not what I wanted to do on Saturday...

 I have somehow screwed something up, and now I cannot boot into my 11.04 partition. 

 The only thing I did was used the "enhanced desktop zoom" plugin,
and once it was zoomed in, there was no way to zoom out, So the only way I could get out was to power it down manually. 

 Then upon reboot, 
I got the all black screen, with the little white blinking **_**, and it stayed there for about 2 minutes, then changed to an all purple screen, never to boot into 11.04 desktop. 

What on Earth has happened?
How can I "fix" this so I can boot back into 11.04?

and Can anyone shed some light on this for me? 

I really hope I dont have to reinstall 11.04 and everything for it all over again! :(

Any insight is greatly appreciated. Thanks. 

signed, the super bummed rasa.

---

### Post by linuxinstalledfromhdd on 2011-05-21
you need to boot into recovery mode, and change the password from the root command line.  You are going to need to research that, you still might not be able to get in.

---

### Post by Rubi1200 on 2011-05-21
Hi,
sorry to hear about your troubles.

Can you boot into recovery mode?

What graphics card do you have?

Have you tried adding any boot options to the kernel line from the GRUB menu?

@linuxinstalledfromhdd
> you need to boot into recovery mode, and change the password from the  root command line.  You are going to need to research that, you still  might not be able to get in.     And, why **exactly** would he need to do this???

---

### Post by linuxinstalledfromhdd on 2011-05-21
root command line: passwd <nameofuser>
And then change password. If you are locked out because of your password, then it makes sense to reset it to something else maybe?

---

### Post by Rasa1111 on 2011-05-21
> **linuxinstalledfromhdd said:**
> root command line: passwd <nameofuser>
And then change password. If you are locked out because of your password, then it makes sense to reset it to something else maybe?

No, I'm not locked out because of my password.
What made you think that?

 my password is fine..
I simply cannot even boot into 11.04.  
Something messed up and I can't even get to the login screen.
If it were simply a password issue I could handle it.
Thanks for trying though. 

Rubi, 
Yeah I think I could boot into recovery mode..
But I have no idea what to do once in there. 

in regards to graphics chip..
I don't think it matters..
It's always worked great with any Ubuntu I throw at it.. 
Never had a graphics card issue with this machine.

 10.10 and 11.04 have both been working perfectly..
its just something that had to do with the "enhanced desktop zoom' plugin that screwed me up..
 though i have no idea how..
or how to fix it. 

 thanks for the reply. :???:

---

### Post by Larkspur on 2011-05-21
I'm not technical, but if you've got a LiveCD handy, you could use it to see if you can get into your install and copy the logs and post them here, so more able minds could diagnose the problem.  You could run Disk Utility while you're doing that to see if there are any errors.

---

### Post by mcduck on 2011-05-21
Remember to set a shortcut for zooming out before you use the zoom in. I'm also not sure if using mouse button 1 would work really well for this. I use scroll wheel instead.

Anyway, it's not the Zoom plugin that's stopping Ubuntu from starting, it's not even loaded until you log into desktop. Sounds more likely that the forced reboot broke something. Next time you might want to use Ctrl-Alt-F1 to get into a TTY and shutdown from there, or hold down Alt+SysRq and type R E I S U B slowly for a clean reboot. Alt-SysRq+k is also often a handy shortcut, it resets the current virtual console, so when done in desktop it would drop you to login screen.

The first thing to try for fixing the boot problem would be booting the computer with a live-CD (or USB) and running fsck on your Ubuntu partition. Forced reboot always has the risk of causing filesystem corruption, which could definitely give you booting problems like what you have now.

edit:
If you are able to boot into recovery mode, then you could do that, select the root console option and once there run "touch /forefsck" and then "reboot" to restart the system. It should then check your root partition's filesystem on next boot.

---

### Post by Rubi1200 on 2011-05-21
Rasa, I think something may have got messed up with the graphics. Either that or the hard shutdown may have damaged something in the file-system.

Let's rule out the last possibility by running the boot script please:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

edit: mcduck is probably right and an fsck would be the order of the day. I tend to be more cautious, which is why I would have wanted to see the script results first before suggesting an fsck.

---

### Post by Rasa1111 on 2011-05-21
> **mcduck said:**
> 

The first thing to try for fixing the boot problem would be booting the computer with a live-CD (or USB) and running fsck on your Ubuntu partition. Forced reboot always has the risk of causing filesystem corruption, which could definitely give you booting problems like what you have now.

Hey mcduck, 

 Thanks for the post. 

Quick question..
You say to "run fsck on your Ubuntu partition"

How exactly would I do that?

I mean, i have 2 Ubuntu partitions, The one im on now (10.10), and the 11.04 partition, the one that I broke. 

So how exactly would I run fsck on the 11.04 partition from LiveCD/USB? 

 Ive read some about fsck, but never had to use it. 

Thanks for the post. <3
______________________________________________

> Rasa, I think something may have got messed up with the graphics. Either that or the hard shutdown may have damaged something in the file-system.

Let's rule out the last possibility by running the boot script please:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

Code:
sudo bash ~/Desktop/boot_info_script*.sh
This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

edit: mcduck is probably right and an fsck would be the order of the day. I tend to be more cautious, which is why I would have wanted to see the script results first before suggesting an fsck.

 Thanks Rubi!
 I will try that soon and come back with the results when done. 

I appreciate you guys. Thanks. <3

---

### Post by linuxinstalledfromhdd on 2011-05-21
I would still drop into command line from recovery mode, and install another environment like LXDE or whatever, and then undo whatever you did yesterday that caused this.  I would run a PPA purge if you added something like that, or backtrack what steps you did yesterday until you are able to log back into your other environment again.

sudo apt-get install lxde

You can do that from recovery mode and start lxde from the command line.

---

### Post by mc4man on 2011-05-21
If things aren't working then disconnect the power to the pc, press power button and wait 30 secs or so
Then re-connect power and try again (and if needed boot to bios, then exit, ect.

---

### Post by mcduck on 2011-05-21
Do you know the name of the broken Ubuntu partition? If you do, then using fsck is simple. Just run the following command (using the right partition of course):

```
sudo fsck /dev/sda1
```
(if you do it from recovery mode you don't need "sudo" in the command, as recovery mode logs you in as root)

The partition you check shouldn't be mounted at the time.

If you don't know the name of the correct partition, then you can run "sudo fdisk -l" to list all your partitions, it should be fairly easy to find the Linux partition with same size as your Ubuntu install's root partition is.

---

### Post by mcduck on 2011-05-21
Actually, I just started thinking... Do you have automatic login enabled or do you use the login screen? At what point exactly does the startup freeze, and can you access the TTY's from there (using Ctrl-Alt-F1, for example)?

---

### Post by linuxinstalledfromhdd on 2011-05-21
They may have an encypted home folder with automatic login enabled.. That will cause this to happen too.

---

### Post by Rasa1111 on 2011-05-21
Well boys..
We are back in business! haha! 

I was just getting ready to load up an 11.04 liveUSB,
when I saw **mc4mans** post. 

So I decided since that sounded the most simple..
I would give it a try before doing anything else ...

So I unplugged my laptop, removed the battery, let it sit for a minute,
put the battery back in, turned it on..  chose the 11.04 partition from GRUB,
and She booted right up!
Wow!  I'm soo happy! lol! :D 

Thanks** mc4man**, and thanks **Rubi** and** mcduck**, and **larkspur** & **linuxinstalledfromhdd**! ! 

 I really appreciate your replies and helpfulness! 
You guys are beautiful. (you know, in a "manly" way..) lol 

:KS for all of you! 
many thanks. <3

---

### Post by mcduck on 2011-05-21
Great that you got it working, and that it was such a simple problem in the end. :)

Alt-SysRq-REISUB and Alt-SysRq-K are still worth keeping in mind to avoid such problems in the future. As they are low-level commands that give instructions directly to Linux kernel they tend to work even when pretty much everything else is frozen. [http://en.wikipedia.org/wiki/Magic_SysRq_key]("http://en.wikipedia.org/wiki/Magic_SysRq_key")

---

### Post by Rasa1111 on 2011-05-21
> **mcduck said:**
> Great that you got it working, and that it was such a simple problem in the end. :)

Alt-SysRq-REISUB and Alt-SysRq-K are still worth keeping in mind to avoid such problems in the future. As they are low-level commands that give instructions directly to Linux kernel they tend to work even when pretty much everything else is frozen. [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)


 Thanks my friend!
Yeah, I cant believe it was soo simple! :D

Alt+SysQ REISUB are a combo that I had to remember well when using 10.04. 
I would get random freezes from time to time and those "magic keys" saved me numerous times! 

 I actually even tried that before I did the hard reset.. 
but it didnt do anything. 
Hard reset is always my last resort.. but that was the first time i saw it actually mess something up.  :( 

 Thanks again man. <3

---

### Post by Rubi1200 on 2011-05-21
Excellent! Glad you are back up and running again :-)

And, please, no more hard shutdowns etc. Use the advice posted by mcduck to use the magic key; works a treat every time (usually).

---

### Post by Duncan Williams on 2011-05-21
Also if you can get into recovery mode, try `failsafe graphics' you may be able to get into your 11.04 install from their. (for anyone else that can't get into normal boot)

---

