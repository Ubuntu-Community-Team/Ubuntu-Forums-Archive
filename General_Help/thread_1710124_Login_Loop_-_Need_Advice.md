---
title: "Login Loop - Need Advice"
date: 2011-03-19
forum: General Help
---

### Post by Ashkwil on 2011-03-19
Hi I have bee running ubuntu 10.10 for about 2 weeks and all has been going smoothly.

I added on some extras to the file manager and download ubuntu tweak, and afterwards some of my documents wouldnt open and said the program to open them was not specified. So i simply uninstalled the addons (but not ubuntu tweak) Then i still could not get into folders so i opted for a reboot.

Now the login screen loads and when i enter my password it just goes black and goes to login again

Ive tried Alt+Ctrl+F1 and tried some stuff I found on the net but its all very confusing to me as im very new to this.

Any suggestions would be great cheers

---

### Post by reiv on 2011-03-19
I ran into similar problem just by updating the natty, though mine already freezed at initializing the gfx mode. I managed to halt the bootup to terminal mode before the gfx initilized by hammering ctrl alt shift + f1 - f8 (not all at the same time, it locks up the kbd!).

Then i googled for some config files, but editing those did nothing. The solution was apt-get remove nvidia* and when that was not enough i did gnome* then reinstalled them and voilâ it boots up and my files are intact!

I am not saying this is how you should do it, this is how my first linux experience started. The terminal really is your friend after a quick sudo passwd and apt-get is THE spell.


(dd if=/dev/null of=/dev/hda was considered briefly during the struggle, as no "startup recovery" was presented, only a mandatory chkdsk after "29 unsuccesfull volume mount"s...)

---

### Post by Ashkwil on 2011-03-19
So your saying I shoudl keep hammering ctrl shft + f1 constantly until I get the terminal, then login through terminal and type

Sudo su
Apt-get uninstall nivada*
Apt-get uninstall gnome*

Then re-install gnome?

If so how do I reinstall it? Sorry if I'm TOTALLY wrong but I'm very new to this, sucks I ran into this problem after only 2 weeks

Cheers

---

### Post by reiv on 2011-03-19
I don't know the exact combo, but the 12-key  one should be universal, both getting to bootloader and to do a terminal login during startup.

Yes, nvidia* for the gfx drivers, assuming you have installed such. This might be enough. You could try something sensible before trying uninstalling gnome*

for instance kill your config files:

cd ../../
sudo rm -vrf .*

if this is not enough go for bigger bombs like..

apt-get remove nuke*

some nukes:

xserver
xorg
gnome
ubuntu-desktop
(ubuntu
kernel)

(put the * after the name only if you are too lazy to find out the exact package names with apt-cache search or similar command)

then

apt-get install nuke
apt-get update
apt-get upgrade

Don't use the * wildcard here since you might end up downloading quite a lot. I don't know exactly.

make sure to reboot now and then during the process and see if you are good so as not to make unnecessary damage. Or wait for someone who knows what they are talking about to instruct you.

---

### Post by Ashkwil on 2011-03-20
Ok thanks for the informative reply I'll give it a go :)

---

### Post by Ashkwil on 2011-03-21
Ok well i tried all of the above and even went for the uninstall gnome, which now I cannot even get into the recovery console

I am also very mad as the email client has downloaded all of my emails to that PC and now its died, is there anyway to get them back as i didnt even realise it had taken them actually off of hotmail!!

I really need all of them back, is there bany way????

---

### Post by pqwoerituytrueiwoq on 2011-03-21
use a live cd and a flash drive
copy the email clients folder to another computer slap the folder in and open the email client up
ex using thunderbird
copy .thunderbird to usb
go to another comp (reinstall/livecd/another install/etc)
copy .thunderbird to $HOME/ and open the email client

as far as removing nvidia i have had that issue on lucid xubuntu
the issue is gdm crashes on login i managed to get the driver working somehow i don't remember maybe when i re-downloaded the driver they fixed a bug in it
once i removed nvidia i just had to use the failsafe xorg.conf file then i could use it
sudo rm /etc/X11/xorg.conf
sudo cp /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf

---

### Post by Ashkwil on 2011-03-21
Ok so I would boot from cd, copy the client folder to usb stick from the hdd, copy to a new pc and open it with thunderbird, then export a .thunderbird file (which contains all of my emails?) And then once I reinstall ubuntu re-open the .thunderbird file? Is there anyway to get them back onto my actual hotmail account?

As for the loop, if I leave the pc to boot now I get a grub menu (after gnome was uninstalled) if I click the recovery console loads of writing flashes up and it just stops and doesn't load any further, I can't get to any command line apart from the grub one, is it a lost cause? Should I just reinstall? Also is 10.04 more stable than 10.10 or?

Oh as for nivada I do not have a graphics card I have intergrated graphics but I did the uninstall anyway but obviously I can't reach a command line to reinstall anything

Thanks again for all of the help

---

### Post by pqwoerituytrueiwoq on 2011-03-21
i do not know what email client you were using 
.thunderbird is a folder not a file
if you are using evolution mail the folder is .evolution
it is located in your home folder
if you copy the folder and open the program it will be the same as if you opened it on the old setup

---

### Post by Ashkwil on 2011-03-21
Ok well yeah I think it was evolution it was the default mail application so...

Also if I open the filesystem from the cd to copy to usb it will most probabley say I don't have the permissions maybe?

I will try when I get home and see what happens

Cheers

---

### Post by Ashkwil on 2011-03-21
Ok sorry for the double post...

Ok so i am currently on the live CD now, my windows HDD is visiable and mounted, but my linux one is visible but unable to mount, i get this error 

"DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending"

It will not mount, if it would i could just take the emails straight out, anyway around this?

Thanks again for the help, as for the boot loop still no luck, looks like its going to have to be a clean install :/

---

