---
title: "Gnome Power Manager"
date: 2011-07-05
forum: General Help
---

### Post by UtahBud on 2011-07-05
Hi there,
I've been running 10.04 LTS (loaded using Wubi alongside Win 7 Home Premium) since late last year, with minimal problems and have thoroughly enjoyed it.  However: Within the past month or so soon after logging in I've been receiving a "Low Disk Space" warning followed by the amount remaining.  First 872.6 Mb (or so) lowering slowing and sporadically to just under 400Mb. I gained some space by removing photos and music but the space loss continued.

 Saturday,  the amount remaining was 315.2 at log-in  and within minutes, while I was just reading a small text file, another warning popped up indicating I had only 36 Mb remaining.  I hadn't downloaded, updated or upgraded a thing. I searched for other large files to remove and finding none I logged off and shut it down.

 Now when I boot up to Ubuntu I get a box with the message **" Install Problem- The configuration defaults for Gnome Power Manager have not been installed correctly. Please contact your administrator."** It allows me to enter my password but when I hit "enter", returns me to that same screen (which is graphically different than log-in screen was when things were OK). ** I tried booting to an earlier Kernel, with the same results**.  I'm a noobie (and often Numb- I neither backed up my files nor wrote down my Firefox passwords) and don't have much experience using terminal, which I can access using safe mode. Ideally I would like to get it back up and running. However, I would settle for getting my data, especially Firefox passwords. Hope I wasn't too verbose here but wanted to include as much detail as I could. Thanks for any/all assistance. Bud

---

### Post by Pard68 on 2011-07-05
If you're just interested in retrieving your personal data (passwords) than I think you can access that from Windows 7 if you are using Wubi. I tried Wubi once on a VM I had (I don't run Windows straight up) and I could access and play with files while in Win7. 

Besides that I use BleachBit might want to give this a try.

