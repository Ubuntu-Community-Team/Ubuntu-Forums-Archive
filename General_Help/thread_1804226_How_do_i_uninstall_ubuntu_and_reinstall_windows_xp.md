---
title: "How do i uninstall ubuntu and reinstall windows xp?"
date: 2011-07-14
forum: General Help
---

### Post by kidhudi on 2011-07-14
i was really excited to try ubuntu and to tell you the truth i love it. but it is just way too slow. i installed it on my old pc dell dimension xps t700r. i figured it should be ok because win xp worked good on it. but i installed ubuntu and it absolutely crawls compared to XP. unless i did something wrong.now when i put my xp setup cd in the CD it won't recognize the disk format. any help would be appreciated.thanks

---

### Post by coffeecat on 2011-07-14
Hi. Welcome to the forum.

The Windows install CD should recognise the Linux partitions but be confused by the filesystems on them. It should be possible to delete all the partitions on the hard drive in the XP installer and then create as many partitions as you want for Windows. From there you should be able to continue with the Windows installation.

But if, for some reason, that is not possible, do you still have an Ubuntu live CD? Boot up with it and open Gparted. You can find that under System -> Adminstration in the classic gnome desktop. Right-click on the swap partition and choose "swapoff" and then delete all the partitions. Remember to click on "Apply". You can now create your NTFS partition(s) for Windows with Gparted if you want. The XP installer will recognise them and use them. Or shut down from the live Ubuntu CD and boot up the XP CD which should now be happy to create your NTFS partitions in the blank HD.

I'm surprised that Ubuntu ran slower than Windows. That is most unusual. What is the specification of your Dell Dimension, and which version of Ubuntu were you trying to run on it?

---

### Post by flipper T on 2011-07-14
i assume that you have set your bios to boot from the cd ?

---

### Post by MARP1961 on 2011-07-14
If you have wiped Windows off your hard drive completely, you will need an installation CD for your version of Windows XP. Windows installation disks are bootable and it sounds as if you just inserted it into the CD drive when Ubuntu was already booted. 

Your computer BIOS might already be set up to boot from CD. Try inserting the CD **before** booting the computer. You might need to shut down with the Windows disk in the tray/slot. When you power up again, your computer will hopefully boot from the Windows disk. If this happens you just need to follow Windows instructions to format the disk and install.

On some computers you need to quickly press something like F12 to boot from CD drive as you power up. You might need to alter the boot order by going into the BIOS menu. This is harmless and reversible if you know what you are doing.

---

### Post by kidhudi on 2011-07-14
thanks for all the tips guys. i will try it tonight.i think the problem is the ati rage 128 pro graphics card is too old or unsupported. and it it slowing it down a bit too much.anyway the setup is a Dell Dimension XPS t700r tower with :Pentuim 3 700 mhz processor3Com Network ethernet cardCreative Labs Soundblaster sound card Audio PCI ATI Rage Pro 128 from the AGPi figured it would be enough to handle the OS because XP ran pretty good and i read that ubuntu ran smoother than windows.
I'm surprised that Ubuntu ran slower than Windows. That is most unusual. What is the specification of your Dell Dimension, and which version of Ubuntu were you trying to run on it?[/QUOTE]

---

### Post by coffeecat on 2011-07-14
> **kidhudi said:**
> thanks for all the tips guys. i will try it tonight.i think the problem is the ati rage 128 pro graphics card is too old or unsupported. and it it slowing it down a bit too much.anyway the setup is a Dell Dimension XPS t700r tower with :Pentuim 3 700 mhz processor3Com Network ethernet cardCreative Labs Soundblaster sound card Audio PCI ATI Rage Pro 128 from the AGPi figured it would be enough to handle the OS because XP ran pretty good and i read that ubuntu ran smoother than windows.

You don't give us one of the most important bits of information - the amount of RAM. My guess is that you've only got about 256MB RAM in that machine. Ubuntu is a little more memory hungry than Windows XP. Windows XP will (just about) run in 256MB, but Ubuntu will be severely hampered. Up the RAM to 512MB and Ubuntu will leave Windows standing.

---

### Post by kidhudi on 2011-07-14
i have 384 ( dont ask me how) i think i bought it with 256 and found one in another junk machine and put it in ther. i will do as you say and but some more ram and give it another try.I really loved what i saw with ubuntu and will definately be using it in the near future. thanks bro

---

### Post by pqwoerituytrueiwoq on 2011-07-14
you can always use xubuntu
[http://www.xubuntu.org/get#lucid](http://www.xubuntu.org/get#lucid)

[http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/10.04/release/xubuntu-10.04.2-desktop-i386.iso.torrent](http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/10.04/release/xubuntu-10.04.2-desktop-i386.iso.torrent)

---

### Post by leclerc65 on 2011-07-14
Try Lubuntu 10.04 or one of the Lupu (Puppy) like 520, 525.

---

### Post by kidhudi on 2011-07-14
what is xubuntu? i never heard of it. i am new to this stuff. i have been a windows man my whole life ( after the commedor 64 (sp?) :) thanks for the tip i will research this for sure. i am reluctantly going back to windows on this machine.if this can prevent that from happening i am game. :)

---

### Post by linuxuser12345 on 2011-07-14
If your computer is *that* old, now is the time to buy a new one. Prices for new electronic parts are cheaper than ever, and keep getting cheaper. I would recommend buying the parts yourself to build a new one with. I recommend going on [www.newegg.com](www.newegg.com) for that.
The basic things you need for a new computer are:
1) A motherboard
2) A matching processor
3) Matching memory (RAM)
4) A hard drive
5) A case
6) [and for most people] A CD/DVD burner

If you decide to do this, just ask us for help anytime! Computers are *very* simple to set up if you have the instruction map that comes with the motherboard. Just connect all the matching plugs to the right sockets as expressed in the map.

---

### Post by linuxuser12345 on 2011-07-14
What do you use your computer for? What do you *want* to use it for?

---

### Post by pqwoerituytrueiwoq on 2011-07-14
if you want to upgrade on a budget you can reuse some stuff int the computer
eg case dvd drives hard drive
[]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813138179")
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813130235R](http://www.newegg.com/Product/Product.aspx?Item=N82E16813130235R)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103896](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103896)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820148338](http://www.newegg.com/Product/Product.aspx?Item=N82E16820148338)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817182006](http://www.newegg.com/Product/Product.aspx?Item=N82E16817182006)

that would be everything you would need for a rather nice upgrade for under 150 USD

i looked up your system it appeared to be a atx case

---

### Post by linuxuser12345 on 2011-07-14
If his/her computer is that old, the hard drive and CD/DVD burner probably won't work on the new system.

---

### Post by pqwoerituytrueiwoq on 2011-07-14
> **linuxuser12345 said:**
> If his/her computer is that old, the hard drive and CD/DVD burner probably won't work on the new system.
old ide drives should work (not on newer intel broads which usually lack a port for a ribbon cable)
the drive wil be slow by todays standards but it will work none the less
i have used old ide drives from windows 98 systems in my phenom II quad core system
after one drive croaked i took the other out of service

---

### Post by kidhudi on 2011-07-16
thanks for requesting xubuntu it seems to be much smother and a lot quicker.

---

### Post by pritam_par on 2011-07-31
This is for windows 7 but work with XP also
[http://gordonburgessparker.wordpress.com/2009/11/06/windows-7-and-grub/](http://gordonburgessparker.wordpress.com/2009/11/06/windows-7-and-grub/)

---

