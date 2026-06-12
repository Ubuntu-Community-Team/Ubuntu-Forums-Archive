---
title: "how do i dual boot karmic and xp(karmic installed)"
date: 2010-01-21
forum: General Help
---

### Post by mastodon88 on 2010-01-21
(new to linux)
can someone point me to the right direction or give me step by step on how to do this? 
thx

---

### Post by quixote on 2010-01-23
This is just a matter of installing grub.  Karmic uses Grub2, which I'm not that up on.  It's late where I am, but I'll look it up tomorrow and get back on to give you particulars.  Or maybe somebody else will have already done it by then. :)

---

### Post by sailorboy on 2010-01-23
There is likely a better thread this should be under but believe that it's easier to to install Ubuntu after the XP install if you wish them to share same hard drive.
 Myself, (on a dell 4700)- I just added an IDE HD for ubuntu and left the original SATA to carry XP. This box has only one IDE channel and I believe the ubuntu HD is actually the slave (recalled my DVD burner instructions requested that it be used as a master).
 I rarely boot to XP- no real need.
 Believe the ubuntu live cd allows easier dual boot on same HD options, but expects the other OS to be in (and defraged fully) first.

---

### Post by JiuJitsu500 on 2010-01-23
I reccomend VirtualBox... not the OSE version.... downloaded from [URL="http://www.virtualbox.org"]VirtualBox.org
[/URL]
Dual Booting is great, but Virtualization is the way to go, especially on any computer with 1GB of RAM or more. Setting up can be painful, but there will not be Grub problems or the bigger pains involved sometimes in dual-booting... And you can use the host OS and the guest at the same time. If you choose, you can have 3 or 4 OS's going provided enough RAM set for them all to work, and enough left over to handle the job of something so.... insane :)

---

### Post by d3v1150m471c on 2010-01-23
> **JiuJitsu500 said:**
> I reccomend VirtualBox... not the OSE version.... downloaded from [VirtualBox.org]("http://www.virtualbox.org")

Personally, I abhor windows but running xp out of virtualbox is not such a bad idea. Granted you may have trouble with onboard microphones. (I had this issue). Other than that it worked fine, seemingly better than running it by itself. You'll avoid the dual-boot complications that people run into with grubs and partitions and it's nice if you write multiplatform software and want to test it.

---

### Post by quixote on 2010-01-23
If I understand it, you already have XP and karmic installed and would like to do something now to be able to boot either one.  

If you already have karmic and would like to install XP, then the other commenters who are suggesting Virtualbox are exactly right.  XP runs perfectly under vbox, but you don't have anywhere near the virus worries that you'd have with a "real" install.  Also, as they say, get the Sun version.  The ose version in synaptic doesn't have good USB support yet.  The only disadvantage to a virtual install is that you have to go through the bother of sharing folders that are outside the virtual machine if you want them available to your vbox XP.  (You only have to do that once.)

If you install karmic *after* XP, there's no problem.  Grub2 will find the Windows install and make an entry for it automatically.  You don't need to do anything.

How to get grub2 to see a Windows install after the fact is covered in good detail under [#13, Recovering Grub2 using LiveCD, in Grub2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275").  

If that's still not seeing the Windows partition, you may also need to add an entry for it in the 40_custom file in the /etc/grub.d/ directory.  There are some [good examples in this post]("http://ubuntuforums.org/showthread.php?p=8191211#post8191211"), page down a couple of screens' worth. (The italic bits are just comments.  Do not include them in the actual 40_custom file!)  The usual format for a Windows entry is something like: 

[COLOR="Red"]*[Edit: this code is wrong, see next comment]*[/COLOR]
```
menuentry "WinXP" {
        set root=(hd0,1)  *[that's the first drive (0), first partition (1).  **Alter to fit your setup**.]*
        makeactive
        chainloader	+1
}
``` I'm not at all sure about the last two lines.  You'd need to find another example to check that.  The title for the entry, the bit between quotes after "menuentry", can be anything you want.

After you change anything on Grub2, like edit the 40_custom file, run ```
sudo update-grub
```

---

### Post by Leppie on 2010-01-23
> **quixote said:**
> The usual format for a Windows entry is something like:
```
title  WinXP     *[can be anything you want]*
root   (hd0,1)   *[that's the first drive (0), first partition (1).  **Alter to fit your setup**.]*
makeactive
chainloader    +1
```
this is a grub legacy menu entry.
in grub2 it should look something like this:
```
menuentry "Microsoft Windows XP (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set #################
    chainloader +1
}
```

---

