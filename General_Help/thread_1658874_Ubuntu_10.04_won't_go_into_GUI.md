---
title: "Ubuntu 10.04 won't go into GUI"
date: 2011-01-03
forum: General Help
---

### Post by rapattack1 on 2011-01-03
Hi after changing what i thought was a dead psu and replacing the video card because i thought that was not compatible Ubuntu doesn't want to go into the the GUI.
Stops at :

Ubuntu 10.04.1 LTS carla-desktop tty1
carla-desktop login:

I googled and someone said try ctrl+alt+F7 but i just get a lot of things that i do not understand and i have to do ctrl+alt+del to get out. Then it restarts and goes through it again.

The first boot afterwards i got some error wanting me to deal with xconfig i think. Something about that ununtu was going into low graphics mode. I think i changed things correctly but maybe not. Don't remember now what that was because of short term memory problem...sorry my illness is hard to explain.

I have tried a few restarts and i am getting different things everytime. This one is still stopping at the login but the text above says :
*Timidity++ ALSA midi emulation...
Home directory /etc/timidity not ours.
and there is an OK next to that on the far right.

At first when i do ctr+alt+del it shows the Ubuntu flash screen if that is what it is called.

On the next boot nothing about timidity is mentioned.

And the next reboot timidity thing is back again...

What is all this? Would appreciate any help thanks :0)

---

### Post by seawolf167 on 2011-01-03
If you are not using the Ubuntu Server version, try this after you login through the command line (assuming the problem is that the switched graphics card is causing the problem because of incorrect settings/configurations):
 
[FONT=monospace]```
startx
```

[/FONT]You can try to start the script manually by doing:
 	
```
sudo /etc/init.d/gdm start
```

Though in 10.10 this should work too:

```
sudo service gdm start
```

If that doesn't start, you can attempt to reconfigure the xserver (which may be the case from the message you said you were getting)

```
sudo dpkg-reconfigure xserver-xorg
```

Then follow the prompts

---

### Post by rapattack1 on 2011-01-03
I m afraid nothing worked...there is mention of the nvidia kernel module...no drivers avilable.....too much to list.
A lot of about the xserver. I better go sleep and tackle this in 24hours...got a busy day :0)
Thanks

---

### Post by oldfred on 2011-01-03
How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

I had to do this with my Nvidia 9600GT:
boot from the cd, press F6 and then select the nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed Nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.
Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

---

### Post by rapattack1 on 2011-01-03
Ah Most of that info is too advanced for me and there are pieces missing. I got into that part to select nomodeset and pressed q to get out but don''t understand where you mention install. Ubuntu is already installed ....should i reinstall?

---

### Post by wkulecz on 2011-01-04
I appear to have the same issue on one 10.04 system.  Was working fine, did a bunch of updates before Xmas and shut it down for the Holidays.  Won't start now.  Get a "low graphics mode" dialog box and system is locked up no mouse, no keyboard -- capslock LED will not toggle.

I can't figure out how to boot to what was the old recovery console/busybox boot as the recovery options in the grub2 menu aren't there  :(

Edit:

This system is multiboot with Windows, 6.06, 8.04 & 10.04.  Only the 10.04 system has problems, the others work fine so its not a hardware issue.

---

### Post by nerdy_kid on 2011-01-04
timidity is a MIDI synthesizer -- dont worry about that, its not related. 


ok first off, is this pc connected to the internet?  It will need to be.

This should get you the display back:

```

sudo -i
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
echo "blacklist nvidia" >> /etc/modprobe.d/blacklist.conf
reboot

```

that backs up your xorg config, blacklists the nvidia driver should it exist and reboots the system.  You should have a low quality display after that.


Then onto getting the nvidia drivers to work:

First you want to see what card you have.  Go to a terminal and
```

lspci | grep VGA

```

Please post the output.


Then we want to see what drivers are around, once again in a terminal:
```

jockey-text --list

```

Post that back too please.

---

### Post by wkulecz on 2011-01-04
I got the system to at least boot up by dual booting into 8.04 and replacing xorg.conf with xorg.config.failsafe on my 10.04 partition.

If you can boot a the live CD, this might at least get you started with fixing what is broken.

But I still have no mouse and a locked up keyboard, so I'm not really anywhere yet. :(

---

### Post by rapattack1 on 2011-01-04
Ok well this time i was connected to the net as you said and it went into low graphcs mode by itself so i went to the next command. The terminal told me i have a nvidia corporation nv18 [Geforce MX 440 AGP 8x] (rev a2)

after i did jockey-text --list i got:
kmod:nvidia_current - nvidia_current (propriety, enabled, not in use)

---

### Post by nerdy_kid on 2011-01-04
> **rapattack1 said:**
> Ok well this time i was connected to the net as you said and it went into low graphcs mode by itself so i went to the next command. The terminal told me i have a nvidia corporation nv18 [Geforce MX 440 AGP 8x] (rev a2)

after i did jockey-text --list i got:
kmod:nvidia_current - nvidia_current (propriety, enabled, not in use)


ok.

do this please:

```

sudo apt-get --purge remove xserver-xorg-video-nouveau xserver-xorg-video-nv

```

Then reboot.

Now, when the pc boots:

as soon as the BIOS screen goes away press and hold <shift>  If you don't know what the BIOS screen is, then just keep hitting <shift> (dont hold it) until you get reach a black and white menu that has "ubuntu linux kernel blahblah" as one of the entries.   Press "e" while the topmost entry is selected.  You will be given a line of text to edit.  Use backspace to delete "quiet splash" off of the end of the line of text.  now add the line "nomodeset" without quotes.  Press <ctrl> <x>.  The system should boot, and hopefully you will have a high quality display.  Once you are logged in to the system, open a terminal and run "nvidia-settings" without quotes.  If the driver loaded correctly you will see the nvidia control utility.  If not, then you will get a error message.

---

### Post by rapattack1 on 2011-01-05
OK did the first command but then when i kept tapping shift i got no reaction. The system went to the process of low-graphics mode. There is an option to reconfigure within that. Dunno how to explain it. I don't know how to use that option thingy.

---

### Post by rapattack1 on 2011-01-08
Hi I was so close....can anyone help?

---

### Post by oldfred on 2011-01-08
Have you looked in system, administartion, additional hardware drivers or in 10.04 in may be just hardware drivers?

---

### Post by rapattack1 on 2011-01-08
Do i reactivate the driver?

---

### Post by nerdy_kid on 2011-01-08
> **rapattack1 said:**
> Do i reactivate the driver?

you could try that.

---

### Post by nerdy_kid on 2011-01-08
ok here is another way to do what I told you in my other post.

```

sudo cp /etc/default/grub /etc/default/grub.bak
gksu gedit /etc/default/grub

```

run both those, then in the text editor that pops up:

look for the line "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" "
replace the "quiet splash"  with "nomodeset"  -- make sure you keep the quotes.  Save the file, then run:

```

sudo update-grub

```

then reboot.  You will not have a pretty splash this time, just a bunch of text.  I'll tell you how to fix that if your graphics work right.  Once the system is up, login and run nvidia-settings in a terminal.  If it gives you an error then the driver is still not working.  Let me know what happens

---

### Post by pbpersson on 2011-01-08
I had this same problem and after none of these fixes worked I am now doing another fresh install.

However, I got a little wild - I think I did:

```
apt-get remove --purge nvidia*
```

And at that point I could no longer get to the recovery console so I gave up.  I thought when I rebooted the system would replace what it needed and do it all correctly.

You know....a little knowledge can be very dangerous

---

### Post by rapattack1 on 2011-01-08
The Hardware drivers thing didn't seem to do anything. Maybe a reboot will see something else.

nerdy_kid...yeah i posted i had problems with the commands a few days ago. Anyway did up to gksu gedit /etc default/grub
and got the attached image....nothing in there to edit.

pbpersson-Thanks i will hold off on the purging....i feel cautious. I was thinking last night i should reinstall Ubuntu. I just gotta have time to backup files and it is hard to find that time. This is a fairly new install so there is not a lot to backup but it is summer here in Oz and too much to do :0)

---

### Post by pbpersson on 2011-01-09
My problem was that I was using the trick where you:

1.  Save a list of all your packages from your old system (with your /home on another partition
2.  Do a fresh install, formatting the root before the fresh install
2.  Use the file with the list of packages to re-install everything and since all your configuration files and preferences are on your old /home, it is like an upgrade but with a fresh install.

**HOWEVER**, in re-installing all my old packages I think I installed old drivers and xserver items from my old Mint 8 system on top of my new Lucid Lynx system?  I think that was a huge part of the problem.  Everything is working great for me now after deleting all that stuff from the list and re-installing all the other packages.

---

### Post by rapattack1 on 2011-01-09
Oh i don't know how to save packages list yet. Didn't know you could do that :0)

---

### Post by oldfred on 2011-01-09
You can export list with command line and reimport from command line or use synaptic.


from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

 dpkg --get-selections > ubuntu-file

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)
File > Save Markings As, tick the "Save full state, not only changes". If you don't tick the 'full state', you will probably get an empty file.
To restore, you would use File, 'Read Markings'

If you want a list that includes versions and more info, so you know what it is as the name is not always clear.

List with explanations of programs, not for reinstall
dpkg -l > ~/Desktop/installed_programs.txt

---

### Post by rapattack1 on 2011-01-09
Thanks oldfred that is very handy!!!

---

### Post by nerdy_kid on 2011-01-09
> **rapattack1 said:**
> The Hardware drivers thing didn't seem to do anything. Maybe a reboot will see something else.

nerdy_kid...yeah i posted i had problems with the commands a few days ago. Anyway did up to gksu gedit /etc default/grub
and got the attached image....nothing in there to edit.

pbpersson-Thanks i will hold off on the purging....i feel cautious. I was thinking last night i should reinstall Ubuntu. I just gotta have time to backup files and it is hard to find that time. This is a fairly new install so there is not a lot to backup but it is summer here in Oz and too much to do :0)

you really shouldn't need to do a reinstall...

I am sorry, it is 
```

gksu gedit /etc/default/grub

```
that should work.  I somehow hit the space bar instead of the slash

