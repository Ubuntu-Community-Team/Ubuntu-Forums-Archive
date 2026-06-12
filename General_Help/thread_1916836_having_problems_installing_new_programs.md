---
title: "having problems installing new programs"
date: 2012-01-28
forum: General Help
---

### Post by 2Dtech on 2012-01-28
[SIZE=2][FONT=Times New Roman]I just installed ubantu  [/FONT][/SIZE]today and am having problems installing an antivirus program from the disk.
I also tried to install an old program that the church uses and it also will not install. Their old computer crashed and burned last month and I am trying to piece an old system together so they can use. It is a very small church only about 35 people, and every dime counts for them.

Would anyone have any ideas, I have included what comes up when I try to install anything.
Thank you very much for any ideas to try. I installed the newest version of ubantu.

Tim


                                  Archive:  /media/Avast & Sygate/setupeng.exe
 [/media/Avast & Sygate/setupeng.exe]
   End-of-central-directory signature not found.  Either this file is not
   a zipfile, or it constitutes one disk of a multi-part archive.  In the
   latter case the central directory and zipfile comment will be found on
   the last disk(s) of this archive.
 zipinfo:  cannot find zipfile directory in one of /media/Avast & Sygate/setupeng.exe or
           /media/Avast & Sygate/setupeng.exe.zip, and cannot find /media/Avast & Sygate/setupeng.exe.ZIP, period.

---

### Post by Rodney9 on 2012-01-28
Ubuntu does not need an AntiVirus.

.EXE files are for Windows not Linux/Ubuntu

Some Window programs will run in [Wine]("http://www.winehq.org/"), however there maybe a Linux/Ubuntu equivalent, see here - [http://www.linuxalt.com/](http://www.linuxalt.com/) 


Rodney

---

### Post by 2Dtech on 2012-01-28
Thank You Rodney, I have never used ubantu before and was hoping to get it close to what the church had before. I still can't get the video drivers to install properly, but it is working.

They have one church program that I am hoping to put back on the system but I think it is for windows.

Once again Thanks, Tim

---

### Post by 2Dtech on 2012-01-28
just 1 more question, where, where is my downloaded programs fromm the ubantu site going to. They are not in the download files and I can't find a programs file.

---

### Post by raja.genupula on 2012-01-28
> **2Dtech said:**
> just 1 more question, where, where is my downloaded programs fromm the ubantu site going to. They are not in the download files and I can't find a programs file.


You mean the packages which are downloaded from update manage , then they will be here .
/var/cache/apt/archives . you can find the  those programs

---

### Post by 2Dtech on 2012-01-28
Raja, that is not what I am talking about. I downloaded Audacity from their website, and the audio drivers and video drivers will not install properly. I am not used to this layout that they have gone to and am getting lost.

Thanks Tim

---

### Post by raja.genupula on 2012-01-28
so i think you have downloaded from your browser right .

go to your browser downloads menu and then there will be list of your downloads . to know where they have , just right click at them and then there you have option ,open containing folder or show folder (for firefox and chrome .)this is the easy of getting .

By default all your downloads will be on your Downloads dir of your home dir .

All the best . hope that helps.

---

### Post by 2Dtech on 2012-01-28
Raja, as I said on the first post no matter what I download or try to install I get an error message like the one below. The only difference is that it will say the program that I tried to install, and every thing else is the same.


Archive:  /media/Avast & Sygate/setupeng.exe
 [/media/Avast & Sygate/setupeng.exe]
   End-of-central-directory signature not found.  Either this file is not
   a zipfile, or it constitutes one disk of a multi-part archive.  In the
   latter case the central directory and zipfile comment will be found on
   the last disk(s) of this archive.
 zipinfo:  cannot find zipfile directory in one of /media/Avast & Sygate/setupeng.exe or
           /media/Avast & Sygate/setupeng.exe.zip, and cannot find /media/Avast & Sygate/setupeng.exe.ZIP, period.


No matter if it is Avast or Power church software, I still receive the same message.

---

### Post by raja.genupula on 2012-01-28
as one of our friend said .EXE not possible in linux . If you wanna still run that use wine software.

regarding your drivers open system -> settings -> hardware -> additional drivers 

if there any drivers are showing to you then you have to install them . 

if you want an Anti-virus program for Ubuntu then we have many options .

look  at here . [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by Rodney9 on 2012-01-29
[http://xiphos.org/](http://xiphos.org/)

Xiphos (formerly known as GnomeSword) is a Bible study tool written for Linux, UNIX, and Windows using GTK, offering a rich and featureful environment for reading, study, and research using modules from The SWORD Project and elsewhere. It is open-source software, and available free-of-charge to all.

Xiphos is available in the Ubuntu Software Centre

Rodney

---

### Post by Zimmer on 2012-01-29
A bit of light reading might be of help..

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

[http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/](http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/)

---

### Post by oldos2er on 2012-01-29
> **2Dtech said:**
> Raja, that is not what I am talking about. I downloaded Audacity from their website

There seems to be some misunderstanding; [Linux is not Windows]("http://linux.oneandoneis2.org/LNW.htm"), and is not meant to be a replacement for Windows. Read the links that Zimmer posted; downloading software from an app/company's website is the last method you want to use to install software, not the first.

Linux does not run Windows software natively, as you've seen. This includes viruses and malware meant to run on Windows, so installing Windows antivirus is unnecessary. There are Linux antivirus programs in the repositories, but generally you don't need to run them unless you're running server software.

---

