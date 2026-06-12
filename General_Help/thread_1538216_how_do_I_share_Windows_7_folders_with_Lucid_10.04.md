---
title: "how do I share Windows 7 folders with Lucid 10.04"
date: 2010-07-24
forum: General Help
---

### Post by charonred on 2010-07-24
I have Lucid 10.04 as my main system, which happily shares files/folders with other Ubuntu & Windows XP PC's around the house; but for the life of me I can't get Windows 7 (new Asus Notebook & older AMD Skt A PC) to share a thing with anything (unless all other PC's are running Win7 as well) - I have Win7 PC set as a workplace PC (not part of 'Home-group').

Also I can't remember how to change the Ubuntu network settings from default 'Workgroup' to my own group name.

---

### Post by geoffjay on 2010-07-24
On Win7 you should just be able to share a folder by R-Click -> Properties the change the sharing settings. From there you should be able to browse those shares from your other computers easily enough.

To change the workgroup used in *nix you need Samba, if you haven't already you'll need to

sudo apt-get install samba 

then edit the file /etc/samba/smb.conf and change workgroup = *** to whatever workgroup you want then restart with:

sudo service smbd restart

---

### Post by charonred on 2010-07-24
Samba is already installed cause I can share with other Ubuntu/Win XP systems. What app do I edit /etc/samba/smb.conf with ? (gedit doesn't allow any changes)

Thanks for the Win7  advice - changing network settings through right click /properties is way easier than that  'Network & Sharing Center' thing (that's a real convoluted pain in the proverbial).

---

### Post by geoffjay on 2010-07-24
you'll need to start gedit via

$ gksudo gedit /etc/samba/smb.conf

---

### Post by Morbius1 on 2010-07-24
I think your smb.conf file is fine the way it is because it's only Win7 that has the problem. Besides I have 4 workgroups in my little home network and everybody is happy.

Do you by any chance have "Windows Live Sign-In Assistant" installed on Win7. You might consider uninstalling it: [http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527](http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527)

It's actually a known bug in Samba with Win7 and there is apparently a fix but I don't know when it will get passed to us.

---

### Post by charonred on 2010-07-24
geoffjay - Thanks, Win7 can now see & browse the shared folder on Lucid.

I ran the ```
sudo service smbd restart
``` command, but trying to browse my network group in Lucid I get
> **Unable to mount location**
Failed to retrieve share list from server

---

### Post by charonred on 2010-07-24
Morbius1 - I Don't have "Windows Live Sign-In Assistant" installed on the Win7 PC, but I think it is on the Asus Notebook - I change it's network settings shortly

---

### Post by geoffjay on 2010-07-24
Does it show up when you run smbtree?

---

### Post by Morbius1 on 2010-07-24
You went from this:
>                                                    I have Lucid  10.04 as my main system, which happily shares files/folders with other  Ubuntu & Windows XP PC's around the houseTo this:
>  Failed to retrieve share list from server                      What error messages do you get if you run this command from Lucid in a terminal:
```
smbtree
```Also can you access a given machine by going after it directly:
In a Terminal:
```
nautilus smb://192.168.0.100
```[COLOR=Blue]*Changing 192.168.0.100 to the ip address of the machine you're trying to access*[/COLOR]

---

### Post by charonred on 2010-07-24
I get this
> \\MYWEBWORX      		
cli_start_connection: failed to connect to MYWEBWORX<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
	\\LUCID64AMD     		lucid64amd server (Samba, Ubuntu)
		\\LUCID64AMD\vboxshared     	
		\\LUCID64AMD\IPC$           	IPC Service (lucid64amd server (Samba, Ubuntu))
		\\LUCID64AMD\print$         	Printer Drivers
	\\ASUS-K52F      		
cli_start_connection: failed to connect to ASUS-K52F<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL

Yet both Win7 (PC & Notebook) can see and browse Lucid shared folders, but I can't browse either Win7 from the other Win7 without entering a password, but I didn't set either PC or Notebook up with a password. 

When I open Network (in Lucid's Places), I'm shown 'Windows Network', and in that I have my Network name and WORKGROUP, but if I try to view anything in my network I get the following
> **Unable to mount location**
Failed to retrieve share list from server 

---

### Post by geoffjay on 2010-07-24
Have a look at the last post at [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/469548](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/469548)

---

### Post by charonred on 2010-07-24
Well I have the Win7's able to browse each other and Lucid - turned off Password protection for the shared folders in each Win7 - that's good cause they can now move files between each other and with Lucid; but Lucid still can't mount my network in Windows Network ??

update - I just fired up the other XP PC and it can browse the Win7's and Lucid, and be browsed by the Win7's, but not Lucid

update2 - suddenly Windows shares on my network now display both Win7's, XP and Lucid, I can browse Lucid and XP shares from Lucid, but not the Win7's (they still fail to mount)

---

### Post by geoffjay on 2010-07-24
So... you're in the same situation as when you started correct?

there's various posts of people saying that they've been able to fix it in this thread - [http://www.tomshardware.com/forum/75-63-windows-samba-issue](http://www.tomshardware.com/forum/75-63-windows-samba-issue)

and this is what appears to be a howto - [http://www.randyjensenonline.com/blog/connect-ubuntu-810-windows-7-share](http://www.randyjensenonline.com/blog/connect-ubuntu-810-windows-7-share)

I can't try any of this out to confirm whether it works or not because I don't really use Windows if I don't have to.

---

### Post by charonred on 2010-07-24
I'd prefer not to use Windows either, I've been using Ubuntu for just over 2 years now, and it's just so much better; but ... there are some apps I need to use that simply won't run in Ubuntu.

Dreamweaver won't, it used to in Hardy 32 & Karmic 32, but not in Lucid 64 ... I had it running for a short time, but then Wine was updated and Dreamweaver ceased to start; I tried various fixes, but nothing worked. 

CuteFTP won't even install via Wine; and there's a few other apps as well - now I've decided to go into website design & hosting properly, rather than just a 'hobby' as such, I need to be able to use those apps, and as good as some Linux apps are, they don't compare to some of the apps that run in Windows.

Hence I've setup a Win7 PC (AMD SktA with a few new bits added) - it has a genuine Windows license cause eventually the 'authorities that be' will check your software legitimacy after you register a web design business here. And the Asus Notebook came with Win7, so that's for 'on the road' presentations of websites etc.

Other than that, I really prefer Ubuntu.

---

### Post by geoffjay on 2010-07-25
Sounds like you're part of one of the most common theme amongst Linux users. I still boot into Windows for gaming, a coworker of mine hangs on to a copy for CAD work, a friend for micro controller development, and on and on. Too bad, but that's the way it's been for a long time, and wine just really isn't a viable option yet, I'd like it to be, but it's not.

Did you have any luck with the suggestions that were made at the links provided?

---

### Post by DeMus on 2010-07-25
> **charonred said:**
> I have Lucid 10.04 as my main system, which happily shares files/folders with other Ubuntu & Windows XP PC's around the house; but for the life of me I can't get Windows 7 (new Asus Notebook & older AMD Skt A PC) to share a thing with anything (unless all other PC's are running Win7 as well) - I have Win7 PC set as a workplace PC (not part of 'Home-group').

Also I can't remember how to change the Ubuntu network settings from default 'Workgroup' to my own group name.

What I use is an extra line in /etc/fstab:
```
//192.168.0.100/xxx    /media/xxx        cifs  username=guest,password=,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
```
(xxx is the username to be able to get hold of the "home" directory in Windows.)
One thing: the computer needs a fixed address otherwise this doesn't work.
I can read and write on the NTFS partitions in Windows without any problem.
Change fstab like this:
```
sudo gedit /etc/fstab

```
Add the above mentioned line to the end of the file and change the ip-address to the one you give to the Windows PC and xxx to the username (or directory name) you like to see. It has to be shared of course.
Save the file in gedit
then in the terminal type:
```
sudo mkdir /media/xxx   (change xxx again)
sudo mount -a

```
The disk will be mounted and you can use it straight away. Whenever you boot the disk will be there automatically.

---

### Post by charonred on 2010-07-25
Thanks DeMus, I 'spose it's another avenue to look at, though I'm happy with DHCP

But at least the Win7's are sharing, which means I can move, copy n paste files between them, instead of back n forth with a thumb drive - both are simply for website work and nothing else, everything else I do is via Lucid and that's fine.

---

### Post by DeMus on 2010-07-25
> **charonred said:**
> Thanks DeMus, I 'spose it's another avenue to look at, though I'm happy with DHCP

But at least the Win7's are sharing, which means I can move, copy n paste files between them, instead of back n forth with a thumb drive - both are simply for website work and nothing else, everything else I do is via Lucid and that's fine.

Yes, I also use DHCP, but with something extra. My router, which serves as DHCP server, has the ability to make reservations for clients. In a list I added the desired IP-address and the mac address of the connected network-card. That way, whenever that computer comes on line it gets that specified DHCP address. And so, I always have connections to my (and my wife's) computers.

---

### Post by charonred on 2010-07-25
Hmmm, I have a Netgear Router and I think that can reserve addresses too, so I'll have to look into that

---

### Post by geoffjay on 2010-07-25
It's not necessary to set a static IP for testing purposes, just go to your Win box and run ipconfig in a cmd prompt.

If you want to test if it will mount before adding to fstab you would run for ex.

$ sudo mount \\\\192.168.0.xxx\\share -t cifs -o username=user,password=xyz /mnt/win7share

I think. If I recall the double \'s are necessary but if that doesn't work try //ip/share instead, "share" is the name of the share that was set in Win, and the win7share directory must be created beforehand obviously.

Did you ever try any of the solutions that were in links I posted? There seemed to be some reasonable solutions there.

---

### Post by charonred on 2010-07-25
geoffjay - thanks, I'll try that later today (it's not quite 6am here, couldn't sleep since 3am). The one from Tom's hardware is for Win7 machines not accessing Linux; that's not the problem I have; my Ubuntu can't mount the Win7 boxes - Win7 can mount each other, XP & Lucid,but not the other way round ??? (usually Linux machines can mount anything)

I'll look at other solution a little later today too.

---

### Post by Morbius1 on 2010-07-25
You never mentioned if a simple:
```
nautilus smb://192.168.0100
```[COLOR=Blue]*Changing 192.168.0.100 to the ip address of the Win7 machine.*[/COLOR]
in a terminal was able to access the Win7 machine.

If you can get your router to set static ip addresses to all your machines you could even just bookmark them in Nautilus so they show up just like a "mapped drive " does in Windows.

---

### Post by charonred on 2010-07-25
tried multiple variations on solution at randyjensenonline, but nothing worked ...

---

### Post by charonred on 2010-07-25
Morbius1
well damn that worked, will the link on the desktop remain, or do I have to do something else?

---

### Post by Morbius1 on 2010-07-25
The Mount Icon on the desktop will go away when you reboot or unmount the share.

When you have smb://192.168.0.100 in nautilus select: Bookmarks > Add Bookmark.

You will notice that on the left vertical panel you will now have an entry titled ( if I remember correctly ) something like "share_name on Server_name"
[COLOR=Blue]EDIT: Actually I think it will say " Windows shares on server_name". It will say that even if the remote box is running linux but ...[/COLOR]

If you now unmount it and then click on the bookmark again it will remount it. The next time you reboot, open Nautilus, click on the bookmark, and you'll mount it. Looks just like a "mapped drive" does in windows.

[COLOR=Blue]EDIT: You can even automount on boot using this "gvfs" method[/COLOR]: [http://ubuntuforums.org/showthread.php?t=1186877](http://ubuntuforums.org/showthread.php?t=1186877)

---

### Post by fbobraga on 2010-07-25
It's very strange, but a issue like yours (*list Win7 shares from Ubuntu*) stopped occurring here with the ***ntfs-config*** package installed (and not even using the tool :P): ```
sudo apt-get install ntfs-config
```

---

### Post by charonred on 2010-07-25
Morbius1
Done that now, very cool  ..thanks

now to get Asus Notebook accessible, strange thing there, I can't get it to reserve the address in Router - invalid MAC address, but it's not .. might try flushing the notebooks wireless IP and get a new one cause it using the start IP for DHCP.

---

### Post by charonred on 2010-07-25
fbobraga
ok, installed that, but now what do I do, it doesn't appear to have changed anything, even after rebooting PC

---

### Post by Morbius1 on 2010-07-26
ntfs-cong ( which, not that you've asked, but is something I do not recommend using ;) ) is a utility to create permanent mount points for partitions formatted in ntfs connected to your local linux system and has nothing to do with accessing a remote share.

For all we know you don't have any ntfs partitions on your local Linux System anyway.

---

### Post by charonred on 2010-07-26
I don't have any drives partitioned for  multiple OS's or file systems - I have several drives in each PC box; if a drive has a OS on it, then it is the sole OS on that drive, or the sole file system.

And when I install an OS to a drive, I physically disconnect all other drives in that PC whilst installing the new  OS. Once installed I reconnect other drives and simply use F12 to select the drive & OS I want if not booting the default drive and OS - each drive is then completely separate from the others, and not dependent on having all installed drives present; with all the correct MBRs with GRUB, NTLDR etc jumble on them.

---

### Post by sinner99 on 2010-08-25
as suggested before the windows live sign in assistant on win7 will keep you from browsing that win7 box from ubuntu.remove it, windows live messenger will still function. there are also the settings in the network sharing center you must set, passwords, yes, the 128 bit encryption yes. secure things in the private 'domain' and it tends to work. the other settings are much more intense in gpedit.msc. you shouldnt need to do that. another note whenever you run the command sudo service smbd stop always include its partner in crime nmbd. in otherwords run it all at once in one command to restart the two service daemons: sudo service smbd stop && sudo service nmbd stop && sudo service smbd start && sudo service nmbd start
I could be incorrect, but I do believe smbd must be first in both stopping and starting. 

hope that helps someone, it took me a long ways at the start for me. in windows 7 when you are sharing, you must set permissions, of course and because you arent on a real AD domain, you need to set full control or read/write as you need for the user 'Everyone'. you will not access your shares until you do that. windows also has a security tab 'the second layer of sharing permissions' setting the necessary permissions for the same user 'everyone' is a necessity. (you cannot import the ubuntu users to the windows box, this is what domain servers do)

---