---

### Post by rapattack1 on 2011-01-09
OK that command worked....well got to do the reboot yet...not sure about the spacebar comment but i will keep that in mind with whatever i see when i reboot :0)
Unfortunately the system has not informed me of anything so no progress. Still booting into low-graphics mode. I did get the text scrolling old way of linux booting...if that makes sense? I have used ubuntu and debian for 3 years now.

---

### Post by nerdy_kid on 2011-01-10
ok, try running 
```

sudo nvidia-xconfig

```

then reboot again.

---

### Post by rapattack1 on 2011-01-10
```
carla@carla-desktop:~$ sudo nvidia-xconfig
[sudo] password for carla: 

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```

OK i have rebooted....what next ? :0)

---

### Post by wkulecz on 2011-01-12
> List with explanations of programs, not for reinstall
dpkg -l > ~/Desktop/installed_programs.txt

Thanks that was some useful dpkg info, but this command soesn't appear to list the source packages I've installed.  For things like gstreamer figuring out the actual name you need to use in apt-get source is not so easy.

Any way to recover this?

---

### Post by oldfred on 2011-01-12
If you have added sources this makes a backup. But note that the version may be different if an upgrade.

But do not just import all sources as that can lead to issues of versions:
[http://askubuntu.com/questions/2038/backup-software-sources](http://askubuntu.com/questions/2038/backup-software-sources)
sudo cp /etc/apt/sources.list ~/sources.list.backup

this lists with dpkg but if not installed with dpkg, I am not sure if it will show:
List with explanations of programs, not for reinstall
dpkg -l > ~/Desktop/installed_programs.txt

Alternative way with aptitude:
aptitude --display-format '%p' search '?installed!?automatic' > ~/my-packages
sudo xargs aptitude --schedule-only install < my-packages 
sudo aptitude install

A tabular list of all manually installed packages can be obtained using:
aptitude search '~i!~M'

Not sure why I saved these links - more info?
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/122047](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/122047)
[http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s03s05.html](http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s03s05.html)
aptitude --disable-columns -F 'no_dependents %p' search '~i!~M!~R(~i)'

---

### Post by rapattack1 on 2011-01-12
OK nerdy_kid whats next?

---

### Post by nerdy_kid on 2011-01-13
alrighty, this thing does not seem to want to cooperate :lol:

do these:

```

sudo apt-get install nvidia-current

```
that should say something about being installed, just double checking.

now, with you logged in:
```

lsmod | grep nvidia

```

if that returns something, then please post the file /etc/X11/xorg.conf  and /var/log/Xorg.0.log  and /var/log/Xorg.1.log

if not, then

```

zip -r $HOME/Desktop/blacklists.zip /etc/modprobe.d/

```
post the blacklists.zip in your desktop.

---

### Post by rapattack1 on 2011-01-13
```
carla@carla-desktop:~$ sudo apt-get install nvidia-current
[sudo] password for carla: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-current is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
carla@carla-desktop:~$ lsmod | grep nvidia
carla@carla-desktop:~$ zip -r $HOME/Desktop/blacklists.zip /etc/modprobe.d/
  adding: etc/modprobe.d/ (stored 0%)
  adding: etc/modprobe.d/blacklist.conf (deflated 50%)
  adding: etc/modprobe.d/blacklist-oss.conf (deflated 70%)
  adding: etc/modprobe.d/alsa-base.conf (deflated 73%)
  adding: etc/modprobe.d/blacklist-watchdog.conf (deflated 68%)
  adding: etc/modprobe.d/nvidia-graphics-drivers.conf (deflated 46%)
  adding: etc/modprobe.d/blacklist-modem.conf (deflated 35%)
  adding: etc/modprobe.d/blacklist-firewire.conf (deflated 44%)
  adding: etc/modprobe.d/blacklist-framebuffer.conf (deflated 60%)
  adding: etc/modprobe.d/blacklist-ath_pci.conf (deflated 27%)
  adding: etc/modprobe.d/libpisock9.conf (stored 0%)
  adding: etc/modprobe.d/blacklist-local.conf (stored 0%)
```

Yes it is stubborn :0)

---

### Post by nerdy_kid on 2011-01-14
> **rapattack1 said:**
> ```
carla@carla-desktop:~$ sudo apt-get install nvidia-current
[sudo] password for carla: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-current is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
carla@carla-desktop:~$ lsmod | grep nvidia
carla@carla-desktop:~$ zip -r $HOME/Desktop/blacklists.zip /etc/modprobe.d/
  adding: etc/modprobe.d/ (stored 0%)
  adding: etc/modprobe.d/blacklist.conf (deflated 50%)
  adding: etc/modprobe.d/blacklist-oss.conf (deflated 70%)
  adding: etc/modprobe.d/alsa-base.conf (deflated 73%)
  adding: etc/modprobe.d/blacklist-watchdog.conf (deflated 68%)
  adding: etc/modprobe.d/nvidia-graphics-drivers.conf (deflated 46%)
  adding: etc/modprobe.d/blacklist-modem.conf (deflated 35%)
  adding: etc/modprobe.d/blacklist-firewire.conf (deflated 44%)
  adding: etc/modprobe.d/blacklist-framebuffer.conf (deflated 60%)
  adding: etc/modprobe.d/blacklist-ath_pci.conf (deflated 27%)
  adding: etc/modprobe.d/libpisock9.conf (stored 0%)
  adding: etc/modprobe.d/blacklist-local.conf (stored 0%)
```

Yes it is stubborn :0)

ok, so the driver is not loading.  can you attach the file "blacklists.zip" in your desktop?
While you are at it, I guess you could attach /etc/X11/xorg.conf and /var/log/Xorg.0.log and /var/log/Xorg.1.log too.  Just so I can double check all the config

---

### Post by rapattack1 on 2011-01-14
Ah sorry i don't know how to do that. Haven't heard of that yet. Can you tell me how? :0)

---

### Post by nerdy_kid on 2011-01-15
no problem:

click new reply, scroll down to Additional Options and then click "manage attachments".  In the box that pops up, click the first "choose file' button, go to your desktop, select the zip file, and click open.  Then click the second choose file button, click "file system" in your places, go the "etc" folder, then go to the "X11" folder.  Select xorg.conf, and click open.  Click the third choose file button, click file system in your places, go to "var", go to "logs" select Xorg.0.log and click open.  Repeat that for Xorg.1.log.  Then click the upload button.  Wait until it finishes, then hit submit new thread.

---

### Post by rapattack1 on 2011-01-15
Did i do this right?

---

### Post by nerdy_kid on 2011-01-16
> **rapattack1 said:**
> Did i do this right?

thats great, but you forgot the Xorg logs.  It might be ok though, as I think I found the culprit :D

run:

```

sudo rm /etc/modprobe.d/blacklist-local

```

then reboot.  If it still doesn't work, please attach the X11 logs like I showed you in my previous post.

---

### Post by rapattack1 on 2011-01-16
```
carla@carla-desktop:~$ sudo rm /etc/modprobe.d/blacklist-local
[sudo] password for carla: 
rm: cannot remove `/etc/modprobe.d/blacklist-local': No such file or directory

```

Um i am a bit lost now as to what that is that i forgot to get and how to get it. I am going over the older posts but am not understanding what to do sorry. I think i am having a brainless day lol.

---

### Post by nerdy_kid on 2011-01-17
sorry, my mistake:  its

```

sudo rm /etc/modprobe.d/blacklist-local.conf

```

then reboot.


Try the above, and if it still doesn't work, then do this for the xorg logs:

click new reply, scroll down to Additional Options and then click "manage attachments". In the box that pops up, click the first "choose file' button, go the "etc" folder, then go to the "X11" folder. Select xorg.conf, and click open. Click the second choose file button, click file system in your places, go to "var", go to "logs" select Xorg.0.log and click open. Click the third choose file button click file system in your places, go to "var", go to "logs" select Xorg.1.log and click open.  Then click the upload button. Wait until it finishes, then hit submit new thread.

---

### Post by rapattack1 on 2011-01-17
OK nothing happened after the command and reboot so have attached the things things. Hope i did it right. Btw way it is log not logs unless i was looking in the wrong place?;)

Oh hang on i don't think those things attached. Maybe they are not allowed?

---

### Post by nerdy_kid on 2011-01-17
run

```

cp /var/log/Xorg.1.log ~/Desktop/log.txt

```

then attach the log.txt file that is on your desktop.

run this too,

```

sudo update-initramfs -u

```

then reboot again, and see if that makes a difference.  Hopefully once I have the log I will be able to tell exactly why the driver is not loading.

---

### Post by rapattack1 on 2011-01-18
Oops the forum is saying that the file size of the txt file is too large.

```
carla@carla-desktop:~$ sudo update-initramfs -u
[sudo] password for carla: 
update-initramfs: Generating /boot/initrd.img-2.6.32-27-generic

```

rebooting now....ok no change sorry :0(

---

### Post by nerdy_kid on 2011-01-18
copy and paste the log here and post the link:  [http://pastebin.com/](http://pastebin.com/)

---

### Post by rapattack1 on 2011-01-18
Sorry i don't understand what your saying and i have never seen that sort of website. Don't know what to do with it :0)
Do you mean to paste the txt ?

---

### Post by nerdy_kid on 2011-01-18
> **rapattack1 said:**
> Sorry i don't understand what your saying and i have never seen that sort of website. Don't know what to do with it :0)
Do you mean to paste the txt ?

yeah, open up the log.txt file on your desktop, select all the text, copy it, paste it in the web site, click submit then copy and paste the url (web address) back here.

---

### Post by rapattack1 on 2011-01-18
Is this right? [http://pastebin.com/mLm6NtaY](http://pastebin.com/mLm6NtaY)

---

### Post by rapattack1 on 2011-01-18
Is this right? [http://pastebin.com/mLm6NtaY](http://pastebin.com/mLm6NtaY)

---

### Post by nerdy_kid on 2011-01-20
yeah, but that is not all of the log.  I need all of the log.  Sorry there isn't an easier way to do this!

---

### Post by rapattack1 on 2011-01-20
Oh i don't know what i am missing?

---

### Post by nerdy_kid on 2011-01-20
open the log again, select all the text by pressing the ctrl key and the A key at the same time.  copy and paste that into the web site, and then post the link.

---

### Post by rapattack1 on 2011-01-20
OK did i do it right this time? [http://pastebin.com/zgziQ8Qn](http://pastebin.com/zgziQ8Qn) :D

---

### Post by nerdy_kid on 2011-01-21
yeah thats better :D

ok, got some info out of that which is useful.  Can you do the same thing for the /etx/X11/xorg.conf file?  and that should be the last file I need.

Then do this in a terminal:

```

