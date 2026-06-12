---
title: "Boot to Windows from Ubuntu Without Making Selection in Grub"
date: 2006-05-03
forum: General Help
---

### Post by debonair23 on 2006-05-03
Is there a way to specify that I want to reboot into windows when shutting down ubuntu so that I do not have to be present to select windows from the bootloader menu when the computer restarts? I don't want to reconfigure grub to always boot windows instead of linux, I want it to be a one time thing.

---

### Post by sYs^ on 2006-05-03
It would be a great idea to create a shortcut named "Reboot to Windows" and while your system is rebooting you wouldn't have to wait for grub, you could go to drink something for example, lol :D

But I don't have any idea how should we do this :D

---

### Post by zxee on 2006-05-03
It's an interesting idea, and perhaps the developers at grub might consider it-if enough people let them know they're interested [http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/) I don't believe what you want is currently possible with grub (grub2 is being developed) Perhaps smartbootloader or some other bootloader might have it.

---

### Post by Slim Odds on 2006-05-03
[QUOTE=debonair23]Is there a way to specify that I want to reboot into windows when shutting down ubuntu so that I do not have to be present to select windows from the bootloader menu when the computer restarts? I don't want to reconfigure grub to always boot windows instead of linux, I want it to be a one time thing.[/QUOTE]

Exactly how do you think this could be done?

The boot loader allows you to decide which operating system gets loaded. If Ununtu modified the boot configuration to boot straight into Windows, how would you get back to Unbuntu when you reboot out of Windows?

---

### Post by debonair23 on 2006-05-03
[QUOTE=Slim Odds]Exactly how do you think this could be done?

The boot loader allows you to decide which operating system gets loaded. If Ununtu modified the boot configuration to boot straight into Windows, how would you get back to Unbuntu when you reboot out of Windows?[/QUOTE]

Well there could just be an extra config option in the grub settings...

NormalLoad = Linux
**ThisLoad = Windows**

When you go to reboot, it will append that variable to the config. During booting it will wipe that variable. When you go to restart from windows it will just see the normalload and go to linux.

---

### Post by Slim Odds on 2006-05-03
[QUOTE=debonair23]Well there could just be an extra config option in the grub settings...

NormalLoad = Linux
**ThisLoad = Windows**

When you go to reboot, it will append that variable to the config. During booting it will wipe that variable. When you go to restart from windows it will just see the normalload and go to linux.[/QUOTE]

Do you see any inherent danger in having grub modify it's configuration files during the boot process? I do.

Also, what's the big deal with simply selecting the operating system each time? That's not exactly painful.

---

### Post by Jose Catre-Vandis on 2006-05-03
What if you are running a headless dual boot server, this is when this functionality would come in handy (although don't ask me why you would do this :-D). With the right software on windows could you reedit the grub to boot back into Ubuntu?

---

### Post by Demon012 on 2006-05-03
Hold on I swear this has been done before I think this was in SuSe Linux. You had to hold left mouse button on the restart button in the shutdown menu and it gave you the option to boot to another operating system on your computer.

May not have been SuSe but it had a little crocodile picture on the menu I am sure of it.

So don't worry guys it has been done but we need to figure out how to do it in ubuntu.

---

### Post by debonair23 on 2006-05-03
[QUOTE=Slim Odds]Do you see any inherent danger in having grub modify it's configuration files during the boot process? I do.

Also, what's the big deal with simply selecting the operating system each time? That's not exactly painful.[/QUOTE]

Actually I don't see the danger... I'm not claiming to be a programmer or anything, thats why I'm asking the question. Someone asked for my thoughts so I gave them.

As for the problem with selecting the OS, I'm running Ubuntu on a business computer to speed up work, but I switch to windows to play games at lunch. When I want to go to windows, I have to sit here and wait literally two minutes for it to reboot and get back to the boot loader where i select the OS. It would be nice to have this done automatically so I could go and do other things really quick.

---

### Post by glotz on 2006-05-03
I think this is a good idea. And it'd make double or multi booting easier, which will in turn encourage people to try Linux. Babysitting the computer is very annoying. Every second counts!

---

### Post by debonair23 on 2006-05-03
[QUOTE=glotz]I think this is a good idea. And it'd make double or multi booting easier, which will in turn encourage people to try Linux. Babysitting the computer is very annoying. Every second counts![/QUOTE]

I agree :) I was originally seeing if this had been or could be done, but i guess now its turning into a mission to get it implemented, lol.

---

### Post by Slim Odds on 2006-05-03
[QUOTE=glotz]Babysitting the computer is very annoying. Every second counts![/QUOTE]

Every second counts when he's rebooting to play games at lunch :rolleyes: 

If every second counts, stay in a OS that works. :D

---

### Post by mabhatter on 2006-05-03
This is a feature I'd like to see. My kids like using Ubuntu for the games, but sometimes they want to play windows games when I'm not home. To expand on the idea, I'd like to see a "Pause and Reboot to:" option instead of logoff.  I use Hibernate on my laptop instead of fully rebooting and it's really sweet.  You don't loose all your work in process and both windows and ubuntu play pretty nice together because the hibernate is controlled by the OS.  Like the orginal said, if you could choose to "Switch OS" as a regular command it would  make things really easy and benificial for multi-booters out there!  Like a few other people said, you can set the wait time at boot up to choose, but who wants to wait 10 seconds.. and miss the entry half the time.  When you're sharing a computer it's important that it be predictable to other family members that might not know so much... or have small fingers that can't switch OS fast enough! 

I believe what everybody was thinking of was BeOS had a feature where the PE installed a desktop shortcut to BeOS.  You booted to windows, then clicked the Be icon to reboot into BeOS.   After you were done the computer rebooted back into windows...  And that was in '99!!!

---

