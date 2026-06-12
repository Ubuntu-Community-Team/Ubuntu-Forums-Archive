---
title: "Installing Windows XP after Ubuntu"
date: 2010-11-25
forum: General Help
---

### Post by Pacopag on 2010-11-25
Hi.  I have a dual boot (windows 7/ ubuntu 10.04) already, and I'd like to add windows xp so I can run an old version of Maple (maple is a program that does math like calculus, algebra, etc.)  First of all, can I even have 3 OSs on one machine?  If so, can I just follow an online tutorial to get grub to work again after I've installed XP.

The alternative is to install Maple in linux using wine.  Does anyone have any experience doing this?  Do you think that Maple will run fast an smooth this way?  I've actually never used wine for anything, so I don't really know how good it is.

---

### Post by Hippytaff on 2010-11-25
A third alternative would be to run windows in a virtual machine like Vmware or Vmbox.

You can have as many os's on a pc that will fit, so it depends on your specs. Not sure about how well that software will work with wine, if its not on their list then the only way to find out would be to give it a go :-)

[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by Gunman1982 on 2010-11-25
I would suggest trying wine first, if it doesn't suit your needs you can still try and install winxp which is a lot more work.

---

### Post by Pacopag on 2010-11-25
Ok.  I'll try Wine first.  Will using Vmware or Vmbox slow things down?

---

### Post by 12apennachi on 2010-11-25
I use Oracle VM Virtualbox with XP and it works really well. There is a torrent with XP and it works perfectly, I highly suggest it.

---

### Post by Hippytaff on 2010-11-25
> **Pacopag said:**
>   Will using Vmware or Vmbox slow things down?

It depends on the processing power you have, and how hungry the software is, depending on this you may see a slight difference in perfomance, I use Spotify (which is an audio streamer in case you didn't know) in wine and it works fine.

Also I meant Virtual box rather than Vmbox...there are others also :-)

---

### Post by Pacopag on 2010-11-25
Can you explain the difference between wine and a virtual machine?  Which would be better for maple?  Think of maple as a VERY high level programming language.

---

### Post by 12apennachi on 2010-11-25
Wine is just a compatability layer to run windows programs. It is that simple (not really), but the concept is that simple. The problem with wine is not all programs are compatible, I have trouble with it all the time. A virualy box "tricks" the operating system inside to think it has a hard drive when it is really just a file on your ubuntu partition. The OS inside the virtualbox is a complete and legitimate  operating system that can function the same as it would on a real hard drive. WINE is a lot less intrusive, but if you have like 10 GB of hard drive space Virtual Box with windows is always the best way to run windows programs, in a real windows environment.

---

### Post by Hippytaff on 2010-11-25
> **12apennachi said:**
> Wine is just a compatability layer to run windows programs. It is that simple (not really), but the concept is that simple. The problem with wine is not all programs are compatible, I have trouble with it all the time. A virualy box "tricks" the operating system inside to think it has a hard drive when it is really just a file on your ubuntu partition. The OS inside the virtualbox is a complete and legitimate  operating system that can function the same as it would on a real hard drive. WINE is a lot less intrusive, but if you have like 10 GB of hard drive space Virtual Box with windows is always the best way to run windows programs, in a real windows environment.

Pretty much nails it on the head :-)

---

### Post by Pacopag on 2010-11-25
Virtual box sounds pretty rad. So as far as the windows programs are concerned, they can't tell the difference between running in a virtualbox and running on an actual windows machine? They'll run just as fast?  Is that right?

---

### Post by Pacopag on 2010-11-25
Ok.  Wine has already failed.  It won't even install.  I get this awesome Windows-like error to the effect of "Installer has encountered a serious error and has to close".

I'll try to figure out how to get Virtualbox kickin'.

---

### Post by 12apennachi on 2010-11-25
The only loss in performance is your processor speed and RAM. The hitch is Ubuntu needs some processor and RAM and so does the virtual windows. Otherwise, windows is real windows.

Edit: But if you are using XP, it doesn't need alot of processor. I have a 2.2 GHz Celeron Single Core and it is still fast a hell.

---

### Post by Hippytaff on 2010-11-25
> **Pacopag said:**
> , they can't tell the difference between running in a virtualbox and running on an actual windows machine? They'll run just as fast?  Is that right?

