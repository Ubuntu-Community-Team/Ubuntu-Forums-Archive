---
title: "Share Files XP -&gt; Ubuntu"
date: 2009-07-19
forum: General Help
---

### Post by solar wind on 2009-07-19
Hi everybody, I am new here.  I am trying to transfer audio and video files from my Windows XP desktop to my Ubuntu laptop, using a router.  I am in Ubuntu at Places > Network -- and there is an icon for Windows Network.  I right click on it and select Open, but get a warning message saying "Unable to mount location."  I would rather not have to burn all the files to a lot of CDs and then load the CDs into the laptop.  How can I use the laptop to copy files from the PC desktop?  Thanks for any help.

---

### Post by ugm6hr on 2009-07-19
In simple terms (assuming on same network):

1. Share the folder with your files from Windows.
From XP File Manager, Right-click folder, select Properties
Select radio button for sharing.
Type **xpshare** in share name (or something with no spaces, all lower case)

2. Find out IP address of XP computer.
From XP, Click the networking icon in System Tray (bottom right) and select Support tab.
Read and record IP address (e.g. **192.168.0.2** in example below)

3. Access share from Ubuntu
From Ubuntu, open Nautilus (File browser)
Change nautlus view to allow text entry of location (at work with Windows, so can't remember how to do this, but I think there is a button to click between the directory pane and the location)
Enter location as **smb://192.168.0.2/xpshare**
You should now have read access to the directory you have shared

---

### Post by solar wind on 2009-07-24
> **ugm6hr said:**
> 
...Change nautlus view to allow text entry of location 
I couldn't figure out how to do this.  Any more specific guidance?  Thanks.

---

### Post by ugm6hr on 2009-07-24
> **solar wind said:**
> I couldn't figure out how to do this.  Any more specific guidance?  Thanks.

To the left of the file location, there is a button that looks like a page of text.

It says, "Toggle between button and text location" - click it.

---

### Post by solar wind on 2009-08-02
OK, thanks.  I tried that and got as far as being able to see the icon for the XP machine, but when I try opening the icon I keep getting a message about being unable to mount.  I am suspecting that the XP machine or router has some anti-intrusion program or settings running - except that usually I would get a pop-up message asking if I wanted to grant permission.  There has been no such request from the XP, so I cannot figure out what is blocking access.  :(

---

### Post by Upkeep on 2009-08-02
Hi, I'm a bit of a Linux newbie, but I recently sorted out a similar problem accessing files on my XP machine.  I'm running Ubuntu 8.10 on an HP2133, but this may turn out to be the same thing on Jaunty.  I think it's the Linux firewall blocking incoming connections.

From System>Administration>Synaptic Package Manager I installed Firestarter and Samba.  Having done that, in terminal, I used sudo gedit smb.conf to edit my Samba config file according to swerdna's instructions in this thread

[http://ubuntuforums.org/showthread.php?t=1184279&highlight=windows+workgroup+share](http://ubuntuforums.org/showthread.php?t=1184279&highlight=windows+workgroup+share)

My XP workgroup is the standard MSHOME and my netbios, the name of my Ubuntu laptop is ian-laptop.  Once that was set up, I disconnected my router from the internet and using Firestarter, I turned off the firewall and from Places>Network I had a crack at opening MSHOME and bingo - there were my shared files.  On the policy tab of Firestarter I added a new inbound traffic policy rule to allow Service: Samba Port: 137-139 445 and selected the "anyone" source.  It didn't quite work out until I checked active connections, copied the ip address associated with my active samba connection and added another incoming policy to allow connections from that ip address.  Then I could turn the firewall back on and re-connect the router to the internet.

It seems a little wobbly from time to time, but by and large it seems to work now.  Sorry my post is a bit waffly - but that's what I'm like!

Hope it works!
Upkeep

---

