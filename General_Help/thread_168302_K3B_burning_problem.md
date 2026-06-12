---
title: "K3B burning problem"
date: 2006-04-30
forum: General Help
---

### Post by richbarna on 2006-04-30
This is just a quick question,
I am using Kubuntu and everything works fine, however I have found that when I burn a dvd (mixed data content, divx avi mpg etc) that sometimes the data is unreadable on my home dvd player (mainly films).
My dvd player plays EVERYTHING, (when burnt on Nero Win Xp )
is there an encoding problem?
is Nero Linux better?

Also The dvd's that i have burnt on Win Xp software, Music, Films cannot be read by Linux. My dvd player and burner work on Kubuntu but just won't read the dvd's that I store all this stuff on.

---

### Post by barbarian on 2006-04-30
Hei,
Probably some codecs needed to install additionaly.
check here:

[https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29)

---

### Post by richbarna on 2006-04-30
Thanks for the tip Barbarian, but I have all the codecs + DMA sorted.
Found that a couple of movies had dodgy encoding already.

The main problem now is accessing backed up files that I have saved on DVD. They were burnt on Windows XP using Nero, when i insert the disk I just get a window opens with Konqueror with a load of code type gibberish.
This is instead of folder icons or .doc icons etc.
Do you think that it's because everything is burnt as windows folders?
Maybe linux doesn't recognise the encoding for the icon graphic ?, you know, like when you have a RAR or ACE file but no WinRAR or WinAce installed.

Thanks anyway, I,ll keep searching.

Rich S

---

### Post by richbarna on 2006-04-30
Hi again,
It's a DVD read problem, I dug out an old backup CD and that opens fine with the CD ROM, I can open folders and access everything.

Strange.

So it looks like either windows burns dvd's differently to cd's, or i need to tinker with something in linux related to dvd data reading.

---

### Post by barbarian on 2006-04-30
.doc format should be read with no problem. If you have .rar archived files you should *apt-get install rar*

or try this:
open terminal and type:

[I]cd /media/cdrom0
ls -a[/I]

if you see your win files try to open them.

[I]kwrite yourwinfile.doc
[/I]
If you dont see your win files it probably means dvd related problem..

---

### Post by richbarna on 2006-04-30
Sorry, my post was a bit misleading, I was using the RAR file as an example of how you can't open them if you don't have winrar installed.

What I mean is when i open a data dvd in kubuntu that only contains .exe files or vids mp3's etc it's fine.
However if those files are inside windows folders I can't see anything.

For example, if i have a dvd with a couple of loose mpeg's a couple of .txt files i can see them and open them no problem.
What don't show up are the six or seven windows folders with mp3's etc INSIDE the folders.

thanks

Rich S

---

### Post by richbarna on 2006-04-30
I did what you said, and got :-
richs@dhcppc0:~$ cd /media/cdrom0
richs@dhcppc0:/media/cdrom0$ ls -a
.  ..  bootskin.ini  mako_boo.bmp  progress.bmp  tempnt.bmp
richs@dhcppc0:/media/cdrom0$

It shows the 4 loose files, but not the other 6 or 7 windows folders.

---

### Post by barbarian on 2006-04-30
So you mean that you do not see even folders?

---

### Post by richbarna on 2006-04-30
Exactly, doesn't even know they exist.
other files yes, folders no.

---

### Post by barbarian on 2006-04-30
hmm strange, first time I hear about this kind of problem.. Maybe sort of permissions problem.. 

anyway, maybe you find something useful here:

