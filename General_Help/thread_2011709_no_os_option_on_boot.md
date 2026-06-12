---
title: "no os option on boot"
date: 2012-06-27
forum: General Help
---

### Post by railkiller on 2012-06-27
hi newbie here, i installed ubuntu 12.04 with live cd side by side with vista(original os) restarted after succsessful instalation and now my machine only boots ubuntu, can anyone help?

---

### Post by wilee-nilee on 2012-06-27
Try in the ubuntu terminal running.
```
sudo update-grub
```

Look for vista to show in the terminal, if it does it is in the boot menu.

---

### Post by railkiller on 2012-06-27
> **wilee-nilee said:**
> Try in the ubuntu terminal running.
```
sudo update-grub
```
 
Look for vista to show in the terminal, if it does it is in the boot menu.
 
 
vista does show in the terminal but i dont get the option to use it when i turn my pc on?

---

### Post by WorMzy on 2012-06-27
Do you have multiple Linux installations?

---

### Post by railkiller on 2012-06-27
> **WorMzy said:**
> Do you have multiple Linux installations?
 
 
no this is the only time i've ever installed or used any linux

---

### Post by wilee-nilee on 2012-06-27
Use this tool in ubuntu to generate the bootinfo summary and post the http to it.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

The first gui you will see when it launches gives you this option, just start with that.

---

### Post by WorMzy on 2012-06-27
Post the contents of your /boot/grub/grub.cfg file here, in-between CODE tags.

---

### Post by railkiller on 2012-06-27
> **wilee-nilee said:**
> Use this tool in ubuntu to generate the bootinfo summary and post the http to it.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
 
The first gui you will see when it launches gives you this option, just start with that.
 
sorry cant use that at the moment, i cant access the web on ubuntu either, i,m using someones laptop,its connected to my livebox but no internet

---

### Post by railkiller on 2012-06-27
> **WorMzy said:**
> Post the contents of your /boot/grub/grub.cfg file here, in-between CODE tags.
 
 
sorry i'll have to type it , cant get no internet on ubuntu at the mo.
 
#cuntos@cuntos-desktop:~$ sudo update-gru
[sudo] password for cuntos:
generating grub.cfg ...
found linux image: /boot/vmlinuz-3.2.0-23generic-pae
found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
found memtest86+ image: /boot/memtest86+.bin
found windows vista (loader) on /dev/sda1
done#
 
i dont know if that helps

---

### Post by railkiller on 2012-06-28
hi can anyone else help , i cant even uninstall ubuntu to get me outta this mess.

---

### Post by Lyfang on 2012-06-28
1. Try to create a Live USB flash drive, copy all of your personal files to an external hard drive from Linux & Windows.

2. Format & reinstall Windows. Next time you might want to try Wubi instead? It's a quick and easy way to try Ubuntu.

---

### Post by nipunshakya on 2012-06-28
I guess the boot repair tool is the only thing that can save u right now... unless u want to use windows installation disk and wipe all your partitions and make a fresh installation of windows...

if you are on someone else's laptop there is no harm in booting to live mode to his/her laptop and then downloading boot repair tool inside the live mode... next, you can run the tool by booting the very cd in your laptop

Tell us one thing, when u were asked to select how to install ubuntu, what options did u choose?? like 'install alongside windows vista', .... 'something else' ???
which one did u choose?

---

### Post by railkiller on 2012-06-28
> **WinuxUser said:**
> I guess the boot repair tool is the only thing that can save u right now... unless u want to use windows installation disk and wipe all your partitions and make a fresh installation of windows...
 
if you are on someone else's laptop there is no harm in booting to live mode to his/her laptop and then downloading boot repair tool inside the live mode... next, you can run the tool by booting the very cd in your laptop
 
Tell us one thing, when u were asked to select how to install ubuntu, what options did u choose?? like 'install alongside windows vista', .... 'something else' ???
which one did u choose?
 
 
i choose alongside vista, 
 
i'll give that a go thanks, how would i move the boot repair tool to my system. can i just drag and drop with a memory stick like windows?

---

### Post by railkiller on 2012-06-28
> **Lyfang said:**
> 1. Try to create a Live USB flash drive, copy all of your personal files to an external hard drive from Linux & Windows.
 
2. Format & reinstall Windows. Next time you might want to try Wubi instead? It's a quick and easy way to try Ubuntu.
 
 
hi my windows files are safe on an external drive, and i dont have an installation disc for a reinstall, thanks tho.

---

### Post by drs305 on 2012-06-28
You might be able to boot into Windows by building a custom menu.

First, determine the UUID of your Windows partition with the following command:
```
sudo blkid
``` 

Next, create a custom menuentry. Substitute your text editor for *gedit* and in the entry add the correct UUID.
```
gksu *gedit* /etc/grub.d/40_custom
```
Below the existing lines, add:

> 
menuentry "Windows 1" {
insmod ntfs
search --set=root --fs-uuid [COLOR="Red"]UUID_HERE[/COLOR]
ntldr /ntldr
}