sudo modprobe nvidia

```
hopefully that will give an error, if you could post that along with the xorg log like I said up there ^ that would be great.

---

### Post by rapattack1 on 2011-01-21
Gee i am lost again. I looked back several pages and can't find the specific thing to do whatever so i thought i would just paste it here
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Thu Apr 22 11:44:23 PDT 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

```
carla@carla-desktop:~$ sudo modprobe nvidia
[sudo] password for carla: 
FATAL: Module nvidia not found.

```

---

### Post by nerdy_kid on 2011-01-22
ok thats fine, everything looks good.

run this please:

```

sudo apt-get --purge remove libvdpau1 nvidia-cg-toolkit nvidia-common nvidia-current nvidia-settings

```

reboot, then open up hardware drivers, select the nvidia driver and click "activate" reboot again, and then run
```

nvidia-settings

```

if the program that pops up gives you an error, then run
```

sudo modprobe nvidia-current

```
and post the output.

if the program that pops up doesn't give you an error, then the driver is installed and working.

---

### Post by rapattack1 on 2011-01-22
OK did the first command and rebooted. Looked at hardware drivers and it said 'No proprietary drivers are in use on this system'. Everything is blank below that so there is nothing to select and nothing to enable :0(

```
carla@carla-desktop:~$ sudo modprobe nvidia-current
[sudo] password for carla: 
FATAL: Module nvidia_current not found.

```

---

### Post by nerdy_kid on 2011-01-22
run this instead of using the hardware drivers:

```

sudo apt-get install nvidia-current

```

and then do the rest of my previous post.

---

### Post by rapattack1 on 2011-01-22
OK did that command so you want me to do everything in this part '9 Hours Ago 03:19 AM'?

---

### Post by nerdy_kid on 2011-01-22
do these after the reboot:

run

```
nvidia-settings
```

if the program that pops up gives you an error, then run

```
sudo modprobe nvidia-current
```

and post the output.

if the program that pops up doesn't give you an error, then the driver is installed and working.

---

### Post by rapattack1 on 2011-01-22
I get the attached when i run that and :
```
carla@carla-desktop:~$ sudo modprobe nvidia-current
[sudo] password for carla: 
FATAL: Error inserting nvidia_current (/lib/modules/2.6.32-27-generic/updates/dkms/nvidia-current.ko): No such device

```

---

### Post by nerdy_kid on 2011-01-23
> **rapattack1 said:**
> I get the attached when i run that and :
```
carla@carla-desktop:~$ sudo modprobe nvidia-current
[sudo] password for carla: 
FATAL: Error inserting nvidia_current (/lib/modules/2.6.32-27-generic/updates/dkms/nvidia-current.ko): No such device

```

alright, so it seems that the wrong driver could be installed.  I think that simplest solution would be to install the nvidia driver off of nvidia site, so this is how to do it:

first, remove any existing nvidia drivers:

```

sudo apt-get --purge remove libvdpau1 nvidia-cg-toolkit nvidia-common nvidia-current nvidia-settings

```

then, go to this page and download the driver:
[URL="http://www.nvidia.com/object/linux-display-ia32-96.43.19-driver.html"]http://www.nvidia.com/object/linux-display-ia32-96.43.19-driver.html
[/URL]

take note of where the file is downloaded to.
once the driver is downloaded, open up a file browser, go to the downloaded file, right click it and under "permissions" click "allow executing".  Now, close all your open programs and logout.  Switch to a virtual terminal by pressing <Ctrl> <ALT> <F1>.  Login to the terminal, and run 
```

sudo service gdm stop

```

now, cd into the folder that you downloaded the driver into.  Type

```

cd PATHTODRIVER

```

for example, I am going to assume that you downloaded the driver to the "downloads" folding in your home folder.  The command would then be

```

cd ~/Downloads

```

once you are there, then get a listing of all the files:

```

ls

```

you should see the driver file in the list of text that results from the above command, type sudo ./ followed by the first few letters of the driver name and then press <TAB> to autocomplete the name.  For example, if the driver is named "nvidia-driver.sh" then you would do this:

```

sudo ./nvidia<TAB>

```
and the terminal would autocomplete the name for you.

the nvidia driver setup will begin, and a screen will pop up and ask you a few questions.  use the arrow keys to move your selection around.  once it is done, reboot your computer.  Everything should work then.

---

### Post by rapattack1 on 2011-01-24
OK i did the first command then there was no reaction when i did ctrl F1. Not sure when i was supposed to do it so i restarted and went into console login. I tried 'sudo service gdm stop' but i got 'stop:unknown instance'. Sorry didn't get far, I did download the driver and do the permission thing :0)

---

### Post by nerdy_kid on 2011-01-24
> **rapattack1 said:**
> OK i did the first command then there was no reaction when i did ctrl F1. Not sure when i was supposed to do it so i restarted and went into console login. I tried 'sudo service gdm stop' but i got 'stop:unknown instance'. Sorry didn't get far, I did download the driver and do the permission thing :0)

ahh sorry, its <Ctrl> <alt> <F1>.  I fixed my guide, so just continue following that.

---

### Post by rapattack1 on 2011-01-24
That got me in there!
OK i got to run the file but then i got this colored page/error:
Nvidia accerlatedGraphics driver....
Error:You appear to be running an X server please exit before installing. There was an OK to click then i rebooted back into the GUI

---

### Post by nerdy_kid on 2011-01-26
> **rapattack1 said:**
> That got me in there!
OK i got to run the file but then i got this colored page/error:
Nvidia accerlatedGraphics driver....
Error:You appear to be running an X server please exit before installing. There was an OK to click then i rebooted back into the GUI

yeah please follow the guide exactly, you have to run
```

sudo service gdm stop

```

after all users are logged out to kill the X server.

---

### Post by rapattack1 on 2011-01-26
Yes i did it exactly as is. There was some error when i did that command but i don't remember as that was yesterday. I will repeat everything when i have time again. Public holiday here in Oz.
OK i tried again because i was impatient he he. I might be missing something. OK so step by step. When i logout and then do ctrl + alt + F1 i get carla-desktop login:
Am i supposed to log back in? Because that is what i did then i did the sudo service gdm stop command and the first time i did it today i got something(can't remember the other word)/waiting and then it went back to the $ . Then i did the other commands and they went fine until the part i described that said something about x server. I tried another time and it didn't work then either. I think there is a missing piece of the puzzle?

---

### Post by nerdy_kid on 2011-01-26
> **rapattack1 said:**
> Yes i did it exactly as is. There was some error when i did that command but i don't remember as that was yesterday. I will repeat everything when i have time again. Public holiday here in Oz.
OK i tried again because i was impatient he he. I might be missing something. OK so step by step. When i logout and then do ctrl + alt + F1 i get carla-desktop login:
Am i supposed to log back in? Because that is what i did then i did the sudo service gdm stop command and the first time i did it today i got something(can't remember the other word)/waiting and then it went back to the $ . Then i did the other commands and they went fine until the part i described that said something about x server. I tried another time and it didn't work then either. I think there is a missing piece of the puzzle?

try restarting the computer, and as soon as it gives you the login dialog (the thing where you click your username and then type your password to login) hit ctrl+alt+F1 and login from the text prompt.  Then run sudo service gdm stop, and follow the rest of the guide.  I just did that on my own pc, so it must be something on your end.  If you still can't get it to work, you can boot into recovery mode. restart the computer, and about 5 seconds before Ubuntu starts loading hit shift multiple times until a text list pops up, and choose the second option.  Then, after a bit, a box will pop up, use the arrow keys to select "root prompt".  Find the nvidia driver like I showed you in my guide, and install it that way.

---

### Post by rapattack1 on 2011-01-26
Hmmmmm very odd i tried to log into this website several times just now. It said i was successfully logged in but then the site did not show that i was by making the subscription part/control panel available. How odd. I had to go back to an old message to get here.
Anyway I still get the login. Do i login? After i do ctrl+alt+f1 ?
Gee sorry i just reread what you said that i do login.....i am so tired! I am still getting that error ....something instance something. After i do the sudo service gdm stop command. Aren't i in recovery mode already? OK will try the shift thing again. I can't seem to get the timing right.

OK finally got into recovery mode(silly me i thought that was what i was booting in everyday). The text rolled then i got 'no signal detected' and then 'out of range'. Could there be something wrong with the video card? I tried a few times and got the same result.

---

### Post by nerdy_kid on 2011-01-27
> **rapattack1 said:**
> Hmmmmm very odd i tried to log into this website several times just now. It said i was successfully logged in but then the site did not show that i was by making the subscription part/control panel available. How odd. I had to go back to an old message to get here.
Anyway I still get the login. Do i login? After i do ctrl+alt+f1 ?
Gee sorry i just reread what you said that i do login.....i am so tired! I am still getting that error ....something instance something. After i do the sudo service gdm stop command. Aren't i in recovery mode already? OK will try the shift thing again. I can't seem to get the timing right.

OK finally got into recovery mode(silly me i thought that was what i was booting in everyday). The text rolled then i got 'no signal detected' and then 'out of range'. Could there be something wrong with the video card? I tried a few times and got the same result.

yeah, they are having some troubles with the forum.

geesh, you dont have a cooperative computer :P

alrighty, forget the recovery console, logout from your computer and hit ctrl+alt+F1 and then login, do 
```

sudo service gdm stop
sudo killall Xorg

