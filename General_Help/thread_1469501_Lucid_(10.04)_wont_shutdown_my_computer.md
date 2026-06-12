---
title: "Lucid (10.04) wont shutdown my computer"
date: 2010-05-02
forum: General Help
---

### Post by Da9eI on 2010-05-02
Hello, this will be my first post..

My ubuntu won't shut down, it stops at the ubuntu logo (with the dots under it). It seems like the OS completely and successfully shuts down, also the harddrive spins down too, except for the computer. I belive this might have happened after I updated my bios. (due to hybrid gpu trouble)

I did search on the internet, and found that it might be some ACPI related issues, and that I have to edit the grub's  menu.lst file and add acpi=force. However my menu.lst file is blank, there is nothing in there.

I have tried to shutdown via the terminal too, but the same happens there. Last time I checked it successfully reboots, and standby works correctly. For me to shutdown this laptop, I have to remove the battery and the power cord for it to shutdown, or hold the power button for 10 secs, which is really annoing.

Anyone who have the best answer?
Thanks.

---

### Post by Monotoko on 2010-05-02
When you get into the GRUB menu, press "e" to edit your entry and add acpi=force to the parameters.

GRUB 2 acts slightly differently to legacy  and doesnt have the menu.lst

---

### Post by colorlessprism on 2010-05-02
open a terminal and type 
"sudo gedit /etc/default/grub"
you should see something like this:
----------------------------------------
If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console
-----------------------------------------
where it says "GRUB_CMDLINE_LINUX="" is where you will add acpi=force. it should look exactly like this:
GRUB_CMDLINE_LINUX="acpi=force"

save your file and get in your terminal again and type:
"sudo update-grub"

---

### Post by Da9eI on 2010-05-02
Thanks for your reply(es)!

Adding the acpi=force to "GRUB_CMDLINE_LINUX" did not help. However I accidetely hit ESC during shutdown, and got some text info (verbose?) on screen

```
* All processes ended within 2 seconds....           [ OK ]

* Deconfiguring network interfaces...                [ OK ]

* Deactivating swap...                               [ OK ]

* Unmounting weak filesystems...                     [ OK ]

* Will now halt
               [  150.465539] Power down.
_

```

This were the last lines. 
And the marker on the bottom of the screen "  _  " does not blink. There are no advanced settings in bios to config acpi. I might however update the bios firmware to a last newest version as there was 4 different versions avaiable as a last option.

---

### Post by colorlessprism on 2010-05-02
try this instead:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"

 i guess some people report bugs when adding to options to GRUB_CMDLINE_LINUX. try editing your  /etc/default/grub and moving the acpi option as seen above. dont forget to:

 "sudo update-grub"

i have always thought it was a good idea to keep the latest firmware on my computer. although you dont usually know there is a new one until you start having problems. when i updated to 9.10 i had major screen flickering and serious usb issues. a simple bios update corrected all of that. try changing your grub and if you still have problems update your bios.

---

### Post by Da9eI on 2010-05-02
> **colorlessprism said:**
> try this instead:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"

 i guess some people report bugs when adding to options to GRUB_CMDLINE_LINUX. try editing your  /etc/default/grub and moving the acpi option as seen above. dont forget to:

 "sudo update-grub"

i have always thought it was a good idea to keep the latest firmware on my computer. although you dont usually know there is a new one until you start having problems. when i updated to 9.10 i had major screen flickering and serious usb issues. a simple bios update corrected all of that. try changing your grub and if you still have problems update your bios.

That didnt help either, it seems like the harddrive shuts down (spindown) to early in the shutdown process, preventing the os reading\writing the last data needed for shutdown. Just a theory..

But thanks anyway, unfortunately I have to use windows to upgrade the Bios firmware. Acer, my computer manufacturer, doesn't provide any way of updating bios through linux. Luckily thats only a harddrive change away.

By the way, its an Acer Aspire 5810TG (timeline series), which doesn't run win very well.

---

### Post by BrokeMahPC on 2010-05-02
Have you updated your bios to the latest version?
Give that a try. Mine was giving me a few acpi and apm hiccups.
It solved a suspend/resume problem which may be related to this.

You will need to change the bios boot order to make sure the cd/dvd drive boots with an Ubuntu CD in it. Apart from that try it with the default settings.
I had the same shutdown problem and could not find a solution - ended up doing a fresh install. It's ok now. 
Also have you checked your install cd with md5sum?

---

### Post by colorlessprism on 2010-05-02
all you need is to download the BIOS update, download UNetBootin, and grab a flash drive. UNetBootin can put freeDOS on a flash drive for you (its in the top dropdown menu). then extract the BIOS update into a folder on the flash drive. print off a copy of the BIOS instructions and boot into FreeDOS. cd into the folder that has the BIOS stuff in it and run the command the instructions tell you to. thats all i had to do to update my wind. good luck

---

### Post by dino99 on 2010-05-02
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"

some users need to remove "splash" from the command above

---