menuentry "Windows 2" {
insmod ntfs
search --set=root --fs-uuid [COLOR="Red"]UUID_HERE[/COLOR]
chainloader +1
}

Save the file, then update GRUB:
```
sudo update-grub
```
Reboot and see if either Windows entry will boot.

I'm not a Windows user but without an Internet connection and/or the LiveCD this is about all I can recommend.

---

### Post by nipunshakya on 2012-06-28
no its not like that...  when you boot to your live cd mode, the whole session is totally independent of your hard disk boot sessions... thats the benefit of ubuntu.
you can run the boot repair tool from within the live cd mode...
Just boot into your live session, and then follow from the topic: '2nd option: install boot-repair in Ubuntu' mentioned in the following link:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by railkiller on 2012-06-28
> **WinuxUser said:**
> no its not like that... when you boot to your live cd mode, the whole session is totally independent of your hard disk boot sessions... thats the benefit of ubuntu.
you can run the boot repair tool from within the live cd mode...
Just boot into your live session, and then follow from the topic: '2nd option: install boot-repair in Ubuntu' mentioned in the following link:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
 
 
ok running it now like i said am a total newb to linux, cheers

---

### Post by nipunshakya on 2012-06-28
ok.. proceed further.. see what happens

---

### Post by Shadius on 2012-06-28
The "**Recommended repair**" option should fix everything for you. By everything, I mean getting back the OS entries on the GRUB menu so you can boot into whichever OS you choose, Windows or Ubuntu. You can also use the "**Create a BootInfo summary**" and post the contents here so we can take a look.

---

