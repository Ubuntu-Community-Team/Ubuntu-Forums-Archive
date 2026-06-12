---
title: "[help please] - USB + DVD not working"
date: 2011-02-19
forum: General Help
---

### Post by Inprogress on 2011-02-19
Last week I decided I need to reinstall XP Pro so that I can use Office 2007 (been using Openoffice and it just doesn't fit well0 plus be able to run my CAD software again, and install my online poker software.

I was dual booting with Ubuntu 9.04 and Mint 10. I installed XP over Ubuntu as Mint is my upgrade from 9.04 - no offense.

Anyhow, stupid me, I deleted my GRUB2 bootloader with my XP installation...didn't know that. I got it fixed with the patient help of Viking777 on the Mint forum.

However (haven't been able to solve this one) now my DVD drive doesn't work (well it works physically cause I can hear it) and any external storage via USB doesn't work either (the usb or external harddrive lights up though). However when I plugged in my mobile phone to use as a modem (now I use a PCMCIA card), that did work...the modem bit, not the phone storage though.

I got some terminal commands to run in...uhm....terminal (please I am dangerous when it comes to the inner workings of Linux - I fix linux the same way you would own a self painted Van Gogh - paint by numbers), but that only gave me info but nothing much else. 

Can anyone help? I can just re-install Mint - maybe I should try Xubuntu, but then I will loose the programs I have installed so far, plus there are some files that I want to save. :(

I have tried commands: 

lsmod | grep usb

and

sudo modprobe usb-storage

and

dmesg

I was told the outputs look fine but I don't know what that means? I have either annoyed them over on the Mint forum, or I'm not doing something that they assume I would grasp. Hey, I use linux cause unlike Windows I can't break it (with Windows I know just enough to mess it up, or I install all kinds of little program etc - plus I always seem to get annoyed with Windows anyway during normal usage). Well, couldn't I suppose :confused:

---

### Post by fabricator4 on 2011-02-19
I think it's just one of those things that's easier to fix with the machine in front of you.

I think it's usb_storage by the way

Try: 
```

lsmod

```

Down the bottom somewhere it should list usb_storage with size and number of processes using.

?

Chris

---

### Post by Inprogress on 2011-02-19
> **fabricator4 said:**
> I think it's just one of those things that's easier to fix with the machine in front of you.

I think it's usb_storage by the way

Try: 
```

lsmod

```

Down the bottom somewhere it should list usb_storage with size and number of processes using.

?

Chris

You know, now that you mention...I forgot about those situations, its been such a long time that I have been able to fix things (my pc and various bikes) via the web.

Anyway, lets just see where this final path leads, thanks Chris.

lsmod says this, I copied the bunch of text around usb_storage:

```

ppp_async               6778  1 
crc_ccitt               1351  1 ppp_async
option                 13133  2 
usb_wwan                9953  1 option
usbserial              33100  7 option,usb_wwan
usb_storage            40172  0 
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
dm_crypt               11385  0 
snd_hda_codec_conexant    29736  1 

```


What now?

---

### Post by Inprogress on 2011-02-19
I think I just found my solution...off sorts - it will work for now.

If I plug in my external harddrive when I am presented with the OS dualboot selection menu (sorry, not sure what you call it..the bootloader menu?), and start Mint then my external hard drive is loaded and usable.

So if this can't be fixed (gonna do it anyway) then I will just reinstall mint 10 (or try Xubuntu 10.04 to tap extra oomf from my laptop).

Thanks Chris. Like I said, does this mean anything?

---

### Post by fabricator4 on 2011-02-19
It means that the usb_storage module is being loaded, but nothing is currently hooked into it. It says '0'.  Now plug a USB memory into it and run lsmod (edited) and see if the module is 'talking' to the device.

It may be that the automount part of the equation is not working.  If you get a result greater than 1 for usb_storage do the following:

```

sudo fdisk -l

```

I don't even know if mint has sudo, or if you have to use a different mechanism.

If you can see the partition for the USB memory it will be (for example) sdb in a single HDD system or sdc in a two HDD system and so on.  If it's there, try:

```

sudo mkdir /media/testdisk
sudo mount /dev/sdc /media/testdisk
cd /media/testdisk
ls

``` 

Of course you should change sdc to whatever the USB device is.  Mint may use /mnt instead of /media to mount temporary drives, so change accordingly.  Not a biggie, you can mount to any valid directory.
 
If all is well ls will list the files that are on the USB drive.

If you have to re-install I can recommend 10.04 Ubuntu.

I normally run it with no visual affects, but actually enabled them today.  Nice cube affect for changing workspaces.  I many use alternate workspaces more now.

Chris

---

### Post by Inprogress on 2011-02-19
Will try the above, just wanted to mention Mint is a derivative of Ubuntu, Mint just comes with a bunch of propritary stuff loaded already. Its basically Ubuntu, just a bit refined and stuff added to it.

---

### Post by Inprogress on 2011-02-19
Are you sure about that command "lsprob" since I get an error stating the command isn't found, I even tried google of that command to see if it might be something similar.Just to check is: Lima Sierra Papa Romeo Oscar Bravo

---

### Post by fabricator4 on 2011-02-19
> **Inprogress said:**
> Are you sure about that command "lsprob" since I get an error stating the command isn't found, I even tried google of that command to see if it might be something similar.Just to check is: Lima Sierra Papa Romeo Oscar Bravo

Oh, sorry.  I meant "lsmod" of course - the command you used earlier. :oops:

Chris

---

### Post by MARP1961 on 2011-02-19
Sorry to interrupt this thread but just to say that Mint and Ubuntu should be almost the same since Mint is based on Ubuntu. With a more 'works out of the box' philosophy and arguably a more attractive user interface I was attracted to Mint until I read about the political views of their founder. Google search 'Mint Hamas' if you want to know why I reverted back to Ubuntu.

---

### Post by fabricator4 on 2011-02-19
> **MARP1961 said:**
> Sorry to interrupt this thread but just to say that Mint and Ubuntu should be almost the same since Mint is based on Ubuntu. With a more 'works out of the box' philosophy and arguably a more attractive user interface I was attracted to Mint until I read about the political views of their founder. Google search 'Mint Hamas' if you want to know why I reverted back to Ubuntu.

Eeeek!  Political alert!

Obviously I can treat Mint as an extension of Ubuntu.  I just wish I didn't have this bad taste in my mouth.

Chris

---

### Post by Perfect Storm on 2011-02-19
Anyway, mint have their own forum, please use it: [http://forums.linuxmint.com/](http://forums.linuxmint.com/)

---

