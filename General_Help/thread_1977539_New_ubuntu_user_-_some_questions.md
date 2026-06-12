---
title: "New ubuntu user - some questions"
date: 2012-05-10
forum: General Help
---

### Post by samwillc on 2012-05-10
Hi everyone,

I have been a dedicated windows user for about a decade, however, the advent of the awful windows 8 has forced me to seek refuge behind another OS. I have been doing a lot of research into ubuntu (plus a windows hating guy at work keeps going on about it!) and it looks great.

I was thinking about dual booting and keeping my win7 and installing ubuntu on the side just until I think it's a good enough replacement. I presume it's a ext4 partition but will obviously check first!

Anyway, I'm very excited about the prospect of a new operating system!

Not quite sure how I'll get adobe fireworks working, or my paragon backup software?

Anyway, that's me, just joined up :) didn't actually ask many questions as the title suggests.

Sam.

---

### Post by nothingspecial on 2012-05-10
Hi, welcome to the forums. :)

Yes it will be an ext4 partition.

Keeping a dual boot is a good idea if you have software you rely on. Very few windows programs will work with full functionality with Ubuntu.

You'll have much more fun learning the way to do what you do with Ubuntu rather than trying to make Ubuntu do what you used to do. That way frustration lies.

Anyway if you do have any more questions, feel free to post.

---

### Post by Henne91 on 2012-05-10
Hey!

Do you need help on how to install a dual boot system? Ubuntu should do this for you automatically. Just insert the Ubuntu LiveCD and choose to install Ubuntu. Ubuntu's installer (Ubiquity) will then ask you whether you want to delete Windows and install Ubuntu or install them aside.

Ubuntu will also replace your bootloader so you can choose on every boot whether you want to boot Windows or Ubuntu.

It seems like Fireworks could work on Ubuntu using WINE ([http://www.fireworksguruforum.com/index.php?showtopic=5250](http://www.fireworksguruforum.com/index.php?showtopic=5250)). Google can tell you more. Nevertheless, it might be a better choice to look for an alternative, for example: [http://askubuntu.com/questions/33212/is-there-an-alternative-to-adobe-fireworks](http://askubuntu.com/questions/33212/is-there-an-alternative-to-adobe-fireworks)

Paragon Backup won't work on Ubuntu but you actually don't need it. Ubuntu comes with a backup utility called Deja Dup which is installed by default and can be configured via System Menu (button at the top right corner of your screen) -> System Settings -> Backup.

Other good places to find answers on common questions (besides this forum) are askubuntu.com or wiki.ubuntu.com.

There is also a build-in help in Ubuntu. Just enter "help" in the Dash (Ubuntu-Circle-Button in the top left corner).

Hope this helps.

Hendrik

---

### Post by samwillc on 2012-05-10
Thanks.

I'm pretty excited right now. I have other things like a canon pixma printer too that came with a windows installer!

I'm still trying to think about how good it will be to be free of the ties that windows seems to bring with it. Although, windows is very well supported!

I also use wampserver for testing websites locally.

I am backing up my files the old fashioned way (drag onto external ntfs), will this drive detect in ubuntu in order for me to drag a few files in to see how it all works?

**edit** code::blocks, which one can I install?? [http://www.codeblocks.org/downloads/26](http://www.codeblocks.org/downloads/26) (win7-easy, mac osx-easy,..... linux1, linux2, linux3, linux4... <----- wtf?!) I can see why some people don't think it's worth the hassle.

Sam.

---

### Post by daisyflower on 2012-05-10
I am a simple user and if you install Ubuntu, it will prioritize itself above Windows when loading.  This means you have to select Windows before it continues, if you want Ubuntu you can do other things and come back to see it fully loaded.  I know there are ways to change the "grub" list (the list where you select Windows).  If you want that, maybe someone can help you there.  One nice thing I like is that it doesn't hide Windows hard drive.      In Windows I can't see "out of the box" where the Ubuntu drives are.  I am sure there is a program out there I could use, but with Ubuntu all drives are right there to play around with.  One big reason why I am mentioning this is that I didn't know how big to partition the Ubuntu drive.  You can make it small and still store files on the Windows C drive.  If you later find you don't need Windows, just do a fresh install.

---

### Post by samwillc on 2012-05-10
> **daisyflower said:**
> You can make it small and still store files on the Windows C drive.  If you later find you don't need Windows, just do a fresh install.

Hi,

Thanks. That's what I was planning to do. My files just consist of the standard docs/photos/music/vids on an external drive and I am not fussed about re installing software.

I just think with win8 looking so cack, I need a get out clause!

Sam.

---

### Post by nothingspecial on 2012-05-10
> **samwillc said:**
> 
Anyway, that's me, just joined up :) didn't actually ask many questions as the title suggests.


btw I can change the thread title to "New ubuntu user - not many questions" if you like :p

---

### Post by Henne91 on 2012-05-10
Ubuntu will detect and set up your printer automatically when you connect it. You won't need the windows installer. There are some cases where Ubuntu cannot automatically detect the vendor and name of the printer. In this case and window will appear and ask you to choose the right print driver (out of a vendor and printer list). In a very rare case, when your driver is not in the database, you might have to get a driver package directly from the vendors website.

External NTFS drives (and other mass storages) are detected automatically by Ubuntu. However, Ubuntu does also have a built-in backup solution called Deja Dup. Just enter "backup" into Unity's Dash.

I'm not sure what wampserver is but I set up an Apache Server on my laptop for testing websites locally. This is the type of server software that's used on most servers in the web.

---

### Post by samwillc on 2012-05-10
> **nothingspecial said:**
> btw I can change the thread title to "New ubuntu user - not many questions" if you like :p

Lol, maybe!

> **Henne91 said:**
> Ubuntu will detect and set up your printer automatically when you connect it. You won't need the windows installer.

External NTFS drives (and other mass storages) are detected automatically by Ubuntu. However, Ubuntu does also have a built-in backup solution called Deja Dup. Just enter "backup" into Unity's Dash.

I'm not sure what wampserver is but I set up an Apache Server on my laptop for testing websites locally. This is the type of server software that's used on most servers in the web.

1) Printer sounds like it will work ok.

2) Backup solution sounds good.

3) Wampserver uses php/mySQL/apache so shouldn't be a problem. I can use whatever, as long as it works!