[http://www.ubuntugeek.com/bleachbit-cleans-unnecessary-files-to-free-disk-space-and-maintain-privacy.html](http://www.ubuntugeek.com/bleachbit-cleans-unnecessary-files-to-free-disk-space-and-maintain-privacy.html)

EDIT

Oops forgot you can only access the terminal. Try this:

[http://ubuntuforums.org/showthread.php?t=140920&highlight=deborphan](http://ubuntuforums.org/showthread.php?t=140920&highlight=deborphan)

And I am giving you cleaning utl. because your problem reminds me of the good old days when Unix log files could over run your memory if you didn't keep them clean.

---

### Post by UtahBud on 2011-07-05
Pard,
So you believe the configuration default error was caused by low disk space?

Also, This morning I located the Ubuntu folder in Win 7 which contained two files (one 17Gb) with .disk extensions that Windows could not open.  Web downloads of .exe 's to read .disk extensions were useless.

---

### Post by Pard68 on 2011-07-05
[https://wiki.ubuntu.com/WubiGuide#How_can_I_access_the_Wubi_files_from_Windows.3F](https://wiki.ubuntu.com/WubiGuide#How_can_I_access_the_Wubi_files_from_Windows.3F)

That should help you with the Wubi thing. Sorry about not linking that the first time :)

Sorry totally forgot the Gnome problem

Instead of logging in do CTRL-ALT-F2 to get into TTY2. From there log in as root and than go

```
sudo apt-get remove gnome-power-manager
```And then 

```
sudo apt-get install gnome-power-manager
```And then

```
shutdown now -r
```If that doesn't do it than it's a write error and you need to change GPM's permissions to writing to /tmp

But seriously try to get space back with the directions above. Ubuntu won't boot if it doesn't have enough space.

And if the cleaning doesn't help try manually making the Wubi disk space bigger. That should at least let you log in so you can more easily tackle this problem (I use CLI all the time and I still find that a GUI is best when managing disk space)

[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

---

### Post by UtahBud on 2011-07-05
Thanx Pard,
I'll give those a go.
Bud

---

### Post by Pard68 on 2011-07-06
Any luck? 

I booted into the recovery mode yesterday and there is a utility in recovery mode that deletes garbage files in case your machine fills up. 

I also did a test with a VM and I am rather certain that your power manager error stems directly from your lack of hard drive space. I got the same error when I duplicated (roughly) your symptoms (ie no HDD space).

---

### Post by UtahBud on 2011-07-07
Hey Pard,
Sorry for the delay and thanx for sticking with me. So far I have been able to open and view root.disk in Win 7.  I located my "hidden" file of my critical passwords and have done my banking and paid my bills (What a relief!) but so far have been unable to locate my Firefox password folder. As far as the space issue:  I booted into recovery mode but nothing happened when I clicked on the "clean"  utility.     When I entered  "df -h"  from root in terminal:

FILESYSTEM                 SIZE               USED        AVAILABLE        USED%             MOUNTED ON           
/dev/loop0                    17G                 16G               0                 100%                      /
/dev/sda3                     564G               74G               511G              13%                     /host

I have been reading much about WUBI and resizing root.disk but still can't seem to figure out how to do it as it appears to me that I need to have space to run commands to create more space.

---

### Post by Pard68 on 2011-07-07
The alternative (not sure if it will work with Wubi but it works with VMs) is to create a larger space and than move Wubi to it. Let me do some research on Wubi (I've only used it in a VM and that was after I saw your post) and see what I can find out.

EDIT

Yeah so you have less than a gig of space. Probably less than 128MB as I have found that Ubuntu will refuse to load with less than that. 

Have you tried deleting/moving files from Wubi to Windows? Maybe that would free up some space. 

Would you be opposed to turning Wubi into its own real OS? That may be the easiest solution.

---

### Post by dragonfly41 on 2011-07-07
I was jumping through the same hoops today including the same error with Gnome Power Manager .. I had a full "/" partition.

see here .. [http://ubuntuforums.org/showthread.php?t=1794170](http://ubuntuforums.org/showthread.php?t=1794170)

and in fact I searched and read your posts.

I used ubuntu liveCD to allow me to purge files .. booting from a CD

then in ubuntu use **[COLOR=Navy]gksudo nautilus[/COLOR]** to view your files and move to trash.

---

### Post by Pard68 on 2011-07-07
> **dragonfly41 said:**
> I was jumping through the same hoops today including the same error with Gnome Power Manager .. I had a full "/" partition.

see here .. [http://ubuntuforums.org/showthread.php?t=1794170](http://ubuntuforums.org/showthread.php?t=1794170)

and in fact I searched and read your posts.

I used ubuntu liveCD to allow me to purge files .. booting from a CD

then in ubuntu use **[COLOR=Navy]gksudo nautilus[/COLOR]** to view your files and move to trash.
Not sure how that will work with Wubi since it's not really an OS in the normal sense of the word. It's installed within his Windows install. But if you can run a LiveCD and mount to the Wubi partition maybe that'd work.

If not I was thinking that installing the real Ubuntu 10.04 and then copying your entire /home to the new Ubuntu would work.

---

### Post by UtahBud on 2011-07-07
I would be willing to try using liveCD to purge files or increase size of root disk but as I said I am a NOOBIE and don't know how to create let alone run liveCD.  Or, if I were to "install the real Ubuntu 10.04" would I need to do that with or without WUBI? Would I need to create a separate partition? In a post by bcbc  he suggested "download** wubi-resize_1.3b.sh** and save it to your Downloads directory".  Then posted code to run from terminal.  How could I do that from terminal and would I have enough disk space to accomplish this?

---

### Post by Pard68 on 2011-07-07
> **UtahBud said:**
> I would be willing to try using liveCD to purge files or increase size of root disk but as I said I am a NOOBIE and don't know how to create let alone run liveCD.
It easy. You go [here]("http://www.ubuntu.com/download/ubuntu/download") and download the .iso. It will take a while (Direct download up to an hour or more. Torrent up to 15 minutes). Do that in Windows 7. Once it is downloaded pop in a CD/DVD. Right click on the file and there should be an option to burn the iso to a disk. Do that. Once it's completed you'll just need to reboot and smash F12 (or DEL depending on your BIOS/PC) Once that pops up use the arrow keys to find the "Boot to CD" and then click enter. Wait like five minutes and you'll be running a live version of Ubuntu. Make sure you click "Try Ubuntu"


> Or, if I were to "install the real Ubuntu 10.04" would I need to do that with or without WUBI?
No you'd install the "real" Ubuntu with that LiveCD. When it loads there are two options. The first is "Try Ubtuntu" the second option is "Install Ubuntu". To install it I recommend you click "Try Ubuntu" and then click the "Install Ubuntu" icon on the desktop. This way you can still use your computer while it's installing (unlike a Windows installation).

> Would I need to create a separate partition?

Technically? No. Do I recommend it? Yes!

To do the partition I'd go into Windows 7. Click the search/run bar at the bottom of the start menu. Type in "**diskmgmt.msc"**. The program should pop up. You'll want to shrink one of your partitions (it looks like you have three partitions? Probably one is a recovery for Windows and one is a recovery from your PC manufacturer and the third (SDA3) is Windows 7.). I'd shrink the SDA3 (well technically I'd delete the first two but that's a different matter).

> In a post by bcbc  he suggested "download** wubi-resize_1.3b.sh** and save it to your Downloads directory".  Then posted code to run from terminal.  How could I do that from terminal and would I have enough disk space to accomplish this?

You should have enough disk space. It shouldn't be that large of a file. If not try adding it in anyways. Technically you have way more than enough space. I've never considered what would happen if you over filled a Loop partition....

To download it from the terminal you'd do:

```
wet http://Website.com/download
```

Just insert the website and you're good to go.

---

### Post by UtahBud on 2011-07-07
Pard,
I'm currently downloading the .iso file. I'll burn it to a disc. Thanx.  In the meantime I'd like to try **wubi-resize_1.3b.sh **but am unable to locate a website to download it from. Bcbc had included it as an attachment in his forum post.  Any way I can use it? I've saved it to my WIN 7 download folder.

---

### Post by Pard68 on 2011-07-07
OK. Here is what you are going to do...

```
wget http://ubuntuforums.org/attachment.php?attachmentid=175968&d=1290144662
```This will download the file.

```
mv attachment.php?attachmentid=175968 wubi-resize_1.3b.sh
```This will rename the file to 'wubi-resize_1.3b.sh'. 

```
mv wubi-resize_1.3b.sh ~/Downloads
```This will move the file into your Downloads folder. 

Now just follow the rest of his instructions and you'll be good to go.

If/when we get this fixed for you I highly suggest you switch from Wubi to a 'real' Ubuntu install. I say this because it's a lot easier to fix all of this stuff with the real Ubuntu than with Wubi. And worst comes to worst you can always tap into the Ubuntu partition and move the /home file (which is where all the data you really care about hangs out).

---

### Post by UtahBud on 2011-07-07
Pard,
Thanx for all your time and assistance.  Once I get my current root.disk enlarged and back up and running w/GUI I'll seriously consider a 'real' Ubuntu install as long as I can keep/save/transfer my current data. I have to go do some work  so I cannot follow your most recent instructions now. When I do, I definitely let you know how it all turned out.  Any way that I can contact you directly through the forum? Take Care and again, Thank You. -Bud

---

### Post by Pard68 on 2011-07-07
If you click my name you can PM me. I'm following this topic though so I will know whenever someone posts here.

---

