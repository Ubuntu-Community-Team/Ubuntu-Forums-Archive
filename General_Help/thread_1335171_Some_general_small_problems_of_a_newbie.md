---
title: "Some general small problems of a newbie"
date: 2009-11-23
forum: General Help
---

### Post by maximilianyuen on 2009-11-23
So I will be quick:
I installed my ubuntu 9.1 on a external HD on a pc, updated and installed driver (nvidia 185 recommanded driver)
and I have google every questions I asked and either don't understand or not working or no answers


1) what is the key binding to use when Ubuntu 9.1 halt?

I know if terminal is there I can use xkill, or force quick launcher in task bar when mouse and screen not halt
but what if a full screen application halt in black screen?
Or everything halt except mouse cursor when click has no respond?



2) How to turn black screen off?

It seems my LCD will just go black but not blank (still on) after about 10 min.
I have disable the screensaver, power save and can't find out why it goes black.



3) Sometimes when the black screen as describe in 2) happened and after a while, I can't wake up the ubuntu.
It is not in suspend mode as if it is my computer power light will flash.
And mouse and keyboard has no respond at all whatsoever.



4) Backup: how can I backup my ubuntu installed in ext HD?

I checked and partimage just don't work for me and their forum can;t figure out why.
there is a TAR zip method but I want to zip it to another ext HD. And I don't know why I can't do so as it shows error.
now I used grsync to do a 1:1 sync of my ubuntu HD and another HD of the same size.

4a) My grsync backuped HD can't boot. It stoped at bootscreen where "grub loading" should show.

Obviously I checked up there is something need to be done in what boot table but I can't understand...
Can anyone please explain what can I do in plain English?...

4b) following 4a), ignoring the boot thing, so if my ubuntu crash or want to restore, I just need to sync back to my original HD and it will work?




5) What's the difference between ext4, ext3 and ext2?

when I format the usb drive to ext4, it disappear when mount, and ext 3 works fine
is that ext4 is for system only?
And in what situation will I need ext 2?



6) Is it safe for ubuntu to read and write on NTFS drive?
There is something in software centre said it allows to write on NTFS, but I not dare to try yet




7)
 Are there any easy to understand /for beginer site for ubuntu?



ubuntu document is good and resourceful but I only like to read when I have specific problem to solve...
I would like some sites and list all little secret / tips / hints thats for newbie...

All sites I find on google are for advance users... (e.g they just tell you need to do so in root level but not telling you how, and when i google it comes both sudo -i or su...which is confusing sometimes)



8) How the application system work?

If I got 2 ubuntu, and both I got an app want to install, can I just download it onetime and store in USB and trasfer and install on another ubuntu?



Still many to ask but that's it for now :)

Appreciate all your time and help

---

### Post by blazemore on 2009-11-23
1) You can enable the shortcut key to force a restart of the graphical display.
The shortcut is Ctrl+Alt+Backspace, and you enable it like this:
```
sudo apt-get install dontzap
sudo dontzap --disable
```

2) Does the screen fade out, or just turn off? Change the screensaver timeout to something like 2 hours, and make sure the power settings are set under both AC and battery power.

3) This might be fixed by following step 2

4) No idea, sorry. Someone cleverer than me may be able to help

5) ext2 is a Linux filesystem.
 ext3 is ext2 with journaling
ext4 is ext3 with many performance enhancements

6) yes. Write support is enabled by default, I even have all my personal folders mapped to locations on an ntfs drive, and the oly problem I;ve had is when untarring large files.

7) [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by maximilianyuen on 2009-11-23
Thanks a lot blazemore

a little bit follow up:

2) 3)
Well this is a pc desktop(sorry I miss this), so I assume i can ignore battery setting?
And I am positive that my screesaver is not active and display sleep is put to never

and yes it is fading to black, not instant black....

anyway I will try to set the battery side as well


4) you are a genius to me :)

5) then we should use ext 4 at all time it seems...

but still I don't understand why a drive/partition I format to ext 4 will disappear after mounting, and stay visible when not mount....



thanks again

---

### Post by John Bean on 2009-11-23
> **maximilianyuen said:**
> 5) then we should use ext 4 at all time it seems...

Not necessarily. I wouldn't use any journalling file system on a flash disk for example, and some people (including me) are still a bit wary of ext4 due to occasional data loss that doesn't seem to happen on the same hardware formatted ext3.

But it's all down to personal priorities and choice. Choice is good.

---

### Post by jmszr on 2009-11-23
maximilianyuen,

