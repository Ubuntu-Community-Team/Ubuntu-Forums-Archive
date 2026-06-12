---
title: "browsing windows shared folders via smb"
date: 2009-08-20
forum: General Help
---

### Post by silverrope on 2009-08-20
I followed two Howto's in the attempt to browse windows shares:
[http://ubuntuforums.org/showthread.php?t=525736](http://ubuntuforums.org/showthread.php?t=525736) and
[http://ubuntuforums.org/showthread.php?t=304131](http://ubuntuforums.org/showthread.php?t=304131)

Both mentioned to give yourself the User Privilege "Allow use of fuse file systems..." or something like that. On my fuse installation, the privilege appears as "Mount user-space file systems (FUSE)". Anyway I gave myself and root this privilege.

I created the directory where my shares will be mounted with the proper permission and group settings:
```

user@user-laptop:/media$ ls -ld network
drwxrwxrwx 2 user fuse 4096 2009-08-18 17:45 network

```However, when I run fusesmb, the permission and group setting changes.  But the mount did not seem to work. There is nothing in the network directory.
```

user@user-laptop:/media$ fusesmb /media/network
user@user-laptop:/media$ ls -ld network
drwxr-xr-x 3 user user 4096 2009-08-20 14:26 network

```When I kill the fusesmb process, the permission and group reverts back to the original settings.

Does anyone have a clue on how to get fusesmb to work?


**Adding a simpler question**: Whether I get fusesmb to work or not, how does one normally access the windows shared folders in xubuntu? I recall in ubuntu, it was easy to access the shared folders (nautilus?), but it is not clear how to do this in xubuntu.

---

### Post by silverrope on 2009-08-21
Uh, ok, I got a simpler question. I can print on my Windows shared printers from my xubuntu laptop. Now how do I get to my Windows shared folders?

Anyone?

---

### Post by rbc on 2009-08-21
Xubuntu's file manager, Thunar, does not have the capability to browse network shares. You could install and try pyneighborhood, although I have never been able to get it to work (probably operator error). The workarounds that I have done is either install Konqueror, Kubuntu's file manager, or download and run gnome-desktop-environment. The downside for Konqeror is that you get updates for a bunch of Kubuntu related stuff. Same deal with gnome-desktop. Additionally Ubuntu's desktop is obviously heavier than xfce, and slower, and kinda defeats the purpose of using Xubuntu. Others may have better ideas, and by the way, if pyneighborhood works for you, please let me know what you did

---

### Post by silverrope on 2009-08-22
> **rbc said:**
> by the way, if pyneighborhood works for you, please let me know what you did

I managed to get pyNeighborhood working. I followed the instructions off of this website.
[http://idyllictux.wordpress.com/2009/06/05/network-browsing-with-pyneighborhood-in-xubuntu-jaunty/](http://idyllictux.wordpress.com/2009/06/05/network-browsing-with-pyneighborhood-in-xubuntu-jaunty/)

I first edited preferences. Anonymous logins did not work (I assumed this was the Guest login under Windows). I put in the administrator username/password on my second try (not secure I know, but this was a test). In the Network tab, I checked the checkbox to try to retrieve IP address.

On the left panel under Groups, I left-clicked and I scanned under msbrowse. It found the WORKGROUP, then I left-clicked and scanned that to get a list of all my shares (on several computers). I picked the server that I was interested in. When I left-clicked and added it, a dialog box appeared. Here, I tried to retrieve the IP data but it failed. So I went to my windows machine, did a ipconfig to get the address and put it in manually. The server then appeared on the right panel and I left-clicked and scanned to get to the shares. I pick the folder and finally left-clicked to mount it.

This worked but it is not a real solution because all this has to be redone every time I login. Also, my windows machine will be assigned a random IP address on reboot which requires me to run ipconfig and manually put in the IP address again.

I also checked out
[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)
but this also requires manually putting in the IP address (in fstab) on every windows reboot.

Looks like xubuntu is not useful in an environment with windows shares.

---

### Post by rbc on 2009-08-22
Well, thanks to that link you provided, I was able to get pyneighborhood to connect to another Ubuntu computer just fine. It will now show me the Windows shares, but they are blank when opened, but I made a little progress. Thanks for the reply, and I wish you luck in your quest

---

### Post by silverrope on 2009-08-24
I finally got my windows shared folders permanently mounted. In order to avoid the manual input of IP addresses, I installed winbind for hostname resolution. As my folders are now available on login, I put a shortcut to my shares in Thunar. I can almost say that now the xubuntu laptop is as good as my machines running Windows. I have de-installed fusesmb and pyneighborhood.

If anyone is interested, I could write a How-To on this. I am surprised this hasn't been done already.

---

### Post by cjff1963 on 2009-08-26
> **silverrope said:**
> I finally got my windows shared folders permanently mounted. In order to avoid the manual input of IP addresses, I installed winbind for hostname resolution. As my folders are now available on login, I put a shortcut to my shares in Thunar. I can almost say that now the xubuntu laptop is as good as my machines running Windows. I have de-installed fusesmb and pyneighborhood.

If anyone is interested, I could write a How-To on this. I am surprised this hasn't been done already.

I will be more than interested in looking into your " how-to"  document. Thanks a lot.

---

