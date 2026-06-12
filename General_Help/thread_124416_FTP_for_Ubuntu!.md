---
title: "FTP for Ubuntu!"
date: 2006-02-01
forum: General Help
---

### Post by daditlefsen on 2006-02-01
Hi.

I run a small company that designs websides and codes php programs for customers. It is not so very long time since I changed out Windows to Ubuntu, and I have not had any big problems whit it besides the FTP.

In Windows I used a program called FlashFXP, so I want to use it in Ubuntu to. I wrote  this to the Inicom Networks:
> iniCom.NetWorks Contact Form

Full Name:  Dag Andre Ditlefsen
Email:  [email]dagdit@gmail.com[/email]
Telephone:  -
Subject:  FlashFXP
Message:  Will the FlashFXP program run on Linux? If it doesn't, when can it do so?

And got this reply:
>  Hello,

I'm sory but FlashFXP does not work in Linux. It is optimized for Windows and takes advantage of a number of the more obscure Windows functions. FlashFXP will work in a Windows emulating enviorment in Linux such as Wine but it is not the best solution. As of this time I am unaware of any plans to port FlashFXP to Linux.

Best Regards,

-Chris
Inicom Networks Support

As Chris from Inicom said I could use Wine to use the program, but I got no expirience whit Wine. Is there any toturial/HOWTOs out there? Or is there any FTP-programs for Linux that rocks? \\:D/  I have tryed gFTP but i think it sucks..

Thanks for the help:)

---

### Post by playmobiel on 2006-02-01
try to test different linux ftp clients, if you don't find anyhting that you like, install wine , and try to install fxp

 > wine fxpinstaller.exe

---

### Post by daditlefsen on 2006-02-01
Thanks. :P That was not so hard;P hehe..

---

### Post by lolcese on 2006-02-01
Try gftp. Install it using:

[FONT=Courier New]sudo apt-get install gftp
[/FONT]

---

### Post by daditlefsen on 2006-02-01
As I said earlyer I've tryed gFTP and I dont like it...

---

### Post by lamego on 2006-02-01
The following text is just dumb comercial talk.
> It is optimized for Windows and takes advantage of a number of the more obscure Windows functions.

Do you like nautlis to browse your disk ? Nautilus supports FTP meaning you can browse and interact with remote ftp servers just has you do on your local disk.
Menu Places -> Connect to Server (FTP with login), put your login info and connect.

---

### Post by nix4me on 2006-02-01
Use secureftp.

It does not do fxp but it is the best ftp client out for linux.
I looks very similar to flashfxp.

I used flashfxp for years and I have tested all ftp clients for linux.

Secureftp is the best.

nix4me

---

### Post by MarkBaum on 2006-02-01
It isn't free, but Igloo FTP is the best graphical FTP program I have seen. I've been using it for a couple weeks, it's $30 to register, free to try.  Lifetime upgrades I think.

[http://www.iglooftp.com/unix/](http://www.iglooftp.com/unix/)

---

### Post by eddiewalker on 2006-02-02
FileZilla is currently being ported to linux.  They have a binary up on their site that, while not complete, already works great.

---

### Post by l.tambiah on 2006-02-02
I am surprised you think gftp is not very good, i find it very stable and it does the job perfectly. It sounds like you are not willing to give other things a go. GFTP allows you to use ssh with instant commands too. So for me and other users GFTP ROCKS!!!!!!!!!!!!!!!!!!!

---

### Post by Mickey1 on 2006-02-02
gFTP also does FXP :-)

I found that FlashFXP crashes using wine...mainloy on listing the content of another server...

I'd stick to gFTP if you really want to fxp

---

### Post by daditlefsen on 2006-02-02
l.tambiah, gFTP gives me the a error while im trying to upload a image, or anything:
> 150 Opening ASCII mode data connection for file list
226 Transfer complete.
Received URL file:///root/Desktop/skjermdump-lite.png
Could not change local directory to /root/Desktop/skjermdump-lite.png: Ikke en filkatalog 

In english it says that /root/Desktop/skjermdump-lite.png is not a file catalog. I dont understand why. Ive tryed to upload files to serval ftp servers, but it still does not work.

nix4me: How do I get secureftp?

---

### Post by fairdoes on 2006-02-07
I've only had Ubuntu for a week, and been online for two days with it (!), but ftp is the only thing preventing a complete swap from MicroLimp.

I have breezy running and a guide to installing an ftp client that works would be excellent. Thanks:)

---

