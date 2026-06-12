---
title: "The disk drive for /whatever is not ready yet or not present - but I don't mind!"
date: 2010-06-23
forum: General Help
---

### Post by hymerman on 2010-06-23
I get this message at boot after upgrading to 9.10, but it's for an external hard drive that's not always turned on (I turn it on and sudo mount -a when I want it). I know about that, and don't care if it's not on - is there a way to disable this message? I've searched the forums and elsewhere and all I can find is a lot of people that are receiving the message in error, whereas here I know it's correct but I don't want it to be treated as an error!

Is the only way going to be to remove it from /etc/fstab and mount it manually when I want it? It's just that I like the convenience of not having to type out the mount point and UUID every time I want it mounted, and the ability to turn it on before I turn on the computer if I know I'm going to need it.

---

### Post by dabl on 2010-06-23
> **hymerman said:**
> 

Is the only way going to be to remove it from /etc/fstab and mount it manually when I want it? 

Yes.

Apparently, you had this drive connected and running when you installed Ubuntu.  So, it was detected and set up in /etc/fstab.  If you did not mean for it to be continuously available, you should not have installed the OS with the drive connected.  If it is a USB connection, then all you have to do is plug it in (with it turned on) and it should be detected and mounted in /media as a USB device.

---

### Post by hymerman on 2010-06-24
Oh, I added it myself, with the intention that it would not always be available - the boot process has never halted on being unable to mount a drive before and I was using it as an easy way to mount it myself later, without needing to specify a mount point and uuid. Is there some other way to achieve this?

---

### Post by dabl on 2010-06-24
Of course you can mount it manually every time you want to use it, or you could write a little shell script to mount it, and (with "sudo") run the script every time.  Don't put it in your /home/hymerman folder or run it from there, however, as that might cause other problems.  Put it in the /root folder.

IMHO the most economical and straightforward method to have large external storage available is to buy one of the big, cheap, not terribly fast drives, like [[COLOR="Green"]**this**[/COLOR]](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148413) one, and mount it in an inexpensive enclosure like [[COLOR="Green"]**this**[/COLOR]](http://www.newegg.com/Product/Product.aspx?Item=N82E16817153066) that includes the SATA-to-USB connections and a power supply, and then use that for data backups or transfers.  You just plug it in to the running system, the "device notifier" lets you know when it is recognized and mounted, and you proceed to copy stuff.  Note that there is no need to buy a fast high-performance drive for this, because the data transfer across the USB line is painfully slow anyway.

You can partition the big drive if it helps manage your data, and format it ext3 or ext4.

You can get fancy and play with E-SATA and/or Firewire connections to external drives, for faster data transfers, but those will cost more and give you other technical challenges to deal with to make them work.  USB just works.

Hope this helps.

---

### Post by pmawhorter on 2010-08-30
I've got the same complaint as hymerman. I like to specify mount directories and options for all of the devices that I own that may or may not be plugged in at various times using /etc/fstab, because that's what it's for. I've got a total of 6 mounts across 5 devices that aren't usually available at boot, which makes the prompts quite annoying, especially given that I've set both "nofail" and "errors=continue" in the options for said mounts. I could move all of that information into shell scripts and put them somewhere, but /etc/fstab is the proper place for it, as it works smoothly with mount -a, works for all users easily, etc.

So if there is a way to solve this problem (i.e. set some option somewhere to disable the prompt, despite the missingness of the devices), I'd be grateful to be informed about it. If there isn't, I'd like to know what to file a bug against. mount? /etc/fstab? just Ubuntu in general?

---

