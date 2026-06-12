---
title: "Virtualbox PUEL lost USB connectivity after upgrade to Karmic"
date: 2010-01-14
forum: General Help
---

### Post by shrauf on 2010-01-14
Hi All! I hope you can help.

I am using the VirtualBox PUEL version, and I used to run Windows + the driver program of my Lexmark USB scanner - successfully.

Now I have upgraded to Karmic, and when I try to attach the virtual machine to the USB scanner I see its line (and all other lines) greyed out, see the screenshot below:

[IMG]http://www.borgulya.hu/%7Egabor/20100114183407GM_USB_gray.png[/IMG]

Thus I have lost USB connectivity after upgrade to Karmic.
Also in the yellow status box "Unavailable" appears.
Any ideas how to use my scanner and other USB devices again?

Thanks!

---

### Post by falconindy on 2010-01-14
You'll need to rebuild the VBox kernel modules for the new kernel that Karmic installed:
```
sudo /etc/init.d/vboxdrv setup
```
This has to be done every time a new kernel is installed.

---

### Post by osmorphyus on 2010-01-14
now is this a general fix for Vbox in karmic?

check this:  i was trying to run Vbox w/XP to run a CLIP MP3 player which is currently unusable in karmic.  no matter WHAT i tried, my USB connectivity stayed greyed out.

i was bummed to find that 9.0c release of UBU supported the CLIP player, but karmic does not, and doesnt look like it will anytime soon.

i was  then going to try to run 9.0c in Vbox, and still my usb connectivity was greyed out.  i gave up on it, for now, until i can get some answers about the usb problems between karmic and vbox.

incidentally, the clip mounts is detected on my xDSL install, but not mountable.  i dont know why.  it says something about the file system not being mountable.  ill create a thread about that one when i try it again.

---

### Post by shrauf on 2010-01-14
Thanks [falconindy]("http://ubuntuforums.org/member.php?u=863375").
The compilation seemed successful:
```
shrauf@vm1520:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for shrauf:
 * Stopping VirtualBox kernel module                                                                                                                                                                       *  done.
 * Removing old VirtualBox netadp kernel module                                                                                                                                                            *  done.
 * Removing old VirtualBox netflt kernel module                                                                                                                                                            *  done.
 * Removing old VirtualBox kernel module                                                                                                                                                                   *  done.
 * Recompiling VirtualBox kernel module                                                                                                                                                                    *  done.
 * Starting VirtualBox kernel module                                                                                                                                                                       *  done.
shrauf@vm1520:~$
```Also the new kernel module seems to be loaded instead of the old one.
Still I have the same problem, the USB devices are greyed out.

---

### Post by osmorphyus on 2010-01-14
i have waited for an answer to the vbox greyed usb problem in karmic for a long time now.... 

the world is watching, karmic!

---

### Post by shrauf on 2010-01-14
Do you think as a workaround I could downgrade some packages to make it work again?
VirtualBox itself was upgraded, too, during my distribution upgrade.
Of cause the best would be if it just worked as it did.

---

### Post by falconindy on 2010-01-15
Hmmmm, stupid question and a possible fix:

1) Are you sure the USB controller is enabled for the guest?
2) If you answered yes to the above, try adding this to /etc/fstab:

```
none        /proc/bus/usb           usbfs       auto,busgid=108,busmode=0775,devgid=108,devmode=0664    0 0
```
Run 'sudo mount /proc/bus/usb' after editing and relaunch VirtualBox. I had to use this trick to get USB working on VBox, but I've got a rather unconventional setup.

---

### Post by shrauf on 2010-01-16
Dear [falconindy]("http://ubuntuforums.org/member.php?u=863375"), thanks for your kind further efforts.
1) the USB controller is enabled in the guest.
2) I tried the edit fstab, mount, restart VirtualBox procedure, too, but all USB devices are still grey.

---

### Post by falconindy on 2010-01-16
> **shrauf said:**
> Dear [falconindy]("http://ubuntuforums.org/member.php?u=863375"), thanks for your kind further efforts.
1) the USB controller is enabled in the guest.
2) I tried the edit fstab, mount, restart VirtualBox procedure, too, but all USB devices are still grey.
Could you post the results of the following?

groups
cat /etc/group

---

