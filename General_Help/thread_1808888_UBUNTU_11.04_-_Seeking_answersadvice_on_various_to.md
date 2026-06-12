---
title: "UBUNTU 11.04 - Seeking answers/advice on various topics"
date: 2011-07-20
forum: General Help
---

### Post by Cheese Power on 2011-07-20
I've been messing around with Ubuntu for a day or so and I've got a lot of preferences set up now. I really haven't done anything that requires any knowledge of the OS and how it works, but I'll get there eventually. For now I've got a few questions dealing mostly with customization and wanting a few simple explanations. I'll just sort of list them out here in no particular order. Feel free to answer any number of them. Suggestions or advice on questions are welcomed even if they may not directly answer a question. Thanks! :D

[COLOR="Blue"]1. I was wondering if there were certain terms for the various areas on the desktop. I'm using the classic layout in Ubuntu (I read many say they liked Gnome better than Unity, and classic is closer to Gnome). Are there terms to describe the following areas in Ubuntu?:

A. The first area has Applications, Places, and System menus. This seems most comparable to the Windows start menu.
B. The panel at the bottom of the desktop shows which applications or files are running. It looks like the task bar.
C. There's an area of one panel that allows you to shutdown, restart, etc. It also has networking options, sound options, time settings, and other things. This makes me think of the system tray. I think this area may also have a notification area, but I haven't noticed any notifications.[/COLOR]

2. Are there any options within Banshee to remove all but the most basic functions? Media Player in Windows had an option to go into some compact or skin mode where it took up very little space. I noticed some sort of Banshee player within the sound controls in the (system tray). Something similar to this would be ideal. I'd like to be able to just select a bunch of songs in a folder and play them all in this condensed version of the audio player.

[COLOR="blue"]3. This has to do with the auto hide feature of the panels when they are located on the left and right side of the desktop. It seems as though the panels will only reappear when my cursor hits the very top of the screen on the corresponding side. So if a panel was set to auto hide on the left side of the desktop, it would only reappear when the cursor was in the top-left-most part of the screen. Is there a way to make it appear when my cursor touches any part of the left edge?[/COLOR]

4. I noticed that I was able to access some files and folders on my Windows partition while in Ubuntu.

A. Can modifying files on the Windows partition have some unwanted consequences?
B. If I made another Linux-based partition, would my current Ubuntu partition be able to access files in the new partition in the same way? Would this require root privileges for every action?

[COLOR="Blue"]5. I've read that modifying the Windows partition from Ubuntu with something like Gparted could have negative effects on Windows' ability to boot properly. Are there similar dangers when modifying the Ubuntu partitions from Windows?

My HDD is currently partitioned like: Win7 400GB, Ubuntu 100GB.
I'm thinking about setting it up like: Win7 350GB, Ubuntu 100GB, unallocated 50GB.

If modifying the Ubuntu partitions from Windows can have negative effects, how should I go about setting this up?[/COLOR]

6. Is there a way to set the size the icons on the desktop without having to resize each one individually.

[COLOR="blue"]7. How difficult is it to set up a customized theme? I haven't found a theme for the controls that I've liked yet. I've seen a couple that were pretty decent, but usually one thing would ruin the theme for me. This made me wonder about making my own.[/COLOR]

8. I believe the media player in use right now is Totem. Like with Banshee, is there a way to have most of the controls of this application hidden or made less noticeable? I tend to favor a minimalist approach when customizing things, so being able to reduce the number of things showing or being able to hide them when I want is always a plus. Maybe someone could suggest an alternate media player that works well to accomplish this. If another player could be paused when the video is clicked, that'd be a small plus.

[COLOR="blue"]9. When setting the folder permissions (read, write, execute), do these overwrite the individual file permissions within the folder? I believe I read that this applies to other folders within the folder. Or do the folder and file permissions not interact with one-another?[/COLOR]

10. My understanding of folder permissions is that none will work without the execute permission being enabled. Why is this? I read of the following configurations(r:read, w:write, x:execute): r-x for read only, rwx for read and write, --- to deny access. The tutorial I read this from advised against other configurations. What would happen if you allowed read and write permissions but disabled execute permissions for folders? What happens if only execute permissions are granted?

