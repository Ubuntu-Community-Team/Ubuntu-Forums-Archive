---
title: "It's Grub Again???"
date: 2011-09-26
forum: General Help
---

### Post by ken0069 on 2011-09-26
OK so I've got this multiboot system that has 5 hard drives in it with as many operating systems, one of which is Ubuntu 10.10.  When I did the install 2 years ago I disconnected the other 4 drives because I didn't want grub on them.  Yeah, and I don't like mayonnaise on my ham sandwich nor do I like cheese on my nachos!  And I really don't like grub on my Windows drives!!!  REALLY!!

For the past 2 years or so I've been disconnecting those drives when I did Ubuntu updates but day before yesterday I had a "senior moment" (I'm 66) and did those updates without disconnecting the Windows drives, which obviously had a grub update also as now when I boot up I get that 10 second pain in the a** boot screen that I hate with a white hot passion before my computer will boot to the drive I have already selected in BIOS!!!???

So I just spent an hour cleaning the grub crap out the boot sector on those 4 Winders drives and now I need to edit the grub boot junk in Ubuntu to get those drives out of my Ubuntu 10.10 load.  

Any help?

Thanks,  

Ken0069

---

### Post by Neobuntu on 2011-09-27
Grub isn't usually auto installed, on all your drives; unless you installed one drive, per distro, at a time. As if, each was the main drive. It's usually, automatically done for you; on your main boot drive. It just gives you the menu option, to boot anything else it may find, that's connected. In any case, having other options, on a GRUB menu, wouldn't slow down booting the "default" drive. Depending on how you set it. It may be a different, speed issue.

Once installed, the default Ubuntu install, without other drives, will not pause at the GRUB menu; unless you hold down the SHIFT key. Perhaps that&#8217;s what you want. To skip the GRUB menu. Once, all other drives are disconnected (if that's easy for you to do), just try...

sudo update-grub

---