There seems to be no difference to your software, it is fooled, but it does depend on your processor whether you will notice that is is slower or not :-)

the best way to find out is to try it :-)

---

### Post by Hippytaff on 2010-11-25
> **Pacopag said:**
> Ok.  Wine has already failed.  It won't even install.  I get this awesome Windows-like error to the effect of "Installer has encountered a serious error and has to close".
Wine is very good at what it is very good at, but some things it just will not do :-)

---

### Post by Pacopag on 2010-11-25
On the VirtualBox download page I can get i386 or AMD64.  Does this refer to the Ubuntu that will be running it, or the Windows that I want to run.  I have 64-bit ubuntu, and I'd like to run 32-bit windows xp.

---

### Post by 12apennachi on 2010-11-25
The ubuntu you have. So get 64 bit. But get 32 bit isos (when you get them) to run inside no matter what. Itb will just be smoother

---

### Post by 12apennachi on 2010-11-25
I have a completely licensed and legal extra windows xp sp2 laying around if you want me to send it  to you via postal service, if you need it. Wink. Wink.

---

### Post by sikander3786 on 2010-11-25
> **Pacopag said:**
> On the VirtualBox download page I can get i386 or AMD64.  Does this refer to the Ubuntu that will be running it, or the Windows that I want to run.  I have 64-bit ubuntu, and I'd like to run 32-bit windows xp.
Unless you need USB support, go for the Open Source Virtual Box. Go to Applications > Software Center, search for Virtualbox and install it from repositories instead of downloading it from the website.

It works as nice as the proprietary version but it doesn't support USB devices. It would definitely support your Mouse and Keyboard but not USB flash drives or printer/scanner etc.

---

### Post by 12apennachi on 2010-11-25
I don't see why it matters. I am very pro-open source, especially after reading linus torvalds' book, Just For Fun. But if the original Oracle version has better functions I don't see why it shouldn't be used more.

---

### Post by sikander3786 on 2010-11-25
> **12apennachi said:**
> I don't see why it matters. I am very pro-open source, especially after reading linus torvalds' book, Just For Fun. But if the original Oracle version has better functions I don't see why it shouldn't be used more.
Installing anything from the repositories matters in a way as it gets updated automatically and regulary and always proves to be more stable than the other as it is tested before making into the repositories (not the case always) ;-)

And it also gets installed for multiple users automatically.

Might be some other benefits that I am lazy to mention now :-)

> But if the original Oracle version has better functions I don't see why it shouldn't be used more.

Always your own choice. Choose the one that suits you best. As I mentioned,

> **Unless** you need USB support, go for the Open Source Virtual Box.

---

### Post by 12apennachi on 2010-11-25
> Always your own choice. Choose the one that suits you best. As I mentioned,

Very true.

---

### Post by Pacopag on 2010-11-25
Thank you all for your help and advice.  I'll give Virtualbox a whirl and let you know how it goes.  I think that USB support will come in handy, so I'll download it of the Oracle site.  Thanks again.

---

### Post by Hippytaff on 2010-11-25
No problem (on behalf of all contributers) please mark the thread as solved in the thread tools at the top of the page so others can benefit from what you decided to do :-)

---

### Post by Pacopag on 2010-11-25
When I install windows xp in virtualbox, should I use ntfs or fat32.  Will I still be able to pass files to and from ubuntu if I use ntfs?

---

### Post by sikander3786 on 2010-11-26
> **Pacopag said:**
> When I install windows xp in virtualbox, should I use ntfs or fat32.  Will I still be able to pass files to and from ubuntu if I use ntfs?
I'd recommend NTFS since it has nothing to do with file sharing between Host and Guest.

And for sharing them, see here.

[http://helpdeskgeek.com/virtualization/virtualbox-share-folder-host-guest/](http://helpdeskgeek.com/virtualization/virtualbox-share-folder-host-guest/)

Or Google "File sharing virtualbox guest host" and you'd find some valuable information.

---

### Post by 12apennachi on 2010-11-26
Also, filesharing is pretty easy with Virtualbox. Just set up your shared folder in virtualbox and it is accessed in the "Network" area of windows.

---

### Post by Pacopag on 2010-11-26
Ok. So VirtualBox is one of the coolest things I've ever seen.  It works like a charm.  Thank you everyone for all your help.  And thanks sikander for the link.  It was very helpful.

---

