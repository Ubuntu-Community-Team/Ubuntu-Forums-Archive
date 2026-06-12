---
title: "How to create a link to my &quot;My Documents&quot; folder on my XP partition?"
date: 2010-04-14
forum: General Help
---

### Post by rtrinkner on 2010-04-14
Hello,

I've recently installed Ubuntu 9.10 Karmic as a dual boot with WinXP and love it.  I've been able to mount my WinXP partition and can access files read/write successfully.

I'd like my WinXP "My Documents"  folder to appear as a linked folder in my Linux Home directory.

I think I should be able to use the ln command, but I can't figure it out.

I've tried to create a link that will appear like a "folder" called WinDocs in my Home directory with this command, run from my Home folder:

**ln -t /dev/sda1/Documents\ and\ Settings/richard/My\ Documents/ /WinDocs/**

but it reports 

**ln: accessing `/dev/sda1/Documents and Settings/richard/My Documents/': Not a directory**

I get the same results if I try /dev/hda1 etc. 

I can see the contents of the folder currently in my Places listing.  Its shortcut is active on my desktop.

Sorry, but I'm a linux noob.  Am I completely off base here?

Thanks

---

### Post by akakingess on 2010-04-14
Have you tried just right-clicking on the folder and choosing 'Make Link'? Then, you could just cut/paste that 'link' wherever you would like. I think that should work, if not, please let us know, but if it does work, please remember to mark this thread as SOLVED. Good luck and happy learning!

---

### Post by Benchamoneh on 2010-04-14
/dev/sda1 is actually a file, not a folder. If you want to access the data on that partition you first need to mount the device (I'm going to guess you already know how to mount drives but if not just ask).

Once mounted you can create a link in your Documents directory with the following command - I've assumed you've mounted your Windows partition as /media/Windows in this example:

```
ln -s /media/Windows/Documents\ and\ Settings/richard/My\ Documents/ ~/Documents/WinDocs
```

---

### Post by JKyleOKC on 2010-04-14
> **rtrinkner said:**
> 

**ln -t /dev/sda1/Documents\ and\ Settings/richard/My\ Documents/ /WinDocs/**

but it reports 

**ln: accessing `/dev/sda1/Documents and Settings/richard/My Documents/': Not a directory**

Sorry, but I'm a linux noob.  Am I completely off base here?

ThanksNot completely, there's just an intermediate step that's necessary. In Linux, there's a distinction between a "device" and a "file" to the effect that the hardware is a device, and the data it contains is grouped into files of various sorts (including directories). You have to mount the device to a specific directory of your system, and then access the content through that directory.

Nautilus handles some of this for you behind the scenes and without your knowledge, which is handy for quick access but leads to wrong impressions as to what's required.

To mount the "My Documents" folder automatically at boot time, you can add a line to the /etc/fstab file -- but it's best to test the setting first by mounting from the command line. Begin by creating the folders you want to use, in your home directory:
```
mkdir .win
```
then issue the command
```
sudo mount $HOME/.win /dev/sda1 -t ntfs -o defaults,uid=1000,gid=1000
```
The $HOME expands to the full path of your home directory; the uid and gid values make you the owner of the device so that you can read from or write to the files on it. The 1000 is correct for the first user created at install time; additional users will have numbers incremented by one for each additional user.
if that works properly, you can now link with
```
ln -t $HOME/win/Documents\ and\ Settings/richard/My\ Documents WinDocs
```
and it should work until you reboot. To make it survive rebooting, do
```
gksu gedit /etc/fstab
```
and add this line to the bottom of the file:
```
$HOME/.win /dev/sda1 ntfs defaults,uid=1000,gid=1000 0 0
```
As you can see, this is almost the same as the command used in the test "sudo mount" action. The "0 0" on the end tells the boot code not to run disk tests when mounting.

---

### Post by rtrinkner on 2010-04-15
Well done!  Thanks: I now have a link to my Windows XP "My Documents"  folder appearing properly in my "Places"  in Ubuntu.  It persists when I restart.

Excellent advice.  Thanks again.

Richard

---

