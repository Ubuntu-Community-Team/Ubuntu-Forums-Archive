---
title: "Dell Duo Setup Guide"
date: 2011-01-02
forum: General Help
---

### Post by Kirboosy on 2011-01-02
[FONT=Verdana]This is a &#8220;How To&#8221; and also a support/research thread for the Dell Inspiron Duo. This thread is a spin off of [[COLOR=blue]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1628232")

I will say that all the hardware doesn't work quite right but its a work in progress. There will be more added as we figure out more. So keep your eyes on this thread.[/FONT]  [FONT=Verdana]

**Things that don't work**[/FONT]   [FONT=Verdana]
1. Accelerometer - unable to have the screen rotate automatically and grab the data from the device (we are getting close to having it work)

**Things that work**[/FONT]   [FONT=Verdana]
1. Touchscreen's single input
2. Webcam
3. Microphone
4. Touchpad
5. Wireless/Bluetooth
6. Multitouch (Works Partly!)
*I'm not sure how the 3G slot works because I didn't get one on mine. Anyone who has any news about that please share.*[/FONT]   [FONT=Verdana]

**First Steps**[/FONT]   [FONT=Verdana]
Go ahead and update your system completely. 

Pop open Update Manager and install all the updates available.

This will take some time based on your Internet speed. Go grab a cup of coffee and watch this [[COLOR=blue]Documentary on Linux[/COLOR]]("http://video.google.com/videoplay?docid=7707585592627775409#") ;)

[/FONT]   [FONT=Verdana][SIZE=2]**Make sure to reboot before proceeding!**[/SIZE][/FONT][FONT=Verdana]

**Touchscreen**[/FONT]   [FONT=Verdana] --**Caboose885 and shartke**[/FONT] [FONT=Verdana]

**All Versions (Kernel 2.6.24+**[/FONT][FONT=Verdana])
1. Go to the following website and download the daemon driver: [EGalax Touch drivers]("http://www.eeti.com.tw/LinuxDriverDownload.html")

2. Extract the file from its archive and r[/FONT][FONT=Verdana]un the sh script found in the driver folder.[/FONT][FONT=Verdana]```
cd ~/Downloads/eTouch-******/
``````
sudo sh setup.sh
```[/FONT][FONT=Verdana]
3. Reboot your computer
[/FONT]
4[FONT=Verdana]. Run the command in terminal (Or find eGalax Calibration Utility under Applications List) ```
eGTouchU
``` 5.[/FONT][FONT=Verdana] You should be able to select the "Draw Test" and verify that your touchscreen and Multi-Touch is working!

[/FONT][FONT=Verdana]5. If your touchscreen Y axis is backwords y[/FONT][FONT=Verdana]ou **might** need to change the **Direction **line from ***0 to 2***.  (This will fix the inverted Y axis. If its backwards after reboot.)[/FONT][FONT=Verdana]
```
sudo gedit /etc/eGTouch.ini
```[/FONT][FONT=Verdana]
[/FONT]  [FONT=Verdana][COLOR=DarkRed]If you are having a problem getting the drivers to work see the attached GRUB.odt file for how to modify GRUB to get the touchscreen working. The Grub way however will only give you single input and not multi-touch[/COLOR][/FONT][FONT=Verdana]

**TwoFinger Multi-touch Touchpad -- Caboose885**[/FONT]  [FONT=Verdana]

Since Ubuntu 12.04+ the touchpad has supported multi-touch right out of the box. Just head to mouse settings and enable it.[/FONT][FONT=Verdana]

[B]Fixing Bluetooth --JaseP
12.04+
[/B]Bluetooth is working without any additional package installs.[/FONT][FONT=Verdana]

**Fixing the Microphone and Headphones -- DfarmerTX**[/FONT]  [FONT=Verdana]

**All Versions**[/FONT]  [FONT=Verdana]
Run the following command into a Terminal
```
gksudo gedit /etc/modprobe.d/alsa-base.conf 
```At the very bottom of the file add the following line.
```
 options snd-hda-intel model=ideapad
```Save and exit. Reboot your Duo and everything should be working properly. (that is listed as working)

**Broadcom Crystal HD Decoder Driver --Caboose885**[/FONT]  [FONT=Verdana]
Download [driver]("http://www.broadcom.com/docs/support/crystalhd/crystalhd_linux_20100703.zip") and follow README to compile
[/FONT][FONT=Verdana]
**Tablet Mode Recognition -- gjahuja**[/FONT]  [FONT=Verdana]
Add the following lines to /etc/rc.local (make sure to sudo)
```
setkeycodes e073 148 &
setkeycodes e074 149
exit 0
```When you flip the screen and close the lid, a keystroke is sent, and when you open the lid one the screen is flipped another one is sent. Those commands maps these keystrokes to XF86LAUNCH1 and XF86LAUNCH2. rc.local runs those commands on start up so you don't need to run them at every session start.

Now open Keyboard Shortcuts and add two new shortcuts, one for Tablet Mode ON, and other one for Tablet Mode OFF, and tell them to run your scripts for each mode. Now, you can't type XF86LAUNCH# to the shortcut field, what you need to do is click it for it to become active (it will say New shortcut...) and then flip the screen and close the lid. The correct keystroke will be added. Then click to edit the other one and while it's active open the lid, you will see XF86LAUNCH2 in the shortcut field.[/FONT] [FONT=Verdana]

**Chrome and Firefox Addons for touchscreen scrolling --Non.Cents**[/FONT]   [FONT=Verdana]
 Install the following Addons based on your browser
[/FONT] [FONT=Verdana][COLOR=DarkRed]Chrome:[/COLOR][/FONT][FONT=Verdana] [ChromeTouch]("https://chrome.google.com/extensions/detail/ncegfehgjifmmpnjaihnjpbpddjjebme")
[/FONT] [FONT=Verdana][COLOR=DarkRed]Firefox: [/COLOR][/FONT][FONT=Verdana]_[Grab and Drag]("https://addons.mozilla.org/en-US/firefox/addon/grab-and-drag/")_

[/FONT]   [FONT=Verdana][COLOR=red]Thanks to the following for their awesomeness![/COLOR][/FONT][FONT=Verdana]
[/FONT] [FONT=Verdana][COLOR=red]shartke[/COLOR][/FONT][FONT=Verdana]
[/FONT] [FONT=Verdana][COLOR=red]ninjaaron[/COLOR][/FONT][FONT=Verdana]
[/FONT] [FONT=Verdana][COLOR=red]w1ll1am[/COLOR][/FONT][FONT=Verdana]
[/FONT] [FONT=Verdana][COLOR=red]DfarmerTX[/COLOR][/FONT][FONT=Verdana]
[/FONT] [FONT=Verdana][COLOR=#ff0000]Kallun[/COLOR][/FONT][FONT=Verdana]
[/FONT] [FONT=Verdana][COLOR=#ff0000]Non.Cents[/COLOR][/FONT][FONT=Verdana]
[/FONT] [FONT=Verdana][COLOR=Red]JaseP[/COLOR][/FONT][FONT=Verdana]

[/FONT]   [FONT=Verdana][SIZE=4]**Optional Packages to Install** [/SIZE][/FONT][FONT=Verdana]
**Via Synaptic Package Manager**[/FONT] [FONT=Verdana] (Applications &#8594; System &#8594; Synaptic Package Manager)
1. **StartupManager **&#8211; Allows you to change the Grub boot menu default selection and reduce the grub default time.
2. **ubuntu-restricted-extras** &#8211; Adds special file support. MP3, MP4, AVI, Flash, Java, and more!
3. **VLC **&#8211; Lighter and better for less powerful hardware (like the Duo) I can get full 1080P [[COLOR=blue]Big Buck Bunny[/COLOR]]("http://www.bigbuckbunny.org/index.php/download/") to play flawlessly on my Duo using VLC
4. **uTouch **&#8211; support for multi-touch. (in theory)
5. **preload -** caches your most used programs to RAM, therefore causing things to open faster.
6. [**EasyStroke**]("https://launchpad.net/%7Eeasystroke/+archive/ppa") - Gesture Recognition for mouse movements

**Other Packages**[/FONT]   [FONT=Verdana]
[[COLOR=blue]Ubuntu Tweak[/COLOR]]("http://launchpad.net/ubuntu-tweak/0.5.x/0.5.9/+download/ubuntu-tweak_0.5.9-1_all.deb")[/FONT] [FONT=Verdana] --Allows you to have some more control over your computer using the GUI and not terminal.
[Florence Virtual Keyboard]("http://florence.sourceforge.net/english.html")[/FONT] [FONT=Verdana]--one of the better onscreen keyboards for touchscreens
[Kvkbd]("http://kde-apps.org/content/show.php/Kvkbd?content=56019")[/FONT] [FONT=Verdana]--Virtual Keyboard used by the KDE Desktop Enviroment[/FONT]

---

### Post by ninjaaron on 2011-01-02
Cool thread. Thanks.

> **Caboose885 said:**
> **Things that don't work**
1. Multi-touch – the current kernel has problems. It will be resolved next kernel. (in theory)
2. Accelerometer 
3. Rotation of screen (ties into the Accelerometer but it also **INCLUDES MANUAL ROTATION**.)


WAT!?:mad:

you can't use the monitor settings to rotate the screen!?

This does not please me. I plan on using the duo heavily as a reader whenever it finally shows up in my Jerusalem mailbox. I'll get this thing spinning, one way or another

---

### Post by Kirboosy on 2011-01-02
The screen **Does** rotate but the mouse doesn't work properly. I guess I should of clarified.  Its like the mouse doesn't rotate with the screen so it makes it awkward to use it. I'm trying to figure out a fix for this issue

---

### Post by ninjaaron on 2011-01-03
> **Caboose885 said:**
> The screen **Does** rotate but the mouse doesn't work properly. I guess I should of clarified.  Its like the mouse doesn't rotate with the screen so it makes it awkward to use it. I'm trying to figure out a fix for this issue

'mouse' as in track-pad or touch-screen?

If it's just the track-pad, that's normal. None of my computers correct track-pad functionality with screen rotation. Of course, with a normal wireless mouse, you just turn the screen so up is up, face the right direction, and it doesn't make a difference.

---

### Post by Kirboosy on 2011-01-03
> **ninjaaron said:**
> 'mouse' as in track-pad or touch-screen?

If it's just the track-pad, that's normal. None of my computers correct track-pad functionality with screen rotation. Of course, with a normal wireless mouse, you just turn the screen so up is up, face the right direction, and it doesn't make a difference.

Its actually both. If you plug a USB mouse in then it works properly.

I'm hoping this next kernel will magically solve most of our problems.

---

### Post by Chuchaqui on 2011-01-03
Is anyone else having problems with the f keys? They are set to the multimedia by default, and f with the function. I reverted the multimedia-f keys in the BIOS, but it seems to only fix the problem for the first boot into Ubuntu. After the first boot, the keys seem to revert back to the multimedia keys first and the f* keys with the function key (only in Ubuntu, not Windows). I've checked the BIOS and it's still set to be the function keys be default as well.

I am also having problems with two-finger scrolling. Though after snooping around some it seems that it's a known bug with the current version of the synaptic drivers. At least from what I understand. I'll post a link if I have time/remember/find it later.

These problems may be limited to Ubuntu 10.10, not UNE. It's running more smoothly for me in full 10.10 than it was in UNE for me for some reason (also I hate UNE, so I'm a little biased). 

Cheers

---

### Post by ninjaaron on 2011-01-03
> **Caboose885 said:**
> Its actually both. If you plug a USB mouse in then it works properly.

I'm hoping this next kernel will magically solve most of our problems.

Oh. That sucks. Here's hoping for the next kernel.

Mine is actually in the country right now. I get a letter today from the Israeli post office security department. I had to call them to confirm I was expecting the package. They told me that they would now send it to a post office where I could pick it up, and they would send me another letter to tell me where that was. Obviously, they will not send the package to the post office where I have my PO box. That would make too much sense. They will send it somewhere else and tell me where to go (via letter sent to my box). This country is apparently run by the same sales rep at Dell responsible for refunding unused Windows licenses.

On the upside, I'm sure that whenever I do manage to get my computer, enough time will have elapsed that all the bugs will certainly be fixed.:p

---

### Post by Kirboosy on 2011-01-03
> **Chuchaqui said:**
> Is anyone else having problems with the f keys? They are set to the multimedia by default, and f with the function. I reverted the multimedia-f keys in the BIOS, but it seems to only fix the problem for the first boot into Ubuntu. After the first boot, the keys seem to revert back to the multimedia keys first and the f* keys with the function key (only in Ubuntu, not Windows). I've checked the BIOS and it's still set to be the function keys be default as well.

I am also having problems with two-finger scrolling. Though after snooping around some it seems that it's a known bug with the current version of the synaptic drivers. At least from what I understand. I'll post a link if I have time/remember/find it later.

These problems may be limited to Ubuntu 10.10, not UNE. It's running more smoothly for me in full 10.10 than it was in UNE for me for some reason (also I hate UNE, so I'm a little biased). 

Cheers

This is my first go round with UNE. My first netbook. I think UNE is ok (I normally use gnome so its not that different)

I have noticed that issue with my F keys. Like you said changed in the BIOS yet it doesn't last. I think its something to do with Ubuntu because in Windows *shudder* it doesn't have that issue. 

I have an idea on how to solve the touchpad issues but I need to play with my Duo first. (I'm at work right now so I can't play with my Duo.) I need to just start bringing my Duo to work with me. Lol

---

### Post by Chuchaqui on 2011-01-03
I am also having problems with the headphone slot. Anyone else? I'll try to look into it some :-/ .

---

### Post by w1ll1am on 2011-01-03
> **Chuchaqui said:**
> I am also having problems with the headphone slot. Anyone else? I'll try to look into it some :-/ .

My headphone port seems to be working fine. what is it yours is doing? nothing at all or sound static or what?

---

### Post by w1ll1am on 2011-01-04
For those of you who are using or would like to use kvkbd as your onscreen keyboard and want it in your unity dock here is how.

1)first open a terminal and run with no sudo

```
 nautilus 
```navigate to /home/XXXXX/.gconf/desktop/unity/lanucher/favorites. (you will have to hit ctrl + h to show hidden files and folders and XXXXXX=your user name) create a new folder called

app-kvkbd.desktop

open another folder up and copy the .xml file inside and put it into the folder you just created. once it is in the new folder open it with gedit remove everything and paste in

```
 <?xml version="1.0"?>
<gconf>
    <entry name="desktop_file" mtime="1293677807" type="string">
        <stringvalue>/usr/share/applications/kvkbd.desktop</stringvalue>
    </entry>
    <entry name="type" mtime="1293677807" type="string">
        <stringvalue>application</stringvalue>
    </entry>
    <entry name="priority" mtime="1294117426" type="float" value="3"/>
</gconf>
```then save and close.

2) open a new terminal and run 

```
 gksudo gedit /.gconf/desktop/unity/launcher/favorites/app-kvkbd.desktop/%gconf.xml 
``````
 nautilus 
```navigate to home/.gconf/desktop/unity/launcher/favorites find the app-kvkbd.desktop file and change the icon to the kvkbd icon. 

the icon is located in /usr/share/icons/Humanity/apps/48 and it is called preferences-desktop-keyboard.svg

3) Run

```
 gconf-editor 
```go to desktop/unity/launcher and click on the favorites folder (do not expand) double click on the favorites_list and add app-kvkbd.desktop.

Reboot or logout and back in and the icon should be there if you have any problems let me know.

---

### Post by Kirboosy on 2011-01-04
> **Chuchaqui said:**
> I am also having problems with the headphone slot. Anyone else? I'll try to look into it some :-/ .

I was about to ask if you had it plugged in the right port but then I realized there is only one :P

I'm listening to music right now through headphones. I just plugged them in for the first time and it worked no problem. Are you up to date with your updates?

---

### Post by Kallun on 2011-01-04
Just in case you wanted to add it, you can also create a bootable flash drive using the dd command in OS X's terminal :)

Convert the .iso file to .img using the convert option of hdiutil (e.g., **hdiutil convert -format UDRW -o ~/path/to/target.img ~/path/to/ubuntu.iso**)

Note: OS X tends to put the .dmg ending on the output file automatically.

Run **diskutil list** to get the current list of devices
Insert your flash media

Run **diskutil list** again and determine the device node assigned to your flash media (e.g. /dev/disk2)
Run**diskutil unmountDisk /dev/diskN** (replace N with the disk number from the last command; in the previous example, N would be 2)
Execute **sudo dd if=/path/to/downloaded.img of=/dev/rdiskN bs=1m** (replace /path/to/downloaded.img with the path where the image file is located; for example, ./ubuntu.img or ./ubuntu.dmg). < **You can easily specify the file path in terminal by simply dragging the file into the shell**
Using /dev/rdisk instead of /dev/disk may be faster.
If you see the error dd: Invalid number '1m', you are using GNU dd. Use the same command but replace bs=1m with bs=1M.
If you see the error dd:/dev/diskN: Resource busy, make sure the disk is not in use. Start the 'Disk Utility.app' and unmount (don't eject) the drive.
Run diskutil eject /dev/diskN and remove your flash media when the command completes
Restart your Mac and press alt while the Mac is restarting to choose the USB-Stick


(Pulled from the 'Get UNE' page from Ubuntu.com looks somewhat daunting, but nice and easy if you can just follow some simple instructions :] )

(Also this may take a while! If you run the last command 'dd if= / of' and get a blinking cursor on the next line, leave it, that means its doing it's job, you'll know its finished when the shell tells you how much data went in and out)

OP - Apologies if this post is a bit messy, feel free to disregard if you feel this is unnecessary.

---

### Post by ninjaaron on 2011-01-04
Interesting post. I indeed read it, and I think I understood it well enough... now I'm just trying to figure out what it might have to do with the Inspiron duo :)

---

### Post by Kirboosy on 2011-01-04
> **ninjaaron said:**
> Interesting post. I indeed read it, and I think I understood it well enough... now I'm just trying to figure out what it might have to do with the Inspiron duo :)

You finally got your Duo!??!! :D :D :D

---

### Post by Kirboosy on 2011-01-04
> **Kallun said:**
> Just in case you wanted to add it, you can also create a bootable flash drive using the dd command in OS X's terminal :)

Convert the .iso file to .img using the convert option of hdiutil (e.g., **hdiutil convert -format UDRW -o ~/path/to/target.img ~/path/to/ubuntu.iso**)

Note: OS X tends to put the .dmg ending on the output file automatically.

Run **diskutil list** to get the current list of devices
Insert your flash media

Run **diskutil list** again and determine the device node assigned to your flash media (e.g. /dev/disk2)
Run**diskutil unmountDisk /dev/diskN** (replace N with the disk number from the last command; in the previous example, N would be 2)
Execute **sudo dd if=/path/to/downloaded.img of=/dev/rdiskN bs=1m** (replace /path/to/downloaded.img with the path where the image file is located; for example, ./ubuntu.img or ./ubuntu.dmg). < **You can easily specify the file path in terminal by simply dragging the file into the shell**
Using /dev/rdisk instead of /dev/disk may be faster.
If you see the error dd: Invalid number '1m', you are using GNU dd. Use the same command but replace bs=1m with bs=1M.
If you see the error dd:/dev/diskN: Resource busy, make sure the disk is not in use. Start the 'Disk Utility.app' and unmount (don't eject) the drive.
Run diskutil eject /dev/diskN and remove your flash media when the command completes
Restart your Mac and press alt while the Mac is restarting to choose the USB-Stick


(Pulled from the 'Get UNE' page from Ubuntu.com looks somewhat daunting, but nice and easy if you can just follow some simple instructions :] )

(Also this may take a while! If you run the last command 'dd if= / of' and get a blinking cursor on the next line, leave it, that means its doing it's job, you'll know its finished when the shell tells you how much data went in and out)

OP - Apologies if this post is a bit messy, feel free to disregard if you feel this is unnecessary.

I didn't think to add Mac because I figured most of them wouldn't be caught dead with a Dell because they like their Mac so much. haha

---

### Post by Kallun on 2011-01-04
Haha, well, that's a good enough reason! :P Thanks for this post by the way (and all the people that have been working to get this baby running smooth) My Duo is in the post, can't wait to start playing with it :D

---

### Post by Kirboosy on 2011-01-04
Ok everyone I added to my original post for fixing the multi-touch touchpad. Enjoy :D

---

### Post by Kallun on 2011-01-04
Nice!

---

### Post by Non.Cents on 2011-01-04
Has anyone thought about using Moblin on the Duo? It seems an interesting idea considering Moblin was originally an intel project, and the Duo has an intel chipset. You can find support for moblin on this forum and conical offers support for moblin as well.

This might just be over complicating things but I might just have to give it a look see. I love ubuntu but it would be interesting to see how another netbook distro would do.

---

### Post by Kirboosy on 2011-01-04
> **Non.Cents said:**
> Has anyone thought about using Moblin on the Duo? It seems an interesting idea considering Moblin was originally an intel project, and the Duo has an intel chipset. You can find support for moblin on this forum and conical offers support for moblin as well.

This might just be over complicating things but I might just have to give it a look see. I love ubuntu but it would be interesting to see how another netbook distro would do.

I thought about it. I still might mess with it just to see how well it runs. I will let you know if I do run it.

Also is it still actively developed? It seems like a dead project since they haven't had a new release since 11-04-2009

---

### Post by Non.Cents on 2011-01-04
> **Caboose885 said:**
> Ok everyone I added to my original post for fixing the multi-touch touchpad. Enjoy :D

It is possible I am doing something wrong but the directions don't seem to be working for me. I will say that I had to mkdir to save that file that is made in the directions, and i had to use ctrl+alt+(fn)+F2 to open a tty session. 

I don't think it should matter which tty session i was in (1-7) but regardless, it didn't do anything for me.

As for moblin, this is one of the reason one should check distro watch before installing a distro. The ubunut-moblin remix latest was 9.10 so its a bit old. Its probably also safe to assume that conical took what it could from it to make the new UNE. Oh well.

---

### Post by Kirboosy on 2011-01-04
You actually don't need to save the file in the directions. Its like a temporary file. That might be why its not working.

Did you try logging out or rebooting?

---

### Post by Non.Cents on 2011-01-04
> **Caboose885 said:**
> You actually don't need to save the file in the directions. Its like a temporary file. That might be why its not working.

Did you try logging out or rebooting?

I did. I also have removed file and directory rebooted and re-did the directions to no avail. 2 fingers does the same thing it did before ie nothing at all lol.:confused:

---

### Post by w1ll1am on 2011-01-04
I seem to be having the same problem getting the touch pad working any suggestions?

Also has anyone though about putting a SSD into there duo for better battery life and if so any thoughts?

Here is a video I made showing off the duo and the dock if anyone is interested.
[http://www.youtube.com/watch?v=E6HLXtIprUg](http://www.youtube.com/watch?v=E6HLXtIprUg)

---

### Post by Chuchaqui on 2011-01-04
Sound comes out of the speakers when plug in the headphones. I cannot get it to come out of the headphones for some reason :-/ .

---

### Post by garwal on 2011-01-04
Made the trip to the new thread. I am going to try a few new things today , you might be interested, giving megoo a shot and also Android. I knew this was going to be a fun toy. Will keep you all posted.
garwal[SIZE="5"][/SIZE]

Ok megoo loads fine and it appears the cursor to the left top corner is an issue in this as well. I actually like the gui better than any * have seen . I think I would solve a lot of the problems witgh a full install and updates. I loose any input from touch or key board at the second page of install. Any suggestions here. It does well running from the usb flash drive.*

---

### Post by Kirboosy on 2011-01-04
I am so sorry everyone. I had a brainfart. I was trying two different ways to fix my mousepad. I thought the other way fixed it but I was wrong. 

Please disregard what I posted early and do the new steps I just added. I know the new way I posted works. Enjoy (The correct version ;) )

---

### Post by Kirboosy on 2011-01-04
> **Chuchaqui said:**
> Sound comes out of the speakers when plug in the headphones. I cannot get it to come out of the headphones for some reason :-/ .

Could you possibly try different Headphones? I don't have any issues and I didn't do anything special. Maybe you changed something and it broke it.

---

### Post by Chuchaqui on 2011-01-05
I've tried different headphones, also tried taking them out and plugging them in repeatedly. It may be due to the fact that I'm using Gnome, not UNE. Perhaps the drivers aren't properly configured for Gnome, since this thing is sort of a netbook.

---

### Post by Chuchaqui on 2011-01-05
I found a fix for the problem [https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/131239](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/131239)

---

### Post by ninjaaron on 2011-01-05
> **Caboose885 said:**
> You finally got your Duo!??!! :D :D :D

Ha! hell no! Israeli customs officers are playing with it for a few days so they can figure out how much they want to tax me.

The readers of this thread will know when I have it.

---

### Post by Kirboosy on 2011-01-05
> **Chuchaqui said:**
> I found a fix for the problem [https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/131239](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/131239)

Awesome find. I didn't think straight Ubuntu and UNE were that much different but I guess I was wrong.


From what I have been reading it seems like the eGalax driver is already installed in 10.10. I'm not sure if that just means Ubuntu in general or if its 10.10 Desktop. 

It seems like the more I read about it the less work we should have to do. I really would like to get my multi-touch working soon but work has now picked up to where I don't have much time to work on it. Hopefully I will get some time this weekend.

---

### Post by Non.Cents on 2011-01-05
Interesting note. I followed the directions at the beginning of [_[COLOR="Blue"]this[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1507489&highlight=multi+touch+touchscreen") thread and the result was..... interesting. The side doc becomes almost completely unpredictable. The screen though seemed (maybe) to recognize dual touch. when two fingers were on the screen the pointer shook between your two fingers. So i will play with it, the egalix calibration and such a little more and see if i get some positive results.

---

### Post by Kirboosy on 2011-01-05
I had that same issue when I installed a driver for eGalax screens. The dock would randomly disappear, then come back or flutter on me. Very unstable and annoying. I think since its going between your two fingers its seeing the multi-touch. On mine if I place two fingers on the screen the mouse still stays to the one finger and never flutters.

I found a driver on [eGalax Website]("http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm") but I wonder if it would have a calibration tool in it.

The driver I linked to **DOES** have a calibration tool. I'm going to try and compile it and see how it goes. I'm actually getting really excited.

---

### Post by Non.Cents on 2011-01-05
I used [[COLOR="Blue"]_this site_[/COLOR]]("http://samiux.blogspot.com/2010/11/howto-ubuntu-1010-on-gigabyte-touchnote.html"),which was linked to in a post from the last thread, to get the calibration down.....ish. Things seem to still be unpredictable at best. Working in the shell (side doc, and such) it seems to work. Inside of programs however, things get tricky. The touchscreen, touch-pad, and even an attached usb mouse don't work properly. They don't click when you do some things, and do when you click on others.
Shaking was perhaps the wrong word. The pointer flashes to both points your finger is touching. Multi touch commands still don't do anything. (scrolling doesn't work, expanding etc)

All in all if this is progress I don't have the know how to move much further forward. Good signs, the pointer moving, continued working of single touch(ish), and no complete collapse, but usability of the gui is now..... pretty bad
:confused: I'm confused but I will keep looking i haven't given up on this track yet

---

### Post by w1ll1am on 2011-01-05
> [B]
TwoFinger Multi-touch touchpad (Optional if you want it)
[/B]Run the command
```
sudo apt-add-repository ppa:plippo/t101mt
```Then....
```
sudo apt-get update
```Then....```
sudo apt-get install eeepc-touchpad-twofingers
```REBOOT!!

Sweet worked great thanks!

---

### Post by robocop408 on 2011-01-05
[s]I just went to buy this and I was shocked to see the price jump $100($40 shipping!). It made me ask myself, is it worth $650 with linux on it? from the reviews I read its not worth that much with win 7 and dell's sluggish tablet UI layer, but the hardware got great reveiws. My question, does ubuntu make a signifigant ($100 or more) difference to the user experience, and how does it stack up next to a six year old, mid range(bulky)laptop for daily use?[/s]

---

### Post by w1ll1am on 2011-01-05
> **robocop408 said:**
> [s]I just went to buy this and I was shocked to see the price jump $100($40 shipping!). It made me ask myself, is it worth $650 with linux on it? from the reviews I read its not worth that much with win 7 and dell's sluggish tablet UI layer, but the hardware got great reveiws. My question, does ubuntu make a signifigant ($100 or more) difference to the user experience, and how does it stack up next to a six year old, mid range(bulky)laptop for daily use?[/s]

I am glad you bought it I think it is a great computer and the UNE makes the touch experience extremely user friendly. I am not a big fan of unity but it is very nice on the duo. Let us know how you like it. 
also you should take a look at this
[http://www.youtube.com/watch?v=E6HLXtIprUg](http://www.youtube.com/watch?v=E6HLXtIprUg)

---

### Post by Kirboosy on 2011-01-06
> **robocop408 said:**
> [s]I just went to buy this and I was shocked to see the price jump $100($40 shipping!). It made me ask myself, is it worth $650 with linux on it? from the reviews I read its not worth that much with win 7 and dell's sluggish tablet UI layer, but the hardware got great reveiws. My question, does ubuntu make a signifigant ($100 or more) difference to the user experience, and how does it stack up next to a six year old, mid range(bulky)laptop for daily use?[/s]

I think that you will be pleasantly surprised. My dad has a SSD in his laptop and my Duo can boot up slightly faster than his (and mine has a 3 second GRUB delay). As soon as we work all the bugs out it will be even awesomer (if thats a word. ;) )

---

### Post by th@dd3us on 2011-01-06
Awesomer -
               Something that is more awesome than awesome but not awesome enough to be the awesomest.

---

### Post by Kirboosy on 2011-01-06
> **th@dd3us said:**
> Awesomer -
               Something that is more awesome than awesome but not awesome enough to be the awesomest.

Well its already the awesomest netbook so it can only get awseomer. :D

On a serious note. I'm still trying to figure out how you would rotate the screen/touchscreen/toucpad to work properly. Multi-touch has sorta dropped down to a lower level for me. I think rotation is a bit more important right now. Maybe I will figure out the accelerometer along the way but we will see.

---

### Post by Non.Cents on 2011-01-06
I still want to find multi touch. It would also be cool if we could figure out a way to right click.

That said i don't know that there is much of a point in working with drivers we have no idea if are even compatible with this device. Does anyone know, or know how to find out, what the maker of the touch screen in the Duo is. The egalax drivers aren't going to work if the device isn't egalax, or compatible with them.

---

### Post by Kirboosy on 2011-01-06
> **Non.Cents said:**
> I still want to find multi touch. It would also be cool if we could figure out a way to right click.

That said i don't know that there is much of a point in working with drivers we have no idea if are even compatible with this device. Does anyone know, or know how to find out, what the maker of the touch screen in the Duo is. The egalax drivers aren't going to work if the device isn't egalax, or compatible with them.

It is a eGalax screen. I ran a command in my terminal to list the input devices and it was a eGalax screen. I'm gonna cut most out of the output cause there is a ton....

```

 **cat /proc/bus/input/devices **
[SIZE=3]
I: Bus=0003 Vendor=0eef Product=725e Version=0210
N: Name="eGalax Inc. USB TouchController"
P: Phys=usb-0000:00:1d.2-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input5
U: Uniq=
H: Handlers=mouse0 event5 
B: EV=1b
B: KEY=421 0 30001 0 0 0 0 0 0 0 0
B: ABS=100 3f
B: MSC=10[/SIZE]
```

---

### Post by ninjaaron on 2011-01-06
> **Non.Cents said:**
> I still want to find multi touch. It would also be cool if we could figure out a way to right click.

That said i don't know that there is much of a point in working with drivers we have no idea if are even compatible with this device. Does anyone know, or know how to find out, what the maker of the touch screen in the Duo is. The egalax drivers aren't going to work if the device isn't egalax, or compatible with them.

If you go into the mouse settings, you can turn on "initiate secondary click by holding down primary button."

That's how most touch-screens do it.

---

### Post by Kirboosy on 2011-01-06
> **ninjaaron said:**
> If you go into the mouse settings, you can turn on "initiate secondary click by holding down primary button."

That's how most touch-screens do it.

Thanks for reminding me. I forgot to include that in my setup guide. I change it without thinking.

---

### Post by garwal on 2011-01-06
I removed MeeGo yesterday as I was not able to find any help on resolving the screen issue. I am sure it is very similar to Unbuntu and it is much easier for tired eyes to read the screen so I have given Unbuntu a shot and all is well except that I am not able to change screen resolution and maintain a full screen, What am I missing here? All else seems to be fine, oh quick question for anyone. Does your LAN connection work when you have the Duo docked ? And are the speakers in the dock working as well.
Thanks
garwal

---

### Post by Non.Cents on 2011-01-06
> **garwal said:**
> Does your LAN connection work when you have the Duo docked ? And are the speakers in the dock working as well.
Thanks
garwal

I have the dock and have tried, right now in ubuntu, its not much but a charger. The speakers dont work, neither does the LAN (you have to fiddle with that in windows to get it to work properly), or any of the ports for that matter. Until our buddy figures out the screen rotation the doc isn't even a good holder while running ubuntu.....

---

### Post by garwal on 2011-01-06
> **Non.Cents said:**
> I have the dock and have tried, right now in ubuntu, its not much but a charger. The speakers dont work, neither does the LAN (you have to fiddle with that in windows to get it to work properly), or any of the ports for that matter. Until our buddy figures out the screen rotation the doc isn't even a good holder while running ubuntu.....

I had not tried but that is what I suspected. I am sure we will get there, regardless it is a much better OS than Windows. I have been a Linux user for 15 years and would be lost without it. My main concern in getting the screen resolution where I can read it. At 62 my eyes are not what they once were and I do not want to have to wear a magnifying head set. I know I would be much happier if I could just get the icons and text to be larger.
Have a good day all
garwal

---

### Post by Non.Cents on 2011-01-06
I wholeheartedly agree. Linux is def. superior, and just plain more fun. This problems solving, and the like is fun to me and nothing feels better than when you finally get everything just the way you want it(which is impossible in those proprietary os's). But as it goes, sometimes linux needs just a bit more than love :). But as linux becomes bigger and bigger in the consumer marketplace, the need to finagle it to get things to work on a consumer device will become a thing of the past.

---

### Post by w1ll1am on 2011-01-06
> **garwal said:**
> I removed MeeGo yesterday as I was not able to find any help on resolving the screen issue. I am sure it is very similar to Unbuntu and it is much easier for tired eyes to read the screen so I have given Unbuntu a shot and all is well except that I am not able to change screen resolution and maintain a full screen, What am I missing here? All else seems to be fine, oh quick question for anyone. Does your LAN connection work when you have the Duo docked ? And are the speakers in the dock working as well.
Thanks
garwal

If you have the Duo docked before you turn it on the Ethernet works. The other ports USB, SD card reader, and volume control all work all the time.

---

### Post by w1ll1am on 2011-01-06
I was wanting the onscreen keyboard that I use "kvkbd" to open automatically at the login screen and I was able to do this but it stays up after login and I want it to close does anyone have an idea how to do this?

To get kvkbd to start at the login I added the following to the bottom of my /etc/gdm/Init/Default

```
 exec kvkbd& 
```

Now all I need is for it to kill automatically after login any help would be great thanks.

---

### Post by garwal on 2011-01-06
> **w1ll1am said:**
> I was wanting the onscreen keyboard that I use "kvkbd" to open automatically at the login screen and I was able to do this but it stays up after login and I want it to close does anyone have an idea how to do this?

To get kvkbd to start at the login I added the following to the bottom of my /etc/gdm/Init/Default

```
 exec kvkbd& 
```

Now all I need is for it to kill automatically after login any help would be great thanks.

I just put kvkbd in the start programs, that way it does not open until I select the icon which is up by the volume. This works good for me if I recall correctly start up programs is in the system folder.
Hope this helps..
garwal

---

### Post by w1ll1am on 2011-01-06
The way I have it now kvkbd starts up at the login screen perfectly positioned but once logged in that position is not good for use with everything else so i want it to close.  if I open kvkbd after logged in it is in the position I have set up for use with everything else. So there two different setups one for use on the login and the other for everything else.

---

### Post by Kirboosy on 2011-01-07
> **w1ll1am said:**
> The way I have it now kvkbd starts up at the login screen perfectly positioned but once logged in that position is not good for use with everything else so i want it to close.  if I open kvkbd after logged in it is in the position I have set up for use with everything else. So there two different setups one for use on the login and the other for everything else.

I'm just talking (because I have no idea if this would work.) But what if we made a screenlet for launching the on screen keyboard. (Or you could make it a keyboard combination.) That way you can launch the keyboard quickly if you need to from tablet mode.

---

### Post by Non.Cents on 2011-01-07
> **Caboose885 said:**
> I'm just talking (because I have no idea if this would work.) But what if we made a screenlet for launching the on screen keyboard. (Or you could make it a keyboard combination.) That way you can launch the keyboard quickly if you need to from tablet mode.

Sounds like a good idea to me. The way it works in windows is actually really convenient. Just a tiny part visible on the side click it and it comes out. The kvkbd has a small doc, but it is awkwardly placed, hard to move, and too big. it needs to be improved. That is at least my opinion.....

once you turn it on tho, it stays in the status bar and clicking up there brings it out so that's good.

---

### Post by w1ll1am on 2011-01-07
Having kvkbd start on the login screen does not mean that it is open it can be if you had it open on the last login but if you didn't the panel launcher is in the bottom right of the login screen and you can open it up if needed.

---

### Post by Non.Cents on 2011-01-07
I found [[COLOR="Blue"]_this touch keyboard_[/COLOR]]("http://florence.sourceforge.net/english.html") actually while searching on the dual touch fix. It is completely customizable, and scalable. I havent set it up but it looks pretty good.

---

### Post by ninjaaron on 2011-01-08
> **Caboose885 said:**
> I'm just talking (because I have no idea if this would work.) But what if we made a screenlet for launching the on screen keyboard. (Or you could make it a keyboard combination.) That way you can launch the keyboard quickly if you need to from tablet mode.

Why not just make a normal taskbar/dock launcher?
:confused:

---

### Post by ninjaaron on 2011-01-08
> **Non.Cents said:**
> I found [[COLOR="Blue"]_this touch keyboard_[/COLOR]]("http://florence.sourceforge.net/english.html") actually while searching on the dual touch fix. It is completely customizable, and scalable. I havent set it up but it looks pretty good.

I built it. 'Tis the sex, in terms of looks and functionality. Function, navigation, and number keys can be turned on and off. The transparency kills (in a good way). There is a toggle icon in the notification area (hideous though it is. I'm sure it can be changed with enough messing around).

Num lock and caps lock also affect my hardware keyboard, but they don't change the LED's, and vis-versa. These keys also make the program crash sometimes.

Still, pretty cool over all. Way cooler than kvkbd or onboard.

Here's the screenshot:
[http://ubuntuone.com/p/XD5/](http://ubuntuone.com/p/XD5/)

---

### Post by Non.Cents on 2011-01-08
So this isn't specific to the Duo BUT in my estimation its a must have. This allows for single touch scrolling in firefox, it seems to me to be very clean and have lost of options. As it requires an actual click to be activated the touch pad does not set it off every time you use it.

[https://addons.mozilla.org/en-US/firefox/addon/1250/eula/68777?src=addondetail](https://addons.mozilla.org/en-US/firefox/addon/1250/eula/68777?src=addondetail)

This one i have not tried but is probably worth a try

[https://chrome.google.com/extensions/detail/ncegfehgjifmmpnjaihnjpbpddjjebme](https://chrome.google.com/extensions/detail/ncegfehgjifmmpnjaihnjpbpddjjebme)

---

### Post by DFarmerTX on 2011-01-08
FYI, I've been searching for the best onscreen keyboard to use in Ubuntu and found florence.  [http://florence.sourceforge.net/english.html](http://florence.sourceforge.net/english.html)

Don't even mess with any of the other ones, this one rocks!

You can find a few deb packages out there if you don't want to build from scratch.

---

### Post by Non.Cents on 2011-01-08
Yup! i found that one the other day and it does indeed rock! Don't be intimidated if your new to linux either, their instructions on how to build it are great. Florence is far superior to the others that i have tried in functionality and the ever important coolosity.

A question for the masses, is there a way, and if so, how do i order the applications in the unity sidebar. For instance, I have minefield and chromium on the sidebar, but id like them to be up at the top next to firefox. In other words I want to make the decision where things go, but it seems to think it knows better than me :/

---

### Post by robocop408 on 2011-01-08
Has anyone tried cell writer? it sounds like a good alternative if you buy a stylus.

---

### Post by Kirboosy on 2011-01-08
> **Non.Cents said:**
> A question for the masses, is there a way, and if so, how do i order the applications in the unity sidebar. For instance, I have minefield and chromium on the sidebar, but id like them to be up at the top next to firefox. In other words I want to make the decision where things go, but it seems to think it knows better than me :/

Just click and hold on the icon on the dock. Pull it to the right (away from the bar) and move it to where you want it. When you start placing it back in the dock the icons should part a spot for it. Then release your mouse and it will set there

---

### Post by w1ll1am on 2011-01-09
So I checked out the florence keyboard and I do like it but one of the major problems is that you can not resize it exactly how you like if I stretch it wider no matter what it also gets taller this is no good. Is anyone else having this problem?

---

### Post by ninjaaron on 2011-01-09
Yeah, that's how it works. If you don't like it, onboard, the gnome default virtual keyboard can be resized however you like. It's an eyesore, but it works well.

---

### Post by Non.Cents on 2011-01-09
You actually can resize it you just have to have decoration on. It is a bit hard to do it without the touchpad, but it can be done.

---

### Post by Kallun on 2011-01-09
In regard to the Florence keyboard, anyone else looking to change the menubar icon? I love the keyboard... but that smiley face is horrible :/

---

### Post by w1ll1am on 2011-01-09
> **Non.Cents said:**
> You actually can resize it you just have to have decoration on. It is a bit hard to do it without the touchpad, but it can be done.

It can be resized but it can not be resized to exact sizes stretching it wider makes it taller no matter what.

---

### Post by Kallun on 2011-01-09
Bam! Got the touchscreen working on Jolicloud thanks to all you guys! Shoutouts for everyone in the video below:

[http://www.youtube.com/watch?v=PEiBRagfSvs](http://www.youtube.com/watch?v=PEiBRagfSvs)

---

### Post by Kirboosy on 2011-01-09
> **Kallun said:**
> Bam! Got the touchscreen working on Jolicloud thanks to all you guys! Shoutouts for everyone in the video below:

[http://www.youtube.com/watch?v=PEiBRagfSvs](http://www.youtube.com/watch?v=PEiBRagfSvs)

DUDE! WICKED SWEET! I smiled so big when I saw my name scroll through the credits. haha

I was thinking about posting my own video on the Duo but there really isn't much to say after seeing the other videos people have posted.

---

### Post by Kallun on 2011-01-09
Haha, well of course! The video wouldn't even exist if it weren't for you :P

---

### Post by Kirboosy on 2011-01-09
I'm totally getting over my head with this Duo. I want to come up with some method of making the mouse disappear when you use the touchscreen. It kinda bugs me when I use the touchscreen and I see the mouse. 

Might just be me but I don't like the mouse when I'm using the tablet features.

---

### Post by Kallun on 2011-01-10
Nah, i'm the same! It's annoying to see a mouse following your every move :/

Perhaps if at some point we manage to get the system to realize when it's screen it flipped, then this might be possible. Would be even more sexy then!

---

### Post by Kirboosy on 2011-01-10
We might not need the accelerometer to work in order to pull it off. The screen and the touchpad are on two different inputs. One is mouse0 and the other is mouse1

Maybe a script that says when I use mouse0 the pointer disappears but when I use mouse1 the pointer appears.

I found this program called "unclutter" Which is a step in the right direction. It hides the mouse after 5 seconds of not being used. It still appears when you touch but at least it will hide while reading something. I might be able to modify the program to work for us :D

Its in Synaptic Package Manager. Just type in the quick search box "unclutter" and install it :D

---

### Post by garwal on 2011-01-10
[SIZE="3"]Just a short FYI, I was able to use [lili ]("http://www.linuxliveusb.com/")to get the current download of Android 1.6 R2 this week end and it installed on the Duo with out a hitch, everything was found except the x axis rotation. Screen touch worked great as well as wireless and audio. And you would be shocked at how fast it is. So I look for that to be released very soon from the guys at [Android x86]("http://www.androidx86.org/") I know this will not be for some of you but I just hate the desk top we have in unbuntu, and from what I have read many feel the same. I am currently working at getting the motion input sensor to work and keep your fingers crossed. I have found quite a bit of information on this in [here]("http://lists.lm-sensors.org/pipermail/lm-sensors/2009-September/subject.html#26787") is a good start. Welcome any help.
garwal[/SIZE]

---

### Post by ninjaaron on 2011-01-10
well, I finally got it. Strangely, the Windows partition wouldn't allow me to re-size. I erased it.

So, I followed setup guide and everything that could be expected to work works. I'm now finding that Windows 7 was much better optimised for touch interface than UNE, so I'm feeling a bit sheepish about deleting it.

I have restore media... but come on... installing Windows? On purpose? my pride has to be taken down a few more notches before that happens... (not to say that's impossible)...

By the way, here are some more nice add-ons for Firefox in a touch environment (I couldn't even open the link in the OP, but I'm pretty sure there are more here):
[https://addons.mozilla.org/en-US/firefox/collections/sudrien/8acb7dc2-42e7-41e7-bd88-1b9bf6/](https://addons.mozilla.org/en-US/firefox/collections/sudrien/8acb7dc2-42e7-41e7-bd88-1b9bf6/)

---

### Post by garwal on 2011-01-10
> **ninjaaron said:**
> well, I finally got it. Strangely, the Windows partition wouldn't allow me to re-size. I erased it.

So, I followed setup guide and everything that could be expected to work works. I'm now finding that Windows 7 was much better optimised for touch interface than UNE, so I'm feeling a bit sheepish about deleting it.

I have restore media... but come on... installing Windows? On purpose? my pride has to be taken down a few more notches before that happens... (not to say that's impossible)...

By the way, here are some more nice add-ons for Firefox in a touch environment (I couldn't even open the link in the OP, but I'm pretty sure there are more here):
[https://addons.mozilla.org/en-US/firefox/collections/sudrien/8acb7dc2-42e7-41e7-bd88-1b9bf6/](https://addons.mozilla.org/en-US/firefox/collections/sudrien/8acb7dc2-42e7-41e7-bd88-1b9bf6/)


Thanks for the link to the goodies, Just wipe that windoz stuff and then you will have more motivation to get every thing working in linux :) 
garwal

---

### Post by Kirboosy on 2011-01-10
We need to figure out a way to make all the buttons bigger. The close buttons are impossible to hit with UNE. I have looked around but I'm unable to find anything about changing the buttons. Guess I will have to root around to find it.

---

### Post by ninjaaron on 2011-01-10
It is quite the conundrum, since the Duo has the resolution of a 14-15" screen, just with teeny, tiny pixels.

---

### Post by garwal on 2011-01-10
Here is the code to ad support for the 3 axis sensor if anyone is interested.  [HERE]("http://www.webservertalk.com/archive242-2010-11-2341558.html")

---

### Post by Kirboosy on 2011-01-10
> **garwal said:**
> Here is the code to ad support for the 3 axis sensor if anyone is interested.  [HERE]("http://www.webservertalk.com/archive242-2010-11-2341558.html")

Care to break it down into a simple to read step by step guide? I know this could be intimidating for people new to Linux. I could do it but I figured since you found it I would let you do it. :)

---

### Post by Non.Cents on 2011-01-10
If you change the screen res to 1360x769 it is still 16:9 and high res but things get just a hair bigger. then if you go into appearance and change font sizes up a bit things get just barely big enough to be manageable. Also i am using orta theme that has an option to have thick scroll bars to help use the bars when drag isn't possible (outside of browsers).

It may not be the end all solution but it should get you by until something better gets found. It is wokin for me.

---

### Post by garwal on 2011-01-10
> **Caboose885 said:**
> Care to break it down into a simple to read step by step guide? I know this could be intimidating for people new to Linux. I could do it but I figured since you found it I would let you do it. :)

I think this will do for most, I have a lot going right now and will try to slim it down as I have time.
garwal

How do I apply a patch?

    * (TAC) (From /usr/src/linux/README) You can upgrade between releases by patching. Patches are distributed in the traditional gzip and the new bzip2 format. To install by patching, get all the newer patch files, enter the top-level directory of the unpacked kernel source tree and execute:
      gzip -cd patchXX.gz | patch -p1 or:
      bzip2 -dc patchXX.bz2 | patch -p1
      (repeat xx for all versions bigger than the version of your current source tree, in order) and you should be ok. You may want to remove the backup files (xxx~ or xxx.orig), and make sure that there are no failed patches (xxx# or xxx.rej). If there are, either you or me has made a mistake.
     [U] Alternatively, the script patch-kernel can be used to automate this process. It determines the current kernel version and applies any patches found. Use it thus:
      scripts/patch-kernel .
      The first argument in the command is the location of the kernel source. Patches are applied from the current directory, but an alternative directory can be specified as the second argument.
    * (RRR) To apply kernel patches please take a look at the kernel README file (/usr/src/linux/README) under "Installing the kernel". There is also a good explanation on the Linux HQ Project site.
[/U]

---

### Post by Kirboosy on 2011-01-10
Is anyone having problems with their blutooth? It says on mine that the adapter is on but when I hit preferences it says Bluetooth is disabled. When I try to enable it it just sits there...

---

### Post by garwal on 2011-01-10
> **Caboose885 said:**
> Is anyone having problems with their blutooth? It says on mine that the adapter is on but when I hit preferences it says Bluetooth is disabled. When I try to enable it it just sits there...

Same here ???

---

### Post by Kirboosy on 2011-01-10
Ok I was just making sure it wasn't just me. I will start looking up a solution.

---

### Post by shartke on 2011-01-10
> **Caboose885 said:**
> Ok I was just making sure it wasn't just me. I will start looking up a solution.

Hey Good Guide!  I had this problem with bluetooth on mine before I got rid of it.. Its a very common problem on dells with linux on them.   I found an article on how to fix it.  If you go into windows first and enable it and reboot it works just fine.  You have to find a way to initiate it before it goes into ubuntu.

---

### Post by Kirboosy on 2011-01-10
Yeah that works, but I want to find a way to fix it that doesn't require windows. I still find it odd that the hardware works properly after rebooting from windows into Ubuntu

---

### Post by w1ll1am on 2011-01-10
> **Caboose885 said:**
> Yeah that works, but I want to find a way to fix it that doesn't require windows. I still find it odd that the hardware works properly after rebooting from windows into Ubuntu

That is what happened to me with the touch screen if i booted into windows and then back into Ubuntu it worked fine once I edited in the line to the grub file to get the screen working it was fine. maybe the fix for the bluetooth will be just as simple.

---

### Post by ninjaaron on 2011-01-11
Lots to tell.

I guess I'm the only one here who doesn't have Windows on the duo at this point, and I'm noticing a couple of interesting differences from what everyone else is describing.

I set the F-keys as primary in the BIOS, and it works just fine.

Bluetooth also works fine (ok, haven't tested it, but it says it's working).

You said you wanted a way to make it work without Windows... well, it doesn't get much more 'Windows-less' than removing the OS.:P

In other news I've sorta abandoned Unity. For the time being, it's just a good idea but not really ready for implementation yet, leastwise not in a tablet environment. For those who don't know, UNE also ships with gnome, and you can switch you session at login to "Ubuntu Desktop Edition." Of course, you can switch any time.

From there, I've installed Compiz and Emerald Theme Manager. The duo has more than enough power for that.

In any event, I modified an existing Emerald window theme that has very large buttons which are fairly easy to touch (for closing, resizing, etc).

I couldn't figure out how to package the theme correctly so it would install like normal but, if you unzip [this file]("http://ubuntuone.com/p/Xkr/"), and drop the folder in ~/.emerald/themes, the theme will appear the next time you open Emerald. It works good.

---

### Post by Kallun on 2011-01-11
> **ninjaaron said:**
> Lots to tell.

I guess I'm the only one here who doesn't have Windows on the duo at this point, and I'm noticing a couple of interesting differences from what everyone else is describing.

I set the F-keys as primary in the BIOS, and it works just fine.

Bluetooth also works fine (ok, haven't tested it, but it says it's working).

You said you wanted a way to make it work without Windows... well, it doesn't get much more 'Windows-less' than removing the OS.:P

In other news I've sorta abandoned Unity. For the time being, it's just a good idea but not really ready for implementation yet, leastwise not in a tablet environment. For those who don't know, UNE also ships with gnome, and you can switch you session at login to "Ubuntu Desktop Edition." Of course, you can switch any time.

From there, I've installed Compiz and Emerald Theme Manager. The duo has more than enough power for that.

In any event, I modified an existing Emerald window theme that has very large buttons which are fairly easy to touch (for closing, resizing, etc).

I couldn't figure out how to package the theme correctly so it would install like normal but, if you unzip [this file]("http://ubuntuone.com/p/Xkr/"), and drop the folder in ~/.emerald/themes, the theme will appear the next time you open Emerald. It works good.


I have a windows-less duo ;D So much nicer.

Thanks for the info though, i'm at work right now, but i'm going to go ahead and try the above. Can't wait to play with wobbly windows :P

---

### Post by ninjaaron on 2011-01-11
so, did anyone explain how to do the screen-keyboard at login yet?
I didn't see anything, and I was a bit confused about it myself, but I've got it sorted now, so here's the story:

At the login screen, there is a bar across the bottom, somewhere on the right side of the bar is an icon that looks kinda like the silhouette of a guy with his arms stretched out.
click it.

When you click it, a menu pops up. I thought it was an info tab for a really long time, because it only had one thing it... but no, you can click that thing.

So click "Universal Accessibility Options," or whatever it says. you will get a dialogue with some boxes for ticking. There's one that says something about 'onscreen keyboard.'

... you get the idea. It the really ugly "onBoard" keyboard, but it gets the job done.

---

### Post by Kirboosy on 2011-01-11
I have found a new glitch. (For those dual booting Windows and Ubuntu)

When I reboot from Windows to Ubuntu my bluetooth works correctly but my touchpad and touchscreen are weird. My touchpad has two finger scrolling enabled and it won't work correctly after I boot Windows to Ubuntu. Also my screen turns into a giant touchpad. If I reboot again into Ubuntu it works properly.

Update: Not that big of a deal because my end goal is to wipe Windows completely. Its just a bit strange

---

### Post by Kallun on 2011-01-11
ninjaaron: if you imstall Florence virtual keyboard (there's a link a couple pages back for it, or if you go to my youtube video on page 8 the deb file is in the description) and then you go to startup programs and select 'Add' and enter 'florence' on the command field, that will launch Florence at login. As far as at startup goes, i.e if you want one for the login screen, i'm not sure i'm afraid.

---

### Post by Kallun on 2011-01-11
are there any dependencies that i need to manually install to get compiz working on the normal ubuntu desktop session? i installed compiz and cokpiz manager, but it doesn't seem to work :( I wanna use wobbly windows!

---

### Post by ninjaaron on 2011-01-11
yeah, Florence, I already have (I'm typing on it now, as a matter of fact), and I had it opening at startup (but via the Preferred Applications dialogue; just have it on a launcher now).

I think there must be a way to get to open at the gdm login screen... I actually got it to open before the login screen, but it totally messed up the startup process...

The thing is that the gdm configuration has changed so much in the past few years that I couldn't figure out which file to edit.

Still, if one follows the directions I gave above, they can at least use the ugly keyboard at the login screen. It is what it is. I would' be totally surprised if you could do something about it with Ubuntu Tweak, but I haven't installed it on this machine, and I'm satisfied with it in any even.

*edit; just saw your second post*

Well, you will probably also want one of the GUI tools for configuring compiz (there's the 'advanced' one and the 'simple' one. I actually use both). Even so, if you go into your Appearance Preferences, you can select more visual effects. If they don't take effect, try running;
```
compiz --replace
```
That ought to do it. You may have to do a reboot at most.

If that doesn't work, then I don't know.

---

### Post by Kallun on 2011-01-11
Ah fair enough, yeah im typing on it too :P 

You mentioned you got compiz working, are there any dependencies i need to install in order for it to work? or anything else? i cant seem to get it working

---

### Post by ninjaaron on 2011-01-11
this is worse than phone-tag. I edited my previous post and told you what I thought would work.

---

### Post by Kallun on 2011-01-11
aha woops, sorry i just replied straight after you posted, ok, cheers for that! ill try it out now :)

---

### Post by w1ll1am on 2011-01-11
> **ninjaaron said:**
> so, did anyone explain how to do the screen-keyboard at login yet?
I didn't see anything, and I was a bit confused about it myself, but I've got it sorted now, so here's the story:

At the login screen, there is a bar across the bottom, somewhere on the right side of the bar is an icon that looks kinda like the silhouette of a guy with his arms stretched out.
click it.

When you click it, a menu pops up. I thought it was an info tab for a really long time, because it only had one thing it... but no, you can click that thing.

So click "Universal Accessibility Options," or whatever it says. you will get a dialogue with some boxes for ticking. There's one that says something about 'onscreen keyboard.'

... you get the idea. It the really ugly "onBoard" keyboard, but it gets the job done.

Add this code to the bottom of /etc/gdm/Init/Default before the exit 0

```
 sudo gedit /etc/gdm/Init/Default 
```

```
 exec florence& 
```

This will make florence run at the login screen

---

### Post by w1ll1am on 2011-01-11
Okay so I was wanting to get rid of the pointer also so I figured an X11 cursor theme would work nice so I made one it works okay but still needs some work which I will keep working on but maybe some of you out there have better program skills than me and can some how make it switch between the normal pointer and this one. 

I attached a compressed folder extract and add this folder to you /usr/share/icons folder and then go to appearance->customize->pointers tab and click on Tablet.

The pointer will go away but I can not get the closed hand to go away when you are moving windows or scrolling in firefox with grab and drag.

---

### Post by Kirboosy on 2011-01-11
> **Kallun said:**
> Ah fair enough, yeah im typing on it too :P 

You mentioned you got compiz working, are there any dependencies i need to install in order for it to work? or anything else? i cant seem to get it working

Did you install the compiz-settings-manger? Its a simple as a click when using that :P

---

### Post by Kallun on 2011-01-11
well... compiz is certainly working, and yep, i have installed compiz settings manager, butttt it seems  that compiz is making all my windows borders red :( very ugly in my opinion, im assuming this is from emerald :/ any idea how to just keep the default ambiance theme but still have the wonderful effects of compiz? 

p.s nice one for getting florence up at login! thanks very much

---

### Post by w1ll1am on 2011-01-11
>  p.s nice one for getting florence up at login! thanks very much

Welcome now someone just has to figure out how to get it to close after login.

---

### Post by ninjaaron on 2011-01-12
> **w1ll1am said:**
> Add this code to the bottom of /etc/gdm/Init/Default before the exit 0

```
 sudo gedit /etc/gdm/Init/Default 
```

```
 exec florence& 
```

This will make florence run at the login screen

Hmmm I did exactly this without the ampersand, and it hijacked my startup process and wouldn't give it back... I had boot from usb to edit the file and make it load correctly.

I have to see this to believe that one little ampersand can change all that...

*edit*

I'm a believer!
What's the ampersand do?

---

### Post by ninjaaron on 2011-01-12
> **Kallun said:**
> well... compiz is certainly working, and yep, i have installed compiz settings manager, butttt it seems  that compiz is making all my windows borders red :( very ugly in my opinion, im assuming this is from emerald :/ any idea how to just keep the default ambiance theme but still have the wonderful effects of compiz?

I'm actually not sure how to switch back to the metacity theme manager, though I'm sure Google can tell you how.

However, you do what I told you with that file I linked, it will open a much better-looking window theme with easy-to-touch buttons. You may still want ambience, I guess, but I don't really know how to switch it. I suppose if you uninstall Emerald and restart gnome, that ought to do the trick. You'll have to figure out your own buttons solution for metacity (though I doubt it would be terribly difficult)

---

### Post by Kallun on 2011-01-12
@ninjaaron - I did try and remove Emerald but that just made the window decorations disappear :| it wasn't fun, and I did check to ensure that decorative windows was enables in compiz settings manager. Un-installed and re-installed compiz but still had the same issue :( been looking around on Google and haven't found much unfortunately, I really do like the default Ambiance theme, so it'd be ideal to stick with that. But I suppose right now, I can keep it simple, nothing fancy, we have bigger fish to fry!

---

### Post by Kirboosy on 2011-01-12
> **ninjaaron said:**
> What's the ampersand do?


ampersand runs the process in the background. if you were to run 

```
florence
``` in a terminal you would have to open a new tab/terminal in order to run another command while Florence is running. Or you have to kill Florence. 

If you run 
```
florence &
``` you can now see that it gives you the ability to keep running new commands but Florence is still running. :)


So when you messed your computer up its because it was only able to execute Florence and nothing else.

So you would have to run a command similar to this to kill off the background process
```
kill florence
```

---

### Post by DFarmerTX on 2011-01-12
Android 1.6?  Forget that, they have a special build specifically for the Duo codenamed "Sparta".  Try it out! Nightly builds: [http://android-x86.moonman.dk/...]("http://android-x86.moonman.dk/index.php?folder=c3BhcnRh")
I have this on a USB stick and it boots and runs just fine.

---

### Post by Kirboosy on 2011-01-12
> **DFarmerTX said:**
> Android 1.6?  Forget that, they have a special build specifically for the Duo codenamed "Sparta".  Try it out! Nightly builds: [http://android-x86.moonman.dk/...]("http://android-x86.moonman.dk/index.php?folder=c3BhcnRh")
I have this on a USB stick and it boots and runs just fine.

Everything runs properly on it?

---

### Post by DFarmerTX on 2011-01-12
> **Caboose885 said:**
> Everything runs properly on it?
Well, as much as they have working for a PC with x86.  There's no official market of course, but I'm sure it could be hacked into the system easily enough.

And no phone.  But for what it is, it's pretty cool.  The touch screen works fine, as does the wireless, so you can surf the net, etc.

It's interesting.  I think Android 3 may be a contender, if it's truly built for tablets.  Until then, I'll check in on the updates for this 2.2 version occasionally.

---

### Post by ninjaaron on 2011-01-12
> **Kallun said:**
> @ninjaaron - I did try and remove Emerald but that just made the window decorations disappear :| it wasn't fun, and I did check to ensure that decorative windows was enables in compiz settings manager. Un-installed and re-installed compiz but still had the same issue :( been looking around on Google and haven't found much unfortunately, I really do like the default Ambiance theme, so it'd be ideal to stick with that. But I suppose right now, I can keep it simple, nothing fancy, we have bigger fish to fry!

Ok, got it.

open synaptic. You can apparently install:

compiz
compiz-gnome
compiz-kde

If you have any if those but compiz-gnome installed, switch it.

Once you are running compiz-gnome, run the command "gtk-window-decorator --replace"

BAM!

I'm not sure if gtk will remain the default after this or not. I think it will, but if you want to make double sure, go to the compiz settings manager>window decorations, and change the 'Command' to what I just gave you above.

---

### Post by ninjaaron on 2011-01-12
> **Caboose885 said:**
> Everything runs properly on it?

Everything except the productivity software... ;)

---

### Post by Kallun on 2011-01-12
Whey! Thanks ninjaaron! It's working perfect now :D

---

### Post by w1ll1am on 2011-01-12
Ninjaaron: I saw your post on the YouTube video for installing an ssd in the duo did you install one?

---

### Post by w1ll1am on 2011-01-12
I just finished installing an SSD on my Duo and I thought I would post some results. The process was not very difficult if you have ever taken apart a laptop before this was probably the easiest I have had. There are also two internal batteries in the front left and front right that are very easy to remove if you ever have to replace them. 

The battery on my Duo at 100% with the 320gb 7200RPM Hitachi HDD at most peaked on the battery indicator at 2:50.

The battery at 100% with a 60gb OCZ agility II SSD peaked on the battery indicator at 3:20.

Boot time with the Hitachi in ubuntu 10.10 netbook edition with automatic login. Timed from the time I hit the power button to the time the desktop appeared was 34.8 seconds.

Boot time with the OCZ SSD was 23.6 seconds! 

If any one is interested I recommend this [Video]("http://www.youtube.com/watch?v=j2VEn5mVGE4") for installing the SSD and this [Thread]("http://ubuntuforums.org/showthread.php?t=1612240") for setting up the SSD in ubuntu. Which guide you follow is up to you there are two links on the page.

The buffered disk reads on the SSD were 255.9 mb/sec at the peak. and I did not do it on the HDD I forgot so if anyone is willing to post what there's is on the Hitachi it would be appreciated.

```
 sudo hdparm -t /dev/sda 
```

---

### Post by Kirboosy on 2011-01-12
> **w1ll1am said:**
> I just finished installing an SSD on my Duo and I thought I would post some results. The process was not very difficult if you have ever taken apart a laptop before this was probably the easiest I have had. There are also two internal batteries in the front left and front right that are very easy to remove if you ever have to replace them. 

The battery on my Duo at 100% with the 320gb 7200RPM Hitachi HDD at most peaked on the battery indicator at 2:50.

The battery at 100% with a 60gb OCZ agility II SSD peaked on the battery indicator at 3:20.

Boot time with the Hitachi in ubuntu 10.10 netbook edition with automatic login. Timed from the time I hit the power button to the time the desktop appeared was 34.8 seconds.

Boot time with the OCZ SSD was 23.6 seconds! 

If any one is interested I recommend this [Video]("http://www.youtube.com/watch?v=j2VEn5mVGE4") for installing the SSD and this [Thread]("http://ubuntuforums.org/showthread.php?t=1612240") for setting up the SSD in ubuntu. Which guide you follow is up to you there are two links on the page.

The buffered disk reads on the SSD were 255.9 mb/sec at the peak. and I did not do it on the HDD I forgot so if anyone is willing to post what there's is on the Hitachi it would be appreciated.

```
 sudo hdparm -t /dev/sda 
```

Nice...and you can always buy an enclosure for the old hard drive and make it a nice external. :D

[B]Duo--82.32 MB/sec for the 7200 RPM Hitachi
Desktop--160 MB/sec for 2 7200 Seagates in RAID 0. [/B]
Moral of the story is I need two SSD in RAID 0. haha

---

### Post by ninjaaron on 2011-01-13
> **w1ll1am said:**
> Ninjaaron: I saw your post on the YouTube video for installing an ssd in the duo did you install one?

No, I haven't. Cool that you have. I would really like to, but I'm not in the financial situation where I can do that. The duo itself was a gift.

On the other hand, if anyone is donating SSD's to poor students, you know where to find me ;)

---

### Post by Kirboosy on 2011-01-13
> **ninjaaron said:**
> No, I haven't. Cool that you have. I would really like to, but I'm not in the financial situation where I can do that. The duo itself was a gift.

On the other hand, if anyone is donating SSD's to poor students, you know where to find me ;)

Same for me! Poor college student here. :D

---

### Post by ninjaaron on 2011-01-15
ok, so I realise that the on-screen keyboard probably isn't the most critical piece of software for the duo, but after messing around a bit, I've come to the conclusion that onboard, the ugliest of them all, is probably also the best. Florence has some weird behaviours that make it very difficult to use in an auto-complete context (ie: typing a web address or using a search engine, which is what I'm usually doing with it). Onboard also gives more immediate access to the F, navigation, and num-pad keys without them always taking up valuable screen space.

What I'm finding out is that onboard is very modifiable through text files and editing SVGs. I'm going to work on getting it to look decent over the next week and see how it goes. Since this is sort of beyond 'Inspiron duo setup,' I'll post a new thread on the moblin board when I get some stuff figured out, and I'll put a link to it over here if anyone shows any interest.

---

### Post by shartke on 2011-01-15
> **ninjaaron said:**
> ok, so I realise that the on-screen keyboard probably isn't the most critical piece of software for the duo, but after messing around a bit, I've come to the conclusion that onboard, the ugliest of them all, is probably also the best. Florence has some weird behaviours that make it very difficult to use in an auto-complete context (ie: typing a web address or using a search engine, which is what I'm usually doing with it). Onboard also gives more immediate access to the F, navigation, and num-pad keys without them always taking up valuable screen space.

What I'm finding out is that onboard is very modifiable through text files and editing SVGs. I'm going to work on getting it to look decent over the next week and see how it goes. Since this is sort of beyond 'Inspiron duo setup,' I'll post a new thread on the moblin board when I get some stuff figured out, and I'll put a link to it over here if anyone shows any interest.

That would be awesome! I gave in and bought the duo again :( I shipped it back but found that there is really nothing else on the market.   So, I will be posting somethings I am finding out.  I found the Kvkbd to be a little finicky but once you get use to it and make sure you always minimize it when done it works well.

---

### Post by shartke on 2011-01-16
Well thought I would give everyone an update.  After playing with UNE 10.10 for 8 hours I decided to ditch it.   Does anyone else think that interface is way too buggy/slow?  I was getting so frusrated so I switched to MeeGo for a while.  I got all the codecs, touchscreen, and everything working.  Even has a killer onscreen keyboard. (Minus the no enter  button? WTH? Who builds a keyboard without an enter button)  I mean this keyboard even pops up when you point to a textbox!  Freaking amazing.   I still miss ubuntu :( I am thinking about slipping back a version and trying that.  I have read reviews stating 10.10 inteface wasn't ready.  What are your thoughts?

---

### Post by garwal on 2011-01-16
> **shartke said:**
> Well thought I would give everyone an update. After playing with UNE 10.10 for 8 hours I decided to ditch it. Does anyone else think that interface is way too buggy/slow? I was getting so frusrated so I switched to MeeGo for a while. I got all the codecs, touchscreen, and everything working. Even has a killer onscreen keyboard. (Minus the no enter button? WTH? Who builds a keyboard without an enter button) I mean this keyboard even pops up when you point to a textbox! Freaking amazing. I still miss ubuntu :( I am thinking about slipping back a version and trying that. I have read reviews stating 10.10 inteface wasn't ready. What are your thoughts?
I agree UNE was and still is not up to use for everyday. Just way to many things that have to be tinkered with, the resolution that is available in all the flavors of linux just is to small for me. I had a great experience with MeeGo as well and believe it is a real contender. Even Android has a better GUI and easier to see jmho. I have finally gone back to Windows , main reason ? The ability to have better control over the screen resolution. I do not like Windows...but it is not half bad using Thinix for a desktop. If you have not really explored what most are having to say about UNE ,do your self a favor and do so. It seems that most begged Unbuntu to not use that desktop. And if they insist upon using it they are going to lose many Unbuntu fans. The Dell Duo is a great little machine and I enjpy having it to use for travel. But it could sure use some refinement in the OS department.

---

### Post by garwal on 2011-01-16
> **shartke said:**
> Well thought I would give everyone an update.  After playing with UNE 10.10 for 8 hours I decided to ditch it.   Does anyone else think that interface is way too buggy/slow?  I was getting so frusrated so I switched to MeeGo for a while.  I got all the codecs, touchscreen, and everything working.  Even has a killer onscreen keyboard. (Minus the no enter  button? WTH? Who builds a keyboard without an enter button)  I mean this keyboard even pops up when you point to a textbox!  Freaking amazing.   I still miss ubuntu :( I am thinking about slipping back a version and trying that.  I have read reviews stating 10.10 inteface wasn't ready.  What are your thoughts?
I agree UNE was and still is not up to use for everyday. Just way to many things that have to be tinkered with, the resolution that is available in all the flavors of linux just is to small for me. I had a great experience with MeeGo as well and believe it is a real contender. Even Android has a better GUI and easier to see jmho. I have finally gone back to Windows , main reason ? The ability to have better control over the screen resolution. I do not like Windows...but it is not half bad using Thinix for a desktop. If you have not really explored what most are having to say about UNE ,do your self a favor and do so. It seems that most begged Unbuntu to not use that desktop. And if they insist upon using it they are going to lose many Unbuntu fans. The Dell Duo is a great little machine and I enjpy having it to use for travel. But it could sure use some refinement in the OS department.

---

### Post by garwal on 2011-01-16
> **shartke said:**
> Well thought I would give everyone an update.  After playing with UNE 10.10 for 8 hours I decided to ditch it.   Does anyone else think that interface is way too buggy/slow?  I was getting so frusrated so I switched to MeeGo for a while.  I got all the codecs, touchscreen, and everything working.  Even has a killer onscreen keyboard. (Minus the no enter  button? WTH? Who builds a keyboard without an enter button)  I mean this keyboard even pops up when you point to a textbox!  Freaking amazing.   I still miss ubuntu :( I am thinking about slipping back a version and trying that.  I have read reviews stating 10.10 inteface wasn't ready.  What are your thoughts?
I agree UNE was and still is not up to use for everyday. Just way to many things that have to be tinkered with, the resolution that is available in all the flavors of linux just is to small for me. I had a great experience with MeeGo as well and believe it is a real contender. Even Android has a better GUI and easier to see jmho. I have finally gone back to Windows , main reason ? The ability to have better control over the screen resolution. I do not like Windows...but it is not half bad using Thinix for a desktop. If you have not really explored what most are having to say about UNE ,do your self a favor and do so. It seems that most begged Unbuntu to not use that desktop. And if they insist upon using it they are going to lose many Unbuntu fans. The Dell Duo is a great little machine and I enjpy having it to use for travel. But it could sure use some refinement in the OS department.

---

### Post by garwal on 2011-01-16
> **shartke said:**
> Well thought I would give everyone an update.  After playing with UNE 10.10 for 8 hours I decided to ditch it.   Does anyone else think that interface is way too buggy/slow?  I was getting so frusrated so I switched to MeeGo for a while.  I got all the codecs, touchscreen, and everything working.  Even has a killer onscreen keyboard. (Minus the no enter  button? WTH? Who builds a keyboard without an enter button)  I mean this keyboard even pops up when you point to a textbox!  Freaking amazing.   I still miss ubuntu :( I am thinking about slipping back a version and trying that.  I have read reviews stating 10.10 inteface wasn't ready.  What are your thoughts?
I agree UNE was and still is not up to use for everyday. Just way to many things that have to be tinkered with, the resolution that is available in all the flavors of linux just is to small for me. I had a great experience with MeeGo as well and believe it is a real contender. Even Android has a better GUI and easier to see jmho. I have finally gone back to Windows , main reason ? The ability to have better control over the screen resolution. I do not like Windows...but it is not half bad using Thinix for a desktop. If you have not really explored what most are having to say about UNE ,do your self a favor and do so. It seems that most begged Unbuntu to not use that desktop. And if they insist upon using it they are going to lose many Unbuntu fans. The Dell Duo is a great little machine and I enjpy having it to use for travel. But it could sure use some refinement in the OS department.

---

### Post by garwal on 2011-01-16
> **shartke said:**
> Well thought I would give everyone an update.  After playing with UNE 10.10 for 8 hours I decided to ditch it.   Does anyone else think that interface is way too buggy/slow?  I was getting so frusrated so I switched to MeeGo for a while.  I got all the codecs, touchscreen, and everything working.  Even has a killer onscreen keyboard. (Minus the no enter  button? WTH? Who builds a keyboard without an enter button)  I mean this keyboard even pops up when you point to a textbox!  Freaking amazing.   I still miss ubuntu :( I am thinking about slipping back a version and trying that.  I have read reviews stating 10.10 inteface wasn't ready.  What are your thoughts?
I agree UNE was and still is not up to use for everyday. Just way to many things that have to be tinkered with, the resolution that is available in all the flavors of linux just is to small for me. I had a great experience with MeeGo as well and believe it is a real contender. Even Android has a better GUI and easier to see jmho. I have finally gone back to Windows , main reason ? The ability to have better control over the screen resolution. I do not like Windows...but it is not half bad using Thinix for a desktop. If you have not really explored what most are having to say about UNE ,do your self a favor and do so. It seems that most begged Unbuntu to not use that desktop. And if they insist upon using it they are going to lose many Unbuntu fans. The Dell Duo is a great little machine and I enjpy having it to use for travel. But it could sure use some refinement in the OS department.

---

### Post by garwal on 2011-01-16
> **shartke said:**
> Well thought I would give everyone an update.  After playing with UNE 10.10 for 8 hours I decided to ditch it.   Does anyone else think that interface is way too buggy/slow?  I was getting so frusrated so I switched to MeeGo for a while.  I got all the codecs, touchscreen, and everything working.  Even has a killer onscreen keyboard. (Minus the no enter  button? WTH? Who builds a keyboard without an enter button)  I mean this keyboard even pops up when you point to a textbox!  Freaking amazing.   I still miss ubuntu :( I am thinking about slipping back a version and trying that.  I have read reviews stating 10.10 inteface wasn't ready.  What are your thoughts?
I agree UNE was and still is not up to use for everyday. Just way to many things that have to be tinkered with, the resolution that is available in all the flavors of linux just is to small for me. I had a great experience with MeeGo as well and believe it is a real contender. Even Android has a better GUI and easier to see jmho. I have finally gone back to Windows , main reason ? The ability to have better control over the screen resolution. I do not like Windows...but it is not half bad using Thinix for a desktop. If you have not really explored what most are having to say about UNE ,do your self a favor and do so. It seems that most begged Unbuntu to not use that desktop. And if they insist upon using it they are going to lose many Unbuntu fans. The Dell Duo is a great little machine and I enjpy having it to use for travel. But it could sure use some refinement in the OS department.

---

### Post by garwal on 2011-01-16
sorry for the multiple posts using ie 9 and it is also not ready for prime time. I can not find where to delete them???? Sorry about this Mods

---

### Post by Kallun on 2011-01-17
> **garwal said:**
> sorry for the multiple posts using ie 9 and it is also not ready for prime time. I can not find where to delete them???? Sorry about this Mods

So switching to Windows is going well for ya then garwal? ;D Haha

---

### Post by overdrank on 2011-01-17
> **garwal said:**
> sorry for the multiple posts using ie 9 and it is also not ready for prime time. I can not find where to delete them???? Sorry about this Mods
No apologies necessary. Forum error happens to everyone. :) 
> **Kallun said:**
> So switching to Windows is going well for ya then garwal? ;D Haha

No need for O/S bashing :)

---

### Post by ninjaaron on 2011-01-17
> **shartke said:**
> Well thought I would give everyone an update.  After playing with UNE 10.10 for 8 hours I decided to ditch it.   Does anyone else think that interface is way too buggy/slow?  I was getting so frusrated so I switched to MeeGo for a while.  I got all the codecs, touchscreen, and everything working.  Even has a killer onscreen keyboard. (Minus the no enter  button? WTH? Who builds a keyboard without an enter button)  I mean this keyboard even pops up when you point to a textbox!  Freaking amazing.   I still miss ubuntu :( I am thinking about slipping back a version and trying that.  I have read reviews stating 10.10 inteface wasn't ready.  What are your thoughts?

I agree, I think. I love Unity, but it's just not quite ready yet. I'm still using UNE though, just switched my session to gnome... and I installed compiz... but now it's great!

I have a docky dock on the left side for an application list and launcher with 60px icons, intelle-hiding (when the active window overlaps, it hides. I'm also using an oversized, auto-hidden gnome panel for my sys-tray, applications menu, and a few other launchers. I have the system and fire-fox font sizes majorly enlarged for my viewing pleasure. Got an emerald window decoration theme with oversized buttons... got my corners setup for workspace expo and window switcher...

It takes some time, but gnome can actually be set up as a pretty good touch environment. The only thing that could be better now is that the scroll-bars are a little tough to grab, but you get used to it, after a bit.

Even though screen rotation doesn't work, Document Viewer, E-Book Reader, and Picture Viewer can all rotate their content, which are the main apps I want in portrait mode anyway.

UNE isn't quite right yet, but Ubuntu can be tweaked to a good touch interface, no problem.

---

### Post by Kirboosy on 2011-01-17
> **ninjaaron said:**
> I agree, I think. I love Unity, but it's just not quite ready yet. I'm still using UNE though, just switched my session to gnome... and I installed compiz... but now it's great!

I have a docky dock on the left side for an application list and launcher with 60px icons, intelle-hiding (when the active window overlaps, it hides. I'm also using an oversized, auto-hidden gnome panel for my sys-tray, applications menu, and a few other launchers. I have the system and fire-fox font sizes majorly enlarged for my viewing pleasure. Got an emerald window decoration theme with oversized buttons... got my corners setup for workspace expo and window switcher...

It takes some time, but gnome can actually be set up as a pretty good touch environment. The only thing that could be better now is that the scroll-bars are a little tough to grab, but you get used to it, after a bit.

Even though screen rotation doesn't work, Document Viewer, E-Book Reader, and Picture Viewer can all rotate their content, which are the main apps I want in portrait mode anyway.

UNE isn't quite right yet, but Ubuntu can be tweaked to a good touch interface, no problem.

I agree. I think that 11.04 UNE will be much better. Now if only April 28 would hurry up and get here!


YAY I'm back from the dead. ;) Work has taken me away for a bit...

---

### Post by Kirboosy on 2011-01-17
> **overdrank said:**
> No apologies necessary. Forum error happens to everyone. :) 


No need for O/S bashing :)

I don't understand why Ubuntu forums doesn't have a delete button and it doesn't have the Ubuntu font! Of all places not to have the Ubuntu font. :)

I use that font on a regular basis and people always comment how much they like it.

---

### Post by Non.Cents on 2011-01-17
I think unity is fine for what it is. The duo has 2 things that arnt exactly common among netbooks and that is 1 a touch screen, and 2 a dual core processor. UNE is designed for something just a tad different than the device we have. 
The unfortunate truth is that when your on the cutting edge of technology you cant always have the expect software to be right there.

That said, not using unity on the Duo is probably for the best. It CAN be fixed to work better with a touch interface, but i wouldn't count on that being too too high on their list of things to improve. With compiz you can do..... well just about anything you want so it becomes the obvious option.

---

### Post by overdrank on 2011-01-17
> **Caboose885 said:**
> I don't understand why Ubuntu forums doesn't have a delete button and it doesn't have the Ubuntu font! Of all places not to have the Ubuntu font. :)

I use that font on a regular basis and people always comment how much they like it.

If a post needs to be removed you can use the report button.
The staff are working on a software upgrade for the forums. :)
Back to the topic at hand.

---

### Post by garwal on 2011-01-18
> **Kallun said:**
> So switching to Windows is going well for ya then garwal? ;D Haha

It is doing great for being Windows, I think a few of you are taking my comments the wrong way. I would be the last person to dis Linux, Just a bit of info for those that think I was slamming Linux. I am a 62 year old Computer Scientist with a PhD and I am sure I have been doing computers and using Linux since you were in diapers. I have been involved in the development of several flavors of Linux in fact I was one of the first to test the gnome desk top and it was not in unbuntu, would you guess Red Hat. 
My point was that if this version was intended to be tablet friendly I think they missed the mark. Tablets by nature are a smaller screen, there for they have to have a GUI that is favorable to the limited real estate it has to play in. I always use some type Linux on one or two of my boxes, currently on a Dell Inspron 2200 with UNE, works well and also using Unbuntu 10.10 on one of my test machines. Please don't take any of my comments personally :) I am just an old dog and I know what I am looking for in a OS for the Duo.
I use the forums to share and learn and not a place to vent or flame .

---

### Post by garwal on 2011-01-18
> **overdrank said:**
> If a post needs to be removed you can use the report button.
The staff are working on a software upgrade for the forums. :)
Back to the topic at hand.
Thank you Sir, I did report the issue. Again thanks for the help.
;)

---

### Post by ninjaaron on 2011-01-18
> **Non.Cents said:**
> I think unity is fine for what it is. The duo has 2 things that arnt exactly common among netbooks and that is 1 a touch screen, and 2 a dual core processor. UNE is designed for something just a tad different than the device we have. 

Not to mention the super hi-res display that makes all the buttons that much tinier. My duo has the same screen resolution as the 15.6" screen on my other laptop. The interface doesn't seem tiny at all on that computer, but that's cause the pixels are more than 1.5x the size.

---

### Post by Kallun on 2011-01-18
> **garwal said:**
> It is doing great for being Windows, I think a few of you are taking my comments the wrong way. I would be the last person to dis Linux, Just a bit of info for those that think I was slamming Linux. I am a 62 year old Computer Scientist with a PhD and I am sure I have been doing computers and using Linux since you were in diapers. I have been involved in the development of several flavors of Linux in fact I was one of the first to test the gnome desk top and it was not in unbuntu, would you guess Red Hat. 
My point was that if this version was intended to be tablet friendly I think they missed the mark. Tablets by nature are a smaller screen, there for they have to have a GUI that is favorable to the limited real estate it has to play in. I always use some type Linux on one or two of my boxes, currently on a Dell Inspron 2200 with UNE, works well and also using Unbuntu 10.10 on one of my test machines. Please don't take any of my comments personally :) I am just an old dog and I know what I am looking for in a OS for the Duo.
I use the forums to share and learn and not a place to vent or flame .


Was only having a little joke ;D Although windows 7 isn't 'built for touch' it's touch support/capability is actually really impressive. I was certainly not taking it seriously, just humouring myself. You can get a pretty nice tablet environment going on with Windows mixed with Rainmeter. There's a lot of themes for it that will make it a very touch friendly desktop, not to mention the wealth of customization options. 

Anyway, to keep on track of the subject at hand, I might try out Meego just for kicks :) See how that goes. Also tried the 'sparta' build of Android for the duo the other day, coming along nicely! :D

---

### Post by Kirboosy on 2011-01-18
> **Kallun said:**
> Also tried the 'sparta' build of Android for the duo the other day, coming along nicely! :D

I also tried the 'Sparta' build of Android! I like it but I wonder how they are going to overcome the lack of a home button on the Duo. I guess they could make a gesture to return home. I wish I could get the app store to run correctly. I wanted to play "Angry Birds" on my Duo :D

I read on my tech feeds that Canonical is working on a tablet edition of Ubuntu. I hope that releases soon (while the Duo is still recent hardware, haha)

I'm going to check out MeeGo soon as well. 

The only problem with Ubuntu right now is the support for my hardware. I'm going to play the fields and see what other projects have done. I have till April until Ubuntu 11.04 launches. (Is it to early to start counting the days down?:) )

---

### Post by Kirboosy on 2011-01-18
Double posted! Sorry (Overdrank if you would do the honors please? :) )

---

### Post by Kallun on 2011-01-18
> **Caboose885 said:**
> I also tried the 'Sparta' build of Android! I like it but I wonder how they are going to overcome the lack of a home button on the Duo. I guess they could make a gesture to return home. I wish I could get the app store to run correctly. I wanted to play "Angry Birds" on my Duo :D

I read on my tech feeds that Canonical is working on a tablet edition of Ubuntu. I hope that releases soon (while the Duo is still recent hardware, haha)

I'm going to check out MeeGo soon as well. 

The only problem with Ubuntu right now is the support for my hardware. I'm going to play the fields and see what other projects have done. I have till April until Ubuntu 11.04 launches. (Is it to early to start counting the days down?:) )

Yup! I know what you mean, Honeycomb, supposedly, has a soft home button, like some sort of task/menu bar, so lets hope that woks nicely if it gets running on the Duo. Ah mannn, in regard to the Ubuntu tablet build... that sounds so sexy. I'm gunna try out Meego tonight, i've been a bit pre-occupied with getting Ubuntu to run on my iMac, i'm now a full Linux convert :D (minus the OS X boot partition still sat on here just in case) 

And on another note, i thought it'd be interesting to try out the 'DESMume' Nintendo DS Emulator on the duo... how awesome would that be! Could actually use the touchscreen :P I'm also trying that tonight, so if anyone's interested i'll put a little note on my next post n let them know how it went :)

---

### Post by Kallun on 2011-01-18
Oh and also, Caboose, this might interest you ;D

[http://www.omgubuntu.co.uk/2011/01/play-angry-birds-under-wine-on-linux/](http://www.omgubuntu.co.uk/2011/01/play-angry-birds-under-wine-on-linux/)

---

### Post by Kirboosy on 2011-01-18
> **Kallun said:**
> iMac, i'm now a full Linux convert :D 

So are you going to mod the Apple logo on the back and change it to a Tux penguin? ;)

> **Kallun]Oh and also, Caboose, this might interest you  said:**
> http://www.omgubuntu.co.uk/2011/01/p...wine-on-linux/[/URL]
Sweet find on the Angry birds. I looked around Christmas time but it wasn't out for Windows. 

I'm currently downloading Meego. After looking through the screenshots it seems like a simple interface yet a good one. The only thing is will it support our Touchscreen? I don't believe Meego is really built for touchscreen devices but we shall see. About another hour until my download is complete.

---

### Post by shartke on 2011-01-18
I finally found an onscreen keyboard I liked.  Ended up using florence.  I love the options that you have.  It will even pull up when you click on certain fields.  You can configure the transparency etc.  I am going to put together a video on how to get it to work very well on the duo.  I will keep you all posted.  Oh, and I have a MAC as well and I was torn between ubuntu and osx.  I really love both operating systems.   The reason I still have windows on my machines is because I program for work and personal in C# and haven't found an IDE that is as good as Visual Studio :D

---

### Post by Kallun on 2011-01-18
Aha, the apple on the back doesn't matter too much, but i'd certainly love to cover the front apple with Tux ;D

Awesome, i'm about to go download meego now :) i'm sure someone said a couple posts back they got meego working with the touchscreen? Might just be me remembering what i want to though :P

Yeah, having spent about 3 years with OS X, although i love the system, i've ended up feeling somewhat restricted. I think of it as a 'lazyboy OS' almost, not in a sense that its not an advanced complex system and doesn't do much... but it just works, you don't really have to do anything, which for me, is the cutting point, if i have something... i've got to tincker and play with it :P OS X certainly has some customization options, be it native or 3rd party, but, after playing with ubuntu enough to actually use it as my primary OS, i've almost subconsciously made the switch :) Are you using rEFIt on your mac shartke?

Anyway, sorry to stray off topic :P If i get Meego working witht he Duo tonight, i'll most probably make a video like my last :)

---

### Post by Kallun on 2011-01-18
Oh, it was shartke himself who got Meego going!

I suppose you're the go to guy for any issues we run into (to an extent of course) ;D

---

### Post by shartke on 2011-01-18
> **Kallun said:**
> Oh, it was shartke himself who got Meego going!

I suppose you're the go to guy for any issues we run into (to an extent of course) ;D

I actually do have refit on my machine.  Pretty nifty little loader. 
Here is the instructions on how to get it to work in meego.  (No Grub :D)
[http://www.thejoojooforum.com/viewtopic.php?f=9&t=689&start=20](http://www.thejoojooforum.com/viewtopic.php?f=9&t=689&start=20)

---

### Post by Kirboosy on 2011-01-19
Hmm I really like Meego...its slick. I'm still gonna play with it a bit before I install it. (I could always triple boot)

I was just thinking. How sick would it be to use the accelerometer on a game like "Neverball"?!? I think it would be awesome!!!

---

### Post by shartke on 2011-01-19
> **Caboose885 said:**
> Hmm I really like Meego...its slick. I'm still gonna play with it a bit before I install it. (I could always triple boot)

I was just thinking. How sick would it be to use the accelerometer on a game like "Neverball"?!? I think it would be awesome!!!

PSSH! Totally sick!  The only problem with Meego is the battery life is HORRIBLE! I dropped 12 percent in like 10 minutes.

---

### Post by Kirboosy on 2011-01-19
> **shartke said:**
> PSSH! Totally sick!  The only problem with Meego is the battery life is HORRIBLE! I dropped 12 percent in like 10 minutes.

I think the reason why it drops so quickly is because meego hammers the wifi (causing it to broadcast more power). I bet if you could disable the social aspect of meego you would get better battery life.

Oh and you can easily install neverball on Ubuntu. Its in the repositories. I will let you know when I figure out a way to get the game to work.

---

### Post by Kallun on 2011-01-19
Hey guys! See the two links below, 2D Unity ;) Just installed it now... this is poifect! It runs great :grin:

[http://bfiller.wordpress.com/2011/01/13/unity-2d/](http://bfiller.wordpress.com/2011/01/13/unity-2d/)

[https://launchpad.net/~unity-2d-team/+archive/unity-2d-daily]("https://launchpad.net/%7Eunity-2d-team/+archive/unity-2d-daily")

---

### Post by Kallun on 2011-01-19
Hey guys! See the two links below, 2D Unity :wink: Just installed it now... this is poifect! It runs great :D

[http://bfiller.wordpress.com/2011/01/13/unity-2d/](http://bfiller.wordpress.com/2011/01/13/unity-2d/)

[https://launchpad.net/~unity-2d-team/+archive/unity-2d-daily](https://launchpad.net/~unity-2d-team/+archive/unity-2d-daily)

---

### Post by Kallun on 2011-01-19
Even drag to scroll works in the launcher!

---

### Post by garwal on 2011-01-19
What is 2D Unity?
Please give details when you are giving information. 
Thanks

---

### Post by shartke on 2011-01-19
> **garwal said:**
> What is 2D Unity?
Please give details when you are giving information. 
Thanks

It is described in detail in the main link.. In case you worry about clicking on links without a description..


"Just a little background on the project.  Unity 2D’s main goal is to provide a Unity environment on hardware platforms that don’t  support Unity’s Open GL requirements. Many ARM platforms fall into this category, so Unity 2D expands Unity’s goodness to a whole new set of platforms."  


From the article

That is very exciting I might give it a try.. Thank you! Nice find.  (BTW the forums have been acting up for me too.. I blamed it on the internet connection  because I am in a hotel)

---

### Post by garwal on 2011-01-19
> **shartke said:**
> It is described in detail in the main link.. In case you worry about clicking on links without a description..


"Just a little background on the project.  Unity 2D’s main goal is to provide a Unity environment on hardware platforms that don’t  support Unity’s Open GL requirements. Many ARM platforms fall into this category, so Unity 2D expands Unity’s goodness to a whole new set of platforms."  


From the article

That is very exciting I might give it a try.. Thank you! Nice find.  (BTW the forums have been acting up for me too.. I blamed it on the internet connection  because I am in a hotel)

Thank you for the information. If the resolution is not improved I do not think Unity is for me. I think I have made my way through all alternative OS and of that bunch I think MeeGo had the most possibilities. It is great that more are taking time to play with something different. One question, has anyone gotten the 3 axis to work in MeeGo? Good luck all I am going to let some of you take the lead on this, I am with you and having a ball just following your progress. Yes and the forums dealt me a fit as well. Just a quick note, in my digging I saw a post where someone ask what is the best flavor of Linux for a net book. I was shocked to hear SUSE, so I ordered a  dvd and will play with it as it arrives. Many years ago I used nothing but SUSE and really enjoyed it but always felt it was just a bit blan. We shall see. 
So what is the general feeling here as to what is the best OS for the Duo at this time. Just checking :p
garwal

---

### Post by Kirboosy on 2011-01-19
I HAZ WONDERFUL NEWS!

THE NEW KERNEL HAS BEEN RELEASED! (you need to unedit your grub in order to allow it to work properly)

Bad news is the screen now does some funky things and it broke my two finger scrolling....

---

### Post by ninjaaron on 2011-01-20
before I go ahead and install it, could you possibly elaborate a little bit on "funky things"?

*edit:*
hmmm... the kernel hasn't appeared in my software list or my update manager yet... maybe it's not uploaded to the servers for Israel yet.

I'll wait and see... but not too long...

---

### Post by Kirboosy on 2011-01-20
> **ninjaaron said:**
> before I go ahead and install it, could you possibly elaborate a little bit on "funky things"?

*edit:*
hmmm... the kernel hasn't appeared in my software list or my update manager yet... maybe it's not uploaded to the servers for Israel yet.

I'll wait and see... but not too long...

It might not be an entire new kernel. It might just be modified...I don't know.I just ran ```
sudo apt-get update && sudo apt-get upgrade
```Remember how before we complained about how the mouse wouldn't click? Well that bug is back now. I think I'm going to try and fresh install Ubuntu and see if that might cure the problems.

---

### Post by Non.Cents on 2011-01-20
I just did the fresh install, and am sorry to say..... i dont see any difference. I still had to do all the things in the beginning to get it to do its stuff. Might be new headers, but it does not seem to be a new kernel.....

```
uname -a
Linux Duo 2.6.35-25-generic #43-Ubuntu SMP Thu Jan 6 22:25:16 UTC 2011 i686 GNU/Linux

```

Oh well. it still works.

---

### Post by garwal on 2011-01-20
> **Non.Cents said:**
> I just did the fresh install, and am sorry to say..... i dont see any difference. I still had to do all the things in the beginning to get it to do its stuff. Might be new headers, but it does not seem to be a new kernel.....

```
uname -a
Linux Duo 2.6.35-25-generic #43-Ubuntu SMP Thu Jan 6 22:25:16 UTC 2011 i686 GNU/Linux

```

Oh well. it still works.

Thanks for the update. What does anyone know about JOOJOOGO I finally got a copy and will give it a spin today. Hoping
garwal

---

### Post by garwal on 2011-01-20
> **Non.Cents said:**
> I just did the fresh install, and am sorry to say..... i dont see any difference. I still had to do all the things in the beginning to get it to do its stuff. Might be new headers, but it does not seem to be a new kernel.....

```
uname -a
Linux Duo 2.6.35-25-generic #43-Ubuntu SMP Thu Jan 6 22:25:16 UTC 2011 i686 GNU/Linux

```

Oh well. it still works.

Thanks for the update. What do we know about JOOJOOGO ? I finally got a copy and will give it a shot today.
FYI, got a call from Dell last night and the Stage software is now in the my downloads for the duo. Remember you will have to also download the media stage and the book  as well as paint if you want it back the way it was from the factory. You will have to use there download software and that will require you set up an account, but the software is now available if anyone wants it.
And this forum is still not right!!!!!

Here we go again. 
Where is the delete button for these posts. And it is a SAD THING WHEN WE CAN NOT EVEN GET A FORUM TO RUN PROPERLY. COME ON GUYS EITHER FIX IT OR SHUT IT DOWN UNTIL IT IS FIXED. please

---

### Post by ninjaaron on 2011-01-20
> **Caboose885 said:**
> It might not be an entire new kernel. It might just be modified...I don't know.I just ran ```
sudo apt-get update && sudo apt-get upgrade
```Remember how before we complained about how the mouse wouldn't click? Well that bug is back now. I think I'm going to try and fresh install Ubuntu and see if that might cure the problems.

I still don't seem to have the 'new kernel' (or whatever it is) available here. I tried doing it from update manager, synaptic, and the command line. It's just not there for me. I blame it (as I do most things these days) on the state of Israel.

---

### Post by Kirboosy on 2011-01-20
Garwal I've talked with a few admins and they are actually requesting that you **do not** report your double posts. As I was told "We have more important issues to work on such as Spam and trolling". They are working on getting new servers but they have no idea how long it will be till they get the new servers.


When I get home tonight I will reinstall Ubuntu. I'm having a terrible time with my mouse not clicking anymore. I looked through my PPA and I don't have anything special enabled. I'm not really sure why I got a kernel update while everyone else has not...I have removed that grub edit and my screen still responds correctly and even acts like its seeing the multi touch. 

I think on this next install I will install 2D Unity just to kick the tires on it. ;)

---

### Post by ninjaaron on 2011-01-21
Hey there, I did some very slight tweaking to the 'Ambience' metacity theme. I changed the buttons a bit. They look the same, but they have more space between them, and the actual area that is active as a button is much larger, which makes them much easier to touch. This doesn't have an effect on the master menu in unity, but it works in gnome, as well as unmaximised windows in Unity.

If you test it with your mouse, you will see that the button actually begins to highlight far below and to the right of the actual picture, which allows for a bit sloppier touching.

Unzip [this file]("http://ubuntuone.com/p/ZMg/") and copy the folder to "~/.themes" or "/usr/share/themes" (the second option requires root privileges).

I'm going to work on doing something similar for the Orta metacity themes, since I prefer that, and possibly equinox. I'll edit this post when I get something done.

*edit:*
This actually goes pretty quick once you know what to do... (just edit the button width and height in three places in the xml file, and edit the trough images to fit the new proportions).

[orta-big]("http://ubuntuone.com/p/ZMk/")
This is just a metacity theme, so you have to go to Customize>Window decoration to select it.

---

### Post by Kirboosy on 2011-01-21
Problematic situation here...My 16Gb Patriot Thumb Drive just died :( So I can't reinstall Ubuntu until the factory sends me a new one. (good thing it was under warranty)

I went ahead and install Unity 2D and I really like it. My Duo seems faster BUT does anyone else have a problem with Firefox crashing in Unity 2D? Firefox is highly unstable for me in Unity 2D so I think I might have so switch back to normal Unity for now...

---

### Post by Kirboosy on 2011-01-21
I just had an amazing find. UNE or UNR has Gnome Desktop installed by default...I don't know if anyone has posted about this or not but I wasn't aware of it until a few minutes ago. So anyone who doesn't like Unity doesn't have to reinstall their Ubuntu, they just need to select the default session as regular gnome. :D

---

### Post by shartke on 2011-01-21
> **Caboose885 said:**
> Problematic situation here...My 16Gb Patriot Thumb Drive just died :( So I can't reinstall Ubuntu until the factory sends me a new one. (good thing it was under warranty)

I went ahead and install Unity 2D and I really like it. My Duo seems faster BUT does anyone else have a problem with Firefox crashing in Unity 2D? Firefox is highly unstable for me in Unity 2D so I think I might have so switch back to normal Unity for now...

My firefox isn't crashing in 2D.   I have been using it all day without issues.   I Heart 2D.  We will see how the tablet experience works next.

@Garwal I have seen videos of joojoogo but haven't used the os Isn't that os proprietary to the hardware? Its funny how Linux people aren't happy with the norm.  They have to always play around.  I was reading the joojoogo forum and everyone wants to put ubuntu or some other os on the device.  Hehe.   If you run it let me know how it runs..

Also, Caboose..   I was reading about the i8042.noloop=1 option that we put in grub.  Apparently, that option isn't needed except for vm's.  I will try to find the forum.   I think in the meantime we might want to take that off

---

### Post by SilentKnowledge on 2011-01-21
From what I've seen since migrating to Ubuntu from Fedora/Windows, they all release with gnome as the default desktop environment. I could be mistaken considering my migration is recent but even in the fedora flavors from at least 10 up gnome is the default.

---

### Post by shartke on 2011-01-21
> **SilentKnowledge said:**
> From what I've seen since migrating to Ubuntu from Fedora/Windows, they all release with gnome as the default desktop environment. I could be mistaken considering my migration is recent but even in the fedora flavors from at least 10 up gnome is the default.

Very true, I think Caboose had an AHA moment.  I think he believed because he was downloading "Netbook Remix" it would only come with Unity since that is the default. (Which makes sense)

---

### Post by Kirboosy on 2011-01-21
> **shartke said:**
> Also, Caboose..   I was reading about the i8042.noloop=1 option that we put in grub.  Apparently, that option isn't needed except for vm's.  I will try to find the forum.   I think in the meantime we might want to take that off


Well take it off your grub and let me know how it goes. I will be more than happy to take it off if its not needed. :)

I rebooted my computer and now it seems like Firefox is stable as a rock....I'm not sure why it was crashing so hard earlier.

I knew unity was Gnome based but I didn't think they included straight Gnome. I'm glad  they did though. haha

---

### Post by shartke on 2011-01-21
> **Caboose885 said:**
> Well take it off your grub and let me know how it goes. I will be more than happy to take it off if its not needed. :)

I rebooted my computer and now it seems like Firefox is stable as a rock....I'm not sure why it was crashing so hard earlier.

Caboose,
I removed it this morning and not a single issue you all day.  I think it is safe.

---

### Post by Kirboosy on 2011-01-22
> **shartke said:**
> Caboose,
I removed it this morning and not a single issue you all day.  I think it is safe.

Ok I changed it. I will make sure to make the change on mine soon as well.

---

### Post by Kirboosy on 2011-01-22
> **garwal said:**
>  What do we know about JOOJOOGO ? I finally got a copy and will give it a shot today.

So I think I have figured a few things out. JooJooGo is just Meego but the OP changed the name. So if we wanted we could simply call ours DuoGo. I'm assuming you could follow that tutorial that shartke linked to and everything would work properly. (Correct me if I'm wrong Shartke)

[QUOTE=shartke][http://www.thejoojooforum.com/viewto...t=689&start=20]("http://www.thejoojooforum.com/viewtopic.php?f=9&t=689&start=20")[/QUOTE]

If I had a thumbdrive I would gladly make a tutorial on how to do it but I don't have another thumbdrive. So I have no way to load the OS...

---

### Post by ninjaaron on 2011-01-22
> **Caboose885 said:**
> I just had an amazing find. UNE or UNR has Gnome Desktop installed by default...I don't know if anyone has posted about this or not but I wasn't aware of it until a few minutes ago. So anyone who doesn't like Unity doesn't have to reinstall their Ubuntu, they just need to select the default session as regular gnome. :D

I think I've mentioned this in at least two posts in this thread so far. It doesn't come with compiz, on the other hand. If you choose to install that, make sure you get the package gnome-compiz and not one of the others.

---

### Post by Kirboosy on 2011-01-22
> **ninjaaron said:**
> I think I've mentioned this in at least two posts in this thread so far. It doesn't come with compiz, on the other hand. If you choose to install that, make sure you get the package gnome-compiz and not one of the others.

Sorry I must of been skimming the post or not really comprehending what you were saying. 

Compiz runs amazingly well on the Duo. I want to get the rain effect to activate with some sort of gesture. That way I can drag my finger through water trails :D

---

### Post by shartke on 2011-01-22
> **Caboose885 said:**
> So I think I have figured a few things out. JooJooGo is just Meego but the OP changed the name. So if we wanted we could simply call ours DuoGo. I'm assuming you could follow that tutorial that shartke linked to and everything would work properly. (Correct me if I'm wrong Shartke)



If I had a thumbdrive I would gladly make a tutorial on how to do it but I don't have another thumbdrive. So I have no way to load the OS...

Instructions on how to get the touchscreen to work without Grub in meego.  (Meego uses a different loader)  I went through the process and it worked well.  The only difference is
vi /boot/grub/extlinux/extlinux.cfg doesnt exists.   I think you take the Directory "grub" out and it works.. 

Also the non-free codecs have to be all manually compiled/downloaded and they have really good instructions on their site.  The keyboard is also listed on the forums. (I would recommend florence over the keyboard in their repositories)   Also, meego is RPM based and uses zypper (Not yum to install )

---

### Post by ninjaaron on 2011-01-23
> **Caboose885 said:**
> Sorry I must of been skimming the post or not really comprehending what you were saying. 


Well, I can get a little long-winded. ;)

---

### Post by w1ll1am on 2011-01-23
Does anyone have there windows theme (like firefox) change to a KDE looking theme randomly?

The picture I attached shows the KDE logout symbol and the KDE wifi bars and sometimes other things look like KDE like firefox.

---

### Post by Kirboosy on 2011-01-24
> **w1ll1am said:**
> Does anyone have there windows theme (like firefox) change to a KDE looking theme randomly?

The picture I attached shows the KDE logout symbol and the KDE wifi bars and sometimes other things look like KDE like firefox.

I think that is just a 10.10 glitch in general. That happens on my other computer sometimes. A quick fix I found is to open up Appearance and click edit on your theme then just close the window. It always puts mine back to normal.

I think its the old Colors theme that it is reverting too (like pre 9.04)

---

### Post by Kirboosy on 2011-01-24
I found this [sweet guide]("http://ubuntuforums.org/showthread.php?t=1594694&"). I think I'm gonna try it on my Duo to see how it runs. I know some people were looking at a SSD drive for their computers but this might eliminate the urge to buy one.

Basically you run everything in Ubuntu off of your RAM (which is way faster than our Hard Drive and probably even some SSD drives) I will say that the boot time might slow down a bit but the overall performance of Ubuntu will improve.

I see that people are able to run their system off of a 1Gb of RAM. Well our Duos have at least 2 (some of you may of upgraded) so I figured we will be able to pull it off pretty easily.

I will let you know how things go and how difficult it was to do.

---

### Post by w1ll1am on 2011-01-24
> **Caboose885 said:**
> I think that is just a 10.10 glitch in general. That happens on my other computer sometimes. A quick fix I found is to open up Appearance and click edit on your theme then just close the window. It always puts mine back to normal.

I think its the old Colors theme that it is reverting too (like pre 9.04)

Okay cool it was just driving me crazy and I was not sure if it was something I did or what. Thanks

---

### Post by w1ll1am on 2011-01-24
Anyone heard anything about the dock speakers or been able to get theirs to work in ubuntu?

Well it is just like every thing else on the dock if it is hooked up before you turn it on it works great! It does not work if you hook it up after it is already turned on. 

Go to sound settings and then output to change to the dock speakers. 

So what is running during start up that finds the hardware? Is there a command that could be run after its hooked up that will find the ethernet, microphone, and speakers?

---

### Post by ninjaaron on 2011-01-25
got rotation working (not auto, but the touchscreen works.)

install touchscreen-helper and run it as a command (terminal, alt+f2, whatever).

BOOM!

Now, go into System>Preferences>Monitors and check the box for "show monitors in panel" so you can change it on the fly.

---

### Post by Kallun on 2011-01-25
> **ninjaaron said:**
> got rotation working (not auto, but the touchscreen works.)

install touchscreen-helper and run it as a command (terminal, alt+f2, whatever).

BOOM!

Now, go into System>Preferences>Monitors and check the box for "show monitors in panel" so you can change it on the fly.

I'm at work right now, so can't try this, but if it works.... Wooooo!, Could make little launchers in the menubar for different orientations :D

Nice one!

---

### Post by ninjaaron on 2011-01-25
> **Kallun said:**
> I'm at work right now, so can't try this, but if it works.... Wooooo!, Could make little launchers in the menubar for different orientations :D

Nice one!

Good idea.

the command is: ```
xrandr -o [normal, inverted, left, right, 0, 1, 2, 3]
```
(numbers and words do the same thing).

I've made two launchers; one for left, and one for normal. I'm not clever enough to make a script that toggles the two... but if someone is... ;)

---

### Post by Kirboosy on 2011-01-25
> **ninjaaron said:**
> got rotation working (not auto, but the touchscreen works.)
 
install touchscreen-helper and run it as a command (terminal, alt+f2, whatever).
 
BOOM!
 
Now, go into System>Preferences>Monitors and check the box for "show monitors in panel" so you can change it on the fly.
 
I somehow knew that you would be the person to figure it out. ;) After when I first made the thread you made a big deal about the screen not rotating.
 
I added it to the "How To" portion of the thread.

---

### Post by ninjaaron on 2011-01-25
> **Caboose885 said:**
> I somehow knew that you would be the person to figure it out. ;) After when I first made the thread you made a big deal about the screen not rotating.
 
I added it to the "How To" portion of the thread.

one thing about the HowTo entry: I think you have to run the command "touchscreen-helper" the first time before it will work. After that it starts at login... At least that's what I did (then again, it may just be that you have to do it to get the daemon running without refreshing your session). 
You *could* also add the xrandr commands for creating the panel buttons that I put up in my following post, but maybe that's sort of outside the realm of this How To. Your choice.


But yeah, today I woke up and thought, "It doesn't make sense that this would be a kernel bug, cause you could theoretically calibrate the mouse however you wanted." Then I realized that there must already be a solution and decided to find it.

---

### Post by Kirboosy on 2011-01-25
> **ninjaaron said:**
> one thing about the HowTo entry: I think you have to run the command "touchscreen-helper" the first time before it will work. After that it starts at login... At least that's what I did (then again, it may just be that you have to do it to get the daemon running without refreshing your session). 
You *could* also add the xrandr commands for creating the panel buttons that I put up in my following post, but maybe that's sort of outside the realm of this How To. Your choice

I think moving the post around is sufficient. Whenever the person reboots the program will automatically initialize. I just moved it up a bit before the Microphone fix.

Adding the commands...

---

### Post by w1ll1am on 2011-01-25
awesome that works great I can't wait for auto rotation!

---

### Post by garwal on 2011-01-25
> **w1ll1am said:**
> awesome that works great I can't wait for auto rotation!

I have been working with the person that submitted the addition to the Kernel for support for the 3 Axis galvanometer . Hopefully I will have a solution that will be an easy one . In case anyone is interested here is how the device works. 

Hi Gary,

I hope you will find this information useful.This is how you can detect yr device rotated or not

Preetham rao


*   x<0         x>0
 *                ^
 *                |
 *    +-----------+-->  y>0
 *    |           |
 *    |           |
 *    |           |
 *    |           |   / z<0
 *    |           |  /
 *    |           | /
 *    O-----------+/
 *    |[]  [ ]  []/
 *    +----------/+     y<0
 *              /
 *             /
 *           |/ z>0 (toward the sky)
 *
 *    O: Origin (x=0,y=0,z=0)

* Acceleration
 * ------------
 *
 *  All values are in SI units (m/s2) and measure the acceleration of the
 *  device minus the force of gravity.
 *  
 *  x: Acceleration minus Gx on the x-axis 
 *  y: Acceleration minus Gy on the y-axis 
 *  z: Acceleration minus Gz on the z-axis
 *  
 *  Examples:
 *    When the device lies flat on a table and is pushed on its left side
 *    toward the right, the x acceleration value is positive.
 *    
 *    When the device lies flat on a table, the acceleration value is +9.81,
 *    which correspond to the acceleration of the device (0 m/s2) minus the
 *    force of gravity (-9.81 m/s2).
 *    
 *    When the device lies flat on a table and is pushed toward the sky, the
 *    acceleration value is greater than +9.81, which correspond to the
 *    acceleration of the device (+A m/s2) minus the force of 
 *    gravity (-9.81 m/s2).
 *    

Also I want to let you all know I received all the restore disks from Dell yesterday which also included all Stage Applications and CyberLink YouPaint. I have not tried it yet but I am assuming that this install disk will also include the script to call all the apps to the stage. Just FYI in case any want to restore to factory state. If any one would like a copy I would be glad to provide it, just need a place to host these files.

---

### Post by Kirboosy on 2011-01-25
> **garwal said:**
> Also I want to let you all know I received all the restore disks from Dell yesterday which also included all Stage Applications and CyberLink YouPaint. I have not tried it yet but I am assuming that this install disk will also include the script to call all the apps to the stage. Just FYI in case any want to restore to factory state. If any one would like a copy I would be glad to provide it, just need a place to host these files.

Dell had installed a recovery partition on the Duo. To access it you simply run Windows and tell it to "repair your computer" (generally F8 before W7 actually starts booting) Then there should be ""Dell Datasafe Restore and Emergency Backup". This will wipe everything off your computer also it is much faster than CDs though.

Glad to see you are still researching the accelerometer still. Hopefully you can get it working soon. :)

---

### Post by garwal on 2011-01-25
> **Caboose885 said:**
> Dell had installed a recovery partition on the Duo. To access it you simply run Windows and tell it to "repair your computer" (generally F8 before W7 actually starts booting) Then there should be ""Dell Datasafe Restore and Emergency Backup". This will wipe everything off your computer also it is much faster than CDs though.

Glad to see you are still researching the accelerometer still. Hopefully you can get it working soon. :)

I had scrubbed the HD ,zip, nada ,gone:p:p:p
I want all the real estate it's mine I say:lolflag:

---

### Post by ninjaaron on 2011-01-25
Revamped [orta-big]("http://ubuntuone.com/p/ZMk/") metacity theme. This time I actually made the images of the buttons themselves longer. This one looks good and is really easy to touch. Oviously, as a simple metacity theme, it will work with other gtk2 themes than just orta.

again, unzip and drop the folder it in ~/.theme and it should automatically appear in Appearance>Themes>Customize>Window Border

---

### Post by ninjaaron on 2011-01-26
a'ight ya'llz, I didn't have the brains to make the rotation toggle script myself, but I did have the brains [to get someone in 'General Help' to write it for me.]("http://ubuntuforums.org/showthread.php?t=1675299") Shout out to **pl@yer** for getting the script working. Here we go:

In a terminal, type:
```
gedit .screen-rotation-toggle
```
copy this into the editor:
```
#!/bin/sh
rotation=`xrandr -q --verbose|grep LVDS1|cut -b37-43`
if [ $rotation = "normal" ] ;
then
  xrandr -o left
else
  xrandr -o normal
fi
```
then save and close the file.
back in terminal land type
```
chmod +x .screen-rotation-toggle
```

close the terminal.
When you create the launcher (in your panel, menu, or dock of choice), in the "command" box put
```
./.screen-rotation-toggle
```

[I]Note:
This script is saved in as a hidden file in your the home folder. If you want it to be available to other users, you will have to modify these instructions.[/I]

---

### Post by Kallun on 2011-01-26
> **ninjaaron said:**
> a'ight ya'llz, I didn't have the brains to make the rotation toggle script myself, but I did have the brains to get someone in 'General Help' to write it for me. Shout out to **pl@yer** for getting the script working. Here we go:

In a terminal, type:
```
gedit .screen-rotation-toggle
```
copy this into the editor:
```
#!/bin/sh
rotation=`xrandr -q --verbose|grep LVDS1|cut -b37-43`
if [ $rotation = "normal" ] ;
then
  xrandr -o left
else
  xrandr -o normal
fi
```
then save and close the file.
back in terminal land type
```
chmod +x .screen-rotation-toggle
```

close the terminal.
When you create the launcher (in your panel, menu, or dock of choice), in the "command" box put
```
./.screen-rotation-toggle
```

[I]Note:
This script is saved in as a hidden file in your the home folder. If you want it to be available to other users, you will have to modify these instructions.[/I]

Damn it! why am I always at work when I read these awesome updates! Seriously nice work! To both pl@yer and ninjaaron. Gunna do this as soon as i'm back home, i'll try your theme too!

---

### Post by Kirboosy on 2011-01-26
> **Kallun said:**
> Damn it! why am I always at work when I read these awesome updates! Seriously nice work! To both pl@yer and ninjaaron. Gunna do this as soon as i'm back home, i'll try your theme too!

If you're at work then why are you on here? Shouldn't you be "working"? ;)

[QUOTE=ninjaaron]a'ight ya'llz, I didn't have the brains to make the rotation toggle script myself, but I did have the brains [to get someone in 'General Help' to write it for me.]("http://ubuntuforums.org/showthread.php?t=1675299") Shout out to **pl@yer** for getting the script working[/QUOTE]

I saw that thread and I was thinking about posting on it but I didn't. :P Very good job to Pl@yer for writing the script and for ninjaaron to finding someone to help us. :D

I modified my script some. I like mine to rotate right ;)

---

### Post by w1ll1am on 2011-01-26
> When you create the launcher (in your panel, menu, or dock of choice), in the "command" box put
```
./.screen-rotation-toggle
```This did not work for me I had to do
```
 /.screen-rotation-toggle 
```also it did not work after
```
 chmod +x .screen-rotation-toggle 
```I had to go in to / and change the permissions by right clicking and going to properties.

other than that works great good job.

P.S. I can not add anything to the panel in netbook edition only in standard gnome and once I log back in to unity it is not there can everyone else add stuff to there panel?

---

### Post by Kallun on 2011-01-26
[QUOTE=Caboose885;10399362]If you're at work then why are you on here? Shouldn't you be "working"? ;)

Haha Caboose, you're on here at work too :P It seems to make the day go a bit quicker when I don't have a million e-mails to deal with ;D

---

### Post by Kirboosy on 2011-01-26
> **Kallun said:**
> Haha Caboose, you're on here at work too :P It seems to make the day go a bit quicker when I don't have a million e-mails to deal with ;D

Truth, I wish I could get internet on my Duo at work though. Then I would be able to work on solutions, but company policy prohibits me from connecting it. :(

At least Ubuntu Forums isn't blocked :D

---

### Post by ninjaaron on 2011-01-26
> **w1ll1am said:**
> This did not work for me I had to do
```
 /.screen-rotation-toggle 
```also it did not work after
```
 chmod +x .screen-rotation-toggle 
```I had to go in to / and change the permissions by right clicking and going to properties.

other than that works great good job.Weird, but at least you got it to work. Are you using a shell besides bash, out of curiosity? Also, did you save it in **/** or in **~** ?
> P.S. I can not add anything to the panel in netbook edition only in standard gnome and once I log back in to unity it is not there can everyone else add stuff to there panel?

As far as I can tell, from the GUI you can only add programs that appear in the panel as they are running (by right clicking and selecting... some option with a forgettable name...). Obviously a shell script doesn't have an window in X, so it never appears in the panel.

Apparently there is also a config file that may be edited to add more items to the panel. I think there is a post about it somewhere in this giant thread, and certainly somewhere else on the Internet.

I've sort of abandoned Unity for the time being. It's a good idea, but a little half-baked in 10.10. I'm quite sure you can add panel launchers already in the daily alpha builds of 11.04, so that shouldn't be a problem in the near future, but I haven't tested it myself.

You could also theoretically run an independent doc (AWN, Cairo, Docky...) and put launcher there, but having to run another dock sort of makes Unity redundant.

---

### Post by ninjaaron on 2011-01-26
> **Caboose885 said:**
> I modified my script some. I like mine to rotate right ;)

It almost seems more natural to rotate it to the right, but I opted against it because of the location of the ports and plug. I rest the bottom on my lap or against my stomach a lot in tablet mode (d*mn heavy tablet, afterall), so it seems more practical to have the ports on top.

Luckily, I've kept 'my code' open source so we can all modify it for our needs. :P

---

### Post by w1ll1am on 2011-01-26
> **ninjaaron said:**
> Weird, but at least you got it to work. Are you using a shell besides bash, out of curiosity? Also, did you save it in **/** or in **~** ?

I did everything that was said to do so i saved it in /. 

I am running cario in gnome and have the launcher there it works fine but it just takes up too much room.

---

### Post by w1ll1am on 2011-01-26
Okay I got the dock speakers to work it seems like all you have to do is set them up for the first time so...

plug your duo into the dock and then turn it on boot into Ubuntu. Once in Ubuntu go to System-> Preferences -> Sound. Then click on the output tab and you should see Docking Audio select that and everything will work.

If you are listening to music and hook it up to the dock it will take a second but then it will switch over to the dock speakers and when you take it off it switches back.

Everything works on my dock now USB, headphone, SD card slot, volume/mute switch and kinda the Ethernet. Ethernet still only works if it is hooked up to the dock before boot.

---

### Post by ninjaaron on 2011-01-26
So long as we're scripting, I threw something together to control brightness (as the panel applet for brightness doesn't seem to work). It requires the installation of "xbacklight".
*edit: I've completely redone the script because I didn't feel like the increases were even to the eye. The increments are quadratic now, and I feel like that works better. Left the old script there, but commented out.*
```
#!/bin/sh
# backlighter
# adjusts backlighting

if [ `xbacklight` = 100.000000 ]; then
  xbacklight = 0
elif [ `xbacklight` = 0.000000 ]; then
  xbacklight = 27
elif [ `xbacklight` = 26.666667  ]; then
  xbacklight = 60
else
  xbacklight = 100
fi
exit

# This is the origninal script that adjust backlighting by a set
# increment. I found didn't seem quite even, so I rewrote it to go
# by more natural steps. Uncomment this and comment (or delete)
# the other to go back to set increments (which is easier to
# modify).

#if [ `xbacklight` = 100.000000 ]; then
#  xbacklight = 0
#else
#  xbacklight +34	#this number adjusts the increment
#fi
```

The program seems to only accept intervals of 6.6666667%, so if you set it to 50, it will go down to 46.6, and you will still have four steps to go through, but the last one will only be a change of 6.67%. It's a bit weird, but there it is.

I made this because my eyes get tired really fast if I'm staring at a backlight that's too much brighter than the light in the room and I find low backlight settings preferable for reading, which is the main reason I bought this instead of another netbook.


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

> **w1ll1am said:**
> I did everything that was said to do so i saved it in /. 

I am running cario in gnome and have the launcher there it works fine but it just takes up too much room.

Hmm... when I do the same, it saves in **~**, but no biggy, I guess, so long as you have it working. In any case, you could try to put it in your panel instead of in your dock. That's where I ended up putting mine.

---

### Post by w1ll1am on 2011-01-26
I ended up just making a launcher and putting it in my unity dock.

---

### Post by w1ll1am on 2011-01-26
Okay so I was getting tired of clicking the wrong button when trying to minimize, maximize, or exit. So I found an Ambiance theme and modified it to make the buttons further apart. To install it you just have to extract it then install the folder inside the extracted one to /usr/share/Themes. Then go to appearance and select the new theme. 

There is a screen shot too so you can see it if you do not want to install it to see how it looks.

this works in unity but not when the windows are maximized and works in gnome fine.

---

### Post by ninjaaron on 2011-01-27
> **w1ll1am said:**
> Okay so I was getting tired of clicking the wrong button when trying to minimize, maximize, or exit. So I found an Ambiance theme and modified it to make the buttons further apart. To install it you just have to extract it then install the folder inside the extracted one to /usr/share/Themes. Then go to appearance and select the new theme. 

There is a screen shot too so you can see it if you do not want to install it to see how it looks.

this works in unity but not when the windows are maximized and works in gnome fine.
[http://ubuntuforums.org/showpost.php?p=10382535&postcount=164]("http://ubuntuforums.org/showpost.php?p=10382535&postcount=164")
;)

---

### Post by Trooper_Max on 2011-01-27
Thanks for the great guide everyone!

I'm new here, but just joined up to say my thanks and share my own experiences (got lengthy, but hopefully someone finds it useful or inspiring). Basically I created recovery images/media for safety/backup, got my Duo triple-booting Windows 7, loop-mounted Ubuntu, Android x86 (not to mention various live ISOs), and got Chrome going with some extensions to make it more touch friendly.

I got my Duo from the Microsoft Store (at the time when I ordered just before the holidays it estimated arrival on Dec 27th whereas Dell site said it would take 15 days to build, putting it into the new year, so I was presently surprised when it arrived the day before Christmas). It seems it came with "Microsoft Signature" even though I didn't pay the extra hundred bucks to ask for it. Basically that means they removed McAfee and possibly other trialware and replaced it with Microsoft stuff (Microsoft Security Essentials) and added Bing wallpapers (which are actually pretty good).

So one of my first concerns with a new device is being able to restore it if I mess something up. I actually made a **dd** image of the entire hard drive (in a slightly used state) and then enclosed that in squashfs for compression (using **mksquashfs**, compressed 320GB hard drive image down to under 40GB, so it was pretty sparse). This has become my preferred way of making read-only archive images because it is compressed and yet I can mount the squashfs to have full access to the raw image, from which I can mount the partitions themselves (yup, talking loop devices mounted off a loop device :D). I'm also able to dd the image back over the hard drive to restore my Duo to the "Microsoft" state. I also used the Dell Data Safe local backup utility to make the recovery thumb drive (I used an 8 gig drive because it was the smallest I have that was large enough). I did this after first zeroing out the thumb drive (dd from /dev/zero) so that I could create a dd image of the thumb drive and then squash it (though in this case I only saved just over a gig). I found that I was able to dd this 8 gig image onto a 16 gig thumb drive and it functioned fine as a recovery drive, so I can restore my image onto either the 8 or 16 as is convenient for me at the time, either works. So the thumb drive lets me restore it to the Dell Factory Image, which is before Microsoft Signature was applied. Satisfied that I could now restore my Duo to either the Dell or Microsoft states as I wish, I went back to the Microsoft state (not a fan of McAfee and didn't see anything else I wanted). I actually ended up removing the Dell Data Safe local backup utility after this since I don't need it and it had started bugging me to upgrade it to premium.

Next I installed **Wubi**, though I could have done this later because afterwards I decided to remove the extra partitions and extend the Windows partition to fill the entire drive (did this using a live Ubuntu usb and gparted). After that I had to use a Windows 7 usb (which I'd created for one of my other machines) to repair the Windows startup to allow it to start normally. I ended up installing **GRUB2** on the drive though since I wanted to add more options (like the Android x86 Sparta build, which did its own bootloader modifications). I used GRUB2 becauce I'd experimented with it before and was confident I could get it booting all three and I did. You can use an Ubuntu live usb/cd to install GRUB2 on a mounted drive using the command: (assuming its mounted at /media/Windows)

sudo grub-install --root-device=/media/Windows /dev/sda

And then on the drive, in the boot folder there's a grub folder in which you create a grub.cfg, here's mine for reference:

```
set default="0"
set timeout=7
set disklabel="Denelle"
set isopath="/Users/Trooper_Max/Downloads/ISO"

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

set ubuntu_parameters="quiet splash usbhid.quirks=0x0eef:0x725e:0x40"

menuentry "Windows 7" {
	set root='(hd0,3)'
        search --no-floppy --label $disklabel --set root
	chainloader +1
}

menuentry "Ubuntu" {
	set root='(hd0,3)'
        search --no-floppy --label $disklabel --set root
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-24-generic root=LABEL=$disklabel loop=/ubuntu/disks/root.disk ro $ubuntu_parameters --
	initrd /boot/initrd.img-2.6.32-24-generic
}

menuentry "Android 2.2 x86" { 
	set root='(hd0,3)'
        search --no-floppy --label $disklabel --set root
        linux   /android-2.2/kernel quiet root=/dev/ram0 androidboot_hardware=sparta acpi_sleep=s3_bios,s3_mode SRC=/android-2.2 SDCARD=/sd/sdcard.img
        initrd  /android-2.2/initrd.img 
}

menuentry "@Maverick" {
    set isofile="$isopath/ubuntu-10.10-desktop-i386.iso"
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt $ubuntu_parameters --
    initrd (loop)/casper/initrd.lz
}

menuentry "@Lucid" {
    set isofile="$isopath/ubuntu-10.10-desktop-i386.iso"
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt $ubuntu_parameters --
    initrd (loop)/casper/initrd.lz
}

menuentry "@Maverick Netbook" {
    set isofile="$isopath/ubuntu-10.10-netbook-i386.iso"
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt $ubuntu_parameters --
    initrd (loop)/casper/initrd.lz
}

menuentry "@Lucid Netbook" {
    set isofile="$isopath/ubuntu-10.04-netbook-i386.iso"
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt $ubuntu_parameters --
    initrd (loop)/casper/initrd.lz
}

menuentry "@Tinycore" {
    set isofile="$isopath/tinycore_2.11.1.iso"
    loopback loop $isofile 
    linux (loop)/boot/bzImage
    initrd (loop)/boot/tinycore.gz
}
```

Yup, I also like to boot ISOs stored on the hard drive :-) I do this on my external hard drive too and yup, I name my computers and my Duo is named Denelle (yeah, it's Dell plus a few other letters mixed in)**-change the disk label to the label of your disk**. Note that my Ubuntu there is the loopmounted Wubi install (I uninstalled Wubi from Windows though after copying the disk files), and I did have to point it to the specific kernel version and initrd, not the links on the root of the disk images because grub doesn't seem to work with the links. I like the loop mounted install because it means I don't have to mess with my partition table ever again. And I've found that it's actually possible to modify the location of the disks (be sure to edit the fstab in the disk image as well, note you can mount disk images using a live usb), so it should also be possible to have separate lucid and maverick disk images that can both be loop mounted and booted via GRUB2. So this lets me have multiple installs without partitioning and backing up is as simple as copying a file.

Also, Chrome has become my browser of choice (there were some things I liked about it when it came out that made it nicer for my preferences than FireFox, though admittedly FireFox has probably since become just as nice for the most part), but I found it to be horrible as a touch browser (making everything smaller around the edges really backfired!). No touch dragging and the worst is those tiny X buttons to close the tabs. Luckily there is a Chrome Touch extension that enables touch dragging (though it is not perfect, make use of the modes it provides, which can be switched between just by tapping the icon in the address bar: full to force touch dragging which won't let you select text, auto to let it try to decide, off to disable it). There's also an extension that lets you double click (or triple click if you prefer) to close tabs, though be aware it is by double-clicking anywhere on the page, not the tab at the top. Also note that these extensions don't work on special chrome pages such as chrome://downloads or chrome://extensions, which is annoying but I'm guessing the Chrome developers didn't want extensions circumventing the special chrome pages. Here are the links to the extensions (these work for me in Windows and Ubuntu):
[http://www.chromeextensions.org/appearance-functioning/chrometouch/](http://www.chromeextensions.org/appearance-functioning/chrometouch/)
[https://chrome.google.com/extensions/detail/megplcpdkmjjoondippkedoaidkeikcm](https://chrome.google.com/extensions/detail/megplcpdkmjjoondippkedoaidkeikcm)

If anyone wants a more detailed walkthrough on any of the stuff I described, let me know, but try not to derail this thread too far away from stuff specific to Ubuntu on the Dell Inspiron Duo. Feel free to message me if you create another thread related to something I mentioned and would like my comments on, just message me with a link to the thread.

**Main things I'd still like to see from Ubuntu on the Duo:**

Nice on-screen keyboard that is always available (at login and lock screens) - sounds like ya'll have made some headway here, but are the keyboards available at the lock screen?

Multitouch support and UI enhancements (it'd be nice to be able to press and hold one finger down on the title bar of a window, then use a second finger to resize the window ie similar to pinch and zoom, would also be neat if windows or at least the on-screen keyboard could be rotated using two fingers as well - basically you'd place one finger on the title bar and then drag another finger away from the first to make a window bigger or toward the first to make it smaller or rotate it to rotate the window)

~Troop

---

### Post by ninjaaron on 2011-01-27
> **Trooper_Max said:**
> 
**Main things I'd still like to see from Ubuntu on the Duo:**

Nice on-screen keyboard that is always available (at login and lock screens) - sounds like ya'll have made some headway here, but are the keyboards available at the lock screen?


At the login screen, click the guy with outstretched arms in the bottom right corner. A tab pops up that says Universal Access or something. Click it. From here a dialogue opens that will allow you to have onboard present at every boot.

To get the keyboard at the lock screen, go onboard settings (you may have to edit your menu under "Universal Access" to enable this program). There is an option to "Show onboard when unlocking the screen." On the other hand, you may choose to turn off the password requirement for waking from suspend and hibernate with [Ubuntu Tweak.]("http://ubuntu-tweak.com/downloads/")

So there it is.

---

### Post by ninjaaron on 2011-01-27
> **Caboose885 said:**
> We might not need the accelerometer to work in order to pull it off. The screen and the touchpad are on two different inputs. One is mouse0 and the other is mouse1

Maybe a script that says when I use mouse0 the pointer disappears but when I use mouse1 the pointer appears.

I found this program called "unclutter" Which is a step in the right direction. It hides the mouse after 5 seconds of not being used. It still appears when you touch but at least it will hide while reading something. I might be able to modify the program to work for us :D

Its in Synaptic Package Manager. Just type in the quick search box "unclutter" and install it :D

you can set the time it takes for uncltter to hide the mouse with: ```
unclutter -idle [time in seconds]
```You can set it to 0 if you like, and then the pointer is only visible while you are actually touching the screen, so yo won't see it at all. setting it this low causes some jittery behaviour when using the touchpad. I have mine set to 0.1, so I can see the pointer for a tenth of a second before it disappears, in case I'm having trouble hitting a button.

---

### Post by Kirboosy on 2011-01-27
> **ninjaaron said:**
> you can set the time it takes for uncltter to hide the mouse with: ```
unclutter -idle [time in seconds]
```You can set it to 0 if you like, and then the pointer is only visible while you are actually touching the screen, so yo won't see it at all. setting it this low causes some jittery behaviour when using the touchpad. I have mine set to 0.1, so I can see the pointer for a tenth of a second before it disappears, in case I'm having trouble hitting a button.


I think I might set mine to 1. That way its at least visible while its moving...at least until I can find a better solution.

---

### Post by ninjaaron on 2011-01-27
> **Caboose885 said:**
> I think I might set mine to 1. That way its at least visible while its moving...at least until I can find a better solution.

The hardware must send some kind of signal when it goes into tablet mode, because Windows knows. What we really need is a daemon that watches these signals and acts accordingly. Alternatively, it might also be based on the last used mouse input, but that kind of thing is way over my head.

In the meantime, I'm working on a script that can toggle unclutter. I have the commands; [FONT="Courier New"]unclutter -idle 0.1[/FONT] and [FONT="Courier New"]pkill unclutter[/FONT]; but the initial instance stays in the process list as [FONT="Courier New"]<defunct>[/FONT] even after it's dead, so it's giving me some difficulty with grep.

Any idea where that initial instance runs from? It's not in 'Startup Applications,' but it doesn't start until login.

hmm...

---

### Post by Trooper_Max on 2011-01-27
Thanks ninjaaron!
 
And doubly so guys, 'cause I actually also have the Toshiba Libretto w105 dual-touchscreen device and will be trying to carry over some of this touch-relevant knowledge gained here to efforts over there (that touchscreen helper program should be a huge boon-though it may need some modifications for two touchscreens, and always having access to the onBoard keyboard is super important on a touch-only device).
 
This is the device (it was limited release):
[http://us.toshiba.com/computers/laptops/libretto/W100/W105-L251](http://us.toshiba.com/computers/laptops/libretto/W100/W105-L251)
 
Here's the thread:
[http://ubuntuforums.org/showthread.php?p=10404067#post10404067](http://ubuntuforums.org/showthread.php?p=10404067#post10404067)
 
Don't mean to derail the thread, just wanted to say thanks again and let you guys know some of your efforts may be useful elsewhere as well.
 
Hopefully I'll get to the point where I can catch up and contribute too, but my time is sparse and working with two devices on the cutting/bleeding edge out here sounds pretty demanding XD
 
~Troop

---

### Post by ninjaaron on 2011-01-27
No prob' Troop!

In other news, I cracked the **unclutter toggle** nut... twice, actually. (not an automatic hardware solution,)

First, I gave up on finding the file that autostarts unclutter, and that actually led me to a more useful solution, albeit a bit messier. This solution uses two scripts and a persistence file, so it remembers the unclutter status between logins and boots. That's nice.

Then I found out how to disable unclutter's autostart: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1450975]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1450975")
I tried it, and sure enough, it stopped the weird zombie process listing. I haven't actually written it yet, but this will only take one script. The cursor will start out on (unless you make a startup command), and it will be toggled by the script from there.

so, Solution #1 (that remembers your settings between boots):
1. Create a file named [FONT="Courier New"].cursor-status[/FONT]. You can leave it empty or write the text [FONT="Courier New"]off[/FONT] in it. It won't make a differnce.

2. in the same directory create this script:
```
#!/bin/sh
cursor=`cat .cursor-status`
if [ $cursor = "on" ] ;
then
  unclutter -idle 0.1 &    # adjust idle time here
  echo off > .cursor-status
else
  pkill unclutter
  echo on > .cursor-status
fi
echo "cursor is " `cat .cursor-status`
exit
```
This is the toggle script. You can edit the interval before the cursor disappears. 0.1s works well for me. Your mileage may vary.

3. In the same directory as the other two create the second script:
```
#!/bin/sh
cursor=`cat .cursor-status`
if [ $cursor = "on" ] ;
then
  pkill unclutter
  echo "cursor is $cursor"
else
  unclutter -idle 0.1 &   # adjust idle time here
  echo echo "cursor is $cursor"
fi
exit
```
This is the starup script. If you changed the idle time in the other one, you better do it in this one too.

4. make your scripts executable.

5. put the command for the first script in some launcher somewhere, and the command for the second script in your "Startup Applications,"

6. Profit
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

I'll get back to you on the single-script version when I get around to it. Here's a hint for anyone who wants to try to figure it out in the meantime: you have to disable unclutter at login (see link in the third paragraph), and you will need this command for the condition:
```
ps -u USERNAME | grep unclutter
```

---

### Post by w1ll1am on 2011-01-28
So has anyone got their buletooth to work? I only have Ubuntu on my duo and my bluetooth icon shows up but it is disabled and I can not enable it I am thinking that if I booted into windows and turned it on and then went back into Ubuntu it  would work but I do not have windows anymore.

---

### Post by Kirboosy on 2011-01-28
> **w1ll1am said:**
> So has anyone got their bluetooth to work? I only have Ubuntu on my duo and my bluetooth icon shows up but it is disabled and I can not enable it I am thinking that if I booted into windows and turned it on and then went back into Ubuntu it  would work but I do not have windows anymore.

If I boot into windows my bluetooth works. Then when I reboot to Ubuntu my bluetooth works for that boot, however my touchscreen and mouse get screwed up. So its a lose lose situation. I'm still trying to see if there is a fix for this...

Oh interesting thing I read today. I saw that Ubuntu 11.04 will have Unity as its default interface. I'm not sure how I feel about this. Gnome3 looks really promising. The only thing about gnome3 is it won't support compiz. It seems as is compiz is slowly trying to be faded out. :(

---

### Post by ninjaaron on 2011-01-28
I'm single booting and my bluetooth has worked from the start.

And FYI, 11.04 will also "ship" with Gnome 2.x, just like UNE does now. Furthermore, Unity in 11.04 is being totally rebuilt as a Compiz plugin. Compiz will be there in all of it's glory. I've been watching the development of 11.04 rather closely, and Unity is going to be a whole other animal by the time we get it. It's already miles away from what we are using (though some of the differences can already be seen in Unity 2D).

Plus, you will be able to install and login to a Gnome 3 session, just like you can do with KDE, xfc, Unity, Fluxbox, etc. already. That's the beauty of the Linux desktop: you're not bound by the choices of a single developer.

---

### Post by w1ll1am on 2011-01-28
> **ninjaaron said:**
> I'm single booting and my bluetooth has worked from the start.

So you can turn your Bluetooth on and off and send/receive files?

---

### Post by ninjaaron on 2011-01-29
> **w1ll1am said:**
> So you can turn your Bluetooth on and off and send/receive files?

Correct. On and Off was there from the start. Had to install and setup gnome-user-share ("Personal File Sharing" in the software center) before I could send and receive files.

But yeah. Works nice.

---

### Post by w1ll1am on 2011-01-29
> **ninjaaron said:**
> Correct. On and Off was there from the start. Had to install and setup gnome-user-share ("Personal File Sharing" in the software center) before I could send and receive files.

But yeah. Works nice.

Lucky you I am going to try to boot up in windows and turn it on I have to switch back to the original hard drive but it might be worth it.

I also reedited my Ambiance theme the actual buttons are larger now and not just the area that you can click. To install it just put the Ambiance-Touchscreen folder in to /usr/share/themes.

---

### Post by w1ll1am on 2011-01-29
Okay I have bluetooth on my desktop ubuntu 10.10 and it is not working either. It worked in 10.04 so I am not sure what the problem is. Does anyone besides ninjaaron's bluetooth work?

---

### Post by ninjaaron on 2011-01-29
So I combined all these scripts I've been posting into one button to rule them all. Ok, it's actually two buttons, but it works.

I now have  a Touch/Type button. When going into 'touch mode,' the onscreen keyboard is activated, the pointer is hidden, and gnome-do is turned off (gnome-do is an application launcher that I'm addicted to, but it's useless without a keyboard).

When going into 'type mode,' the onscreen keyboard is turned off, gnome-do is turned on, the screen orientation is reset to normal, the cursor is set only to hide after five seconds, and gnome-do is activated.

The other button is the rotation button, which has evolved. Now, when I press the rotation button, it automatically enters "touch mode" if it was previously in "type mode." I figured I'm only going to be rotating the screen as a tablet anyway, so I might as well get that taken care of.

There was still a problem. Florence doesn't rotate so well. Onboard, however, can be opened with specified dimensions and placement. When in portrait view, the the keyboard switches over to onboard, which draws near the bottom of the screen in the appropriate size. I have onboard set to "minimize on launch" in the settings, so I just get the little floating icon for it.

At first, I was just having it draw two different onboard windows for each orientation, but onboard is so big and ugly in landscape view that I couldn't stand looking at it... still... it does work very well... I left all the code for it in, just commented out so I can change my mind.

Course, there is a persistence file to tell what mode your in, so it remembers that stuff between boots.

Rather than inflicting more of my scripts on all of you unbidden, I think I'll wait until someone expresses an interest before I spill the beans. It's a pretty good system for me.

Whether you're interested in the launchers or not, the nice thing is that most of the code will transfer directly over whenever we figure out how to get the OS to recognize the accelerometer and tablet vs. netbook mode.

---

### Post by ninjaaron on 2011-01-29
> **w1ll1am said:**
> Okay I have bluetooth on my desktop ubuntu 10.10 and it is not working either. It worked in 10.04 so I am not sure what the problem is. Does anyone besides ninjaaron's bluetooth work?

Eh... I realize that I am, in fact, ninjaaron, but I'm curious as to whether you can turn bluetooth on and off on the desktop.  My bluetooth on my other laptop could turn on and off for a long time, but it wouldn't send or receive files until I installed gnome-user-share (just like the duo).```
sudo apt-get install gnome-user-share
```Of course, if it isn't turning on and off at all, then I don't know. It works on both of my computers in 10.10. :confused:

---

### Post by w1ll1am on 2011-01-29
> **ninjaaron said:**
> Eh... I realize that I am, in fact, ninjaaron, but I'm curious as to whether you can turn bluetooth on and off on the desktop.  My bluetooth on my other laptop could turn on and off for a long time, but it wouldn't send or receive files until I installed gnome-user-share (just like the duo).```
sudo apt-get install gnome-user-share
```Of course, if it isn't turning on and off at all, then I don't know. It works on both of my computers in 10.10. :confused:

Okay well strange thing I tried installing gnome-user-share on my desktop and restated and nothing happened still did not work. Then when I came home and turned on my desktop it was working? So I installed it on my duo and have shut it down and restarted and everything but it still will not turn on.

and now today it is not working on my desktop? it is only working when it wants to.

---

### Post by ninjaaron on 2011-01-30
Alright everyone, I just finished writing a bunch of scripts that work together to harmonize cursor visibility, onscreen keyboards, and screen rotation. It supports both onboard and florence (and actually a mix of the two on one setting).

It hides the cursor and starts the onscreen keyboard when you tell it you're in tablet mode (either by rotating the screen, or by hitting a Touch/Type launcher). When the screen rotates, it redraws the keyboard to the set dimensions. Tap the Touch/Type button again, and the screen returns to normal, the cursor reappears, and the onscreen keyboard exits.

I should be done tweaking it and documenting it in the next day or two. When it's ready, I'll tar it and put it up. I'm pretty pumped. This is the first thing I've written that does anything useful!

---

### Post by Kirboosy on 2011-02-03
My bluetooth doesn't work properly either. It says its on when I click the emblem but when I setup a new device it says the adapter is off. I tried installing gnome-user-share but that didn't help anything.

I have bluetooth on my desktop and it works no problem.

Ninjaaron--Any updates on your scripts?

---

### Post by ninjaaron on 2011-02-03
Edit: This post is obsolete. Check this thread for the lastest Touch/Type updates:
[http://ubuntuforums.org/showthread.php?p=10442849#post10442849]("http://ubuntuforums.org/showthread.php?p=10442849#post10442849")

> **Caboose885 said:**
> 

Ninjaaron--Any updates on your scripts?

They are done and they work great. Documentation for the scripts and the settings file is finished. Just need to make the setup documentation now and figure out how to GLP it. However, setup should not be a big issue for you guys, since you are all using the same hardware as I am, and I'm not too worried about GLP at the moment, since I doubt anyone would ever try to place a restrictive copyright on a shell script.

This is what it is so far:
[http://ubuntuone.com/p/cI6/](http://ubuntuone.com/p/cI6/)

[B]To make it work, make sure all the scripts are executable (they should be already). Drop the "touch-type" folder in your home folder, and put a period in front of the name to make it hidden. It won't work unless you do this.

Make a command for [FONT="Courier New"].touch-type/persistence.sh[/FONT] in "Startup Applications." This sets startup behavior. It can be configured from the 'settings' file.

Make launchers for [FONT="Courier New"].touch-type/rotation-toggle.sh[/font] and [FONT="Courier New"].touch-type/touch-type.sh[/font] where ever you make your launchers. 

That's it. Should work now.[/B]

rotation-toggle.sh controls rotation (and turns on touch mode, if it was off), touch-type toggles between mode settings. Rotation direction can be changed from the settings file. I like to make the launchers in "Universal Access," and then they are easy to put anywhere else. I also made myself a menu item for the settings file with the command [FONT="Courier New"]gedit .touch-type/settings[/font], so I don't have to d*ck around with opening hidden folders and all to get to it.

It is set up to use onBoard by default, but you can select Florence in settings (or a mixed mode). There is also a new theme for onboard that I made, which is selected by default, and I also made offensive remarks about the onBoard bundled themes (see *settings, 7.2*). The theme can be turned off. Basically, I tried to make everything configurable that I thought people would like to configure. No kvkbd. I don't really like it at all, and I don't use it, so someone else will have to add support for that if they like. That would be done with the use of a new script to draw kvkbd in different orientations, based on what I've done in draw-onboard.sh and draw-florence.sh, as well as modification to sync-keyboard.sh and the settings file.

**backlighter.sh** isn't part of the system. It's the script for the button I use to change my brightness in tablet mode. Give it a shot. [font="Courier New"].touch-type/backlighter.sh[/font]

I've also included **Big Touch Dark 2.0 metacity theme** I made with big buttons. Copy the folder into ~/.themes if you want to try it out. No screenshots yet. It's the title bar of ambience, but the buttons look nothing alike. Used Inkscape and GIMP to make them.

So that should do it, I think. There is some other stuff you would have to do if you had different hardware. If it doesn't work, or there is a problem, tell me. I've never made anything this complex. It works perfectly for me, and I tried to make it portable, but I don't know.

"Look again. The scripts are now diamonds. I'm on a horse."

Dependencies:
unclutter
touchscreen-helper (it's in the eeepc repo)

Optional:
florence
gnome-do

backlighter.sh depends on xbacklight.
It is in Universe.

All of this was created on the Dell duo. Try that with yer' damned iPad!

*Edit:*
Ok, I'm finding out that Ubuntu One is not the ideal way to host this. Anyone know a better way?

ps:> **Caboose885 said:**
> I tried installing gnome-user-share but that didn't help anything.
This may be a stupid question, but did you try configuring gnome-usr-share?

---

### Post by ninjaaron on 2011-02-03
Ok, I just tried it on my other laptop and everything worked with no modification.

looks like we're good to go.

PS. If anyone is interested, the awful default sys-tray icon for florence can be changed in /usr/share/pixmaps/florence.svg. This changes the menu item and the widget icon as well. Use whatever SVG icon you like.

You can do the same for onBoard by changing the file in /usr/share/icons/hicolor/scalable/apps/onboard.svg

Tablets should look pretty.

---

### Post by Kirboosy on 2011-02-04
> **ninjaaron said:**
> All of this was created on the Dell duo. Try that with yer' damned iPad!
+1,000,000,000 :D 

> *Edit:*
Ok, I'm finding out that Ubuntu One is not the ideal way to host this. Anyone know a better way?You could have a FTP or SFTP Server setup. Then you would physically hosting the files...

> ps:
This may be a stupid question, but did you try configuring gnome-usr-share?Yes I tried configuring it but still no avail. I still can't get the Bluetooth to be seen as on. If I could just get it to see the adapter as on...


PS... I found this compiz [plugin]("http://%22http://gnome-look.org/content/show.php/Compiz+Experimental+Plugins+32%2664+NEW+%21?content=118511"). (If you guys like compiz) Its just some extra plugins. (I really like the screensaver one.)

PSS...I also tried Opera Browser yesterday for the first time in a while. 10.25 was slow but they are up to 11.01. ITS AMAZING! Think of it as the speed of chrome but its also like firefox and a mix of Opera power ;). I just really like it. I used to use Opera exclusively until 10 came out. I backed away from it for a while because it was so bloated but they have all the speed issues fixed. Opera is truly the fasted browser again.

---

### Post by ninjaaron on 2011-02-04
> **Caboose885 said:**
> +1,000,000,000 :D give me feedback on the program damnit!!

> You could have a FTP or SFTP Server setup. Then you would physically hosting the files...perhaps I'll look into it.


> PS... I found this compiz [plugin]("http://gnome-look.org/content/show.php/Compiz+Experimental+Plugins+32%2664+NEW+%21?content=118511"). (If you guys like compiz) Its just some extra plugins. (I really like the screensaver one.)

corrected the URL.

---

### Post by ninjaaron on 2011-02-05
Edit: This post is obsolete. Check this thread:
[http://ubuntuforums.org/showthread.php?p=10442849#post10442849]("http://ubuntuforums.org/showthread.php?p=10442849#post10442849")

Ok, I got in contact with the developer of Florence. I sorta fixed it.

Florence now uses the same default config file in portrait and landscape mode, so the properties GUI tool works right again for both settings.

The user will have to specify the sizes and window locations in the Touch/Type settings file.

[http://ubuntuone.com/p/cI6/]("http://ubuntuone.com/p/cI6/")

---

### Post by Trooper_Max on 2011-02-06
A little late, but I just noticed in the package manager GUI you can select unclutter and in the menu go to Package > Configure... and it gives you the option to set whether unclutter starts automatically.

You can also right click on it and hit Properties and there is an Installed Files tab that will show you its files (from which you can probably guess how it starts up).

No need to use Perl like that other thread suggests... you can just edit the config file:
```
# /etc/default/unclutter - configuration file for unclutter

# Set this option to 'true' if you want to start unclutter
# automagically after X has been started for a user.
# Otherwise, set it to 'false'.
START_UNCLUTTER=true

# Options passed to unclutter, see 'man unclutter' for details.
EXTRA_OPTS="-idle 1 -root"

```

~Troop

---

### Post by ninjaaron on 2011-02-06
Yeah, That's actually what I did too. I didn't really read the post. I saw it said something about perl. I just went to the config file and read it.

In other news, I tried Natty Alpha 2 on my Duo (which uses kernel 2.6.38 ), and it still has the weird glitch where the cursor goes up in the corner no matter where you touch the screen. Furthermore, the fix in this thread didn't fix it there. I didn't try anything else, since I don't want to make a big time investment in setting up an Alpha where the window manager crashes every five minutes (compiz!). Brand new xorg stack, you know.

So, I couldn't really see if multi-touch working since everything was just up in the corner anyway. I didn't see any signs of two pointers popping up, but they could have been on top of each other, or maybe only one finger gets a pointer (or maybe it needs the driver from the eeepc PPA, which I didn't try, since the mouse was just going up in the corner anyway).

Also: Alpha 2 is totally unusable, but it's at least starting to look cool. I liked it a lot when it wasn't making me terrificly angry.:p

---

### Post by w1ll1am on 2011-02-07
>  There is also a new theme for onboard that I made, which is selected by default, and I also made offensive remarks about the onBoard bundled themes (see *settings, 7.2*). The theme can be turned off. 

How did you make a custom theme?

---

### Post by leobuntu on 2011-02-08
> **ninjaaron said:**
> 

In other news, I tried Natty Alpha 2 on my Duo (which uses kernel 2.6.38 ), and it still has the weird glitch where the cursor goes up in the corner no matter where you touch the screen. Furthermore, the fix in this thread didn't fix it there.

Sounds like you need to take additional steps to make Alpha2 working with multitouch:

[https://www.libavg.org/wiki/index.php/Ubuntu_Natty_Multitouch_Setup](https://www.libavg.org/wiki/index.php/Ubuntu_Natty_Multitouch_Setup)

HTH

---

### Post by Trooper_Max on 2011-02-08
How will we know if multitouch works anyway? Should we see two pointers if we tap the screen with two separate fingers? From what I've read, uTouch is the project that provides multitouch gestures, but I've been having trouble finding any sort of explanation of exactly what all the gestures are (though there are some neat videos, but I'm guessing the lack of details is because uTouch is really just an API and so the gestures that are setup with it will be system/application-specific).

I'd like to see multitouch window resizing similar to the pinch-to-zoom that is common in smartphones. Maybe have to press a finger down on the title bar first, then slide a second finger away from the first to make a window bigger, or toward the first to make the window smaller... maybe even rotate to rotate windows? That'd be kinda neat and something you can't normally do by default, but probably not very useful. Maybe pinch completely to close windows. Two finger flick the title bar toward the system bar to minimize/hide? Wouldn't even need buttons to use the buttons for this stuff anymore...

Also, if anyone is **brave**, you can find **new kernel releases** here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

That'll allow you to try newer development kernels without necessarily trying natty. There is a **2.6.37-rc2** (release candidate) kernel available for **Maverick** as .deb packages you can install using dpkg or if you just double click them in nautilus I think the Ubuntu Software center will offer to install them for you. I imagine they will update your GRUB, but if not, you may have to do this manually. I'll probably try this tonight, if not on my Duo at least on my dual-touchscreen Libretto.

Found the kernels from this thread:
[http://forums.linuxmint.com/viewtopic.php?f=42&t=40185](http://forums.linuxmint.com/viewtopic.php?f=42&t=40185)

**Mainly, be sure to **install the headers package for all architectures first, then the headers package for your architecture (i386 or amd64), then the image for your architecture (i386 or amd64).

Also, I looked at the source code to unclutter (using apt-get source) thinking about trying to develop a version of it that would act differently depending on which mouse device was last used, and it is a little more complicated than I anticipated, but I may still try to come up with a way to tweak it soon. I'm just not very familiar with X programming yet.

**Edit:** Also, this site has some useful xrandr information: [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2) Might be neat to figure out how to get a function key to rotate the screen...

~Troop

---

### Post by ninjaaron on 2011-02-09
> **Trooper_Max said:**
> 

**Edit:** Also, this site has some useful xrandr information: [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2) Might be neat to figure out how to get a function key to rotate the screen...

~Troop

Easy:
Compiz Settings Manager > Commands

add a command for xrandr or a to run a rotation toggle script. Go to the bindings tab and select what ever shortcut you like.

After you get that working, you can come back and tell me why you would ever want to rotate the screen while you were using the keyboard :lolflag:


I'll checkout the new kernel. More later.
*Edit: New Kernel installed. Nothing is broken, but no multitouch out of box. Let's see...*


PS: if you don't want to write a rotation toggle script, download my tarball in [post #227]("http://ubuntuforums.org/showpost.php?p=10425776&postcount=227") and follow the instructions. It will sync unclutter, screen rotation, and keyboard size for you. You can obviously link that to a key-binding in compiz as well.

---

### Post by ninjaaron on 2011-02-09
> **w1ll1am said:**
> How did you make a custom theme?

Well the instructions say you can use Inkscape to do it. This is a lie. onboard doesn't support some of the features that inkscape automatically saves with. Inkscape actually breaks onboard layout files because it builds groups into the file

I opened the svgs and xml (.onboard) files in a gedit and twiddled with numbers until I was satisfied. It was not fun, but it goes fast once you get the hang of it, with "replace all" and things like that. It's actually faster than inkscape for some of that stuff... Just have to brush up on your hex color codes :D .

However, onboard's svg interpreter doesn't read things like gradients and rounded corners; just boxes, strokes, colors, and IDs.

Believe me, if I could have use gradients and rounded corners, I would have. I reported it as a "bug" on their launchpad site. I feel like the people who wrote this program have never had to look at it for more than five minutes... or I hope not, at least. I like to give people the benefit of the doubt.

---

### Post by ninjaaron on 2011-02-09
*Edit:*
Alright guys, my "touch/type" thing has gone official. I made a seprate thread for it and touchscreen interface tweaks. [http://ubuntuforums.org/showthread.php?p=10442849#post10442849]("http://ubuntuforums.org/showthread.php?p=10442849#post10442849")

---

### Post by Trooper_Max on 2011-02-09
> **ninjaaron said:**
> Easy:
Compiz Settings Manager > Commands

add a command for xrandr or a to run a rotation toggle script. Go to the bindings tab and select what ever shortcut you like.

After you get that working, you can come back and tell me why you would ever want to rotate the screen while you were using the keyboard :lolflag:

Hey, you never know when you might want to do some upside down computing ;)

Really, I was just thinking of it as a hit a button before/as you flip it into tablet mode type of thing. Supposing that you always used it in portrait layout while in tablet mode, you wouldn't necessarily want to devote screen space in the form of a launcher to toggling the layout. The function key would be available as you're converting either way (or before/after). Auto would be better of course.

And yeah, I've been meaning to try out your scripts, just haven't gotten around to it yet. But I looked in the other thread and it looks pretty nice... I didn't think onboard was necessarily ugly, it just wasn't pretty, your theme is definitely much better. I'll try and post in your other thread once I've tried it out and played with it a little.

EDIT: I am also curious about the potential of Gnome Do, but I've only used it a little before... It's streamlined for a keyboard interface though, might be interesting to think about what a system similarly streamlined for touch would look like. I also recognized Docky, but have you tried Avant Window Navigator?

~Troop

---

### Post by ninjaaron on 2011-02-10
> **Trooper_Max said:**
> ... you wouldn't necessarily want to devote screen space in the form of a launcher to toggling the layout... my thoughts exactly! That's why I have it on a hidden panel.

But yeah, I find that I often want to change orientations in "tablet mode" in any event. Portrait is great for reading ebooks and veiwing certain types of media. It's a bit narrow for most websites, since it's a wide-screen display and all. For me, It's nice to have the option to rotate at any time. Course, you can just add the launcher to the menu somewhere, then you don't have any problem either way.

> EDIT: I am also curious about the potential of Gnome Do, but I've only used it a little before... It's streamlined for a keyboard interface though, might be interesting to think about what a system similarly streamlined for touch would look like. I also recognized Docky, but have you tried Avant Window Navigator?

~Troop

Gnome Do, basically just lets you open stuff really, really fast. It's nothing fancy. You don't notice it until it's not on and you feel like your dragging through the mud, navigating through a menu. There are also extetions to make it control your media player and execute shell commands, do google searches, and whatever. It's pretty nice. Gnome Do also works well with the onscreen keyboard, and sometimes I turn it on while in "touch mode."

I'm trying to get a similar level of functionality out of my drawer-based menu. If you open all of the draws, they stay open, so you really just have to click the menu button after that and all the programs are right there. The fly in my ointment is that they all close again when you logout. Still, not too bad. Course, touching the screen is inherently faster than navigating somewhere with a mouse or touchpad, so that's also something to consider. I have my most used touch mode apps pinned to the dock, Firefox and my E-Book Reader (Which is so great to be able to use. I'm loving this e-book stuff!). 

As for other docks, I like docky because it has the "panel mode," which I like because it gives me lots of empty space where I can click to bring it up when it's hidden without accidentally opening a program or changing focus. I also like it because it's the lightest in terms of resources. I tried AWN a two or three years back, and there was some reason I didn't get along with it (which I have forgotten), but I'm sure the program is different now. I really liked Cairo dock when I tried it, but it seems to be a bit more demanding of resources, and docky does exactly what I wanted: It replaces the window list and the clock on the panel (and I have it monitoring system activity now too). It has a few simple extra widgets if you like. It also does intelle-hide, which I think is great, though I think the others do that too.

I'm a freak about managing system resources, which isn't necessaries a bad thing with a netbook, so so alot of my tweaks are to keep the interface from taking over the system resources.

Some programs still open a bit slowly, however. At some point, I might wipe the system and see how it preforms with a 64bit kernel, probably in April, if not before. It uses twice the ram, but it still only boots to about 450KB, and I still hardly ever use more than 1.2GB on my more powerful system with a 64bit kernel, even when I'm using a lot of tabs in firefox, Open Office, and a few giant PDFs open.

The duo has 2GB, and there is always swap space, so it should work alright, and it may improve speed and performance for some things. As it is, I've still haven't gotten ram usage up to 50%. The CPU, on the other hand, is pretty heavily taxed at times, and 64bit might help that. I dunno.

---

### Post by Kirboosy on 2011-02-10
Uh is the Duo even 64 Bit compatible? I didn't think it was since it was a Intel Atom...


Sorry I haven't been on lately guys. My Duo is only running Windows at the moment. I should have a new thumb drive soon, at which point I will install lUbuntu and test the new kernel. I will probably also run everything from the RAM just to see how well that works. I have alot to do...just need a thumbdrive to install from.

---

### Post by Trooper_Max on 2011-02-10
> **ninjaaron said:**
> my thoughts exactly! That's why I have it on a hidden panel.

But yeah, I find that I often want to change orientations in "tablet  mode" in any event. Portrait is great for reading ebooks and veiwing  certain types of media. It's a bit narrow for most websites, since it's a  wide-screen display and all. For me, It's nice to have the option to  rotate at any time. Course, you can just add the launcher to the menu  somewhere, then you don't have any problem either way.

Or even just to make the conscious decision as to whether you're going to be in portrait or landscape as you convert... but yeah, there may still be times when you want to change layout while in tablet mode.

Also, I've done a little experimenting with having Firefox spoof different user agents (ie tell the websites its an iPhone or Android, there's a user agent switcher extension you can use) to get a more portrait-friendly interface. It's neat for the sites that have such interfaces available (they also usually have a special alternate url you can use for mobile/touch). It's also faster to surf this way sometimes because they tend to deliver lighter webpages.

> **ninjaaron said:**
>  As for other docks, I like docky because it has the "panel mode," which I  like because it gives me lots of empty space where I can click to bring  it up when it's hidden without accidentally opening a program or  changing focus. I also like it because it's the lightest in terms of  resources. I tried AWN a two or three years back, and there was some  reason I didn't get along with it (which I have forgotten), but I'm sure  the program is different now. I really liked Cairo dock when I tried  it, but it seems to be a bit more demanding of resources, and docky does  exactly what I wanted: It replaces the window list and the clock on the  panel (and I have it monitoring system activity now too). It has a few  simple extra widgets if you like. It also does intelle-hide, which I  think is great, though I think the others do that too.

Yeah, AWN does everything you mentioned, and I think it has more widgets available from the Ubuntu package repositories (some are written in c, some in python). Don't remember why I went from Docky to AWN on my other computer, but I think it had to do with AWN seeming to have more features/widgets/being better supported, and I don't remember if Docky let you get rid of that Docky settings icon... in AWN you don't have to have a settings icon taking up space (which forces you to have to right-click to get a context menu and get to the settings that way, which doesn't take up dock space and I don't change settings that often). I don't know how they compare in terms of resources, so if Docky is the lighter, does-what-you-need-it-to-do solution, that's cool.

> **Caboose885 said:**
> Uh is the Duo even 64 Bit compatible? I didn't think it was since it was a Intel Atom...

Yup, it is 64-bit. Here's the processor specs from Intel:
[http://ark.intel.com/Product.aspx?id=50154](http://ark.intel.com/Product.aspx?id=50154)

EDIT: Meant to comment I'm glad they didn't ship it with 64-bit Windows, because it's a pain (can only use signed drivers unless you do some workarounds). I'm not sure how much a 64-bit OS will really buy you over a 32-bit OS (on my desktop I have to use 64-bit in order to have access to all 8 GB of RAM, that's about the only reason I've used it). Does Ubuntu/Linux support 64-bit computing with the same level of support as 32-bit computing? (in terms of kernel/drivers - low-level stuff that uses assembly code often requires more work to get working under both architectures)

~Troop

---

### Post by ninjaaron on 2011-02-10
> **Trooper_Max said:**
> 

Also, I've done a little experimenting with having Firefox spoof different user agents (ie tell the websites its an iPhone or Android, there's a user agent switcher extension you can use) to get a more portrait-friendly interface. It's neat for the sites that have such interfaces available (they also usually have a special alternate url you can use for mobile/touch). It's also faster to surf this way sometimes because they tend to deliver lighter webpages.
:shock: I've been trying to do this. Do tell! *edit: figured it out with a google search*
> Yeah, AWN does everything you mentioned, and I think it has more widgets available from the Ubuntu package repositories (some are written in c, some in python). Don't remember why I went from Docky to AWN on my other computer, but I think it had to do with AWN seeming to have more features/widgets/being better supported, and I don't remember if Docky let you get rid of that Docky settings icon... in AWN you don't have to have a settings icon taking up space (which forces you to have to right-click to get a context menu and get to the settings that way, which doesn't take up dock space and I don't change settings that often). I don't know how they compare in terms of resources, so if Docky is the lighter, does-what-you-need-it-to-do solution, that's cool.
hmm... I'll give AWN another look and see how I like it this time around. The Docky icon is apparently immutable, which does buggy me. Plus, I guess AWN shouldn't take up to many more resources if I don't have all the extra widgets turned on. I'll definitely try it again.
*Edit: Tired it again. I like it more than Docky. It stays!*
> EDIT: Meant to comment I'm glad they didn't ship it with 64-bit Windows, because it's a pain (can only use signed drivers unless you do some workarounds). I'm not sure how much a 64-bit OS will really buy you over a 32-bit OS (on my desktop I have to use 64-bit in order to have access to all 8 GB of RAM, that's about the only reason I've used it). Does Ubuntu/Linux support 64-bit computing with the same level of support as 32-bit computing? (in terms of kernel/drivers - low-level stuff that uses assembly code often requires more work to get working under both architectures)

~Troop

Well, given the ram requirements of Windows, I think the duo would barely run a 64bit version, though I'm not particularly glad about Dell's choice to ship with 32bit Windows, since wiping the harddisk was one of the first things I did, and I'd be just as a happy with any OS they chose to ship, and even happier if they shipped it without an OS at all. I'd rather MS didn't get my money, had I the option (which, of course, I don't).

I think driver and app support for the 64bit kernel isn't much behind the 32bit kernel. There have been very few things I haven't been able to do on my 64bit system.

I realize that the major benefits of 64bit processing are for really intensive tasks like encoding and rendering, or to open up more than 4GB of ram in case you want to, say, watch several HD movies, render effects on a video, and play a few flash games all at once. Course, you'd need more and better cores than the duo has for that kind of thing anyway. 

However, I've also heard that programs can be optimised for 64bit. I've heard that there are read differences in boot-time and the performance of Google Chrome, for instance, and that was a couple of years ago... if more apps are optimized for 64bit now...

I don't know, really. I just want to try it to see if it makes any difference in performance. If not, I'll just go back to 32. No harm in trying.

---

### Post by Kirboosy on 2011-02-11
Well I installed lubuntu on my Duo. lUbuntu is RIDICULOUSLY FAST! Its designed for older, less powerful hardware. The Duo really isn't underpowered so lUbuntu flys on it! I will have to say that I'm having to relearn most of the programs because its not the normal GNOME application set. I would install some of the GNOME applications but then it would probably slow it down. I'm fine with it so far. 

Right now I'm on a quest to get compiz to work with LXDE (that's my interface now) I'm also trying to figure out the bluetooth issues but so far no success. Also, my twofinger touch doesn't work even though I installed the package...Still tinkering with everything...


Oh by the way if you guys use screensavers the 'xscreensaver-extra' package is pretty cool. They have one called "Wormhole" and its really cool. Its really simple but its still mystifying. :)

---

### Post by w1ll1am on 2011-02-11
> Oh by the way if you guys use screensavers the 'xscreensaver-extra' package is pretty cool. They have one called "Wormhole" and its really cool. Its really simple but its still mystifying. :)

I found this cool clock screensaver I was looking for a replacement for the clock on Windows 7 when you put the Duo in the dock. It is called qmlsaver it's pretty cool.

---

### Post by ninjaaron on 2011-02-12
> **Caboose885 said:**
> Well I installed lubuntu on my Duo. lUbuntu is RIDICULOUSLY FAST! Its designed for older, less powerful hardware. The Duo really isn't underpowered so lUbuntu flys on it! I will have to say that I'm having to relearn most of the programs because its not the normal GNOME application set. I would install some of the GNOME applications but then it would probably slow it down. I'm fine with it so far. I don't think Gnome applications will slow down the rest of the system too much. They might be slower themselves, but if you don't open them, they won't slow down the system just by installation, and they will certainly benefit from the extra resources available.

> Right now I'm on a quest to get compiz to work with LXDE.did you try the command [FONT="Courier New"]compiz --replace[/FONT]. 

In any case compiz is one thing that definitely will slow down the system. Openbox is an extremely lightweight and standards compliant, where compiz is really big and sexy and a bit slow. Openbox is sorta LXDE's trump card for speed.

I installed LXDE in my system to see how it was. The environment was actually pretty decent, but I found that it wasn't as easily customised for touch-accessibility as gnome.

However, it is possible to run a gnome session with openbox, if you like. There are packages to install the gnome desktop in the repositories, and then you should have an option for an openbox session at the lxdm screen (or gdm, should you chose to change it).

But... I'm hopelessly addicted to transparency effects... I can't live without compositing... (and it's not so slow with the settings I have anyway. I have most of the extras turned off)

> Also, my twofinger touch doesn't work even though I installed the package...Still tinkering with everything...

Yeah, I don't think anyone has it working. The answer might be in reconfiguring xinput... finding a way to change the settings it used when the system was installed... but I don't know how to do that short of installing it from scratch with newer kernel, and that would mean using a different distro or building Ubuntu from scratch with Debian.

I have been meaning to try out Arch... and that way I could upgrade the kernel before I even install xorg... hmmm...

But there should be some way to reconfigure xinput in a running system... just have to find it.

---

### Post by Kallun on 2011-02-12
> **ninjaaron said:**
> 
I have been meaning to try out Arch... and that way I could upgrade the kernel before I even install xorg... hmmm...


Hmmm, let us know how it goes! I'd love to see how Arch is on the Duo.

Just thought I'd drop by cause I haven't been active on this thread for a while, I'm still here guys :D I've been trying to build Gnome Shell, I keep hitting a lot of issues :/ I'll be honest, it's not particularly fun, but as soon as I get it running, I'll keep you guys posted, unless anyone else has had any success with it? There's just one or two little forks in the road I keep hitting... in fact they seem to be pretty f***ing big forks. Anyhoo, I just think it'd be a very friendly UI to have at your fingers :) Hope everyone is well

---

### Post by ninjaaron on 2011-02-12
> **Kallun said:**
> Hmmm, let us know how it goes! I'd love to see how Arch is on the Duo.

Just thought I'd drop by cause I haven't been active on this thread for a while, I'm still here guys :D I've been trying to build Gnome Shell, I keep hitting a lot of issues :/ I'll be honest, it's not particularly fun, but as soon as I get it running, I'll keep you guys posted, unless anyone else has had any success with it? There's just one or two little forks in the road I keep hitting... in fact they seem to be pretty f***ing big forks. Anyhoo, I just think it'd be a very friendly UI to have at your fingers :) Hope everyone is well

Hey, no promises about this Arch stuff! Spring semester starts tomorrow, and I don't have time to play around with my computer all day every day anymore!

So about gnome shell... I already have it on my computer. It's in the universe repository... what's the problem? [FONT="Courier New"]sudo apt-get install gnome-shell.[/FONT]

---

### Post by Kirboosy on 2011-02-12
> **ninjaaron said:**
> did you try the command [FONT="Courier New"]compiz --replace[/FONT].

I have tried that but it falls back to a failsafe x session. Whats weird is the applications I have already open on the screen I can still interact with. It just places a failsafe terminal in the upper right corner... I know its possible to get compiz working but its not as easy as it sounds.

My mouse use to two finger scroll with UNR or Gnome but LXDE behaves differently. I really like it still. Just adds a few problems. :)

---

### Post by ninjaaron on 2011-02-13
Name: Universal Menu in Gnome
Appearance: sleek
Details: much sought after, seldom achieved
Status: pwnt

[http://i4.photobucket.com/albums/y124/ninjaaron_0/universal-menu.png](http://i4.photobucket.com/albums/y124/ninjaaron_0/universal-menu.png)

---

### Post by Kallun on 2011-02-14
> **ninjaaron said:**
> Hey, no promises about this Arch stuff! Spring semester starts tomorrow, and I don't have time to play around with my computer all day every day anymore!

So about gnome shell... I already have it on my computer. It's in the universe repository... what's the problem? [FONT="Courier New"]sudo apt-get install gnome-shell.[/FONT]

Aha fair enough, the thought of Arch on the Duo just got me excited! :P

Using apt to get gnome shell gives you a relatively old build, building with git gives you the latest and greatest, and there is actually a huge difference.

---

### Post by Kirboosy on 2011-02-14
I am trying Awesome WM on my Duo. I really like minimalistic looking desktops. Although it will take a bit of time to get everything setup right in Awesome.

I also came to the conclusion that lUbuntu uses LXDE but it must be modified in such a way that compiz won't run. Whenever I went to synaptic the LXDE package wasn't installed. They have a package called the lubuntu-desktop which contains everything. Obviously something compiz needs to run is missing. However when I tried to install the LXDE package it broke my system. 

lUbuntu seems to have taken some stability away from Ubuntu because it broke way to easily. Whenever I try to boot it just sits there forever "checking battery state". I don't really have any important information on it so I will end up reinstalling UNR (that way I have both Unity and GNOME, but I'm gonna install Awesome too)


After my short walk with other versions of Ubuntu I'm coming back to the main one. Actually I might install gentoo just for giggles.... ;)

---

### Post by w1ll1am on 2011-02-14
For anyone wanting to install a SSD in their Duo.  The original drive in the Duo is a 1.8" and most SSDs are 2.5". I was able to install the drive without the bracket and it fit fine but after using it for a while I realized that when I closed the laptop it was lifted up slightly. The larger drive made the keyboard raise up just a little. I decided to take apart my Duo again and see if there was anything I could do and it turns out the only thing that fixed it was to take the case off of my drive and take out the guts. This voids the warranty on the drive but installing a SSD in the Duo voids its warranty so if you plan on doing this I doubt you are worried about that. 

Also check out my new bling!

---

### Post by Kirboosy on 2011-02-14
Yeah I wanted to take apart my Duo just to see what made it tick but as soon as I saw the sticker covered screw hole I stopped. I don't want to void my warranty. This is the first time I have actually had a new enough computer to be covered by a warranty. My luck something would break on it just after I voided my warranty.


As soon as the warranty expires though I will rip it open. :)

---

### Post by Trooper_Max on 2011-02-14
Woah, several posts to catch up on, that's what I get for having fun for a weekend >_>

> **ninjaaron said:**
> > Also, my twofinger touch doesn't work even though I installed the package...Still tinkering with everything...                                 Yeah, I don't think anyone has it working. The answer might be in  reconfiguring xinput... finding a way to change the settings it used  when the system was installed... but I don't know how to do that short  of installing it from scratch with newer kernel, and that would mean  using a different distro or building Ubuntu from scratch with Debian.

Reconfiguration beyond using the "xinput" command from the terminal? I've been fooling around with xinput on my dual-touchscreen Libretto. Seems like there's a lot of properties you can mess with there... and the test option is handy for monitoring input events.

Check out my post on the libretto thread for a little xinput reference:
[http://ubuntuforums.org/showpost.php?p=10447402&postcount=18](http://ubuntuforums.org/showpost.php?p=10447402&postcount=18)

Also, if anyone is interested, I dived into the touchscreen-helper program a little bit in my previous post in that same thread:
[http://ubuntuforums.org/showpost.php?p=10444942&postcount=17](http://ubuntuforums.org/showpost.php?p=10444942&postcount=17)

Maybe if I get some time, I'll pull down the twofinger touch source and try to figure it out, but I'm guessing it'll be a more complicated fix. And I've been giving my dual-touchscreen Libretto a little bit higher priority lately because I still haven't been able to effectively use both screens on it in Linux yet (works fine with one screen or the screens mirrored).

**Oh yeah, **one thing I noticed when using xinput on the Dell Inspiron Duo that concerned/interested me is related to that usb hid quirks kernel parameter we've been using. I noticed that without that parameter (when the touchscreen always clicks the top-left corner), the xinput list command shows the eGalax [SIZE=1](don't remember the exact name)[/SIZE] touchscreen device one time, but with the usb hid quirks kernel parameter, the eGalax touchscreen device shows up 3 times (and using xinput test, only one of them, the middle one, actually generates events). This may be relevant as we try to get multitouch and different touch features working, but hopefully it won't be an issue...

**Edit:** Also, when I wasn't using the usb hid quirks parameter, I was **not** able to fix the touchscreen problem by manipulating xinput from the command line... doubt it can be done, but it is one thing I tried to look into and am curious about.

~Troop

---

### Post by xyzo on 2011-02-16
Hi!

I've read this whole thread: very interesting :-)
I've installed Ubuntu 10.10 since the beginning and I'm not using UNE but the standard desktop.

My Duo came with an embedded GPS: it was working (well) will the stock Win7. Any idea how I could enable it with Ubuntu? I've tried GpsDrive but, as far as I can see, it doesn't recognize the GPS. Any help welcome :-) TIA!

---

### Post by Kirboosy on 2011-02-16
I don't believe mine came with a GPS. I think mine was as low as you could go. I have a option on my W7 for GPS but it doesn't actually do anything. :(

I actually just bought an external USB GPS so I can go wardriving. Have you installed the gpsd package? (It enables Ubuntu to communicate with the GPS)

Also Ninjaaron will be taking a break for about a week. He sent me a message yesterday stating he will be gone until the 21 of Febuary for various reasons. So Aaron didn't die, he just is taking a break. :)

---

### Post by Kallun on 2011-02-18
Just got Linux Mint 10 running on the Duo, it's very slick! :) The gnome panel at the bottom is perfect, it has a 'hider' button on each edge, which upon pressing, slides the panel left or right off the screen, giving you just that little extra screen real-estate ;D 
 
...One bad thing though, gnome seesm to enjoy crashing on it :/ It'll randomly take me to the login screen quite often, even when i'm not doing anything particularly intesive.
 
But as for the interface, I really like the 'Mine Menu' very touch friendly, especially with the 'Favorites' feature.
 
How's everyone doing anyway? :) Any recent breakthroughs with the Duo?

---

### Post by w1ll1am on 2011-02-18
> 
 
...One bad thing though, gnome seesm to enjoy crashing on it :/ It'll randomly take me to the login screen quite often, even when i'm not doing anything particularly intesive.
 


I have had this problem on my desktop a few times it is very annoying. It was happening to me mostly while on firefox.

---

### Post by Kirboosy on 2011-02-18
> **Kallun said:**
> it has a 'hider' button on each edge, which upon pressing, slides the panel left or right off the screen, giving you just that little extra screen real-estate ;D

You can do this with regular gnome ;) I have docky installed now and its very touchable.


As for any recent breakthroughs....none on my end. I haven't had much time to sit down and tinker. I've been trying to get my bluetooth to function properly but to no avail. I'm also running 64 bit desktop edition now and I will install unity 2D eventually.


I'm starting to hold my breath in anticipation of 11.04. I really hope they nail everything so it works properly with our Duos. Tinkering is fun and all but normal computer users just want it to "just work" (Steve Jobs, *shudder*)

---

### Post by Kallun on 2011-02-18
> **Caboose885 said:**
> You can do this with regular gnome ;) I have docky installed now and its very touchable.
 
 
As for any recent breakthroughs....none on my end. I haven't had much time to sit down and tinker. I've been trying to get my bluetooth to function properly but to no avail. I'm also running 64 bit desktop edition now and I will install unity 2D eventually.
 
 
I'm starting to hold my breath in anticipation of 11.04. I really hope they nail everything so it works properly with our Duos. Tinkering is fun and all but normal computer users just want it to "just work" (Steve Jobs, *shudder*)
 
Haha "just work", I can't imagine the day when the Linux community start calling everything 'magic' and labeling everything they do as 'innovation', kinda ironic cause most of it usually is :P
 
I know you can do it with regular gnome, I just didn't think of doing it before haha, plus the 'Mint Menu' panel is really nice :D
 
Ah that's fair enough, yeah hopefully with the arrival of 11.04 some of our troubles will be gone! I haven't attempted building gnome shell again, I hate sector 27 and beyond! Stupid 'gnome-settings' wont build because of this one package they've got it there, which when you remove, it screws the whole thing up. Mind you, since the last time, they might've sorted it :)

---

### Post by ninjaaron on 2011-02-20
hmm... looks like I'm unbant early for mouthing off at the mods. Thanx admin. :)

Hai everyone.

If you like the Mint Menu, the GnoMenu might also be worth checking out. It's basically the same thing, but more theme-able. The search function isn't integrated with the package manager unfortunately. You have to add "ppa:gnomenu-team/ppa" to your software sources to get it.

I finally got an interface I'm happy with. I sucks the window controls into the control bar ([window-applets]("http://gnome-look.org/content/show.php/Window+Applets?content=103732")), uses a Windows 7 style window selection applet, ([DockbarX]("http://gnome-look.org/content/show.php/DockbarX?content=101604")), and I got the application menus and indicator applets on their own hidden panels (indicator-applet-appmenu. It's in universe). I'm done tweaking the interface. Everything does what I want it to now. Whoo!

Tried to get a screenshot with Gnomenu open, but it doesn't work. Oh well.

*edit: p.s. Unity 2D works for real now*

---

### Post by shumifan50 on 2011-02-22
I have installed one of the Seagate Hybrid drives in my Duo. The screws to hold the drive on the bracket don't line up, but the drive is firmly held in place by the bracket and the sponge underneath it. This is because the drive is slightly thicker than the standard rive. I used PING ([http://ping.windowsdream.com](http://ping.windowsdream.com)) to make the backup of the Dell installation (all 3 partitions) and restored it on the hybrid drive. That gets you back all the Dell stuff etc and leaves 180GB unpartitioned space. (I have the 500GB with 4GB SSD). I installed Linux in the 180GB, leaving the Windows installation pretty much intact. This provides nice space for experimentation with OSes. The hybrid drive also speeds up booting and loading of frequently used applications - this will not be as fast as an SSD all the time as it does dynamic caching of most fequently used bits. If you buy this drive, remember to update the firmware to the latest version SD24, they ship with SD23.

I downloaded the Andriod USB link earlier in this thread, formatted a pendrive and dd'ed it to a USB pendrive and tried booting it, but it just came up with "GRUB" in the top left corner and hung there - or so it seems (note that it did try to boot off the USB, I saw the lights flashing and my boot options were for USB first). Should I wait for a long time before Android starts, or should it be fairly quick, which is what I sort of expect.

---

### Post by Kirboosy on 2011-02-23
It should be a quick boot process. I would reformat and dd the drive. I don't remember GRUB coming up when I played with Android... You might wanna see if you can find a md5 to check your img. cause that might be corrupt (small chance but its possible)

Also I think our sparta builds are dead because the folder for the nightly builds no longer exists :(

---

### Post by Kallun on 2011-02-24
Unity 2D's got some sexy updates, check out the link below from OMGUbuntu;

[http://www.omgubuntu.co.uk/2011/02/unity-2ds-new-design-in-motion-video/](http://www.omgubuntu.co.uk/2011/02/unity-2ds-new-design-in-motion-video/)

---

### Post by garwal on 2011-02-24
After I realized I wanted to use the duo and just not play with it I found Fontface and have not looked back. It just works and there is no trying to build a total new UI.. Check it.
[http://www.mirabyte.com/en/products/frontface-for-netbooks-and-tablets/]("http://www.mirabyte.com/en/products/frontface-for-netbooks-and-tablets/")

---

### Post by Kirboosy on 2011-02-25
Interesting Garwal but its for Windows and it cost money.Good find though. If I have any Windows friends ask I will make sure to tell them.

I am still beating my head against the wall trying to figure out how to fix Bluetooth. I have a bump on my head from it ;)

---

### Post by garwal on 2011-02-25
Here is another one I have tried yesterday. Looks great and has a great UI. Free and it is Linux. Just a little on the heavy side but that can be easily fixed. Check it:guitar:.
[http://www.ultimateeditionoz.com/]("http://www.ultimateeditionoz.com/")

---

### Post by Kirboosy on 2011-02-28
[SIZE=2]This looks awesome [Linpus Lite Multi-Touch Edition]("http://www.linpus.com/products_meego_slate.html")

Sadly it only looks like it will be available as a OEM/preinstall option. They aren't planning on making it free to download. Also its not a finished product yet.[/SIZE] 

[SIZE=3]BUT

[SIZE=2]It got me thinking. If they are using MeeGo then there must be some sort of package available to enable multi touch. I have contacted them to see if they will assist me.[/SIZE]
[/SIZE]

---

### Post by garwal on 2011-02-28
> **Caboose885 said:**
> [SIZE=2]This looks awesome [Linpus Lite Multi-Touch Edition]("http://www.linpus.com/products_meego_slate.html")

Sadly it only looks like it will be available as a OEM/preinstall option. They aren't planning on making it free to download. Also its not a finished product yet.[/SIZE] 

[SIZE=3]BUT

[SIZE=2]It got me thinking. If they are using MeeGo then there must be some sort of package available to enable multi touch. I have contacted them to see if they will assist me.[/SIZE]
[/SIZE]

MeeGo always looked good to me as well I hope you have luck with finding a source for what your after. I wonder if Acer woulkd sell a restore disk ?
garwal

---

### Post by ninjaaron on 2011-03-06
Typing this from Natty Alpha 3. Unity is starting to be awesome now and behave almost like a real operating system.

The touch input is still broken out of the box, but the environment is stable enough that I would be willing to install it on a partition and work on it if I wasn't in the middle of a lot of school work.

Still, I'm going to play with it a little on my USB.

One thing I noticed is that the touch is now broken in a different way. Now, when the screen is touched, the cursor position doesn't change, but it still registers a click. This still basically means that it's unusable, but it also means that they are working on xinput stuff.

I must say, I'm really digging the interface now, which is good, since the feature freeze is probably in effect now and they are focusing on getting the broken stuff working for the remainder of the development cycle.

Also, menu bar respects themes now, both for icons and window controls. Big buttons, here we come.

---

### Post by Kirboosy on 2011-03-07
Hmm so your touchscreen is now completely unusable?

Also what about Bluetooth?

---

### Post by Kallun on 2011-03-07
> **Caboose885 said:**
> Hmm so your touchscreen is now completely unusable?

Also what about Bluetooth?

Nope, I think he means when touching the screen it registers some sort of input, but instead, doesn't jump to the top left like in 10.10, I experienced the same thing. It works fine after you've edited the grub conf file :)

---

### Post by Kirboosy on 2011-03-07
I take it bluetooth is still screwy?

---

### Post by ninjaaron on 2011-03-10
My bluetooth worked from the get-go. I don't know what ya'll's problem is. It's probably that pesky windows installation that you haven't managed to wipe yet.

---

### Post by garwal on 2011-03-10
Check Joli 1.2 released yesterday, looks good and working great also Suse 11.4 with Gnome 3 shell is way cool as well. Just passing along some new ones I tried today.):P

---

### Post by w1ll1am on 2011-03-15
> **ninjaaron said:**
> My bluetooth worked from the get-go. I don't know what ya'll's problem is. It's probably that pesky windows installation that you haven't managed to wipe yet.

I have not had Windows on my system for more than two months and did a fresh install of ubuntu on my SSD and it still does not work. I tried everything every where nothing works.

---

### Post by ninjaaron on 2011-03-19
I found something great that came out yesterday. Some guy created a patch for the PDF reader that allows the user to toggle drag-scrolling. Woo!!

[http://www.techytalk.info/2011/03/ubuntu-evince-with-panning-hand-for-scrolling-ppa/]("http://www.techytalk.info/2011/03/ubuntu-evince-with-panning-hand-for-scrolling-ppa/")

In Bluetooth news: I am finding that my bluetooth doesn't seem to work with all devices. It doesn't connect to my Archos or my friend's Mac (though it does connect to another friend's mac). I can't connect to either of those devices with either of my Ubuntu machines (and I don't have any other machines).

Maybe it's an Ubuntu + certain devices thing?

---

### Post by Kirboosy on 2011-03-21
I think it has something to do with the kernel. I tried [Sabayon Linux]("http://www.sabayon.org/") which is Gentoo based and I still couldn't get my Bluetooth to work. It had the same exact issue. It could see the adapter but couldn't turn it on.

Fedora, and Suse also had the same issue.

Ninjaaron -- you must be extremely lucky for yours to be working at all :P

---

### Post by w1ll1am on 2011-03-22
The power button on my Duo has stopped working correctly. I have to plug it in to turn it on then it works fine but its very annoying. I contacted dell and they are sending me a new system. I hope that the bluetooth works on this next one. I am not going to even turn windows on so we will see. I will let you guys know.

I also hope they accidentally send me a 3g model. lol

---

### Post by Kirboosy on 2011-03-24
> **w1ll1am said:**
> The power button on my Duo has stopped working correctly. I have to plug it in to turn it on then it works fine but its very annoying. I contacted dell and they are sending me a new system. I hope that the bluetooth works on this next one. I am not going to even turn windows on so we will see. I will let you guys know.

I also hope they accidentally send me a 3g model. lol

Ahh sorry to hear that. You sure its not because you changed the hard drive and over tightened the screws or something crazy? :P

I'm having problems with my battery. I only get like 1.5 hours max off of it. :( Anyone else having this issue?

---

### Post by mcmonee on 2011-03-26
hi everyone!

i am pretty new to threads and forums so i honestly dont know what im doing. first of all i have indeed read most of the instructions for installing ubuntu on a dell inspirion duo. i have not even bought one yet . i was wondering since the instructions were from earlier this year if their was  a new version of ubuntu that works perfectly. i am just seeing if it is possible to get that software on the duo and everything would work better than windows. im not a very software kind of guy. so i really want some help. so is their a new version that works perfectly on the duo if so please post link or something so i can try to install it. btw if i install it does it void warranty? 
thanks sincerly
new forum guy.

---

### Post by Kirboosy on 2011-03-27
> **mcmonee said:**
> hi everyone!

i am pretty new to threads and forums so i honestly dont know what im doing. first of all i have indeed read most of the instructions for installing ubuntu on a dell inspirion duo. i have not even bought one yet . i was wondering since the instructions were from earlier this year if their was  a new version of ubuntu that works perfectly. i am just seeing if it is possible to get that software on the duo and everything would work better than windows. im not a very software kind of guy. so i really want some help. so is their a new version that works perfectly on the duo if so please post link or something so i can try to install it. btw if i install it does it void warranty? 
thanks sincerly
new forum guy.

Welcome to the Forums! :D

Sadly there really isn't anything new that will fix all the issues we have had. April 11 is when the new version of Ubuntu will launch (11.04) and we are all hoping that it fixes some issues. :)

I do not believe it will void your warranty...as long as you don't take the laptop apart physically... I would leave the recovery partition or order some recovery CDs just in case Dell is dumb about it. That way if anything goes wrong you can reinstall Windows and ship it back.

---

### Post by mcmonee on 2011-03-27
Thanks! 

ok well ill just wait till the 11th before making the judgment call on whether or not to buy it.

Thanks again caboose885!

---

### Post by supernovus on 2011-03-29
I am running Ubuntu 11.04 Natty on the Duo, and many things worked "out of the box", including the touch screen (although after the latest updates, it seems to be broken, I hate regressions, but that's the chance you take when running alphas.)

However, one thing that is horrible, terrible, and completely unacceptable is a bug which seems to affect the ath9k driver. The speed is horrendous. I don't mean "it's a bit slow", I mean it's unacceptably slow. An "apt-get update" takes 10 to 15 minutes. Transferring 250 MB of data took over an hour. Stuff like rsync often just freezes up in the middle of a transfer, forcing you to break the connection and restart.

I tried using the latest madwifi from svn, but NetworkManager did not recognize it at all.

At this point, I'm going to try re-installing with 10.10 UNR and see how that works, but I dread these issues returning upon upgrading to 11.04.

Has anyone else experienced the evil doom of ath9k bugs on the duo?

EDIT: 

I'm installing Ubuntu 10.10 Desktop Edition 64bit (I intend to install the ubuntu-netbook meta-package once I'm done) and the download speeds for packages have gone from an average of 5000B/s (with plenty of timeouts) to an average of 300KB/s (with no timeouts.) I'd say there's a fairly significant bug in the ath9k driver for kernel 2.6.38. Hope it gets fixed before 11.04 is released, as there are some nice enhancements in 11.04, particularly in usability on the Duo.

---

### Post by Non.Cents on 2011-03-29
Just to clarify supernovus, do you mean that dual touch worked out of the box, or the single touch the way we have it fixed up here (this thread). I actually dl-ed both 11.04 and 10.10 to do a fresh install today but decided on 10.10 last second. (sounds like it was a good choice)

---

### Post by Kirboosy on 2011-03-29
I've played with the daily Isos on my netbook by liveCD and the touchscreen didn't respond. I figured I would have to edit GRUB like with 10.10


By the way, I'm running 10.10 64 Bit on my Duo and it runs no different than 32 Bit...It just makes some applications (mostly games) hard to find because they are 32 bit only. :(

---

### Post by supernovus on 2011-03-30
> **Non.Cents said:**
> Just to clarify supernovus, do you mean that dual touch worked out of the box, or the single touch the way we have it fixed up here (this thread). I actually dl-ed both 11.04 and 10.10 to do a fresh install today but decided on 10.10 last second. (sounds like it was a good choice)

Single touch worked out of the box with alpha 3, no need for the kernel quirks. However, it seemed to go wonky after updating.

The network speed issues were there from the get-go on 11.04, and upgrading to the latest kernel didn't help.

I have no problems with network speed using 10.10, but I certainly miss the newer Unity Desktop. The "windows" button and quick find was so much nicer in the 11.04 than it is in 10.10. Oh well, hopefully they work out the problems with the network speed issues before 11.04 is released. I'll try upgrading when the official version is out.

This was posted from my Duo :-)

---

### Post by ninjaaron on 2011-03-31
I'm running Natty on my other computer, and I'm not having any trouble with my wifi speed. Maybe it's hardware specific?

---

### Post by Trooper_Max on 2011-03-31
> **supernovus said:**
> Single touch worked out of the box with alpha 3, no need for the kernel quirks. However, it seemed to go wonky after updating.

That was really good news until the going wonky part... >_>

BTW, Multitouch actually works in that Android-x86 build that was released back in January (Sparta). [http://www.android-x86.org/download](http://www.android-x86.org/download)

You can see this by opening up the App Drawer and using the "Dev Tools" app, then select "Pointer Location" and then it will let you test the input... pretty cool. Will be awesome once Ubuntu gets multitouch all figured out.

~Troop

---

### Post by Kirboosy on 2011-03-31
[Sparta Nightly Builds]("http://android-x86.moonman.dk/index.php?folder=c3BhcnRh")

It will be better once they figure out a soft home button. Its quite annoying right now to keep the Duo open to hit the 'Esc' key. 

I'm still crossing my fingers for 11.04 getting multi-touch squared away...

---

### Post by Cgenec on 2011-03-31
Hey all... I have really appreciated all your work with the Dell duo... so much so that I think im going to get one and install Ubuntu on it... for a FYI... Staples is selling the thing for $499 if anyone reading this is kinda on the fence... its a good price.. 

Fine it[ here ](http://www.staples.com/Dell-Inspiron-Duo-10.1-Tablet-PC/product_917467?cmArea=SEARCH")

---

### Post by Trooper_Max on 2011-03-31
> **Caboose885 said:**
> It will be better once they figure out a soft home button. Its quite annoying right now to keep the Duo open to hit the 'Esc' key. 

I'm still crossing my fingers for 11.04 getting multi-touch squared away...

My thoughts exactly... I thought about adding in some softkeys myself, but haven't messed with it (sad as it sounds, the lack of Angry Birds support decreased my interest in running Android on x86 >_>). I think I read that Honeycomb has softkeys or something of the like to make it usable on touch-only devices... too bad the Honeycomb source won't be released any time soon. (Google is holding back on it, possibly until Ice Cream, when one article I've read said the phone and tablet branches will merge back together into one OS for both phones and tablets)

I love Android, it's just never quite where it needs to be...

Here's hoping Ubuntu gets to where it needs to be :-)

EDIT: Perhaps a tip worth passing along, thanks for including Ubuntu tweak in the notes, I found it's ability to create custom Window Titlebar Button layouts (Under Window Manager Settings) very useful. Using it you can add/remove/rearrange the minimize/maximize/close button... I've found I actually prefer to just remove the minimize/maximize buttons (since I can minimize by clicking the icon in the Unity/AWN bar and maximize by double-tapping the titlebar anywhere). This leaves just the close button, **eliminating the possibility of trying to hit one button and accidentally hitting another**. I also added in the Menu on the far left of the title bar (whereas I have close button on the far right). This way I can tap the button on the left to bring up a menu that gives me all the options (minimize/maximize/move/resize/always on top/etc, and I've found that on menus you can touch and drag and it won't actually activate the menu item until you release, **again eliminating misclicks**). I find this setup quite handy and it pretty much eliminates any potential of misclicks.

~Troop

---

### Post by w1ll1am on 2011-03-31
I just installed the beta and thought I would share my experiences so far.

-looks very nice
-grub is a higher resolution and now purple
-boots super quick
-touch did not work had to edit grub
-standard ubuntu (gnome) is now called ubuntu classic
-unity dock auto hides
-bluetooth works!

-no wifi problems 
-still no multi-touch
-can't edit what goes on panel

---

### Post by Cgenec on 2011-03-31
hey all.. I just wanted you all to see what I have found about 11.4.  is the little grey "invalid" word next to not supporting tabs mean anything since the DUO is a netbook AND tab???

[Gesture Support]("https://blueprints.launchpad.net/ubuntu/+spec/appdevs-dx-n-gesture-support-in-applications")

---

### Post by Kirboosy on 2011-04-01
I think when Ubuntu 11.04 launches I will install Kubuntu on my Duo. I didn't like regular Kubuntu all that much until I found the netbook mode. It makes a very pretty and very nice touch interface. It also has Kvkbd preinstalled so its works well out of the box. Its still Ubuntu at the core so I still had to edit Grub but that was expected.

It also has pretty desktop effects out of the box. At first I was hesitant to install because I would lose evolution mail but I simply reinstalled the package and it works really well. 

[Links to some basic screenshots and info]("http://www.kde.org/workspaces/plasmanetbook/")

[ATTACH]187769[/ATTACH] (Screenshot of my setup.)

> hey all.. I just wanted you all to see what I have found about 11.4. is the little grey "invalid" word next to not supporting tabs mean anything since the DUO is a netbook AND tab???

I'm not sure what you mean by this...The Duo is a hybrid computer. Meaning it is a tablet and netbook

---

### Post by pressurepoint on 2011-04-01
> **Caboose885 said:**
> [Sparta Nightly Builds]("http://android-x86.moonman.dk/index.php?folder=c3BhcnRh")

It will be better once they figure out a soft home button. Its quite annoying right now to keep the Duo open to hit the 'Esc' key. 

I'm still crossing my fingers for 11.04 getting multi-touch squared away...

check out button savior.  It puts always on top collapsible set of buttons including back and home.  There is also soft keys but I find button savior works best.  It says it needs root and I have found it to work great right out of the box.
I love the android builds!  Great to play with or just jump on the net real quick.

---

### Post by Non.Cents on 2011-04-01
Hey guys, I just thought id drop in a fyi of my own on related os'. 

Elementary put outtheir first release 'Jupiter' today(4/1/11). It is a clean, and pretty though for the most part scaled down os based on ubuntu. It is indeed all of that (from my experience in the past 45 min.....) but it has a major downside for most of us. scroll bars are TINY!!!!! there are also no arrows on the ends of them. its all cosmetic and can be easily changed tho.

Anyways its a nifty little Ubuntu derivative and all our workarounds/fixes work on it. I like the functionality of docky with our comp though, it really makes things touchable. Implementing the new unity shell (in 11.04), which has HUGE polishing over the one we used with une, would be sexy.

Try it out, if you dont like it..... you can just dl the other programs/ change the looks of it all. maybe 20 min of work to make it the same as ubuntu.

---

### Post by Darrvid on 2011-04-02
So I've tried out 10.10 and 11.04, and have a touchscreen problem. If I change my power settings so the display is turned off when the lid is closed, then close and open the lid, only a portion of the screen accepts any touch input. Specifically the bottom half, and about upper quarter of the screen don't respond to touch. I followed all of the directions at the beginning of this post. Oddly, the same thing happens in windows, although a factory reset has gotten windows working properly again (for the time being anyway). I've not installed or done anything extra other than what the directions in the first post list.
 
Edit: After getting Ubuntu going, I rebooted back into Windows and it's doing the same thing in this os now too.  I turned the power setting so closing the lid 'does nothing' (which actually will just turn the screen off) and the touchinput bugs out like I described above.  Going to suspend/hibernate in ubuntu and windows resolves the problem until I close the lid again.
 
What could be causing this?
 
 
Also, 11.04 doesn't have working multitouch touchpad. I noticed some packages were giving 404 errors in the terminal update, while following the steps to add this.

---

### Post by pressurepoint on 2011-04-03
Hello
I have installed Joli OS to give it a try.  I installed it after Ubuntu and so did not reinstall grub.  I only added the appropriate entry to grub.

Because there is no /etc/default/grub file there is nothing to change and no way to update if I did.  There is a /etc/default/grub.ucf-old which has the text of the grub file, but changing it does nothing.

any ideas?

[EDIT] I just went into the /boot/grub/grub.cfg file (gksudo gedit) of the default ubuntu partition that grub boots from and changed the "linux /boot/vmlinuz" line of the jolicloud part by adding the rest of the line from the 'main ubuntu' part -  ro   quiet splash usbhid.quirks=0x0eef:0x725e:0x40.  apparently this does not get passed to the cfg file for 'other' linux installations.
now to try it for my puppy installation......

---

### Post by ninjaaron on 2011-04-03
The ASUS maintained ppa for Eee PC T101MT (which has the same screen and trackpad as the duo) is partially updated for Natty.

[https://launchpad.net/~plippo/+archive/t101mt]("https://launchpad.net/~plippo/+archive/t101mt")

---

### Post by Kirboosy on 2011-04-04
> **Darrvid said:**
> So I've tried out 10.10 and 11.04, and have a touchscreen problem. If I change my power settings so the display is turned off when the lid is closed, then close and open the lid, only a portion of the screen accepts any touch input. Specifically the bottom half, and about upper quarter of the screen don't respond to touch. I followed all of the directions at the beginning of this post. Oddly, the same thing happens in windows, although a factory reset has gotten windows working properly again (for the time being anyway). I've not installed or done anything extra other than what the directions in the first post list.
 
Edit: After getting Ubuntu going, I rebooted back into Windows and it's doing the same thing in this os now too.  I turned the power setting so closing the lid 'does nothing' (which actually will just turn the screen off) and the touchinput bugs out like I described above.  Going to suspend/hibernate in ubuntu and windows resolves the problem until I close the lid again.
 
What could be causing this?
 
 
Also, 11.04 doesn't have working multitouch touchpad. I noticed some packages were giving 404 errors in the terminal update, while following the steps to add this.

Hmm so strange. I really don't know what could be causing it. You might want to call Dell about it because I don't have any issues with mine. I close my lid and everything still works fine after I reopen it. It might be faulty hardware. :(

---

### Post by Darrvid on 2011-04-04
I spoke with support and I'll be sending it back to have the motherboard and screen replaced. Even though I doubt they'll open it up to troubleshoot, what would be the best way to uninstall ubuntu? When I installed ubu, I chose to have it on a large partition and shrunk the win7 partition down. I don't want to use a win7 recovery because for whatever reason it actually works fine after a factory reset, and I want to make sure I send it back broken just in case they pop it open.
 
I can't figure that its anything other than broken hardware, as all Duo's *should* have the same components I'd think. If it works for everyone else, it should work for me.
 
 
Also, I want to thank everyone involved in this thread. It's awesome that there's a Duo community here, and I think once the kinks get ironed out this will be a sweet system!

---

### Post by Kirboosy on 2011-04-04
You can liveCD (LiveUSB) [Gparted]("http://gparted.sourceforge.net/livecd.php") and Delete the Ubuntu ext4 and SWAP partition. Then enlarge the Windows 7 partition back. 

Now this might cause your system to not boot anymore but if thats the case then I would just run the recovery partition to fix windows. If it does fix the screen issues then I'm sure we can find a way to mess them up again. ;) I highly doubt though that the screen problems would be fixed that easily. It really sounds like a hardware issue.

---

### Post by radalin on 2011-04-05
Hi, I have tried to search in the thread but I was not able to find anything about Opera Mobile (nothing but just a mention of normal Opera as the perfect web browser:).

I have installed Opera Mobile Meego WeTab edition (it had an rpm package and I converted with alien to deb and installed via that way) and it really works smoothly, best touch experience so far. I was even surprised that the touch screen was really really responsive.

But (yes there is always a but :) I can't seem to run flash on it. Normal Opera works fine same as Firefox however I was not able to find a way to run flash on Opera Mobile, did any of you tried and was successful?

thanks

---

### Post by Kirboosy on 2011-04-05
I believe that Opera Mobile does not have flash support. I have noticed on my phone while using it that when I open a youtube video it dumps it to my Blackberry Media player. This tells me that Opera M doesn't have flash or a media player. (Which makes sense in order to keep it compatible across many devices and small)

---

### Post by Non.Cents on 2011-04-05
I am not sure if this is of any use to anyone out there dual booting, but I have noticed that you have to shut down the computer completely from windows7 in order to not have any issues when loading up Ubuntu. This (in my experience) is the case regardless of the dist. If you do a shutdown (instead of a reboot or anything of the like) then it works fine, otherwise, be prepared to have several strange issues, usually with the touch interface.

Its almost like a bios issue, though win7 is rarely affected.....

---

### Post by Kallun on 2011-04-05
> **Non.Cents said:**
> I am not sure if this is of any use to anyone out there dual booting, but I have noticed that you have to shut down the computer completely from windows7 in order to not have any issues when loading up Ubuntu. This (in my experience) is the case regardless of the dist. If you do a shutdown (instead of a reboot or anything of the like) then it works fine, otherwise, be prepared to have several strange issues, usually with the touch interface.

Its almost like a bios issue, though win7 is rarely affected.....


Very weird, throughout the duration of this thread people have mentioned about issues with Windows and rebooting and whatnot. I for one wouldn't know as I got rid of Windows on the Duo once this thread was started and everything works for me. Perhaps something to do with RAM not draining properly?


[EDIT]

I've been chatting with the OS Architect at Jolicloud as he got in contact with me after seeing my youtube video of Joli running on the Duo. Whilst talking to him about the Duo's capabilities and how it run's with Ubuntu based systems, he mentioned he might be able to get multi-touch working. I enquired as to how this might be implemented and he replied today:

'To do the double-touch right, triple-touch middle it involves a kernel
modification to interpret the events. AFAIK there is no way to do this
solely in user-space. My plan is to merge some of the hid-apple code
into the other touchpad screens, like the hid-egalax on the Duo.

Ofcourse, once we have this implemented, all you'll need to do is
download a kernel update. Naturally I'll send a test build your way to
validate, after which we'll make an announcement when its ready. I
feel reasonably confident that we can do this.'

Fortunately he's very keen on getting the new build of Joli working nicely with the Duo, so it's only a matter of time! :D

I've got a really nice setup right now with Elementary running on my Duo, I might do another video in a day or so.

---

### Post by Non.Cents on 2011-04-06
> I've got a really nice setup right now with Elementary running on my Duo, I might do another video in a day or so.

Just fyi, i found out if you do the alt+f2 then run update -d you can actually update Elementary to ubuntu 11.04. Idk how that will work (i just installed 11.04 the old fissioned way), but it was interesting to note that it was a possibility. Elementary is a pretty slick system though isn't it, it would be cool to see it with the new unity :P

---

### Post by pressurepoint on 2011-04-09
Okay I feel like a total doofus admitting this but maybe it will help others.  I was having a problem with the headphones, mentioned earlier but no mentioned fix worked.
In 10.04 sound came from both the headphones and speakers and in 10.10 the headphones would not work.  I have agonized over this for weeks!!!  module assistant never worked, etc.
I was perusing the initial setup instructions and saw the instructions for fixing the microphone, which I was never concerned about, and noticed they looked strangely familiar!  
The fix for the microphone fixed the headphone/speaker issue - which is why so many have probably never noticed it.

So -  caboose - could you add to the microphone line that it is a headphone/speaker fix in case there are others like me?

This makes ubuntu complete for me - well, almost, still no netflix!

---

### Post by Kirboosy on 2011-04-09
> **pressurepoint said:**
> So -  caboose - could you add to the microphone line that it is a headphone/speaker fix in case there are others like me?

Ok thanks for that. Didn't realize that. Changed.

---

### Post by raphaelsaldanha on 2011-04-10
Hi guys,

I'm planning to buy a Duo, and I'm anxious to see it running Ubuntu. Indeed, I will be a new Ubuntu user, with a lot of newbie questions.

About this forum, I'm reading carefully, giving a "Yes!" when someone discovers how to fix something, and I'm avid to get my device and start to help, if I can.

But I would like to ask you guys a brief: currently, what is working well (natively or with a fix) with Ubuntu and Dell Duo?

- Internal speaker
- Headphone jack
- Microphone
- Camera
- Screen rotation, mouse orientation and accelerometer
- Multi-touch
- Dock: speakers and his ports

Thanks on advance by the help!

---

### Post by semidark on 2011-04-10
Hi,

Could it be that the Bluetooth Problem has something to do with this generic Dell Bluetooth bug?

[http://bugs.launchpad.net/ubuntu/+source/linux/+bug/37288?comments=all](http://bugs.launchpad.net/ubuntu/+source/linux/+bug/37288?comments=all)

It seems that dell has updated their BT-Firmware and now the Linux Kernel won't recognise it any more. The suggested fix is to install XP and downgrade the firmware with a Dell Firmware-Flash Software. I haven't  tried it yet because i only got Win7 installed as dualboot.

But maybe someone more Senior on the Linux Kernel could pick up from here. Or we could all tell the Launchpad that this Bug affects us Duo Users.

@Caboose885: Could you please update the "What works section" on the first page. Obviously BT is not functional ;)

Greetz Semidark

---

### Post by w1ll1am on 2011-04-10
> **semidark said:**
> Hi,

Could it be that the Bluetooth Problem has something to do with this generic Dell Bluetooth bug?

[http://bugs.launchpad.net/ubuntu/+source/linux/+bug/37288?comments=all](http://bugs.launchpad.net/ubuntu/+source/linux/+bug/37288?comments=all)

It seems that dell has updated their BT-Firmware and now the Linux Kernel won't recognise it any more. The suggested fix is to install XP and downgrade the firmware with a Dell Firmware-Flash Software. I haven't  tried it yet because i only got Win7 installed as dualboot.

But maybe someone more Senior on the Linux Kernel could pick up from here. Or we could all tell the Launchpad that this Bug affects us Duo Users.

@Caboose885: Could you please update the "What works section" on the first page. Obviously BT is not functional ;)

Greetz Semidark

bluetooth is working in the beta of 11.04 so just be patient.

---

### Post by w1ll1am on 2011-04-10
> **raphaelsaldanha said:**
> Hi guys,

I'm planning to buy a Duo, and I'm anxious to see it running Ubuntu. Indeed, I will be a new Ubuntu user, with a lot of newbie questions.

About this forum, I'm reading carefully, giving a "Yes!" when someone discovers how to fix something, and I'm avid to get my device and start to help, if I can.

But I would like to ask you guys a brief: currently, what is working well (natively or with a fix) with Ubuntu and Dell Duo?

- Internal speaker
- Headphone jack
- Microphone
- Camera
- Screen rotation, mouse orientation and accelerometer
- Multi-touch
- Dock: speakers and his ports

Thanks on advance by the help!

speakers work
headphones work
microphone works
camera works
screen rotation can be done manually and mouse orientation is changed along with that
dock speakers work and all the port besides the ethernet witch kinda works

multi-touch doesn't work
accelerometer doesn't work

---

### Post by raphaelsaldanha on 2011-04-10
Thanks!

---

### Post by ninjaaron on 2011-04-13
> **Kallun said:**
> 

I've been chatting with the OS Architect at Jolicloud as he got in contact with me after seeing my youtube video of Joli running on the Duo. Whilst talking to him about the Duo's capabilities and how it run's with Ubuntu based systems, he mentioned he might be able to get multi-touch working. I enquired as to how this might be implemented and he replied today:

'To do the double-touch right, triple-touch middle it involves a kernel
modification to interpret the events. AFAIK there is no way to do this
solely in user-space. My plan is to merge some of the hid-apple code
into the other touchpad screens, like the hid-egalax on the Duo.

Ofcourse, once we have this implemented, all you'll need to do is
download a kernel update. Naturally I'll send a test build your way to
validate, after which we'll make an announcement when its ready. I
feel reasonably confident that we can do this.'

Fortunately he's very keen on getting the new build of Joli working nicely with the Duo, so it's only a matter of time! :D

I've got a really nice setup right now with Elementary running on my Duo, I might do another video in a day or so.

This pleases me greatly.

[edit]
and by that I mean "This is awesome if he sends the code upstream, since I have no intention of using Jolicloud."

---

### Post by kahnk11 on 2011-04-13
Hey. Loving this little Duo and very anxious to get UBE up and running on it. I am experiencing a strange problem though. After a minute of working, my mouse buttons don't work anymore. The mouse moves around with fingers or pad, but I cannot click on anything. I think when it first happened I saw an error box saying something about my mouse being hijacked?? I have to navigate with the keyboard until I reboot.

---

### Post by kahnk11 on 2011-04-13
Ok. I must have done something wrong in the setup. Now the mouse won't reposition itself to where my finger is and the icons on my side bar dissapear and jump around when I try and select them. I may start from scratch here.

---

### Post by rickpref on 2011-04-14
Has anyone tried installing 11.04 Beta 1 yet?  

I just got the Duo today and find it pretty decent as it is and I haven't installed my SSD drive yet.

My download speed here is really slow so I wanted to hear about 11.04 before deciding what to download.

---

### Post by w1ll1am on 2011-04-14
> **rickpref said:**
> Has anyone tried installing 11.04 Beta 1 yet?  

I just got the Duo today and find it pretty decent as it is and I haven't installed my SSD drive yet.

My download speed here is really slow so I wanted to hear about 11.04 before deciding what to download.

The beta looks pretty nice. there is still no multi-touch and you have to use the same steps in the beginning of this thread to get single touch to work. If i were you I would just wait till the full release is out and install it. It's almost here!

---

### Post by Kirboosy on 2011-04-14
> **kahnk11 said:**
> Hey. Loving this little Duo and very anxious to get UBE up and running on it. I am experiencing a strange problem though. After a minute of working, my mouse buttons don't work anymore. The mouse moves around with fingers or pad, but I cannot click on anything. I think when it first happened I saw an error box saying something about my mouse being hijacked?? I have to navigate with the keyboard until I reboot.



Sounds like you didn't get grub updated or something like that...I used to have that issue before the grub fix was found...If you forgot to run ```
sudo update-grub
```then that might be why it hasn't fixed anything.

---

### Post by rickpref on 2011-04-14
> **w1ll1am said:**
> The beta looks pretty nice. there is still no multi-touch and you have to use the same steps in the beginning of this thread to get single touch to work. If i were you I would just wait till the full release is out and install it. It's almost here!

So I can run the same steps as in this guide with 11.04?  Cool.  Beta 2 just showed up on Distrowatch.  Is multi-touch supposed to be working in the final release?  They advertise as it should have worked already with Beta 1.

---

### Post by joey-elijah on 2011-04-15
Having just got a Dell Duo I was quite miffed to find that touch - let alone multi-touch - doesn't work out of the box. 

Steps at the beginning do work in 11.04, however every now and again the mouse will register touch an inch away from my finger. Rebooting solves this.

Here's hoping Multi-touch support appears soon :)

---

### Post by Kirboosy on 2011-04-15
> **rickpref said:**
> So I can run the same steps as in this guide with 11.04?  Cool.  Beta 2 just showed up on Distrowatch.  Is multi-touch supposed to be working in the final release?  They advertise as it should have worked already with Beta 1.

Multi-touch is hardware specific. They say it has multi-touch but 10.10 has multi-touch support as well. (See [this video]("http://downloadsquad.switched.com/2010/10/15/video-canonical-shows-off-ubuntu-10-10-multitouch-kung-fu/")) Whats interesting in that video is they use a Dell...

I am downloading Beta2 now and I will post an update soon.

---

### Post by Kirboosy on 2011-04-15
Ok so I played with a LiveCD of Ubuntu 11.04 Beta 2 and out of the box it doesn't seem like the touchscreen responds at all. I think if I installed it and did the GRUB changes it would work like 10.10. 

Other than that I don't see anything worth mentioning that you already don't know. Its really fast. lol

---

### Post by w1ll1am on 2011-04-16
Today I was looking around in /var/log/kern.log and saw eGalax Inc. USB TouchController.

I do not remember if we determined who made the screen for the duo earlier in the thread but if not now we know. Maybe it will help.

---

### Post by salmander on 2011-04-17
> **Caboose885 said:**
> Ok so I played with a LiveCD of Ubuntu 11.04 Beta 2 and out of the box it doesn't seem like the touchscreen responds at all. I think if I installed it and did the GRUB changes it would work like 10.10. 

Other than that I don't see anything worth mentioning that you already don't know. Its really fast. lol
Hello I am new to linux and new to Ubuntu. I just installed ubuntu 10.10 on my new Dell Duo after watching a video on youtube. and followed the guide mentioned here to set it up for dell....but its not fast as i was expecting....infact sometimes i experience lag of 4-5 seconds between switching apps and opening application launcher.
Anyway thanks for the guide....and u saying 11.04 beta 2 is fast?? really?? is it faster than 10.10?

and how do i update to beta 2? coz i dont have external cd-rom drive. isnt there usb flash drive method for it??

---

### Post by erbey on 2011-04-17
> **salmander said:**
> Hello I am new to linux and new to Ubuntu. I just installed ubuntu 10.10 on my new Dell Duo after watching a video on youtube. and followed the guide mentioned here to set it up for dell....but its not fast as i was expecting....infact sometimes i experience lag of 4-5 seconds between switching apps and opening application launcher.
Anyway thanks for the guide....and u saying 11.04 beta 2 is fast?? really?? is it faster than 10.10?

and how do i update to beta 2? coz i dont have external cd-rom drive. isnt there usb flash drive method for it??

i haven't tried 11.04 beta so i can't comment on speed but if you want to upgrade type 

code:
sudo update-manager -d

into a terminal (under accessories) and it should ask you to confirm to upgrade to 11.04 but its still in beta testing at the moment so it may want to wait until its released in 11 days especially if your new to linux.

---

### Post by Kirboosy on 2011-04-18
> **salmander said:**
> Hello I am new to linux and new to Ubuntu. I just installed ubuntu 10.10 on my new Dell Duo after watching a video on youtube. and followed the guide mentioned here to set it up for dell....but its not fast as i was expecting....infact sometimes i experience lag of 4-5 seconds between switching apps and opening application launcher.
Anyway thanks for the guide....and u saying 11.04 beta 2 is fast?? really?? is it faster than 10.10?

and how do i update to beta 2? coz i dont have external cd-rom drive. isnt there usb flash drive method for it??

Honestly since you are new to Linux I would not upgrade to Beta 2 just yet. (Yes you can install the Beta2 using a flash drive) There are alot bugs that still need to be fixed in the next few days. Did you install Ubuntu Netbook edition on your Duo?

I abandoned Netbook Edition because the Unity interface that came with it was very junky. (The new Unity coming in 11.04 is improved greatly) I bet if you switch to "Classic Gnome" you will see a performance increase.
> 1. Click the User Switcher in the top right hand corner of the screen and then press Log out to log out of Ubuntu

2. At the log-in screen which appears, press Options &#8594; Select Session...

3. Choose the "Ubuntu Desktop" option and press Change Session

4. Enter your username and password as normal. Classic Gnome should then start.You will notice things are different but I bet you will see a speed increase. You can also use Compiz for desktop effects (which is really cool to impress your friends with ;) )

I actually run Kubuntu on my Duo now with the netbook interface since I found it very pretty and touchable. We will see if Gnome3 or Unity will bring me back. I like Gnome better because it takes less resources but on my netbook I need a touchable interface. On my desktop I still run Gnome 2.3


> **w1ll1am said:**
> Today I was looking around in /var/log/kern.log and saw eGalax Inc. USB TouchController.

I do not remember if we determined who made the screen for the duo earlier in the thread but if not now we know. Maybe it will help.

Yes we determined this earlier but we never really did anything with it. I even found drivers which I never compiled. Maybe since I have more free time I will try to get those drivers working. :)

~Caboose

---

### Post by joey-elijah on 2011-04-19
> **Caboose885 said:**
> Yes we determined this earlier but we never really did anything with it. I even found drivers which I never compiled. Maybe since I have more free time I will try to get those drivers working. :)

~Caboose

Which drivers were these out of interest? I tried the ones @ [http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm](http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm) but they didn't do anything for multi-touch (at least for me).

---

### Post by Ba5ik57 on 2011-04-19
Hey all just got my duo YEAH! I have been watching this thread for a few weeks thanks for the sharing. For Google Chrome I'm using extension chromeTouch for scrolling just like grab and drag. Also for a on broad screen keyboard I'm using Florence Virtual&#65279; Keyboard. I love ubuntu 10.10 Desktop but the interface is a bit small making it hard to touch the right button. Ubuntu multi touch please.... Thanks Again

---

### Post by Kirboosy on 2011-04-19
> **joey-elijah said:**
> Which drivers were these out of interest? I tried the ones @ [http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm](http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm) but they didn't do anything for multi-touch (at least for me).

Yep those would be the ones...Did you undo the GRUB changes after you installed the driver?

---

### Post by w1ll1am on 2011-04-19
Check out this [thread]("http://ubuntuforums.org/showthread.php?t=1658480") I was able to get my accelerometer to work and got a program to auto run if I flipped my screen! This guy is a genius.

I was only able to get the screen flip thing to work once and I am not sure why it has stopped working if anyone else gets it to work let me know how. 

Also the accelerometer works but then the mouse well touch screen does not respond correctly like when rotating the screen manually.

---

### Post by joey-elijah on 2011-04-20
> **Caboose885 said:**
> Yep those would be the ones...Did you undo the GRUB changes after you installed the driver?

I'm pretty sure I did, yeah. But I'll give it another go just to make sure.

---

### Post by newttyy on 2011-04-22
Hi guys,

So I have followed every single step in the first post of this thread and I am still having a problem with the touch screen.

Every time I try to touch the screen, the mouse jumps to the top-left corner and refuses to move from there. I'm stuck using the track pad only.

Help! :(

---

### Post by repunante on 2011-04-23
I installed Natty in the Duo and the touch screen works after editing the grub.
The only problem I see (so far) is that I cannot change the screen resolution to something like 960x540 or 1040x585, not even using xrandr in terminal; 1360x768 for the tablet mode make the buttons very small.

---

### Post by Ba5ik57 on 2011-04-23
> **newttyy said:**
> Hi guys,

So I have followed every single step in the first post of this thread and I am still having a problem with the touch screen.

Every time I try to touch the screen, the mouse jumps to the top-left corner and refuses to move from there. I'm stuck using the track pad only.

Help! :(

It took me a few tries but it works! Try rebooting after editing and updating the grub..  [http://samiux.blogspot.com/2010/11/howto-ubuntu-1010-on-gigabyte-touchnote.html](http://samiux.blogspot.com/2010/11/howto-ubuntu-1010-on-gigabyte-touchnote.html)  Hope thats helps

---

### Post by mac37m on 2011-04-26
RE: using ONSCREEN Keyboard guide need some clarification - I'm a newbie.

I got confused right around here "**[COLOR=SeaGreen]open another folder up[/COLOR]** and copy the .xml file inside and put it into the  folder you just created. once it is in the new folder open it with  gedit remove everything and paste in"

instead of opening a folder I open up a new file and paste in the quoted .xml file shown in the box and run gedit in another terminal 

and then,,, totally got lost in this section 
"navigate to home/.gconf/desktop/unity/launcher/favorites find the app-kvkbd.desktop file and change the icon to the kvkbd icon. 

the icon is located in /usr/share/icons/Humanity/apps/48 and it is called preferences-desktop-keyboard.svg

3) Run

 	Code:
 	 gconf-editor 
go to desktop/unity/launcher and click on the favorites folder (do  not expand) double click on the favorites_list and add  app-kvkbd.desktop.

Reboot or logout and back in and the icon should be there if you have any problems let me know."


Please help and I'm trying to get the Onscreen keyboard to come up in my launcher page.

Thanks!

---

### Post by Kirboosy on 2011-04-27
> **joey-elijah said:**
> I'm pretty sure I did, yeah. But I'll give it another go just to make sure.

Did it at least allow you to remove the Grub changes and your screen still function properly?

---

### Post by Kirboosy on 2011-04-28
Alright guys I have successfully installed 11.04 on my Duo. Already I have noticed that two finger scrolling works out of the box. I'm still seeing if there are any major differences. Bluetooth is still not working on my Duo...Same exact thing as before. Bluetooth gets hung at turning on...

Now I'm wondering. Should I update the guide for just 11.04 or should I just add on a new section for 11.04 and move the 10.10 section to the bottom?

---

### Post by macshield on 2011-04-28
> **Caboose885 said:**
> Alright guys I have successfully installed 11.04 on my Duo. Already I have noticed that two finger scrolling works out of the box. I'm still seeing if there are any major differences. Bluetooth is still not working on my Duo...Same exact thing as before. Bluetooth gets hung at turning on...

Now I'm wondering. Should I update the guide for just 11.04 or should I just add on a new section for 11.04 and move the 10.10 section to the bottom?

Does this mean that multi touch screen is working?

---

### Post by Darrvid on 2011-04-28
> **Caboose885 said:**
> Alright guys I have successfully installed 11.04 on my Duo. Already I have noticed that two finger scrolling works out of the box. I'm still seeing if there are any major differences. Bluetooth is still not working on my Duo...Same exact thing as before. Bluetooth gets hung at turning on...

Now I'm wondering. Should I update the guide for just 11.04 or should I just add on a new section for 11.04 and move the 10.10 section to the bottom?

As far as I can tell, this is the best resource for Duo users wanting ubuntu on the system... so I don't see a reason to remove info- which is to say if someone wanted 10.10, your post is the only place I've seen online that would help them get it running.

---

### Post by Kirboosy on 2011-04-28
> **macshield said:**
> Does this mean that multi touch screen is working?

No from what I can tell the multi touch is still not working. I'm monkeying around with it to see if I can get it to work, but so far no. The only thing that works differently out of the box is two finger scrolling. (just change the mouse settings). The touchscreen though still needs GRUB editing.

> **Darrvid said:**
> As far as I can tell, this is the best resource for Duo users wanting ubuntu on the system... so I don't see a reason to remove info- which is to say if someone wanted 10.10, your post is the only place I've seen online that would help them get it running.

Yeah I think I will just add on to what I got and leave all the old info.

---

### Post by w1ll1am on 2011-04-28
> **Caboose885 said:**
> Bluetooth is still not working on my Duo...Same exact thing as before. Bluetooth gets hung at turning on...

dang that is strange... I had Bluetooth working in in the beta? I am installing 11.04 now so I will let you know if mine works.

---

### Post by garethledger on 2011-04-28
Just install 11.04 and loving it...

How do I get the Virtual Keyboard working??

---

### Post by Aaddron on 2011-04-28
Coming from beta 2 it wont let me enable two finger scrolling(option is grayed out), doing a fresh install wouldn't be a big deal but any ideas?

> **Caboose885 said:**
> Bluetooth is still not working on my Duo...

Same as w1ll1am in the beta Bluetooth was working and now it's not.

---

### Post by pressurepoint on 2011-04-28
Caboose mentioned earlier something about decreased battery life and I came across this article which I thought may be of interest:

[http://www.phoronix.com/scan.php?page=article&item=linux_kernel_regress2&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_kernel_regress2&num=1)

Essentially it talks about a "bad power regression in the mainline Linux kernel" that is causing significant decreases in battery life.  The affected kernels seem to be 38 and 39, so this would be primarily of concern to 11.04 users.  I am on 10.10 with 35.

I admit I am speaking above my paygrade but I found the article of interest and thought I would share!

Correction: Later in the article it is stated: "However, with the Linux 2.6.35 kernel, the power consumption goes up noticeably. That first power regression remains in Linux 2.6.36 and 2.6.37, and now with 2.6.38 the power consumption goes up even more. "  So 10.10 users are affected as well, which might explain noticeable drops in battery times.

---

### Post by Kirboosy on 2011-04-29
Ok. Apparently the touchscreen-helper package has been removed from the repositories. Meaning when you rotate the screen using the script the touchscreen doesn't work properly. I'm trying to find a solution...

---

### Post by ninjaaron on 2011-04-30
> **Caboose885 said:**
> Ok. Apparently the touchscreen-helper package has been removed from the repositories. Meaning when you rotate the screen using the script the touchscreen doesn't work properly. I'm trying to find a solution...

It isn't removed. ASUS just hasn't compiled it for the natty repo.

If you go the the launchpad site, the touchscreen-helper package for Maverick can be downloaded, but the performance is very... eh... "weird" on Natty (probably because they rebuilt the x-input libraries in this development cycle).

I may try compiling it from source to see if I can get it to work any better.

---

### Post by Kirboosy on 2011-04-30
I would likes some verification of my bug I have found in 11.04.

When running Unity (it doesn't happen in Classic Gnome) if I unplug or plug in my Duo, Ubuntu crashes. The only way to fix it is to hard kill the computer and restart it.

Is this just me or do other people have this issue?

---

### Post by w1ll1am on 2011-05-01
> **Caboose885 said:**
> I would likes some verification of my bug I have found in 11.04.

When running Unity (it doesn't happen in Classic Gnome) if I unplug or plug in my Duo, Ubuntu crashes. The only way to fix it is to hard kill the computer and restart it.

Is this just me or do other people have this issue?

Yupp same problem here... well kinda it did it the first time then I restarted and I tried again and now it will not even recognize that it is plugged in it says discharging and it even does the same thing on the dock its really weird. So this is a definite verification of a bug.

Well now I am not sure. It has only happened once I have shutdown, restarted, held in the power and did all of this with and without the power cable in as I turn it on and it has not happened again. Does this happen to you every time Caboose885?

---

### Post by ninjaaron on 2011-05-01
I don't have this exact problem, but every now and then when I unplug, I get kicked into a console screen, a bunch of messages go by very quickly, and then my desktop comes back. I'm sure it's related, but I've been running natty exclusively on my duo since beta 1, so maybe there are some spare parts lying around in mine that keep it from completely going out.

---

### Post by DFarmerTX on 2011-05-01
I'm downloading 11.04 64 bit now, I'm going to start fresh with the Duo.  I'll let you know what I find...

---

### Post by DFarmerTX on 2011-05-01
> **DFarmerTX said:**
> I'm downloading 11.04 64 bit now, I'm going to start fresh with the Duo.  I'll let you know what I find...

Just a quick review of the issues with 64 bit 11.04 (new install from USB)...

1.  I had to apply the grub usb io quirk to get the touchscreen to work.
2.  I added the entry to the modprobe for sound.
3.  The onscreen keyboard doesn't work with the unity interface (unity takes over and you can't use the keyboard).
4.  Docking or un-docking crashes the system.
5.  I accidentally turned off the wireless radio with F2 and I couldn't turn it back on.  I had to boot into Windows to get it back.  The syslog complained about not being able to map a keyboard key when trying F2 after that.

-DF

---

### Post by salmander on 2011-05-01
> **DFarmerTX said:**
> Just a quick review of the issues with 64 bit 11.04 (new install from USB)...

1.  I had to apply the grub usb io quirk to get the touchscreen to work.
2.  I added the entry to the modprobe for sound.
3.  The onscreen keyboard doesn't work with the unity interface (unity takes over and you can't use the keyboard).
4.  Docking or un-docking crashes the system.
5.  I accidentally turned off the wireless radio with F2 and I couldn't turn it back on.  I had to boot into Windows to get it back.  The syslog complained about not being able to map a keyboard key when trying F2 after that.

-DF
i m updating it now to 11.04 via software update....lets see how it goes...review doesnt sounds that great....will update you guys of my findings...

---

### Post by salmander on 2011-05-01
> **salmander said:**
> i m updating it now to 11.04 via software update....lets see how it goes...review doesnt sounds that great....will update you guys of my findings...
3 minutes left for downloading the updates.....whoop...
will see the effect soon...


edit: ok the downloading phase is finished...but now its on installing the upgrades phase...and its saying 3 hours 22 mins remaining :| i mean if u fresh install it...it takes 10 mins...how come this long for upgrading it?? confused...but i guess i just have to wait for it...hope it worth the wait.

---

### Post by salmander on 2011-05-01
> **salmander said:**
> 3 minutes left for downloading the updates.....whoop...
will see the effect soon...


edit: ok the downloading phase is finished...but now its on installing the upgrades phase...and its saying 3 hours 22 mins remaining :| i mean if u fresh install it...it takes 10 mins...how come this long for upgrading it?? confused...but i guess i just have to wait for it...hope it worth the wait.
Ok it was taking extremly long....so I thought that there is something wrong..the shutdown button was red and when I clicked on it, in the dropdown menu it said restart to finish installing updates....I thought maybe while running system and installing update is the reason of it taking soo long....so. clicked on restart...now its stuck at the screen where it says the disc drive / is not yet ready or not present. Continue to wait or press s to skip.....
Ahhh man....what do I do now any helpp???

---

### Post by DFarmerTX on 2011-05-01
> **salmander said:**
> Ok it was taking extremly long....so I thought that there is something wrong..the shutdown button was red and when I clicked on it, in the dropdown menu it said restart to finish installing updates....I thought maybe while running system and installing update is the reason of it taking soo long....so. clicked on restart...now its stuck at the screen where it says the disc drive / is not yet ready or not present. Continue to wait or press s to skip.....
Ahhh man....what do I do now any helpp???
You might be able to start a new install and choose "upgrade" when (if) it finds your old installation.  This could keep some of your settings.

But, when that happened to me, I had to delete the ext4 the partition and start over.

---

### Post by w1ll1am on 2011-05-01
> **Kallun said:**
> Very weird, throughout the duration of this thread people have mentioned about issues with Windows and rebooting and whatnot. I for one wouldn't know as I got rid of Windows on the Duo once this thread was started and everything works for me. Perhaps something to do with RAM not draining properly?


[EDIT]

I've been chatting with the OS Architect at Jolicloud as he got in contact with me after seeing my youtube video of Joli running on the Duo. Whilst talking to him about the Duo's capabilities and how it run's with Ubuntu based systems, he mentioned he might be able to get multi-touch working. I enquired as to how this might be implemented and he replied today:

'To do the double-touch right, triple-touch middle it involves a kernel
modification to interpret the events. AFAIK there is no way to do this
solely in user-space. My plan is to merge some of the hid-apple code
into the other touchpad screens, like the hid-egalax on the Duo.

Ofcourse, once we have this implemented, all you'll need to do is
download a kernel update. Naturally I'll send a test build your way to
validate, after which we'll make an announcement when its ready. I
feel reasonably confident that we can do this.'

Fortunately he's very keen on getting the new build of Joli working nicely with the Duo, so it's only a matter of time! :D

I've got a really nice setup right now with Elementary running on my Duo, I might do another video in a day or so.

any update on this? Has he gotten back to you since you last spoke?

---

### Post by salmander on 2011-05-02
> **DFarmerTX said:**
> You might be able to start a new install and choose "upgrade" when (if) it finds your old installation.  This could keep some of your settings.

But, when that happened to me, I had to delete the ext4 the partition and start over.
And how do I do that???
what do I do man??? Please help me.

---

### Post by robofighter on 2011-05-02
Hello, does anyone know a script or program that switch the output from the laptop speakers to the docking station and back when the computers gets docked and undocked.

---

### Post by erlguta on 2011-05-02
For all of you that have this Dell inspiron duo I would be very grateful if someone answers these questions:
- Does suspend/hibernate works?
- Does the microphone and webcam works?
- How is the battery life?
- How is the noise level?

Thank you very much in advance.

---

### Post by radalin on 2011-05-02
> **erlguta said:**
> For all of you that have this Dell inspiron duo I would be very grateful if someone answers these questions:
- Does suspend/hibernate works?
- Does the microphone and webcam works?
- How is the battery life?
- How is the noise level?

Thank you very much in advance.

suspend and hibernate are not working that good, cam and mic works perfectly. Battery is fine too like 3+ hours. There is not much noise in mine even during the high cpu requiring tasks.

---

### Post by erlguta on 2011-05-02
Thank you Radalin!
:D

---

### Post by salmander on 2011-05-02
sudo apt-get install eeepc-touchpad-twofingers
the above statement is not working anymore...it was working on 10.10 but not on 11.04 now....its giving an error that cant get package or something like that....anybody else getting this??

---

### Post by Kirboosy on 2011-05-02
> **salmander said:**
> sudo apt-get install eeepc-touchpad-twofingers
the above statement is not working anymore...it was working on 10.10 but not on 11.04 now....its giving an error that cant get package or something like that....anybody else getting this??

You actually do not need those packages anymore for two finger scrolling in 11.04. Just go change the Mouse -->Touchpad settings to Two Finger Scrolling

---

### Post by Kirboosy on 2011-05-03
> **robofighter said:**
> Hello, does anyone know a script or program that switch the output from the laptop speakers to the docking station and back when the computers gets docked and undocked.

I did not get a dock with mine (I wish I would have...) but if you go to the sound settings while the Duo is docked. Does any other device show up under the 'output' tab besides "Internal Audio Analog Stereo"?

---

### Post by rg4w on 2011-05-03
The Dell Duo is a sexy machine.  Ubuntu is a sexy OS.

They would seem made for each other, yet 37 pages later no one has a way to do so smoothly.

Sad.

All that time/money spent on Unity, but it can't be used on one of the nicest machines out there until there's an equal investment in driver support....  :(

---

### Post by salmander on 2011-05-03
> **Caboose885 said:**
> You actually do not need those packages anymore for two finger scrolling in 11.04. Just go change the Mouse -->Touchpad settings to Two Finger Scrolling
its greyed out....i mean i cant change it...its default unchecked... :(
thanks for the reply though....
overall its working fine...does anyone know any apps or packages that i can use that would be cool for duo?

---

### Post by Kirboosy on 2011-05-03
> **salmander said:**
> its greyed out....i mean i cant change it...its default unchecked... :(
thanks for the reply though....
overall its working fine...does anyone know any apps or packages that i can use that would be cool for duo?

Are you running 11.04? (also did you upgrade or clean install?)

Cool programs...hmmm...not sure on that one. If we get multi-touch working I can think of a few ;)

---

### Post by radalin on 2011-05-04
> **salmander said:**
> its greyed out....i mean i cant change it...its default unchecked... :(
thanks for the reply though....
overall its working fine...does anyone know any apps or packages that i can use that would be cool for duo?

Opera Mobile definitely :) If you can run the flash too it's all the better :)

---

### Post by salmander on 2011-05-04
> **Caboose885 said:**
> Are you running 11.04? (also did you upgrade or clean install?)

Cool programs...hmmm...not sure on that one. If we get multi-touch working I can think of a few ;)
i did the clean install....
yes i am running 11.04 with unity interface.

---

### Post by joey-elijah on 2011-05-04
> **radalin said:**
> Opera Mobile definitely :)

This. I reviewed Opera Mobile on OMG! a while back (and on a Dell Duo, too) and it works *so* well. It would work even better if damn multi-touch was working.

I have a 32bit .deb of Opera Mobile 11 (the official RPM alien'd to a .deb) in my UbuntuOne if anyone needs it.

[http://ubuntuone.com/p/nhM/](http://ubuntuone.com/p/nhM/)

---

### Post by radalin on 2011-05-04
> **joey-elijah said:**
> This. I reviewed Opera Mobile on OMG! a while back (and on a Dell Duo, too) and it works *so* well. It would work even better if damn multi-touch was working.

I have a 32bit .deb of Opera Mobile 11 (the official RPM alien'd to a .deb) in my UbuntuOne if anyone needs it.

[http://ubuntuone.com/p/nhM/](http://ubuntuone.com/p/nhM/)

where you able to run flash on it btw? because when I set the Opera's plugin folder as the Opera Mobile's plugin folder, but it doesn't seem to work.

---

### Post by Kirboosy on 2011-05-04
> **salmander said:**
> i did the clean install....
yes i am running 11.04 with unity interface.

Strange. Because I also did a clean install of 11.04 and I could change it to two finger scrolling no problem (and with no special drivers/repositories) I wonder if Dell has different firmware versions on their touchpads or something crazy. (They apparently have different wireless cards. Thats why some people report Bluetooth working and others can't get it working.)

---

### Post by w1ll1am on 2011-05-04
> **robofighter said:**
> Hello, does anyone know a script or program that switch the output from the laptop speakers to the docking station and back when the computers gets docked and undocked.

I believe that if you hook the duo up to the dock and then go to sound preferences ( right click on the sound icon in the right conner )  and click output tab you can change it to the speakers. Then when even you switch between the duo and the docked duo it should automatically change what speakers its using.

I just tested it with my dock and it works.

---

### Post by robofighter on 2011-05-04
The speakers switch fine. But the problem is that you have to manually switch on sound preferences if you want the buildin volume control buttons to work.

---

### Post by mokolo on 2011-05-04
> **robofighter said:**
> The speakers switch fine. But the problem is that you have to manually switch on sound preferences if you want the buildin volume control buttons to work.

same thing for me.

---

### Post by salmander on 2011-05-04
> **Caboose885 said:**
> Strange. Because I also did a clean install of 11.04 and I could change it to two finger scrolling no problem (and with no special drivers/repositories) I wonder if Dell has different firmware versions on their touchpads or something crazy. (They apparently have different wireless cards. Thats why some people report Bluetooth working and others can't get it working.)
hmmm interesting.....so does that mean i wont be able to use two fingers on touchpad or on screen.....btw which virtual keyboard you using??

---

### Post by Kirboosy on 2011-05-04
> **salmander said:**
> hmmm interesting.....so does that mean i wont be able to use two fingers on touchpad or on screen.....btw which virtual keyboard you using??

Did the two finger scrolling work in 10.10 for you?

I'm using the Kvkbd keyboard but I know most people on this thread use [Florence]("http://florence.sourceforge.net/english.html")

---

### Post by salmander on 2011-05-04
> **Caboose885 said:**
> Did the two finger scrolling work in 10.10 for you?

I'm using the Kvkbd keyboard but I know most people on this thread use [Florence]("http://florence.sourceforge.net/english.html")
ya it did work for me on 10.10.... had to follow your guide for that...
ummm i was using florence on 10.10... is kckbd any better?? btw it will work with unity right? because some programs are not coming in my system tray anymore in unity..like dropbox and other stuff...

---

### Post by Kirboosy on 2011-05-04
Actually florence is probably the better vkeyboard but KDE has kvkbd built into it and it works well enough for me.

I have no problems with items in my sys tray. (I use dropbox and I have the little dropbox icon in my tray) Are you sure Dropbox is running?

---

### Post by Cammaaron on 2011-05-04
I just did a clean install of Ubuntu 11.04 on my Dell Duo via Wubi

Rotating the screen makes the touchscreen works incorrectly. 
When I rotate my screen to the left, if I move my finger up the mouse pointer goes left.

---

### Post by repunante on 2011-05-05
I like the idea of this guy:
[http://www.ideastorm.com/ideaView?id=087700000008WiBAAU](http://www.ideastorm.com/ideaView?id=087700000008WiBAAU)

It would be great to switch between Ubuntu (netbook mode) and something like Android (tablet mode) without rebooting.

Something maybe interesting:
[http://www.alwaysinnovating.com/products/aios.htm](http://www.alwaysinnovating.com/products/aios.htm)

---

### Post by Kirboosy on 2011-05-05
> **Cammaaron said:**
> I just did a clean install of Ubuntu 11.04 on my Dell Duo via Wubi

Rotating the screen makes the touchscreen works incorrectly. 
When I rotate my screen to the left, if I move my finger up the mouse pointer goes left.

That is because the touchscreen-helper package never got up converted for 11.04. Without this package the touchscreen won't work right when rotated. (I don't have enough time to get the package working on 11.04 :( )

---

### Post by Cammaaron on 2011-05-05
Hey, I downloaded the package directly from his lauchpad site instead of the responsitory. Rebooted the computer. And now the touch screen is working when rotated.

However I would recommended using the Unity 2D instead of the default 3D. As it seems to mess up the background with you rotate on 3D

---

### Post by Non.Cents on 2011-05-05
> **repunante said:**
> I like the idea of this guy:
[http://www.ideastorm.com/ideaView?id=087700000008WiBAAU](http://www.ideastorm.com/ideaView?id=087700000008WiBAAU)

It would be great to switch between Ubuntu (netbook mode) and something like Android (tablet mode) without rebooting.

Something maybe interesting:
[http://www.alwaysinnovating.com/products/aios.htm](http://www.alwaysinnovating.com/products/aios.htm)

I know its not the same as what your looking for, but one could run a macro, or have a script that would launch chrome os in virtual box when you press a button.

That, always innovating is neat. Its like virtulization on the font end with a gui.

---

### Post by raphaelsaldanha on 2011-05-06
Related: [http://www.pcworld.com/businesscenter/article/224429/canonical_commits_to_netbooks_over_tablets_for_ubuntu.html](http://www.pcworld.com/businesscenter/article/224429/canonical_commits_to_netbooks_over_tablets_for_ubuntu.html)

PS: still waiting for the delivery of my Duo, next week I think.

---

### Post by JaseP on 2011-05-06
My Duo is (supposed) to come today. Any recommendations as to Maverick vs. Natty & what is & isn't working?


PS: Some Fedora user has the accelerometers working:
[http://lukeross.name/dell/](http://lukeross.name/dell/)

---

### Post by salmander on 2011-05-07
> **Caboose885 said:**
> Actually florence is probably the better vkeyboard but KDE has kvkbd built into it and it works well enough for me.

I have no problems with items in my sys tray. (I use dropbox and I have the little dropbox icon in my tray) Are you sure Dropbox is running?
I switched to classic desktop mode and dropbox is there....but in unity one its not displaying in system tray...any ideas??

---

### Post by repunante on 2011-05-07
> **Non.Cents said:**
> I know its not the same as what your looking for, but one could run a macro, or have a script that would launch chrome os in virtual box when you press a button.

That, always innovating is neat. Its like virtulization on the font end with a gui.

I tried Android in VirtualBox but unfortunately the touch screen is not working for me.
I managed to arrange a dual boot Android 2.2 (Sparta, x86)/Ubuntu Natty; it is working OK but I'm still looking for a better solution than rebooting.

---

### Post by joey-elijah on 2011-05-08
> **salmander said:**
> I switched to classic desktop mode and dropbox is there....but in unity one its not displaying in system tray...any ideas??

I, too, have Dropbox in my system tray with no issue. Where did you download/install it from?

---

### Post by JaseP on 2011-05-08
> **repunante said:**
> I tried Android in VirtualBox but unfortunately the touch screen is not working for me.
I managed to arrange a dual boot Android 2.2 (Sparta, x86)/Ubuntu Natty; it is working OK but I'm still looking for a better solution than rebooting.

Is there a fundamental difference between running Chromium browser full screen versus the entire Chrome OS??? My understanding is that you could run Chrome OS services in the Chromium browser... that the OS was just the browser running as a dedicated app as a window manager on top of Linux. ?!?!

---

### Post by nasul on 2011-05-08
Thanks for the tutorial. I have a frined with an Dell Inspiron Duo and Windows 7 did not work as expected but Ubuntu UNR works fine.

---

### Post by Azelphur on 2011-05-08
The issues I'm currently having in Natty are...

Touch screen doesn't work even with usbhid.quirks=0x0eef:0x725e:0x40
Headphone port doesn't work, but first page alsa fix fixes it
Kernel panics most of the time when unplugging or plugging in the laptop
"Touchpad" tab from Mouse preferences is missing (Touchpad not detected as a touchpad?) so none of the following work: disable while typing, clicks with touchpad, two-finger or edge scrolling.

Can anyone confirm any of these issues for me?

I've been looking into the kernel panics, I tried the mainline kernel and the issue still persists. I tried to setup netconsole however it doesn't work via wifi or usb ethernet, so I'm stuck trying to get a log for a bug report. :(

---

### Post by BruinFisher on 2011-05-09
I just ordered my Duo. I need to thank you guys for your sterling work and selfless advice, which has given me the courage to commit my hard-earned pennies. 

I'm not clever like you but I am a keen Ubuntu user (for the last five years or more on my now-failing Toshiba laptop) and I've seen the Duo some time back but couldn't take the risk that I wouldn't be able to get Ubuntu running well on it. But now I've found your guide and advice and I'm going for it.

A couple of (possibly off-topic) comments about the purchase process: here in the UK the Duo is £448 direct from Dell (250Gb HDU, 5400rpm) or about £570 from Amazon who claim it has a 320Gb HDU although both say it's only available in one configuration. I phoned Dell and asked for the machine without OS and the guy said they can't supply without an OS but he offered me £30 off the price anyway. So I ordered it for £418. Not buying the JBL dock yet, I'll wait until someone reports it works!

This is my first post in the Ubuntu Forums. If I'm bungling, just tell me!

Thanks again, guys. You are what makes the open source solution great.

---

### Post by JaseP on 2011-05-09
I have had my Duo sine Friday, and am loving it. This is the experience I was looking for since I got a Pepper Pad 3 about 5 years ago.

I tried Lucid for a short while before the sound crapped out... and decided to go with Maverick, since that's where most of the success seems to be. I too have issues with bluetooth (apparently seen, but not really workable). As others seem to indicate, there are 2 cards these things seem to be shipping with. One is no problem in Linux. The other is an issue (Dell rebranded AR9285, apparently).

I haven't yet tried the alleged auto-rotation hack, but may soon.

---

### Post by Kirboosy on 2011-05-09
> **Azelphur said:**
> The issues I'm currently having in Natty are...

Touch screen doesn't work even with usbhid.quirks=0x0eef:0x725e:0x40
Headphone port doesn't work, but first page alsa fix fixes it
Kernel panics most of the time when unplugging or plugging in the laptop
"Touchpad" tab from Mouse preferences is missing (Touchpad not detected as a touchpad?) so none of the following work: disable while typing, clicks with touchpad, two-finger or edge scrolling.

Can anyone confirm any of these issues for me?

I've been looking into the kernel panics, I tried the mainline kernel and the issue still persists. I tried to setup netconsole however it doesn't work via wifi or usb ethernet, so I'm stuck trying to get a log for a bug report. :(

I can verify the kernel panic issue and two finger scrolling (for some) doesn't work. I'm not sure why the two finger scrolling worked for me out of the box but others say that it doesn't work on theirs.

As for the rest of your issues, are you sure you did everything in the tutorial correctly?

> **BruinFisher said:**
> I just ordered my Duo. I need to thank you guys for your sterling work and selfless advice, which has given me the courage to commit my hard-earned pennies. 

I'm not clever like you but I am a keen Ubuntu user (for the last five years or more on my now-failing Toshiba laptop) and I've seen the Duo some time back but couldn't take the risk that I wouldn't be able to get Ubuntu running well on it. But now I've found your guide and advice and I'm going for it.

A couple of (possibly off-topic) comments about the purchase process: here in the UK the Duo is £448 direct from Dell (250Gb HDU, 5400rpm) or about £570 from Amazon who claim it has a 320Gb HDU although both say it's only available in one configuration. I phoned Dell and asked for the machine without OS and the guy said they can't supply without an OS but he offered me £30 off the price anyway. So I ordered it for £418. Not buying the JBL dock yet, I'll wait until someone reports it works!

This is my first post in the Ubuntu Forums. If I'm bungling, just tell me!

Thanks again, guys. You are what makes the open source solution great.

Welcome to the forums! :D


As for the dock, I'm going to buy one. I searched on Ebay and found a brand new for a few bucks cheaper than Dell wanted to sell it to me for. (I tried to buy one from Dell but I didn't see any way unless I ordered another Duo.) I really want an RJ45 port on my Duo thats why I bought the dock.

-------------------------------------------------------------------------

As for everyone else. I think I'm going to roll back to Maverick and see if the touchscreen drivers will install correctly. The drivers egalax gave do not support 11.04 just yet. I know our touchscreen is using the USB interface to communicate with the rest of the system. I booted into Windows and used the windows version of the driver to find this information out.

I know that once the driver is installed it will not magically give you multi touch. It actually broke my multi-touch functionality on Windows as the multi-touch interpretor didn't work correctly after the update. 

Utouch will be needed for it to work properly. I'm still trying to figure out uTouch. As for the gestures. What would everyone like to see for the multi-touch? I know two finger scrolling is a must but what else?

---

### Post by salmander on 2011-05-09
> **joey-elijah said:**
> I, too, have Dropbox in my system tray with no issue. Where did you download/install it from?
the file i downloaded from is dropbox website...the file says its 0.6.7 and the web says the latest version is 1.1.31 for linux.... and the dopbox prefences says its 1.1.28. so I am a bit confused....whichever one it is.. Anyways i uninstalled it and downloaded a new file from internet and installed it again...but same version i m getting... right now i m running ubuntu classic interface (with no unity) and i can see the icon on the system tray... but in unity i cant. but the sync works fine...like if i add some files to a folder...and i check on my mobile dropbox it shows there...

---

### Post by JaseP on 2011-05-09
Just a helpful hint,...

If you use the Compiz magnify tool, you can get an on-screen magnification that does not mess you up for using the touch screen. this is helpful in getting more accuracy with the touch screen on menu items and on toolbars with small icons,...

Using onboard I defined the keys to activate magnification as being [Alt]+[Super]+z, and deactivated zooming. I set the default zoom to 3x in the next tab. When using onbaord to deactivate, you can click than slide to each successive key in order, within the magnification window (click then drag to the next key, then click then drag to the following key, etc.). For my onbaord setting,... I have Compiz refuse to allow resizing, minimising, moving, etc. (only closing). I have onboard set to sticky (all windows), and have given it a translucency of about 70%.

On my M912m, I had used a second dock menu to bring up onboard or cellwriter, and also to define screen rotation (portrait & landscape) icons. I had two separate icons for onboard (one that defined portrait sized keyboard settings & and another for landscape). I use Cairo-dock, by the way, and have only a gnome-panel that auto-hides for back-up. I also have 3 desktops on a cube that rotate with the Cairo-dock widget, or auto-rotate to restore windows to their original desktop.

Has anyone any success with the drivers & script for auto rotation with the accelerometers???

---

### Post by Azelphur on 2011-05-10
> **Caboose885 said:**
> 
As for the rest of your issues, are you sure you did everything in the tutorial correctly?

Reasonably sure, yes

azelphur@azelphur-inspiron:~$ cat /etc/default/grub | grep quirks
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbhid.quirks=0x0eef:0x725e:0x40"
azelphur@azelphur-inspiron:~$ cat /boot/grub/grub.cfg | grep quirks
	linux	/boot/vmlinuz-2.6.38-02063805-generic root=UUID=ce34d4c7-e509-4e25-84ac-b1e86ebaba0b ro   quiet splash usbhid.quirks=0x0eef:0x725e:0x40 vt.handoff=7
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=ce34d4c7-e509-4e25-84ac-b1e86ebaba0b ro   quiet splash usbhid.quirks=0x0eef:0x725e:0x40 vt.handoff=7

Interestingly, My touch screen doesn't work in android x86 either, and it's supposed to. I'm starting to wonder if I got a new revision of the device but with a different touch screen. Is there any way to get the model of the touch screen?

---

### Post by JaseP on 2011-05-10
Did you run the command to update grub when you made the grub changes??? It's doubtful that there's a revision of the device... The third alternative (the one you don't want to hear) is that you touch screen is broken. Does (or did) it work in Windoze???

Install the package "input-utils" then run (in a terminal) "sudo lsinput". There should be 5 event entries for an eGalax controller.

---

### Post by Azelphur on 2011-05-10
> **JaseP said:**
> Did you run the command to update grub when you made the grub changes??? It's doubtful that there's a revision of the device... The third alternative (the one you don't want to hear) is that you touch screen is broken. Does (or did) it work in Windoze???

Install the package "input-utils" then run (in a terminal) "sudo lsinput". There should be 5 event entries for an eGalax controller.

No idea if it worked in windows, I bought it refurbished with no OS, it is however under warranty. :)

Here's my lsinput. No sign of an eGalax controller. :(

```
/dev/input/event0
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x1
   version : 0
   name    : "Power Button"
   phys    : "PNP0C0C/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event1
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x3
   version : 0
   name    : "Sleep Button"
   phys    : "PNP0C0E/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event2
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x5
   version : 0
   name    : "Lid Switch"
   phys    : "PNP0C0D/button/input0"
   bits ev : EV_SYN EV_SW

/dev/input/event3
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x1
   version : 0
   name    : "Power Button"
   phys    : "LNXPWRBN/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event4
   bustype : BUS_I8042
   vendor  : 0x1
   product : 0x1
   version : 43841
   name    : "AT Translated Set 2 keyboard"
   phys    : "isa0060/serio0/input0"
   bits ev : EV_SYN EV_KEY EV_MSC EV_LED EV_REP

/dev/input/event5
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x6
   version : 0
   name    : "Video Bus"
   phys    : "LNXVIDEO/video/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event6
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "Dell WMI hotkeys"
   phys    : "wmi/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event7
   bustype : BUS_USB
   vendor  : 0xbda
   product : 0x58f4
   version : 2599
   name    : "Laptop_Integrated_Webcam_1.3M"
   phys    : "usb-0000:00:1d.7-3/button"
   bits ev : EV_SYN EV_KEY

/dev/input/event8
   bustype : BUS_I8042
   vendor  : 0x2
   product : 0x7
   version : 433
   name    : "SynPS/2 Synaptics TouchPad"
   phys    : "isa0060/serio1/input0"
   bits ev : EV_SYN EV_KEY EV_ABS

```

Also called up the guy I bought it off (he's a friend of mine that runs a refurb store) and he says it was tested before I got it and it was working, so either something strange with software or it died in the post.

---

### Post by JaseP on 2011-05-10
Install the gnome device manager, just to be sure... And did it put the pointer in the upper-left corner when you touched the screen???

If no eGalax touch or pointer movement,... it's fried or otherwise broken.

---

### Post by JaseP on 2011-05-10
I have confirmed that the Atheros AR9285 Bluetooth problem is a known issue. Please look here:

[http://www.spinics.net/lists/linux-bluetooth/msg10284.html](http://www.spinics.net/lists/linux-bluetooth/msg10284.html)

So, there is apparently a patch, just maybe not for Ubuntu Maverick or Natty yet... If we're lucky, it is only a kernel module that needs patching, not the whole kernel...

If anyone knows a solution to the bluetooth issue, let us know.


PS: A possible fix until a fix is made upstream;

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/714862](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/714862)

---

### Post by Azelphur on 2011-05-10
> **JaseP said:**
> Install the gnome device manager, just to be sure... And did it put the pointer in the upper-left corner when you touched the screen???

If no eGalax touch or pointer movement,... it's fried or otherwise broken.

No eGalax in gnome device manager, no pointer movement. :(

---

### Post by Kirboosy on 2011-05-10
Try liveCD Ubuntu and see if it appears then. (I think your touchscreen is bad. That might be the reason why the device was refurbished in the first place.)

---

### Post by JaseP on 2011-05-11
I'm 95% sure his touchscreen is SOL...


Has anyone tried the wireless patch I've referenced above???


What about the accelerometer hack (I think it could be modded to work with Compiz's commands &/or dbus...)???

---

### Post by Kirboosy on 2011-05-11
> **JaseP said:**
> Has anyone tried the wireless patch I've referenced above??

I did try the patch. It fixed my problem with Bluetooth. (I'm running 10.10 32 Bit.) I'm going to add it to the Tutorial...

---

### Post by JaseP on 2011-05-11
Fantastic,... 
That just leaves accelerometers, optimised power management & full multi-touch to go (not holding my breath regarding power management &/or full multi-touch)...

I'm going to apply the wireless patch, then take a stab at the accelerometers tonight.

---

### Post by JaseP on 2011-05-11
Bluetooth working for me too (a little sluggish, that's the AR9285, though). I've set up (very simple) hotkeys for Xrandr screen rotation. I'm going to try pairing them with Lukeross's accelerometer script tonight.

---

### Post by erbey on 2011-05-11
sorry if it's already been found, but while browsing today i found this-
[http://www.techdrivein.com/2011/05/10-useful-application-indicators-for.html](http://www.techdrivein.com/2011/05/10-useful-application-indicators-for.html)

a list of 10 useful application indicators for natty, the one of interest was a touchpad indicator...
can't test it or anything as the duo STILL isn't out in australia...but some may find it usefull

---

### Post by salmander on 2011-05-12
> **erbey said:**
> sorry if it's already been found, but while browsing today i found this-
[http://www.techdrivein.com/2011/05/10-useful-application-indicators-for.html](http://www.techdrivein.com/2011/05/10-useful-application-indicators-for.html)

a list of 10 useful application indicators for natty, the one of interest was a touchpad indicator...
can't test it or anything as the duo STILL isn't out in australia...but some may find it usefull
thanks for this man...
Does anybody know how to install florence in ubuntu natty?
i "cd florence && ./configure2" did this and got this error
"configure: error: Could not configure libpanelapplet2. Please either install libpanelapplet2 or disable it: --without-panelapplet configure option"

any suggestions??

---

### Post by JaseP on 2011-05-12
Look for florence using the synaptic package manager. If it's not there, try looking for it on the Ubuntu Launchpad PPAs...

You're better off installing from a PPA, if not in the usual repositories, than from trying to compile it yourself.

---

### Post by salmander on 2011-05-12
> **JaseP said:**
> Look for florence using the synaptic package manager. If it's not there, try looking for it on the Ubuntu Launchpad PPAs...

You're better off installing from a PPA, if not in the usual repositories, than from trying to compile it yourself.
thanks mate....i found it in synaptic package manager....i wonder why i didnt look for it earlier...
anyways...i m new to linux and soo ya not very familar with everything...
but ya thanks... but earlier on it used to show its icon on the system tray...and now it doesnt anymore...it does show itself in the app launcher though...
take care...

---

### Post by Kirboosy on 2011-05-12
Hey everyone. I emailed EETI (makers of egalax) for some help with the touchscreen. Here was my email [QUOTE=Caboose885]To Whome It May Concern:
  I installed your Linux Touchkit driver on 32-Bit Ubuntu 10.10 (your driver does not work on Ubuntu 11.04) for my Dell Duo. Everything worked great. The driver went in easily and I calibrated the screen and everything seemed good. I only have one quirk/problem with it. Is this driver supposed to give my tablet multi-touch? My screen is supposed to have 2 point multi-touch but even after installing the driver I only had a single input.

Any information would be greatly appreciated.

Thank you

Drew

P.S. Here is the Ubuntu Forums thread that I started as a guide/research thread for the Dell Duo. Any information will be directly sent back to this thread to help the community.
 
[http://ubuntuforums.org/showthread.php?t=1658635](http://ubuntuforums.org/showthread.php?t=1658635)[/QUOTE]
 
Here is the response
 
[QUOTE=Timmy Cheng]Dear Sir:
 
Sorry for our driver that was not verified on Ubuntu 11.04 (X-version 1.10.x).

So the new revision must wait for a few days.

The official driver on EETI website only supports one finger touch due to X server doesn't support multi-touch feature by default.
 
Thanks!! 
 
 
Best Regards, Timmy Cheng[/QUOTE]

So I'm not sure where to go from here with it...

---

### Post by JaseP on 2011-05-13
Same old, same old... They figure we should be grateful for ***any*** support. Nothing you can do until the driver modules can properly handle it.

---

### Post by w1ll1am on 2011-05-13
> **Caboose885 said:**
> 

As for everyone else. I think I'm going to roll back to Maverick and see if the touchscreen drivers will install correctly. The drivers egalax gave do not support 11.04 just yet. I know our touchscreen is using the USB interface to communicate with the rest of the system. I booted into Windows and used the windows version of the driver to find this information out.

I know that once the driver is installed it will not magically give you multi touch. It actually broke my multi-touch functionality on Windows as the multi-touch interpretor didn't work correctly after the update. 

Utouch will be needed for it to work properly. I'm still trying to figure out uTouch. As for the gestures. What would everyone like to see for the multi-touch? I know two finger scrolling is a must but what else?

Did you ever install this driver and if so what happened?

Is this the driver that you emailed EETI about?

---

### Post by Kirboosy on 2011-05-13
> **w1ll1am said:**
> Is this the driver that you emailed EETI about?

Correct. I installed the driver and I only have single touch. Emailed EETI and they didn't really help. So I guess we are one a limb until a developer comes along and works with us. Drivers are a bit over me.

---

### Post by salmander on 2011-05-15
> **Caboose885 said:**
> Correct. I installed the driver and I only have single touch. Emailed EETI and they didn't really help. So I guess we are one a limb until a developer comes along and works with us. Drivers are a bit over me.
i installed the script mentioned in your first post and it did rotated my screen but my trackpad and touchscreen was working in a weird way...so i guess it wasnt for natty...anyway i edited the file and removed all of its contents and saved it again...so i dont accidently open it or something...as i dont know how to delete the file using terminal...

thanks man...for your effort..

---

### Post by Kirboosy on 2011-05-15
> **salmander said:**
> i installed the script mentioned in your first post and it did rotated my screen but my trackpad and touchscreen was working in a weird way...so i guess it wasnt for natty...anyway i edited the file and removed all of its contents and saved it again...so i dont accidently open it or something...as i dont know how to delete the file using terminal...

thanks man...for your effort..

to delete the file through terminal just run ```
rm /location/to/script/rotate.sh (or whatever you named the file)
```

If its a folder run ```
rm -rf /location/to/script/rotate.sh
```

[COLOR="Red"]EDIT: Be careful with the **rm -rf** command because it will delete stuff without asking for confirmation. It will not delete root/system files but you still could delete important data files off your computer accidentally [/COLOR]

---

### Post by teamkde on 2011-05-16
Has anyone been able to get multi-touch working with 11.04? I had one of the release candidates and out of the box it recognized touching the screen with multiple fingers to bring up the workspaces, but then when the release came out I still had to modify grub to get the touch screen to work. I like 11.04 better in every way and it's very usable but two finger scrolling would be great.

---

### Post by salmander on 2011-05-16
> **Caboose885 said:**
> to delete the file through terminal just run ```
rm /location/to/script/rotate.sh (or whatever you named the file)
```

If its a folder run ```
rm -rf /location/to/script/rotate.sh
```

[COLOR="Red"]EDIT: Be careful with the **rm -rf** command because it will delete stuff without asking for confirmation. It will not delete root/system files but you still could delete important data files off your computer accidentally [/COLOR]
thanks man...

---

### Post by bikealot on 2011-05-18
After reviewing the Forum it sounds as though the Duo works better on 10.10 than 11.04.  Anyone have a running score of the pros and cons for each Ubuntu release?

---

### Post by JaseP on 2011-05-19
I came to the same conclusion...

But, I don't think anyone has a "Pros & Cons" list... It's inevitable, 10.10 has just been out longer than 11.04 & had more touch screen support than 10.04 LTS (which runs on 11 of my home's 13 computers).

---

### Post by SleEpInG_GoD on 2011-05-20
USB driver, it give me 5 options...
1-Install Ubuntu Netbook Edition 10.x
2-Apply simple updates
3-Do both 1 & 2
4-Fast image (both 1 & 2, format user home, no prompts)
5-Expert Options.
So I have 2 drivers partitions (c: for W7) and (D: the one that I have created for Ubuntu).SO I've selected the 1 options and displays the next information: this installation will erase all your data....So please can anybody help me go trough this????I don't know what 2 do, because this installation in the first steps it's not graphical one( with interface).

---

### Post by JaseP on 2011-05-20
Use unetbootin to create a Live CD image on a flash drive & then choose to boot the Live image. Run the installer manually, & make sure to use custom partitioning or the preserve current OS options to install to the empty partition. I'd use the x386 desktop version, not netbook,... you can always install the netbook remix launcher later.

---

### Post by SleEpInG_GoD on 2011-05-20
Please can  anybody tell me if I choose option one to install ubermix.img, it will erase my windows or not???

---

### Post by JaseP on 2011-05-21
If you are concerned, don't use that image,... use a Live CD image instead. If you use an image that could potentially erase your M$ partition, you can't blame it on Linux. That'd be user error.

---

### Post by macshield on 2011-05-21
> **SleEpInG_GoD said:**
> Please can  anybody tell me if I choose option one to install ubermix.img, it will erase my windows or not???

If I remember correctly choosing option 1 will erase your whole hard drive. I didn't figure out how to have it install on a specific partition.

---

### Post by SleEpInG_GoD on 2011-05-21
SO the version x386 for desktop supports touch screen???Cause I want to be able 2 explore the duo maximum.

---

### Post by Kirboosy on 2011-05-21
> **SleEpInG_GoD said:**
> SO the version x386 for desktop supports touch screen???Cause I want to be able 2 explore the duo maximum.

Yes. Any version of Ubuntu supports the touchscreen as well as the netbook version. (Its still Ubuntu at the core so you just have to decide on how you want it to look an feel.) I really liked KDE on my Duo because it made it very touchable and pretty. Now I run Fluxbox and have a very minimalistic setup. :D

You should have an option to 'specify the partitions manually'. That is what I do to install Ubuntu on my computer.

---

### Post by khanning on 2011-05-21
Hey everyone just picked up a duo yesterday and wanted to say thanks to everyone that has contributed to this thread. 

Has anyone had luck setting a lower 16:9 resolution? In the Monitor Preferences I just have:

1366x768 (16:9)
1360x768 (16.9)
1024x768 (4:3)
800x600 (4:3)
640x480 (4:3)

I tried adding 1280x720, and 1024x576 using xrandr but the screen goes black after trying to set one of those two resolutions. I am able to set other resolutions like 1280x600 but it results in black bars on the sides of the screen.

I'm basically trying to get the display working like the guy in this video at 3:18:
[http://www.youtube.com/watch?v=vGlPvnW6mgU](http://www.youtube.com/watch?v=vGlPvnW6mgU)

I dont know if he's using an applications or just a script to toggle the display size, but that looks nice.

Any help will be greatly appreciated.

*Edit* I am running 11.04 32-bit

---

### Post by SleEpInG_GoD on 2011-05-21
[COLOR="Red"]Caboose88[/COLOR]5 THANK 4 the help, I've installed Ubuntu 11.04 Desktop version.It's looks fresh and nice.Now I am investigating all about KDE and Gnome.So If I Install KDE it want fight with Gnome Desktop environment????Oh Bye Bye W7...Welcome Ubuntu.

---

### Post by khanning on 2011-05-21
> **SleEpInG_GoD said:**
> [COLOR=Red]Caboose88[/COLOR]5 THANK 4 the help, I've installed Ubuntu 11.04 Desktop version.It's looks fresh and nice.Now I am investigating all about KDE and Gnome.So If I Install KDE it want fight with Gnome Desktop environment????Oh Bye Bye W7...Welcome Ubuntu.

You can actually install KDE from the repositories and then choose between Gnome or KDE each time you log in. There is a drop down at the bottom of the GDM login screen that lets you choose the desktop session.

---

### Post by Kirboosy on 2011-05-21
> **SleEpInG_GoD said:**
> [COLOR="Red"]Caboose88[/COLOR]5 THANK 4 the help, I've installed Ubuntu 11.04 Desktop version.It's looks fresh and nice.Now I am investigating all about KDE and Gnome.So If I Install KDE it want fight with Gnome Desktop environment????Oh Bye Bye W7...Welcome Ubuntu.

in Synaptic if you type in the 'Quick Search' Box "kubuntu-desktop" or "kubuntu-netbook" you can install KDE that way. It will install a bunch of additional programs on your computer too. I recommend Netbook but you can use whichever you wish. :)

---

### Post by khanning on 2011-05-22
Reporting back on my previous post about possible 16:9 resolutions.

I've gone back to Ubuntu 10.10 as I wasn't able to get any lower 16:9 resolutions working in Natty. In Ubuntu 10.10 I'm able to get 1280x720, 1024x576, and 856x480 working. I personally prefer 1024x576 when using the device as a tablet.

Here are the xrandr commands I used to add each resolution.

1280x720
```

To add:

xrandr --newmode "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync

xrandr --addmode LVDS1 1280x720_60.00

To choose:

xrandr --output LVDS1 --mode 1280x720_60.00

```1024x576
```

To add:

xrandr --newmode "1024x576_60.00"   46.50  1024 1064 1160 1296  576 579 584 599 -hsync +vsync

xrandr --addmode LVDS1 1024x576_60.00

To choose:

xrandr --output LVDS1 --mode 1024x576_60.00

```856x480
 ```

To add:

xrandr --newmode "856x480_60.00"   31.75  856 880 960 1064  480 483 493 500 -hsync +vsync
 
xrandr --addmode LVDS1 856x480_60.00

To choose:

xrandr --output LVDS1 --mode 856x480_60.00

```

---

### Post by repunante on 2011-05-22
> **khanning said:**
> Reporting back on my previous post about possible 16:9 resolutions.

I've gone back to Ubuntu 10.10 as I wasn't able to get any lower 16:9 resolutions working in Natty. In Ubuntu 10.10 I'm able to get 1280x720, 1024x576, and 856x480 working. I personally prefer 1024x576 when using the device as a tablet.

Here are the xrandr commands I used to add each resolution.

1280x720
```

To add:

xrandr --newmode "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync

xrandr --addmode LVDS1 1280x720_60.00

To choose:

xrandr --output LVDS1 --mode 1280x720_60.00

```1024x576
```

To add:

xrandr --newmode "1024x576_60.00"   46.50  1024 1064 1160 1296  576 579 584 599 -hsync +vsync

xrandr --addmode LVDS1 1024x576_60.00

To choose:

xrandr --output LVDS1 --mode 1024x576_60.00

```856x480
 ```

To add:

xrandr --newmode "856x480_60.00"   31.75  856 880 960 1064  480 483 493 500 -hsync +vsync
 
xrandr --addmode LVDS1 856x480_60.00

To choose:

xrandr --output LVDS1 --mode 856x480_60.00

```


Good one, thanks.

I was looking for some resolutions and I personally prefer the 1040x585, here they are the commands:

xrandr --newmode "1040x585_60.00"   48.25  1040 1080 1184 1328  585 588 593 609 -hsync +vsync
xrandr --addmode LVDS1  1040x585_60.00
xrandr --output LVDS1 --mode 1040x585_60.00


I wasn't able to change the resolution in 11.04 neither, it is a bit annoying.

---

### Post by bikealot on 2011-05-23
> **macshield said:**
> If I remember correctly choosing option 1 will erase your whole hard drive. I didn't figure out how to have it install on a specific partition.

I have tested, and YES, this option will reformat the entire drive.  Once you do this, you will no longer be able to press F8 and get back to the factory image.

---

### Post by Kirboosy on 2011-05-23
> **bikealot said:**
> I have tested, and YES, this option will reformat the entire drive.  Once you do this, you will no longer be able to press F8 and get back to the factory image.

My Duo is actually having a problem where I can't start "Repair My Computer" mode. I wanted to reinstall Windows and resize the partition but Windows won't work properly. I think it is a sign that it might be time to erase Windows totally and only have Windows on my desktop. 

Honestly the only reason I have kept Windows on it for so long is because of Angry Birds and so I can try and figure out multi-touch. (It sounds like multi-touch will be next to impossible unless the devs work with us.)

---

### Post by bikealot on 2011-05-24
> **khanning said:**
> 
Has anyone had luck setting a lower 16:9 resolution? In the Monitor Preferences I just have:

1366x768 (16:9)
1360x768 (16.9)
1024x768 (4:3)
800x600 (4:3)
640x480 (4:3)

I tried adding 1280x720, and 1024x576 using xrandr but the screen goes black after trying to set one of those two resolutions. I am able to set other resolutions like 1280x600 but it results in black bars on the sides of the screen.


Yes, this is an issue with 11.04 - it works in 10.10.  The problem exists on all desktops (Unity, 2D, Classic, ..). I submitted a Launchpad bug, so we will see where that leads us.

---

### Post by bikealot on 2011-05-25
In reference to rotating the cursor with the screen...

I found some info on how to rotate the cursor with the screen, but ran out of spare time to take to completion.  So, if somebody has time to track down, here are some information pointers.

1) There is a related Launchpad bug [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/217182](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/217182).  The key piece of info in this bug is:
[INDENT]This bug can be fix manually using next command:
 $ xsetwacom set stylus rotate X
$ xsetwacom set cursor rotate X
$ xsetwacom set eraser rotate X
 where X is
cw --> for 180º rotate
ccw --> for portrait use
none --> for normal use
 xsetwacom is provided by wacom-tools package

[/INDENT]2) xsetwacom is shipped with Ubuntu

3) the devices (stylus, cursor, eraser) are defined in xorg.conf, but this X configuration file is no longer used. It would need to be created.

4) I found a pointer for how to create the devices in xorg.conf, but it was not clear and will require more digging... [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page) 

Another useful reference page may be [http://ubuntuforums.org/showthread.php?t=301380](http://ubuntuforums.org/showthread.php?t=301380)

Hopefully, someone who has a good handle on xorg.conf can assist here....

---

### Post by JaseP on 2011-05-25
If you follow the guide in the first post for Maverick 10.10 (32-bit) & install some of the extras (the touchscreen helper ones), you shouldn't have problems using xrandr to rotate with (touchscreen) cursor support working just fine. You can set icons to run the xrandr commands on whatever dock you use...

I am still exploring doing rotate with the accelerometers, but haven't had time. Damn that stomach flu... Well, there's always Memorial Day weekend...

---

### Post by bikealot on 2011-05-25
> **JaseP said:**
> If you follow the guide in the first post for Maverick 10.10 (32-bit) & install some of the extras (the touchscreen helper ones), you shouldn't have problems using xrandr to rotate with (touchscreen) cursor support working just fine. You can set icons to run the xander commands on whatever dock you use...

I am still exploring doing rotate with the accelerometers, but haven't had time. Damn that stomach flu... Well, there's always Memorial Day weekend...

I am on 11.04.  I did not do any of the 10.10 configuration changes on the  first post.  Maybe I need to also look at doing some of those...

---

### Post by rafael.rro on 2011-05-26
I'm on 11.04 and the touchscreen-helper found on the PPA does work, but two  problems appears. One is that when you rotate right or left part of the screen becomes black (it seems to be a problem with Unity, so unity --replace kinda "solves" this until an update comes...), and there is a problem when you drag the pointer on the touchscreen (using chromeTouch for example), the mouse acts weird going on various directions, and the same thing does not happen when you use the touchpad.

Anyone knows something about the 2.6.38 version for the accelerometer driver? 

And another one, does anyone knows something about the Broadcom CrystalHD driver too?

---

### Post by Kirboosy on 2011-05-26
> **rafael.rro said:**
> And another one, does anyone knows something about the Broadcom CrystalHD driver too?

Yes, I downloaded and compiled it but I did not see any difference with it. VLC and Mplayer can play anything on my Duo quite well without it. If you still want to install the driver it can be found [here]("http://www.broadcom.com/support/crystal_hd/")

The README will tell you exactly what to do. :)

---

### Post by rafael.rro on 2011-05-26
> **Caboose885 said:**
> Yes, I downloaded and compiled it but I did not see any difference with it. VLC and Mplayer can play anything on my Duo quite well without it. If you still want to install the driver it can be found [here]("http://www.broadcom.com/support/crystal_hd/")

The README will tell you exactly what to do. :)
Did you try some HD video, for example the nvidia HD test with 1080p? (available at [http://www.youtube.com/watch?v=XITHbsUUlYI](http://www.youtube.com/watch?v=XITHbsUUlYI)) On Windows it worked just fine, but here on Ubuntu the CPU goes 100% and it's still very slow...

Anyway, I will compile it and give it a try, thanks!

PS: Download the video instead of watching on You Tube because it seems that Linux's Adobe Flash port does not support HD content.

---

### Post by bikealot on 2011-05-26
> **rafael.rro said:**
> I'm on 11.04 and the touchscreen-helper found on the PPA does work, but two  problems appears. One is that when you rotate right or left part of the screen becomes black (it seems to be a problem with Unity, so unity --replace kinda "solves" this until an update comes...), and there is a problem when you drag the pointer on the touchscreen (using chromeTouch for example), the mouse acts weird going on various directions, and the same thing does not happen when you use the touchpad.

Anyone knows something about the 2.6.38 version for the accelerometer driver? 

And another one, does anyone knows something about the Broadcom CrystalHD driver too?

Could someone provide a pointer to the PPA?  I have found a 10.10 touchscreen PPA, but not 11.04.

---

### Post by rafael.rro on 2011-05-26
Sorry for the misunderstanding, but I used the lucid version of the .deb from [https://launchpad.net/~plippo/+ppa-packages](https://launchpad.net/~plippo/+ppa-packages) on my Ubuntu version 11.04. Is not that I found a 11.04 PPA.

---

### Post by rafael.rro on 2011-05-26
And sorry again, not Lucid but Maverick. Here is the exact link to be more precise -> [https://launchpad.net/~plippo/+archive/t101mt/+files/touchscreen-helper_0.0.1-ppa2_i386.deb](https://launchpad.net/~plippo/+archive/t101mt/+files/touchscreen-helper_0.0.1-ppa2_i386.deb)

---

### Post by bikealot on 2011-05-26
> **rafael.rro said:**
> And sorry again, not Lucid but Maverick. Here is the exact link to be more precise -> [https://launchpad.net/~plippo/+archive/t101mt/+files/touchscreen-helper_0.0.1-ppa2_i386.deb]("https://launchpad.net/%7Eplippo/+archive/t101mt/+files/touchscreen-helper_0.0.1-ppa2_i386.deb")

Thank you.  I was able to install on 11.04.  As you stated, it works "ok", but does have issues, but it is better than nothing at the moment.  BTW, I am using Unity-2D as my desktop.

---

### Post by Kirboosy on 2011-05-26
> **rafael.rro said:**
> Did you try some HD video, for example the nvidia HD test with 1080p? (available at [http://www.youtube.com/watch?v=XITHbsUUlYI](http://www.youtube.com/watch?v=XITHbsUUlYI)) On Windows it worked just fine, but here on Ubuntu the CPU goes 100% and it's still very slow...

Anyway, I will compile it and give it a try, thanks!

PS: Download the video instead of watching on You Tube because it seems that Linux's Adobe Flash port does not support HD content.

Yes, I can play [Big Buck Bunny]("http://www.bigbuckbunny.org/") and [Elephants Dream]("http://www.elephantsdream.org/") flawlessly in 1080p. Make sure any HD you play is with VLC because Totem will always die. Sometimes VLC will even not work right. Mplayer seems to play anything well. 

I am downloading the video you linked to now. (Flash in general doesn't work to well on Ubuntu. Even on my Quad Core Desktop flash is often times jittery and poor.)

EDIT: I can play that test video flawlessly with mplayer. VLC for some reason locks up but my CPU doesn't hit higher than 40%. Oh well... Also I don't think that video is really HD because its so grainy. Big Buck Bunny and Elephants Dream look so much better in my opinion. Oh and that is WITHOUT the HD chip driver. I will go ahead and re compile it and see if it allows VLC to work properly

---

### Post by SleEpInG_GoD on 2011-05-28
Caboose885 I have a problem.I have downloaded eGalaxTouch 64 kb, and instaled it...The trick part is when I reboot the system,I open the terminal and insert: eGalaxTouch...But he don't put the tocuh screen to work, the message is(bas:/usr/bin/eGalaxTouch : can't realizate the binarie fail( i had to translate because I installed the ubuntu 10.10 in Russian lenguage).Please forgive me for mu bad English, and I hope that U can give me some lights.

---

### Post by Kirboosy on 2011-05-29
> **SleEpInG_GoD said:**
> Caboose885 I have a problem.I have downloaded eGalaxTouch 64 kb, and instaled it...The trick part is when I reboot the system,I open the terminal and insert: eGalaxTouch...But he don't put the tocuh screen to work, the message is(bas:/usr/bin/eGalaxTouch : can't realizate the binarie fail( i had to translate because I installed the ubuntu 10.10 in Russian lenguage).Please forgive me for mu bad English, and I hope that U can give me some lights.

What did is the output in the terminal after you install the driver before you reboot? (if you can just copy and paste that would work)

---

### Post by jamynn on 2011-05-29
I am running into a bug where with 11.04 the touchscreen just doesnt work after I close the lid.  Rebooting doesnt solve the issue, only booting into Windows and then coming back to Ubuntu brings the touchscreen capability back, until the next time.

Whats also odd is that adding 

>  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbhid.quirks=0x0eef:0x725e:0x40"isnt required for me to have the touchscreen capability that is there.  The behavior after sleep is the same too.

---

### Post by Kirboosy on 2011-05-29
> **jamynn said:**
> I am running into a bug where with 11.04 the touchscreen just doesnt work after I close the lid.  Rebooting doesnt solve the issue, only booting into Windows and then coming back to Ubuntu brings the touchscreen capability back, until the next time.

Whats also odd is that adding 

isnt required for me to have the touchscreen capability that is there.  The behavior after sleep is the same too.

If you add the ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbhid.quirks=0x0eef:0x725e:0x40"
```

then you won't have to boot into Windows everytime to get your touchscreen working properly. If you notice if you boot into Windows and totally shut off your computer (not reboot but a full shutdown) your touchscreen won't work. Adding that line and running ```
sudo update-grub
``` will solve this issue.

---

### Post by jamynn on 2011-05-29
> **Caboose885 said:**
> If you add the ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbhid.quirks=0x0eef:0x725e:0x40"
```then you won't have to boot into Windows everytime to get your touchscreen working properly. If you notice if you boot into Windows and totally shut off your computer (not reboot but a full shutdown) your touchscreen won't work. Adding that line and running ```
sudo update-grub
``` will solve this issue.

I actually did do all that originally.  I followed your instructions step for step from the first post.  It doesnt appear to make a difference :(.

---

### Post by jamynn on 2011-05-29
> **jamynn said:**
> I actually did do all that originally.  I followed your instructions step for step from the first post.  It doesnt appear to make a difference :(.


you were right about the full shut down making it so that it doesnt work as well.  I guess in other words, that grub command doesnt appear to get my touch screen to work, any ideas?

---

### Post by Kirboosy on 2011-05-29
> **jamynn said:**
> you were right about the full shut down making it so that it doesnt work as well.  I guess in other words, that grub command doesnt appear to get my touch screen to work, any ideas?

I honestly have no idea. As soon as eGalax releases an updated driver that works with 11.04 I would suggest trying that, but so far there have not been any new driver releases.

I'm wondering if Dell switched out the touchscreen hardware or something crazy...

---

### Post by jamynn on 2011-05-29
just to make sure I am not doing anything stupid, here is the file content:

root@eran-Inspiron-1090:/home/eran# cat /etc/default/grub 
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbhid.quirks=0x0eef:0725e:0x40"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by Kirboosy on 2011-05-29
> **jamynn said:**
> root@eran-Inspiron-1090:/home/eran# cat /etc/default/grub 
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbhid.quirks=0x0eef:**0725e**:0x40"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
I found the problem. I noticed you didn't copy and paste because you missed a letter in the command. there is a x between the 0 and 7

it should read 0**x**725e:0x40 :)

Add the letter and rerun the update-grub command and you will be good to go

---

### Post by SleEpInG_GoD on 2011-05-30
Caboose 885..This is the script that I am seeing on my netbook.I have installed the 64-bit Ubuntu 10.10.But after installing the eGalaxTouch,I've rebooted the netbook, but it's seems not to work after all.Now I had readed the last line that sound like:(I) Please reboot the system for some changes to take effect. 
(I)	After booting, type "eGalaxTouch" to do calibration.So I have to boot where,cause If I have to booth somewhere than I am doing everything wrong, I am just rebooting Pc for changes to take effect.
SO THIS IS THE TEXT SCRIPT OF eGalaxTouch Installation

edson@SleEpInGGoD:~$ cd /home/edson/&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080;/eGalaxTouch64 
edson@SleEpInGGoD:~/&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080;/eGalaxTouch64$ sudo sh setup.sh[sudo] password for edson:  
 
 
(*) Linux driver installer for eGalaxTouch controller  
 
(I) Check user permission: root, you are the supervisor. 
(I) Begin to setup the eGalaxTouch driver. 
(I) Found and removed previous eGalaxTouch driver. 
(I) Extract eGalaxTouch driver archive to /usr/local/eGalaxTouch64. 
: not found029:  
(I) Create eGalaxTouch utility shortcut in /usr/bin. 
(I) Create TKCal tool shortcut in /usr/bin. 
(I) Searching the X input modules directory. 
(I) Check X window version: 1.9.x 
(I) Copy X module: x19/egalax_drv.so to /usr/lib/xorg/modules/input. 
 
(Q) Which interface controller do you use? 
(I) [1] RS232 [2] PS/2 [3] USB : 3 
(I) Using interface: USB 
(W) Unknown: Skip to check USB type. 
(I) Note that the option "SkipClick" "1" should be appended in the touch 
    section of X configuration file for HID compliant touch controller. 
    Besides, if the using touch controller is non-HID compliant controller, 
    the option "Device" "/dev/input/mice" for mouse should be changed to 
    "Device" "/dev/input/mouseX" to prevent the mouse driver from reading. 
(I) For details, see the document "Driver Guide.pdf". 
 
(I) Copy udev rule: 50-egalax.conf to /usr/share/X11/xorg.conf.d. 
 
(I) Please reboot the system for some changes to take effect. 
(I)	After booting, type "eGalaxTouch" to do calibration. 
edson@SleEpInGGoD:~/&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080;/eGalaxTouch64$

---

### Post by Kirboosy on 2011-05-30
> **SleEpInG_GoD said:**
> Caboose 885..This is the script that I am seeing on my netbook.I have installed the 64-bit Ubuntu 10.10.But after installing the eGalaxTouch,I've rebooted the netbook, but it's seems not to work after all.Now I had readed the last line that sound like:(I) Please reboot the system for some changes to take effect. 
(I)	After booting, type "eGalaxTouch" to do calibration.So I have to boot where,cause If I have to booth somewhere than I am doing everything wrong, I am just rebooting Pc for changes to take effect.
SO THIS IS THE TEXT SCRIPT OF eGalaxTouch Installation

So when you run the command ```
eGalaxTouch
``` it won't bring up any sort of menu? (remember commands in Linux are case sensitive. Also tab complete is really handy. You can type "eG" then hit the tab key for it to auto complete the word. :))

If its giving you an error while trying to perform the "4 Pts calibration" then try selecting "Clear Parameters" (its right under the 4 Pts Cal button.) and see if that helps any.

---

### Post by SleEpInG_GoD on 2011-05-30
Caboose885..No lucky...Stills not bring any sort of menu.I guess it's because I have Installed the Desktop version 64-bit instead of installing the 32 version...Man I am freaking out, I have already readed a lot of multitouch buildings and seems that the eGalaxTouch is the most easier to use.I am new at Ubuntu and there is a lot of things that I am sort of dumb..So there is a way to go from 64-bit 2 32-bit Ubuntu 10.10???

---

### Post by Kirboosy on 2011-05-30
> **SleEpInG_GoD said:**
> Caboose885..No lucky...Stills not bring any sort of menu.I guess it's because I have Installed the Desktop version 64-bit instead of installing the 32 version...Man I am freaking out, I have already readed a lot of multitouch buildings and seems that the eGalaxTouch is the most easier to use.I am new at Ubuntu and there is a lot of things that I am sort of dumb..So there is a way to go from 64-bit 2 32-bit Ubuntu 10.10???

The only way you can change (easily) from 64 bit to 32 bit is a clean install. (Back everything up and wipe it out...)

I'm not sure why the driver wouldn't be working for 64 bit if you are using the 64 bit driver.

---

### Post by SleEpInG_GoD on 2011-05-30
Caboose maybe I should do a Grub upgrade...like in this comment that I found: Re: Who Plans on getting a Dell inspiron Duo and installing Ubuntu?
Looks like some other people have the same issue with the eGalax Touch Screen and ubuntu. There is a document on how to get it work here.. I am still playing with it

[http://ubuntuforums.org/archive/inde...t-1613000.html](http://ubuntuforums.org/archive/inde...t-1613000.html)

Got it to work!

Login and open termina
Type sudo gedit /etc/default/grub
find the line that says
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
Replace with: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.noloop=1 usbhid.quirks=0x0eef:0x725e:0x40"

Save and close geditor.
Run sudo update-grub
Reboot.. Everything is working
__________________
The Only problem is that I don't know if this will mess up with the booth manager of W7.

---

### Post by Kirboosy on 2011-05-30
> **SleEpInG_GoD said:**
> Caboose maybe I should do a Grub upgrade...like in this comment that I found: Re: Who Plans on getting a Dell inspiron Duo and installing Ubuntu?
Looks like some other people have the same issue with the eGalax Touch Screen and ubuntu. There is a document on how to get it work here.. I am still playing with it

[http://ubuntuforums.org/archive/inde...t-1613000.html](http://ubuntuforums.org/archive/inde...t-1613000.html)

Got it to work!

Login and open termina
Type sudo gedit /etc/default/grub
find the line that says
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
Replace with: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.noloop=1 usbhid.quirks=0x0eef:0x725e:0x40"

Save and close geditor.
Run sudo update-grub
Reboot.. Everything is working
__________________
The Only problem is that I don't know if this will mess up with the booth manager of W7.


Oh yeah I forgot you can simply do the GRUB quirks still. (I like the driver better because you can calibrate it)

It won't mess up your W7 at all. That line that you added only effects Linux.

---

### Post by SleEpInG_GoD on 2011-05-30
So I just have to insert the codes of that comment that I have posted moments ago?

---

### Post by SleEpInG_GoD on 2011-05-30
:frown::frown::frown: Nothing is working in this crap...Even the commands of Grub R all mess up...I have tried trough GRUB,But the system says that The files that I am trying to call up Are not available...Man it's just annoying

---

### Post by rafael.rro on 2011-05-30
> **Caboose885 said:**
> Yes, I can play [Big Buck Bunny]("http://www.bigbuckbunny.org/") and [Elephants Dream]("http://www.elephantsdream.org/") flawlessly in 1080p. Make sure any HD you play is with VLC because Totem will always die. Sometimes VLC will even not work right. Mplayer seems to play anything well. 

I am downloading the video you linked to now. (Flash in general doesn't work to well on Ubuntu. Even on my Quad Core Desktop flash is often times jittery and poor.)

EDIT: I can play that test video flawlessly with mplayer. VLC for some reason locks up but my CPU doesn't hit higher than 40%. Oh well... Also I don't think that video is really HD because its so grainy. Big Buck Bunny and Elephants Dream look so much better in my opinion. Oh and that is WITHOUT the HD chip driver. I will go ahead and re compile it and see if it allows VLC to work properly
Tried to compile but still no luck... 100% CPU and frames dropping a lot. I even tried using mplayer before and after compiling the drivers and libs, but it had no effect...

Maybe is some configuration on mplayer?? Or even totem, as it was compiled a gstreamer plugin.

---

### Post by Kirboosy on 2011-05-30
> **SleEpInG_GoD said:**
> :frown::frown::frown: Nothing is working in this crap...Even the commands of Grub R all mess up...I have tried trough GRUB,But the system says that The files that I am trying to call up Are not available...Man it's just annoying

Try using this instead

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbhid.quirks=0x0eef:0x725e:0x40"
```

---

### Post by SleEpInG_GoD on 2011-05-30
Nopssss...Nothing is working,I am filling so DUMB right now...I think that it's because I am running on netbook full version(2 and something GB) 64-bit 10.10 Merkel.So I will make a fresh Install of 32-bit 10.10( image 533 MB)..Than I will run the updates,maybe this will solve mine problem.

---

### Post by jamynn on 2011-05-31
> **Caboose885 said:**
> I found the problem. I noticed you didn't copy and paste because you missed a letter in the command. there is a x between the 0 and 7

it should read 0**x**725e:0x40 :)

Add the letter and rerun the update-grub command and you will be good to go


Caboose, your a G, it worked, good catch :).  The ironic part is that the same thing (missing the hex x in a command line) happened at work this week to someone else and I caught it to make the command (and therefore the whole test) work - what goes around, comes around :-P.

---

### Post by SleEpInG_GoD on 2011-06-01
S.o.s.......:(

---

### Post by InteractiveTimmy on 2011-06-02
Everything on the screen is too small, I can't figure out how to increase the DPI in 11.04 [not the text DPI, but overall screen DPI]. Help please?

---

### Post by rafael.rro on 2011-06-02
I think that for now the best option for an Inspiron Duo is 10.10... Unity is not that stable yet (needs time...) and the changes on the new kernel makes the accelerometer and the HD decoder drivers nonfunctional (needs patches...). I started with 11.04 but then rolled back...

---

### Post by JaseP on 2011-06-02
I started with Lucid & rolled forward,... but agreed... 
10.10's the "it" distro for the Duo...

---

### Post by philipvs on 2011-06-02
Thank you for being a great help. I have a brand new Inspiron Duo 1090 which is running Ubuntu 11.04. I ripped out the normal HDD and fit an SSD, and did a completely clean install of Ubuntu 11.04 64-bit. Following that I followed the instructions you provided and then loaded Florence as a virtual keyboard, and everything is working great.

---

### Post by repunante on 2011-06-02
I have read at some point that [Caboose885]("http://ubuntuforums.org/member.php?u=900617") was using Kubuntu in the Dell Duo and today I gave it a try.
Well, Kubuntu 11.04 still needs the adjusts for the touchscreen but it has the possibility to use a desktop or a netbook interface and the latter one is exactly what I was looking for. It is really really good, much better than Ubuntu for touchscreen devices.

---

### Post by JaseP on 2011-06-03
Ubuntu, Kubuntu, Xubuntu,... all just respins with a different WM. All the packages for any are available in the same repository. And, you can install the other WM & make that the default on a user-to-user basis. In-fighting between the respins is unnecessary.

---

### Post by repunante on 2011-06-03
I don't feel it like a fight, just different desktops with different aims, and I think Kubuntu suits better for touchscreen out of the box (with the grub tweak).
I didn't know about the netbook interface of Kubuntu and I just wanted to let other people know, maybe they are looking for the same thing.

---

### Post by Kirboosy on 2011-06-04
There are no fights here. He was just stating his satisfaction with Kubuntu. :) (I like Kubuntu netbook very much on the Duo.)

Recently no new updates. Haven't made any progress lately with things. :( I'm trying to get eGalax to help get multi touch working. So far they aren't very helpful

---

### Post by bikealot on 2011-06-14
> **JaseP said:**
> I started with Lucid & rolled forward,... but agreed... 
10.10's the "it" distro for the Duo...

One of the major issues I have had with 11.04 is not being able to change screen resolution.  I had someone suggest trying the 10.10 kernel with 11.04.  Well, this works. I am now able to change screen resolutions. I have not done enough investigation as to what else works or does not work with this set-up, but felt it was worth sharing.

Now, for instructions on how to install a 10.10 kernel onto 11.04...for me it took many push-ups and I frankly do not feel confident that I can accurately describe this without starting from scratch again.  So maybe there is someone you knows how to do this in a strait forward and simple manner - At the highest level, [INDENT]            * copied 10.10 kernel from 10.10 installation to /boot
           * copied /lib/modules from 10.10 installation
           * reboot
           * % sudo update-initramfs -c -k <name-of-kernel>
           * % sudo update-grub  ## note may need to reboot first
           * Hold down Shift-key during boot to get Grub, and look under "previous" kernels.[/INDENT]

---

### Post by kirangayatri20 on 2011-06-20
Hi,
 
i m a windows user and i don't have that much knowledge regarding linux version of softwares. recently i bought Dell inspiron duo. i wanna install ubuntu. i have gone through the comments of how to install and how to do the setup. but its little bit confusing to me. Please can anyone send me the proper steps to complete ubuntu for my Dell inspiron duo. 
thanks for help in advance.
 
Regards,
G.K

---

### Post by Kirboosy on 2011-06-20
> **kirangayatri20 said:**
> Hi,
 
i m a windows user and i don't have that much knowledge regarding linux version of softwares. recently i bought Dell inspiron duo. i wanna install ubuntu. i have gone through the comments of how to install and how to do the setup. but its little bit confusing to me. Please can anyone send me the proper steps to complete ubuntu for my Dell inspiron duo. 
thanks for help in advance.
 
Regards,
G.K

All the steps and information we know that are relevant for you to get started are in the very [first post]("http://ubuntuforums.org/showthread.php?t=1658635") of this thread

---

### Post by kirangayatri20 on 2011-06-21
I need a suggestion for which version of Ubuntu(10.10 or 11.04) best suits for the Dell duo and also suggest 32 bit is good or 64 bit is good.i observed in windows its showing 32 bit.

Please suggest me.

Thanks in advance for your help.

Regards,
G.K

---

### Post by Kirboosy on 2011-06-21
I would choose 10.10 right now. 11.04 doesn't seem ready yet. 

Honestly you won't notice a difference between 32 bit and 64 bit so for simplicity, 32 bit. 32 bit seemed to have larger repositories and I believe most of the people on here are using 32 bit.

---

### Post by philipvs on 2011-06-22
:p I seem to be the one odd one out that's running Ubuntu 11.04 64bit on the Dell Inspiron Duo

---

### Post by kirangayatri20 on 2011-06-22
Hi Caboose,

Thank you very much for your help.you are really amazing and awesome. i successfully done installation of ubuntu 10.10 64 bit version.Its looking cool and running very fast.

Touch working perfectly.

Multi touch is not working.

screen Auto rotation not working.

and in the youtube video i seen the left side panel which showing all the options like applications,workspaces,terminal but i m unable to see that panel.

is there any way to enable that one.

and the control buttons(close , minimize, maximize buttons) of the screen are very small to work with touch.



Regards,
G.K

---

### Post by bikealot on 2011-06-23
> **philipvs said:**
> :p I seem to be the one odd one out that's running Ubuntu 11.04 64bit on the Dell Inspiron Duo

Can you change screen resolution? To something like 1024x576

From earlier posts, the process would be ...
$ cvt 1024 576
# 1024x576 59.90 Hz (CVT 0.59M9) hsync: 35.88 kHz; pclk: 46.50 MHz
Modeline "1024x576_60.00"   46.50  1024 1064 1160 1296  576 579 584 599 -hsync +vsync


 $ xrandr --newmode  "1024x576_60.00"   46.50  1024 1064 1160 1296  576 579 584 599 -hsync +vsync
$ xrandr --addmode LVDS1 1024x576_60.00
$ xrandr --output LVDS1 --mode 1024x576_60.00

At this point on the 32bit system the screen would blank out.  Though I have found the 10.10 kernel with 11.04 does work.

Another problem is plugging in a power cord sometimes crashes Ubuntu - not always, but sometimes.

---

### Post by gjahuja on 2011-06-23
Great thread! Got (almost) everything working on my Duo thanks to you. I'm available to try possible fixes for multitouch/accelerometer/screen rotation, so if someone needs me to try some script and send output or something please contact me.

Here are my two cents:

**Enable Unity Love Handles (11.04 only)** [http://www.omgubuntu.co.uk/2011/03/unity-love-handles-resizing-in-ubuntu-just-got-sexy/]("http://www.omgubuntu.co.uk/2011/03/unity-love-handles-resizing-in-ubuntu-just-got-sexy/")

1. Install CompizConfig Settings Manager
```
sudo apt-get install ccsm
```

2. Launch ccsm, scroll all the way to the bottom and click "Unity MT Handles". Enable the plugin and add a shortcut for toggling handles on and off (I used ctrl+alt+h).

Now we need a way to toggle handles by touch input until multitouch works with the Duo:

3. Install xdotool (for sending key strokes as commands)
```
sudo apt-get install xdotool
```

4. Create a Launcher with the following command (Replace with the shortcut you used)
```
xdotool key ctrl+alt+h
```
Add it to Unity's Launcher. Clicking it will display the handles when needed.

**Toggle Launcher hiding mode (11.04 only)**

It seems most of you have scripts that run when switching to/from tablem mode by (un)folding the Duo (for unclutter, on-screen keyboard, etc.). I've found that when working in tablet mode it is annoying to access the Launcher, as it is not easy to go to the edge of the screen. Thus, one may add the following lines to the relevant script in order to change Launcher's hiding mode from "Dodge Windows" to "Never Hide".

Change hiding mode to "Never Hide" (Tablet mode)
```
gconftool-2 --type int --set /apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode 0
```

Change hiding mode to "Dodge Windows" (Netbook mode)
```
gconftool-2 --type int --set /apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode 2
```

Add the following line to /etc/gdm/PostSession/Default
```
gconftool-2 --type int --set /apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode 2
```
This is to change hiding mode to default when logging out, in case you turned off the computer in tablet mode.

If you are concerned about sacrificing screen real-state you can change icon sizes with the following command
```
gconftool-2 --type int --set /apps/compiz-1/plugins/unityshell/screen0/options/icon_size 36
```
Here you can change 36 for any integer value between 32 and 64. Of course full-screen applications (e.g. video playback) will cover the Launcher.

Finally, a question:
When rotating screen manually, half of my screen turns black and mouse/touchscreen coordinates are swapped. Any one knows where are we standing on this?

---

### Post by philipvs on 2011-06-24
> **bikealot said:**
> Can you change screen resolution? To something like 1024x576

From earlier posts, the process would be ...
$ cvt 1024 576
# 1024x576 59.90 Hz (CVT 0.59M9) hsync: 35.88 kHz; pclk: 46.50 MHz
Modeline "1024x576_60.00"   46.50  1024 1064 1160 1296  576 579 584 599 -hsync +vsync


 $ xrandr --newmode  "1024x576_60.00"   46.50  1024 1064 1160 1296  576 579 584 599 -hsync +vsync
$ xrandr --addmode LVDS1 1024x576_60.00
$ xrandr --output LVDS1 --mode 1024x576_60.00

At this point on the 32bit system the screen would blank out.  Though I have found the 10.10 kernel with 11.04 does work.

Another problem is plugging in a power cord sometimes crashes Ubuntu - not always, but sometimes.

Unfortunately the 64-bit version has precisely the same problems that you experience in the 32-bit version.

---

### Post by Kirboosy on 2011-06-24
> **bikealot said:**
> Another problem is plugging in a power cord sometimes crashes Ubuntu - not always, but sometimes.

This is the major reason why I left 11.04. It seemed that issue only was in Unity though. If I remember correctly it wouldn't crash under "Classic Gnome" (But if you aren't using Unity you might as well switch back to 10.10....right? ;) )

---

### Post by gjahuja on 2011-06-30
I just updated my system (11.04) a few minutes ago. I noticed two fixes so far:

Touch screen detected, no need to add usbhid.quirks to /etc/default/grub

(Manual) Screen rotation working, no black screen, mouse coordinates still require manual fix.

---

### Post by gjahuja on 2011-07-01
Here is the script to rotate mouse cursor:
```
#!/bin/bash
rotation=`xrandr -q --verbose|grep LVDS1|cut -b37-43`
if [ $rotation = "normal" ] ;
then
	xinput set-prop 11 137 0 1 0 1 0 0 0 0 1
	xinput set-prop 11 300 0 1
	xrandr -o left
else
	xinput set-prop 11 137 1 0 0 0 1 0 0 0 1
	xinput set-prop 11 300 0 0
	xrandr -o normal
fi
exit 0
```

---

### Post by ninjaaron on 2011-07-03
> **gjahuja said:**
> 
**Enable Unity Love Handles (11.04 only)** [http://www.omgubuntu.co.uk/2011/03/unity-love-handles-resizing-in-ubuntu-just-got-sexy/]("http://www.omgubuntu.co.uk/2011/03/unity-love-handles-resizing-in-ubuntu-just-got-sexy/")

[...]

**Toggle Launcher hiding mode (11.04 only)**

[...]


Cool ideas!  I used them both (with my own spin, naturally).

> **gjahuja said:**
> Here is the script to rotate mouse cursor:
```
#!/bin/bash
rotation=`xrandr -q --verbose|grep LVDS1|cut -b37-43`
if [ $rotation = "normal" ] ;
then
	xinput set-prop 11 137 0 1 0 1 0 0 0 0 1
	xinput set-prop 11 300 0 1
	xrandr -o left
else
	xinput set-prop 11 137 1 0 0 0 1 0 0 0 1
	xinput set-prop 11 300 0 0
	xrandr -o normal
fi
exit 0
```

I went to test this out, and before changing anything, I just did the rotation again on a whim, and the cursor tracked perfectly.

It looks like they've fixed it higher up (and it's about time)!

---

### Post by gjahuja on 2011-07-03
> **ninjaaron said:**
> 
I went to test this out, and before changing anything, I just did the rotation again on a whim, and the cursor tracked perfectly.

It looks like they've fixed it higher up (and it's about time)!

That's odd, what Ubuntu version are you using? I get screen rotation, but mouse coordinates are swapped.

Could you share how did you use love handles and stuff? I'm looking for ideas on how to improve the "tablet experience" until multitouch works.

---

### Post by ninjaaron on 2011-07-03
> **gjahuja said:**
> That's odd, what Ubuntu version are you using? I get screen rotation, but mouse coordinates are swapped. 11.04.  I dunno what could have made the difference.  It was messed up for me too before.

> Could you share how did you use love handles and stuff? I'm looking for ideas on how to improve the "tablet experience" until multitouch works.

Well, I basically did what you said for the love handles; made a desktop launcher. But then, after I made it, put it in a hidden folder where I keep all of my scripts and tweaks for the touch stuff, and dragged it into the dock from there, so now it's a dock icon.

As far as the dock hiding behaviour, I integrated it into a system of scripts I have that basically turns the cursor OFF (with the package "unclutter") and the software keyboard ON when in "tablet mode."  It also redraws the keyboard to the appropriate size and location when the screen is rotated.

I already have subscripts in there for fetching the screen orientation and mode (tablet or notebook), so I set it up to always be on when it is both in tablet mode and in landscape orientation, but to dodge when oriented in portrait (when horizontal space is at a premium) or in notebook mode.  This isn't very fancy. I don't have a way to make the system detect when the screen flips, so at this point, I'm just using a button (F12) to switch "modes."

---

### Post by gjahuja on 2011-07-03
> **ninjaaron said:**
> I don't have a way to make the system detect when the screen flips, so at this point, I'm just using a button (F12) to switch "modes."

I found a way to do this in another thread, you can read more about it here: [http://lukeross.name/dell/]("http://lukeross.name/dell/").

Add the following lines to /etc/rc.local (you need to use sudo):
```
setkeycodes e073 148 &
setkeycodes e074 149
exit 0
```

When you flip the screen and close the lid, a keystroke is sent, and when you open the lid one the screen is flipped another one is sent. Those commands maps these keystrokes to XF86LAUNCH1 and XF86LAUNCH2. rc.local runs those commands on start up so you don't need to run them at every session start.

Now open Keyboard Shortcuts and add two new shortcuts, one for Tablet Mode ON, and other one for Tablet Mode OFF, and tell them to run your scripts for each mode. Now, you can't type XF86LAUNCH# to the shortcut field, what you need to do is click it for it to become active (it will say New shortcut...) and then flip the screen and close the lid. The correct keystroke will be added. Then click to edit the other one and while it's active open the lid, you will see XF86LAUNCH2 in the shortcut field.

---

### Post by gjahuja on 2011-07-03
ninjaaron, do you have any hints on loading the accelerometer in 11.04? I would like to mess with that now. Thanks

---

### Post by ninjaaron on 2011-07-04
> **gjahuja said:**
> I found a way to do this in another thread, you can read more about it here: [http://lukeross.name/dell/]("http://lukeross.name/dell/")...
perfect! thanks!
> **gjahuja said:**
> ninjaaron, do you have any hints on loading the accelerometer in 11.04? I would like to mess with that now. Thanks

lukeross got it working for 10.10.  I'm sure he could do it for 11.04 if you can persuade him. I don't have a clue about that stuff. Sorry!:confused:

---

### Post by gjahuja on 2011-07-05
Well, I was able to build the kernel module in 11.04, unfortunately it seems to need further patching as I can load the module but it won't let me enable it. I will ask lukeross for help.

Thanks

---

### Post by groo1887 on 2011-07-06
I am trying to get the eGalax drivers to install. My touch screen works but when I run eGalaxTouch to do a calibration (after a reboot) I get "No Touch Device found"

I've tried uninstalling the eGalax driver but get a message saying that the driver is not installed. When I try to install the output of setup.sh looks like this:

```
amir@duo:~/Downloads/eGalaxTouch32$ sudo sh setup.sh 



(*) Linux driver installer for eGalaxTouch controller 

(I) Check user permission: root, you are the supervisor.
(I) Begin to setup the eGalaxTouch driver.
(I) Extract eGalaxTouch driver archive to /usr/local/eGalaxTouch32.
(I) Searching the shared library: libXfixes.so.3
(I) Create eGalaxTouch utility shortcut in /usr/bin.
(I) Create TKCal tool shortcut in /usr/bin.
(I) Check X window version: 6.9.0 ~ 7.2.0
(I) Copy X module: x69/egalax_drv.so to /usr/lib/xorg/modules/input.

(Q) Which interface controller do you use?
(I) [1] RS232 [2] PS/2 [3] USB : 3
(I) Using interface: USB
(W) Unknown: Skip to check USB type.
(I) Note that the option "SkipClick" "1" should be appended in the touch
    section of X configuration file for HID compliant touch controller.
    Besides, if the using touch controller is non-HID compliant controller,
    the option "Device" "/dev/input/mice" for mouse should be changed to
    "Device" "/dev/input/mouseX" to prevent the mouse driver from reading.
(I) For details, see the document "Driver Guide.pdf".

(I) Removed eGalaxTouch driver archive from /usr/local/eGalaxTouch32.
(I) Removed eGalaxTouch utility shortcut.
(I) Removed TKCal tool shortcut.
(I) Removed X module.
(E) No X configuration file found
```

Looks like the script is failing to recognize the USB device output of my lsusb looks like this:

```
amir@duo:~/Downloads/eGalaxTouch32$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0cf3:3002 Atheros Communications, Inc. 
Bus 004 Device 002: ID 0eef:725e D-WAV Scientific Co., Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:58f4 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
amir@duo:~/Downloads/eGalaxTouch32$
``` 

The following line is in my /etc/default/grub
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbhid.quirks=0x0eef:0x725e:0x40"
```

Any help appreciated

---

### Post by gjahuja on 2011-07-06
Try installing xinput-calibrator

---

### Post by groo1887 on 2011-07-07
Thanks gjahuja that worked for me. Didn't realize that the eGalax drivers weren't needed for 11.04. Works swell now.

---

### Post by sasquadge on 2011-07-07
Hey guys I'm having a real problem here. I downloaded the ubermix 10.10 first off is this correct? and is there a link better for this? or should I just be using the main Ubuntu software not the ubermix netbook stuff? Also I do the updates as listed on page one but i get a error on second step and never works and wont let me continue. also I cant watch youtube videos? if you guys could help would be greatly appreciated.

---

### Post by joey-elijah on 2011-07-07
> **groo1887 said:**
> Thanks gjahuja that worked for me. Didn't realize that the eGalax drivers weren't needed for 11.04. Works swell now.

Multi-touch or no?

---

### Post by mokolo on 2011-07-07
> **joey-elijah said:**
> Multi-touch or no?

No multi-touch

---

### Post by ninjaaron on 2011-07-07
Testing Oneric Alpha 2 right now.  The usbhid.quirks thing doesn't work here.The touch input all goes to the top left corner like in 10.10. Don't have a fix for it yet.

The touchpad is automatically recognized and two finger scrolling can be enabled out of box.

Everything else is the same as before as far as the duo is concerned.

*edit:*  By that I mean that Bluetooth works, just like it always did for me.

---

### Post by Kirboosy on 2011-07-07
> **joey-elijah said:**
> Multi-touch or no?

Multi touch is the biggest hindrance right now. Sad thing is the manufacturer isn't willing to help us.

---

### Post by Kirboosy on 2011-07-07
Ok so I found this guide for setting up 10.10 for egalax touchscreen. So far I'm unable to get it to work right but I figured the more people I have trying it the better chance we have at getting it to work.

[http://samiux.blogspot.com/2010/11/howto-ubuntu-1010-on-gigabyte-touchnote.html](http://samiux.blogspot.com/2010/11/howto-ubuntu-1010-on-gigabyte-touchnote.html)

I would recommend trying it on a clean install. I have a feeling the reason its not working properly for me is because I already have the Egalax Driver controlling my screen.

Good luck to everyone

---

### Post by ninjaaron on 2011-07-08
I think the screen might be a different model on that guy's machine... either that, or he doesn't have multitouch either and he doesn't know he should. Check it out:

> Step 7 (Optional) :

Get uTouch (Multi-touch). However, **this netbook does not support multi-touch.** The following procedure does not causing harm to your system anyway.


---

### Post by Kirboosy on 2011-07-10
> **ninjaaron said:**
> I think the screen might be a different model on that guy's machine... either that, or he doesn't have multitouch either and he doesn't know he should. Check it out:

I think he is implying that Multi-touch should work but it doesn't on his because of hardware limitations. (Thats the only reason I can figure why he would add the multi-touch part)

---

### Post by ninjaaron on 2011-07-11
> **Caboose885 said:**
> I think he is implying that Multi-touch should work but it doesn't on his because of hardware limitations. (Thats the only reason I can figure why he would add the multi-touch part)

I'm not really a computer guy per se, but if he has the same screen, doesn't that mean there is no hardware limitation?  It seems to me that if he does have the same screen but has never had multi-touch, it is because his computer probably came with Windows 7 Starter, which doesn't have software support for multi-touch... just like Ubuntu... still...

---

### Post by gjahuja on 2011-07-12
I tried the solution, but it didn't work. I think he has a different display model as the identifier used for usbquirks is different than the one used for the Duo.

---

### Post by raphaelsaldanha on 2011-07-13
Hi guys,
 
I had received my Duo from two or three months ago and had planned to migrate o Linux before the purchase.
 
I'm still surving with Windows 'till now, and I'm following the advances on this forum.
 
But I'm really tired with Windows. So, I aks: is this the right time to migrate? If so, wich version 10.04 or 11.04 ?
 
Thanks in advance!
 
Raphael Saldanha
Brazil

---

### Post by Kirboosy on 2011-07-14
> **raphaelsaldanha said:**
> Hi guys,
 
I had received my Duo from two or three months ago and had planned to migrate o Linux before the purchase.
 
I'm still surving with Windows 'till now, and I'm following the advances on this forum.
 
But I'm really tired with Windows. So, I aks: is this the right time to migrate? If so, wich version 10.04 or 11.04 ?
 
Thanks in advance!
 
Raphael Saldanha
Brazil

Anytime is a good time to migrate to Ubuntu ;)

Seriously though, I use Ubuntu all the time even though I can't fully utilze my Duo features. The only big thing you will be missing with the Duo and Ubuntu is multi-touch. If that doesn't bother you then go right on ahead and install Ubuntu. (I recommend dual-booting 10.04 and Windows)

---

### Post by w1ll1am on 2011-07-14
I think that dual booting would be a great idea but I think that you should dual boot 10.10 and windows. We have made more progress with 10.10 than we have 10.04 at least that I am aware of.

---

### Post by nm_geo on 2011-07-14
> **raphaelsaldanha said:**
> Hi guys,
 
I had received my Duo from two or three months ago and had planned to migrate o Linux before the purchase.
 
I'm still surving with Windows 'till now, and I'm following the advances on this forum.
 
But I'm really tired with Windows. So, I aks: is this the right time to migrate? If so, wich version 10.04 or 11.04 ?
 
Thanks in advance!
 
Raphael Saldanha
Brazil

Depends on what you want to do.  Here is a thought 10.04 is very stable and will be supported until April 2013.  Maverick 10.10 is also a pretty stable version but support will end April 2012.. 

Here's another thought install both and triple boot.. Or do like me and spend hours each day updating 7 or 8 flavors.   I just like to see where Ubuntu is headed and my main operating version is still Lucid 10.04,,

One other thing to consider Gnome 2 is fast becoming history.. So you will have Unity or Gnome 3 in the future.

Too many things to consider I know.. In the end ..I recommend Lucid 10.04 to learn on.

---

### Post by raphaelsaldanha on 2011-07-16
Hey! Thanks for the answers. A question: is the Dock working good (sound and usb at least)? In both versions?
 
Thanks!

---

### Post by Samatva on 2011-07-16
> **raphaelsaldanha said:**
> Hey! Thanks for the answers. A question: is the Dock working good (sound and usb at least)? In both versions?
 
Thanks!
The dock has always worked, speakers, USB and network, with my install of 11.04 - except... it won't automatically switch to WiFi when you pull it out of the dock - I just have to go in and disable the hardwired network port.

---

### Post by raphaelsaldanha on 2011-07-17
Running Ubuntu 10.04 LTS !!! Thanks for the help and advices my friends :o

I have run all the tips on the first thread and every thing is going ok. 

EDIT: not everyhing... I have only have sound when docked, or when undocked witjh earphones. I don't have sound undocked without earphones. Any help?

I would like to have some help about the virtual keyboard. In the tablet mode, how can I call the virtual keyboard? I have read on this thread about the florence. I tried to install it but have some packages missing in the ./config process. Can anyone help me?

Thanks!

---

### Post by Kirboosy on 2011-07-17
> **raphaelsaldanha said:**
> I have only have sound when docked, or when undocked witjh earphones. I don't have sound undocked without earphones. Any help?

You should try changing the output device in the sound manager. If its outputting to the dock speakers then it will ignore your headphones.

> 
I would like to have some help about the virtual keyboard. In the tablet mode, how can I call the virtual keyboard? I have read on this thread about the florence. I tried to install it but have some packages missing in the ./config process. Can anyone help me?

Have you looked at the [install page?]("http://florence.sourceforge.net/english/install.html") (control + F will help you find the Ubuntu install instructions.)

---

### Post by raphaelsaldanha on 2011-07-18
Hi Caboose,

**Audio**: I've tried that, but without success. The situation is: I turn on the Duo without headphones and without dock, and Ubuntu starts. No sound. When I go to the output device configuration, the internal speakers are selected, but no sound...

**Keyboard**: Sorry, I don't have seen this page. I tried to follow the 'Install' text inside the archive, but this page is much better. Thanks! 

Thanks for the attention!

EDIT: Florence working! Thanks!!! Still need help with the sound...

---

### Post by Kirboosy on 2011-07-20
> **raphaelsaldanha said:**
> **Audio**: I've tried that, but without success. The situation is: I turn on the Duo without headphones and without dock, and Ubuntu starts. No sound. When I go to the output device configuration, the internal speakers are selected, but no sound...

Try removing that line we added from the /etc/modprobe.d/alsa-base.conf and reboot. 
See if your sound returns. (It will most likely "break" your headphone jack)

---

### Post by Cammaaron on 2011-07-23
How can I increase the size of the scroll bar (for non-firefox program) and buttons so they are more touch-friendly.

---

### Post by raphaelsaldanha on 2011-07-25
Hi Caboose,

I'm running the file without the modifications, but no sound. On the first login, I had o sound either. 

I put attached my alsa-base conf file.

Thanks for the help!

---

### Post by raphaelsaldanha on 2011-07-26
> **Cammaaron said:**
> How can I increase the size of the scroll bar (for non-firefox program) and buttons so they are more touch-friendly.

Hi Cammaaron,

I think that is possible changing the theme of Ubuntu. I have a good experience increasing the size of the fonts. Here is a good tutorial about appearance in Ubuntu: [http://www.wawuk.net/book/export/html/33](http://www.wawuk.net/book/export/html/33)

---

### Post by raphaelsaldanha on 2011-07-28
Hi Caboose,

Advances with the sound problem! I was using the 10.04 LTS, and having these difficulties with the sound. So, yesterday, I have upgraded to 10.10. On the first boot, the sound was alive!

I don't have time yet to test the modifications on the alsa file, earphones and etc, but I will test it soon.

Thanks!! I'm loving Ubuntu :-)

---

### Post by ninjaaron on 2011-07-30
We were talking about meego a while back.  There are fixes now to activate the touchscreen, for anyone interested. It's the same fix we're using, but with a different bootloader.

[This thread]("http://forum.meego.com/showthread.php?t=3009&highlight=usbhid") explains how to get it working on a system that uses meego's bootloader.

If you want to boot it using Ubuntu's GRUB, you need to create a custom menu entry with the usbhid.quirks thing in that entry, which is explained [here]("https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries").  The Meego UI is, overall, an excellent fit for the duo.  There is still difficulty for me getting the virtual keyboard to work.  There is an excellent virtual keyboard in the repos for the meego handhelds, but I haven't managed to pull it in (may be because I'm using netbook version 1.2, and the handset version is still on 1.1 and has a different kernel).

---

### Post by ninjaaron on 2011-07-30
Touchscreen is working in 11.10

Still no multitouch :mad:

---

### Post by Kirboosy on 2011-07-30
> **ninjaaron said:**
> Touchscreen is working in 11.10

Still no multitouch :mad:

Lack of multi touch makes me sad. :'( Only weakness of running Ubuntu on my Duo.

---

### Post by ninjaaron on 2011-07-31
> **Caboose885 said:**
> Lack of multi touch makes me sad. :'( Only weakness of running Ubuntu on my Duo.

Well, I found something that ought to make you happy today (no, not multitouch, sorry).

Found a package in universe called [FONT="Courier New"]easystroke[/FONT] (yes, someone actually thought that was a good name for a program).  It links user-defined gestures with user-defined actions... can be shell commands (including scripts), key combinations, and various other actions.

IT IS WONDERFUL!!

So far, I've got gestures for closing, minimising, and fullscreening windows, activating compiz's new "love handles," showing all windows (the Super+w thing), calling the keyboard, clockwise and counter-clockwise rotations, and scrolling.

It really is wonderful.  This is the ideal solution for single-touch tablet PC.  I finally feel like my custom UI is done.  It's a good feeling.
:guitar:

---

### Post by U875 on 2011-08-04
Good morning to all,

Firstly, thanks for the effort to educate the people how they can configure the Duo to make it usable with ubuntu and the touch screen. 
I followed the article too at [http://ubuntuforums.org/showthread.php?t=1658635](http://ubuntuforums.org/showthread.php?t=1658635), but instead of using the new unity desktop I preferred to keep the "computer mode" of the duo active and just mak more user friendly interface for the touch screen (i.e. to marry the computer philosophy with a lot of capabilities with the nice human-machine interface that one sees on ipads....). That briefly means that I made extensive use of the awn bar on the left, a lot of programmes as icons defined on workspace (both of them for the typical usage of the laptop/tablet), increased size of task bars and menus (so fingures capture them easier), simple defined applets (so when the laptop rotates they are not too close), and even a "kill" button if anythings hangs...etc.

A few items though did not work as hoped and I was wondering if any one out there has found any configuration trick that he could share for the following:

1) I prefer desktop wall and rotating cube enabled but although with the mouse (in a computer mode) a window is sliding to the next workspace when pushed to the edge, using the touch screen this does not happen :(. That is, a finger pushing a window to the edge does not result to a rotating cube change. So, how can someone make the cube rotate when a window is being carried across from one worskpace to another?

2) One of the basic things we use with a mouse is a "right click" to create folders, check properties etc. Is there any way to have a "right-click" capability with the touch screen? (without using the on-screen keyboard)

3) When using the touch screen, scrolling requires the fingure to accurately grab the scroll bar to pull a doc down - for all document types. This make its use difficult. It would be more appropriate to have the cursor scrolling down a doc as long as the document is not editable and have an "edi mode button" somewhere defined if some text needed to be marked or edited. The ipad's philosophy popping up the on-board keyboard when in "editing mode" is a good idea. All we have is to figure out how to do it....
In addition, the size of the keyboard is not appropriate at the moment. If and when the gyroscopic sensor use gets sorted I feel it would be useful to have the onboard keyboard invoked with a size adjusted to the size of the screen. 

4) The 2-finger zoom does not work for me either. Couldn't get it working at the moment:(. 

If any one of the community has some more tipe to play with these features and get some results, I would kindly ask to drop us anote in the forum. It would help a great deal. 

Best regards

Alex

---

### Post by raphaelsaldanha on 2011-08-04
Hi Alex,

About the right click, you just need touch and maintain the touch for about 3 or 4 seconds, and the menu appears.

Can you share you us, with more details, all the improvements you have made? 

Raphael

---

### Post by ninjaaron on 2011-08-04
> **raphaelsaldanha said:**
> Hi Alex,

About the right click, you just need touch and maintain the touch for about 3 or 4 seconds, and the menu appears.

Can you share you us, with more details, all the improvements you have made? 

Raphael

You have to enable it first in the mouse>accessibility dialogue, and it's glitchy in 11.04. You can create a gesture for it in easytouch, however.

As for getting the screen to flip... hmmm... let me check...
***

nope... according to configuration editor (gconf), there is supposed to be an option that allows you to change where the screen edge begins and end in the future, but it's not implemented yet... let me verify that on google...
***
nope, doesn't look like it.

[http://forum.compiz.org/viewtopic.php?t=6885]("http://forum.compiz.org/viewtopic.php?t=6885").

---

### Post by Cammaaron on 2011-08-07
I am curious.

As anyone looked in why the touchscreen multi-touch does not work?
Isn't there a way to comparing what data is being sent from the touchscreen between linux and windows and seeing how it being sent through the kernel for its touchscreen support.

---

### Post by w1ll1am on 2011-08-08
> **ninjaaron said:**
> Well, I found something that ought to make you happy today (no, not multitouch, sorry).

Found a package in universe called [FONT=Courier New]easystroke[/FONT] (yes, someone actually thought that was a good name for a program).  It links user-defined gestures with user-defined actions... can be shell commands (including scripts), key combinations, and various other actions.

IT IS WONDERFUL!!

So far, I've got gestures for closing, minimising, and fullscreening windows, activating compiz's new "love handles," showing all windows (the Super+w thing), calling the keyboard, clockwise and counter-clockwise rotations, and scrolling.

It really is wonderful.  This is the ideal solution for single-touch tablet PC.  I finally feel like my custom UI is done.  It's a good feeling.
:guitar:


this makes me want to use my duo again. i have not used it in so long because without multitouch its almost pointless. thanks for finding it. great job

---

### Post by ninjaaron on 2011-08-08
> **Cammaaron said:**
> I am curious.

As anyone looked in why the touchscreen multi-touch does not work?
Isn't there a way to comparing what data is being sent from the touchscreen between linux and windows and seeing how it being sent through the kernel for its touchscreen support.

I looked at some of that stuff in the beginning. I can't remember the exactly what the program is, but it's something about an xinput prober.  It seems like it was registering multiple input ports from the screen, but it was like 3 or 4 of them, and I think we somehow decided that the presence of all those extra inputs was confusing X, since none of them do anything except the one... I don't remember exactly, but I know the X server was expecting multiple inputs for this device, but it wouldn't read them for some reason.

That makes me wonder if an input stack based on GEM or something would read the inputs correctly.  I hear stack through which X processes multitouch input is incredibly convoluted (I actually watched a really nice video lecture by one of the head guys at xorg talking about how much X sucks and he can't wait for new frameworks to supersede it).

edit: found the weird thing I was talking about.
if you run [FONT="Comic Sans MS"]xinput list[/FONT], you get this in the pointer section:
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; eGalax Inc. USB TouchController         	id=10	[slave  pointer  (2)]
&#9116;   &#8627; eGalax Inc. USB TouchController         	id=11	[slave  pointer  (2)]
&#9116;   &#8627; eGalax Inc. USB TouchController         	id=12	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=15	[slave  pointer  (2)]

```

I don't know if it should be reading one or two from the screen, but three is too many. Something fishy about it.

It got me working on the multitouch again.  No success, but I did somehow manage to enable pinch zooming on the touchpad in the process.  You can get it if you add the utouch team repository and update.  This does some weird things to the scrolling however, so I'm not going to post instructions.  Google is at the disposal of those who would like to try it.

---

### Post by ludovicus on 2011-08-08
Greetings New owners of Dell Duo, (~24 hours)
I have played with Old School Gnome, 2d unity and 3d unity.

Read through most of the postings and I am having issues installing the last theme that ninjaaron posted, plus scripts.
Could you please point out a page on how you installed the scripts and what you did to install the theme.  (i have been googling but hey if you point me in the right direction i'll detail step by step notes)  I think a majority of my issues with it being a usable tablet has to do with theme'ng and some shortcuts to flip screen and landscape/portrait, quick suspend, quick record audio (audacity), and a keyboard popup.

has anyone gotten a keyboard to showup when the screen locks?  (during screensaver?)
 
has anyone had kernel panic issues when removing or adding the power adapter?  (has happened several times already)

Bought this as a returned and discounted item at tigerdirect and it works fine as a netbook... but i want it to be a productivity tool at work.

Hamster-indicator--works, would like larger icons though.
ubuntuone/dropbox--works great
cisco vpn/citrix--works great
networking-awesome, (it's linux!)

what other productivity apps have you all customized to get working?

having fun but it's half baked right now.  I officially have no desire to use an iPAD anymore because the productivity tools aren't really useful and the fact i have to use iTunes everytime i want to move a file is overthetop.


-L-:P:P

---

### Post by w1ll1am on 2011-08-09
> **ludovicus said:**
> Greetings New owners of Dell Duo, (~24 hours)
I have played with Old School Gnome, 2d unity and 3d unity.

Read through most of the postings and I am having issues installing the last theme that ninjaaron posted, plus scripts.
Could you please point out a page on how you installed the scripts and what you did to install the theme.  (i have been googling but hey if you point me in the right direction i'll detail step by step notes)  I think a majority of my issues with it being a usable tablet has to do with theme'ng and some shortcuts to flip screen and landscape/portrait, quick suspend, quick record audio (audacity), and a keyboard popup.

has anyone gotten a keyboard to showup when the screen locks?  (during screensaver?)
 
has anyone had kernel panic issues when removing or adding the power adapter?  (has happened several times already)

Bought this as a returned and discounted item at tigerdirect and it works fine as a netbook... but i want it to be a productivity tool at work.

Hamster-indicator--works, would like larger icons though.
ubuntuone/dropbox--works great
cisco vpn/citrix--works great
networking-awesome, (it's linux!)

what other productivity apps have you all customized to get working?

having fun but it's half baked right now.  I officially have no desire to use an iPAD anymore because the productivity tools aren't really useful and the fact i have to use iTunes everytime i want to move a file is overthetop.


-L-:P:P

I have also had problems installing the themes that I made after a re-install they are tricky for some reason. All I remember is having to extract the folder and then moving it to usr/share/themes and making sure it has the right permissions. 

What keyboard are you using? If you are using onboard it has an option to enable at screen saver. 

I had the kernel panics for like two days and I have not had them since I am not sure what caused it to stop though. let us know it if keeps happening.  

Hope this helps. Have you tried easystroke yet? It really helps with the lack of multi-touch

---

### Post by ninjaaron on 2011-08-09
> **ludovicus said:**
> Greetings New owners of Dell Duo, (~24 hours)
I have played with Old School Gnome, 2d unity and 3d unity.

Read through most of the postings and I am having issues installing the last theme that ninjaaron posted, plus scripts.
Could you please point out a page on how you installed the scripts and what you did to install the theme.  (i have been googling but hey if you point me in the right direction i'll detail step by step notes)  I think a majority of my issues with it being a usable tablet has to do with theme'ng and some shortcuts to flip screen and landscape/portrait, quick suspend, quick record audio (audacity), and a keyboard popup.

has anyone gotten a keyboard to showup when the screen locks?  (during screensaver?)
 
has anyone had kernel panic issues when removing or adding the power adapter?  (has happened several times already)

Bought this as a returned and discounted item at tigerdirect and it works fine as a netbook... but i want it to be a productivity tool at work.

Hamster-indicator--works, would like larger icons though.
ubuntuone/dropbox--works great
cisco vpn/citrix--works great
networking-awesome, (it's linux!)

what other productivity apps have you all customized to get working?

having fun but it's half baked right now.  I officially have no desire to use an iPAD anymore because the productivity tools aren't really useful and the fact i have to use iTunes everytime i want to move a file is overthetop.


-L-:P:P

Well, I'm using easytouch gestures now for window controls (you should definitely install easytouch right now!), so I'm not using a special theme anyomre, and the scripts have changed dramatically since I originally posted them since I discovered easytouch and we found out how to get input from flipping the screen (and just adding some ideas that I had.).  I can post the new scripts and instructions some time later this week.  Some of the new changes aren't integrated with the settings file yet.  I really need to find a way to build a GUI for the settings file, but I'm not a programmer, and I have no clue where to start with that. (the script to toggle the screen rotation was the first script I had ever written, and it's sort of escalated from there... don't get caught up in bash and cli any more than you can help... can't tell you how many hours of my life are lost...)

---

### Post by ninjaaron on 2011-08-09
> **w1ll1am said:**
> It really helps with the lack of multi-touch

Totally. For me, easystroke is, like, THE gamechanger.  I have something like 35 gestures now.

---

### Post by ludovicus on 2011-08-09
Thanks for the quick reply!

Have you all been to this site?

UberMix
[http://community.saugususd.org/swattec/page/1+-+Overview](http://community.saugususd.org/swattec/page/1+-+Overview)

Downloads:
[http://community.saugususd.org/swattec/page/Download+Files](http://community.saugususd.org/swattec/page/Download+Files)

There is a popular youtube demo:
[http://blog.mypapit.net/2011/07/dell-inspiron-duo-table-notebook-running-ubuntu.html](http://blog.mypapit.net/2011/07/dell-inspiron-duo-table-notebook-running-ubuntu.html)

on this site that I believe is using UberMix

I believe there might be a good point of reference if you all doing research on how to best use your Dell Duo.  (Scripts or otherwise)

Has anyone configured X11 for multi-touch?  It's been years since i had to fiddle with xorg configuration settings?

I'll try the permissions settings again tonight but most likely i'll be installing UberMix.  
Will give feedback tomorrow.
-L-

---

### Post by ludovicus on 2011-08-09
Ubuntu Peeps.

[http://www.lii-enac.fr/en/architecture/linux-input/index.html#xorg](http://www.lii-enac.fr/en/architecture/linux-input/index.html#xorg)

have you all been following this?  
Do we have a page or discussion forum on research?  is this in the ubuntu wiki?
-L-

---

### Post by ninjaaron on 2011-08-10
> **ludovicus said:**
> Thanks for the quick reply!

Have you all been to this site?

UberMix
[http://community.saugususd.org/swattec/page/1+-+Overview](http://community.saugususd.org/swattec/page/1+-+Overview)

Downloads:
[http://community.saugususd.org/swattec/page/Download+Files](http://community.saugususd.org/swattec/page/Download+Files)

There is a popular youtube demo:
[http://blog.mypapit.net/2011/07/dell-inspiron-duo-table-notebook-running-ubuntu.html](http://blog.mypapit.net/2011/07/dell-inspiron-duo-table-notebook-running-ubuntu.html)

on this site that I believe is using UberMix

I believe there might be a good point of reference if you all doing research on how to best use your Dell Duo.  (Scripts or otherwise)I looks interesting, but more for those who just want something that works well on a fresh install.  I change everything anyway when I install a new OS (and my post-install scripts assume they are working on Ubuntu), so I'm not sure it would be helpful for me.

> Has anyone configured X11 for multi-touch?  It's been years since i had to fiddle with xorg configuration settings?Yes. Over and over.  The multitouch works fine on the touchpad (with a tiny bit of setup). This is a problem specific to the eGalax USB touchscreen that comes on the Duo.

> I'll try the permissions settings again tonight but most likely i'll be installing UberMix.  
Will give feedback tomorrow.
-L-
You can also just drop any theme folder into ~/.themes.  It's a hidden folder, so you would need to hit ctrl+h in your home folder to see it.  Drop the folder in there.  The them I made isn't complete in itself, however.  You go to "appearance," select a theme, and then go to customize, where you can select "window borders and titles" or something, and you can select any metacity theme you like.

Scripts should be ready in a a couple of days.  They work fine for me already, but I'm doing some minor maintenance on the code (getting to run a little smarter.  The scripts are tiny, so it's already fast, but it's the principle of the thing).  I'm also adding more controls for user-defined settings.

Just for you, I'm going to write an install script so all you have to do is run it, answer a few questions, then all dependencies will install, all the files will be in the right place, and the system should basically work.  You will still have to link some of the scripts to launchers or gestures yourself, however.

---

### Post by ludovicus on 2011-08-11
has anyone used Jupiter?

it was a utility installed in the [http://community.saugususd.org/swatt...e/1+-+Overview](http://community.saugususd.org/swatt...e/1+-+Overview)  version of UNE, aka ubermix.

If you install the "ubermix" flavor in a VM one could improve their setup.  I want to ask permission to share what is inside, as it's really well done before I post here.  

But don't take my word for it, it's in the image posted on the site.

I agree, i decided to uninstall ubermix and try to play with default ubuntu.

so far, day 5.  5 installs, natty, uber, natty, oneiric, and now back to natty. :)

-L-

---

### Post by ludovicus on 2011-08-12
ok, i have install uTouch.  now where do you configure all the multitouch gestures?

I played around with the debug display but not dice on usability.

Ninjaaron.  how exactly did you configure gestures with 'easy touch'.. is this a package in the ubuntu repository?  is there a PPA?
-L-

---

### Post by ninjaaron on 2011-08-14
> **ludovicus said:**
> ok, i have install uTouch.  now where do you configure all the multitouch gestures?

I played around with the debug display but not dice on usability.

Ninjaaron.  how exactly did you configure gestures with 'easy touch'.. is this a package in the ubuntu repository?  is there a PPA?
-L-

I'm not sure how I got the multitouch gestures working in uTouch.  There is a thread about the EeePc somewhere on these forums, and some guy recently got it's touchsreen working (it's near the end of the thread), so I though I would try to follow his instructions to see if the screen would for me.  It didn't work, but about half-way through, I had pinch to zoom on the touchpad.  I didn't cnofigure anything, I just installed a bunch of packages from the tutorial.  The two-finger scrolling in Firefox, however, became very erratic, so I took it off with ppa-purge, and I had to remove some of packages manually.  I don't recommend the experience.  It only works with certain programs anyway, like evince (document viewer) and eog (image viewer).  uTouch is still very much in development, and it won't do anything for our screen anyway until certain hardware issues are solved, for we would probably need the help of a kernel programmer and/or people from eGalax.

easytouch (one word) is in the repository. You can search for it in the software-center or [FONT="Courier New"]sudo apt-get install easytouch[/FONT].  You have to turn it on twice to get the config screen.  The actual configuration is pretty self-explanitory: name the action, select a type (button combo, shell command, etc...) define the action, and create the gesture.  It works beautifully.

The code for the scripts is all where I want it now, but I'm re-documenting a couple of things, and then I have to create the install script, but that *should* be pretty strait-forward.  I may finish it today.

---

### Post by ninjaaron on 2011-08-14
> **ludovicus said:**
> ok, i have install uTouch.  now where do you configure all the multitouch gestures?

I played around with the debug display but not dice on usability.

Ninjaaron.  how exactly did you configure gestures with 'easy touch'.. is this a package in the ubuntu repository?  is there a PPA?
-L-

I'm not sure how I got the multitouch gestures working in uTouch.  There is a thread about the EeePc somewhere on these forums, and some guy recently got it's touchsreen working (it's near the end of the thread), so I though I would try to follow his instructions to see if the screen would for me.  It didn't work, but about half-way through, I had pinch to zoom on the touchpad.  I didn't cnofigure anything, I just installed a bunch of packages from the tutorial.  The two-finger scrolling in Firefox, however, became very erratic, so I took it off with ppa-purge, and I had to remove some of packages manually.  I don't recommend the experience.  It only works with certain programs anyway, like evince (document viewer) and eog (image viewer).  uTouch is still very much in development, and it won't do anything for our screen anyway until certain hardware issues are solved, for we would probably need the help of a kernel programmer and/or people from eGalax.

easytouch (one word) is in the repository. You can search for it in the software-center or [FONT="Courier New"]sudo apt-get install easytouch[/FONT].  You have to turn it on twice to get the config screen.  The actual configuration is pretty self-explanitory: name the action, select a type (button combo, shell command, etc...) define the action, and create the gesture.  It works beautifully.

The code for the scripts is all where I want it now, but I'm re-documenting a couple of things, and then I have to create the install script, but that *should* be pretty strait-forward.  I may finish it today.  No promises.

---

### Post by beastrace91 on 2011-08-23
Howdy All,

Just picked one of these little guys up and I'd just like to say thanks for the HOWTO for getting the screen working with that grub line.

I'd just like to ask if anyone round these parts has figured out a method of detecting when the duo is put into "tablet" mode. 

EG: I'd like to fire a custom command or two when I flip the screen around and close the lid.

Anyone know if this is possible/figured out yet?

~Jeff

---

### Post by JaseP on 2011-08-25
Check here:

[http://ubuntuforums.org/showthread.php?t=1658480](http://ubuntuforums.org/showthread.php?t=1658480)

---

### Post by raphaelsaldanha on 2011-08-26
Hi guys,

How are our expectations about 11.10 Oneiric Lancelot? Any tests with the multi-touch, Unity and etc?

---

### Post by beastrace91 on 2011-08-26
Multi Touch on the trackpad works OOTB on the latest kernel, the screen is still single touch though. 

As far as unity goes - I didn't realize people actually used that trash. Although it does look like it was designed for a touch screen phone, so maybe the duo isn't a bad fit for it.

~Jeff

---

### Post by ninjaaron on 2011-08-26
Let's not start that here.

---

### Post by w1ll1am on 2011-09-02
Has anyone tried the beta yet? I am really really hoping for multi-touch this release.

---

### Post by ninjaaron on 2011-09-02
> **w1ll1am said:**
> Has anyone tried the beta yet? I am really really hoping for multi-touch this release.

I haven't tried it yet, but I wouldn't be too optimistic.  It's the same kernel as the alpha, and it didn't work there either.

---

### Post by Kirboosy on 2011-09-04
Unless one of the developers specifically targeted our Duo I don't think we will see multi touch anytime soon. (I'm back from the dead. ;) )

---

### Post by Zephonim on 2011-09-04
Hello all,

Fantastic job on this. It was a great read. Can't wait to get my Duo up and running Ubuntu.

---

### Post by Kirboosy on 2011-09-05
Ok so I just installed Ubuntu 11.04 back on my Duo. The touchscreen drivers finally support 11.04 and its much easier. I was going to take the GRUB method out of the setup guide.

Is anyone against this?

---

### Post by senor_smile on 2011-09-05
> **Caboose885 said:**
> Ok so I just installed Ubuntu 11.04 back on my Duo. The touchscreen drivers finally support 11.04 and its much easier. I was going to take the GRUB method out of the setup guide.

Is anyone against this?

Thanks for the guide.  I haven't run Ubuntu since Unity took over gnome, but decided to give it a try with my new dell inspiron duo.  I installed 11.10 beta.  The touchscreen worked out of the box until I updated.  I had to apply the grub addition to fix it.  It also seems to be crashing quite a bit.  I hope the final release is a bit more stable.

---

### Post by ninjaaron on 2011-09-06
> **Caboose885 said:**
> Ok so I just installed Ubuntu 11.04 back on my Duo. The touchscreen drivers finally support 11.04 and its much easier. I was going to take the GRUB method out of the setup guide.

Is anyone against this?

Let's hold off on that until we get a confirmation.  Besides, we may still need it in 11.10

But so long as we are talking about editing the original post, you might want to add something about easytouch and the way to get the computer to recognize a screen flip.  I consider both of those things significant breakthroughs for the duo.

---

### Post by ninjaaron on 2011-09-06
> **senor_smile said:**
> I installed 11.10 beta [...] It also seems to be crashing quite a bit.  I hope the final release is a bit more stable.

That's kind of the point of a development cycle.

---

### Post by Kirboosy on 2011-09-06
One of the issues with the Duo is lack of an ethernet port. (Unless you have a dock.) I have a dock but I'm not going to carry it around with me from job to job because its too big. I found a very inexpensive [USB to 10/100 RJ45 adapter]("http://www.dealextreme.com/p/usb-10-100-rj45-ethernet-network-adapter-dongle-2797") that works beautifully. Its much cheaper than spending $100 (USA at least) on a dock just for ethernet. 

It takes zero configuration. I just simply plug it in and Ubuntu knows what to do with it.

---

### Post by ehofman on 2011-09-06
Thanks for this great guide. I'm flowing this from the first post. Got my duo in January. Still working with ubuntu 10.10 and 2d unity. I'm really happy with this setup. I bought the audio station with my duo and works perfect except for the network card. It works if you boot the duo in the dock, but after some time, it just stops working. 

I bought this one: [http://www.dealextreme.com/p/usb-2-0-10-100mbps-rj45-lan-ethernet-network-adapter-dongle-34691](http://www.dealextreme.com/p/usb-2-0-10-100mbps-rj45-lan-ethernet-network-adapter-dongle-34691)

It comes with linux drivers and they work, but are a little old. Performance is good and it has a short cable attached, so you don't mess up your usb port. They get hot, but keep working all day if you want.

Finaly, keep up the good work, i love reading this topic. Hope to see multi-touch soon.

---

### Post by Kirboosy on 2011-09-06
Would anyone here like to test out my Broadcom Crystal HD Decoder install script? 

I know its very rough but it got the job done on mine and I figured it might be somewhat useful for others... If you see any errors let me know and I will fix them.

---

### Post by Kirboosy on 2011-09-06
Oh, also I'm trying to get the flip detection on my Duo working. I modified the rotate script by adding zenity to have a box come up that simply says "Rotate the Screen?" with Yes or No buttons.

By binding to the screen flip we should be able to have a nice little pop up when we put the screen into tablet mode. Then bind another script that rotates the screen back to normal when exiting tablet mode. (it doesn't ask though it just forces it back to 'normal mode' automatically)

---

### Post by ludovicus on 2011-09-07
using ubuntu 11.04 Oneiric Ocelot alpha 3, is working pretty good for me finally.  it's been two weeks of struggle and it appears to beginning plateau to a stable environment.

there were constant unity issues, and quite a few prob with all the applets i had running.

power management is much better, and i'm hoping to see more improvements with driver support.  

Work was crazy for 2 weeks, now getting back into play mode.

---

### Post by ludovicus on 2011-09-07
broadcom script is working fine.

---

### Post by senor_smile on 2011-09-07
So, I was having many problems with 11.10.  I decided to try out Fedora 15 with gnome 3.  Gnome 3 is VERY well suited to this sort of a device.  I realize this isn't a Fedora forum, but there seem to be no posts about this device on the Fedora forums.  I will start one once I get everything working well and tested.  I haven't tested much yet though.  

I installed the eGalaxTouch program and now have perfectly working touchscreen.  I want to get a well working pop up keyboard now.  Is there any preferred one being used in Ubuntu now?  I found a video some where of a guy running Fedora I believe with some pop up keyboard from meego.  I can't find the video now.

---

### Post by beastrace91 on 2011-09-07
Enlightenment runs even better on touch devices and has far less bloat... Video demo of E running on a tablet PC:

[http://www.youtube.com/watch?v=7jJNRm3RjTA](http://www.youtube.com/watch?v=7jJNRm3RjTA)

~Jeff

---

### Post by googatrix on 2011-09-08
> **bikealot said:**
> Yes, this is an issue with 11.04 - it works in 10.10.  The problem exists on all desktops (Unity, 2D, Classic, ..). I submitted a Launchpad bug, so we will see where that leads us.

For reference, this is the link to the [[COLOR="Blue"]_screen resolution bug on Launchpad_[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/787587"). Please click the "This bug affects ... people" link on top of the page to (hopefully) draw some attention to this problem.

---

### Post by Kirboosy on 2011-09-08
> **beastrace91 said:**
> Enlightenment runs even better on touch devices and has far less bloat... Video demo of E running on a tablet PC:

[http://www.youtube.com/watch?v=7jJNRm3RjTA](http://www.youtube.com/watch?v=7jJNRm3RjTA)

~Jeff

Thanks for reminding me. I tried this WM sometime ago and I remember thinking "If I was using a touchscreen this would be great". Now I have a touchscreen but I totally forgot about it. :oops:

> **senor_smile said:**
>  Is there any preferred one being used in Ubuntu now?  I found a video some where of a guy running Fedora I believe with some pop up keyboard from meego.  I can't find the video now.

We like to push [florence virtual keyboard]("http://florence.sourceforge.net/english.html")...If that doesn't suite your fancy you can try [kvkbd]("http://kde-apps.org/content/show.php/Kvkbd?content=56019")

---

### Post by ninjaaron on 2011-09-09
> **Caboose885 said:**
> Would anyone here like to test out my Broadcom Crystal HD Decoder install script? 

I know its very rough but it got the job done on mine and I figured it might be somewhat useful for others... If you see any errors let me know and I will fix them.I'll give this a shot.

> **Caboose885 said:**
> Oh, also I'm trying to get the flip detection on my Duo working.

Sorry to leave you hanging on this, but here: [http://ubuntuforums.org/showpost.php?p=11010054&postcount=500]("http://ubuntuforums.org/showpost.php?p=11010054&postcount=500")

---

### Post by beastrace91 on 2011-09-09
Video of Enlightenment running on my dell duo :D

[http://www.youtube.com/watch?v=7qMTCXPybH4](http://www.youtube.com/watch?v=7qMTCXPybH4)

~Jeff

---

### Post by Kirboosy on 2011-09-09
> **ninjaaron said:**
> Sorry to leave you hanging on this, but here: [http://ubuntuforums.org/showpost.php?p=11010054&postcount=500](http://ubuntuforums.org/showpost.php?p=11010054&postcount=500)

Oh ok, sweet I will make sure to add it.

> **beastrace91 said:**
> Video of Enlightenment running on my dell duo :D

[http://www.youtube.com/watch?v=6A-jpFtirgY](http://www.youtube.com/watch?v=6A-jpFtirgY)

~Jeff

"Video has been removed by user" :'(

---

### Post by beastrace91 on 2011-09-09
Sorry bout that here is the updated link - [http://www.youtube.com/watch?v=7qMTCXPybH4](http://www.youtube.com/watch?v=7qMTCXPybH4)

First one I uploaded had some audio issues.

~Jeff

---

### Post by senor_smile on 2011-09-09
> **beastrace91 said:**
> Sorry bout that here is the updated link - [http://www.youtube.com/watch?v=7qMTCXPybH4](http://www.youtube.com/watch?v=7qMTCXPybH4)

First one I uploaded had some audio issues.

~Jeff

Wow, this even looks more impressive on the Dell.  The original video was running on an archos 7 with an ARM processor, which is impressive in its own right.  

I want to try this out immediately.  I imagine you could get very good performance out of the Dell Duo with the low overhead of Enlightenment, especially vs. Win7 or Gnome 3.  What customizations did you have to do after a base install of Bodhi to get the UI working as you showed in the latest youtube video?

---

### Post by beastrace91 on 2011-09-09
That touch GUI is simply the default tablet profile Bodhi 1.2.0 ships with. The first "laptop" setup shown is our laptop profile. You can toggle the automatic switching between profiles by how I mention on my blog here - [http://jeffhoogland.blogspot.com/2011/09/enlightening-your-dell-duo-with-linux.html](http://jeffhoogland.blogspot.com/2011/09/enlightening-your-dell-duo-with-linux.html)

~Jeff

---

### Post by amras5584 on 2011-09-13
Hi!! Before all, sorry for my bad English, I'm Spanish...

I've Installed Kubuntu 11.10 on my Dell from zero and touch-screen runs very well, but not with multi-touch. However, on the touch-pad runs multi-touch too!!

All these without editing any grub archive!! I wish it runs well too on Ubuntu, Luck!!

Thanks for all your messages, was very helpful.

BYE!!

EDIT: False alarm. I shut down and now it don't run the touch on screen. I've installed Android-x86 2011-20-02 and when I reboot after it the touch runs, but not if I shoot up, sorry for these, my fault.

---

### Post by submarine123 on 2011-09-14
I figured it out, the SystemID was case sensitive.

Here's teh SystemID if you need it for BIOS updates, if it's not already mentioned.

0x048B

---

### Post by mobby2011 on 2011-09-14
Hey guys, great work on all this duo stuff!  I tried the scripting/coding whatever for seting up Tablet Mode On/Off and I am having no luck.  The keyboard assignment isnt getting picked up when i close and open the lid.  Any idea's?  Othet than that my duo works great.  Is enlightenment better for viewing and touching than Unity?  I am old guy and can hardly see the little things on unity.  
 
Thanks

---

### Post by Zephonim on 2011-09-15
Definitely great work. Ubuntu is great on the duo, but once I got Bodhi set up, it works so much better with what seemed to be less hassle. You should give it a try. Here is the link again.

[http://jeffhoogland.blogspot.com/2011/09/enlightening-your-dell-duo-with-linux.html](http://jeffhoogland.blogspot.com/2011/09/enlightening-your-dell-duo-with-linux.html)

---

### Post by drumour on 2011-09-23
A big Thanks to everyone for all the work on getting this working.

I am running natty without installing EGalax Touch drivers but with the grub edit:

I have replaced unity with netbook-launcher-efl:

I have edited the metacity style to increase the windows control button size:

And I am almost ready to wipe windows...

But the big show-stopper is the lack of multi-touch,
What hope is there that this will work?

---

### Post by Darrvid on 2011-09-26
So I'm having problems with HD video.  I used the script to install the HD driver.  VLC and totem do a very poor job running it.  Mplayer has smooth playback, but it plays slowly.  I have no idea how to tell if the drivers installed correctly, or how to manage mplayer to make sure it's using hardware acceleration (I only barely figured out how to play a movie with it... ubuntu seems pretty cool but there's a learning curve for sure).  So, keep in mind my OS experience is all windows up until now.

The video is .mp4 1080p.  720p mkv also runs choppy.  Also seems worth mentioning that the Big Buck Bunny trailer is choppy as well.

Any help is appreciated!

Edit:  Just installed smplayer, which seems to offer a decent gui so I can try changing the video output- but no choices fix the problem.  I see nothing that indicates my CrystalHD chip.  I also went in and manually installed the driver- still no luck.

---

### Post by ninjaaron on 2011-09-27
> **drumour said:**
> But the big show-stopper is the lack of multi-touch,
What hope is there that this will work?

Probably not at least for the next release cycle.  I believe the real problem is that the device isn't very popular, and it was antiquated not long after it came out.  Mutli-touch actually did work on some much earlier kernel versions (I think it may work in 9.10 or 10.04), but there has been a regression in support, and nobody cares (including eGalax and the kernel devs).

I'm not optimistic that the problem will ever be resolved, though anything can happen.  The easystroke gesture recognition program, however, does most of the things that I had hoped to do with multitouch, and I don't feel that the duo is crippled at all when I use it.

---

### Post by beastrace91 on 2011-09-29
> **Zephonim said:**
> Definitely great work. Ubuntu is great on the duo, but once I got Bodhi set up, it works so much better with what seemed to be less hassle. You should give it a try. Here is the link again.

[http://jeffhoogland.blogspot.com/2011/09/enlightening-your-dell-duo-with-linux.html](http://jeffhoogland.blogspot.com/2011/09/enlightening-your-dell-duo-with-linux.html)

Thanks :)

~Jeff

---

### Post by celticbhoy on 2011-10-03
Been trying to follow through this thread, but it covers a lot of time, versions of Ubuntu, and pages. Got a Duo a week or so ago, and I am enjoying the fun factor this little netbook brings. I wiped the standard Win 7, and replaced it with win 8 as the interface really suits a touch screen. I also have Bodhi linux installed (and have to say well done to Jeff for putting a nice distro together), and an early build Android honeyComb X86 running. I am now setting up Ubuntu and have most of the fixes mentioned working on 11.10, but the area confusing me is the accelerometer. Is this working on any Ubuntu version, and if so what version, and where are the fix instructions located. 

Thanx for any help in advance.

---

### Post by w1ll1am on 2011-10-04
> **celticbhoy said:**
> Been trying to follow through this thread, but it covers a lot of time, versions of Ubuntu, and pages. Got a Duo a week or so ago, and I am enjoying the fun factor this little netbook brings. I wiped the standard Win 7, and replaced it with win 8 as the interface really suits a touch screen. I also have Bodhi linux installed (and have to say well done to Jeff for putting a nice distro together), and an early build Android honeyComb X86 running. I am now setting up Ubuntu and have most of the fixes mentioned working on 11.10, but the area confusing me is the accelerometer. Is this working on any Ubuntu version, and if so what version, and where are the fix instructions located. 

Thanx for any help in advance.

You need to read this [http://ubuntuforums.org/showthread.php?t=1658480](http://ubuntuforums.org/showthread.php?t=1658480)

The accelerometer is working somewhat it is not automated and has to be started every time you turn on your duo. It looks promising but I am not sure that lukeross is still working on it or not. Let us know what you find out.[]("http://ubuntuforums.org/member.php?u=776920")

---

### Post by drumour on 2011-10-06
> **ninjaaron said:**
> ...it was antiquated not long after it came out.... The easystroke gesture recognition program, however, does most of the things that I had hoped to do with multitouch...

Thank you again, Easystroke is a good recommendation. However it seems Windows is the only way of turning the wireless back on if I inadvertently turn it off with the F2 key (Sometimes the function keys are F* keys  by default other times they act as Battery wireless, etc switches)

"Antiquated" and yet still in the catalog and receiving sales hype![http://ubuntuforums.org/images/smilies/smiley-faces-75.gif](http://ubuntuforums.org/images/smilies/smiley-faces-75.gif)

---

### Post by ninjaaron on 2011-10-08
> **drumour said:**
> Thank you again, Easystroke is a good recommendation. However it seems Windows is the only way of turning the wireless back on if I inadvertently turn it off with the F2 key (Sometimes the function keys are F* keys  by default other times they act as Battery wireless, etc switches)

"Antiquated" and yet still in the catalog and receiving sales hype![http://ubuntuforums.org/images/smilies/smiley-faces-75.gif](http://ubuntuforums.org/images/smilies/smiley-faces-75.gif)

I'm talking especially about the screen, which a couple of devices that used to use it have actually abandoned.  The Duo is still going strong (or, as strong as ever), but I thinke eGalax may be pretty much done with it.

As far as the wireless key behavior, it is terrible.  I only have Ubuntu on mine, but you can actually switch it back by pressing the button again.  It's just that the change doesn't take effect until you reboot, which is ridiculous.  I'm pretty sure there is a way to fix this with rfkill, but I haven't sat down to figure it out yet.  I love my duo, and I love Ubuntu, and I'm pretty happy with them most of the time, but there are some things that just plain suck.

---

### Post by garwal on 2011-10-08
Hello been some time since I played with the Duo,Now do not think I don't love my Unbuntu and Linux, but the work needed to make it functional is a bit much for some and the results are less than seller so Just for kicks I installed Win 8 development release and I was shocked. Everything worked on install except the rotation feature. Touch is excellent and works the way it was designed to. Fast is not a good word to describe the zip in this dell now. I have a full install only of win 8 now as it does everything I want it to do. There is a learning curve on how to adapt to doing some tasks that we are so old school on. I will just say that if you were given a Duo with Win 8 installed you would not think twice, If you would like to see the mighty Duo do it thing please find a copy and give it a spin. If there is any interest I would be glad to help you get going.

[IMG]http://www.howtogeek.com/wp-content/uploads/2011/09/image.png[/IMG]

How Can I Get Windows 8?
[http://www.howtogeek.com/74089/windows-8-the-gigantic-how-to-geek-screenshot-tour/]("http://www.howtogeek.com/74089/windows-8-the-gigantic-how-to-geek-screenshot-tour/")

Windows 8 Developer Preview downloads
[http://msdn.microsoft.com/en-us/windows/apps/br229516]("http://msdn.microsoft.com/en-us/windows/apps/br229516")

---

### Post by ninjaaron on 2011-10-09
> **garwal said:**
> Hello been some time since I played with the Duo,Now do not think I don't love my Unbuntu and Linux, but the work needed to make it functional is a bit much for some and the results are less than seller so Just for kicks I installed Win 8 development release and I was shocked. Everything worked on install except the rotation feature. Touch is excellent and works the way it was designed to. Fast is not a good word to describe the zip in this dell now. I have a full install only of win 8 now as it does everything I want it to do. There is a learning curve on how to adapt to doing some tasks that we are so old school on. I will just say that if you were given a Duo with Win 8 installed you would not think twice, If you would like to see the mighty Duo do it thing please find a copy and give it a spin. If there is any interest I would be glad to help you get going.

Yeah, Windows 8 looks awesome.  I'd try it in a second if I didn't have ideological objections to it and it wasn't a security hazard.  The new interface is pure genius, in my opinion.

---

### Post by celticbhoy on 2011-10-13
> **ninjaaron said:**
> I'm talking especially about the screen, which a couple of devices that used to use it have actually abandoned.  The Duo is still going strong (or, as strong as ever), but I thinke eGalax may be pretty much done with it.

As far as the wireless key behavior, it is terrible.  I only have Ubuntu on mine, but you can actually switch it back by pressing the button again.  It's just that the change doesn't take effect until you reboot, which is ridiculous.  I'm pretty sure there is a way to fix this with rfkill, but I haven't sat down to figure it out yet.  I love my duo, and I love Ubuntu, and I'm pretty happy with them most of the time, but there are some things that just plain suck.

I have found that once you turn wireless back on using the keyboard you then have to re-enable it in Network-Manager. Either by right clicking the icon (pre-11.10) or just clicking it and selecting enable wireless.

---

### Post by raphaelsaldanha on 2011-10-14
Had anyone tried the 11.10 on Duo? The interface seems to be more touch friendly...

---

### Post by Schnippzle on 2011-10-14
> **raphaelsaldanha said:**
> Had anyone tried the 11.10 on Duo? The interface seems to be more touch friendly...

I'll be getting my duo on Wednesday so it's the first thing I'll be trying :D

---

### Post by Enterpart on 2011-10-15
> Originally Posted by ninjaaron  
...it was antiquated not long after it came out.... The easystroke gesture recognition program, however, does most of the things that I had hoped to do with multitouch...

easystroke can do alot of things you didnt you can, like configure tap zones, be able to emulate up to 8 scroll wheels and 8 additional buttons just by using the touchpad. Ive written how to on here

[http://ubuntuforums.org/showthread.php?t=1859936&highlight=tap+zones]("http://ubuntuforums.org/showthread.php?t=1859936&highlight=tap+zones")

and to configure the tap zones check this.

[http://ubuntuforums.org/showthread.php?t=1824870&highlight=tap+zones]("http://ubuntuforums.org/showthread.php?t=1824870&highlight=tap+zones")

so much more powerful than what windows can do with this trick

---

### Post by drumour on 2011-10-28
Using 11.10 Lubuntu, seems slightly slicker. Setting up everything is the same as per instructions in first post for 11.04. with one IMPORTANT exception, I recommend 'Onboard' virtual keyboard instead of 'Florence' (may just have been me, but Florence was not as stable on Lubuntu 11.10 as it was on Ubuntu 11.04)

---

### Post by beastrace91 on 2011-10-28
> **drumour said:**
> Using 11.10 Lubuntu, seems slightly slicker. Setting up everything is the same as per instructions in first post for 11.04. with one IMPORTANT exception, I recommend 'Onboard' virtual keyboard instead of 'Florence' (may just have been me, but Florence was not as stable on Lubuntu 11.10 as it was on Ubuntu 11.04)

If you think that is slick you will be blown away by Enlightenment :)

~Jeff

---

### Post by celticbhoy on 2011-10-28
I don't know if this will help anyone with the accelerometer, but the Duo uses the same chip as the HP Touchpad, and the guys over at CyanogenMod have got it working on CM7. I don't really know much about kernels, but if its on android, it should be able to work on Linux.

---

### Post by beastrace91 on 2011-10-28
> **celticbhoy said:**
> if its on android, it should be able to work on Linux.

As someone who owns a few android devices that all have **** poor Linux support I can attest to this not being true.

~Jeff

---

### Post by celticbhoy on 2011-10-30
> **beastrace91 said:**
> As someone who owns a few android devices that all have **** poor Linux support I can attest to this not being true.

~Jeff

I realise that its not as simple as dropping the kernel module from Android into Ubuntu, and I also note that on the accelerometer thread you asked for the module sources. 

[http://www.st.com/stonline/stappl/resourceSelector/app?page=resourceSelector&doctype=SW_DRIVER&ClassID=1575](http://www.st.com/stonline/stappl/resourceSelector/app?page=resourceSelector&doctype=SW_DRIVER&ClassID=1575)

You will see that an Android version, and a OS independent version are on the page. I would guess the CM7 guys made their module from the code listed here, hopefully we can too.

---

### Post by pressurepoint on 2011-11-01
I'm currently using 11.1 with gnome 3 and I have to say I like it.  It is taking some getting used to since I wasn't expecting such a huge change from gnome 2 but so far so good.  
There is an universal access settings icon which lets you turn on a basic but functional screen keyboard.  The onboard keyboard seems to work well too.
I believe the touchscreen worked with screen rotation out of the box.  I may have installed touchscreen helper without remembering.
There are some strange strange things like you have to log out to hibernate or shutdown from the menu but from the terminal is fine.
Side scrolling (scrolling with finger on the edge of the touchpad) works great - no need for two finger scrolling IMO.

---

### Post by mfarshada on 2011-11-02
> **ninjaaron said:**
> Let's hold off on that until we get a confirmation.  Besides, we may still need it in 11.10

But so long as we are talking about editing the original post, you might want to add something about easytouch and the way to get the computer to recognize a screen flip.  I consider both of those things significant breakthroughs for the duo.

If you are still looking for the answer, look at the neat solution in post #1:
> 
Tablet Mode Recognition -- gjahuja
Add the following lines to /etc/rc.local (make sure to sudo)
Code:

setkeycodes e073 148 &
setkeycodes e074 149
exit 0

When you flip the screen and close the lid, a keystroke is sent, and when you open the lid one the screen is flipped another one is sent. Those commands maps these keystrokes to XF86LAUNCH1 and XF86LAUNCH2. rc.local runs those commands on start up so you don't need to run them at every session start.

Now open Keyboard Shortcuts and add two new shortcuts, one for Tablet Mode ON, and other one for Tablet Mode OFF, and tell them to run your scripts for each mode. Now, you can't type XF86LAUNCH# to the shortcut field, what you need to do is click it for it to become active (it will say New shortcut...) and then flip the screen and close the lid. The correct keystroke will be added. Then click to edit the other one and while it's active open the lid, you will see XF86LAUNCH2 in the shortcut field.


It worked for me, though I don't know of useful commands to assign to tablet mode on/off. And I couldn't get your installer for touchscreen-helper. Niether ppa nor your link here worked "ninjaaron." Could you please put it here if it still works?

Thanks

---

### Post by raphaelsaldanha on 2011-11-28
Hi guys,

I'm using 11.10 with the Duo, and almost everything is Ok, except an extrange behavior on the touchpad. Sometimes, generally after type something, I loose the touchpad: the arrow doesn't move and the two buttons doesn't work (but the touchsreen keeps fine).

What that can be?

---

### Post by Kirboosy on 2011-11-29
> **raphaelsaldanha said:**
> Hi guys,

I'm using 11.10 with the Duo, and almost everything is Ok, except an extrange behavior on the touchpad. Sometimes, generally after type something, I loose the touchpad: the arrow doesn't move and the two buttons doesn't work (but the touchsreen keeps fine).

What that can be?

Under the mouse settings make sure that "Disable trackpad while typing" is **not checked**

See if that helps any

---

### Post by unused_bagels on 2011-12-02
I don't get the option for 4pts calibration.  In fact, when i was installing the eGalaxTouch driver, it didn't give me 3 options.  It just asked me to reboot.  When I try autocomplete, all I get are eGalaxCalib and eGTouchd.  Neither of them give me what I need.  the X axis is fine on my touchscreen, but the y is inverted.

---

### Post by celticbhoy on 2011-12-10
> **unused_bagels said:**
> I don't get the option for 4pts calibration.  In fact, when i was installing the eGalaxTouch driver, it didn't give me 3 options.  It just asked me to reboot.  When I try autocomplete, all I get are eGalaxCalib and eGTouchd.  Neither of them give me what I need.  the X axis is fine on my touchscreen, but the y is inverted.

Thats because the driver has been updated for the 3.x kernel family. To fix the Y axis, you need to edit the .ini file located in /etc/ in it option number 8 is set to 0 by default, changing this to 2 will invert your Y. 

The good thing about the new driver is it comes fully documented for both linux & android, via an included pdf. Only just noticed the update and installed so have not had much chance to test any benefits, but it seems that multitouch is enabled within the driver by default, again accessible through the .ini file.

---

### Post by unused_bagels on 2011-12-10
I would, but I just found a version of Natty designed for the Dell Duo.  Perhaps the OP could be updated to include info on the .ini file, but also, people should look into Ubuntu Ubermix. 
While at first it doesn't seem like something power users might like, once the "altering the base image" is performed, I can pretty much do what I want, and the whole system works great!

---

### Post by teh603 on 2011-12-10
Dunno about the rest of you, but mine (if I get one; its not a given at this point) is going to use Kubuntu. I've been meaning to try out Plasma Netbook for a while now; it looks closer to traditional KDE than Unity does to Gnome.

---

### Post by Kirboosy on 2011-12-10
> **celticbhoy said:**
> Thats because the driver has been updated for the 3.x kernel family. To fix the Y axis, you need to edit the .ini file located in /etc/ in it option number 8 is set to 0 by default, changing this to 2 will invert your Y. 

The good thing about the new driver is it comes fully documented for both linux & android, via an included pdf. Only just noticed the update and installed so have not had much chance to test any benefits, but it seems that multitouch is enabled within the driver by default, again accessible through the .ini file.

You are correct. It does have multitouch by defaut enabled. I also am happy to announce that multitouch is **[SIZE="2"]WORKING[/SIZE]** on my Duo! :D (Ubuntu 11.10)

It still doesn't do much for you because I haven't figured out how to get uTouch to interpret it yet but I haven't fiddled much yet. If anyone is a uTouch expert please help us get something working.

It also looks like I will have to rehaul the "How to" portion of the thread. I'm working on it but I'm not quite finished with it yet. I will post the update soon though. All hope is not lost on this little device after all! \\:D/

---

### Post by digitalmc on 2011-12-11
Greetings Duo Fans!!!

I have read through about this entire post (as well as many others) and I have an SOS question if anyone could help me. 

I need the touchscreen to rotate with the screen. When i rotate the screen, the touchscreen does not rotate with it. I have a script that runs this from a keyboard shortcut, so if anyone knows script that i could include to rotate touch screen as well that would be huge. I am running ubuntu Netbook Remix / ubuntu 10.04. 

Also on a side-note I have yet to get multi-touch to work. I installed the software suggested on this forum to no avail. Anyone have any suggestions? 

Thanks guys. I am very tired and desperate at this point. Countless hours have been put into this lol. I'm about ready to go back to Windows ;) ha just joking... but really. pretty tired.

---

### Post by ninjaaron on 2011-12-12
> **Caboose885 said:**
> You are correct. It does have multitouch by defaut enabled. I also am happy to announce that multitouch is **[SIZE="2"]WORKING[/SIZE]** on my Duo! :D (Ubuntu 11.10)

It still doesn't do much for you because I haven't figured out how to get uTouch to interpret it yet but I haven't fiddled much yet. If anyone is a uTouch expert please help us get something working.

It also looks like I will have to rehaul the "How to" portion of the thread. I'm working on it but I'm not quite finished with it yet. I will post the update soon though. All hope is not lost on this little device after all! \\:D/

wait, what's this .ini file now?

---

### Post by Kirboosy on 2011-12-12
> **ninjaaron said:**
> wait, what's this .ini file now?

Ninja! :D

All i had to change in the default ini file after installation was the Direction from 0 to 2. My touchscreen worked flawlessly after that. (I added directions into the how to section)

---

### Post by ninjaaron on 2011-12-12
> **Caboose885 said:**
> Ninja! :D

All i had to change in the default ini file after installation was the Direction from 0 to 2. My touchscreen worked flawlessly after that. (I added directions into the how to section)

Hmm... helpful directions.  Thanks.

Now easystroke isn't responding to gestures from the screen, only the mouse/touchpad.  Needless to say, multitouch that doesn't do anything is less useful easystroke.  I'll try twiddling the knobs in /etc/eGTouchd.ini and see if I can't get something to work.

Also image viewer and document viewer can use some multitouch to zoom, rotate, scroll, etc.  The response is pretty awful at the moment, but at least it's something to play with until Canonical decides through some £ at the project (which we may assume will happen sometime in the next year, given the announcements at the last UDS).

[i][edit] Ok, looks like if I turn multitouch off in the config file, easystroke works again.  I hate disabling it, but it's not doing anything anyway, and easystroke does a lot, so the choice isn't too difficult.  If anyone figures out how to get the two working in harmony, let me know!

[second edit] One of the options in /etc/eGTouchd.ini is `MultiTouchEable.`  This must be set to 0 for easystroke to work.  This only disables event reporting to utouch (which is useless at this point), but if the ReportPoint is set to a value of 2 or greater, it will still register multiple touch points for any apps that can use them.[/i]

Oh yeah, about the screen rotation ppa thing.  That package hasn't really been updated for the last two ubuntu releases, but you can still download it directly for a previous release and install the deb yourself.  Works just as before.

dowload links:
[64bit](https://launchpad.net/~plippo/+archive/t101mt/+files/touchscreen-helper_0.0.1-ppa2_amd64.deb)
[32bit](https://launchpad.net/~plippo/+archive/t101mt/+files/touchscreen-helper_0.0.1-ppa2_i386.deb)

---

### Post by ninjaaron on 2011-12-13
There is a program out there called touchegg which supposedly supplies multitouch gesture recognition via utouch.  Trying now.

***

Wasn't impressed.  Many of the gestures require more than two touchpoints, which this screen doesn't have.  Furthermore, the pinch and rotate gestures don't seem to be registered by touchegg for some reason.  Sticking with easystroke for now.

---

### Post by Kirboosy on 2011-12-13
> **ninjaaron said:**
> There is a program out there called touchegg which supposedly supplies multitouch gesture recognition via utouch.  Trying now.

***

Wasn't impressed.  Many of the gestures require more than two touchpoints, which this screen doesn't have.  Furthermore, the pinch and rotate gestures don't seem to be registered by touchegg for some reason.  Sticking with easystroke for now.

I also saw a program called [twofing]("http://ubuntuforums.org/showpost.php?p=9353432&postcount=77") but sadly I haven't been able to get it to work on my Duo. (It might be because I am running 11.10...not sure)

---

### Post by digitalmc on 2011-12-14
NICE! That screen rotation helper worked amazing. Thanks so much. Really, you made my month. Thanks for all the hard work guys. It's really helped me get this thing up and running. =D>

---

### Post by teh603 on 2011-12-14
Just curious, did anyone solve the issue of ethernet not connecting when you hot-plug it into the docking station?

---

### Post by Kirboosy on 2011-12-15
I have come up with a pretty slick setup using KDE. If you do not use KDE this post might not be of much help to you but any KDE users might find this helpful

I created a script that toggles between plasma-desktoop and plasma-netbook. Netbook mode is a very touchable version but I don't like using it all the time because I found in cumbersome to use with a mouse. To remedy the situation I just bound the events from the screen rotation to my script. My script took the same style as Ninjaarons for the rotation script. If the screen is this then do this. If any one has any more questions about it please don't hesitate to ask.

I have attached the script that I am using.

> **teh603 said:**
> Just curious, did anyone solve the issue of ethernet not connecting when you hot-plug it into the docking station?
I am working on this issue now. I forgot totally about it until you mentioned it. ;)

---

### Post by teh603 on 2011-12-15
> **Caboose885 said:**
> I have come up with a pretty slick setup using KDE. If you do not use KDE this post might not be of much help to you but any KDE users might find this helpful

I created a script that toggles between plasma-desktoop and plasma-netbook. Netbook mode is a very touchable version but I don't like using it all the time because I found in cumbersome to use with a mouse. To remedy the situation I just bound the events from the screen rotation to my script. My script took the same style as Ninjaarons for the rotation script. If the screen is this then do this. If any one has any more questions about it please don't hesitate to ask.

I have attached the script that I am using.Oooh, Kubuntu user here! 

Only one problem- how do I use it?

> I am working on this issue now. I forgot totally about it until you mentioned it. ;)Good to hear.

I got to thinking, since the Duo has only USB on itself and the only extra port the dock has is Ethernet, maybe they shaved a little weight and a few chips by only equipping it with a USB controller, and put an Ethernet-to-USB converter into the dock?

---

### Post by teh603 on 2011-12-15
So I just got mine, and it keeps turning itself off at random.

And then the idiot with the place I got it from came up with some line about "Well, you voided the warranty by trying to install Linux on it, because the OS is an integral part of the hardware."

Someone's likely to get some very negative feedback on Ebay for Xmas.

Edit: Only does it when the main AC adapter is connected for some reason. Didn't turn off once when I connected it to the dock. This is very strange.

---

### Post by Kirboosy on 2011-12-15
> **teh603 said:**
> So I just got mine, and it keeps turning itself off at random.

And then the idiot with the place I got it from came up with some line about "Well, you voided the warranty by trying to install Linux on it, because the OS is an integral part of the hardware."

Someone's likely to get some very negative feedback on Ebay for Xmas.

Edit: Only does it when the main AC adapter is connected for some reason. Didn't turn off once when I connected it to the dock. This is very strange.

Is it a kernel panic?

---

### Post by teh603 on 2011-12-15
> **Caboose885 said:**
> Is it a kernel panic?Nope, just cuts power and turns off. I've heard its a fairly "common" issue with Dell laptops, so I'm going to see if a computer repair place can fix it. Its probably a broken trace or something.

---

### Post by duyquang27 on 2011-12-17
Anyone can help me, when i install  Egalax, i got this:

```
(*) Linux eGTouch driver installer for eGalaxTouch controller 

(I) Check user permission: root, you are the supervisor.
cp: cannot stat `eGTouch32.tar.gz': No such file or directory
tar (child): eGTouch32.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
chown: cannot access `eGTouch32/eGalaxCalib': No such file or directory
chmod: cannot access `eGTouch32/eGalaxCalib': No such file or directory
(I) Extract eGTouch driver archive to .
(E) The eGTouchd.ini can NOT be copied to /etc.
```

Here is code i typed: ```
sudo /home/quang/Downloads/eGTouch_v1.01.1014.L-x/setup.sh
```

---

### Post by teh603 on 2011-12-17
Before running it, try typing this:

```
cd /home/quang/Downloads/eGTouch_v1.01.1014.L-x/
```

Then re-paste what you typed earlier and it should help. At least it helped me. It was also surprising to find that cd works the same way in Linux as it does in MS-DOS. At least that's one code that I won't have to worry about re-learning.

---

### Post by duyquang27 on 2011-12-17
> **teh603 said:**
> Before running it, try typing this:

```
cd /home/quang/Downloads/eGTouch_v1.01.1014.L-x/
```Then re-paste what you typed earlier and it should help. At least it helped me. It was also surprising to find that cd works the same way in Linux as it does in MS-DOS. At least that's one code that I won't have to worry about re-learning.

Thank u so much !!!

But when install completed, I changed Direction to 2 or 0 its still [FONT=Verdana]inverted Y axis. Why?[/FONT]

---

### Post by teh603 on 2011-12-17
> **duyquang27 said:**
> Thank u so much !!!

But when install completed, I changed Direction to 2 or 0 its still [FONT=Verdana]inverted Y axis. Why?[/FONT]Well, you have to use the Draw Test in eGalaxCalib to see if you need to reverse it. You'll know if you do, because when you draw an upwards arc, the line will go down instead. Then you just edit the .ini and reboot.

In case anyone's wondering, it works in Kubuntu as well, although you'll have to manually select "netbook" after installation. This is where we could the screen switch script.

By the way, at what time do we get enough stuff for a .deb or even a PPA? Cause right now we've got two key bindings, a script to switch between the two Plasma interfaces, and a driver that could all be bundled together to save a lot of time and headache.

---

### Post by duyquang27 on 2011-12-21
I use 11.10 and install Florence. Its work fine but it cant auto hide, no icon in task bar, and no intermediate icon. I checked it in stting but still not work. I type:

```
$ sudo apt-get install build-essential libxml2-dev libgconf2-dev \ > libglade2-dev libatspi-dev libcairo2-dev gnome-doc-utils librsvg2-dev gettext \ > libnotify-dev libxtst-dev intltool libpanel-applet2-dev
```but it say:

```
Package libpanel-applet2-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libgnome-desktop-dev
```so i replace libpanel-applet2-dev = libgnome-desktop-dev.

Anyone can help me fix it? And wat ubuntu ver work fine with florence?

---

### Post by amras5584 on 2011-12-21
i use onboard, and had no problems.

also, gnome3 add his own onscreen keybord from Universal Help on Write or else... I'm Spanish, so don't know how is the correct name of this, sorry. for me is not very practical 'cause no has ñ or accents, but for English people... onboard has it.

really sorry about my English...

---

### Post by teh603 on 2011-12-21
> **amras5584 said:**
> i use onboard, and had no problems.

also, gnome3 add his own onscreen keybord from Universal Help on Write or else... I'm Spanish, so don't know how is the correct name of this, sorry. for me is not very practical 'cause no has ñ or accents, but for English people... onboard has it.

really sorry about my English...You looked in to getting the physical keyboard replaced with a Spanish one?

I'll be honest, I know practically nothing about a modern gnome interface, since I've been using KDE since 10.04. It'd make sense that you could change the keyboard layouts in software, though, and get the actual hardware keyboard changed by a technician.

---

### Post by ninjaaron on 2011-12-21
Florence has always had some difficulty with certain glyphs and keyboard layouts.  I've tried to use it for Hebrew, and it's impossible.  Onboard has been great for as long as the Duo has been out.  With the release of Gnome 3, Onboard also offers many of the features that made florence more appealing in the beginning (hidden window boarders, transparency, keyboard graphics with gradients and rounded corners for a smoother look).  I actually got on their mailing list for a little while and whined about it, and they actually did everything that I said.

Unfortunately, I don't know how to fix your problems with Florence, but I think if you play with the options for Onboard, you will probably find it more than adequate.

I'm not totally sure if this is the issue, but I hope this helps.  If it's a question about switching keyboard layouts in the system, that's another matter.  There's a program called "keyboard" or "keyboard layout" or something, and you can add and delete layouts there.  I assume you installed with a Spanish keyboard, and your issue is with the on-screen keyboard simulation.

---

### Post by amras5584 on 2011-12-22
> **teh603 said:**
> You looked in to getting the physical keyboard replaced with a Spanish one?

I'll be honest, I know practically nothing about a modern gnome interface, since I've been using KDE since 10.04. It'd make sense that you could change the keyboard layouts in software, though, and get the actual hardware keyboard changed by a technician.
onboard is the name of the program I use for the screen keyboard, but is part of genome package, so sorry. my phisycal keyboard of course has Spanish characters. i'm talking about screen keyboard of genome3... sorry about my english.

---

### Post by Kirboosy on 2011-12-22
> **teh603 said:**
> Oooh, Kubuntu user here! 

Only one problem- how do I use it?

I made a [video ]("https://www.youtube.com/watch?v=TUU51YREJtA&context=C390aa21ADOEgsToPDskIcQyWOcZCgpQThTCVC_xXt")on how to get it working.

---

### Post by teh603 on 2011-12-23
Thanks. I'll see how it works once I get my Duo back and test it to make sure they really did fix it. The repair turnaround was so bloody fast, I wouldn't be surprised if all they did was reinstall Win7 and try to claim that everything was fixed. But I don't see how, because there's no way it'd stay powered for a full install unless they did what I told them not to and plugged it into a docking station.

---

### Post by gjahuja on 2011-12-26
> **ninjaaron said:**
> [i][edit] Ok, looks like if I turn multitouch off in the config file, easystroke works again.  I hate disabling it, but it's not doing anything anyway, and easystroke does a lot, so the choice isn't too difficult.  If anyone figures out how to get the two working in harmony, let me know!


I've found a patch for easystroke that enables multitouch:
[http://sourceforge.net/apps/trac/easystroke/ticket/107]("http://sourceforge.net/apps/trac/easystroke/ticket/107")

Here are some video demonstations:
[http://www.youtube.com/watch?v=kmcTue1nSZA]("http://www.youtube.com/watch?v=kmcTue1nSZA")
[http://www.youtube.com/watch?v=0z2hH0lgyrM]("http://www.youtube.com/watch?v=0z2hH0lgyrM")

I've installed this patched version and it works as advertised, although if you plan to use this for gestures like "pinch to zoom" it will not look continuos as in other devices, as each gesture is associated with one key stroke/combination.

Also, I succeeded to build the accelerometer driver from source, but I cannot figure out how to get it working (can load the module, but with some errors)

---

### Post by gjahuja on 2011-12-26
By the way, there is a very good build of Android 4.0 ICS for the TegaV2 that works "almost" compeltely with the Duo (wifi, multitouch display). No sound, no bluetooth, and apparently the camera works, but you cannot see yourself in it. Anyway, it is a recent build so I expect things will get better. You can try it live from a USB drive:

[http://www.android-x86.org/download]("http://www.android-x86.org/download")

Look for android-x86-4.0-tegav2-20111209.iso I've tried it, and it looks very promising, in fact I plan to dual boot soon (I whish someday there is Android support for LaTeX).

---

### Post by Tomrade on 2011-12-26
Thankyou for the KDE script, maybe using actvities would be faster ? make one with search and launch and the other with desktop then move with qdbus commands (either next activity or using activity uid) but I cant work out how to have different panels on activities and how to make all windows span all activites by default . Im looking forward to plasma active though , trying to resist putting openSuSe on to try it out

---

### Post by teh603 on 2011-12-29
Going to be a lot longer before I can start testing. Looks like Dell shipped it back without replacing the motherboard- all they did was reinstall Windows 7 using a docking station, like I told them not to- and then shipped it back. So back to the depot it goes until I get a system that works without a docking station, or I give up and file a BBB complaint.

---

### Post by teh603 on 2012-01-03
Awright, *finally* got mine home working.

First off, Bluetooth didn't seem to be working under Ocelot- it didn't even detect the adapter, which is unexpected because it and the wifi are supposed to share a card. Works in Precise, not quite sure what the deal is. Ironically, kubuntu-low-fat-settings isn't working quite right and makes things look... odd. But that's a problem with the package and not the Duo. So if you've got a Duo and the bluetooth isn't detected, try the good ol' "wait six months" trick and it should work in the LTS.

Wish this thing could've had an SSD. It feels so fragile compared to my other netbooks and my Inspiron 15. I might still get one installed sometime down the line, who knows?

I didn't get a 3g SIM card socket, so I'm not checking that. My creaky old cell modem still has a lot of life in it.

Couldn't get the touchscreen working in Precise. Going to try reinstalling the Ocelot and see if that works. Worst comes to wurts, we'll have to file a bug report on this and hope it gets fixed.

Edit: Here's the result of my lsusb:
```
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:58f4 Realtek Semiconductor Corp. 
Bus 004 Device 002: ID 0eef:725e D-WAV Scientific Co., Ltd 
Bus 004 Device 003: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth

```

---

### Post by teh603 on 2012-01-04
Ok, another update. Got everything working in Ocelot. Would you believe some nimrod broke Muon so it chokes on updates following a clean install?

Everything somehow worked the first time around. I'm not quite sure why it didn't work in Precise, but it just didn't. The desktop switcher script works like a real charm. The bluetooth driver .deb also worked.

---

### Post by teh603 on 2012-01-05
Another Dell Duo update: Please check the bug linked below and see if it affects you like it does me: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/908560](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/908560)

---

### Post by Shuckle on 2012-01-08
Hello, everyone! I am Shuckle. I'm no stranger to open-source anything, but I do happen to be a total novice to Ubuntu.> **Caboose885 said:**
> [FONT=Verdana][/FONT][FONT=Verdana]**Touchscreen**[/FONT]   [FONT=Verdana] --**Caboose885 and shartke**[/FONT] [FONT=Verdana]

**11.10 (Kernel 3.*)**[/FONT][FONT=Verdana]
1. Go to the following website and download the driver: [EGalax Touch drivers]("http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm")The site has multiple kernels and it confuses the heck out of me. Everything else looks understandable, but I'm not sure which kernel to pick, if you'll excuse the pun.[/FONT]

I can't wait to get everything hooked up to the necessary applications/coding and I will definitely be on the lookout for potential problems/fixes and new ways to creatively use the Duo's design. ^_^

---

### Post by celticbhoy on 2012-01-09
> **Shuckle said:**
> Hello, everyone! I am Shuckle. I'm no stranger to open-source anything, but I do happen to be a total novice to Ubuntu.The site has multiple kernels and it confuses the heck out of me. Everything else looks understandable, but I'm not sure which kernel to pick, if you'll excuse the pun.[/FONT]

I can't wait to get everything hooked up to the necessary applications/coding and I will definitely be on the lookout for potential problems/fixes and new ways to creatively use the Duo's design. ^_^

this depends what version of Ubuntu you are using, if you have install 11.10 (latest version) then you want to download the version for the 3.X kernel. I believe it is V1.01.1014.

---

### Post by celticbhoy on 2012-01-09
> **gjahuja said:**
> By the way, there is a very good build of Android 4.0 ICS for the TegaV2 that works "almost" compeltely with the Duo (wifi, multitouch display). No sound, no bluetooth, and apparently the camera works, but you cannot see yourself in it. Anyway, it is a recent build so I expect things will get better. You can try it live from a USB drive:

[http://www.android-x86.org/download]("http://www.android-x86.org/download")

Look for android-x86-4.0-tegav2-20111209.iso I've tried it, and it looks very promising, in fact I plan to dual boot soon (I whish someday there is Android support for LaTeX).

Sound can be enabled with a small kernel hack.

---

### Post by jdcnc on 2012-01-09
Can someone please point me to the original information about Touchscreen_Helper as mentioned on the first page of this thread.  I have been reading and following this thread while I setup openSuSE 12.1 on my Dell Duo.  Most things are working, but I would really like to get the touch screen working better along with the automatic change between tablet mode and desktop mode.  

Thanks is advance for your help and for this great forum thread.

---

### Post by teh603 on 2012-01-09
Got another [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/913848") to report; this one for the black screen I get on trying to wake from sleep. If any of these bugs affect you, please list yourself as being affected (and register on Launchpad if needed) so we can get these things fixed as soon as possible; the more people we get subscribed, the better.

---

### Post by Shuckle on 2012-01-09
Alright. I downloaded the latest kernel (it seemed to make the most sense, seeing as I had the latest version of Ubuntu - I'm glad to see I was right ^_^) and the Terminal claims that all the code I typed in was an invalid command.

If I have the setup.sh in my Downloads folder in a folder marked "eGTouch", then would the code not be: ```
sudo ./home/shuckle/Downloads/eGTouch/setup.sh
```Whenever I type this in, I get an error message. I have tried multiple variants of this and always get "invalid command" as a response. I would like to get the touch screen up and running so I can do touch screen things.

As a side note, has anybody run into these Win7 problems with the touch screen when running Ubuntu?

~Touch screen is frustratingly inaccurate around the border
~Touch screen is not compatible with certain applications and sends a strange signal
~When drawing in a drawing application that is not YouPaint, touch screen clicks at random intervals, making the construction of basic shapes impossible

Just checking. It's not as though these issues are VITALLY IMPORTANT, but they were glitchy and annoying Win7 bugs and I'm curious to see if Ubuntu has fixed them.

---

### Post by teh603 on 2012-01-09
```
cd /home/shuckle/Downloads/eGTouch/setup.sh
```

Try this. (edit: BEFORE running the setup.sh script) It always works on mine.

On the issue of touchscreens and graphics, I don't use one for graphics. I have a perfectly good tablet that I use for graphics and photo retouching. The touchscreen is for playing around hand having fun, not srs bsns.

---

### Post by Shuckle on 2012-01-10
I am not having the best of luck getting this touch screen up and running.

"No such file or directory"

I'm going to keep searching for a solution for now, if anyone has one that would be quite helpful.

---

### Post by mahlerchiro on 2012-01-10
When I try to install the drivers this is what I get can anyone help
3.0.0-12-generic 

(*) Linux eGTouch driver installer for eGalaxTouch controller 

(I) Check user permission: root, you are the supervisor.
cp: cannot stat `eGTouch32.tar.gz': No such file or directory
cd: 386: can't cd to /usr/local
tar (child): eGTouch32.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
(I) Extract eGTouch driver archive to .
(E) The eGTouchd.ini can NOT be copied to /etc.


sudo /home/****/Downloads/eGTouch/setup.sh
**** = user and I changed the directory to eGTouch thought it might help but didn't got same results when I left directory name as extracted

I dragged the files to the proper location from the download. The touch screen is working but the calibration program is only doing draw test and not 4 point calibration can I use another program to calibrate.

switched direction to 2 and y axis is still inverted x is ok but y was inverted at 0 and at 2

I was trying to use mint 12 I switched to ubuntu 11.10 but had to cd (change directory) to the directory first for the install to work then used the commande

cd /home/****/Downloads/eGTouch/

then

sudo /home/****/Downloads/eGTouch/setup.sh

this then gave me multi point on the draw test not sure how it will function in applications yet

I have tryed to set up the duo in Mint 11 and Mint 12 worked ok and in Bohdi linux I am now back to ubuntu 11.10

---

### Post by mahlerchiro on 2012-01-10
see post below seemed to work

---

### Post by teh603 on 2012-01-10
> **Shuckle said:**
> I am not having the best of luck getting this touch screen up and running.

"No such file or directory"

I'm going to keep searching for a solution for now, if anyone has one that would be quite helpful.

D'oh, forgot to remove the setup.sh from the CD line. Try it again like that?

---

### Post by Shuckle on 2012-01-10
> **teh603 said:**
> D'oh, forgot to remove the setup.sh from the CD line. Try it again like that?

Yes, that worked. Thanks.

The Y axis is inverted :/ even though I changed the direction to 2. I foresee another reboot, will edit soon with confirmation/denial, hopefully. I think the problem was I did it before the reboot - better add that to the OP, caboose.

Denial. Rebooting after changing the direction back to 2.

Oddly enough, the inversion is not rectifying itself. I have changed Direction to 2 multiple times and back to 0 multiple times. I am changing it where it first appears on the screen - has anybody had any luck with this issue? I can work around it for a little while but it's distracting and not at all fun to have to work around.

---

### Post by teh603 on 2012-01-11
See if you can't run eGalaxCalib or whatever the calibration app is called. That might fix things. Otherwise, we're at my limit of expertise and you'll have to wait for someone more skilled.

---

### Post by jdcnc on 2012-01-12
For what ever it may be worth, I have found that a reboot after inverting the Y axis works, it does not seem to re-read the .ini file until you reboot the computer.  At least that has been my experience.

John G.

---

### Post by Shuckle on 2012-01-12
So now there is no touch input whatsoever. I'm going to delete the kernel I had and then try to reinstall and reconfigure it the correct way in case I did something really bad and funky.

---

### Post by teh603 on 2012-01-13
If you're using Precise, the touchscreen isn't working. I've filed a bug, but I get the feeling that the kernel isn't being compiled to provide the input services required. The developers are in an obstructionist mood again; one of them told me to try updating at a time when running even the command line updater resulted in massive borkage.

*shrug*

Prolly better to wait for the release.

---

### Post by ray420 on 2012-01-22
has anyone tried to play around with ginn? you can find the config file under /etc/ginn/wishes.xml and add ginn to start up programs. you'll be limited alot cause we only have 2 finger input and not 4 like its configured for but with a little tweaking i think it can do pretty OK.let me know what you think.

---

### Post by gjahuja on 2012-01-23
> **teh603 said:**
> If you're using Precise, the touchscreen isn't working.

Since Linux Kernel 3.2, multitouch displays are handled by the hid-multitouch module. See [this page]("http://manpages.ubuntu.com/manpages/precise/man5/modules.5.html") for loading hid-multitouch module at boot. To configure the touchscreen see [this post in the ArchForums]("https://bbs.archlinux.org/viewtopic.php?id=133851") and [this article in the ArchWiki]("https://wiki.archlinux.org/index.php/Multitouch_Displays"). I've submited the VID and PID of my display,
```

$ lsusb
-----
Bus 004 Device 002: ID 0eef:725e D-WAV Scientific Co., Ltd 
```if it works with yours and you have different numbers (I don't know if all Duos are sold with the exact same model of display) you should send the details to the linux-input mailing list so they can be added to the module and hopefully it will be detected automatically at boot in later kernel versions.

Caboose885, you may also like to add a section the instructions post, for the ones who would like to try Precise right know and not loose touchscreen functionality.

---

### Post by teh603 on 2012-01-24
Thanks, I'll try that. I was about to declare the bloody thing a total loss and go back to my big old Inspiron 15.

Edit: Can you give me a step-by-step for Ubuntu or Kubuntu? I got to the point where I was supposed to add an "echo" line to something, but it didn't seem to work. Running the echo line gave an "access denied" response, even when prefaced with sudo- but then again, what can we expect from a Linux distro that's not being run for the general populace?

---

### Post by loganbell45 on 2012-02-04
Hey all - new duo owner, massive thanks for this thread. I'm having trouble installing florence, but I'm working on it and people from other threads are helping (It's cropping up with so many issues when i try to ./configure). I'm also having a lot of trouble getting sound to play through the JBL speakers...

The main reason I'm here though is to ask how you've all configured easystroke? I don't want to have to press a key in order to use it as I want to use it in tablet mode, how have you guys done it?

---

### Post by ray420 on 2012-02-07
Theres a dependency that you cant install with ubuntu greater than 10.10 you have to do ./configure without that dependency. it tells you the command at the end of the error message when you run ./configure, that's a least the problem I had. I think its something to do with not being compatible with ubuntu indicators and wanting gnome 2 indicators. hope that helps.

---

### Post by Fredo on 2012-02-14
Hi!

I am currently trying to get the touchscreen working with Precise. I installed the eGTouch driver and added hid-multitouch to /etc/modules. It seems to work somewhat, I get this output in syslog:

```
Feb 14 23:12:31 my-duo kernel: [  176.340771] input: eGalax Inc. USB TouchController as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input10
Feb 14 23:12:31 my-duo kernel: [  176.342360] hid-multitouch 0003:0EEF:725E.0001: input,hiddev0,hidraw0: USB HID v2.10 Pointer [eGalax Inc. USB TouchController] on usb-0000:00:1d.2-1/input0
Feb 14 23:12:32 my-duo kernel: [  177.661486] input: eGalaxTouch Virtual Device for Multi as /devices/virtual/input/input11
Feb 14 23:12:32 my-duo kernel: [  177.662825] input: eGalaxTouch Virtual Device for Single as /devices/virtual/input/input12

```

Still, multitouch is not working. And the eGTouchU utility does not list any devices.

Could anybody share some insights as how to get the touchscreen working unter Precise?

Thanks in advance,
Fredo

---

### Post by teh603 on 2012-02-17
> **Fredo said:**
> Hi!
Could anybody share some insights as how to get the touchscreen working unter Precise?

There's a bug filed on it in Launchpad, but it has nobody assigned to it and it only has medium priority.

---

### Post by Fredo on 2012-02-17
When I run my Duo on battery, and then plug in the AC adapter, Ubuntu crashes.

There was a kernel bug[1], and what I can tell from it is that this is a BIOS bug. Did anybody find a proper way to deal with this? I read that downgrading pm-utils should help, but for me, it didn’t.

[1] [https://bugzilla.kernel.org/show_bug.cgi?id=38782](https://bugzilla.kernel.org/show_bug.cgi?id=38782)

---

### Post by teh603 on 2012-02-18
Sounds like a cop-out if you ask me. Flashing the BIOS is the worst thing you can do to a computer; I've heard more horror stories of failed BIOS flashes than I have successful ones. So instead of just saying "Oh, its the BIOS not complying with standards," the response should be, "Ok, its quirky, let's get a patch out there."

Cause quirky BIOSes don't stop Windows 7, so why should we let them stop us?

---

### Post by teh603 on 2012-02-22
Ok, got the touchscreen to work finally, but the ACPI is still hammered to hell and back. Editing the local.rc worked, when the same command didn't from the touchscreen. No freaking idea why.

Shame my lil' Duo is just gathering dust instead of rocking out the way its supposed to.

---

### Post by Kirboosy on 2012-02-24
> **Fredo said:**
> When I run my Duo on battery, and then plug in the AC adapter, Ubuntu crashes.

There was a kernel bug[1], and what I can tell from it is that this is a BIOS bug. Did anybody find a proper way to deal with this? I read that downgrading pm-utils should help, but for me, it didn&#8217;t.

[1] [https://bugzilla.kernel.org/show_bug.cgi?id=38782](https://bugzilla.kernel.org/show_bug.cgi?id=38782)

What version of Ubuntu are you running and what BIOS is your Duo?

I'm running 11.10 and A06 BIOS and I have no problems with it crashing. I do believe 10.10 and 11.04 had crashing problems in the very beginning. I can't remember now but I know I posted about it in this thread.

However you will not be able to update your BIOS easily without Windows installed.

EDIT: Thinking about it I think it was more of a Unity issue for me because when I would switch my computer to Classic Gnome it wouldn't crash but Unity would. I now run Kubuntu so I can't really verify that Unity has this problem still.

---

### Post by teh603 on 2012-02-25
> **Caboose885 said:**
> What version of Ubuntu are you running and what BIOS is your Duo?

I'm running 11.10 and A06 BIOS and I have no problems with it crashing. I do believe 10.10 and 11.04 had crashing problems in the very beginning. I can't remember now but I know I posted about it in this thread.I think I'm still running AO6; its a replacement motherboard but its still pretty much stock. You'll have to excuse me; I'm 200+ miles away from it. Its running Precise, though. The only thing that worked on Ocelot was the touchscreen. The ACPI has worked off and on in Precise; it worked early on (although it was using the phantom AC adapter so the only thing it could register was when I unplugged it; it didn't even register being plugged in or charging), and then stopped working in a late version of 3.2.

You might want to add the hid-multitouch local.rc echo line to the front page; its a one- line hack that seems to get it working quickly and easily in Precise.
> However you will not be able to update your BIOS easily without Windows installed.To misquote a USENET joke, a guy realizes he has a problem with his computer, and decides to flash the BIOS. Now he has two problems.

> EDIT: Thinking about it I think it was more of a Unity issue for me because when I would switch my computer to Classic Gnome it wouldn't crash but Unity would. I now run Kubuntu so I can't really verify that Unity has this problem still.I'm not so sure how Unity or -Unity would fix a kernel- level issue.

---

### Post by amras5584 on 2012-02-26
i have the same problem with Kubuntu 11.10, Ubuntu 11.10, Mint 11 (gnome 2) and Mint 12 (genome3), so is not problem of Unity but Kernelll, in my own opinion... i don't know the bios version of my duo, how can i know it?? sorry for my english, it is a bit late...

---

### Post by teh603 on 2012-02-28
> **amras5584 said:**
> i have the same problem with Kubuntu 11.10, Ubuntu 11.10, Mint 11 (gnome 2) and Mint 12 (genome3), so is not problem of Unity but Kernelll, in my own opinion... i don't know the bios version of my duo, how can i know it?? sorry for my english, it is a bit late...You can't flash the BIOS on Linux; you need to either assemble a flasher using FreeDos, a USB stick, and the flasher itself; or be running Windows. This is one of those cases where a hardware manufacturer finds a security flaw in Windows, decides its "working as intended," and bases an OS feature around it. The ROM flash mechanism can also be used to deliver a crafted virus that can destroy the ROMS of a known brand of motherboard; it happened to a friend back in the late '90s.

I'd really suggest you NOT flash your BIOS, though. I've heard of people bricking their computers more often than successfully flashing, which is why IMO we should handle BIOS glitches with kernel patches the way Windows does instead of telling hardware manufacturers to patch them.

---

### Post by amras5584 on 2012-03-01
EDIT, see my next message...

---

### Post by ninjaaron on 2012-03-02
Ah crap.  I deleted windows a long time ago.

---

### Post by teh603 on 2012-03-02
You can supposedly run it from a FreeDOS boot USB, but I'm still a little hesitant about it. Too many horror stories about failed BIOS flashes bricking someone's system.

Edit: What the heck, that BIOS has been out for a long time now, and some of us who have ACPI issues are already running it. Check the version number, why don't you?

---

### Post by amras5584 on 2012-03-02
sorry, sorry, sorry. it seems that is a residual thing of using windows or something, because if i reboot from windows to linux, it doesn't crash when plugged the ac connector, but if i start directly to linux it crashes allways... sorry for my english.

something similar happened with the touch screen without installing anything on Linux, when i reboot from windows to linux it worked without problems... strange things that happen...

---

### Post by teh603 on 2012-03-03
Wouldn't be the first time that hardware has behaved strangely on a reboot. I had an Acer Aspire One whose wifi would crash at the hardware level; I never found out why, but I think it was something to do with buffer flushing. You just had to power-cycle it for it to come back up. It drove a lot of the "I never turn my computer off" people bananas, though.

---

### Post by amras5584 on 2012-03-03
also, on duo if you switch off the wifi you can't switch on from linux. you have to do it from windows... it sucks because sometimes the function keys work in reverse and if you want to use F2 (to rename, for example) accidentally switch off the wifi...

---

### Post by Kirboosy on 2012-03-11
If you really want to flash your BIOS you could Download the Consumer Preview of Windows 8 and temporarily install that. (However it will wipeout your Ubuntu since Windows doesn't like to dual boot) Also I've used MiniPE verions of Windows which are like LiveCD. Either way you should be fine. Asus has a big problem with bricking their machines with BIOS flashing but I haven't had any problems with Dells and I've updated hundreds of them.

> i have the same problem with Kubuntu 11.10, Ubuntu 11.10, Mint 11 (gnome 2) and Mint 12 (genome3), so is not problem of Unity but Kernelll, in my own opinion... i don't know the bios version of my duo, how can i know it?? sorry for my english, it is a bit late...

The BIOS should have the version number under the main menu of the BIOS Configuration. Hit F2 while the computer is displaying the Dell logo to access this menu.

> also, on duo if you switch off the wifi you can't switch on from linux.  you have to do it from windows... it sucks because sometimes the  function keys work in reverse and if you want to use F2 (to rename, for  example) accidentally switch off the wifi...On mine I can turn my wifi on and off with ease. (I am running just Ubuntu and not Windows) The trick is when you turn off the card and turn it back on you need to re-enable wireless from the Networking drop down under Ubuntu. (There is a little tick box "Enable Wireless".)

---

### Post by teh603 on 2012-03-11
> **Caboose885 said:**
> The BIOS should have the version number under the main menu of the BIOS Configuration. Hit F2 while the computer is displaying the Dell logo to access this menu.
It does. I think the current version is AO2 or something like that.

---

### Post by hortera on 2012-03-12
Hi. I'm very new to Linux.
I downloaded eGalax driver. Extracted it, run terminal, but it says that I miss some files/directories.

---

### Post by teh603 on 2012-03-12
> **hortera said:**
> Hi. I'm very new to Linux.
I downloaded eGalax driver. Extracted it, run terminal, but it says that I miss some files/directories.You have to CD into the directory before running the setup script, or you get that error. That's the step that nobody seems to remember.

---

### Post by hortera on 2012-03-12
> **teh603 said:**
> You have to CD into the directory before running the setup script, or you get that error. That's the step that nobody seems to remember.

Thanks. How would I do It?

---

### Post by teh603 on 2012-03-12
> **hortera said:**
> Thanks. How would I do It?

Type CD and then the path to the folder that contains the setup script. For example:

CD /home/hgrahamcull/Downloads/Sample_Folder

Helps if you remove spaces from the stack of folders, though. It doesn't work too well with the command prompt for some reason.

---

### Post by hortera on 2012-03-13
> **teh603 said:**
> Type CD and then the path to the folder that contains the setup script. For example:

CD /home/hgrahamcull/Downloads/Sample_Folder

Helps if you remove spaces from the stack of folders, though. It doesn't work too well with the command prompt for some reason.

Thanks. Apologizes for stupid questions.

---

### Post by teh603 on 2012-03-15
> **hortera said:**
> Thanks. Apologizes for stupid questions.Ain't that stupid. Took me two hours to figure it out.

---

### Post by unused_bagels on 2012-04-26
I'm running Precise, and I have everything going great except for click-and-drag on my touchscreen.  I can only click.
 
ALSO! For those of you with fat fingers, I found this script:
```
#!/bin/bash
#
# $Zoom toggle
# Jim Klein

SCRIPT_VAR="/var/tmp"
SCRIPT_PATH=`echo $(readlink -f $0) | sed "s/$(basename $0)//g"`

if [[ "$*" =~ "silent" ]]; then
  NO_NOTIFY=1
fi

function notify {
  if [ ! "$NO_NOTIFY" = "1" ]; then
    ICON=$2
    MESSAGE=$1
    if [ "$DISTRIB_RELEASE" = "9.10" ]; then
      DISPLAY=:0.0 /usr/bin/notify-send -i $ICON -t 1500 "$MESSAGE" 2>/dev/null
    else
      USER=$(who | sed -n '/ (:0[\.0]*)$\| :0 /{s/ .*//p;q}')
      USERCNT=$(who | wc -l)
      if [ ! "$(whoami)" = "$USER" ]; then
        if [ ! "$USERCNT" -lt 1 ]; then
          su $USER -l -c "DISPLAY=:0.0 /usr/bin/notify-send -i $ICON -t 700 \"$MESSAGE\" 2>/dev/null"
        fi
      else
        if [ ! "$USERCNT" -lt 1 ]; then
          /usr/bin/notify-send -i $ICON -t 700 "$MESSAGE" 2>/dev/null
        fi
      fi
    fi
  fi
}

NICON="/usr/share/icons/zoom-in-out.png"

if [ ! -d "$SCRIPT_VAR" ]; then
  mkdir $SCRIPT_VAR 2>/dev/null
fi

if [ -e "$SCRIPT_VAR/zoom_saved" ]; then
  ZOOM_RESTORE=$(cat $SCRIPT_VAR/zoom_saved)
else
  echo nozoom > $SCRIPT_VAR/zoom_saved
  ZOOM_RESTORE=nozoom
fi

LVDS_DEVICE=$(xrandr | grep " connected" | awk '{print $1}' | grep LVDS)

function zoom_toggle {
  if [ "$ZOOM_RESTORE" = "zoom" ]; then
    nozoom
  elif [ "$ZOOM_RESTORE" = "nozoom" ]; then
    zoom
  else
    nozoom
  fi
}

function zoom {
  xrandr --output $LVDS_DEVICE --scale .75x.75
  if [ "$?" = "0" ]; then
    echo zoom > $SCRIPT_VAR/zoom_saved
  else
    notify $"Could not zoom display." $NICON
  fi
  exit 0
}

function nozoom {
  xrandr --output $LVDS_DEVICE --scale 1x1
  if [ "$?" = "0" ]; then
    echo nozoom > $SCRIPT_VAR/zoom_saved
  else
    notify $"Could not zoom display." $NICON
  fi
  exit 0
}

case $1 in
  restore)
    NO_NOTIFY=1
    if [ "$ZOOM_RESTORE" = "zoom" ]; then
      zoom
    elif [ "$ZOOM_RESTORE" = "nozoom" ]; then
      nozoom
    fi
  ;;
  *)
    zoom_toggle
  ;;
esac
echo $SCRIPT_VAR $ZOOM_RESTORE
```
Running this will change your resolution to a more finger-friendly one.  I didn't make it, I just found it.
You can apparently tie it to unity with this:
[http://ubuntutechnical.wordpress.com/2011/12/02/calling-shell-script-from-unity-launcher/](http://ubuntutechnical.wordpress.com/2011/12/02/calling-shell-script-from-unity-launcher/)
 
Can anyone help me with my click and drag problem, hmmmm? ):P
Also, sometimes my touchpad and touchscreen lose the ability to click.  It's really annoying.  How can I stop this?

---

### Post by cshep70 on 2012-04-30
Caboose885,

Thank you for the duo setup guide, it helped this newbie enjoy his machine properly.

Have you upgraded your Duo to 12.04 yet?  Disaster...

After upgrading to 12.04, I lost the touchscreen. No Prob, called up your guide and downloaded the latest EGalax drivers and installed them.  Yay - Fixed.  Except when I used ninjaaron's .screen-rotation-toggle script.  The USB mouse was properly oriented, but the touchscreen alignment was 90 degrees out of sync.

I uninstalled the new EGalax drivers.  I uninstalled the old EGalax drivers.  I removed the touchscreen helper.  I rebooted.

No touchscreen.  Good so Far.  I install the latest EGalax drivers.  The script asks if I have a serial, ps2 or USB device.  I choose USB and it claims to have found one.  The install finishes without error.  Reboot again.  

No Touchscreen.  I run the EGalax Touchscreen Utility:  No Touch Controller Found.

I change grub's "quiet splash" line like you specify and reboot.

Still no touchscreen.  I'll keep looking and trying, but if you get to the upgrade to 12.04 and run in to these problems:

PLEASE tell us how you fixed them.

Thanks Again,
Shep

---

### Post by drumour on 2012-05-01
Cshep,

See this thread re 12.04 touchscreen -> [http://ubuntuforums.org/showthread.php?t=1961558](http://ubuntuforums.org/showthread.php?t=1961558)

Like you though no luck with screen rotation & touchscreen, script and xrandr commands do rotate screen and a usb mouse works fine but the touchscreen doesnt

---

### Post by cmongini on 2012-05-01
i installed ubuntu 12.4 on my dell duo. touchscreen is fine, but when i rotate the screen i cant use the mouse anymore. ( the mouse appears simmetrically to my touch: ex: i i touch with my finger in the upper left of the screen, the mouse appears in the upper right..)i installed the touchscreen helper, but there seems to be no response, when i launch it in a terminal nothing happens...
have you got any idea? thanks

---

### Post by cshep70 on 2012-05-02
drumour, 

A follow up:  I did a clean install of 12.04 on my duo.  I followed Caboose885's directions at the beginning of this post, (update, install eGalax drivers) but I still can't get my touchscreen to work at all now. I used a newer driver than last time, I will try to uninstall them and roll back to the old driver and post my findings.

---

### Post by cmongini on 2012-05-02
well the new egalax driver worked for me... did you make sure you installed the right one? there is a note on the driver page about the commands leading you to the right version...i must say this is worth while, as the quality of the touchscreen is improved quite a lot with 12.4 and the new drive...this new version brings the dell easily to its limit, i solved it by choosing lubuntu as the GUI, which is much slimmmer 

but still.. no hint how to solve the rotation problem...

---

### Post by drumour on 2012-05-03
Cshep,

 Are you using at least linux kernel 3.2.0-24.37 (headers/headers genric-pae/ image generic-pae) from precise proposed repository? I used Synaptic, then Settings->Repositories->Updates and put a tick against precise proposed (the current latest is 3.2.0-24.38 ) .

The eGalax deamon I used is eGTouch_v2.2.1506.L-x from the eGalax site. For me this combo does not require any further tweaks or settings on my system. That said to run the egalax settings program I have to use sudo ie "sudo eGTouchU" If I try just "eGTouchU" I get "command not found"!.

All in all happy with this bit of kit but it is the flakiest system I own!

---

### Post by gizilgen on 2012-05-04
Hello,

I don't know if my problem is really with my hardware, but I thought that this is the right place to seek an answer to my problem since I have an inspiron duo.

The problem is: I had Pardus (a linux dist) and Windows 7 Pro on my duo and when precise pangolin came out, I installed it via usb stick. Now I cannot open Ubuntu unless the usb stick is mounted. When I restart my computer and the usb stick is not mounted, the computer faces me with a black screen and a single cursor blinking at the upper left on the screen.

What could be the problem?

edit: By the way, the ubuntu installation deleted the old operating systems. Now I only have precise pangolin on my duo.

---

### Post by cshep70 on 2012-05-04
drumour,

Thank you for making me look at the mistake I had made.  Your statement "The eGalax deamon I used..." is what triggered me.  I had downloaded both the daemon drivers(v2.3.xxx) AND the Touch driver (v3.07.xxxx).  My initial upgrade from 11.10 to 12.04 was just all munged up from all my newbie-learning trial and error efforts to learn Ubuntu so doing a clean install was no big deal.  When I backed up my downloads directory prior to wiping the partition I deleted the "older" eGalax driver (the daemon driver).  

I was using the wrong driver. D'oh.  My touchscreen now works thanks to you.

Thanks for the heads-up on the kernel.  I was at 3.2.0-24.37 but added the proposed repository and upgraded to 3.2.0-24.38
Not sure if I want to be out front with the newest kernels but I learn more when I have to fix something.

/Shep

---

### Post by KenBW2 on 2012-05-06
Does anyone know if the plug-in-the-power-it-dies-on-you thing is fixed in Precise? I know there's the amendment you can make to the GRUB line, but I miss suspend :(

I'm wanting to upgrade to see if this is sorted, but it sounds like it gets tricky with the touchscreen

---

### Post by teh603 on 2012-05-06
> **KenBW2 said:**
> Does anyone know if the plug-in-the-power-it-dies-on-you thing is fixed in Precise? I know there's the amendment you can make to the GRUB line, but I miss suspend :(

I'm wanting to upgrade to see if this is sorted, but it sounds like it gets tricky with the touchscreenFrom what I gather, the answer is most likely to be "never fix." The BIOS issue is officially a Dell problem, according to the kernel folks upstream. Ubuntu can patch it easily enouh, but from a recent post of "start a new bug," it sounds like nobody here wants to either.

Looks like my next tablet- if I get one- will be running Android. The Dell Duo is a great platform for Kubuntu, but thanks to its quirky BIOS, there's no desire from upstream to actually support it.

Course with all this obstructionism, Bug #1 might as well be marked invalid.

---

### Post by emmlar on 2012-05-08
I just recently updated from 11.10 to 12.04 and like others, my touchscreen stopped working.  I had been using the grub quirks configuration with 11.10 and was hoping to continue using that method, as opposed to the egalax drivers.

Thus, I have questions:

1) Are the grub quirks values the same for this version?  (And how are these determined?)

2) I'm on 3.2.0-24.37.  Would going to a newer version be likely to have any effect?

I may just temporarily reinstall 11.10, but if there is a way to make 12.04 work I'd love to hear it.

---

### Post by drumour on 2012-05-08
KenBW2 (#697),
No, it still crashes if you plug/unplug power - for me the workaround is to suspend first, then it seems to handle the switch okay

Emmlar (#699),
In my experience 12.04 absolutely needs the kernel patches in 3.2.0-24.37 (and up) AND the eGTouch_v2.2.1506.L-x daemon driver. However the driver is not that large, free/readily available and to me, as easy to install as it would be to edit in grub quirks...(with the caveat that I mentioned in post #694 that i have to use "sudo eGTouchU" rather than just "eGTouchU" to get to the preferences

---

### Post by teh603 on 2012-05-08
> **drumour said:**
> KenBW2 (#697),
No, it still crashes if you plug/unplug power - for me the workaround is to suspend first, then it seems to handle the switch okayDang it, now I'm going to have to try that again. Under anything prior, trying to plug or unplug while suspended always gave me a black screen of death.

---

### Post by unused_bagels on 2012-05-13
After a fresh install of 12.04, I see now that everything works, except two important things, both with touchscreen ONLY. (My touch*pad* works swell)

I have no hold-to-right-click, except that when I do, a context menu appears at bottom dead center of the screen, which is invariably not what I clicked on.
 
I have no double-click.

I try to change the eGalax Utility Daemon's settings to see if i can get it to work, and it always says failed to communicate with device.  What did I do wrong this time?

---

### Post by cmongini on 2012-05-14
did you all get the rotation working on 12.4? that is, when you click on rotate, dou you have control on the mouse? (in my case, when the screen is turned, the mouse is asymmetrical.. i click somewhere on the screen and the mouse appears on the opposite side..)

---

### Post by variona on 2012-05-23
@cmongini Did it work for you with 11.04,11.10 or is it your first try? Do you mean the Touchpad/USB mouse stops working or do you mean the cursor appears strangely mirrored? If the latter then you have to apply a transformation matrix on the input device (i.e the "touch"screen) which would be a property of xinput. (I'm not yet using 12.04 so I'm curious: how did you turn the screen (the output device)?)

I attach the script that I use to rotate Input and output device.(touchrotate_dell.txt)

I call it via a button that fires another script which rotates toleft if orientation is normal and vice versa.

```
#!/bin/sh

ROTATION=$(xinput list-props  11 | grep -E Matrix |grep -o 'Matrix [^ ]*' | sed 's/Matrix (137)://')

if [ $ROTATION =  1.000000, ];
then /PATH_TO_SCRIPT/touchrotate_dell toleft
else /PATH_TO_SCRIPT/touchrotate_dell normal
fi
```

---

### Post by cmongini on 2012-05-23
Dear variona, thanks for your answer! yes i had already installed the 11.10 version through the instructions at the beginning of the thread and they worked... now the screen works and it is also possible to be rotated  through the rotating screen script proposed at the beginning. it it just a problem of mirroring the mouse. ( the instructions regarding the mirroring problem at the beginning don't work.) I will test the script that you porpose and let you know

---

### Post by cmongini on 2012-05-23
the rotating script that i use is this one: 
[http://ubuntuforums.org/showpost.php?p=10398914&postcount=194](http://ubuntuforums.org/showpost.php?p=10398914&postcount=194)

how would i then connect it to your script?

---

### Post by variona on 2012-05-24
You don't - you use it instead. If you look at the script you'll see why. Your script only rotates the screen (the OUTPUT device by calling xrandr), touch is an input device that's why you need xinput. Please read the man pages xrandr and xinput for a better understanding. The attached script is a modification of a script for the T101MT therefore it has more options than needed. If it doesn't work it is most probably because your devices have a different name.(see lines 16 and 21)
The code I've posted directly is a variation of the script you use - to find out the orientation I use xinput instead of xrandr.

(try a console and type ```
xrandr -q
``` or ```
xinput --list
```)

---

### Post by unused_bagels on 2012-05-24
Awesome! I'll try the rotation script.  I was afraid to try it, as last time I installed it, all it did was make my screen go wonky when I booted up.  
 
Does anyone else have a problem with double-clicking and right-clicking?
 
Also, my touchscreen just... doesn't work sometimes.  I can point, but sometimes no clicky.  Why is it so glitchy this time around?

---

### Post by teh603 on 2012-05-24
> **unused_bagels said:**
> Awesome! I'll try the rotation script.  I was afraid to try it, as last time I installed it, all it did was make my screen go wonky when I booted up.  
 
Does anyone else have a problem with double-clicking and right-clicking?
 
Also, my touchscreen just... doesn't work sometimes.  I can point, but sometimes no clicky.  Why is it so glitchy this time around?I can make a few guesses, but most of them involve hid-multitouch being excessively new and needing a lot more testing.

---

### Post by cmongini on 2012-05-24
thanks! yes as you say it doesn't recognize the screen... the message it gives is:

Usage: touchrotate [output inputdevice] left|right|inverted|normal|toleft|toright|topdown|current

---

### Post by variona on 2012-05-25
Meaning to tell you: Please call me with a parameter. Like ```
touchrotate_dell toleft
```

and if your devices are really not recognized you will have to change thhe script to your needs.
(see my llast post on how to identify your devices)

---

### Post by cmongini on 2012-05-25
i think i got it now but it doesnt seem to work

i changed lines 21 with 
then EG=$(xinput list|grep -E 'eGalaxTouch Virtual Device for Single')

and line 16 with 
then LV=$(xrandr|grep -i 'LVDS1')

the outcome of 
xrandr -q:
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 4096 x 4096
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 223mm x 125mm
   1366x768       60.0*+   40.0  
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)

and claudia@claudia-Inspiron-1090:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; eGalaxTouch Virtual Device for Multi    	id=13	[slave  pointer  (2)]
&#9116;   &#8627; eGalaxTouch Virtual Device for Single   	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Integrated Webcam                       	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=15	[slave  keyboard (3)]

the result is that wenn i call the script with the command toleft ( for example) it kicks me out of the session!

---

### Post by cmongini on 2012-05-25
@ unuse_bagels yes i have the same problem with the hold to right click!

---

### Post by unused_bagels on 2012-05-25
> **teh603 said:**
> I can make a few guesses, but most of them involve hid-multitouch being excessively new and needing a lot more testing.

No, not multi-touch, I mean good old-fashioned double clicking.  Like for opening files.
 
> **cmongini said:**
> @ unuse_bagels yes i have the same problem with the hold to right click!
Sucks that it happens to you, but glad I'm not the only one.

---

### Post by teh603 on 2012-05-26
> **drumour said:**
> KenBW2 (#697),
No, it still crashes if you plug/unplug power - for me the workaround is to suspend first, then it seems to handle the switch okay
Ok, so having finally gotten up off my butt to test this, I've got some pretty good news.

On Lubuntu, at least, the power manager issues seem to be intermittently fixed. I say intermittently because I still get the black screen of kerneloops death from time to time, and plugging/unplugging while suspended is unreliable. That having been said, an intermittent fix is better than no fix and shows a step in the right direction.

---

### Post by variona on 2012-05-28
@cmongini

Try the different parts of the script to find out where and why you get kicked out

```
xrandr --output LVDS1 --rotate left
```

```
xinput set-prop '14' 'Coordinate Transformation Matrix' 0 -1 1 1 0 0 0 0
``` 

if your session dies you can append >error.txt to see if any useful debug output is generated and of course /var/log/ could hold some info you need to find the reason for crashing.

I'm not using 12.04 yet so all I can do is guessing - maybe someone who uses it can help?


Oops: The  $INPUTDEV parameter is not used in the xinput function call! (quickhack - sorry you would have to change it to:```
xinput set-prop $INPUTDEV 'Coordinate Transformation Matrix' 0 -1 1 1 0 0 0 0
``` and so forth) In your case the script tries to apply the Transformation Matrix on the keyboard (id 11)!

As you found out your eGalax touch has id 13 and id 14!

HTH

---

### Post by cmongini on 2012-05-28
yes the porblem lies by xinput. i let you know if i find a solution!

---

### Post by Bray90820 on 2012-06-04
for some reason every time i plug or unplug the charger the system hangs 

[ATTACH]219187[/ATTACH]

---

### Post by teh603 on 2012-06-05
> **Bray90820 said:**
> for some reason every time i plug or unplug the charger the system hangs 

[ATTACH]219187[/ATTACH]That's a running issue. tl;dr is that some nimrods way far upstream are sticking their fingers in their ears and refusing to issue a patch, and claiming that its Dell's problem to fix.

---

### Post by Bray90820 on 2012-06-06
> **teh603 said:**
> That's a running issue. tl;dr is that some nimrods way far upstream are sticking their fingers in their ears and refusing to issue a patch, and claiming that its Dell's problem to fix.

i know for a fact it is not dell i was using joli os which is based off of ubuntu and this problem does not exist

---

### Post by teh603 on 2012-06-06
> **Bray90820 said:**
> i know for a fact it is not dell i was using joli os which is based off of ubuntu and this problem does not existCan you find out what they did to patch it, and get them to submit it upstream?

---

### Post by Tomrade on 2012-06-06
Fedora seem to have fixed it in 17. not had it happen in weeks

---

### Post by Bray90820 on 2012-06-06
> **teh603 said:**
> Can you find out what they did to patch it, and get them to submit it upstream?

im sorry but i am no where near a developer and do not know how

---

### Post by robofighter on 2012-06-08
hey guys, I am trying to get the driver worker.

I have ubuntu 11.10, and I been following the instructions on the read me. But when ever I try to use the make command, I get errors. Too the best of my knowledge, I did install all the required libraries.

  CC [M]  /home/aaron/Downloads/crystalhd_linux/07032010/driver/linux/crystalhd_lnx.o
/home/aaron/Downloads/crystalhd_linux/07032010/driver/linux/crystalhd_lnx.c:356:2: error: unknown field ‘ioctl’ specified in initializer
/home/aaron/Downloads/crystalhd_linux/07032010/driver/linux/crystalhd_lnx.c:356:2: error: initialization from incompatible pointer type [-Werror]
/home/aaron/Downloads/crystalhd_linux/07032010/driver/linux/crystalhd_lnx.c:356:2: error: (near initialization for ‘chd_dec_fops.llseek’) [-Werror]
cc1: all warnings being treated as errors

make[2]: *** [/home/aaron/Downloads/crystalhd_linux/07032010/driver/linux/crystalhd_lnx.o] Error 1
make[1]: *** [_module_/home/aaron/Downloads/crystalhd_linux/07032010/driver/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-17-generic'
make: *** [all] Error 2

---

### Post by piotr5 on 2012-06-11
> **teh603 said:**
> That's a running issue. tl;dr is that some nimrods way far upstream are sticking their fingers in their ears and refusing to issue a patch, and claiming that its Dell's problem to fix.

some time ago I had the problem of crashing kernel whenever I attach my duo to a power-cord. now that's gone since I upgraded to a newer kernel. (bios-upgrade didn't help.) however, I still have the problem of kernel-oops whenever I attach or detach to/from the jbl-speaker system (the docking-station). so my question is, the patch they refuse to issue is about the cable, or about the docking-station? afterall, both are about unplugging or plugging-in the charger...

---

### Post by teh603 on 2012-06-11
Which kernel version, if you don't mind my asking?

---

### Post by Bray90820 on 2012-06-11
joli os which is ubuntu based and does not have this problem is built with a custom kernel

---

### Post by piotr5 on 2012-06-12
sorry for the misinformation, I booted into the wrong partition, with 2.6.32 kernel. that's the same kernel that crashes whenever the power-cord is plugged in/out. I think already 2.6.38 had that problem fixed. currently I'm using 3.0.9 though, and there I have no problems at all.

so it really doesn't matter if powercord or docking-station, linux will crash when you plug/unplug.

---

### Post by piotr5 on 2012-06-14
> **robofighter said:**
> hey guys, I am trying to get the driver worker.

I have ubuntu 11.10, and I been following the instructions on the read me. But when ever I try to use the make command, I get errors. Too the best of my knowledge, I did install all the required libraries.

  CC [M]  /home/aaron/Downloads/crystalhd_linux/07032010/driver/linux/crystalhd_lnx.o
/home/aaron/Downloads/crystalhd_linux/07032010/driver/linux/crystalhd_lnx.c:356:2: error: unknown field &#8216;ioctl&#8217; specified in initializer
/home/aaron/Downloads/crystalhd_linux/07032010/driver/linux/crystalhd_lnx.c:356:2: error: initialization from incompatible pointer type [-Werror]
/home/aaron/Downloads/crystalhd_linux/07032010/driver/linux/crystalhd_lnx.c:356:2: error: (near initialization for &#8216;chd_dec_fops.llseek&#8217;) [-Werror]
cc1: all warnings being treated as errors

make[2]: *** [/home/aaron/Downloads/crystalhd_linux/07032010/driver/linux/crystalhd_lnx.o] Error 1
make[1]: *** [_module_/home/aaron/Downloads/crystalhd_linux/07032010/driver/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-17-generic'
make: *** [all] Error 2
this error shows that this crystalhd driver only works up to but not including kernel-version 2.6.36 there was a transition-aera since 2.6.11 to move from the deprecated ioctl method to unlocked_ioctl. so you need a newer driver or you must alter the related function yourself so that it actually uses a lock of its own choice. that's what google told me.

anyway, no need to build the driver, ubuntu comes with one. just do "find /lib/modules/?.* -iname crystalhd\*" in the terminal to check. it's in the kernel now, maintained by the linux developers, no need to worry. however, you still must load the module and maybe provide the firmware or whatever...

---

### Post by Bray90820 on 2012-06-20
Any update on the charging bug

---

### Post by raphaelsaldanha on 2012-06-25
Hi! I'm using Ubuntu 12.04 with kernel 3.2.0.25-generic, and the eGTouch daemon driver (2012-06-21).

I'm having problems with the navigation on Nautilus. With touch, I can roll the file list  (just like an Android/iOs in a tablet or cellphone), but when I try to click in some file or folder, the system seems to don't recognize the click, or a double-click. So, I can't open files  or folder when navigation. In the left pane, I can click on the mapped folders (like Music, Images, etc), but on the main window, I can't navigate.

When I use the test area for mouse configuration, the simple and double click are recognized.

When I try the right click, the pointer moves down, and always display the menu for a right clicking in the blank area of a folder. So, when I try to right click a specific folder or file, the menu that appears is related to the relative root folder, with the pointer moved.

With some research, I have found a bug listed on [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/913164"), relating this sort of problem to kernel modifications and suggesting a try to upgrade to a RC kernel.

Is there anyone with the same problem? Is there a know solution for this?

Thank in advance!

---

### Post by Tomrade on 2012-07-05
opensuse 12.2 also seems to have a fixed kernel, could be fixed upstream, if both fedora 17 and opensuse 12.2 seem fine with kernel 3.4

---

### Post by Bray90820 on 2012-07-11
is there a way we could port the kernel from a working distro

---

### Post by ehofman on 2012-07-18
Hi,

I might have a work around for the power/kernel oops problem.

I had the same problem, but solved it as folows:

First of all use the i386 and not the x64 version of ubuntu 12.04.

Still having problems i tried upgrading the kernel manualy, from kernel version 3.4 and up i am rarley having problems with connecting power or docking.

There are some rules: 
-Boot on battery and you're fine plugging in and out the charger.
-suspend on battery = wake-up on battery, suspend with charger/dock = wake-up with charger/dock.

If you folow these basic steps, the kernel oops will be gone (most of the time). It will eventualy oops, but now it's more like 1 in 50 times, wich is better then every time.

---

### Post by spacestationspaz on 2012-08-30
> **variona said:**
> @cmongini Did it work for you with 11.04,11.10 or is it your first try? Do you mean the Touchpad/USB mouse stops working or do you mean the cursor appears strangely mirrored? If the latter then you have to apply a transformation matrix on the input device (i.e the "touch"screen) which would be a property of xinput. (I'm not yet using 12.04 so I'm curious: how did you turn the screen (the output device)?)

I attach the script that I use to rotate Input and output device.(touchrotate_dell.txt)

I call it via a button that fires another script which rotates toleft if orientation is normal and vice versa.

```
#!/bin/sh

ROTATION=$(xinput list-props  11 | grep -E Matrix |grep -o 'Matrix [^ ]*' | sed 's/Matrix (137)://')

if [ $ROTATION =  1.000000, ];
then /PATH_TO_SCRIPT/touchrotate_dell toleft
else /PATH_TO_SCRIPT/touchrotate_dell normal
fi
```

Variona, your script is the closest I've come to getting touchpad rotation working, but it only works for the y axis. For x axis the screen seems really confused, like its also taking the x axis input from y position. I think it may have something to do with multitouch. Any ideas?

---

### Post by loxley108 on 2012-09-06
Hi

I really hope someone can help me.
 
I have a Dell Inspiron Duo 1090 and have now got the touch screen working and have been looking for a good web browser to use on it.
 
I would really like to use Opera Mobile for this as it has a built in keyboard and seems quick.  I am using the latest version of Ubuntu (12.04.01) and installed Opera Mobile via the Opera website.

The problem is when I run it it doesn't respond to the touch screen at all - in every other way the Dell touch screen works fine (and works with Chromium ,Firefox etc) but not with Opera Mobile.  

I have tried setting the emulator for different models but still not success and have tired touch and tablet options.

This is very frustrating as I really wanted to use Opera Mobile on the Duo.

Does anyone have any suggestions to help me? I would really appreciate it.  I have spent hours searching online without any success.

Thanks so much

---

### Post by qrrbrrbirlbel81 on 2012-09-17
has anyone else noticed that the touchscreen doesn't exactly "play well" with kde's plasma widgets and netbook workspace?  I'm running kde 12.04 with the egtouch driver installed.  i was really excited to hook up caboos's kdeplasmaswitcher script, but then very bummed out when my touch screen wouldn't interact with the gui at all.  to clarify, it doesn't register a press on the screen as a click.  when i do this the cursor goes to where i "clicked" and just sits there as if i only wanted to put the cursor there and brings up a tooltip.  as a side note, the touch screen does work entirely while inside of programs such as chromium and the like....it is only when i try to use it with kde's plasma stuff.

---

### Post by JaseP on 2012-09-25
Also looking for a status,... Re: Working yet on K/Ubuntu 12.04?

Or is power issue still a problem?
What about rotation and touch screen input?

KDE a problem?

*Note: Looks like my Bluetooth fix is no longer necessary, ... good.*

---

### Post by piotr5 on 2012-09-26
just in case you don't know, there were several new versions of the eGalaxy driver this summer. now I'm testing a new thing: I observed that after suspend touchscreen doesn't work the way it should. then I read the guide and discovered ubuntu is missing a kernel-patch to make eGalaxy work correctly. this patch just disables the in-kernel drivers for joystick and mouse. doesn't sound urgent, and probably the driver will disable them too. however, after suspend kernel will enable all drivers again, so I have created a new file: /etc/pm/sleep.d/66_eGTouch :

```

#! /bin/sh

if [ ! -x /usr/bin/eGTouchD ]; then
    exit 0
fi

case $1 in
     suspend|suspend_hybrid|hibernate)
        /usr/bin/eGTouchD -k
        ;;
     resume|thaw)
        /usr/bin/eGTouchD
        ;;
esac

```let's try how well this will work...

**Edit: **don't forget to do
sudo a+x /etc/pm/sleep.d/66_eGTouch
after the sudo gedit /etc/pm/sleep.d/66_eGTouch
(for kde use something else instead of gedit)
all that in a Terminal or Konsole

---

### Post by matgras on 2012-10-04
help, i am an noob to ubuntu (ive got it about 2 weeks)  but i want the graphics card drivers running but i dont know how, i cant find tutorials anywere :(

---

### Post by piotr5 on 2012-12-12
I just finished setting up mine by following: [http://knowledge.evot.biz/documentation/how-to-compile-and-install-the-broadcom-crystal-hd-hardware-decoder-bcm70012-70015-driver-on-ubuntu](http://knowledge.evot.biz/documentation/how-to-compile-and-install-the-broadcom-crystal-hd-hardware-decoder-bcm70012-70015-driver-on-ubuntu)

only problem with that howto is it doesn't mention that beforehand you need to install linux-headers. then

ls -l /lib/modules/`uname -r`/build

to check if the make-files will find them for your current kernel. (those are ` characters above and not ' characters.) i.e. you will need to get the headers for exactly the same kernel-version your autoupdate installed last. if you have done everything right in this howto you will get a white cHD logo among your panel-applets. while playing a flash-video this will become somewhat blue. (strangely, after suspend it is grey again because of being turned off.)

I should also mention that #include <linux/delay.h> is already in the newest version, the other change mentioned in the howto isn't. just put it as the first thing in the file, or down below the comments where other #include lines are located. and maybe to the hackers, after compiling the driver there will be a complaint that the module isn't really written the way modules should be written, but it works anyway. guess there's still something to do before it can be included in the kernel. so you should check the [changelog]("http://git.linuxtv.org/jarod/crystalhd.git") regularly. if there are any news, do a git pull

---

### Post by JaseP on 2013-02-19
> **ehofman said:**
> Hi,

I might have a work around for the power/kernel oops problem.

I had the same problem, but solved it as folows:

First of all use the i386 and not the x64 version of ubuntu 12.04.

Still having problems i tried upgrading the kernel manualy, from kernel version 3.4 and up i am rarley having problems with connecting power or docking.

There are some rules: 
-Boot on battery and you're fine plugging in and out the charger.
-suspend on battery = wake-up on battery, suspend with charger/dock = wake-up with charger/dock.

If you folow these basic steps, the kernel oops will be gone (most of the time). It will eventualy oops, but now it's more like 1 in 50 times, wich is better then every time.

I've been thinking about this... My understanding of the Kernel oops is that there are two instances of power devices being reported on the system (correct me if that's wrong),... Does anyone think a udev rule to basically ignore the extraneous power device might work to do an end-run around the oops???

---

### Post by Bray90820 on 2013-02-21
About the charging issue the JolliOS kernel seems to work so maybe someone could have a look at it and see whats going on

---

### Post by Kirboosy on 2013-03-21
Hi all!

Been a while since I've updated anything. There are some noticeable changes in 12.10 for our hardware. The power problem has been resolved. I can plug and unplug my computer without any crashes. I didn't do anything special either. 

Also touchscreen works out of the box. However I would recommend installing the proprietary drivers from eGalax still. I hope since Ubuntu phone has been announced it will push touchscreen support in the full desktop version ever further.

Finally, I'm updating the guide. Trying to clean it up and add the new information. Sorry its taken so long. Hopefully I am back in the community again helping out where I can.

---

### Post by piotr5 on 2013-04-03
nice to see this guide isn't dead. I made a new discovery: the  accelerator driver is going into the official kernel! I can't await it,  it's in the release-candidate of 3.9, so I guess it will take some time  till ubuntu will pick it up. here's what I did do:

copy  linux-master/drivers/iio/{accel,common}/ from the zip-file provided by  [https://github.com/torvalds/linux](https://github.com/torvalds/linux) into drivers/iio of my currently used  linux-sources 3.7.10 (and I also copied the magnetometer directory too, but it doesn't work).  then I further copied linux-master/include/linux/iio into include/linux  of my sources (I didn't overwrite any existing files though).  alternatively just use the rc-version directly.

in menuconfig I  did choose the st_accel_i2c driver and the trigger driver as modules (in  drivers/iio). the buffer driver I did leave unchecked. (compilation  error if I did build that.) then compile a new kernel and restart linux to use it.

modprobe i2c_i801
modprobe st_accel_i2c

in order to figure out what i2c to use I did do

cat /sys/class/i2c-adapter/i2c-*/name

to get

SMBus I801 adapter at 5000

at  the end, i.e. the last entry in the /sys/class/i2c-adapter/i2c-* is the  one I want, it's i2c-6 for me. after reading  drivers/iio/accel/st_accel.h in the kernel sources I learned that the  iio driver is only reacting to a device called "lsm303dlh_accel".  therefore I did do

echo lsm303dlh_accel 25 >/sys/class/i2c-adapter/i2c-6/new_device

and  automatically the device was detected and I got a new  /sys/bus/iio/devices/iio\:device0 directory to play around with. for  example I can do

while true ;do echo `cat  /sys/bus/iio/devices/iio\:device0/in_accel_x_raw`, `cat  /sys/bus/iio/devices/iio\:device0/in_accel_y_raw`, `cat  /sys/bus/iio/devices/iio\:device0/in_accel_z_raw` ;done

and  observe how tilting my duo will decrease z-axis and increase the  otherwise zero-ish value of some other axis. windows uses that for  triggering screen-rotation. (I wouldn't recommend parroting that  though.) but I think it would be more important to have a program  detecting when the duo is in free-fall, to turn off hdd like in  windows...

---

### Post by Kirboosy on 2013-04-06
I have slowly been working on migrating my tutorial to the wiki.

Here is the link. 

[Dell-Duo/Inspiron-1090 Wiki]("https://help.ubuntu.com/community/dell-duo/inspiron-1090")

This is now an "Opensource guide." Feel free to add and contribute to the wiki.

---

### Post by alkitchen on 2013-06-10
Sorry, total noob here (as my son would say)…  My kids seem to destroy computers with viruses, so I decided I would put Ubuntu 13.04 on my daughters Inspiron Duo.  The more I have looked at Ubuntu the more I like it.  I was looking at a YouTube clip about Bodhi, and how when he flipped the screen it took on a while new tablet UI.  I think I found the video by reading through this thread [http://www.youtube.com/watch?v=7qMTCXPybH4](http://www.youtube.com/watch?v=7qMTCXPybH4).  Does Ubuntu have/do something similar?  I apologize if this is a stupid question.  

Thanks for all of your help.

---

### Post by Kirboosy on 2013-09-10
It depends on your Desktop Enviroment. If you are using regular Ubuntu with Unity there isn't such a way. However if you are using KDE or another desktop enviroment you can make it possible. I have a link in the main post to a youtube video on how to setup KDE to use the signals from the lid switch.

If you want to use his desktop enviroment he is using [Enlightenment ]("http://www.enlightenment.org/")

---

### Post by piotr5 on 2013-12-10
just wrote a few lines on the wiki. however, I've encountered a problem that might affect ubuntu in future: gdm now requires systemd since no other init-system supports what gnome3.8 needs. so I had to write my own eGalaxy service file for it. I'm in gentoo and there all systemd services are located in /usr/lib/systemd/, in ubuntu this might differ. I don't know if the driver for eGalaxy has been updated with systemd support, their site is unreachable. what I wrote is:

**/usr/lib/systemd/system/eGalaxy.service:**```

[Unit]
Description=eGalaxy Touch Screen Multitouch Daemon
After=gpm.service
After=gdm.service

[Service]
ExecStart=/usr/bin/eGTouchD -f
StandardOutput=syslog
Type=forking

[Install]
WantedBy=multi-user.target
WantedBy=graphical.target

```

---

### Post by colonel-dan on 2014-05-14
Hi all, decided to try throwing Kubuntu 14.04 on my duo.

eGalaxy works out of the box but I installed the proprietary drivers.  Only issue is that (as mentioned elsewhere) plasma doesn't seem to pick up clicks when the touchscreen is in normal mode.  It registers the point position but not the click.  Other applications however do register the click, so I think it's something weird in plasma.  If I switch to tablet mode it doesn't register any clicks but then when I go back to desktop mode plasma registers the clicks until I click on a widget.  Very strange, and I would appreciate any help tracking this down because I would love to get it working.  I have seen elsewhere that KDE running on top of Debian doesn't have the same problem so I'm not sure where to start.

Also had problems getting the linked CrystalHD drivers to work but found this patched set on git which worked a treat:
[https://github.com/yeradis/crystalhd](https://github.com/yeradis/crystalhd)

---

### Post by Kirboosy on 2014-05-14
I just recently reinstalled regular Ubuntu 14.04 64 bit on my Duo. Most  everything is working out of the box but I'll make sure to take notes  and update the wiki as fit. 

Also I will probably strip the guide of everything except Ubuntu 12.04 and 14.04 (Since they are the only ones in support)

---

### Post by mörgæs on 2014-09-27
Now the guide spans 76 pages but searching for 'temperature' yields no results, so I have to ask: How hot does a Dell Duo get when running Buntu and does the fan control work as expected?

---

