---
title: "I think Bluetooth has broken my computer..."
date: 2011-12-30
forum: General Help
---

### Post by L R C on 2011-12-30
I got a pair of bluetooth headphones yesterday, to use with my phone. I didn't plan on using them with my computer (I didn't think it had Bluetooth compatibility) but I had them on earlier when I turned my PC on. If it helps, here are the specs:

2x AMD dual-core processor (not sure which type, since I can't actually use my computer)
3.9 GB RAM
Made around 2008 (custom built)
Ubuntu 11.10 dual-booted with a copy of Windows XP, which is so messed up that it's unusable.

When I turned my computer on, it ran as normal for a while (telling me which OS to select, BIOS, etc), but the last normal thing in the process was a purple screen, with the Ubuntu text on it, and five red dots, which stayed on the screen for about five seconds. After this it would usually go into the login menu, but this time it went into a different screen. I took a picture with my phone:

[img]http://img249.imageshack.us/i/imageqny.jpg/[/img]

Nothing happened after this, I've left the computer for about half an hour. I've tried restarting it, with all my bluetooth devices turned off, and it just happened again. The correct ASCII characters appeared on the screen when I typed, but nothing seemed to happen. Pressing keys such as the function keys, Esc and the arrow keys made code appear, instead of doing anything to the text, if that makes sense.

It also mentioned battery state, which is weird since it's a desktop computer.

I'm not actually sure if bluetooth had anything to do with what happened, but the presence of the word "bluetooth" on the screen and the fact that this only happened when there was a bluetooth signal in the room, makes me a bit suspicious.

Anyone know what I can do to fix my computer?

---

### Post by Ms. Daisy on 2011-12-30
Is it just Ubuntu that's messed up? You said you can access BIOS & you get the OS selection screen. Have you successfully booted Win XP?
 
BTW, the link to your photo was broken for me.

---

### Post by LinuxFan999 on 2011-12-30
Try completely removing the Bluetooth module, then boot the computer again. If that doesn't work, you have a broken Ubuntu installation and will need to back up your data and reinstall Ubuntu.

---

### Post by L R C on 2011-12-30
> **Ms. Daisy said:**
> Is it just Ubuntu that's messed up? You said you can access BIOS & you get the OS selection screen. Have you successfully booted Win XP?
 
BTW, the link to your photo was broken for me.

I originally installed Ubuntu because Windows kept crashing, I took it in to get fixed and the guy basically told me he could fix the computer after every crash but he couldn't do anything to prevent them, because it was an illegal copy. And the BIOS has never worked fully, even with Windows, so I can't select anything or change anything - I made Ubuntu the default OS and now I can't access Windows.

Sorry about the link, I'll see if I can fix it.

In response to the next post: I'm not sure if my computer even has bluetooth, I can't remember asking to have it when the computer was built, and I've never seen it in my settings in Windows or Ubuntu. The problem might not have been caused by bluetooth; the screen that came up also mentioned a battery, which I don't have. It's just that I hadn't used bluetooth devices until today, which is the first time this has happened, and since the aforementioned screen also mentioned bluetooth, I feel like there might be a link.

---

### Post by LinuxFan999 on 2011-12-30
> **L R C said:**
> I originally installed Ubuntu because Windows kept crashing, I took it in to get fixed and the guy basically told me he could fix the computer after every crash but he couldn't do anything to prevent them, because it was an illegal copy. And the BIOS has never worked fully, even with Windows, so I can't select anything or change anything - I made Ubuntu the default OS and now I can't access Windows.

Sorry about the link, I'll see if I can fix it.

In response to the next post: I'm not sure if my computer even has bluetooth, I can't remember asking to have it when the computer was built, and I've never seen it in my settings in Windows or Ubuntu. The problem might not have been caused by bluetooth; the screen that came up also mentioned a battery, which I don't have. It's just that I hadn't used bluetooth devices until today, which is the first time this has happened, and since the aforementioned screen also mentioned bluetooth, I feel like there might be a link.
Why not just delete Windows, since it is an illegal copy?

There is one more thing you could try before reinstalling Ubuntu. If you open the Computer and look around the motherboard, you will see a coin sized battery.
Unplug the computer, open it up, and remove the battery. Leave it alone for about 20 minutes. After 20 minutes, put the battery back on the motherboard(make sure it is inserted correctly) , then close the case, plug the computer back in and turn it on.
Enter the BIOS and set the correct time, then save your changes and restart.
Try booting into Ubuntu after doing that. If Ubuntu doesn't boot, then you need to back up your data and reinstall Ubuntu.

---

### Post by L R C on 2011-12-30
> **LinuxFan999 said:**
> Why not just delete Windows, since it is an illegal copy?

There is one more thing you could try before reinstalling Ubuntu. If you open the Computer and look around the motherboard, you will see a coin sized battery.
Unplug the computer, open it up, and remove the battery. Leave it alone for about 20 minutes. After 20 minutes, put the battery back on the motherboard(make sure it is inserted correctly) , then close the case, plug the computer back in and turn it on.
Enter the BIOS and set the correct time, then save your changes and restart.
Try booting into Ubuntu after doing that. If Ubuntu doesn't boot, then you need to back up your data and reinstall Ubuntu.

Thanks for your advice.

I don't know much about computers; the furthest I'll interact with it beyond the GUI is typing stuff into the terminal. As a result, I'm not really sure how I'd go about deleting Windows. I've checked and I don't think I can access any of my pre-ubuntu files, it's like it's an entirely new computer, rather than a dual-boot.

What does replacing the battery do? I think I've encountered it before but I have no idea what it's for.

One last question: how would I go about backing up my data, since I can't access the computer? Would something like Puppy Linux help?

---

### Post by LinuxFan999 on 2011-12-30
> **L R C said:**
> Thanks for your advice.

I don't know much about computers; the furthest I'll interact with it beyond the GUI is typing stuff into the terminal. As a result, I'm not really sure how I'd go about deleting Windows. I've checked and I don't think I can access any of my pre-ubuntu files, it's like it's an entirely new computer, rather than a dual-boot.

What does replacing the battery do? I think I've encountered it before but I have no idea what it's for.

One last question: how would I go about backing up my data, since I can't access the computer? Would something like Puppy Linux help?
Removing the battery clears the CMOS memory, which stores the BIOS setting, and resets the clock. This means that when you reinsert the battery and turn on the computer, you will need to set the time and change any settings you want to change.

A live CD like Puppy Linux can help you back up your files. All you need to do is boot from the CD, mount the internal hard drive and an external storage device, then find your fi;es and move them over to the external storage. After you do that, you can boot from your Ubuntu CD, and format the hard drive and install Ubuntu.

---

### Post by L R C on 2011-12-30
> **LinuxFan999 said:**
> Removing the battery clears the CMOS memory, which stores the BIOS setting, and resets the clock. This means that when you reinsert the battery and turn on the computer, you will need to set the time and change any settings you want to change.

A live CD like Puppy Linux can help you back up your files. All you need to do is boot from the CD, mount the internal hard drive and an external storage device, then find your fi;es and move them over to the external storage. After you do that, you can boot from your Ubuntu CD, and format the hard drive and install Ubuntu.

Thanks a lot for your help. I'll open the computer up when I get round to removing all the stuff that I've put on top of it... :-P

---

### Post by matt_symes on 2011-12-30
Hi

Do you actually use Timidity ?

I woud suggest it may be an issue between the bluetooth headphone sound (for your headset) and Timidity. Maybe they are both trying to grab the sound node at the same time or one is blocking the other.

You could test this by booting into a liveCD and ensuring the bluetooth init script does not run. Then you could reboot into your hard drive to check.

From a terminal in the live CD.

```
sudo chmod 000 /etc/init.d/bluetooth
```

Then boot into your hard drive install.

Kind regards

---

### Post by L R C on 2011-12-30
> **matt_symes said:**
> Hi

Do you actually use Timidity ?

I woud suggest it may be an issue between the bluetooth headphone sound (for your headset) and Timidity. Maybe they are both trying to grab the sound node at the same time or one is blocking the other.

You could test this by booting into a liveCD and ensuring the bluetooth init script does not run. Then you could reboot into your hard drive to check.

From a terminal in the live CD.

```
sudo chmod 000 /etc/init.d/bluetooth
```

Then boot into your hard drive install.

Kind regards

I don't think I use Timidity, I downloaded tons of programs when I was trying to get tuxguitar to work, and that was one of them...

Like I said, I'm not sure if my computer even has bluetooth. The headphones were paired with my phone, so they weren't trying to join with my computer; there's a good chance the two are unrelated.

I'm afraid I don't understand any of the things you said about the live CD.

Thanks for your help.

---

### Post by matt_symes on 2011-12-30
Hi
> 
Like I said, I'm not sure if my computer even has bluetooth. The  headphones were paired with my phone, so they weren't trying to join  with my computer; there's a good chance the two are unrelated.I see. I though you had paired the headphones with Ubuntu. 

Can you boot into recovery mode (root console) from the Grub menu? 

If you can then uninstall Timidity from the command line using (no sudo required as root console)

```
apt-get remove --purge timidity
```Then type

```
shutdown -h now
```to shutdown your computer. Then start it up as normal.

Does it still hang ?

Kind regards

---

### Post by L R C on 2011-12-30
> **matt_symes said:**
> Hi
I see. I though you had paired the headphones with Ubuntu. 

Can you boot into recovery mode (root console) from the Grub menu? 

If you can then uninstall Timidity from the command line using (no sudo required as root console)

```
apt-get remove --purge timidity
```Then type

```
shutdown -h now
```to shutdown your computer. Then start it up as normal.

Does it still hang ?

Kind regards

Unfortunately the computer ignores me until I'm at the login menu, I can't do anything until then. You wouldn't know how to fix this, would you?

Thanks in advance

---

### Post by matt_symes on 2011-12-30
Hi
> 
Unfortunately the computer ignores me until I'm at the login menu,The computer ignores all your key presses at the grub menu ? You cannot choose a kernel ?

In case your not sure, the grub menu is the first menu you see just after you switch on your PC. It allows you to pick a kernel.

From here you can select the recovery kernel option and when the menu appears you can use the arrow keys to select a root console. Then you can follow the steps in my last post to remove Timidity.

If you do not see the grub menu then press (and keep depressed) the shift key when you turn the computer on. This should bring up the Grub menu.

Your other option is to use a LiveCD and chroot into your install and uninstall it that way.

I think that may fix your problem.

Kind regards

---

### Post by L R C on 2012-01-04
Hi again,

It turns out the computer was ignoring my input because USB keyboard input wasn't enabled. After I figured out how to enable it, I was able to enter recovery mode (and use Windows, for that matter). I uninstalled timidity but upon trying again, the same screen appeared as I had originally, it just didn't mention timidity.

I would back up all of my files by going on Windows so I can reinstall Ubuntu, but I can't see anything I have in Ubuntu, it's like the two OS's don't want to acknowledge each other's presence.

Thanks for your help by the way.

---

### Post by dFlyer on 2012-01-04
> **L R C said:**
> Hi again,

It turns out the computer was ignoring my input because USB keyboard input wasn't enabled. After I figured out how to enable it, I was able to enter recovery mode (and use Windows, for that matter). I uninstalled timidity but upon trying again, the same screen appeared as I had originally, it just didn't mention timidity.

I would back up all of my files by going on Windows so I can reinstall Ubuntu, but I can't see anything I have in Ubuntu, it's like the two OS's don't want to acknowledge each other's presence.

Thanks for your help by the way.

Linux can read ntfs, but windows can't read ext partitions.

---

### Post by Rasa1111 on 2012-01-04
Just try unplugging it for 5-10 minutes.
Plug it back in, and try to boot'er up.

Might be surprised.

And you can use a regular Ubuntu LiveCD to access and back up your files. 

Boot a liveCD, open the home folder, and then open/mount the hdd/ "file system"
Theres all your files. 
Good luck.

---

### Post by L R C on 2012-01-04
> **Rasa1111 said:**
> Just try unplugging it for 5-10 minutes.
Plug it back in, and try to boot'er up.

Might be surprised.

And you can use a regular Ubuntu LiveCD to access and back up your files. 

Boot a liveCD, open the home folder, and then open/mount the hdd/ "file system"
Theres all your files. 
Good luck.

I unplug my computer every time I turn it off, I'm pretty sure it's not that :-|

I'll try the LiveCD as soon as I can.

---

### Post by Rasa1111 on 2012-01-04
huh.
Sorry man, thought it was worth a shot. lol

There's been a few times in my couple years using Ubuntu where I could not get it to boot for anything.
Then someone suggested what I suggested to you...
and sure enough... Every time Ive not been able to boot (only a few), Killing all power for a couple minutes has worked. On laptop and desktop. 

The removal of the battery from the tower is also a good suggestion.

---

