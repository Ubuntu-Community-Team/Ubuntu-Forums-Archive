---
title: "Can't get Networking going"
date: 2009-09-23
forum: General Help
---

### Post by DrScum on 2009-09-23
Just switched from XP to Ubuntu on my laptop (completely, no dual boot) everything went smooth and painless except the Networking!

I have a home network based on wireless adapters controlled by a WLAN router. This network has Windows and Linux machines and works fine, I get internet access through the WLAN.

Now I want to connect my laptop through the ethernet card to a wired network consisting of only Linux machines. There is no need for the wired network seeing the WLAN network, I just want to share files and folders. 
How can I do this?

I had it set up this way when my Laptop, was running XP but so far I couldn't get it to work with the Laptop running Ubuntu 9.04. The other Linux stations are on Ubuntu 8.04 by the way.

So far I tried to use Samba and the Network manager. I am familiar with creating samba shares and I did all that.

The Ethernet card on the laptop is up and has a static IP assigend (ifconfig output). The same is true for the other members of the wired network. They can ping each other. The files I want to share appear as shared in the file manager, but they are invisible when I try to open Places>Network. All I see there is "Windows Network" when trying to open that I get: "Unable to mount location Failed to retrieve share list from server"

Help is appreciated, thanks

---

### Post by SteveDee on 2009-09-23
I have a similar setup, where each machine uses a 192.168.0.. series IP for WLAN and 200.1.1... series on 2 machines that share a wired link for faster file transfer.

The Nautilus "Network" shortcut uses my WLAN network because (presumably) this is the default interface controlled by Network Manager.

To use the wired link in Nautilus I type the remote machines (wired) IP address in the "Location:" box. Example: smb://200.1.1.2.

I can then bookmark this to create a more convenient short-cut.

I hope this helps.

Additional:-
Reading your post again, it looks like you also have a problem sharing files via your WLAN.
If it helps, on 9.04 I let the default "Network Manager" handle the WLAN interface. I then installed the old "gnome-network-admin" (as used on 8.04) so I could manually configure the wired (ethernet) network connection.

These 2 docs may help:-
[https://help.ubuntu.com/community/NetworkAdmin](https://help.ubuntu.com/community/NetworkAdmin)
[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)

---

### Post by DrScum on 2009-09-23
Thanks for the reply. Yes, I do have problems sharing files via the wired network. That seems to be a Samba problem. However, ever since I used Samba for the first time (which was about 12 years ago), it's always been a pain.

Now, where is this "Location Box" you are talking about? Nautilus is the default file manager on the GNU Desktop, I assume?

---

### Post by DrScum on 2009-09-23
In the meantime I found the location box under Go>location.

When I do as you suggested I get the message either "Couldn't find network:///<IP entered> or, when entering only IP : couldn't display <IPentered> Nautilus cannot handle this kind of connections.

However: when I use the ping command the machines can ping each other both ways, if I enter the IP and if I enter the hostname.

---

### Post by Iowan on 2009-09-23
[Here]("http://ubuntuforums.org/showthread.php?t=1169149") is a How-To page for Windows-sharing problems.
 [This]("https://help.ubuntu.com/8.10/internet/C/networking-shares.html") page is for sharing in 8.10.

---

### Post by SteveDee on 2009-09-24
> **DrScum said:**
> Thanks for the reply. Yes, I do have problems sharing files via the wired network. That seems to be a Samba problem. However, ever since I used Samba for the first time (which was about 12 years ago), it's always been a pain.

Now, where is this "Location Box" you are talking about? Nautilus is the default file manager on the GNU Desktop, I assume?

If you are using Ubuntu (not another flavor like Xubuntu which does not use Gnome) then Nautilus should be your default file manager, and the "Location:" box should be clearly visible. Its the text box that shows the current path and allows you to type a path directly. I think when you select Network, the location path will be: smb:/// but you must delete one of the "/" before typing an IP (e.g. smb://200.1.1.2 not smb:///200.1.1.2).

Network shares with 9.04 are usually very easy to setup. You normally only have to right click on the folder in Nautilus and select the share options. When you do this for the first time, the system will automatically download the necessary sharing service software (as long as you have an internet connection).

In addition to the links already mentioned, forum member Swerdna has created a very clear set of instructions here: [http://ubuntu.swerdna.org/ubulanprimer.html](http://ubuntu.swerdna.org/ubulanprimer.html)

A note on the: "Unable to mount location Failed to retrieve share list from server" message. I get this message if I try to access a network location soon after booting my computer. This can be misleading if you are network fault finding and continually rebooting, so ensure that both computers (local & remote) have been running for a few minutes before accessing the other via the network.

Workgroups: I keep reading comments that all computers must belong to the same workgroup. I think this must be out of date, recycled information. On my network I can see 2 workgroups and access computers that belong to either the "UBUNTU" workgroup or the "WORKGROUP" workgroup.

I hope some of this stuff helps.

---

### Post by DrScum on 2009-09-24
Thanks guys.

I did find the "location box" and did as suggested and did get this:"Error: Failed to mount Windows share
Please select another viewer and try again."

I am using Ubuntu 9.04 on the laptop and 8.04 on the desktop. 

When I had the Laptop under XP things worked exactly like Steve describes. You could access the shares only after a few minutes, I could see both networks available (the Windows one AND the linux one). However, with Ubuntu on the laptop I can't get this to work anymore.

---

### Post by DrScum on 2009-09-24
I seem to have arrived at the situation discribed by SteveDee above, i.e. when typing smb://<hostIP> a window opens asking for a password upon entering of which I have access to the shared folders.

The key settings change in my situation was to change the settings in Administration>Samba>Preferences>Security "Encrypt Passwords" to YES and "Guest Account" to No guest account.

Whether that's the default setting or whether I did change that before I can't retrace now since I have fiddled with this for a week now.

If I try to access the shares by any file manager (tried Nautilus and Gnome commander) I have no access getting the "failed to retrieve share list from server" message (even after waiting for a long time).

Well, I do set the thread to [solved] now but it kind of isn't. And I very much do hope that after rebooting this kind of acceptable situation holds up.

Got work to do now!

Thanks for all the help.

---

