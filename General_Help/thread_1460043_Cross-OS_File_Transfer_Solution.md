---
title: "Cross-OS File Transfer Solution?"
date: 2010-04-22
forum: General Help
---

### Post by opethfan89 on 2010-04-22
Hi all,

I recently discovered TeamViewer, a free windows application to let me remote control between 2 windows installs, and most importantly, FILE transfer easily between the two. 

I'm trying to find a similar solution for ubuntu, so if need be, I can xfer between windows and ubuntu. I **have** done cross-OS remote desktoping previously, using tightVNC on windows to control Ubuntu and it worked pretty well, but I could not do file transfers, and that is what my major premise is.

Can anyone suggest some viable solutions that will allow me to do Ubuntu-->Ubuntu and Windows<--> Ubuntu Transfers?

I should explain that I have a dual boot of Win 7/Ubuntu Karmic on Laptop, and Win XP/Karmic on Desktop.

Thanks for any suggestions,
Opethfan89

---

### Post by phisher1 on 2010-04-22
Samba would be the easiest way. You can create Samba shares on Ubuntu and connect to them from Windows, or you can create Windows shares on Windows and connect to them from Ubuntu.

---

### Post by Calcipher on 2010-04-22
What I did was install an ssh server on my Ubuntu machine and then use WinSCP to move files back and forth.  The only bad thing about this is that the Windows machine must always be the initiator unless you want to go investigate Windows based SSH servers (there are a few good ones like MobaSSH and, the one I've used, freeSSHd).

---

### Post by Lepy on 2010-04-22
+1 for samba. You could look into nfs shares as well, but I've heard windows support is laughable. This approach might get confusing if you are constantly switching and transferring files, unless you have ubuntu mount the samba shared folders on each windows partition.

If you are only transferring small files at a time or want file syncing, a dropbox account would probably be the easiest way to manage things since it is cross platform.

If you have spare parts lying around, you could cheaply build a freenas. This approach would allow you to share one folder as both a samba and nfs mount and keep all the files in one easily accessed place. Kinda like your own local dropbox. You could even setup remote access for when you are away from home.

---

### Post by 2hot6ft2 on 2010-04-22
> **opethfan89 said:**
> Hi all,

I recently discovered TeamViewer, a free windows application to let me remote control between 2 windows installs, and most importantly, FILE transfer easily between the two.
I thought teamviewer cost $750 for Business, $1,500 for Premium and $2,700 for Corporate.
They have a ubuntu version now
[http://www.teamviewer.com/download/index.aspx?os=linux](http://www.teamviewer.com/download/index.aspx?os=linux)

Samba or [Dropbox]("http://www.dropbox.com/")

---

### Post by dannyboy79 on 2010-04-22
openbox or ubuntuone. use the cloud, it's there to use for free.

OR

create a fat32 partition to mount in both OS's.

---

### Post by Chronon on 2010-04-22
> **dannyboy79 said:**
> openbox or ubuntuone. use the cloud, it's there to use for free.

OR

create a fat32 partition to mount in both OS's.

I think you meant dropbox -- openbox is a window manager.

---

### Post by opethfan89 on 2010-04-22
> **2hot6ft2 said:**
> I thought teamviewer cost $750 for Business, $1,500 for Premium and $2,700 for Corporate.
They have a ubuntu version now
[http://www.teamviewer.com/download/index.aspx?os=linux](http://www.teamviewer.com/download/index.aspx?os=linux)

Samba or [Dropbox]("http://www.dropbox.com/")

Well, it is free for PRIVATE/NON-COMMERCIAL use, and they show a small reminder each time the session is ended. It serves its purpose VERY well, and does everything I need, and nothing I don't. Also, I had no idea they have a linux version, that just makes things THAT much easier for me to use, awesome!! Definately cheered me up :)


> **dannyboy79 said:**
> openbox or ubuntuone. use the cloud, it's there to use for free.

OR

create a fat32 partition to mount in both OS's.

I've used dropbox, and I didn't mention this in my OP but my wish IS to basically have file sync.  I do have an external FAT 32 HDD (WD My Passport 400GB) and it serves its purpose but I bought that more for backups than for continual, day-to-day file transfers. I have an 8gb flash drive and that gets the job done for the time being, but I don't want to forget it at home one day and not have my necessary files, if that is understandable.

I've used Dropbox in the past, but the only thing I don't like is that it uploads every single file to the online server, and that takes time. And my MP3 collection is 10+gb, so even uploading 2GB of that on a crappy 128kb/s upload speed will take forever.



Thank you everyone for your responses. I will look more into ssh, samba,  and other methods when my schedule permits a bit more time. College  finals have got me fully occupied lately!

---

### Post by lisati on 2010-04-22
+1 for [samba]("http://ubuntuforums.org/showthread.php?t=202605")

---

### Post by opethfan89 on 2010-04-23
Well, just thought I'd let you guys know that I ended up installing Teamviewer and it works perfectly. I don't think I'll need anything else now since they released it for Linux, and I will probably end up using Teamviewer for transfers, and dropbox for file syncing.

Thank you very much for all your help, and I feel this topic can be marked [SOLVED] and closed :)

---

