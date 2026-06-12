---
title: "Ubuntu 9.04 many problems"
date: 2009-10-24
forum: General Help
---

### Post by daldude on 2009-10-24
I don't know if It was a bad install or just the way 9.04 64-bit is but I have many annoying  problems with j9.04.

1 I can't drag my Windows XP NTFS partitions to the desktop to have them automatically mount and then stay that way if I reboot.

 2 WINE (that program that lets you run Windows Programs in Ubuntu) does not work properly, I had to install it twice to get it to work and the Fonts in the Windows programs are that script type font that is 
impossible to read.

3 The System Sounds don't work properly, if I change the log on sound to something different the the default sound it still plays that default sound even though the file listed under Log In is not the default sound. 

I have not noticed any increase in performance over 9.04 32-bit.

The only benefit is I don't have to close Firefox or leave Youtube in order to play a video file iwith movie player. With 8.04 if I tried to lplay a video file with the movie player program while Youtube was loaded in Firefox the video would not play correctely and would platy real slow with no sound. If I'm playing a video file with movie player Youyube videos play without sound under 8.04 32-bit. This is just one anoyence compared to at least 3 with 9.04 64-bit.:mad::confused:

---

### Post by 101011010010 on 2009-10-24
Hello there,
I had similar problems on Jaunty x64, I switched to Karmicx64 beta and now rc and everything works perfectly.
I hope this helps.

---

### Post by rockstarrem on 2009-10-24
Why are you using 64 bit? If you have the hardware for it, that's obviously a good reason, but you said you used 32 bit before, why did you switch?

---

### Post by daldude on 2009-10-24
I'm using 64-bit because I have  64-bit system and everyone told me if I have a 64-bit system to take advantage of it. I was using the 32-bit 8.04 before because of the problem wit installing Flash for Firefox before I learned how to install it manually from the terminal window.

Maybe 9.10 will fix my problems, if not I 'll just go back to 8.04 or 8.10 because it upgrades if you run upgrade manager.

---

### Post by daldude on 2009-10-24
> **101011010010 said:**
> Hello there,
I had similar problems on Jaunty x64, I switched to Karmicx64 beta and now rc and everything works perfectly.
I hope this helps.


What is Karmicx64 and where do I get it? Is it still Ubuntu with it's easy to install programs via Add/  Remove or is it like other Linux operating systems where you have to manually install programs with complex commands in a terminal window?

---

### Post by aust77 on 2009-10-24
Jaunty has some problems, but perhaps some installations were done incorrectly. For example, how did you install Wine? Via Synaptic or via the WineHQ site, where you can get the latest release?

---

### Post by daldude on 2009-10-24
First I installed it using Add / Remove and then when it did not work I went the WINE Web Page and tried to figure out how to download the latest version of WINE but it confused me because it said thing about binaries are not available yet and that the source code could be downloaded and I downloaded that but the decompression program asked me where to put the files so I had no idea what to do. Then I tried doing what it said on the web page where they tell you to type something into software sources third party tab so I just cut and pasted what it said under Ubuntu 9.04 and then downloaded a file and did a import key file into the authentication tab. Then it starrted to work but had the hard to read fonts in all the Windows programs I ran.

---

### Post by 3rdalbum on 2009-10-24
WINE is not perfect. Far from it. Also, you should check if you have the "msttcorefonts" package installed - this gives you Microsoft fonts.

"Karmic x64" is just Ubuntu 9.10, 64-bit. x64 is another way to say "64-bit", and Karmic is the codename for Ubuntu 9.10.

---

### Post by daldude on 2009-10-25
I Installed the msttcorefonts package and it fixed the un readable fonts in my Windows Programs, THANKS.

Yes I know WINE is far from perfect but at least WINE was more perfect in Ubuntu 8.04  32-bit then it is in 9.04 64-bit.

---

### Post by psycho5 on 2009-10-25
For your hard disk issue, you can just look at the howto documentation and add your disk to fstab give it a proper label and set it to automount. Just a little bit of work. 

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)


As far as performance goes, if you installed 9.04 fresh, then it shouldn't have any performance problem as far as I have experienced. I found it to be most stable. 

If you have updated, then you might have some software that runs natively on 32 bit and its being adaptive to your 64 bit OS it might cause performance slow down. 

Also, your computer specifications? If you list more info we can help you more. List your hardware in terminal 

```
sudo lshw
```

Then people might be able to take it from there...

---

### Post by DeMus on 2009-10-25
> **daldude said:**
> I don't know if It was a bad install or just the way 9.04 64-bit is but I have many annoying  problems with j9.04.

1 I can't drag my Windows XP NTFS partitions to the desktop to have them automatically mount and then stay that way if I reboot.

 2 WINE (that program that lets you run Windows Programs in Ubuntu) does not work properly, I had to install it twice to get it to work and the Fonts in the Windows programs are that script type font that is 
impossible to read.

3 The System Sounds don't work properly, if I change the log on sound to something different the the default sound it still plays that default sound even though the file listed under Log In is not the default sound. 

I have not noticed any increase in performance over 9.04 32-bit.

The only benefit is I don't have to close Firefox or leave Youtube in order to play a video file iwith movie player. With 8.04 if I tried to lplay a video file with the movie player program while Youtube was loaded in Firefox the video would not play correctely and would platy real slow with no sound. If I'm playing a video file with movie player Youyube videos play without sound under 8.04 32-bit. This is just one anoyence compared to at least 3 with 9.04 64-bit.:mad::confused:

Question 1:
**_Auto mount Windows disks_**
Fire up a terminal, to do this click Applications > Accessories > Terminal
Then type (or copy/paste) the following - 1 line at a time
```

sudo aptitude update
sudo aptitude install ntfs-config
```
Ok so when that returns you to user@pcname, that should be installed                 

Next, make sure you have **_NO_** drives mounted (when then they'll usually appear on your desktop). If you have disks mounted, right-click the icons (one by one) and choose unmount.
They also appear when opening Nautilus.
Then run the program from System > Administration > NTFS Configuration Tool

Enter your password when prompted - and choose the drives that you want to be automounted. Click Apply.

Now simply make sure that "Enable Write Support for Internal Drives" is checked and click OK.

Question 2:
I also don't like Wine, don't have it installed now. I just try to find a program which can replace the program I used on Windows. There is a pretty good website [_**here**_]("http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software")

Question 3:
I always switch off system sounds. I don't like it to switch on or off the computer and get a sound in high volume thrown at me because my music volume switch was still high. Did that with XP, do that here as well.

64/32 bits:
Only when you use programs which use the CPU for intensive calculations you will notice an increase in speed. It's because now the CPU can do 64-bit calculations instead of 2 32-bits calculations. Otherwise I doubt if you notice it.

---

### Post by daldude on 2009-10-25
Thanks DeMus that did the trick. Much easier then trying to figure out all those complex commands to put in to the fstab file after figuring out how to log on as root (when I tried to log on as root at the log in screen it sad "administrators can't log on from this screen"):)

:guitar:

---