### Post by Da9eI on 2010-05-03
> **BrokeMahPC said:**
> Have you updated your bios to the latest version?
Give that a try. Mine was giving me a few acpi and apm hiccups.
It solved a suspend/resume problem which may be related to this.

You will need to change the bios boot order to make sure the cd/dvd drive boots with an Ubuntu CD in it. Apart from that try it with the default settings.
I had the same shutdown problem and could not find a solution - ended up doing a fresh install. It's ok now. 
Also have you checked your install cd with md5sum?

Everything (most) worked right out of the "box", however, I did not know what graphics card that was in use. Either the ATI 4330 or the Intel integrated. I dont want to use the ATI card, since I dont use graphic heavy applications on this computer (battery time). The only options in bios says SWITCHABLE or dGPU, and I figured that dGPU meant dedicated gpu (ATI). In between here I installed the drivers for the ATI Card, but got black screen during startup of ubuntu, the OS was still running normally tho. So I upgraded the BIOS to the newest version, which could (I hoped) have the option to set to ATI, INTEL or SWITCHABLE, but it didnt. After After som retries I found that dGPU meant Descrete GPU (INTEL), thats why I got black screen (wrong driver). I were able to uninstall the ATI driver and thats when I discovered that the computer wouldnt shut down properly.

The no shutdown issue might have happened right after I upgraded the bios, but Im not entirely sure since I couldn't see anything. Im gonna try updating (downdating?, sorry my Ingelich) to an older bios, and see if it helps.

Im going to try the method "colorlessprism" gave me for updating the bios, it seemed to be the easyest way, instad of removing 10 screws and lots of plastic covers to replace the harddrive with the windows one.

Thanks alot for your help so far guys, and Ill probably post a message here if my bios "downdate"\downgrade helps.

---

### Post by Laeg on 2010-05-03
I can confirm this to some extent. The same happened to me with an Amilo Sa 3650 and Lucid on it. The laptop has an onboard graphics card as well as a more powerful ATI card. After installing the ATI drivers (which gave me some errors btw) and removing them afterwards, the computer would not properly shut down.

However, the situation has resolved itself today. The laptop now shuts down properly. Unfortunately, I cannot reconstruct the error (sorry for that) as I added and removed lots of packages today (it was a pretty fresh install of Lucid after all). Still, it might have to do something with this ATI driver.

---

### Post by Da9eI on 2010-05-05
> **Laeg said:**
> I can confirm this to some extent. The same happened to me with an Amilo Sa 3650 and Lucid on it. The laptop has an onboard graphics card as well as a more powerful ATI card. After installing the ATI drivers (which gave me some errors btw) and removing them afterwards, the computer would not properly shut down.

However, the situation has resolved itself today. The laptop now shuts down properly. Unfortunately, I cannot reconstruct the error (sorry for that) as I added and removed lots of packages today (it was a pretty fresh install of Lucid after all). Still, it might have to do something with this ATI driver.

I did try to run the update program in ubuntu to see if it helped, but it didnt. However the computer will now reboot without any problems.

I have yet to try the bios thing, but I haven't had the time to try. I did search a little up on ATI and shutdown problems, and it gave some info I will look into later. Looks to be a common problem.

---

### Post by Michelexub on 2010-05-07
@Da9eI

I have a Acer 4810TZG and have the same issue.
Worked fine with Xubuntu 9.10, since upgrading to 10.4 it does not shutdown properly anymore.

If you find a solution, can you please post it here?
Thanks.

Michele

---

### Post by zecharia on 2010-05-07
Same problem here - computer won't power down :( Exactly like on the screenshot on previous page. Ubuntu 9.10 worked flawlessly, and currently installed on second partition Arch Linux powers down properly. Tried everything I could find concerning acpi, nothing worked so far :(

---

### Post by Fitch on 2010-05-13
Just as a test, disable your ethernet and then shut down.

---

### Post by Da9eI on 2010-05-16
> **Fitch said:**
> Just as a test, disable your ethernet and then shut down.

Uhmm:confused:.. where do I disable ethernet?  There are no options for it in bios except boot, did try that too. I disabled the wifi using the hw wifi button, but same result.
"interfaces" in /etc/network only have two lines which doesn't make any sense
```
auto lo
iface lo inet loopback
```

Im afraid I couldnt test the older bios version since acer removed the older bios versions from their download page. I did find the poweroff command, but it doesnt help either. Im still stuck, so help is still apprechiated!

Thanks :)

---

### Post by Michelexub on 2010-06-17
*Bump!*
Anyone has any idea that we can try?

M.

---

### Post by kgarbutt on 2010-06-18
I have the same problem with my work computer running Lucid 10.04. It won't shutdown. I didn't try the things suggested here on this forum, but this works for me (from the terminal):

sudo shutdown -P now

I have since added it to my .bashrc as an alias until a fix in found:
alias sd='sudo shutdown -P now'

---

### Post by BiGViC340 on 2010-06-19
I had to remove splash but editing the grub did the trick for me thanks guys! :) 

