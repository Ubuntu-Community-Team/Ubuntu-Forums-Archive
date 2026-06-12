---
title: "grub2  menu shows mac os x but........."
date: 2010-03-18
forum: General Help
---

### Post by bigsmitty64 on 2010-03-18
I have three  os's, ubuntu 9.10, win7, and Mac OS X Snow Leopard.

boot order in bios:

1:Ubuntu
2:Win7
3:Mac OS X Snow Leopard

Mac was last OS installed

All three show up in grub2 menu, but I can't boot the mac os, it just does nothing when clicked.

note: all three are on separate drives, and win7 and Ubuntu boot fine. Has anyone done this yet?  Successfully triple boot? I know I'm close! Any ideas are welcome. Thanks in advance,
Smitty

---

### Post by srs5694 on 2010-03-18
I'm pretty sure that the default GRUB 2 configuration for OS X is to attempt to run the OS X kernel directly. This works sometimes, but sometimes it doesn't. You may have better luck chain-loading the boot loader you presumably installed along with OS X (Chameleon, Boot Think, or whatever). To do this, you'd treat it much more like a Windows boot. I don't have a complete example handy right now, so I'll refrain from giving you one by memory, which might be flawed. Try copying your existing Windows entry, but change the partition IDs for OS X or the MBR on your OS X drive, if it's a separate physical disk.

Also, note that Ubuntu includes tools that automatically overwrite /boot/grub/grub.cfg whenever you upgrade your kernel. Thus, if you edit that file directly, be sure to keep a backup; you'll need to keep re-editing it. The better alternative is to edit the scripts that do the editing, in /etc/grub.d. You can add your entries to /etc/grub.d/40_custom, for instance.

If you have further problems, you may want to join a Hackintosh forum; people there are far more familiar with the intricacies of the OSx86 boot loaders than most people here.

---

### Post by pSYcl0Ne on 2011-05-09
I know it's an old post, but I'd really appreciate if anyone has figured out how to do this. Breaking my brain atm. This is really simple with grub-legacy.

---

### Post by lifelike27 on 2011-05-19
Yeah, I'm having problems too with this.

I've managed to install all three operating systems on one drive with OS X installed first. Grub2 detects it, but when I click of Mac OS X 32 bit or 64 bit, it shows nothing on the screen for a few seconds and then restarts and goes back to grub2...

---

### Post by Quackers on 2011-05-19
My OS X86 system boots directly from the grub menu without a problem (other than not being able to enter any boot options, as chameleon is not being used) so I made an entry in /etc/grub.d/40_custom like below, then ran sudo update-grub.
This entry now boots the chameleon bootloader.