### Post by septus on 2006-02-10
I followed advise from this forum and tried to install gftp (which I like from Puppy Linux). However, sudo apt-get install gftp did not work due to incompatible dependencis, and I failed to connect to my website host's ftp server from Nautilus. Hopefully secureftp will be "more cooperative".
Cheers
"septus":(

---

### Post by Zeroangel on 2006-02-10
Re: The dependencies, I would enable the Universe and Multiverse repositories if I were you (temporarily, at least, if you want the greatest stability)

Personally, I prefer Quanta to bluefish, as it has FTP built right into the project manager so that you can upload files to the webserver by right clicking on the filename (in the project sidebar) and a few other features that I really like. I think of Bluefish as ~OO.o  v1.4 where Quanta is more like ~MS Office 2000. A little more bloat, but some of it is good.

---

### Post by l.tambiah on 2006-02-10
I not sure as to why your getting problems, as i say gftp works fine for me,  i never have any problems. As for using  SSH i use FTP but i know you can use it. I would advise reading gftp FAQ's.

Here:-
[gftp FAQs]("http://gftp.seul.org/readme.html")

*There is nothing wrong with gftp many are using it quite happily. I know i am....

---

### Post by lol on 2006-02-10
> There is nothing wrong with gftp many are using it quite happily.

I cannot agree with this. gftp fails to meet my most basic requirements, which I believe should be part of any decent ftp client.

1 - I cannot delete a lot of files/directories (unless I spend hours in front of gftp). There is a 45s timeout of my ftp server. It takes about 30 to 40s to gftp to get the full list of files when I want to delete one of the top directories. It then start to delete some files, but because there is no keep alive implemented (the author don't want to), the connection is closed before gftp has time to delete more than a few files. And I then have to start again from scratch... Doing the same with any other windows client, it takes 5s of my time.

2 - gftp is really unstable, at least with bad connections. I often have segmentation faults, when trying to delete directories for example, but also when trying to connect using a ftp proxy (actually, the client crashed everytime I tried this).

IglooFTP seems good, too bad it's not free. Right now, when I need to delete a lot of files from linux, I use virgoFtp. It's ugly and I really don't like it, but at least it can handle the work.

---

### Post by l.tambiah on 2006-02-10
I just find it strange that you have all these issues, but i get none of these. My gftp works as well as any other FTP client, are you using Breezy and installing via apt? As someone else said you could try FileZilla which has nightly builds at current. 

[http://filezilla-project.org/nightly.php]("http://filezilla-project.org/nightly.php")

---

### Post by beerorkid on 2006-02-10
I use konqueror and krusader for FTP, they are awesome.

in konqueror you have to edit the tool bar to show a dual pane icon, this lets you open up two windows simply drag and drop.  Could not be easier.

---

### Post by fairdoes on 2006-02-10
I found gftp after enabling repositories - it seems good. I wish there was a user guide. The alleged user guide is only a list of problems!

for newbies (that's me) it seems a good idea to test it out on a website that isn't too important ... ;)

---

### Post by l.tambiah on 2006-02-10
Another option that you could try is the extension called "FireFTP" for Mozilla Firefox, it is currently beta but give it a whirl by using it. You can find out more here:-

Home Page:-[http://fireftp.mozdev.org]("http://fireftp.mozdev.org")

---

### Post by beerorkid on 2006-02-10
I used it for a little bit (fire FTP).  I did have some problems with it though.  when doing large file transfers it borked out.  Also I found it a little hard to figure out where exactly you are putting things.

I hope it does get a little better in the future.  It is a great idea.

---

### Post by daditlefsen on 2006-02-16
Why i dont like GFTP? I cant download a hole folder. I cant chmod ha hole folder and all the files in the folder in just one click. 

The FTP problem is the one thing I dont like about Linux. I tryed IglooFTP and it seems that it is the greatest program for Linux. Its a shame its not free:(

---

### Post by l.tambiah on 2006-02-20
[quote=daditlefsen]Why i dont like GFTP? I cant download a hole folder. I cant chmod ha hole folder and all the files in the folder in just one click. 

The FTP problem is the one thing I dont like about Linux. I tryed IglooFTP and it seems that it is the greatest program for Linux. Its a shame its not free:([/quote] 
Without insulting your intelligence here, can i just add that gFTP can download whole directories and is perfectly capable of chmod multiple files. Dont forget as well too invest your time in the command line client ftp, its easy to use. Getting started with FTP see this [guide.]("http://www.ibiblio.org/pub/Linux/docs/HOWTO/FTP")

---

### Post by psusi on 2006-02-20
The only reason I ever found for using FlashFXP was because it supported site to site transfers, though I had been doing those 'by hand' for about 2 years before FlashFXP came out.  

These days I just avoid ftp completely.  It is insecure and has trouble with firewalls.  For those reasons I prefer to just use https.  It's secure, has no trouble with firewalls, and all you need to use it is a web browser!

In windows you can use explorer's 'web folders' feature and in ubuntu, Nautilus supports the same thing, just doesn't call it that.  Lets you open the folder on the server just as if it were local.

---

### Post by fairdoes on 2006-02-22
daditlefsen - I'm also new to gftp (and ubuntu!), but suddenly gftp makes sense!

 I think extra downloads improve it - gftp-common, gftp-gtk and gftp-text are all now installed on my machine, and it's better than what i was used to on Windows.

 If you select many files at once, you can **chmod** them all together. Clicking the buttons above the files allows you to sort the directory so all the folders and files are in the order most convenient to you - example - newest, folders on top, files on top.

 It's a shame there's not a manual.

 Talking of manuals - the firewall **firestarter** has a brilliant pdf download, and it should solve the insecurities that ftp may otherwise have (previous contributor mentioned http being more secure; my hosts do https transfers, but it takes for ever.).

 The timeout may be frustrating, but it's normally the webhosts doing this for your own security. I have free space from my dial up and you can stay logged on to them all day via ftp! It's totally insecure ...

ftp was the final hurdle for me in a complete exit from MS. I know the transition is frustrating, but it's good when it finally all gells.:-D

---