My second week on Linux and that bug was very discouraging. My symptoms were no sound, no shutdown/restart, no unlock, and I  couldn't edit users and groups on random boots. After shutting down with  terminal everything would work fine sometimes like I said very random.

Why does this happen though I would like to know. Why does adding acpi and removing splash "fix" these problems? Being a newb I want to learn as much as I can :) As I have no idea how Linux works.

---

### Post by BiGViC340 on 2010-06-19
Well I just booted ubuntu up again and had the same issues no sound, no shutdown/restart, no unlock, and I  couldn't edit users and  groups. So fix didn't work then I guess :( hopefully it will get fixed soon

I did another update-grub.. and rebooted and it worked? usually it takes like 5 reboots or more.. maybe this makes it more consistent weird bug...

---

### Post by BiGViC340 on 2010-06-20
UPDATE: boot up this mourning same issue I guess all we can do is wait  for a fix...nothing has worked so far. I do have sound I  fixed that issue by sudo users-admin>Advance Settings>User  Privileges>Check Use Audio Devices. I have sound every boot after that even on the ones I don't have no mount! :(,no shutdown/restart, no unlock, and I can't edit users and  groups

---

### Post by Robotnic on 2010-06-23
Same issue except no option to shutdown for me at all. Shutdown panel button greyed out. I don't make it to the three dots part! Also broken is cpu frequency scaling applet. need that to keep my cpu from overheating till i can afford a decent fan!

Some have fixed inability to shutdown by disabling open office quickstarter apparently but its not enabled in my case. 

Please some clever person find the answer! [-o<

---

### Post by doko1 on 2010-06-28
I have the same issue, but ONLY when i use the terminal command: 
sudo shutdown XX:XX

After typing the password, the terminal prompts the amount of minutes, until ubuntu will shutdown. But the computer will "freeze" at this screen: 

[IMG]http://dl.dropbox.com/u/7679029/boot1.png[/IMG]

The computer fan is running on high speed and the only thing i can do now is pushing the power-button for 5 secs. 

Note: All this never happens to me when i shutdown the computer normally via the panel.

I hope this gets solved someday...

---

### Post by alcatail on 2010-06-29
[[SIZE=5][COLOR=#000000]BrokeMahPC[/COLOR][/SIZE]]("http://ubuntuforums.org/member.php?u=974676") Thanks mate yourt a legend, I updated my Bios as per you suggestion and my computer now shuts down. I had the same problem as the other guys >>>> that is I would go to shut down and the harddrive turns off but the computer hangs on the shutdown screen. I too was runing an earlier version of Xubuntu without any problems but decided to upgrade to linux mint 9. I could not fix the problem and decided to switch over to xubuntu 10.04 and still had the same shutdown problem. After logging bugs with linux mint, etc still had no luck. I found this thread tonight, reflashed my bios and bingo problem solvered. Thanks for your help and I dropped a thankyou into you on my bug report. I am now reinstalling linux mint but I assume this problem is with drivers in the ACPI and some BIOS's need reflashing to work with the new drivers????
 
any way heres a link to my bug report
[https://bugs.launchpad.net/linuxmint/+bug/597251](https://bugs.launchpad.net/linuxmint/+bug/597251)
 
Thanx
Michael :guitar:

---

### Post by mohamed_fawzy21 on 2010-07-19
I had an acer aspire 5542g and ubuntu 10.04.
I had a similar problem where shutdown didn't work and instead it reboots the laptop.

I had downloaded the hardware for ATI driver and it is now working for me.

You can find it under System->Administration->Hardware Drivers

Hope it work for you.

---

### Post by erniequintero on 2010-07-21
i got this problem after i did the latest kernel update.  if i select a previous kernel then it shutdown just fine any ideas.  thanks.

---

### Post by Michelexub on 2010-07-24
> **mohamed_fawzy21 said:**
> I had an acer aspire 5542g and ubuntu 10.04.
I had a similar problem where shutdown didn't work and instead it reboots the laptop.

I had downloaded the hardware for ATI driver and it is now working for me.

You can find it under System->Administration->Hardware Drivers

Hope it work for you.

Hi mohamed_fawzy2.
It worked perfectly for me.
Thanks.

Michelexub

---

### Post by Scallyph on 2010-09-04
Hi
I installed  the 10.04 release kernel 2.6.32-24 (Lucid) on a Presario 1700 600Mhz 256Mb and I faced the same problem. Os shuts down >drive stops spinning > display stayed active. Pressing on/off button did not result in system start only HD spinning briefly.Holding button for 5secs did also not work (?), unplug power cable did the job, frustrating yes.

I can confirm that adding "apci=force" to the line: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" worked on this system for me.
 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash apci=force"

So,...roasted ones for you, colorlessprism

---

### Post by Futurian on 2012-10-06
Colorlessprism,

I had to reinstall 10.04 on my ancient Gateway desktop, and it would not shutdown cleanly, so it checked the disks each and every time I rebooted. Your fix eliminated this problem
Thank you!

---