### Post by garvinrick4 on 2011-09-27
You want to only boot Ubuntu when booting that drive in Bios first and not to see a grub menu then you have to edit /etc/default/grub as to not show a grub menuentry at all.
```
gksudo gedit /etc/default/grub
```[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub")

Whole section on editing /etc/default/grub as to do what you wish.
Remember after making changes must.
sudo update-grub
to put them in config-file and make them permanent.

---

### Post by garvinrick4 on 2011-09-27
When you install grub2 (grub-pc) you just have to tell it which drive to install on.
sda
sdb
sdc
sdd
sde
It will go into the mbr of only drive you tell it to, you are in control of your machine.
#It will not go jumping from drive to drive like a fungus.
#Now grub2 does have a package called os-prober to go out and fetch other operating systems
and put them in the grub2's config file and as a menuentry on that one drive. If you do not want
it to do that then remove "os-prober" and make a new config file with sudo update-grub
```
sudo apt-get purge os-prober
``````
sudo update-grub
```No more other operating systems discovered. No reason to hate with a white hot passion. Is a very nice boot loader you just did not understand it.

---

### Post by ken0069 on 2011-09-27
So what you are saying is that grub does not install anything on those 4 Windwos drives?  I was under the impression that it did because I had a Windows problem years ago that I attributed to grub and it's been mentioned on other boards that the fix for removing it from Windows drives is just to do a fdisk /mbr and that will wipe it out?  Which is what I did on those 4 drives.  Win XP isn't bad but on both Vista and Win7 you have to load the DVD, boot from that and have it fix the MBR before that OS will boot again.  

This Ubuntu load started out as 9.04 and has been updated to 10.10 and as I said, I've been disconnecting the other drives when I did updates until the other day.  Now I get the grub boot menu and all those other drives are listed?

So the purge command then update grub command will remove the Windows drives from grub?

Thanks

---

### Post by Blasphemist on 2011-09-27
You have been working under some misunderstandings. When Grub2, or its predecessor Grub, is installed it writes some components to the Linux partition and a component to the mbr of the drive designated. This component written to the mbr does little besides take the hand off from bios and then provide boot functionality based on choices for configuration that you make, by loading components from the Linux partition. I doubt that you have done any configuration by the sounds of it so the default configuration is in place. 

When an update that includes a kernel update happens, grub must be updated to know about the new kernel version but that happens to the part of grub in the Linux partition, not what is in the mbr. If an update happens that changes grub version, such as would have happened to you at some point (I think when you updated to 10.04) when Grub went from Grub legacy to Grub2, the Grub installation program will be run and prompt you for where to write the part of the program that normally goes to the mbr. You will choose mbr or a boot partition and if there are more than one drive you will choose which drive.

The scripts that run during an update-grub, that you can run manually or will be run by Ubuntu when a kernel version is updated, include a script that looks for other operating systems to give you as boot options. This is the /etc/grub.d/30_os-prober and can be purged as described earlier or you can just set it to not be executable. This script only searches for other OSs and provides what it finds to grub.cfg it does not write anything to other drives or partitions. 

I do think you should do some review of the Grub2 documentation and it will all make sense to you. [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by oldfred on 2011-09-27
When you have multple installs and multiple drives it becomes difficult to keep track of what is where.

I use this for my own sanity before & after any install.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

If you use manual install, you get a choice on which drive to install grub2's boot loader. Generally it is best to install to the same drive unless you have an old IDE system that only boots sda.

Some more ways to customize grub2.
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
The Grub 2 Guide (formerly Grub 2 Basics) manual way
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Herman has some of the best guides on installing if you want lots of detail and explanation, not just a do this & it works install.
nstalling Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by garvinrick4 on 2011-09-27
> So the purge command then update grub command will remove the Windows drives from grub? If no "os-prober than no other other operating systems in config file or as a menu entry.

##oldfred is quite the grub aficionado if you were to give him a boot_info_script he could diagnose your whole system if you choose. (Windows and Linux)

@Ken0069
   You have a nice day and enjoy your Ubuntu, with all the links I believe you will understand grub2 (grub-pc) better and see how it can be manipulated to whatever you choose it to accomplish.

## To bad there is no link[COLOR=Red] for that Sr. Moment thing[/COLOR] you are on your own there, do the put something where you will never lose it thing and forget where you put it about 2 minutes later that
is always a nice one.

---

### Post by ken0069 on 2011-09-27
> **garvinrick4 said:**
> When you install grub2 (grub-pc) you just have to tell it which drive to install on.
sda
sdb
sdc
sdd
sde
It will go into the mbr of only drive you tell it to, you are in control of your machine.
#It will not go jumping from drive to drive like a fungus.
#Now grub2 does have a package called os-prober to go out and fetch other operating systems
and put them in the grub2's config file and as a menuentry on that one drive. If you do not want
it to do that then remove "os-prober" and make a new config file with sudo update-grub
```
sudo apt-get purge os-prober
``````
sudo update-grub
```No more other operating systems discovered. No reason to hate with a white hot passion. Is a very nice boot loader you just did not understand it.

Ran this once and when it rebooted it still had the boot screen and still had my Windows drives listed even though they are all disconnected?  Just ran this again and here is what I got:

```
ken@ken-System-Product-Name:~$ sudo apt-get purge os-prober
[sudo] password for ken: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package os-prober is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
ken@ken-System-Product-Name:~$  

ken@ken-System-Product-Name:~$ sudo update grub
sudo: update: command not found
ken@ken-System-Product-Name:~$ 

```

---

### Post by garvinrick4 on 2011-09-27
> ken@ken-System-Product-Name:~$ sudo update grub```
sudo update-grub
```Forgot the piece between update and grub (Senior moment)

What is output of
```
grub-install -v
```## You should be fine now.

---

### Post by Blasphemist on 2011-09-27
The command includes a -
```
sudo update-grub
```

---

### Post by ken0069 on 2011-10-01
OK guys/gals, I think I've got it where I can live with it, ie, there's no grub boot screen showing up now and that makes me happy as one of the things I like about Ubuntu is that it boots quickly. 
  
 On another note, Thanks to all who posted all the links to the grub stuff but to be honest, I have no desire to be a Ubuntu commandline junkie as there's a bunch of stuff that I do in real life that use a great deal of my time.  I've said this before and I'll say it again now:   
 Ubuntu is a tool that I use mainly for secure online work.  A couple of years ago I had my forum's admin account get hacked, which I attributed to the possibility that I had gotten a keylogger  on that Windows computer I had been using to administer that board prior to that incident.  Since then it's been Ubuntu only for that kind of stuff and so far, so good!  I also use Ubuntu for secure transactions involving credit cards and bank accounts.   
 

 And on a final note, v10.10 will be my last Ubuntu version as I've loaded 11.04 on a mule box and I absolutely despise the new desktop junk!  I've played with Mepis and as soon as I resolve a few issues (grub there too and my N13 wireless card) I'll be updating my 3 systems to that as I'm not a big Mac fan and it looks more and more like everything done with Ubuntu is geared toward a Mac type format and away from Windows.   
 

 Again, thanks for your help and I will miss that part as I do believe that Ubuntu has the best support forum of any of the dystros to date.........................
 

 Ken

---

### Post by oldfred on 2011-10-01
Glad you got it resolved.

I also am not a fan of the new gui. But in 11.04, you can change it back on the login screen, I could not really tell the difference. But I also still am  on Maverick as my wife has complained about changing all the time. I just install to new ones to try out.

Not sure if I will convert to Unity or not. I originally did not like the change from grub to grub2 and now really like grub2, maybe once they make Unity a bit more customizable, I will also come around.

---