[COLOR="blue"]11. I have the display set to dim when idle. What does it mean to be "idle"? The amount of time it takes for the screen to dim seems vary randomly.[/COLOR]

12. This chunk of questions relates to Linux and its uses with various companies.

A. Why do companies that use Linux machines heavily use these Linux machines? Is it just an open source, money-saving matter?
B. For a person whose responsibilities are to maintain and run things on these machines, what might his or her responsibilities include?
C. What sort of skills should this person have? What other technologies are often used in conjunction with Linux machines to accomplish some of the companies' goals?
D. I'd imagine that with servers or whatever other things are running on these machines, the companies wouldn't want excess software or system files to be taking up resources. This leads me to think that these machines would have to be handled without GUIs and such. Would one be able to simulate the limitations of these machines in Ubuntu? Is it as simple as limiting one's self to the terminal to do everything? Are there things Linux can do on its own that Ubuntu cannot do?

---

### Post by Herman on 2011-07-21
> 1. I was wondering if there were certain terms for the  various areas on the desktop. I'm using the classic layout in Ubuntu (I  read many say they liked Gnome better than Unity, and classic is closer  to Gnome). Are there terms to describe the following areas in Ubuntu?:

A. The first area has Applications, Places, and System menus. This seems most comparable to the Windows start menu.
B. The panel at the bottom of the desktop shows which applications or files are running. It looks like the task bar.
C. There's an area of one panel that allows you to shutdown, restart,  etc. It also has networking options, sound options, time settings, and  other things. This makes me think of the system tray. I think this area  may also have a notification area, but I haven't noticed any  notifications.1. Yes, I still prefer the classic layout myself but I think it's only because I have spent a lot of time using it and I have developed many habits for how to use it which best suit my needs. Old habits die hard. When I take the time to try out the new desktop I really like it and I do know it has a lot of advantages, it's just a matter of me being able to adjust to it. The more I try out Unity  or Gnome 3 the more I like it.

About the classic desktop,

A. The menubar, it has three menu buttons, applications, places and system.

B. The bottom panel, typically it has the garbage bin icon on the extreme right, and just beside that is the workspace switcher.
On the left-hand end there's a button for hiding / showing all open Windows and between that and the workspace switcher there's room on the bottom panel for your window list.

C. The notification area.

In addition, here are links to a couple of web pages I think best answer your questions,
Link 1: [GNOME 2.0 Desktop for the Solaris Operating Environment User Guide]("http://download.oracle.com/docs/cd/E19754-01/806-6873/6jfpm4g30/") - comprehensive - in particular, scroll down and see Figure 2&#8211;1 A Typical Desktop Environment.
Link 2: [The Ubuntu Desktop]("http://www.geekgumbo.com/2010/01/02/the-ubuntu-desktop-an-overview/") &#8211; An Overview - geek gumbo

... and for the newer desktop, 
Link 3: [Visual Tour of the Gnome 3 Shell in Ubuntu]("http://digitizor.com/2009/11/09/visual-tour-of-gnome-3-shell-in-ubuntu-9-10/") - 

Last, but not least, the Help Menu. I think most of us overlook the help menu, it's very helpful. (Circular blue icon with a white question mark in it).