Just gotta wait now while my files are copying across to the external drive, whilst sticking feet up and enjoying house of 1000 corpses. Funny the things you find to do on your day off from work other than what you are supposed to be doing...

**edit** is everything done via the terminal in linux? I've noticed most threads include some form of 'fire up the terminal, type in this command...'.

Sam.

---

### Post by flemur13013 on 2012-05-10
> Although, windows is very well supported!

That's only real advantage Windows has: more and better 3rd-party software.  Unfortunately, it's a big advantage.

I don't know anything about Win8, and hope I never do, but it's probably about the same as Win7 but with a different user interface.  If you decide against linux, or go dual boot,  because of the lack of applications, you might look at the following, which replace the "explorer" windows manager in XP/Win7, and might work in Win8:

- EmergeDesktop: simple, easy to customize, like fluxbox for linux, comes with a terrible default setup that'll make you hate it at first. I use this on Win7.

- SharpeEnviro (or "SharpE"): looks and acts a lot like a standard gnome interface, complete with gnome icons.

---

### Post by samwillc on 2012-05-10
> **flemur13013 said:**
> That's only real advantage Windows has: more and better 3rd-party software.  Unfortunately, it's a big advantage.

I don't know anything about Win8, and hope I never do, but it's probably about the same as Win7 but with a different user interface.  If you decide against linux, or go dual boot,  because of the lack of applications, you might look at the following, which replace the "explorer" windows manager in XP/Win7, and might work in Win8:

- EmergeDesktop: simple, easy to customize, like fluxbox for linux, comes with a terrible default setup that'll make you hate it at first. I use this on Win7.

- SharpeEnviro (or "SharpE"): looks and acts a lot like a standard gnome interface, complete with gnome icons.

Thanks, I've been looking at gnome3 as I don't think I'm going to like unity after viewing the vids. Of course, the proof is in the trying out.

Gnome3 has a gorgeous UI and I could get well used to that! Must try! Don't quite understand how you can just 'change' your desktop though. Does it overwrite, is it an app? Does it slow things down like adding a launcher does on android phones?

Sam.

---

### Post by nothingspecial on 2012-05-10
> **samwillc said:**
> 
**edit** is everything done via the terminal in linux? I've noticed most threads include some form of 'fire up the terminal, type in this command...'.



Not at all, there should be no reason why you should ever ***have*** to use the terminal, unless you want to.

It's just easier to give instructions that way and for the people reading them to copy and paste.

---

### Post by samwillc on 2012-05-10
> **nothingspecial said:**
> Not at all, there should be no reason why you should ever ***have*** to use the terminal, unless you want to.

It's just easier to give instructions that way and for the people reading them to copy and paste.

Thanks. I see. Makes sense. I don't mind using the terminal (powershell in windows). Same thing I presume.

I'm all backed up now, got my ubuntu 12.04 .iso burned to disc and ready for the grand install later this evening. Can't wait to try it! The only thing that bothers me by the look of unity is the minimize/close buttons being on the top left instead of top right, I'm not used to that at all, gonna be some clicking in empty spaces I think. All part of the fun though!

Sam.

---

### Post by traditionalist on 2012-05-10
I am a new convert to Ubuntu. I found the best solution was to run windows in a virtual machine.  Such as Virtual box. Easy to use;

[https://www.virtualbox.org/](https://www.virtualbox.org/)

Regards.... Trad

---

### Post by SuaSwe on 2012-05-10
> **samwillc said:**
> ... The only thing that bothers me by the look of unity is the minimize/close buttons being on the top left instead of top right, I'm not used to that at all, gonna be some clicking in empty spaces I think.


This bothers  me too - but luckily it can be changed! Take a look at [these instructions]("http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/"); they are aimed at Ubuntu 10.04 but far as I can remember are the same - or very nearly so - for later distros. Basically it just involves opening gconf-editor (usually Alt+F2 then type gconf-editor and hit Run), then navigate to apps/metacity/general in the Registry Edit-like editor, and change the value of button_layout to: 

```

menu:maximize,minimize,close

```

... or whichever order you prefer. Sorted! :)

---

### Post by samwillc on 2012-05-12
Thanks, I found that too.

Only problem is, they go top right, but in full screen, the close/minimise is back at top left! A bit of uniformity is required. For that reason, I am learning to live with it top left! :)

Sam.

---

