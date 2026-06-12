---
title: "All of my videos disappaered after running this command"
date: 2012-03-01
forum: General Help
---

### Post by helpme222 on 2012-03-01
Hi, I ran the following command trying to refresh thumbnails in a folder. I ran this command:

**find /home/user/videos/ -name "*.flv" -exec rm -f {} \;**

And then all the flv videos disapeared! How do I get them back now? I really need them. I don't know what I did. I am using lubuntu.

---

### Post by jerome1232 on 2012-03-01
So in summary, that command searched for all flash video's in your ~/Videos folder, and then forced a permanent removal of them.

The only way that you may be able to recover the files, is to use photorec (I'm not sure if it can recover flash videos), it [COLOR="Red"]might[/COLOR] be able to recover the videos, you need either a second partition or an external drive to write the data too, you can't write to the partition your attempting to recover from as it may overwrite the very data your trying to recover.

edit: Is your /home on a separate partition than your /? Do you still have your live cd or live usb?

---

### Post by helpme222 on 2012-03-01
> **jerome1232 said:**
> So in summary, that command searched for all flash video's in your ~/Videos folder, and then forced a permanent removal of them.

The only way that you may be able to recover the files, is to use photorec (I'm not sure if it can recover flash videos), it [COLOR="Red"]might[/COLOR] be able to recover the videos, you need either a second partition or an external drive to write the data too, you can't write to the partition your attempting to recover from as it may overwrite the very data your trying to recover.

edit: Is your /home on a separate partition than your /? Do you still have your live cd or live usb?
Actauly it was in virtualbox, so how exectely would that work?

---

### Post by helpme222 on 2012-03-01
I was just following the advice in the second to last post here:
[http://www.linuxquestions.org/questions/ubuntu-63/no-thumbnail-for-flv-file-though-present-for-mpg-avi-and-mp4-files-761542/](http://www.linuxquestions.org/questions/ubuntu-63/no-thumbnail-for-flv-file-though-present-for-mpg-avi-and-mp4-files-761542/)

---

### Post by nothingspecial on 2012-03-01
That command was to remove all the video thumbnails.

You have deleted all your videos, well all the .flvs anyway.

Stop using the computer right now and have a look here

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

Never ever use a command you find on the internet unless you understand exactly what it is going to do.


***Edit*** Just seen that this was in a virtual machine. I have no idea how photorec will deal with that or even if it can.

---

### Post by aeronutt on 2012-03-01
> **helpme222 said:**
> I was just following the advice in the second to last post here:
[http://www.linuxquestions.org/questions/ubuntu-63/no-thumbnail-for-flv-file-though-present-for-mpg-avi-and-mp4-files-761542/](http://www.linuxquestions.org/questions/ubuntu-63/no-thumbnail-for-flv-file-though-present-for-mpg-avi-and-mp4-files-761542/)

There's a huge difference between this command:
```
find ~/.thumbnails/ -name "*.png" -exec rm -f {} \;
```

and the command you ran:
```
find /home/user/videos/ -name "*.flv" -exec rm -f {} \;
```

---

### Post by HeroOfCanton on 2012-03-01
> **helpme222 said:**
> I was just following the advice in the second to last post here:
[http://www.linuxquestions.org/questions/ubuntu-63/no-thumbnail-for-flv-file-though-present-for-mpg-avi-and-mp4-files-761542/](http://www.linuxquestions.org/questions/ubuntu-63/no-thumbnail-for-flv-file-though-present-for-mpg-avi-and-mp4-files-761542/)

Never run a command you don't understand. Especially if it contains the rm (delete) command.

Sorry.

---

### Post by helpme222 on 2012-03-01
Well, I ran the first command and it did nothing. Is there any application I can use in lubuntu like recuva?

---

### Post by jerome1232 on 2012-03-01
> **nothingspecial said:**
> 

***Edit*** Just seen that this was in a virtual machine. I have no idea how photorec will deal with that or even if it can.

That makes this much easier then, OP needs to just boot the vm with an iso, install photorec while running in live mode (it will be stored in ram), and run it from within the virtual machine.

You will also need to make a new virtual hardisk, format it, mount it, and write the data to this new virtual disk.

edit: I'm way to tired atm to give detailed steps, but using that as a guide I'm sure someone else can take it from here.

in case it hasn't been mentioned, [COLOR="Red"]Turn off the virtual machine, do not run it unless running off of a live cd(iso file) so that writes are not occurring to the disk[/COLOR]

---

### Post by helpme222 on 2012-03-01
> That makes this much easier then, OP needs to just boot the vm with an iso, install photorec while running in live mode (it will be stored in ram), and run it from within the virtual machine.
According to mywot it says "photorec" is malware, is this thing safe?

> You will also need to make a new hardisk, format it, mount it, and write the data to this new virtual disk.
And how do I get it to be recognized by the other os?

---

### Post by helpme222 on 2012-03-01
Ah well, I guess I really don't need them that much anyway. But thanks for the advice everybody. :)

But I was wondering, how do I get the flv thumbnails to show?

---

### Post by jerome1232 on 2012-03-01
It's safe, you install it using apt-get/synaptic, it's in the ubuntu repositories.

edit: nvm I guess your not going to pursue rescuing the files?

---

### Post by matt_symes on 2012-03-01
Hi

> find /home/user/videos/ -name "*.flv" -exec rm -f {} \;

> According to mywot it says "photorec" is malware, is this thing safe?

Where on earth are you getting this information ?

Please, please, please do yourself a favour. Post on these forums before running any command you see on the Internet and get the feedback of other users as to whether it's a safe command to run.

Kind regards

---