### Post by railkiller on 2012-06-28
ok so i burnt the boot-repair disk onto cd opened a normal session in ubuntu and dont know how to get it to run i typed boot-repair into the terminal like the link that winuxuser posted([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) but it says command not found, also typed it into the dash and not found , dont know how to get into sytem->administration->boot-repair(gnome). do i need to run the disc on bootup??

---

### Post by Shadius on 2012-06-28
> **railkiller said:**
> ok so i burnt the boot-repair disk onto cd opened a normal session in ubuntu and dont know how to get it to run i typed boot-repair into the terminal like the link that winuxuser posted([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) but it says command not found, also typed it into the dash and not found , dont know how to get into sytem->administration->boot-repair(gnome). do i need to run the disc on bootup??

Make sure you're computer's BIOS is set to boot from CD/DVD and reboot.

---

### Post by railkiller on 2012-06-28
> **Shadius said:**
> Make sure you're computer's BIOS is set to boot from CD/DVD and reboot.
 
 
yeah have done that, its been scanning systems. please wait few seconds for a while, will be patient an wait.

---

### Post by nipunshakya on 2012-06-28
> **WinuxUser said:**
> 
Just boot into your live session, and then follow from the topic: '2nd option: install boot-repair in Ubuntu' mentioned in the following link:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

it meant that you boot your ubuntu 12.04 cd in live session, then at there run the terminal and type 
```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
``` to add the source from where you will be getting the software
and then
```
sudo apt-get install -y boot-repair && boot-repair
```to  install boot-repair tool in your livecd and then after that you can launch the boot-repair tool from the terminal by typing ```
boot-repair
```The easiest method. After you have run the boot-repair tool, you could use the 'Recommended Settings' and that might have fixed your problem.

But since you made a seperate boot-repair disk, similar things might work out too.. Do post the latest updates

By now you might have understood well that Boot-repair could be used in two different ways, one by creating its own cd and booting from it, and two by installing the app as i suggested above and running it from the terminal..

Goodluck out there..

---

### Post by railkiller on 2012-06-28
> **Shadius said:**
> The "**Recommended repair**" option should fix everything for you. By everything, I mean getting back the OS entries on the GRUB menu so you can boot into whichever OS you choose, Windows or Ubuntu. You can also use the "**Create a BootInfo summary**" and post the contents here so we can take a look.
 
ok its finished , chose recommended repair it did its thing, then said to reboot off hard drive , did that , booted to ubuntu again with no os choice. cant post 'creat a bootinfo summary' because i cant get my internet to work with ubuntu, i could type it but that could take hours, if i run it again would there be a particular line you? would look for? 
this is a real ball ache, thanks for your time.

---

### Post by nipunshakya on 2012-06-28
the boot info summary contains valuable information of where and how your system is configured to boot and other information too.... with it, your problem could be exactly pointed out too.....

When you said you selected 'alongside windows', then and there there rises a suspicion that the ubuntu installation might have disturbed your windows partitions and so causing difficulty for windows to boot.. windows is just there, it just needs a drive check of some sort so that it can fix itself into the right position where it resided before ubuntu was on your machine...

Really the boot-info summary have helped alot to reduce the problem...

---

### Post by drs305 on 2012-06-28
Can you save the file to a thumb drive and then attach it to a post here from your other computer?

---

### Post by railkiller on 2012-06-28
> **drs305 said:**
> Can you save the file to a thumb drive and then attach it to a post here from your other computer?
 
 
this system is running win 7, will it cross over ok?

---

### Post by drs305 on 2012-06-28
> **railkiller said:**
> this system is running win 7, will it cross over ok?

Run the report in Ubuntu; it will be called RESULTS.txt

The report is only a text file. However you can access it from Windows will be fine. You can open it and paste the contents between 'code' tags (press the # icon in the post's menubar) or simply attach it to a post.

---

### Post by railkiller on 2012-06-28
> **drs305 said:**
> Run the report in Ubuntu; it will be called RESULTS.txt
 
The report is only a text file. However you can access it from Windows will be fine. You can open it and paste the contents between 'code' tags (press the # icon in the post's menubar) or simply attach it to a post.
 
 
ok running it again.

---

### Post by railkiller on 2012-06-28
> **drs305 said:**
> Run the report in Ubuntu; it will be called RESULTS.txt
 
The report is only a text file. However you can access it from Windows will be fine. You can open it and paste the contents between 'code' tags (press the # icon in the post's menubar) or simply attach it to a post.
 
 
how do you run it in ubuntu?(total newb) couldnt save it to my memory stick in boot-repair

---

### Post by drs305 on 2012-06-28
I could not find a way to run the boot info script from Boot Repair and designate where to save the file it generates. Apparently it is only meant to be uploaded to the Internet. 

However, on exploring my drive, I found a copy tucked away in the /tmp/BootInfo-<alphanumeric> folder. The name of mine was /tmp/BootInfo-AUFk88xw and the info file (aka RESULTS.txt) was named "Log". It looks like it creates two log files, so use the latest one (Log1 for me).

You may have to open the /tmp file as root, so explore the /tmp folder with your file browswer and 'gksu'. For Ubuntu, it would be:
```
gksu nautilus /temp
```

---

### Post by nipunshakya on 2012-06-28
> **railkiller said:**
> how do you run it in ubuntu?(total newb) couldnt save it to my memory stick in boot-repair

If you follow my post #23 without skipping any part, you will relieve urself..
you might know what terminal is,don't u?? so do the thing in terminal and run boot-repair from live session. its so crystal clear steps..i just wonder why aren't u being able to follow the steps...

---

### Post by railkiller on 2012-06-29
hello, just got back from work where a colleague suggested that grub is there i just cant see it for some reason, so first i spammed the arrow and enter keys at boot and it magicly loaded checkdisk for windows restarted and then obviously ran ubuntu on the next boot. he also said to hold shift down after the setup page on boot to show grub if it was there, and it did (thank the lord!)so now i can use vista, its sh*t i know but it does work on my system, i think i'll have a look at some basic(very) tutorials before i start having a go at linux.
i would like to say a big thankyou to winuxuser,wilee nilee, wormzy, lyfang,shadius and drs305 for at least taking the time to try and help, i'll be back with a bit more knowledge soon.
 
please mark as solved(sort of)

---

### Post by Lyfang on 2012-06-29
> **railkiller said:**
> hello, just got back from work where a colleague suggested that grub is there i just cant see it for some reason, so first i spammed the arrow and enter keys at boot and it magicly loaded checkdisk for windows restarted and then obviously ran ubuntu on the next boot. he also said to hold shift down after the setup page on boot to show grub if it was there, and it did (thank the lord!)so now i can use vista, its sh*t i know but it does work on my system, i think i'll have a look at some basic(very) tutorials before i start having a go at linux.
i would like to say a big thankyou to winuxuser,wilee nilee, wormzy, lyfang,shadius and drs305 for at least taking the time to try and help, i'll be back with a bit more knowledge soon.
 
please mark as solved(sort of)

Bear in mind that your user experiance really depends on these usability issues, such as the design. Thank you for taking the time trying out Ubuntu! Wubi is also really quite easy to install & uninstall.

---

### Post by nipunshakya on 2012-06-29
> **railkiller said:**
> hello, just got back from work where a colleague suggested that grub is there i just cant see it for some reason, so first i spammed the arrow and enter keys at boot and it magicly loaded checkdisk for windows restarted and then obviously ran ubuntu on the next boot. he also said to hold shift down after the setup page on boot to show grub if it was there, and it did (thank the lord!)so now i can use vista, its sh*t i know but it does work on my system, i think i'll have a look at some basic(very) tutorials before i start having a go at linux.
i would like to say a big thankyou to winuxuser,wilee nilee, wormzy, lyfang,shadius and drs305 for at least taking the time to try and help, i'll be back with a bit more knowledge soon.
 
please mark as solved(sort of)

There is no harm trying to learn...the best way to learn is by implementing your learning to practice... and you did by trying to install ubuntu... 

Next time when you want a dual boot, don't select 'alongside vista' rather select 'something else'... when u are ready, post back.. and we are ready too...

Goodluck out there mate:guitar:

---

### Post by Shadius on 2012-06-29
You're welcome! Glad to help! I'm glad your friend suggested you try to hold down the *Shift* key to see if the GRUB menu was hidden. I was thinking about that option as well. Like my signature says, when you break a lot of things, you learn a lot of things! Part of learning is breaking and fixing. Break away! :D We'll help you fix it, of course. :lolflag: ;)

---