> ubuntu document is good and resourceful but I only like to read when I have specific problem to solve...
I would like some sites and list all little secret / tips / hints thats for newbie...


Welcome aboard!

        I would suggest this sticky by ugm6hr: [http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404) . The links to Psychocats Ubuntu Guide:  [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)  and Free Ubuntu Pocket Guide by Keir Thomas:  [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)  are of particular note but the entire sticky is full of a lot of good information.

Also: [http://ubuntuforums.org/showthread.php?t=790485](http://ubuntuforums.org/showthread.php?t=790485)  (Newbie 101) and: 

[http://ubuntuforums.org/showthread.php?t=714338](http://ubuntuforums.org/showthread.php?t=714338)  (Newbie Terminal Intro)
[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)   (Terminal for Beginners) 

Media howto: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) 

To add the Ubuntu search engine to Firefox: [http://www.ubuntu-search.org/](http://www.ubuntu-search.org/)

---

### Post by maximilianyuen on 2009-12-02
> **blazemore said:**
> 1) You can enable the shortcut key to force a restart of the graphical display.
The shortcut is Ctrl+Alt+Backspace, and you enable it like this:
```
sudo apt-get install dontzap
sudo dontzap --disable
```2) Does the screen fade out, or just turn off? Change the screensaver timeout to something like 2 hours, and make sure the power settings are set under both AC and battery power.

3) This might be fixed by following step 2

4) No idea, sorry. Someone cleverer than me may be able to help

5) ext2 is a Linux filesystem.
 ext3 is ext2 with journaling
ext4 is ext3 with many performance enhancements

6) yes. Write support is enabled by default, I even have all my personal folders mapped to locations on an ntfs drive, and the oly problem I;ve had is when untarring large files.

7) [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)


dontzap seems does not exist...

---

### Post by blazemore on 2009-12-02
Sorry, I didn't realise it wasn't in Karmic.
* Get to the System->Preferences->Keyboard menu. 
* Select the "Layouts" tab and click on the "Layout Options" button. 
* Then select "Key sequence to kill the X server" and enable "Control + Alt + Backspace".

---

### Post by 3rdalbum on 2009-12-02
> **blazemore said:**
> Sorry, I didn't realise it wasn't in Karmic.
* Get to the System->Preferences->Keyboard menu. 
* Select the "Layouts" tab and click on the "Layout Options" button. 
* Then select "Key sequence to kill the X server" and enable "Control + Alt + Backspace".

You don't need to go to all that hassle.

You can kill the X server (and it will restart) by pressing Alt-Printscreen-K or Alt-SysRq-K.

4. Clonezilla is probably your answer. It's a drive imaging tool.

5. Just use Ext4, unless you are going to interoperate with computers that are running older Linux distributions (in which case, use Ext3). Don't use Ext2.

6. It's safe to write to NTFS, but it's slow.

8. Yes, you can download some packages and put them onto a USB drive. You can go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and download the packages corresponding to your version of Ubuntu, and make sure you download the dependencies too (they are listed on the page for that package). Transfer the packages to the other computer, double-click on them and they will install.

---

### Post by maximilianyuen on 2009-12-04
> **blazemore said:**
> Sorry, I didn't realise it wasn't in Karmic.
* Get to the System->Preferences->Keyboard menu. 
* Select the "Layouts" tab and click on the "Layout Options" button. 
* Then select "Key sequence to kill the X server" and enable "Control + Alt + Backspace".

thanks:)

---

### Post by maximilianyuen on 2009-12-04
> **3rdalbum said:**
> You don't need to go to all that hassle.

You can kill the X server (and it will restart) by pressing Alt-Printscreen-K or Alt-SysRq-K.

4. Clonezilla is probably your answer. It's a drive imaging tool.

5. Just use Ext4, unless you are going to interoperate with computers that are running older Linux distributions (in which case, use Ext3). Don't use Ext2.

6. It's safe to write to NTFS, but it's slow.

8. Yes, you can download some packages and put them onto a USB drive. You can go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and download the packages corresponding to your version of Ubuntu, and make sure you download the dependencies too (they are listed on the page for that package). Transfer the packages to the other computer, double-click on them and they will install.


thanks for every answers, it helps a lot:D

but as said, I am having trouble when format my second HD to Ext4
when It is not mount, i can see it
when it is mounted, it just disappeared.....

but that's my first day in Ubuntu...I will try again with a thumb drive later to see if anything wrong, thanks again

---