EDIT: Link: [How to do all those things in Ubuntu Unity that everyone says you can't do in Ubuntu Unity]("http://www.security-camera-warehouse.com/blog/1440/how-to-do-all-those-things-in-ubuntu-unity-that-everyone-says-you-cant-do-in-ubuntu-unity") - Security Camera Warehouse.

---

### Post by Herman on 2011-07-21
> 4. I noticed that I was able to access some files and folders on my Windows partition while in Ubuntu.

A. Can modifying files on the Windows partition have some unwanted consequences?
B. If I made another Linux-based partition, would my current Ubuntu  partition be able to access files in the new partition in the same way?  Would this require root privileges for every action?4. Yes, Ubuntu can easily read and write to FAT and NTFS but Windows can neither read nor write to the ext series file systems. I think there is a driver to enable Windows to work with ext2 and 3, but I'm not sure about ext4. Windows doesn't have it by default AFAIK.

A. No, not that I can think of. Most people who dual boot do it all the time.
A few years ago it was considered risky to write to NTFS from Ubuntu but now we can do just about everything with NTFS except run a file system check on it. Some things we're able to do for Windows are done better using Ubuntu than Windows itself, at least in my opinion, although Ubuntu is not intended to be an auxilliary operating system to support Windows. It's meant to replace Windows.
It is possible to accidentally download a file in Ubuntu that might contain a hidden virus which will be harmless and undetected in Ubuntu. If such a file were to be copied and pasted directly from Ubuntu into Windows it could later be activated from within Windows. For that reason if you really need to copy files from one system to the other, a staging partition that both operating systems can read and write to (NTFS) is recommended. That permits files you're transferring into Windows to be scanned for viruses with your favorite Windows security program first. Ubuntu does have virus scanners, just for the use of people running Windows. Ubuntu doesn't need any virus scanner for its own use. Files we make ourselves in Ubuntu should be okay, it's just internet files you need to be careful with.
Apps in Ubuntu such as writer and spreadsheet apps can easily create files in a range of formats to suit various versions of Windows by using the 'save as' function. This another example of something GNU/Linux OS's can do better than most Windows programs are capable of. (Probably because they want you to pay money again for the newer version of their programs).

B. Yes, you will be able to access files in a data partition regardless of what file system you format your new partition with.
You can set file ownership and permissions on the mount point,  (the directory you create as a sort of doorway into the other file  system, usually but not necessarily located in either your /media or  /mnt directories).  We use the chmod and chown commands for that.  If you use a Gnu/Linux file system you will have the ability to set file ownership and permission rules on directories and files within the file system.

---

### Post by Herman on 2011-08-19
> [COLOR=Blue]5. I've read that modifying the Windows partition  from Ubuntu with something like Gparted could have negative effects on  Windows' ability to boot properly. Are there similar dangers when  modifying the Ubuntu partitions from Windows?

My HDD is currently partitioned like: Win7 400GB, Ubuntu 100GB.
I'm thinking about setting it up like: Win7 350GB, Ubuntu 100GB, unallocated 50GB.

If modifying the Ubuntu partitions from Windows can have negative effects, how should I go about setting this up?[/COLOR]5. This is (at least in my opinion) a popular misconception that has been picked up by web parrots and repeated around the internet so many times that people tend to believe it just because it has been stated so often, (and exaggerated).
The problem is that Windows ships with a simple boot loader. I imagine the reason for that is probably because it isn't in Microsoft's interest to promote dual booting, even with other versions of their own operating system. They'd rather have you buy a new computer with a new operating system in it and then next year when a newer version of Windows comes out you're supposed to be excited and go buy new computers and all the software to go with them or else you'll be made to feel inferior. Windows doesn't make money from making a good boot loader and encouraging people to dual boot. They are in business to sell operating systems and software.
Fortunately though, they do provide some very good and easy use tools for fixing their boot loader when it's functionality is lacking.  As long as you have your Windows Installation CD or DVD you can always fix your Windows boot. If the Vista/Windows7 boot repair tool doesn't do it then go to the command line and run bootrec /fixboot and possibly CHKDSK /R. I haven't run into a Windows installation yet that isn't easy to fix after resizing with GParted.
It's a lot faster to shrink a Windows partition with GParted than with Windows own inbuilt tools because with GParted the Windows file system does not require to be defragged first, which can save many hours of waiting time, and also GParted can shrink Windows as much as the user wants. Windows own tools can only shrink Windows to about half-way at the most. An exception to this is if Windows is installed in any kind of special format such as any kind of encryption, dynamic drive overlay or RAID or the like. In those cases you would probably not be touching it anyway, but looking at using another hard disk.

For your specific situation as you only want to shrink Vista from 400 GB to 350 GB it will probably not matter which partition editor you use. If you wanted to shrink Windows to less than 250 GB though, you would only be able to use GParted since you would run into the Windows MFT at about that point, assuming your Windows originally occupied the entire 500 GB disk. GParted can move the MFT but Windows tools are not capable of that. It's a pretty good trick to be able to resize a partition while it's mounted though, I do think the Windows resizing tool is kind of neat for that trick. :)