```

and then try installing the driver.  I dont understand how sudo service gdm stop is not working, if you could give me the exact error message it would be useful, I dont know if you have another computer though.

---

### Post by rapattack1 on 2011-01-27
Ah yeah i thought as first it was me he he. I thought maybe i messed up something.

Phew and the problems are getting worse there is a red flickering thing going on that i have seen before. It appears only in certain fields on the screen. Dunno if the monitor is on its way out or it is the damned video card? I am thinking maybe we should try and install the video card i was trying to get happening before this used card. I bought a nice new one. It is a Zeus 5500 Galaxy Nvidia G-Force FX 5500. When i had put it in the damn machine was not booting at all. I think the psu went at the same time. I had to get the psu from my other machine and stick it in and put in a video card also from the other machine as i knew both were working. 
So should i try the new video card again or is that what caused the psu to fry?

OK will try those commands. My other machine(windows) is not fully together. I have to put another video card/psu in it. Time is very limited these days too. I did but another psu but have had no time to put it inside. I also have another spare video card but i don't know if it is working.

---

### Post by nerdy_kid on 2011-01-28
ok at this point i say try the Nvidia G-Force FX 5500 out, but do grab the maverick cd image boot from it to rule out any existing issues with your current ubuntu install.  Let me know how it goes. FYI, nvidia is usually not at all this difficult, I have dealt with several and none have been this problematic.

---

### Post by rapattack1 on 2011-01-28
The maverick cd image....do you mean the livecd?
Yeah i have had several nvidia cards too. Once i learned how things go ihh was fine...odd

---

### Post by nerdy_kid on 2011-01-28
> **rapattack1 said:**
> The maverick cd image....do you mean the livecd?
Yeah i have had several nvidia cards too. Once i learned how things go ihh was fine...odd

yeah, the livecd.

---

### Post by rapattack1 on 2011-01-29
This is great!!!!! It worked. No low graphics mode or whatever was or anything!!!!!:popcorn:
Going to do a few reboots then to see all is cool. Ohhhhhhh just discovered that i forgot to put the livecd in the drawer. He he well it all worked out anyway. Must have been because i was connected to the net at the same time.:KS
Ok second boot was bad. I got into the desktop but the bar at the top or bottom didn't appear.
Third boot is cool.
Hope the good booting continues.
There seemed to be some awful noise coming from the box like something was shorting. Not sure how to describe it. I dunno maybe it was the fan on the new video card sorting it self out. Now it is quiet as a mouse he he.

Had about 5 boots and no further problems. Graphics much better than the previous two video cards!!!!! Thanks so much Nerdy_kid your a gem for persisting with me. Must have been hardware?!

---

### Post by nerdy_kid on 2011-01-30
> **rapattack1 said:**
> This is great!!!!! It worked. No low graphics mode or whatever was or anything!!!!!:popcorn:
Going to do a few reboots then to see all is cool. Ohhhhhhh just discovered that i forgot to put the livecd in the drawer. He he well it all worked out anyway. Must have been because i was connected to the net at the same time.:KS
Ok second boot was bad. I got into the desktop but the bar at the top or bottom didn't appear.
Third boot is cool.
Hope the good booting continues.
There seemed to be some awful noise coming from the box like something was shorting. Not sure how to describe it. I dunno maybe it was the fan on the new video card sorting it self out. Now it is quiet as a mouse he he.

Had about 5 boots and no further problems. Graphics much better than the previous two video cards!!!!! Thanks so much Nerdy_kid your a gem for persisting with me. Must have been hardware?!

Great! 
check the GPU (graphics card) fan to see if somethings in it?  Maybe thats whats making the racket.
It must've been hardware, like I said, never had such an uncooperative driver install!
glad to help, remember to mark the thread as solved under the "thread tools"

---

### Post by rapattack1 on 2011-01-31
Oh great i can log in now...phew!
Yeah it is quiet now so that is not a hassle. I will probably have to check things again soon though as there has been some funny graphics problem. After being on the computer/internet for a long time i think it starts to acts funny. I get red inside some of the fields on the page.
Yep i did the solved thing :0)

---

### Post by nerdy_kid on 2011-01-31
> **rapattack1 said:**
> Oh great i can log in now...phew!
Yeah it is quiet now so that is not a hassle. I will probably have to check things again soon though as there has been some funny graphics problem. After being on the computer/internet for a long time i think it starts to acts funny. I get red inside some of the fields on the page.
Yep i did the solved thing :0)

well, you are all set!  the driver is working.

The red inside some fields is probably the fact that you are using a not so good graphics driver with compiz -- the fancy desktop effects.  If you right click your desktop, click change desktop background, click the effects tab and click "none" then the issue should go away.

---

### Post by rapattack1 on 2011-01-31
No i don't get into effects, themes or anything. Always plain desktop is the best to me :0) I checked what you said it is set to 'none'.

---

### Post by nerdy_kid on 2011-01-31
hmm ok, well I dont know what could be causing the red fields, probably a driver quirk.

---

### Post by rapattack1 on 2011-01-31
Yeah i thought it was when the machine heats up. You know after it has been on for a while but this session it started almost straight away. I noticed that also the desktop is affected. I took a video of that and will post that too. This has happened with previous video cards especially that last one.

Ok here is the url to the video. You will see a sort of ring of looking thing on the right of the desktop.
[http://www.youtube.com/watch?v=skUel6xFjt0](http://www.youtube.com/watch?v=skUel6xFjt0)

---

### Post by rapattack1 on 2011-02-01
I don't know what to make of it but after a update upgrade whatever that pops up and a restart that it demanded i got that low-graphics error thing again but the graphics seem the same as the previous boot. Odd. I notice there was a linux kernel update. Is that right? There is so much to learn and it went so quick i am not sure. Anyway no redness yet so things might be fine?!

---

### Post by rapattack1 on 2011-02-01
Gee sorry to say but more graphics problems today. Not long after i got online i started to see not only the redness issue but also some blobby yellow where the mouse was positioned on the screen. That didn't show long and then some other weird pattern started the take over the screen. I could see anything after a while and i did a ctrl+alt+del could barely see the thing to scroll down to restart. I clicked it and then can't remember some parts. I have taken photos so will attach. I think i did a boot at some point and still had the audio on and there was a voice that said something like 'system vga not passed'???? Can't remember. Just surprised. How did that happen? So i was going to swap lcd monitors(i also have another machine that runs windowsxp) but then as i was unhooking i noticed that there was a hdmi connection hidden under a rubber panel at the back of the monitor that i hadn't seem before and i know the new video card uses it. I had a new hdmi cable so now i have booted with it hooked up to the same monitor. I am truly in low-graphics mode now :0(

---

### Post by nerdy_kid on 2011-02-02
idk, as long as the nvidia control panel starts up without any errors then the nvidia driver is in use which means that everything is working correctly.

---

### Post by rapattack1 on 2011-02-02
Ummmmmm i forgot what idk means. Ahhhh you might not have read everything i said. Heaps of problems! Gee maybe after all this it is the motherboard not communicating with the video card properly. ONly a theory. Which is bad!!!! I would hate to ditch this computer but it seams after spending so much money i might have to :0(

---

### Post by nerdy_kid on 2011-02-03
for some reason I managed to miss your entire post lol  Something looks seriously wrong, try reseting your BIOS setting to default, and reseating the card.  Other then that, I can say try a LiveCD, but it probably won't make any difference.

---

### Post by rapattack1 on 2011-02-18
Sorry finally got round to moving the box, opening it and doing as instructed. Damn thing is no different i am afraid. Ah well might have to put up with low graphics for a bit and think about getting me a Mac. I am soooooo sick of these hardware issues and i spent money for nothing. I don't know when and if i can afford a mac but maybe some money will fall into my lap lol. Got no chance of a job because of illness so will just wait :0(

---

### Post by cascade9 on 2011-02-18
The screenshot looks like graphical corruption. It could be from overheating, a dodgy card ('cooked' cards sometimes do that) or other dodgy parts (probably a motherboard. 

For it to be using a FX5500, its probably an AGP card, and an older system. So its not that suprising. Hopefully you didnt spend to much money, FX5500s are worth about $10-25 .au ;) 

I wouldnt buy a mac thinking they will have no hardware problems. They should be OK to begin with, but everything electrical has the capability to get degraded, from various causes. I'm actually waiting to see if I can get a MacPro box or 2 from a friend of mines workplace, and they arent even that old (they died just out of warranty IIRC).

---

### Post by rapattack1 on 2011-02-19
Wow i couldn't log in at all yesterday. That bug is back!

Yeah it seems it is the motherboard as one of the video card i had in there was put back into another working system and it going along fine. The latest video card that i put in is new from a shop so i think after all it is the stupid refurbished board that i bought from someone on ebay. I will have to see if he will still cover me for warranty.
 

Ah well i think i am off to spend what little saving i have to buy a mac. I am sick of these hardware issues and just don't trust anything anymore. I want to be able to do audio and video production and what i have been using just doesn't do it. I talked to the mac store today and he was saying i could duel boot so that is good as the mac software is way too expensive and i love linux's multimedia stuff!
Ouch really that happened?! I haven't heard of such a thing.

---

### Post by cascade9 on 2011-02-19
> **rapattack1 said:**
> Ouch really that happened?! I haven't heard of such a thing.

What, dead mac pros? All hardware can die. 

If you are short on money, just get a decent normal computer (not refurbished, and not off ebay).

---

### Post by rapattack1 on 2011-02-19
I know but it seems everyone i know with a mac is having a great time!
I have had enough of secondhand computers. I am done! I have bought only two new computers in my time of hundreds of computers coming across my path. The two that i bought new work really well. Dunno why. I have one pc that has windows on it and it is still work over 5 years later. Done a fair amount of upgrades like ram, optical drive, added another hd and psu but motherboard is working great. The other i bought new was a eeepc i bought 1.5 years ago but the keys are too small and it is neglected now. The box i have been using with ubuntu has had wayyyyyyyyyy too many issues and i have to move on. It was built for multimedia and that is what i need. The machine with windows on it can't be used. It just doesn't have enough power for what i need.
Yep i am on a disability pension and a LOT of secondhand computers come my way. Can do them anymore. I have to move on to doing some actual recording/editing and stop fixing crap all the time. Really sick of it

---

### Post by cascade9 on 2011-02-19
*blinks* 

So, the 2 computers you bought new are OK, its only the 2nd hand boxxen that have problems? There is probably a reason why are became 2nd hand.....

I just dont get it. Unless you are looking at $2K+ on a 27'' imac all the mac deals are easy to beat (and the only reason you would have problems 'beating' a 27'' iMac is.......27'' monitors are uncommon). I'd doubt that you are looking at a 27'' imac, and the 21.5 imacs arent worth the money unless you are a big fan of OSX. 

If you want to run ubuntu, and you havent had any issues with the new computers you bought, why look at mac?

---

### Post by rapattack1 on 2011-02-19
Well it is all too much of a long story. Well documented on the forums. Drives me nuts. It was working fine. Anyway no more...
No i am looking at a mac mini. I have done my research and i will do a dual boot with ubuntu.
I don't want to use both the other computers with ubuntu. The laptop is too small and the windows machine is needed for that! Not enough grunt for what i need as i said! Even a pc would cost me close to the $900 i saw the mac mine for. I don't need all the other fluff as i already have a monitor, kb and mouse. All can be used again!

---

### Post by cascade9 on 2011-02-19
> **rapattack1 said:**
> Even a pc would cost me close to the $900 i saw the mac mine for.


Where on earth are you looking, harvery normans? 

The mac mini is an older CPU (core2duo) and the $899 .au version is 2GB of RAM, 320GB HDD, DVD-RW and a (mobile) nvidia GPU. 

You can get systems better than that for far, far less. 

Umart- 

> Product Description:  Intel Core i3 540 Processor LGA1156 3.06GHz 4MB Cache CPU
Asus P7H55D-M Pro LGA1156 4DDR3 GLAN 1PCIEx16 mATX HDMI HD AUDIO 
Kingston 4GB(2 X 2GB) DDR3-1333MHZ
Samsung 22X DVDRW Black SATA (SH-S223C-BL)
Western Digital 500G SATAII 7200 rpm HDD(16Mb Cache)
CoolerMaster Centurion RC333 Elite Black with 420W + HD Audio(RC333KKR
Logitech  MK250 Wireless Desktop 
1 Years return to base Warranty
Computer System


$600. 

[http://www.umart.com.au/pro/products_listnew.phtml?id=10&id2=78&bid=2&sid=68130](http://www.umart.com.au/pro/products_listnew.phtml?id=10&id2=78&bid=2&sid=68130)

Add a GT220 (about $60) and its got a far better specifications than the mac mini. 

BTW, I wouldnt buy that system, I'd get an AMD (more bang for your buck). [URL="http://www.umart.com.au/pro/products_listnew.phtml?id=10&id2=78&bid=2&sid=68130"]
[/URL][ ]("http://www.umart.com.au/pro/products_listnew.phtml?id=10&id2=78&bid=2&sid=68130")
That is a long way from the cheapest system I know of that is better than the mac mini (MSY has i3 systems with 1GB RAM/250GB HDD for $380, if you got a Core2Duo like the mac mini they go as low as $270.....)[URL="http://www.umart.com.au/pro/products_listnew.phtml?id=10&id2=78&bid=2&sid=68130"]
[/URL]

---

### Post by rapattack1 on 2011-02-19
I have never seen a mac in harvey norman. In a mac store is where i saw it. It is the latest mac mini! Yeah but most people i have spoken to they tell me macs grunt is heaps more than other computers. Like with AMD's being more than Intel.

I don't want less grunt. As i keep saying i am doing audio/video editing and i have had heaps of machines fail on me and i learnt that i must ask people that do the same thing. Trouble is those people in the pc world are thin on the ground and i can't seem to get a hold of them. I have been trying for ten years. I need specifics and i can't seem to get that. In the mac world it is taken for granted that they all do multimedia well. Yes i know many movies etc are made with linux on pc's but where is the information? I have been trying for 10 years and no one in that field is telling me. I don't want the advice from a non multimedia person. I even went to a SLUG group hoping to get advice or track down a multimedia person. Well i went to several and nothing. 10 years of being held back is too much. I have done what i can but when i did the final cut pro course plus audio production in a professional mac studio all i know is i got a fantastic result. ofcourse i can't afford the software so i will dual boot.

I do know MSY. I live near there and got the parts for this stupid computer from there.

---

### Post by cascade9 on 2011-02-20
I cant tell if you are being deliberately obtuse, but I'll answer this anyway....  

> **rapattack1 said:**
> I have never seen a mac in harvey norman. In a mac store is where i saw it. It is the latest mac mini! Yeah but most people i have spoken to they tell me macs grunt is heaps more than other computers. Like with AMD's being more than Intel.

I meant 'where are you looking at computer prices', not mac mini prices. 

The 'latest' mac mini was released in june 2010, and that was only a GPU upgrade (OK, it also got a HDMI port and SD card slot), the CPUs are the same Core2Duo CPUs since the october 2009 mac mini release, and that was pretty much just a minor CPU upgrade from the 2007 mac mini.... 

BTW, there is a new one on the way apparently- 

[http://buyersguide.macrumors.com/#Mac_mini](http://buyersguide.macrumors.com/#Mac_mini)

'Latest' doesnt mean that the systyem is anywhere near current. Marketoids, they dont care about when the 'latest' was released, they just want to make a sale....

BTW, if there is a difference between how much 'grunt' a mac has in xcomparison to a 'normal' computer, its purely from the OS in these days of intel macs. Also, these days Intel is back out in front as far as performance goes....but you pay more for similar levels of performance from intel compared to AMD. 

> **rapattack1 said:**
> As i keep saying i am doing audio/video editing and i have had heaps of machines fail on me and i learnt that i must ask people that do the same thing. Trouble is those people in the pc world are thin on the ground and i can't seem to get a hold of them. I have been trying for ten years. I need specifics and i can't seem to get that. 

The 'heaps of machines' that have 'failed' on your were giveaway 2nd hand boxes, right? Like I said, there is probably a reason they became 2nd hand giveaways. 

> **rapattack1 said:**
> In the mac world it is taken for granted that they all do multimedia well.

Aside from possibly software (which you've said you wont be using because its too expensive) current apples use the same basic hardware as you can get with normal x86 computers. 

 > **rapattack1 said:**
> Yes i know many movies etc are made with linux on pc's but where is the information? I have been trying for 10 years and no one in that field is telling me. I don't want the advice from a non multimedia person. 

I dont do multimedia much at all, but I know some people who do. The only one that matters in this case actuaklly works in 3D/movies (and that is where I was hoping to get the dead mac pros from actually). 

Where he works, there are mac workstations, windows workstations, and last I heard there was some linux render nodes (thought they were thinking about replacing them, or moving to a different OS due to odd path problems with linux maya render nodes). His workstation at work is running windows, as is his personal machine at home.  

He started out with 3Dstudio max, doing 3D modeling and texturing for real time graphics and games. Moved from 3D studio max to maya while doing a degree ([FONT=helvetica]Bachelor of Fine Arts Animation), and currently works profesionally as a [/FONT][FONT=helvetica]matte-painter and 3D visual effects artist. [/FONT]

So, what information are you after? System specs? 

> **rapattack1 said:**
> I even went to a SLUG group hoping to get advice or track down a multimedia person. Well i went to several and nothing. 

Sydney linux users groups? Not that many multimedia people use linux for desktops, so you wont find much advice there.  

 > **rapattack1 said:**
> 10 years of being held back is too much. I have done what i can but when i did the final cut pro course plus audio production in a professional mac studio all i know is i got a fantastic result. ofcourse i can't afford the software so i will dual boot.

[FONT=helvetica]If you arent going to use the apple software, then getting an apple is just so you can say 'I've got an apple!'. Like I said above, apples use intel CPUs, intel chipsets, standard HDDs, standard GPUs (fiddled with so that you cant just go out an buy a new 'normal' video card), etc.  
[/FONT]
> **rapattack1 said:**
> I don't want less grunt. 

Then dont get a mac mini. 

Its a dual-core CPU from several years ago, with a lowend GPU, a 8GB RAM limit (and apple only supports up to 4GB) running 'slow' DDR3 (1066). 

You could get a current quad core (upgradable to hexa-core), more and faster RAM (at least DDR3 1333) with a much higher max RAM limit, a faster GPU, more HDD space for the same amount of money as the mac mini.

---

### Post by Miguel Tavares on 2011-02-20
Hi,
if it doesnt work out, try ctrl+alt+F8 instead of F7 :D

---

### Post by rapattack1 on 2011-02-20
No i am just tired of the problem and that it is a bit late for this. Just really over it.
Yes i am around computers all the time and know the prices.

Well in a way i am kind of leaning towards AMD as my machine running windows is an AMD and i purposely bought it at that time because of it being so. Been so reliable!

Well no the machine that i am talking about was fine. Great multimedia machine . Custom built for that purpose but i made a mistake with it and blew the motherboard. Longgggggg story but i wasn't concentrating and i stuffed it. Bought a refurbished mb of the same type and it seems i have been ripped off. It has taken far too long to find out it is indeed the mb. Longggggggg story again but that is the case.

Just wish i knew someone that built multimedia machines as that is where the whole thing goes no where. I tried in that older AMD machine that i have with UBuntu on it but noooooooooo good. Just not strong enough. Even 3 years ago when i first used Ubuntu or Debian i don't remember. When it comes to multimedia you have to have something stronger. Maybe something like gaming. I am not sure as i so not interested in gaming. Just wish i had reliable advice from someone that does multimedia. I have asked for sooooooo many years.

Oh that is interesting that you know this person that does the 3d stuff. I have wanted to do that too.
Yes well mainly it is the soundcard thing as soundonboard is no good. I have to plug a mic in and record with it. I find soundonboard has no stability. There are so many sound cards out there it is impossible to know what will take what i need. Video i guess it would be ok whatever a gamer uses as they have high graphic needs as well.
I think the other thing that puts me off is i heard of a lot of gamers spending $2000 on their machines so that i another reason i thought that that is what i would need to spend and i am not prepared to go that high.

OK yes i think i did hear there was a new mac mini coming out. Somewhere i read it. Hard to keep up sometimes :0)

Yes i know the computers for example in Harvey Norman are crazy. And many places. I often go with friends that 'just want a computer'. That is never fun lol. So because they don't understand MSY i take them to stupid Harvey first so they can look at a pc. Then they can tell me what they expect. When i tell them they can get so much cheaper at MSY then they are happy! I send them with something written on paper and they are set :0)

I have an older computer scientist friend and he says lots of movies are made with Linux. He uses all platforms but does a lot of video editing on Linux. He is also an actor. I exhausted him as a resource not long after i got into Linux because i was clueless lol. So can't call him anymore and audio production is not his field so he is no help there.

I had heard about the mac's using intel stuff. Hmmmmmm so it is true. OK i thought it was like a conspiracy or something. OK thats made me think again!

OK thanks for sticking with me. I know i am a cranky old bugger. Had some bad experiences with spending money on this machine and in my world that means not eating. I do have some money left from something i sold but wanted to spend it on something else. Well this might be the only way to go! AMD machine hmmmmmmm. OK will look closer at what MSY has....thanks:( ...sorry again! 

Miguel-Hi what is that about F7? Inside joke?

---

### Post by cascade9 on 2011-02-21
3D is one of the hardest jobs to get into, if you wanted to do it professionally. There are so many people that want to get into 3D that the _very_ few jobs around get a lot of applicants.

Generally, the guy I know who does 3D get the fastest system he can for however much money he has to spend when he gets new machines, uses normal geforce cards. The place where he works always uses nVidia quadro or ATI fire cards, because they are the only ones certified to work with maya. The 'professional' cards like the fire and quadro cost a lot more than the radeon/geforce cards, so its not worth even looking at (and you can sometimes 'softmod' the geforce cards into quadros, no idea if you can do something like that with ATI). 

Sound cards.....onboard sound can be crappy. The newer onboard sound chips are a lot better than the older chip, they were just junk. M-audio cards are what a lot of home/semi professionals use (and some professionals as well AFAIK), but again, they arent cheap. Its also hard to find one here. 

You migth be able to find a cheaper brand sound card with one of the chips M-Audio uses, I havent checked.  Barrign that, probably a asus card would be the way to go (you can get a decent soundcard for under $100), but I'll try askign the audio guy I know.....when I see him next, that might not be till the weekend. 

I think that part of yoru problem is lumping everythign together under 'multimedia'. The 3D guys home machine is great for 3D and 2D drawing. It would be awful for sound work, he doesnt care about sound quality, and has always used the onboard sound he got with the motherboard.

---

### Post by Miguel Tavares on 2011-02-24
> **rapattack1 said:**
> No i am just tired of the problem and that it is a bit late for this. Just really over it.
Yes i am around computers all the time and know the prices.

Well in a way i am kind of leaning towards AMD as my machine running windows is an AMD and i purposely bought it at that time because of it being so. Been so reliable!

Well no the machine that i am talking about was fine. Great multimedia machine . Custom built for that purpose but i made a mistake with it and blew the motherboard. Longgggggg story but i wasn't concentrating and i stuffed it. Bought a refurbished mb of the same type and it seems i have been ripped off. It has taken far too long to find out it is indeed the mb. Longggggggg story again but that is the case.

Just wish i knew someone that built multimedia machines as that is where the whole thing goes no where. I tried in that older AMD machine that i have with UBuntu on it but noooooooooo good. Just not strong enough. Even 3 years ago when i first used Ubuntu or Debian i don't remember. When it comes to multimedia you have to have something stronger. Maybe something like gaming. I am not sure as i so not interested in gaming. Just wish i had reliable advice from someone that does multimedia. I have asked for sooooooo many years.

Oh that is interesting that you know this person that does the 3d stuff. I have wanted to do that too.
Yes well mainly it is the soundcard thing as soundonboard is no good. I have to plug a mic in and record with it. I find soundonboard has no stability. There are so many sound cards out there it is impossible to know what will take what i need. Video i guess it would be ok whatever a gamer uses as they have high graphic needs as well.
I think the other thing that puts me off is i heard of a lot of gamers spending $2000 on their machines so that i another reason i thought that that is what i would need to spend and i am not prepared to go that high.

OK yes i think i did hear there was a new mac mini coming out. Somewhere i read it. Hard to keep up sometimes :0)

Yes i know the computers for example in Harvey Norman are crazy. And many places. I often go with friends that 'just want a computer'. That is never fun lol. So because they don't understand MSY i take them to stupid Harvey first so they can look at a pc. Then they can tell me what they expect. When i tell them they can get so much cheaper at MSY then they are happy! I send them with something written on paper and they are set :0)

I have an older computer scientist friend and he says lots of movies are made with Linux. He uses all platforms but does a lot of video editing on Linux. He is also an actor. I exhausted him as a resource not long after i got into Linux because i was clueless lol. So can't call him anymore and audio production is not his field so he is no help there.

I had heard about the mac's using intel stuff. Hmmmmmm so it is true. OK i thought it was like a conspiracy or something. OK thats made me think again!

OK thanks for sticking with me. I know i am a cranky old bugger. Had some bad experiences with spending money on this machine and in my world that means not eating. I do have some money left from something i sold but wanted to spend it on something else. Well this might be the only way to go! AMD machine hmmmmmmm. OK will look closer at what MSY has....thanks:( ...sorry again! 

Miguel-Hi what is that about F7? Inside joke?

Totally ^_^ :P, well, wtf do you need a mac for? all darwin kernel fkn same deb tree from systemv from 1969 with some mods into it. nevertheless you can get the same result with ubuntu so get a cheap lappy and uplink deb into it :D. with beryl or compiz will look like a mac if you like the looks and feel and opensource man.

---

### Post by rapattack1 on 2011-02-24
cascade9- Yes i can imagine that would be hard work to get into. Everything i do these days is hobby level because of my illness but at the end of the day i should concentrate on the audio production. It's all interesting though! Thanks!
Thanks for the rest of that info. It is more advice than i have gotten in years! Oh and yes take your time. If your friend knows more about a sound card for audio production then i would appreciate the advice!

Miguel Tavares-Yeah laptops cost more and the soundonboard is not very good. Desktop is a much better option for me. No not worried about the maccy look. I have DreamLinux at one point which is very close to the look of mac OS but it is a bugger to work with/install etc. Really painful OS. Ah well i gave it a good try and i am sure with someone with more knowledge it is a great one. Ubuntu has been good to me so it will be good. I was going to dual boot the mac but now cascade9 has got me thinking back to an AMD machine :0)

---

### Post by cascade9 on 2011-02-26
Well, I asked the guy I know who does audio, and he's no help at all LOL. 

Currently hes got some M-Audio card he imported worth $400+, and couldnt tell me anything about cards that dont cost a forture.

---

### Post by rapattack1 on 2011-02-27
LOL gee now you have had a taste of my experiences with audio guys ....gee what is it with them? Ah well i think i might have to wing it then. After all anything has got to be better than my old hardware i guess. MSY have some great deals on AMD machines. 
Thanks for asking him anyway and if i can stretch my dollar i might get a M-audio thingy. Hey does your friend use Linux?

---

### Post by cascade9 on 2011-02-28
I actually know what his problems are- dead end job, alcohol and substance abuse problems in particular, but they arent the only ones..... 

The other reason why he did that is the typical 'got the right tool for the job and if you cant get it you arent trying hard enough' attitude. You've met them before, right? 

BTW, he did rant and rave about creative being 'absolute crap'. I think that he had a hell of a time with a creative SBlive and 'live drive' setup he got sold once, and thats what pushed him to get the M-Audio. 

I still think that the best of the affordable cards for sound production would be an asus xonar DX or D1.

---

### Post by rapattack1 on 2011-02-28
Oops that is sad for him. Yeah i dunno with the ones i met. Most of them i didn't get to know them but they seemed to have no life outside of computers. My social life is very strong. The person that got me into linux though i think he has gone a bit koo koo. Spends way too much time with the computers. In his 60's, out of work, well sometimes acting jobs, retired computer scientist and lives alone. The other linux people i know here tend to like to show you they know something but when you ask them in detail they don't answer....wft! The general computing community are annoying on so many levels. Stubborn Microshaft people are even more annoying. Wft they annoy me the most he he.
Oh yes i met A LOT of people that think i haven't tried hard enough to find the solution. A LOT!!!! 

Oh he he i have a Creative Live Drive in my windows machine....I didn't get it working. Someone gave it to me and it is supposed to work but i think i found out there was some issue with AMD. Dunno why. I think that was when i stopped trying to get the drive part working and just use the pci card with it. Had some good creative cards though so can't complain about them generally.

OK I am looking at those soundcards you recommended now. Seems that one reviews says that a preamp is still needed. Also one looks like you can plug a guitar jack in their which is what my mic has. I am mainly interested in the card recording voice through a mic. I am a rapper and Hip Hop is what i do.

This card looks interesting [http://msy.com.au/product.jsp?productId=5613](http://msy.com.au/product.jsp?productId=5613)

---

### Post by cascade9 on 2011-03-01
As far as I know, if you want to get good results you will need a preamp. 

Auzentech X-Fi Bravura is just a glorified creative X-Fi. You would be much better of finding a M-Audio Delta 1010LT. Even a cheaper Audiophile 2496 would be much better from what I can see. It would be better than a xonar as well, just you cant go and buy one of the shelf in this country (well, not from computer shops anyway, you might find some in as music store, but that would be more expensive than importing). 

[http://ixbtlabs.com/articles/maudioaudiophile/](http://ixbtlabs.com/articles/maudioaudiophile/)

---

### Post by rapattack1 on 2011-03-01
Oh but i thought it said on that page that it had a preamp built in?

Oh that link seems to be rather old. Is it a soundcard or a separate usb device. I am a bit confused as the m-audio things i saw were separate usb devices. 
Ah so i would have to go to a music shop or ebay? I can imagine music shops would be super expensive. Is there any trusted websites or is that ixbtlab site trusted to buy from ? I don't have a credit card so can only use paypal.

OK well searched for a reseller in Oz and am even more confused. They website keeps bouncing back to US site. Can't find any soundcards on the Australian links. Only the preamp boxes but they don't show a usb connection. The soundcards i am unclear about as well. There is a shop in sydney so whenever i get time i might go there.

---

### Post by cascade9 on 2011-03-01
The Bravura might have prer-amps on the card, but that doesnt mean they are any good (and IIRC the electrically noisy enviroment inside computer cases isnt a good place to put pre-amps). 

That linked card is a soundcard, theres even a pic of the card if your scoll down the page.... 

You wont need a USB interface on the pre-amp, the 2496 has RCA inputs. The Delta is even better, its got XLR inputs. 

M-Audio pretty much pulled out of the australian market as far as computer shops go. Music shops are expensive, yes (I used to work in one, I've seen the mark-up), so the only easy choice is importing as far as M-Audio goes. There should be a ton of places that will sell you an M-Audio card online.

---

### Post by rapattack1 on 2011-03-01
OK now i am still confused. Linked card? Um so do you mean i have to buy two things? One is the boxy thing and a card? Sorry the terms are confusing me and there are so many models i can't keep track.

I read somewhere or someone said that the boxy thing was connected via usb. So am clueless now :0(

Yeah i am sure there are places to buy online but i am not very trusting. I don't have a credit card anyway so maybe ebay is the only option :0) 
Ah so you used to work in a music shop. Cool i would have loved that. I was brought up as a muso and many family members still are but i have had a varied career of many types of performing so left being a musician behind as a child.

---

### Post by rapattack1 on 2011-03-02
Did you mean this card [http://www.m-audio.com/products/en_us/Audiophile2496.html](http://www.m-audio.com/products/en_us/Audiophile2496.html)   ?

---

### Post by rapattack1 on 2011-03-03
At last i found a reseller in Sydney [http://www.sounddevices.com.au/categories/100284-M-Audio/](http://www.sounddevices.com.au/categories/100284-M-Audio/)
I will go there maybe monday or tuesday :0)

---

### Post by cascade9 on 2011-03-05
Heh, goes to show you can find stuff if you relly look for it (I didnt). Still, its a fair bit more expensive than the prices in the US, especially now the US$ is in freefall.

---

### Post by rapattack1 on 2011-03-05
:0) Yeah but i didn't know what to look for until you gave me info. Hey can you tell me which thing am i looking for. Sorry i am still not cleat wether i have to get a soundcard and external thing or just the external thing.

---

### Post by cascade9 on 2011-03-06
The only 'external thing' you should (might? I dont know for sure) need is a pre-amp. 

Just getting a pre-amp wont really help much, you still need a way to input the audio.

---

### Post by rapattack1 on 2011-03-06
Oh so soundonboard is no good?

---

### Post by cascade9 on 2011-03-06
You're asking me this now? 

> **rapattack1 said:**
> Yes well mainly it is the soundcard thing as soundonboard is no good. There are so many sound cards out there it is impossible to know what will take what i need. 

I'd almost be confused, but I've been given hints all the way though this thread.....

---

### Post by rapattack1 on 2011-03-07
Well thats why i am asking because i don't know this generations machines. If they come up to scratch. OK well it's a huge investment. New machine, soundcard and Audio buddy....phew....will have to rebudget again and see if i can do it :0)

---

### Post by cascade9 on 2011-03-07
The audiobuddy is just a preamp, you dont have to use a Maudio branded preamp with the Maudio cards. 

Jaycar was selling pre-amps for like $25 not that long ago.

---

### Post by rapattack1 on 2011-03-08
Is this the product from Jaycar [http://jaycar.com.au/productView.asp?ID=AC1662&keywords=preamp&form=KEYWORD](http://jaycar.com.au/productView.asp?ID=AC1662&keywords=preamp&form=KEYWORD)   ?
So are you saying it is more important to spend the money on the soundcard? Which would you recommend?

---

### Post by cascade9 on 2011-03-09
No, thats a aux pre-amp, not a mic pre-amp. It might work, but its not what I was thinking of. 

As for sound card, I'm not going back over that again.

---

### Post by rapattack1 on 2011-03-09
Oh ok glad i asked you then because it's all rather confusing. Won't get that then :0)

OK i couldn't find the info about the soundcard. You said something about scrolling down a page and i didn't know what page.

I went to the store called Sound Devices today and they have no idea about customer service. I wouldn't buy anything from them. No way. They were aloof and more interested in what they were doing before i walked in. When i said Linux well that finished that. Geez!!!! They crapped on about mac's and that that is the only or best option for what i needed. Didn't even get to speak. I tried but what two morons!!! 
Ah well will just get the AMD machine and plug into the soundcard like i have done before.
Oh btw they told me at that shop to get a creative card he he. They also did mention another brand but gee they were so impatient that i had no time to write it down or ask for details :0(

---

### Post by cascade9 on 2011-03-09
I meant this page- 

[http://ixbtlabs.com/articles/maudioaudiophile/](http://ixbtlabs.com/articles/maudioaudiophile/)

Its just an article on the Maudio audiophlie 2496. 

> **rapattack1 said:**
> I went to the store called Sound Devices today and they have no idea about customer service. I wouldn't buy anything from them. No way. They were aloof and more interested in what they were doing before i walked in. When i said Linux well that finished that. Geez!!!! They crapped on about mac's and that that is the only or best option for what i needed. Didn't even get to speak. I tried but what two morons!!! 
Ah well will just get the AMD machine and plug into the soundcard like i have done before.
Oh btw they told me at that shop to get a creative card he he. They also did mention another brand but gee they were so impatient that i had no time to write it down or ask for details :0(

Thats typical of those sorts of stores.

---

### Post by rapattack1 on 2011-03-09
Ah ok. Those dudes at the shop said that M-Audio stuff has no linux drivers anymore. They said there was a website that had drivers but they are not doing them anymore.

Gee so it is typical. Very annoying. It is like when i first got into computers lots of stores were like that. Not now though he he. I had this experience a few times where i just happen to go into Harvey Norman and they had the little Eeepc lappies there with Xandros on them and i was explaining the benefits of the machine/OS over the windows version, to a customer because the sales guy had no clue. Then a few times i was in real computer stores where they said something about linux and i corrected them by saying 'oh no linux has changed and anyone can use it'. Also had a few experiences where it was more about hardware. Now i walk into the same stores months or years later and the staff love me being there :0)

I have been searching around and can't see anything recent on linux drivers or to get an M-audio product happening with linux :0(

---

### Post by cascade9 on 2011-03-10
> **rapattack1 said:**
> Ah ok. Those dudes at the shop said that M-Audio stuff has no linux drivers anymore. They said there was a website that had drivers but they are not doing them anymore.

They dont know squat....

MAudio cards have been supported for so long that the alsa page doesnt even bother listing the needed kernel/alsa version to get support (IIRC they had support in kernel 2.4.X, which is like the dinosaur age as far as linux goes)- 

[http://www.alsa-project.org/main/index.php/Matrix:Vendor-MAudio](http://www.alsa-project.org/main/index.php/Matrix:Vendor-MAudio)

The 'details' bit on that page is just in case you dotn get automagic support, out of the box. 

There is still development going on for the ICE1712 chips (which he maudio cars use)-

> The "Mudita24" package is a modification of alsa-tools' envy24control:
an application controlling the digital mixer, channel gains and other
hardware settings for sound cards based on the ice1712 chipset  (
[http://alsa.cybermirror.org/manuals/icensemble/envy24.pdf](http://alsa.cybermirror.org/manuals/icensemble/envy24.pdf)  ).   It
also displays a level meter for each input and output channel and
maintains peak  level indicators.  This utility is preferable to
alsamixer(1) for those with ice1712-based cards: M-Audio Delta 1010,
Delta 1010LT, Delta DiO  2496,  Delta 66, Delta 44, Delta 410 and
Audiophile 2496. TerraTec EWS 88MT, EWS 88D, EWX 24/96, DMX 6Fire,
Phase 88.  Hoontech SoundTrack DSP  24,  SoundTrack  DSP 24 Value,
SoundTrack DSP 24 Media 7.1.  Event Electronics EZ8.  Digigram VX442.
Lionstracs, Mediastaton.  Terrasoniq TS 88.   Partial support for
Roland/Edirol DA-2496.

[http://www.spinics.net/lists/linux-audio-users/msg71213.html](http://www.spinics.net/lists/linux-audio-users/msg71213.html)

---

### Post by rapattack1 on 2011-03-10
See that is why i get on this forum because there are people that know this stuff here like you. So many dumbasses around in the world :lolflag:

---

### Post by rapattack1 on 2011-03-10
[http://cgi.ebay.com.au/ws/eBayISAPI.dll?ViewItem&item=280637700626&ssPageName=STRK:MEWAX:IT](http://cgi.ebay.com.au/ws/eBayISAPI.dll?ViewItem&item=280637700626&ssPageName=STRK:MEWAX:IT)
I am going to bid on this item. If not the Sound Devices store where the idiots work have it on sale for $120. They also sell the audio buddy preamp for $130 .
MSY has  a 'AMD x2 Dual Core 255 3.10Ghz' for $290 or i could go to a 'AMD x4 Quad Core 955 3.20Ghz' for $390.
There are many deals but these seem to be it as they don't include things like a dvd writer, monitor, speakers, windows(yuk) which i already have. I will probably add some more ram though as i think those deals only have 1gig or ddr3 ram. I looked at the boards online and i think there is a pci slot. I know there is all this stuff about pcie but the boards like like they have both.

---

### Post by cascade9 on 2011-03-22
> **rapattack1 said:**
> See that is why i get on this forum because there are people that know this stuff here like you. So many dumbasses around in the world :lolflag:

LOL, I'm not here much anymore....I'm pulling back from forums in general, and this forum in particular. 

Anyway, I havent given teh cheap-arsed MSY deals. I'm always wary of the very cheap computers, they tend to have nasty power supplies, the cheapest RAM and motherboard they can get, etc. 

I built a computer for yesterday actually. I got it from umart (no umarts in sydney though) but MSY has all the same stuff as far as I know. Parts list-

Corsair CMX4GX3M2A1600C9 4GB (2x XMS3 2GB)
CoolerMaster Centurion 5 II Black Tower Case W 500W 
AMD Athlon II X2 Dual Core 255 
Gigabyte GA-870A-UD3
Western Digital 500G SATAIII Caviar Blue
Palit G210 512M  DVI VGA HDMI
Using a DVD-RW drive the person  built it for already owned. 

I had to change to a different video card though umart didnt have that one in stock. About $450. The power supply isnt quite as good as I would like, and its a strech to connect the 4+4pin ATX power connector, but aside from that its not bad at all.

---

### Post by rapattack1 on 2011-03-23
Ah i don't blame you. I used to get on computing.net all the time years back. I actually did help people out for a while there with older windoze problems but real life called :0)

Actually i have chosen i think a better(gaming machine AMD quad core ) deal at MSY. Not one of the cheapies. I have bought a fair bit from them over the time i have known they were there and advised people to get whatever there. So far so good :0)
I might get the machine in the next few days and also just bought a nice usb microphone for recording vocals. Did a stack of research phew....i am tired lol.
Might slot in a good soundcard after i get the machine as i haven't 100% decided on that yet. Bid on a few things and kept missing out. Was exciting because i usually do a lot of 'buy' it now' on ebay lately. To get into a bidding situation is quite a rush but i pulled back knowing the price was going tooo high.

Funny thing is i found a machine on the street that is exactly that one that you have. The case is rusty(the suburb i found it in is right near the beach) and the psu. Many parts were missing but the mb looks free of corrosion. I have ummm and ahhh about waiting til i test this board but i think i won't as i need a working now machine . I have way too many unused crap machines.

Thanks for your patience and will post back when i get all this happening.
Oh btw i am buying a Samson usb mic as they have a preamp built in.

---

### Post by cascade9 on 2011-03-23
> **rapattack1 said:**
> Funny thing is i found a machine on the street that is exactly that one that you have. The case is rusty(the suburb i found it in is right near the beach) and the psu. Many parts were missing but the mb looks free of corrosion. I have ummm and ahhh about waiting til i test this board but i think i won't as i need a working now machine . I have way too many unused crap machines.

Thanks for your patience and will post back when i get all this happening.
Oh btw i am buying a Samson usb mic as they have a preamp built in.

I'd doubt that any computer you would find in the street are speced anything like my machine, or that machine I just just built (thats not for mine). Hell, if it is and you dont want it, I'll pay for postage to QLD. Not kidding ;)  

AFAIK, all the 'of the shelf' systems MSY sells are going to use the cheapo motherboards with onboard video...you would be better of spending a bit more for a decent board + video card. even if you have to 'drop' the quad core to dual core (you shouldnt really notice any difference for audio work with dualcore vs quadcore). 

Good luck ;)

---

### Post by rapattack1 on 2011-03-23
Don't worry i was surprised myself. I know when i picked up the box from the street it was an AMD but paid little attention to it because the case is so rusty and the psu. Then i saw the sticker on the front and not knowing that much about amd 64's until i started looking at the computers on the msy website i thought wow. I have taken the mb out of the case and looked at the cpu and yes sure enough it is what i said. I tell you where i go trash hunting these people chuck out the craziest good stuff. 
Ok yeah sorry i forgot that other machine you built for someone else.
So many times i am writing somewhere on the net and i get distracted by the phone.
Well i don't know if the board is working and bench testing is not something i have mastered. I haven't got a spare psu etc to plug into this. I hate pulling apart my working machines. Thats if you call this machine working lol. It will take me ages to get to it anyway. Too much happening!

Yes i know there are a lot of cheapie boards at MSY and other stuff too. I would get a separate video card thats for sure. I researched. I m just bad at remembering all the specs at a drop of a hat. Short term memory loss is fun!!!! lol NOT! :0(
So what type of board do you recommend because i think ia m getting the same as that one you mentioned. I dunno will check later as i want to get offline and do my workout. It's the only way i can sleep. Plus the mozzies are chewing on my legs ekkkkkkkk. They love to hide under the desk and have a good go....buggers!!!!

---

### Post by cascade9 on 2011-03-23
Thers AMD64s from 2002. Not all AMd64 are made the same. 

I've got a 'trowaway' system I got with a AMD64 3000+ in the other room. When I get an extra PCIe video card I'll be using that for my media/'smoking room' box.....something about short term memory, but heh, to much time in the smoking room. :lolflag: (just jokes, I've actually got a good memory, my problem is a high lead count :( Ohh, and dyslexia, hence the huge number of typos)

No need to tell me about the stuff people throw away, I've found some really nice stuff by the side of the road. That 3000+ I was talking about above is using a found PSU (thermaltake 430watt) and HDD (seagate 80GB). If only the onboard video worked it would alreadyb be downstairs.

I really like the gigabyte boards. Gigabyte GA-870A-UD3 is what I would get. An asus M4A-87TD is probably the best 2nd choice (they are cheaper than the gigabyte boards, but for various reasons I just dont like the asus boards as much)

Cheap hint- if you have a wooden desk, try putting a bit of tea tree oil on the back of the desk legs. Mozzies hate the stuff. Its also good for removing sticker crap, using on skin problems (nothing kills acne faster), as an anti-fungal, anti-bacterial, general odour removal, and a whole heap of stuff I cant recall now. Short term memory again LOL. 

I dont know how you can workout before sleep, that normally wakes me up. Unless I do a very long session. I might have to do that tonight, the weather up here has decided that since we got a wet cool summer, its going to be a hot, humid autumn. I dont deal well with high heat + high humidity.

---

### Post by rapattack1 on 2011-03-24
Ah ok i didn't know the 64's went that far back.
OK dunno what a media/smoking room is lol. Never smoked anything and everything is in one room for me he he. Gee how do you get a high lead count?
My short term memory is because i have CFS. Pretty common but hey i better than some in my position :0)
Gee how do i explain my typos then lol?
Ah so your out there collecting too. Great! Someone has to reuse eh!!!
Ah ok yeah i think the board in that machine i am ordering from msy has an asus board. I think one these machines i have here has an asus. Oh and the eepc lappie has an asus board. Gee i miss my little lappie but now that i have a blackberry i don't need it. I got given the BB and it had a cracked screen. What an easy thing to fix/replace!!! Having a great time with it!

I think this is a laminated chip board desk but yeah i would have to use mountains of Teat tree to get rid of these mongrels. Grrrrrrr. I have mcs as well which means i got to be careful how much natural stuff i use and definately no synthetic substances. Grrrrr hate being sick but that problem has always existed so i am used to it!
Yep i do use teat tree oil for cleaning stickers off things and general cleaning but i have to water it down because of the smell.
Ha ha yeah tea tree is great. I made a different cleaner the other day though and can't wait to try it. Soak orange peels in vinegar for a week or two then pick out the peels. Great for cleaning the benchtops apparently. Anyway thats for later :0)

Yeah i have to do up to an hour then the stiffness goes from my body. It is not heart racing type of working out. Just doing pilates.
Yeah humidity is bad. I deal with it better than most but that cold weather i never deal with that well.

Well hope you did get some sleep. Phew working on someones lappie right now. Gee damn windows vista is crapppppppppppp. I think though that he has a stuffed hard drive so i will recommend he take it to a shop to get looked at.

---

### Post by rapattack1 on 2011-03-27
OK the system i might get tomorrow is this.
ASRock N68-S3-UCC DDR3
AMD x4 Quad Core 955 3.20Ghz for $390 or AMD x2 Dual Core 555 3.20Ghz $330
i will get more ram which is $55 for 4gb
This machine has no dvd writer/OS/monitor.

Just looking on the msy website to see if they have the boards you like

OK now i had a closer look at the parts pages of msy. 
How about this as a package:
Asus board [http://msy.com.au/product.jsp?productId=3147](http://msy.com.au/product.jsp?productId=3147)
AMD cpu [http://msy.com.au/product.jsp?productId=1435](http://msy.com.au/product.jsp?productId=1435)
PQI ram [http://msy.com.au/product.jsp?productId=5196](http://msy.com.au/product.jsp?productId=5196)
His video card [http://msy.com.au/product.jsp?productId=6267](http://msy.com.au/product.jsp?productId=6267)

I can use the case i have now.....ok not sure if that MB will fit in it. Will have to look at that. And i bought a psu so recently i think i could use that. Bought from msy. Did i miss anything?

---

### Post by cascade9 on 2011-04-15
Probably way to late, but I've pretty much quit this site due to the actions of canonical. 

ASRock N68-S3-UCC DDR3? Wouldnt touch it with a bargepole. I've got the DDR2 version of that board, its the cheapest, nastiest board I've seen in years...  I'd get a decent board with less RAM and CPU.  Changing CPU and adding RAM is easy, changing motherboards is much more of  a pain......

BTW, you might find this article intersting and usefull- 

[http://www.linuxaria.com/article/music-production-linux-1?lang=en](http://www.linuxaria.com/article/music-production-linux-1?lang=en)

Found it here- 

[http://www.linuxquestions.org/questions/syndicated-linux-news-67/lxer-music-production-in-linux-1-a-872292/](http://www.linuxquestions.org/questions/syndicated-linux-news-67/lxer-music-production-in-linux-1-a-872292/)

> **rapattack1 said:**
> Ah ok i didn't know the 64's went that far back.
OK dunno what a media/smoking room is lol. Never smoked anything and everything is in one room for me he he. Gee how do you get a high lead count?

High lead copunt, easy- printing tiles (lead based glaze), plastic (lead in the plastic) and using leaded petrol to clean stuff.

---

### Post by rapattack1 on 2011-04-15
Oh what did Cononical do?

Thanks i ended up buying the machine i was originally after. Well the dual core one. I will just have to wear whatever happens. I know motherboards are much harder to change. Ah well. I get the new computer in a few days. I was just tired of waiting. Not because of you but because a few people were supposed to help me out and i can't wait forever. :0)


Ekkkk that sounds like a nasty concoction of poison :twisted:

Thanks for all your help!!!!

Oh did i tell you i got a Samson co1U microphone? Its nice. Haven't given it a strong test yet!

---