Firstly you need to boot into the Linux system which has control of grub2.
It was then necessary for me to download a boot0 file (which is actually part of the chameleon bootloader on my system, but I couldn't find it :-) )

A copy can be downloaded here if required
wget [http://downloads.bodhilinux.com/jeff91/misc/boot0](http://downloads.bodhilinux.com/jeff91/misc/boot0)
though this site is nothing to do with me, I hasten to add!

Then run these terminal commands ```
sudo mkdir /boot/chameleon
cd /boot/chameleon
wget http://downloads.bodhilinux.com/jeff91/misc/boot0  # Only if required # 
```
Or, instead of the last line you can just copy your own boot0 file into that directory.

My menu entry
```
menuentry "Mac OS X Boot Loader" {
insmod hfsplus
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 870b3434-803f-3c62-b17b-5758b6e467
parttool (hd0,3) boot+
chainloader (hd1,6)/boot/chameleon/boot0
}
```

For explanation, where my entry uses (hd0,3) this is where my OS X86 system is installed (/dev/sda3) and the UUID in line 4 is the UUID of that partition.
Where the entry uses (hd1,6) it is referring to where I placed the /boot/chameleon folder (/dev/sdb6).
Obviously yours will be different and they will need changing!

Credit goes to a guy named Jeff Hoogland, whose blog page I followed - though I'm not sure I can link to it, due to code of conduct.

---

### Post by lifelike27 on 2011-05-19
> **Quackers said:**
> My OS X86 system boots directly from the grub menu without a problem (other than not being able to enter any boot options, as chameleon is not being used) so I made an entry in /etc/grub.d/40_custom like below, then ran sudo update-grub.
This entry now boots the chameleon bootloader.

Firstly you need to boot into the Linux system which has control of grub2.
It was then necessary for me to download a boot0 file (which is actually part of the chameleon bootloader on my system, but I couldn't find it :-) )

A copy can be downloaded here if required
wget [http://downloads.bodhilinux.com/jeff91/misc/boot0](http://downloads.bodhilinux.com/jeff91/misc/boot0)
though this site is nothing to do with me, I hasten to add!

Then run these terminal commands ```
sudo mkdir /boot/chameleon
cd /boot/chameleon
wget http://downloads.bodhilinux.com/jeff91/misc/boot0  # Only if required # 
```
Or, instead of the last line you can just copy your own boot0 file into that directory.

My menu entry
```
menuentry "Mac OS X Boot Loader" {
insmod hfsplus
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 870b3434-803f-3c62-b17b-5758b6e467
parttool (hd0,3) boot+
chainloader (hd1,6)/boot/chameleon/boot0
}
```

For explanation, where my entry uses (hd0,3) this is where my OS X86 system is installed (/dev/sda3) and the UUID in line 4 is the UUID of that partition.
Where the entry uses (hd1,6) it is referring to where I placed the /boot/chameleon folder (/dev/sdb6).
Obviously yours will be different and they will need changing!

Credit goes to a guy named Jeff Hoogland, whose blog page I followed - though I'm not sure I can link to it, due to code of conduct.

I'm not an expert in this, but is it implicitly required to add the UUID of the partition?

---

### Post by lifelike27 on 2011-05-19
I was hoping I could get OS X to boot using grub only.
i.e. without chain loading it with other boot loaders

---

### Post by Quackers on 2011-05-19
> **lifelike27 said:**
> I'm not an expert in this, but is it implicitly required to add the UUID of the partition?

I don't know, I just followed the guide :-)

With regard to your last post I don't know why it is not booting direct from the grub menu - mine does, though there are screen resolution problems when I use that method, due to not being able to use a boot option.

---

### Post by lifelike27 on 2011-05-19
> though there are screen resolution problems when I use that method, due to not being able to use a boot option.

I read on another forum/post that you can fix that if you add this to your OS X menu entry.
```
gfxpayload="1366x768-24"
```

Just replace 1366x768 for your screen resolution since that's my screen resolution.

---

### Post by Quackers on 2011-05-19
Yes you can fix it with an entry (but I think it's "Graphics Mode"="1920x1200" or whatever) but not if you can't get to chameleon first :-)  That was my problem when booting from grub.

EDIT  Actually I'm wrong there. I think you need to edit boot.plist once you're in there, if I remember correctly. It's a while since I did it.

---

### Post by lifelike27 on 2011-05-19
I might have done something wrong. The menu entry I made from following your instructions boots into my Windows partition instead. :P

Tomorrow morning I think I'm going to install Chameleon in the OS X partition and try to get grub to boot to that.

I'm not sure if that's what you were trying to get me to do though. Like I said, I'm not an expert. >_<

---

### Post by Quackers on 2011-05-19
It sounds like you used the Windows partition by mistake (in the (hd0,3) bit) or its UUID maybe.
Have a sleep and try again :-)

---

### Post by drs305 on 2011-05-19
lifelike27,

If it's the partition number, remember Grub2 counts the first drive as 0, and the first partition as 1. 

Example: sda3 = (hd0,3)

---

### Post by lifelike27 on 2011-05-19
I have this problem... 

I can never leave a problem unsolved. I'll stay awake thinking about it!

This is my menu entry for OS X, which you'll notice, is just an edited version of yours:
```
menuentry "Mac OS X Boot Loader" {
insmod hfsplus
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 067b0e6b-7c8d-39a1-804b-f3ee9dcc52b0
#parttool (hd0,4) boot+
chainloader (hd0,3)/boot/chameleon/boot0
}
```

I hashed out parttool because I get an error in grub saying that it can't identify boot+

Here's a screenshot of GParted since I can't use fdisk with a GUID Partition: [http://dl.dropbox.com/u/8515110/temp/-dev-sda%20-%20GParted_005.png](http://dl.dropbox.com/u/8515110/temp/-dev-sda%20-%20GParted_005.png)

Is the entry wrong?

---

### Post by lifelike27 on 2011-05-19
> **drs305 said:**
> lifelike27,

If it's the partition number, remember Grub2 counts the first drive as 0, and the first partition as 1. 

Example: sda3 = (hd0,3)

I have only one drive, so for me it's always hd0 and I understand that sda3 would be (hd0,3).

Thanks. :)

---

### Post by Quackers on 2011-05-19
Are you using GUID Partition table? I'm on MBR so there may be differences I don't know about.
The entries look ok, but I would imagine parttool needs to be uncommented. The error regarding boot+ I'm afraid I can't help with, as I just haven't experienced that. Sorry.

---

### Post by drs305 on 2011-05-19
> **lifelike27 said:**
> I have this problem... 

I can never leave a problem unsolved. I'll stay awake thinking about it!

This is my menu entry for OS X, which you'll notice, is just an edited version of yours:
```
menuentry "Mac OS X Boot Loader" {
insmod hfsplus
set root='(hd0,4)'
search --no-floppy --fs-uuid **--set[COLOR="Red"]=root[/COLOR]** 067b0e6b-7c8d-39a1-804b-f3ee9dcc52b0
#parttool (hd0,4) boot+
chainloader (hd0,3)/boot/chameleon/boot0
}
```

I hashed out parttool because I get an error in grub saying that it can't identify boot+

Here's a screenshot of GParted since I can't use fdisk with a GUID Partition: [http://dl.dropbox.com/u/8515110/temp/-dev-sda%20-%20GParted_005.png](http://dl.dropbox.com/u/8515110/temp/-dev-sda%20-%20GParted_005.png)

Is the entry wrong?

Grub 1.99 / Natty changed the search line a bit. The "--set" is now "**[COLOR="Red"]--set=root[/COLOR]**". Don't know if that will fix your menu, as I unfortunately know nothing about OSX. It's still '--set' in older versions.

---

### Post by Quackers on 2011-05-19
Thanks drs305, that may be an issue. I haven't booted into Mac for some time. Things could have changed.

---

### Post by lifelike27 on 2011-05-19
Thanks drs305. Though now I'm getting another error - cannot find device [my UUID]

I still get that same error as well that boot+ cannot be recognized when I uncomment it out. Then boots into Windows.

Tomorrow morning it is then!

---

### Post by Quackers on 2011-05-19
pm on the way to you.

---

### Post by drs305 on 2011-05-19
> **lifelike27 said:**
> Thanks drs305. Though now I'm getting another error - cannot find device [my UUID]

I still get that same error as well that boot+ cannot be recognized when I uncomment it out. Then boots into Windows.

Tomorrow morning it is then!

You might confirm you are running Grub 1.99, or try changing it back to "--set" to see if the UUID error goes away... You can see which Grub 2 you are using with "grub-install -v" or look at the top of the Grub menu when it boots. In any case, hope you can get this figured out.

---

### Post by lifelike27 on 2011-05-19
> **drs305 said:**
> You might confirm you are running Grub 1.99, or try changing it back to "--set" to see if the UUID error goes away... You can see which Grub 2 you are using with "grub-install -v" or look at the top of the Grub menu when it boots. In any case, hope you can get this figured out.


I am running grub 1.99 from a fresh install of 11.04 stable release.
```
jon@jon-ubuntu:~$ grub-install -v
grub-install (GRUB) 1.99~rc1-13ubuntu3

```

---

### Post by lifelike27 on 2011-05-26
> **Quackers said:**
> My OS X86 system boots directly from the grub menu without a problem (other than not being able to enter any boot options, as chameleon is not being used) so I made an entry in /etc/grub.d/40_custom like below, then ran sudo update-grub.
This entry now boots the chameleon bootloader.

Firstly you need to boot into the Linux system which has control of grub2.
It was then necessary for me to download a boot0 file (which is actually part of the chameleon bootloader on my system, but I couldn't find it :-) )

A copy can be downloaded here if required
wget [http://downloads.bodhilinux.com/jeff91/misc/boot0](http://downloads.bodhilinux.com/jeff91/misc/boot0)
though this site is nothing to do with me, I hasten to add!

Then run these terminal commands ```
sudo mkdir /boot/chameleon
cd /boot/chameleon
wget http://downloads.bodhilinux.com/jeff91/misc/boot0  # Only if required # 
```
Or, instead of the last line you can just copy your own boot0 file into that directory.

My menu entry
```
menuentry "Mac OS X Boot Loader" {
insmod hfsplus
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 870b3434-803f-3c62-b17b-5758b6e467
parttool (hd0,3) boot+
chainloader (hd1,6)/boot/chameleon/boot0
}
```

For explanation, where my entry uses (hd0,3) this is where my OS X86 system is installed (/dev/sda3) and the UUID in line 4 is the UUID of that partition.
Where the entry uses (hd1,6) it is referring to where I placed the /boot/chameleon folder (/dev/sdb6).
Obviously yours will be different and they will need changing!

Credit goes to a guy named Jeff Hoogland, whose blog page I followed - though I'm not sure I can link to it, due to code of conduct.

I was able to use Quackers guide to get OS X to chainload but with an edit to my menu entry.

```
menuentry "Mac OS X Boot Loader" {
insmod hfsplus
set root='(hd0,4)'
chainloader (hd0,3)/boot/chameleon/boot0
}
```

This works just fine!

My next problem is getting OS X to load after a combo update!

---

### Post by ptaramelli on 2012-01-04
> **lifelike27 said:**
> I was hoping I could get OS X to boot using grub only.
i.e. without chain loading it with other boot loaders

Hey!, it works!, the post is :[http://jeffhoogland.blogspot.com/2011/04/howto-chainload-grub2-into-chameleon.html]("http://jeffhoogland.blogspot.com/2011/04/howto-chainload-grub2-into-chameleon.html")

But I have some issues, for if it help, I here copy my comment in the blog:

Jeff: Thank you!!!!!!. Two days trying until I see your blog.

For if it helps to others, I changed the following:

Having win7 in sda1, ubuntu 11.10 in sda2, osx 10.6.8 in sdb2 and chameleon in sdb1. The code that i put in /etc/grub.d/40_custom so it could be write in /boot/grub/grub.cfg via sudo update-grub2 and works for me was this:

menuentry "Mac OS X Boot Loader" {
insmod part_gpt
insmod hfsplus
set root='(hd1,gpt2)'
search --no-floppy --fs-uuid --set=root b47b98437e42addb
# parttool (hd1,gpt2) boot+
chainloader (hd0,2)/boot/chameleon/boot0

I explain errors I've got until get this.
1-putting set xxxxxx instead of set root= xxxxx give me " ...no argument ...."
2- the line i commented (...parttool etc) give me boot +  was not recognize as command
3- the "insmod part_gpt" and '(hd1,gpt2)' etc for what i read has someting to do with gui partition of second drive (where osx is), I have before error that " ..no partition ..."
4- finally "file not found" was mine, stupid that I forget that I put your boot0 in my ext4 linux partition.I was chainloading to EFI (sdb1)

One more thing, the UUID i've got from sudo blkid was wrong, I had to copy the one in grub.cfg generated by grub2

Once more: thanks !!!!!!!!!!!!!!!!!

Pablo Taramelli [email]ptaramelli@gmail.com[/email]
Sorry, my english is terrible.....

---

### Post by lifelike27 on 2012-01-04
Yes, your entry is directed at the wrong partition. This should work:
```
menuentry "Mac OS X Boot Loader" {
insmod hfsplus
set root='(hd1,2)'
chainloader (hd1,1)/boot/chameleon/boot0
}
```

---