I wasn't aware it is possible at all to use Windows tools to do anything to a Linux partition, unless you're talking about some third party app that can be installed in Windows. :)

---

### Post by Herman on 2011-08-20
> 12. This chunk of questions relates to Linux and its uses with various companies.

A. Why do companies that use Linux machines heavily use these Linux machines? Is it just an open source, money-saving matter?
B. For a person whose responsibilities are to maintain and run things on  these machines, what might his or her responsibilities include?
C. What sort of skills should this person have? What other technologies  are often used in conjunction with Linux machines to accomplish some of  the companies' goals?
D. I'd imagine that with servers or whatever other things are running on  these machines, the companies wouldn't want excess software or system  files to be taking up resources. This leads me to think that these  machines would have to be handled without GUIs and such. Would one be  able to simulate the limitations of these machines in Ubuntu? Is it as  simple as limiting one's self to the terminal to do everything? Are  there things Linux can do on its own that Ubuntu cannot do?A. I am only guessing, it depends of course on what kind of business the company or department would be running. 
I think that once the advantages of using FOSS software is realized, it just doesn't make sense to go backwards and invest more in proprietary, closed source systems. FOSS has so much more to offer.

B. 
i) Staff training - Help Desk type stuff. 
ii) Maybe maintaining servers - knowledge of hardware plus RAID and LVM, the ability to identify and swap out a failing hard disk and replace it with a new one.

C. I think such a person or people would need a good all-round knowledge of the various networking apps, like OpenSSH, OpenVPN, Apache http and Cloud computing, associated filters and security practices plus Gnu/Linux file ownership and permissions, and Zoneminder for security cameras, Quantum GIS for mapping, the list is endless. 

D. I'm not sure exactly what the disadvantages of having a server capable of video display and mouse and keyboard input could be. Maybe someone can enlighten us on this subject?
I imagine server rooms to be often small and crammed with shelves full of hardware and cables. Apart from the un-necessary expense of providing keyboards, mice and monitors for them that will only be used once in a blue moon there would be the spatial limitations. I can't see why one couldn't just hot-plug a keyboard, mouse and monitor into a unit that requires work done on it, but then again it wouldn't really be necessary even to do that if one can just SSH into a server and do everything one wants from another PC at the command line.
To train yourself and/or to train others, (staff), it would be easiest I think to begin with a box that is equipped with a monitor, keyboard and mouse and then practice controlling it by ssh from another PC in your LAN. I don't think there would be anything much that can't be done remotely by the command line that you'd use the GUI for, at least not as far as work you might need to do for a server would be concerned.

You asked a lot of good questions and I don't know why there aren't more people coming forward with answers, surely there are others around with more/better ideas/experience than me. :)

---

### Post by Mark Phelps on 2011-08-20
Regarding your question #5 ... everyone is entitled to their own opinion -- that's why we all have them.

The concern I have about using GParted to mess with Win7 partitions is if it DOES damage the partition (and there's no guarantee that it will), the solution that EVERYONE offers is essentially the same -- boot from a CD or DVD and run Startup Repair.

Why is that a problem?

For two reasons:
1) When folks buy machines today, they come with Win7 preinstalled and NO CD.  That means you do not have the CD needed to do the repairs.
2) ALL the websites the reference the downloadable Vista-Win7 Repair CD images reference the same NeoSmart Technologies site web pages -- and NeoSmart NO LONGER provides those images.

Given that there already exists a free utility inside Vista and Win7 to shrink the OS volume, and the risk that if the volume does get corrupted, you most probably have NO WAY of repairing that -- it just seems to me a big risk to take.

But then, that is only MY opinion.  And, as I said, we all have them -- opinions.

---

### Post by Herman on 2011-08-20
Just google 'Windows 7 +free download' then. :)

---

