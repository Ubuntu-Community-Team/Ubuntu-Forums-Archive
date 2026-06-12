---
title: "Access Ubuntu files in Windows (hidden partition)"
date: 2009-07-05
forum: General Help
---

### Post by SPARTAN-118 on 2009-07-05
Hi, I use my files A LOT, whether it be in Windows or Ubuntu (9.04 Jaunty Jackalope).

I usually only use my Windows for either playing commercial games (which, by the way, usually doesn't work, since my graphics card/CPU is _**CRAPPY**_). 
However, I recently have been downloading songs off of Limewire (.deb package - not via WINE!) and am having issues with transferring them to my iPod. I know there are some great programs out there that allow you to do this, but for some reason, Ubuntu's not recognizing my iPod. Also, I can't find any [good] programs for transferring videos to iPod, so Ubuntu's not serving my needs.

Therefore, I need to be able to access my [music, videos, pictures, etc.] on my Ubuntu from Windows. I have tried two programs recommended by Ubuntu Geek:


[LIST]
[*]Linux Reader by DiskInternals Research, and
[*]Ext2 IFS (also compatible with Ext3 partitions) by Stephen Schreiber.
[/LIST]
However, I installed Ubuntu via Wubi, and neither of these programs access my (hidden?) partition. (Well, I'm not so sure about Ext2 IFS; it DID show SOME files on Ubuntu, but it was only a few songs in my Music folder: the drive was labeled "O" and the folder was located in Users -> Matthew -> Music -> O, and didn't even contain all my music, only a few songs by the Offspring.)

Any ideas? Oh, and I'm running Windows Vista, and the Ubuntu [working] directory is C:\ubuntu\disks (which, BTW, only contains .disk files, not folders, like I thought it would), as displayed by [GRUB?] when my computer starts up and I select Ubuntu.

---

### Post by Woody1987 on 2009-07-06
what i do is have windows installed in virtualbox and share my ubuntu music folder with it. From within virtualbox XP i can then update my ipod.

---

### Post by blueridgedog on 2009-07-06
I don't know a thing about wubi so I can't offer much help, but can you tell me what model of iPod you have?  All but the latest iPod Touch are well supported (I use floola).

---

### Post by ugm6hr on 2009-07-06
Those ext2/3 reasing utilities won't work.

Wubi installs Ubuntu in a non-Linux partition (i.e. NTFS).

I have no idea if it is possible to access the files from Windows...

---

### Post by blueridgedog on 2009-07-06
> **ugm6hr said:**
> Those ext2/3 reasing utilities won't work.

Wubi installs Ubuntu in a non-Linux partition (i.e. NTFS).

I have no idea if it is possible to access the files from Windows...

Is Wubi performance substantially better than a liveCD image on a USB stick?

---

### Post by irv on 2009-07-06
What woody mentioned was a great idea. The last couple of days I downloaded virtualbox 3.0, and installed WinXP under virtualbox. Setup a shared folder and I can do my windows thing and see the files in Ubuntu. And the best part I can do all this and never leave Ubuntu. Your ipod will work the way you want and you will have the best of both world without rebooting you pc.
Here is the link to the Virtualization under Ubuntu forum.
[http://ubuntuforums.org/forumdisplay.php?f=308]("http://ubuntuforums.org/forumdisplay.php?f=308")
Check out some of the post and maybe you will get the idea how this work.
I have two windows programs I need to run and this allows me to do this. I love the idea.

---

### Post by ugm6hr on 2009-07-07
> **blueridgedog said:**
> Is Wubi performance substantially better than a liveCD image on a USB stick?

Yes.

A LiveUSB is compressed; a wubi install is not.  Additionally, even USB2 is not as fast as SATA or IDE HDs.

---

### Post by irv on 2009-07-07
Another way to share files is to use Ubuntu One. It works because I have use it. You need a fast Internet connection because you are uploading files to a Internet server and then downloading them on to your windows machine.

---

### Post by SPARTAN-118 on 2009-07-09
Unfortunately, I do not have the hardware capacity required to run a Virtual OS.

However, I do use Dropbox, which is similar to Ubuntu One.

What sizes does Ubuntu One have?
Because Dropbox's 2GB isn't large enough for me, and I'm not upgrading;
also, it continuously tries to upload the files to the server, though it should have been done A LONG time ago.

Plus, I don't have that much hard drive space left, and I can't buy an External Hard Drive as of this moment.

Thanks,
SPARTAN-118

---

### Post by irv on 2009-07-09
> **SPARTAN-118 said:**
> Unfortunately, I do not have the hardware capacity required to run a Virtual OS.

However, I do use Dropbox, which is similar to Ubuntu One.

What sizes does Ubuntu One have?
Because Dropbox's 2GB isn't large enough for me, and I'm not upgrading;
also, it continuously tries to upload the files to the server, though it should have been done A LONG time ago.

Plus, I don't have that much hard drive space left, and I can't buy an External Hard Drive as of this moment.

Thanks,
SPARTAN-118

Ubuntu One has 2GB also. You can buy more. Another thing I did a few years ago was buy a external HD case and put a old hard drive in it until I could afford a bigger one, and then I bought a 250GB drive. The price of drives are coming down. About 6 months ago I bought a 1TB external drive for $119. The only complaint I have is it is half full and it takes about 4 or 5 minutes to read all the files in it when I plug it in to the USB port. Because of that I leave it plugged in all the time. It runs very warm so it must be using a lot of power. 
There's getting to be so many old PC's around if you watch rummage sales etc, you might pick one up for next to nothing and use it for a file server, that might be an option also.

---

### Post by SPARTAN-118 on 2009-07-09
> **irv said:**
> Ubuntu One has 2GB also. You can buy more. Another thing I did a few years ago was buy a external HD case and put a old hard drive in it until I could afford a bigger one, and then I bought a 250GB drive. The price of drives are coming down. About 6 months ago I bought a 1TB external drive for $119. The only complaint I have is it is half full and it takes about 4 or 5 minutes to read all the files in it when I plug it in to the USB port. Because of that I leave it plugged in all the time. It runs very warm so it must be using a lot of power. 
There's getting to be so many old PC's around if you watch rummage sales etc, you might pick one up for next to nothing and use it for a file server, that might be an option also.

I don't even know HOW to set up a server, nor do I think I want to learn how to...

I guess I'll try using Dropbox/Ubuntu One, and not keep all the files in it, just the ones I want to access right away, like my most recent music, etc.

Can you have an Ubuntu One account AND Dropbox account set up at the same time?
Or would that take up too much Bandwidth?

SPARTAN-118

PS: Why aren't the :confused: smilies right on the right sidebar? 
Can you add smilies to that sidebar? That'd be really usefull for [most] of my threads.

PSS: (or is it PPS?): Firefox's dictionary sucks.

---

### Post by ugm6hr on 2009-07-10
> **SPARTAN-118 said:**
> I don't even know HOW to set up a server, nor do I think I want to learn how to...

It is actually very easy with FreeNAS - check my link below.

If you want to be able to access your files from within your LAN (local / home network), it is very, very simple to enable that.

You can then gradually add additional features as required.  No real learning required!

I installed mine in a redundant computer (that I got free).

---

### Post by irv on 2009-07-10
> **SPARTAN-118 said:**
> I don't even know HOW to set up a server, nor do I think I want to learn how to...

I guess I'll try using Dropbox/Ubuntu One, and not keep all the files in it, just the ones I want to access right away, like my most recent music, etc.

Can you have an Ubuntu One account AND Dropbox account set up at the same time?
Or would that take up too much Bandwidth?

SPARTAN-118

PS: Why aren't the :confused: smilies right on the right sidebar? 
Can you add smilies to that sidebar? That'd be really usefull for [most] of my threads.

PSS: (or is it PPS?): Firefox's dictionary sucks.

Don't be afraid to setup a server. It it just Ubuntu loaded on another PC with samba for file sharing. All you need to do is:

1. First you will have to install samba

    ```
sudo apt-get install samba
```

2. After installing, edit the smb.conf ( /etc/samba/smb.conf )

    ```
sudo gedit /etc/samba/smb.conf
```

What to Change?

    > * Change Workgroup to your home network. Save.
    * Now Right click the folder that you want to share and choose sharing options.
    * The option windows will appear and give a check to share this folder and guest access.

3. Restart Samba

    ```
sudo /etc/init.d/samba restart
```

Test your home network using another PC.
If you are using window just go to your workgroup under networks and you can access all your files.
It is just that simple.

---

### Post by SPARTAN-118 on 2009-07-10
Thanks, though I don't feel like getting another computer just yet (even if it is just for Samba!).

For now, I'll just use Dropbox/Ubuntu One, maybe use both so I get double the size?

---

### Post by nakul777 on 2010-09-08
i have dell inspiron laptop, i tried installing all the software mentioned here. machine runs on vista home basic. but none of them worked in any way...
Someone is not reading the ext2 file system while the others are not opening the files system being shown(ext2)...

---