### Post by Sutekh on 2006-05-03
[QUOTE=debonair23]I agree :) I was originally seeing if this had been or could be done, but i guess now its turning into a mission to get it implemented, lol.[/QUOTE]
You can do this now

[GRUB Manual - grub-set-default](http://www.gnu.org/software/grub/manual/grub.html#Invoking-grub_002dset_002ddefault)



You could also create your own executable to do this.
```
sudo nano /usr/sbin/**windowsreboot**
```
 - You could call it something else in place of the bold

 - Then add these contents
```
 ### /usr/sbin/windowsreboot ###
echo "savedefault --default=**1** --once quit" | grub
reboot
```
 - Substituting the correct nuber to boot windows

 - Save the file and make it executable
```
sudo chmod +x /usr/sbin/windowsreboot
```
 - If you run the executable, from the terminal or a launcher, then it should change the default GRUB menu and then reboot.

 - I haven't tested this yet though.

---

### Post by Face1 on 2006-05-03
That last message lost me a little bit, but it probably works...However, if it doesn't an alternative (yet messy!) solution is to do the following:

Create a script that simply edits the grub.conf file to set windows as the default OS, and then reboots.

Then, create a startup script in Linux that changes that back to ubuntu whenever ubuntu is booted.

---

### Post by _linux_ on 2006-05-03
[QUOTE=debonair23]Is there a way to specify that I want to reboot into windows when shutting down ubuntu so that I do not have to be present to select windows from the bootloader menu when the computer restarts? I don't want to reconfigure grub to always boot windows instead of linux, I want it to be a one time thing.[/QUOTE]

I've also wanted to do something like that, but I'm not sure if it's possible in Ubuntu. I know that you can do it in SUSE. Hopefully, it will be put into Ubuntu too.:KS

---

### Post by enopepsoo on 2006-05-03
[QUOTE=_linux_]The day Microsft makes something that doesn't suck is the day they make vaccuum cleaners[/QUOTE]
Classic.

---

### Post by mjziegle on 2006-05-03
Edit /boot/grub/menu.1st

Find the section for Windows.  Cut it and put the 4 or so lines before the ubuntu lines.  Done.  When you reboot you go into windows first by default.  The downside is if you want ubuntu you have to select it.

A new kernel will also put itself on top of menu.1st so you will have to redo the above.  Otherwise to avoid this configure a default as the above poster suggested.

It is highly recommended to configure a default anyway so when you update your kernel and reboot remotely you don't go into a kernel that all your driver modules won't work for.

-Matt

---

### Post by debonair23 on 2006-05-04
I don't want to set windows as the default boot option, I mentioned this in my first post. I only want it to be a one time thing and I want linux to be the default boot option.

---

### Post by Engnome on 2006-05-04
I wold rather have a "boot into ubuntu icon in windows."

---

### Post by debonair23 on 2006-05-04
[QUOTE=Engnome]I wold rather have a "boot into ubuntu icon in windows."[/QUOTE]

Thats the same thing I'm looking for, except a "Boot into Windows" icon in Ubuntu

---

### Post by Sutekh on 2006-05-05
For this to work, you need to 

1) Edit your GRUB menu
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo nano /boot/grub/menu.lst
```
and find this line ```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
**default         0**

```
and change it to
```
**default        saved**
```

2) Then you need to make sure that the GRUB entry that you want to boot to has the line **savedefault**, for example
```
title           Microsoft Windows XP Professional
root            (hd1,0)
**savedefault**
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

3) Finally you can use this code to echo the menu default to grub using a pipe (the | ) and then shutdown the computer for a reboot
```
echo savedefault --default=**N** --once | grub
sudo shutdown -r now
```
Changing **N** for the number corresponding to the entry you want to boot.
When the GRUB menu starts the N'th GRUB menu entry will be automatically selected and booted.

You can add the code to a launcher and call it "Boot Windows" or something.

You can also use
```
sudo grub-reboot **N**
``` to change the default boot entry.  This does exactly the same thing as the code above, yet waits for you to give it the okay to reboot.  

So you can use whichever method appeals to you.

---

### Post by frio on 2006-05-10
Why not use a simple script that renames /boot/grub/menu.lst (I think that's the path, I'm not at my ubuntu machine). Have two grub config files, each specifies a different default boot partition, Run a script or batch that renames the files accordingly and then reboots the machine...?

---

### Post by Ramses de Norre on 2006-05-10
Because it's permanent then..

---

### Post by elamericano on 2006-05-10
Doesn't Sutekh's method permanently change the default, until you manually select Ubuntu at the boot screen?

I think the OP was looking for a one-time Windows boot.

Personally, I have a script that boots into Windows, and a batch file that boots me back into Linux. Those are good times to take a break, 'cause I don't have to be at the keyboard to switch OSes.

---

### Post by Resurrection on 2006-05-10
[QUOTE=elamericano]Personally, I have a script that boots into Windows, and a batch file that boots me back into Linux. Those are good times to take a break, 'cause I don't have to be at the keyboard to switch OSes.[/QUOTE]
And how do you do it?  Care to share what your batch/script looks like?

---

### Post by elamericano on 2006-05-10
I didn't figure that people would want to emulate my setup, but here's the trick:
GRUB is installed in the partition, not the MBR
> lilo -A /dev/hda 1
Yes, I'm still using GRUB, but I installed lilo for this command. It switches the active partition back to 1, which is XP on my computer.

From Windows:
> MBRWiz /Active=1
shutdown -r -f -t 0
Again, the 1 is the Linux partition on my system (the tool counts from 0). I always recommend that people use primary partitions and the bootloader NOT in the MBR, because it's much cleaner that way. You could blow away either partition, and the other one will still boot - the MBR doesn't have to be restored.

I notice there is a linux version of MBRWiz, but I've never used it.

---