[http://kudos.berlios.de/kf/toc.html](http://kudos.berlios.de/kf/toc.html)

---

### Post by richbarna on 2006-04-30
Hey Barbarian,
Thanks for the link, I found this :-
>  
How to relax restrictions on CD/DVDs?
 When accessed, a CD/DVD is auto-mounted ("started") with certain restrictions that prevent running programs or seeing hidden files on the CD/DVD. To allow program execution directly off the CD, "exec" option has to, and "suid" option might have to be enabled. To see hidden and associated files, "nohide" should be enabled. In order to enable all of them, after mounting the CD, issue: 
sudo mount -o remount,user=$USER,nohide,exec,suid /media/cdrom0
 Use "/media/cdrom0" for the first drive, "/media/cdrom1" for the second, etc.

I did as it said but still no go.
The funny thing is, I have tried 8 or 9 different cd's and dvd's in the drive just see what I would get.
One was burnt using K3B - Shows up as zero files zero folders
A dvd with data             - Shows some files but no folders
A cd with data               - All files and folders are ok (Don't Know Why)
another cd                    - zero files 1 folder with a windows .exe file inside
cd with .deb files            - show up but with ???????? instead of file name
Original DVD movie          - plays perfectly with Totem
Copy DVD movie             - plays perfectly with Totem
A dvd with folders          - the folders are white blocks 3Mb with ?? on them

All of these were burnt with Nero on the same PC with Win XP, They don't have file protection enabled, just the usual drag 'n' drop and burn.

I am now determined to get to the bottom of this, I have also seen a few other threads regarding being unable to read dvd's, so if i can find a solution i will post an answer.

Common sense tells me that the way nero burns data to dvd's is causing a problem with whatever drivers my dvd rom is using. As i said before, my CD ROM reads everything no problem.
It's also strange that I can play dvd movies when so many other people have problems, but something as basic as opening a data dvd won't work.

Once again thanks for your help, I have bookmarked the KUDOS link.

Rich S

---

### Post by barbarian on 2006-05-01
Last thing..
Which KDE version do you use, 3.4? If so, don't throw avay those DVD, because in 3.5.2 many konqueror and k3b related bugs were fixed.

---

### Post by richbarna on 2006-05-01
I think i have the latest kDe not sure, Kubuntu 5.10 with all upates.
The DvD's i can open with xp it's just that i am trying to completely switch to Linux.

Thanks for your help, much appreciateD,

Notice the capital D all the time ?
I installeD xbinDkeys to Do some keyboarD shortcuts anD my little D DisappeareD.

New ThreaD time.

Thanks again

Rich S

---

### Post by [pl]ice on 2006-05-01
join the club!!!!!!!

   tried asking that at k3b devel mail list, they came up with settings,
well i got similar problems, 2 different DVD burners, same problem :/

 i can write the dvds but can't bloody open them!!
  throw dmesg, should say hdX track errors, yet Windowz will read it all! goodbye my backups!! (including 1 giga+ matlab....)

ok, to overcome this... 
  when u burn ur dvd don't put it on auto, use what it soupossed to use! (eg for R- etc) that will burn tracks after time, not on the fly,and i've changed from ISO2 to ISO1 in the settings, haven't got problems yet.... or the 'dodgy' method...
    'search' for Nero Linux , seems to overcome that problem, except nevest version can't burn DVD movies (have to drop whole iso of a movie)

 so yeh, if u find an answer, pls PM me!
have fun!!!!
oh, soon,(when i got some time, will try if K3B does the same under freeBSD...)

---

### Post by richbarna on 2006-05-01
For dvd movies i use K9Copy and then burn them with K3B and they work ok.

Like i said, for me movies aren't the problem, opening dvd's with backup docs etc.
Strange how some work and some don't, i will continue to investigate burning properties ISO's, etc.
I had Nero installed before and had no problems, I gave k3b a go and it was ok so i got rid of nero (i don't like having loads of apps that do the same job).
I'm gonna do what you suggested and change to ISO 1 and not burn on the fly and see what happens.

Cheers

Rich S

---

### Post by [pl]ice on 2006-05-01
sorry, but the same thing happens when i burn on cd/dvd normal files backup avis etc, i'm just burning heaps of movies, that's why the example...
good luck

---

