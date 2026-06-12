---
title: "Installing Ubuntu on a computer having only freedos"
date: 2011-04-20
forum: General Help
---

### Post by naiquevin on 2011-04-20
Hello, 

I am buying a laptop with only freedos installed and install ubuntu on it. Not sure if this would make it a dual boot system but I would prefer to keep freedos as well.

I have been using ubuntu since past one and a half year or so and pretty comfortable with it and have an experience of setting up ubuntu-windows7 dual boot a couple of times. 

But I have never worked with freedos. I would like to know if there is anything that I should keep in mind or be careful about while installing ubuntu along with freedos. 

To be more specific, I know that while installing ubuntu with windows, we need to shrink a drive to make some memory available to ubuntu. Is this to be done in similar way in this case ? How would be the memory allocation on a machine having only freedos ? 

Sorry if this sounds more of a freedos question than a ubuntu question :)

Thanks.

---

### Post by psusi on 2011-04-20
Why on earth would you want freedos?  If you have an old dos game or something from the late 80s or early 90s, then you can run it under dosemu rather than boot into an actual 16 bit single tasking command line operating system.

---

### Post by BertN45 on 2011-04-20
Consider to use freedos in Virtualbox. I am using DR-DOS 6 that way, not for anything useful, but just for old times sake.

---

### Post by naiquevin on 2011-04-21
> **psusi said:**
> Why on earth would you want freedos?  If you have an old dos game or something from the late 80s or early 90s, then you can run it under dosemu rather than boot into an actual 16 bit single tasking command line operating system.

I have heard that as per Dell's policy all laptops come loaded with some OS. And for those who don't want windows, they provide freedos. 

So FreeDos is not a requirement here, just that if I am getting it anyway why not keep the actual thing

---

### Post by psusi on 2011-04-21
> **naiquevin said:**
> 
So FreeDos is not a requirement here, just that if I am getting it anyway why not keep the actual thing

I can drop off my trash at your place too, but just because you got it doesn't mean you want to keep it ;)

If you want to fiddle with it you can always download it and install it in a vm, but there is no reason to keep it installed on the machine and actually boot into it.

---

### Post by oldfred on 2011-04-21
While I have to agree with everyone on not keeping it, but if your drive is large enough keeping an extra few GB is not the end of the world. Dual boot would not be as easy as the VM choices but you can easily make it dual boot.

Just shrink Freedos partition and install Ubuntu. I would suggest manual partitioning if using 10.10 as it has some confusing buttons that then overwrite entire drive.

Some examples of installs and issues:
Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by naiquevin on 2011-04-21
> **psusi said:**
> 
If you want to fiddle with it you can always download it an d install it in a vm, but there is no reason to keep it installed on the machine and actually boot into it.

Sorry I don't exactly get your point. Do you mean to say that setting up a freedos-ubuntu dual boot is such a complicated process that it would be  rather easier to uninstall freedos first and then go ahead with ubuntu installation ? Or is it that freedos is a total waste of memory in your opinion ?

I donot need freedos right now but theres no problem if it just stays in the system. Just like I wouldn't uninstall all the things that come with ubuntu that I don't end up using. 

Any way, I got the machine today and dell was kind enough to give a freedos cd instead of pre-installed OS. So no question of dual booting and I have everything up and running perfectly fine.

@oldfred - thanks for the resources. The last one is a superb link.

---

### Post by psusi on 2011-04-21
My point is that freedos is useless.  The only two possible uses are tinkering ( and how long can you do that for?  There just isn't much there to tinker with ) and playing ancient dos computer games, both of which you are better off doing in a VM so you can still be multitasking, rather than shutting down Ubuntu and booting into freedos.  Also you probably don't have an original sound blaster 16 compatible sound card that the old dos programs would know how to use, so sound won't work if you actually boot into freedos, but will if you run it under a VM, which will emulate that old hardware.

---

### Post by littlejoe5 on 2011-08-13
> **psusi said:**
> My point is that freedos is useless.  The only two possible uses are tinkering ( and how long can you do that for?  There just isn't much there to tinker with ) and playing ancient dos computer games, both of which you are better off doing in a VM so you can still be multitasking, rather than shutting down Ubuntu and booting into freedos.  Also you probably don't have an original sound blaster 16 compatible sound card that the old dos programs would know how to use, so sound won't work if you actually boot into freedos, but will if you run it under a VM, which will emulate that old hardware.


You ought to recognize that the above opinion is just that. I have a number of older programs (not games) that I still use.  I deliberate put Freedos )which installs on a 32bit format) in order to make good use of these programs.

If it is possible to run dos efficiently and completely under dosemu, they certainly haven't made it easy. One of the major problems is getting the floppy drive to do all the things that a floppy drive is supposed to do. Another rather difficult thing is to install a complete install of Dos (even Freedos} in a useable way. 

Now for those of you who do understand dosemu, I have a serious question: I was able to make my dos partition available to dosemu for reading and writing, and include apropriate directories in the 'path'. But what I would like to do (because you are right in that it would be nice to be able to run a full install of real dos (Freedos) without having to boot into it separately). Here then is the question:

How can I connect dosemu, so that it does not use it's own very limited portion of freedos, but rather uses the complete install that I have already installed in the first partition (sda1)?  And if I do so will dosemu still be inhibiting the use of the floopy drive, and other functions of freedos?

Thanks,    Dave

---

### Post by dandnsmith on 2011-08-14
There's another possible reason why it might have freedos.
If supplied by (eg)Dell, then, to provide support, they may want some OS they know about to carry out tests.
I know that, when I had a problem with a customers PC the first thing Dell wanted was for a set of tests to be run - some of which depended on the OS and content of an odd partition set up by them.

---

