---
title: "Anyone used BURG to beautify GRUB2?"
date: 2010-08-04
forum: General Help
---

### Post by spiralx on 2010-08-04
Just wanted to say that I use 10.04 without much problem, apart from my printer.

I do keep a Windows partition available, though, for odd things like the above, and so I have GRUB2 to look at every time I boot up.

It's always been DOS-ugly, and crude-looking, and no-one at Ubuntu (or anywhere else, apart from Mint) seems to spend much time looking at that.  But another project, BURG, did.

[http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html](http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html)

Has anyone any experience of this, and if so, how well did it work for them?

---

### Post by watupgroupie on 2010-08-04
I've installed it and it works great. Haven't bothered to reinstall since breaking it with my Windows 7 install but it worked fine for the short time I had it. I used the burg manager instead though [http://www.omgubuntu.co.uk/2010/07/burg-boot-loader-installation-themeing.html](http://www.omgubuntu.co.uk/2010/07/burg-boot-loader-installation-themeing.html) (glad to see another OMG! Ubuntu! reader)

---

### Post by dcstar on 2010-08-04
> **spiralx said:**
> 
........
Has anyone any experience of this, and if so, how well did it work for them?

Works fine, just uninstall Grub-PC after you get BURG set up.

---

### Post by elliotn on 2010-08-04
BURG looks great I will install it soon

---

### Post by marshmallow1304 on 2010-08-04
Sure it looks great, but my GRUB timeout is only 10s, so it's not worth the effort at the moment.

---

### Post by slooksterpsv on 2010-08-04
I just installed BURG and did the Homer Simpson splash screen, I love it!

---

### Post by spiralx on 2010-08-04
It's good to read that so many people have found it worth while.

Many thanks, too, for the updated Manager link, *watupgroupie*!

I have just tried to install it, and none of the methods worked for me, not quite sure why.

The originating site is Italian, which I ignored and got on with the commands themselves, but they all seem to have "deb" in them, and my terminal tells me that that is not a command, , and that .deb is not a file!

I'll try it again, but if no-go again, then I'll just keep an eye on their site, and see if anything improves in the future...

---

### Post by spiralx on 2010-08-04
Just seen this thread:

[http://ubuntuforums.org/showthread.php?t=1458329](http://ubuntuforums.org/showthread.php?t=1458329)

which is a bit worrying.  Maybe the "Manager" approach would get past this particular problem, as it is July 2010, whereas the person installing in this thread was using instructions from April?

---

### Post by Smart Viking on 2010-08-04
> **spiralx said:**
> Just seen this thread:

[http://ubuntuforums.org/showthread.php?t=1458329](http://ubuntuforums.org/showthread.php?t=1458329)

which is a bit worrying.  Maybe the "Manager" approach would get past this particular problem, as it is July 2010, whereas the person installing in this thread was using instructions from April?

Hi, i followed this link when i installed it, worked great i hope it helps for you. :)

[http://code.google.com/p/burg/wiki/InstallUbuntu](http://code.google.com/p/burg/wiki/InstallUbuntu)

---

### Post by 23dornot23d on 2010-08-04
I just tried it and its good ..... 

I like it .... all installed well and not a problem yet ...... seems a tad slow at booting up
though ,,,,  :)

---

### Post by Mi11z on 2010-08-04
> **spiralx said:**
> Just wanted to say that I use 10.04 without much problem, apart from my printer.

I do keep a Windows partition available, though, for odd things like the above, and so I have GRUB2 to look at every time I boot up.

It's always been DOS-ugly, and crude-looking, and no-one at Ubuntu (or anywhere else, apart from Mint) seems to spend much time looking at that.  But another project, BURG, did.

[http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html](http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html)

Has anyone any experience of this, and if so, how well did it work for them?


I have and my boot menu looks nice and minimalistic nowadays:

[IMG]http://i371.photobucket.com/albums/oo151/xl-mi11z/Other/Screenshot-4.png[/IMG]

---

### Post by Mi11z on 2010-08-04
> **marshmallow1304 said:**
> Sure it looks great, but my GRUB timeout is only 10s, so it's not worth the effort at the moment.

You can change the load time in burg manager: 

[http://www.sourceslist.eu/burg-2/burg-manager-configurare-e-installare-il-burg-non-e-mai-stato-cosi-semplice/](http://www.sourceslist.eu/burg-2/burg-manager-configurare-e-installare-il-burg-non-e-mai-stato-cosi-semplice/)

---

### Post by marshmallow1304 on 2010-08-04
> **Mi11z said:**
> You can change the load time in burg manager

That's good, but my point was that I only have to look at Grub for 10s tops during each boot.  And TBH, I actually like having instant access to any installed kernel.  BURG does look good though.

---

### Post by watupgroupie on 2010-08-04
You can access any installed kernel. I can't remember the key to toggle it but it's just an extended view that lists all of the kernels available.

---

### Post by spiralx on 2010-08-05
> Hi, i followed this link when i installed it, worked great i hope it helps for you. :smile:

[http://code.google.com/p/burg/wiki/InstallUbuntu](http://code.google.com/p/burg/wiki/InstallUbuntu) 

Ah!  Thank you!  THAT explains why ignoring the Eye-talian was NOT a good idea!  The bit I couldn't read was about first modifying sources.list, using
sudo gedit /etc/apt/sources.list

No wonder when I entered those two  "deb" lines into my terminal, it didn't like it!

---

### Post by What Rights on 2010-08-05
I will probably use this when I have a system that runs OSX, but if I owned a mac I would use the built in loader.

---

### Post by stlsaint on 2010-08-05
You can actually grub with themeing. See grub2 link in signature.

---

### Post by spiralx on 2010-08-05
> You can change the load time in burg manager: 

[http://www.sourceslist.eu/burg-2/bur...cosi-semplice/ ]("http://www.sourceslist.eu/burg-2/burg-manager-configurare-e-installare-il-burg-non-e-mai-stato-cosi-semplice/")...but as that link is all in Italian (!), you may not be able to, either!
> You can actually grub with themeing. See grub2 link in signature....somewhere, down in the murky depths of that spiel under Grub2, may be something to do with themeing, but heaven only knows where, how or with what (I suspect an arduous encounter with Terminal, again...!).

I agree with other posters' comments, that BURG seems distinctly slower than GRUB, and I couldn't find anywhere simple to speed it up.

Changing the screen resolution is a bit clumsy, too, needing F3 - r , then "Enter", and it doesn't handle wide-screen (though the 1024x768 seemed OK to look at).

Shame, cos it's so pretty compared to GRUB2!

Also, although it shows my Windows partition (once I entered "folded mode", because all the many kernel additions ran Windows off the screen!), it will not enter it.

So - BURG is a lovely work-in-progress, but clearly needs more work to make it more user-friendly.

---

### Post by 23dornot23d on 2010-08-06
GRUB2 can look a lot better than it does ..... but it all depends on setting it up
and as you say its using the command line at the moment to do it.

I keep the information [here for my own use]("https://sites.google.com/site/linuxbootubuntu/") ..... when I need to set a nicer boot screen up.

But things are constantly changing ..... so maybe in the future there will be easier ways
to do this task.

Burg is ok and runs well and so does Grub 2 ...... once set up properly.

I now have BURG on a Flash drive that I can add ...... when I want my laptop to be mobile
and the 2 USB hard drives disconnected.

So its solved a problem for me ...... grub 2 seemed not to work if I removed the USB hard drives ......

But now I can remove them and plug the USB flash drive in and all is good ..... 
although a tad slowish its no big problem ...... once you get into the OS you choose its ok.


I found a problem with the BOOT from a LAPTOP .....
A COLD BOOT ...... *not a restart ....... sets the boot order of my USBs one way (0,1)

A WARM BOOT ..... "the restart from a running OS ..... swaps the boot order (1,0)

So I always have to shutdown ...... completely ..... and then press the power on 
This then lets me boot into the BURG menu.

Just information in case anybody else has this problem ..... as it baffled me for quite a
while. 
(its ok once you know whats happening - I believe its to do with the speed some USB's identify themselves to the system)

---