### Post by shrauf on 2010-01-17
Thanks, [falconindy]("http://ubuntuforums.org/member.php?u=863375")! That was the solution!
```

shrauf@vm1520:~$ cat /etc/group | grep v*box
vboxusers:x:124:
shrauf@vm1520:~$ groups
shrauf adm dialout cdrom plugdev lpadmin admin sambashare
 
```During the distribution upgrade I got removed from the virtualbox group! :(

The following command
 ```

 shrauf@vm1520:~$ sudo usermod -G vboxusers -a shrauf
  
``` plus logging out from the X windows and logging in again has solved the USB accessibility! :D

I am grateful for your help.

---

### Post by eggplant37 on 2010-01-17
I've discovered here that mounting usbfs works fine on 2.6.31-17-generic; however, an upgrade to 2.6.31-18-generic over the weekend, mounting usbfs utterly fails for no apparent reason. I believe there's a problem somewhere in the kernel and related modules and have another thread open to figure out what's what.

---

### Post by falconindy on 2010-01-17
> **shrauf said:**
> Thanks, [falconindy]("http://ubuntuforums.org/member.php?u=863375")! That was the solution!
```

shrauf@vm1520:~$ cat /etc/group | grep v*box
vboxusers:x:124:
shrauf@vm1520:~$ groups
shrauf adm dialout cdrom plugdev lpadmin admin sambashare
 
```During the distribution upgrade I got removed from the virtualbox group! :(

The following command
 ```

 shrauf@vm1520:~$ sudo usermod -G vboxusers -a shrauf
  
``` plus logging out from the X windows and logging in again has solved the USB accessibility! :D

I am grateful for your help.
Awesome, glad to hear you're up and running. You could/should probably see if you can operate without the manual usbfs mounting. It's a filthy hack that I use in lieu of HAL, but really shouldn't be necessary in Karmic.

---

### Post by osmorphyus on 2010-01-17
<my 2 cents>

i fail to see how this establishes a problem as solved.  solved would entail the problem to be fixed in the current updated and active kernal.  nobody wants to reinstall an older version just to get one app working to its full potential.

thats why im not rolling back to a 9.0c release just to get one mp3 player working.  sure, i could do it, but what does that do for the current release?  USB functionality *has* to be corrected in the current build with no exceptions.  offering a partially completed package benefits noone.  i dont even want to run a VBOX if i dont have to, and if i do have to, i want it to work entirely. 

 i am looking to use linux exclusively (ubu builds).  i dont want to (and dont at all, mind you) rely on a dual boot option into xp for "some things" because as i become more and more used to using linux, and skilled with it, i grow to dislike the entire windows operating system in every way more and more.  the look, the feel, etc.

so i dont see this as solved.  i see it as a suggestion to others who have the same problem:  if you want this function to work, for now you will have to use another option, and hopefully someone is looking into it behind the scenes.

</my 2 cents>

---

### Post by falconindy on 2010-01-18
> **osmorphyus said:**
> <my 2 cents>

i fail to see how this establishes a problem as solved.  solved would entail the problem to be fixed in the current updated and active kernal.  nobody wants to reinstall an older version just to get one app working to its full potential.

thats why im not rolling back to a 9.0c release just to get one mp3 player working.  sure, i could do it, but what does that do for the current release?  USB functionality *has* to be corrected in the current build with no exceptions.  offering a partially completed package benefits noone.  i dont even want to run a VBOX if i dont have to, and if i do have to, i want it to work entirely. 

 i am looking to use linux exclusively (ubu builds).  i dont want to (and dont at all, mind you) rely on a dual boot option into xp for "some things" because as i become more and more used to using linux, and skilled with it, i grow to dislike the entire windows operating system in every way more and more.  the look, the feel, etc.

so i dont see this as solved.  i see it as a suggestion to others who have the same problem:  if you want this function to work, for now you will have to use another option, and hopefully someone is looking into it behind the scenes.

</my 2 cents>
This isn't your thread. The OP's problem is solved, therefore the thread is too.

---

### Post by osmorphyus on 2010-01-18
"isnt your thread",  thats cute.  i noted problems with the same thread however, and the fact remains that the issue will need deeper resolution behind the scenes, else the problem will continue to resurface.

---

### Post by falconindy on 2010-01-18
> **osmorphyus said:**
> "isnt your thread",  thats cute.  i noted problems with the same thread however, and the fact remains that the issue will need deeper resolution behind the scenes, else the problem will continue to resurface.
If you want advice, you need to do more than gripe. Have you tried everything in this thread?

1) Have you compiled the VBox kernel module for your current kernel?
2) Do you have guest additions installed on the Guest OS?
3) Is your user on the host OS a member of vboxusers?
4) Is the USB controller enabled for the Guest?
5) Failing all that, have you tried manually mounting usbfs?

"It still doesn't work" doesn't provide enough for anyone to be able to provide assistance. Also, this isn't an upstream bug.

---

