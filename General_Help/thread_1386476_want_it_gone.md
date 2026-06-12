---
title: "want it gone"
date: 2010-01-20
forum: General Help
---

### Post by cloudytriker on 2010-01-20
hi, I down loaded  ubuntu 9.10 to disk then tryed a dual install. appeared to be sucsessful but when restarted computer would not allow me to select which operating system to use. after set time started windows xp. thought I'd remove the program but still get the select screen on start up. tried reinstalling it and still have the same problem. All I want now is for this program to be gone an have my computer back the way it was. Thankyou

---

### Post by pqwoerituytrueiwoq on 2010-01-20
are you using ubuntu and not able to load or xp with out some hd space

---

### Post by 73ckn797 on 2010-01-20
If you want to restore back to only Windows then boot from the Windows disk and select recovery (pressing r). Once at the command prompt type in ```
fixmbr
``` then remove disk and reboot.

---

### Post by cloudytriker on 2010-01-20
inserted the windows disk.shut down the computer then restarted .it asked if i wanted to boot from disc click any key. I clicked enter, then it went to the select operating system screen again . wouldn't allow me to choose. counted down then started wimdows

---

### Post by pqwoerituytrueiwoq on 2010-01-20
i assume you are using a wireless keyboard
so use a hardwire one

---

### Post by cloudytriker on 2010-01-20
have a hard wired key board

---

### Post by Leppie on 2010-01-20
in xp, go to the command prompt then issue the "fixmbr" command.
that should do the trick.

---

### Post by cloudytriker on 2010-01-20
excuse the ignorance but where is the command prompt?

---

### Post by steveneddy on 2010-01-20
Start --> Run --> Command

I think

---

### Post by cloudytriker on 2010-01-20
start- run  gives a box called run, won't recognize fixmbr

---

### Post by Leppie on 2010-01-20
i believe it's: Start>Accessories>Command Prompt

---

### Post by cloudytriker on 2010-01-20
thanks have worked out how to retore the system back to yesterdays settings, seems to have done the trick.thanks for the help

---

### Post by djchandler on 2010-01-20
> **cloudytriker said:**
> hi, I down loaded  ubuntu 9.10 to disk then tried a dual install. appeared to be successful but when restarted computer would not allow me to select which operating system to use. after set time started windows xp. thought I'd remove the program but still get the select screen on start up. tried reinstalling it and still have the same problem. All I want now is for this program to be gone an have my computer back the way it was. Thank you

You may need to hit escape during a short countdown to get the GRUB (GRand Unified Bootloader) menu.

To return your machine to its original state, try this link:
[http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php](http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php)

I can't vouch for its safety nor do I accept responsibility if this messes up your XP install. Using the XP install disk and selecting repair from its menu should have worked.

Another suggestion is get [SuperGRUB]("http://www.supergrubdisk.org/"). You can download an ISO CD image that will let you boot from the CD, then choose from any OS installed on your hard drive(s).

Neither of these will actually remove Ubuntu. I assume you know how to use the administrative tools to access the [disk management]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/sag_diskconcepts_02a.mspx") utilities and delete those partitions.

Apparently you have never gotten into Ubuntu to know whether you truly like it or not.

May I make a suggestion?

Once you get things returned to their original state, then try [Wubi]("http://wubi-installer.org/"). [Wubi]("http://wubi-installer.org/") will allow you to install and uninstall just as you would a Windows program, using a virtual hard disk file instead of partitioning your disk. It uses the NTFS bootloader instead of GRUB too, so your master boot record is only altered to add the choice of booting into Ubuntu. Uninstalling from the Windows Control Panel (Add or Remove Programs) will return your XP system to its original state.

---

### Post by steveneddy on 2010-01-20
I remember

start -> run

then type in 

**cmd**

to get the command prompt

(you really need to stay in Windows......)

EDIT:

Just booted Vist in a VM

this is correct

---

### Post by dirtblack on 2010-01-20
The best way to fix that would be to use your xp disk, use it to start the system. Choose repair console after that, should get a command prompt. Run fixmbr from the disk and reboot.

---

### Post by 73ckn797 on 2010-01-20
Press Start, Programs, Accessories, Command Prompt, then enter "fixmbr" without the quotes. If Command Prompt is not in Accessories it will be in System.

---

### Post by 73ckn797 on 2010-01-20
> **steveneddy said:**
> (you really need to stay in Windows......)


They should.

---

### Post by cloudytriker on 2010-01-20
thanks for all the advice guys. restoreing the system to yesterdays settings seems to have done the trick. I have the same free hard drive space as I did before installing the ubuntu program. will not try it again. will stick with what works.

---

### Post by d3v1150m471c on 2010-01-20
run "cmd". that will take you to your command prompt

---

### Post by 73ckn797 on 2010-01-20
> **cloudytriker said:**
> thanks for all the advice guys. restoreing the system to yesterdays settings seems to have done the trick. I have the same free hard drive space as I did before installing the ubuntu program. will not try it again. will stick with what works.


You can figure it out. Maybe now is just not the time.

---

### Post by jamesisin on 2010-01-20
You can't run fixmbr from the normal login/command prompt or run dialog.  You have to use the recovery console:

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

---

### Post by _H3MLOCK on 2010-01-20
Basically, you installed ubuntu and set up a dual boot using some boot loader, I'm thinking its the windows one since windows was set as the default boot. The reason you couldn't select ubuntu is because apparently your keyboard is not supported by your BIOS... Either update your BIOS or use an old PS/2 keyboard to get keyboard support on boot.

---

### Post by steveneddy on 2010-01-21
OK - you fixed the issue. great!

Now since you seem to be an inexperienced user regarding possibly advanced computer functions and applications, I would like to recommend that you start trying out Ubuntu in a virtual machine.

No, not Wubi. Stay away from Wubi.

Go to:

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

which is the website for the VirtualBox virtual machine - this is the downloads page.

Download for your version of Windows and then you can run Ubuntu or other operating systems in VirtualBox, negating the need to partition your HD and still getting a real experience.

Ubuntu is a completely different environment than Windows. The learning curve is high. 

Using a virtual machine will give you the opportunity to experience Ubuntu slowly without messing up your Windows machine or settings.
:popcorn:

---

### Post by jamesisin on 2010-01-21
Also, you should probably mark this thread as SOLVED (in Thread Tools above).

---

### Post by Leppie on 2010-01-21
or using the link just below the last post :P

---

