---
title: "bootloader issue"
date: 2011-04-22
forum: General Help
---

### Post by neighbor_dave on 2011-04-22
I had Ubuntu 10.10, upgraded to 11.04 beta, didn't like Unity and tried installing gnome 3 with directions online.  Killed my ubuntu install.  So I loaded Mint and thought maybe I would like that better.  Decided to go back to Ubuntu, but keep having bootloader problems at the end of the install.  I can still install Kubuntu or Mint whenever I want, but try to install Ubuntu 10.10 or 11.04 from disc and same bootloader problem.  Curse my being fickle, any help appreciated.

---

### Post by drs305 on 2011-04-22
Hi neighbor! Welcome to the Ubuntu Forums.

We need more information. What kind of boot problem are you having? Does the installation complete? Do you have Windows on the computer? (Some third party Window apps will prevent writing to the area just beyond the MBR which caused Grub problems.)

If Ubuntu is installed but won't boot, please download the boot info script from the following site. Run the script and post the contents of RESULTS.txt.  

If you press the # icon while posting you can paste the contents between 'code' tags, which helps viewing.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by neighbor_dave on 2011-04-22
No windows or dual boot, told it to erase and use entire hard drive.  The ubuntu installations will complete if I tell it to do it without a bootloader.  Which being a newb is out of my league to install one manually.  It tells me to pick a location to install the bootloader, but there is only one option, and it doesn't accept it.  I currently have mint reinstalled so I have a working machine for the family until I get this resolved.

---

### Post by drs305 on 2011-04-22
> **neighbor_dave said:**
> No windows or dual boot, told it to erase and use entire hard drive.  The ubuntu installations will complete if I tell it to do it without a bootloader.  Which being a newb is out of my league to install one manually.  It tells me to pick a location to install the bootloader, but there is only one option, and it doesn't accept it.  I currently have mint reinstalled so I have a working machine for the family until I get this resolved.

Installing the bootloader is actually very simple from the LiveCD. You mount the Ubuntu partition and run one command. Let's assume Ubuntu is on sda5. The commands would be:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```
You just want to make sure you don't include the partition number in the second command. You want Grub2 in the MBR, not on the partition, in most cases.

The one thing that concerns me a bit is that Grub2 is not installing initially. If there is a problem with something on the drive or CD, the above may not work either (since you are using the same CD and trying to write to the same MBR).

If you are installing Ubuntu in addition to Mint, you can elect to not install the bootloader at all and you can use the Mint bootloader; at least initially. After you install Ubuntu just boot back into Mint and run "sudo update-grub" and it should add Ubuntu to your Mint Grub2 menu.

---

### Post by neighbor_dave on 2011-04-22
FIrst of all Drs305 - Gracias.  People like you are always much appreciated.  I went the dual boot route.  So now I have both.  I guess when I pick one after the final release of 11.04 or 11, I will want to pick just one.  Any advice on the best way to proceed?  Grub 2 found my ubuntu 11.04 install, but will I just run into the same problem if I try to reinstall a stand alone Ubuntu 11.04 again?  Hmmm... If you don't know.  No problema.  I'll cross that bridge when I get to it.  Anyway.  Thanks for the options and help :D

---

### Post by drs305 on 2011-04-22
We don't know why the installation failed to install G2. But if you have Grub2 on the MBR (which you do assuming Mint isn't a really old version) even if it doesn't install the next time we can give you instructions to boot into your new OS from the grub rescue prompt.

The rescue prompt would be where you end up if G2 is still on the MBR but can't find it's /boot/grub files. So I'd recommend trying to do a complete installation the next time. Just do it when you have a bit of time to get on the forums and get things resolved. That is - don't do it the night before the project is due or the spouse, friend or parent needs the computer for something really important. And have your data on a separate partition (or separate /home) so you are sure not to lose it.

---

### Post by neighbor_dave on 2011-04-22
Will do and thank you.  This is why Ubuntu Totally Rocks!!!!

---

### Post by Curly Drew on 2011-04-28
I had the same issue, only I don't dual boot. I followed the LiveCD instructions from drs305 (post #4). Now on boot I now get the grub rescue prompt, which is progress but not quite there yet...

I found some instructions for getting a one time boot for grub 1 prompt but this doesn't work on grub 2 so presumably the commands have changed. Any help would be appreciated,

Thanks,
Drew.

[COLOR=Black]
 P.s. Is there some major problem with Ubuntu live CDs? The last two  versions (10.10 and 11.04) of the live CD both fail consistently. Has anybody got any  idea of the scope(or cause/condition) of this problem?[/COLOR] [COLOR=Black]
  
  
  
  **Update**: I found a working reference and muddled through, here  is a quick walk through to get from grub2 rescue prompt to booting  Ubuntu.
  
  
Remember that pressing the Tab key will provide suggestions and auto-complete. Where you see [/COLOR][COLOR=Black][COLOR=Red]<tab>[/COLOR]  in the code, press tab, don't type it. All of the commands below  (unless otherwise specified) need to be entered into the grub2 rescue  prompt.
  
Type the following to set the hard drive and partition. Pressing tab  after "hd" will list your hard drives, if you have only one hard drive,  grub will auto complete to "hd0". When pressing the second tab grub will  list the partitions and sizes, if you are using the whole disk for one  OS then select the larger one.
[/COLOR]```
[COLOR=Black]set root[/COLOR][COLOR=Black]=(hd[COLOR=Red]<tab>[/COLOR],[/COLOR][COLOR=Black][COLOR=Red]<tab>[/COLOR][/COLOR][COLOR=Black])[/COLOR]
```The result should look something like this;
```
[COLOR=Black]set root[/COLOR][COLOR=Black]=(hd0,[/COLOR][COLOR=Black]1[/COLOR][COLOR=Black])[/COLOR]
```
Now press return. Next we are setting the kernal and root partition. The  "root=" needs to by typed out because auto complete does not work with  it. It is the same hard drive and partition referenced in the last  command but in linux' format, so for example if the root in the previous  command had instead been set to "root=(hd1,2)" the root setting below  would read "root=/dev/sdb2". 
```
linux /boot/vml[COLOR=Red]<tab>[/COLOR] root=/dev/sda1
```This should auto complete to something like this;
```
linux /boot/vml[COLOR=Black]inuz-2.6.38-8-generic[/COLOR] root=/dev/sda1
```Now press return. Next we are setting the initial ram disk by doing the following;
```
initrd /boot/in[COLOR=Red]<tab>[/COLOR]
```[COLOR=Black]Which should auto-complete to something like this;
[/COLOR] ```
initrd /boot/initrd.img-[COLOR=Black]2.6.38-8[/COLOR]-generic
```Press return. Finally we tell it to boot by typing the following;
```
boot
```And press return. 

You should (after a minute or two) be confronted with the normal log in  screen. Once logged in remember to go to the terminal and run;
```
sudo update-grub
```And press return. This is so that you don't have to follow this procedure again.

Hope this helps anyone in the same situation,
Drew

---

