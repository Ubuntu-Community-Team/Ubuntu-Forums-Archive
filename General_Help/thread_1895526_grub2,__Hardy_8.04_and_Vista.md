---
title: "grub2,  Hardy 8.04 and Vista"
date: 2011-12-15
forum: General Help
---

### Post by nedonedo on 2011-12-15
Hey,

I have a laptop dual booting Ubuntu 8.04 and vista. I am attempting to upgrade grub to grub2 and have run into a strange little issue as follows.

Grub2 chainload works but only the Ubuntu versions show up in the grub boot menu. When I run os-prober I see the vista info. 

Any ideas?

Grub version supported in Hardy is 1.96. 

I also have another laptop booting Vista and Ubuntu 10.04 with no issues, and while it may not make sense to some, I do want to keep Hardy on this machine.

thanks in advance.

---

### Post by dandnsmith on 2011-12-15
It sounds as though you haven't done a proper 'update' to grub2.
What did you do to install the newer version?
Did you reinstall the bootloader and bootstrap to /dev/sda (or whatever was appropriate)?

---

### Post by Mark Phelps on 2011-12-15
> **nedonedo said:**
>  I do want to keep Hardy on this machine

Hey ... I understand ... really.

I have an old tablet PC that worked GREAT with Hardy -- and I still have it on there.  No Ubuntu version since then has worked on it.

In my case, I'm using Win7, Vista, and Hardy -- and use EasyBCD to boot into Hardy.

If you are interested in how to do this on your PC, then PM me and I will email you the details.

---

### Post by nedonedo on 2011-12-15
install with 

sudo apt-get install grub2

Taken from ([http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html))

The install was fine and the chainload part works fine. All my legacy grub entries (not taking the chainload route) all still work with no problem.

Following the chainload entry takes me to grub 2 boot loader and only the ubuntu versions show up, plus mem-test.

I found another link that referred to os-prober which i installed and ran, and it shows my vista partitions.

I then tried sudo update-grub and still just ubuntu.

Oddly enough, the web site I referred to above is for the same version grub i have and also shows a dual boot configuration. 

I think I must have missed a step....

thanks again for any help

---

### Post by N00b-un-2 on 2011-12-16
Just out of curiosity why are you still running Hardy?  Support officially ended already didn't it?  Don't get me wrong, Hardy was by far my favorite version of Ubuntu I've ever used but it's downright ancient now.
But as far as getting grub2 installed on Hardy, it should be as easy as purging GRUB and then installing Grub2 to the MBR of your hard drive.  But truthfully, there is no major advantage as far as I can tell in upgrading to Grub2 if legacy GRUB is capable of dual booting Windows and Ubuntu.
Personally, I've never understood the need for the upgrade as GRUB2 is far more complicated than Legacy GRUB.  To this day, I still don't use GRUB2 as it doesn't add any kind of value or additional functionality.  I instead use BURG which is a graphical bootloader based on GRUB2 source code.  Now if grub2 were to support something like passwords, that'd be something

---

### Post by dandnsmith on 2011-12-17
> Following the chainload entry takes me to grub 2 boot loader and only the ubuntu versions show up, plus mem-test.

I don't understand this - if you've correctly installed grub2, there shouldn't be any question of chainloading to get to the grub2 menu, and the os-prober run as part of the install/update of grub will pick up all of the OS on the HDDs.

I think it's time to download and run [the bootinfo script](http://sourceforge.net/projects/bootinfoscript/), and display the results so we can all see them. This should get us out of the guessing game.

---

### Post by mörgæs on 2011-12-17
As have been mentioned above, 8.04 is out of security bug fixes. You are not doing yourself a favour by sticking to this one.

If your computer can run Vista, it can also run a newer Buntu. I would recommend a live boot for testing and then a fresh install, which will automatically give you Grub 2.

---

### Post by nedonedo on 2011-12-18
First, My motivation for keeping Hardy on THIS machine are my own. 

Second, I'm not interested in a different bootloader.

Third, Chainload to grub2 works, and ubuntu boots. It just doesn't see vista.

Forth, the boot option for grub legacy, to vista, (not taking the chainload path)  does work. 

I have a different machine, as stated above, that works fine with Ubuntu 10.04, Vista and grub2

Having said all that, I just want to figure out what went wrong, and why. If i can't, I need to remove grub2.

From everything I have read, this should be a no-brainer....

---

### Post by dandnsmith on 2011-12-19
> **nedonedo said:**
> Third, Chainload to grub2 works, and ubuntu boots. It just doesn't see vista.

Fourth, the boot option for grub legacy, to vista, (not taking the chainload path)  does work. 

I have a different machine, as stated above, that works fine with Ubuntu 10.04, Vista and grub2

Having said all that, I just want to figure out what went wrong, and why. If i can't, I need to remove grub2.

I'm with you if you have something which *works*, and have reason to keep it, why not.

If the 'different machine' works, then do you chainload from legacy grub to grub2 - if not, then my previous comments still apply.

---

### Post by nedonedo on 2011-12-27
I think I found the problem and I'm not sure why it is.....

I don't have a 30_os-prober script in grub.d

I have added an empty file of that name and no change on update-grub.

All the documentation i've read indicates this "should" have been created during the grub 2 install, and I have searched for an example of this script with no luck, any suggestions

Dan, i did run the script you suggested and saw pretty much what i expected to see, and as I stated above, this is a functional machine, not a fresh install.

---

### Post by oldfred on 2011-12-28
If you have grub legacy installed, the sudo update-grub updates grub legacy as it is the same command to update either grub or grub2. I think you do not get a full update to grub2's menu without deleting grub legacy. 

I do not know about grub2 1.96, but even the 1.97 version did not find other systems as well as the newer versions do. Lbuntu used to not install os-prober by default so maybe with 1.96 it does not install it by default either? 

Why even add grub2 to the mix if grub legacy works to boot Ubuntu & Vista? 

I like grub2 but used grub legacy for quite a while and initially resisted the change.  You can always add a Vista boot stanza to 40_custom if you want.

---

