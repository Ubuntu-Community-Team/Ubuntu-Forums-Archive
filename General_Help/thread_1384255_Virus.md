---
title: "Virus??"
date: 2010-01-18
forum: General Help
---

### Post by criptommy on 2010-01-18
I am havin various .exe files and other text files created automatically in some of my folders. They reappear even after i delete them continuously. Is this a virus or somethin. Please suggest some solution

---

### Post by MelDJ on 2010-01-18
what folder are they in?

---

### Post by criptommy on 2010-01-18
DC downloads folder and Music folder. I havent observed in any other folders but it might be there. Not sure abt other folders

---

### Post by Leppie on 2010-01-18
have checked your system for viruses?
you could install clamav (in the repos):
```
sudo apt-get install clamav clamtk
```

---

### Post by scottuss on 2010-01-18
This is on Ubuntu, right?

---

### Post by criptommy on 2010-01-18
yes in karmic koala

---

### Post by criptommy on 2010-01-18
> **scottuss said:**
> This is on Ubuntu, right?

> **Leppie said:**
> have checked your system for viruses?
you could install clamav (in the repos):
```
sudo apt-get install clamav clamtk
```
thanx lemme check

---

### Post by criptommy on 2010-01-19
the problem is still there even after deleting the files using the antivirus :(

---

### Post by Hazey on 2010-01-19
Hi,

are the text files empty?

Regards,
Hazey

---

### Post by Leppie on 2010-01-19
> **criptommy said:**
> the problem is still there even after deleting the files using the antivirus :(
did the antivirus notify you of viruses present on your system?

---

### Post by m4tic on 2010-01-19
april fools, hope itis. Are the folders on a windows partition or an EXT4partition

---

### Post by cascade9 on 2010-01-19
> **criptommy said:**
> DC downloads folder and Music folder. I havent observed in any other folders but it might be there. Not sure abt other folders

DC being 'direct connection'? If I recall correctly, there was a DC/DC++ virus that did just what your having happen....

---

### Post by MelDJ on 2010-01-19
do the files have names?

---

### Post by criptommy on 2010-01-19
> **Hazey said:**
> Hi,

are the text files empty?

Regards,
Hazey
yup
> **Leppie said:**
> did the antivirus notify you of viruses present on your system?
yes it detected all the exe files as trojans and deleted them
> **m4tic said:**
> april fools, hope itis. Are the folders on a windows partition or an EXT4partition
i didn understand. I dont have windows. Ubuntu in one single partition
> **cascade9 said:**
> DC being 'direct connection'? If I recall correctly, there was a DC/DC++ virus that did just what your having happen....
I dont think it has anything to do with DC. I didnt have any problem till a week ago when this started. Its also present in Music folder
> **MelDJ said:**
> do the files have names?
yup the text files are always named khv

---

### Post by scottuss on 2010-01-19
You're running this software with Wine?

---

### Post by criptommy on 2010-01-19
> **scottuss said:**
> You're running this software with Wine?
no i'm not its linuxdc++

---

### Post by Leppie on 2010-01-19
if it's only with dc/dc++ then uninstall it and don't use it anymore ;)
there's plenty of torrents around ;)
or are these files also created while not using dc/dc++?

---

### Post by john newbuntu on 2010-01-19
The next time you find a file that you suspect is a virus, upload it to 
[http://www.virustotal.com/](http://www.virustotal.com/)
It gets scanned by several AVs, just to get rid of false positives.

---

### Post by retro_killa on 2010-01-19
any p2p applaction is wonderful for getting bugs if you are into d/l files look into using IRC & go to [http://xdccing.com/](http://xdccing.com/)

---

### Post by criptommy on 2010-01-19
> **Leppie said:**
> if it's only with dc/dc++ then uninstall it and don't use it anymore ;)
there's plenty of torrents around ;)
or are these files also created while not using dc/dc++?
noooooo, DC++ is used for file transfer in LAN, yes i dont think these files have anything to do with it.
> **john newbuntu said:**
> The next time you find a file that you suspect is a virus, upload it to 
[http://www.virustotal.com/](http://www.virustotal.com/)
It gets scanned by several AVs, just to get rid of false positives.

> **retro_killa said:**
> any p2p applaction is wonderful for getting bugs if you are into d/l files look into using IRC & go to [http://xdccing.com/](http://xdccing.com/)
is there any way i can scan my computer and get rid of these bugs?? Virus Scanner didn't help :(

---

### Post by Leppie on 2010-01-19
> **criptommy said:**
> noooooo, DC++ is used for file transfer in LAN, yes i dont think these files have anything to do with it.



is there any way i can scan my computer and get rid of these bugs?? Virus Scanner didn't help :(
try other virus scanners, like avast, avg, fprot, kaspersky, etc.

---

### Post by criptommy on 2010-01-19
how do i install kaspersky or any other antivirus in Koala??

---

### Post by JustMarius on 2010-01-19
> **criptommy said:**
> how do i install kaspersky or any other antivirus in Koala??


maybe this will give ya a clue if not try to google something

[http://en.wikipedia.org/wiki/Linux_malware#Viruses_and_trojan_horses](http://en.wikipedia.org/wiki/Linux_malware#Viruses_and_trojan_horses)

---

### Post by SlugSlug on 2010-01-20
> **criptommy said:**
> how do i install kaspersky or any other antivirus in Koala??


get the deb from here

[http://www.avast.com/linux-home-edition#tab4](http://www.avast.com/linux-home-edition#tab4)

---

### Post by scottuss on 2010-01-20
Could you post screenshots / preferably video of this happening?

It's rather interesting to see something like this, if it is authentic.

---

### Post by Ordes on 2010-01-20
exe are mainly windows applications.. how they come onto your system?

i once read an article that it is possible for some windows viruses to become active under wine...

Are you running any windows software through wine?

---

### Post by criptommy on 2010-01-21
> **scottuss said:**
> Could you post screenshots / preferably video of this happening?

It's rather interesting to see something like this, if it is authentic.
[IMG]http://img260.imageshack.us/img260/3919/screenshotlf.png[/IMG]
khu, khv and khw are the text files and the three exe files are also there
> **Ordes said:**
> exe are mainly windows applications.. how they come onto your system?

i once read an article that it is possible for some windows viruses to become active under wine...

Are you running any windows software through wine?
i unistalled wine and all other windows programs long ago
Can somebody help me with AVG, i installed it but i am not able to find any icon to open the program

---

### Post by Ordes on 2010-01-21
never used avg on linux... might be command line only..

check 
$man avg 

[http://ubuntuforums.org/showthread.php?t=136064](http://ubuntuforums.org/showthread.php?t=136064)

if this is still true u can onlu scan with the free linux version. so no big use

avast for linux is terminal and gui..scans and removes viruses.

----
its kind of hard to follow your informations. i know now that u have three txt khu, khv khw and 3 exe. Nothing about their location behavior content etc. You should be more detailed so we can understand whats going on...

----
anyhow those 3 are all listed here
[http://www.softwaretipsandtricks.com/virus/page36](http://www.softwaretipsandtricks.com/virus/page36)
---

cant u just remove them by terminal?

sudo rm khu      [make sure u use the correct / full name, if khu.txt >$ sudo rm khu.txt ] 
or if they are all in one folder
sudo rm -r folder

what happens if u try to remove them through terminal?

sometimes it helps to rename them first and than delete

mv khu.txt file1
try sudo if it doesnt let u do it...
and than

rm file1
also use sudo if u dont have the permissions to remove

---

### Post by criptommy on 2010-01-21
thanx Ordes, all the files are empty and they dont cause any activity except for the fact they multiply. They are found only in the DC Downloads folder and Music folder

---

### Post by flabdablet on 2010-01-21
I don't think you'll find you have any actual malware running in your Linux box. What I suspect is happening is that there's an exploit in your download software, that somebody on the far end of it is attempting to use to inject malware into your system. Because they're only Windows executables, and you don't have Wine installed, there's no way for them to actually run on your Linux box. The fact that they're only appearing in the folders where you're downloading unsigned stuff from unknown places lends weight to this belief.

In fact, the exploit might not even be in your downloading software - it might be a straight social-engineering effort, where you download a rar file or some other kind of archive, expecting it to be music, and it actually contains these malware files either instead or as well. If your downloading software has some kind of automatic decompression or un-archiving feature, try turning it off. That way, you'll see these things spring into existence when you unpack a downloaded archive manually, and you'll know which file to avoid downloading again.

---

### Post by Ordes on 2010-01-21
yup.. sounds plausible...

can u find any pattern when they multiply.. e.g when using the download manager? or any other kind of behaving pattern..

---

### Post by scottuss on 2010-01-21
> **flabdablet said:**
> I don't think you'll find you have any actual malware running in your Linux box. What I suspect is happening is that there's an exploit in your download software, that somebody on the far end of it is attempting to use to inject malware into your system. Because they're only Windows executables, and you don't have Wine installed, there's no way for them to actually run on your Linux box. The fact that they're only appearing in the folders where you're downloading unsigned stuff from unknown places lends weight to this belief.

In fact, the exploit might not even be in your downloading software - it might be a straight social-engineering effort, where you download a rar file or some other kind of archive, expecting it to be music, and it actually contains these malware files either instead or as well. If your downloading software has some kind of automatic decompression or un-archiving feature, try turning it off. That way, you'll see these things spring into existence when you unpack a downloaded archive manually, and you'll know which file to avoid downloading again.

I was thinking something similar. I don't think that the fact that they are reappearing is the result of malware, I think that the P2P software is re-creating the files through an exploit in it rather than something else running on your box.

Remove DC Connect or whatever it's called and see if it still happens.

---

### Post by criptommy on 2010-01-21
> **Ordes said:**
> yup.. sounds plausible...

can u find any pattern when they multiply.. e.g when using the download manager? or any other kind of behaving pattern..
not really havent observed anything like that yet

---

### Post by criptommy on 2010-01-21
found out something now. I deleted all the files. I did run Linuc Dc++ but files didnt appear for a while. Suddenly an exe file and a text file appeared in DC Dpwnloads folder and the same two foles popped in Music folder also

---

### Post by flabdablet on 2010-01-21
I've just been reading up a little on dc++, and it appears that it uses two folders for downloads: one for unfinished files, and another for finished ones. I suspect that yours is set up to use DC Downloads for unfinished files, and Music for finished files, and that one or more of the files you've told dc++ to fetch for you are simply not the files you've been led to believe they are.

With dc++ running, cancel all outstanding downloads. Also have a look in its download queue; if there are still downloads waiting to complete, cancel those as well. Now stop dc++ again, delete the malware files, and restart dc++. Check its download queue again; There should not be anything in it. Leave it running like this, without starting any downloads at all, for longer than it has previously taken for the odd files to show up. My guess is that they won't.

If they *do* show up again, checking the dc++ download log should show you exactly where they came from and what they're claiming to be.

---

### Post by jamesisin on 2010-01-21
I use Transmission for BT.  I am able to look into each torrent and examine the files scheduled for up/download by opening the Properties for that torrent (in Transmission).  I should think you would be able to do something similar to locate which torrent included the files in question.

---

### Post by flabdablet on 2010-01-21
But dc++ isn't a bittorrent client, is it?

---

### Post by jamesisin on 2010-01-21
It's similar (in that it's p2p file sharing).  I was speculating about a way in which they are likely to share a property, namely the property to view the files which you are selecting in a meaningful way outside of your own file system.

---

### Post by steveneddy on 2010-01-21
So you are pirating those files you show in the screenshot?

What's in the occupation 101 folder?

---

### Post by criptommy on 2010-01-22
> **flabdablet said:**
> I've just been reading up a little on dc++, and it appears that it uses two folders for downloads: one for unfinished files, and another for finished ones. I suspect that yours is set up to use DC Downloads for unfinished files, and Music for finished files, and that one or more of the files you've told dc++ to fetch for you are simply not the files you've been led to believe they are.

With dc++ running, cancel all outstanding downloads. Also have a look in its download queue; if there are still downloads waiting to complete, cancel those as well. Now stop dc++ again, delete the malware files, and restart dc++. Check its download queue again; There should not be anything in it. Leave it running like this, without starting any downloads at all, for longer than it has previously taken for the odd files to show up. My guess is that they won't.

If they *do* show up again, checking the dc++ download log should show you exactly where they came from and what they're claiming to be.
And my finished downloads go to DC downloads and unfinished in Incomplete folder inside dC++. Music folder has nothing to do with DC++. Thats why i think these files have nothin to do with DC++ application
> **jamesisin said:**
> I use Transmission for BT.  I am able to look into each torrent and examine the files scheduled for up/download by opening the Properties for that torrent (in Transmission).  I should think you would be able to do something similar to locate which torrent included the files in question.
none of the files are infected. 
> **steveneddy said:**
> So you are **pirating those files** you show in the screenshot?

What's in the occupation 101 folder?
i didnt get you. Occupation 101 is a documentary

---

### Post by jamesisin on 2010-01-22
> **criptommy said:**
> none of the files are infected.

I think you misunderstand.  Suppose you have a download called "Really Important Software" and it contains files (seems plausible).  If you look at the list of files which represent that download, perhaps one of those contained files would be called "khw".

If DC++ is not running and the files DO NOT reappear, that ought to tell you something.

---

### Post by flabdablet on 2010-01-22
I have never used dc++ at all myself, so I may be way off base here, but I do recall that at one point the FireFTP extension for Firefox had a vulnerability involving filenames containing ../ sequences, and that a malicious FTP server could take advantage of this to store files basically anywhere it liked inside the client's filesystem (or, at least, anywhere the client's filesystem permissions gave it access to). So now I'm wondering what happens if an infected or otherwise malicious dc++ hub hands your dc++ client a filename like ../Music/yndovu.exe.

You say you're using dc++ for file transfers on the LAN. What are the chances that one of the dc++ hubs you're connected to is a virus-infected Windows box?

---

### Post by criptommy on 2010-01-26
Hey i think i found out the problem and solution myself!!!!!!! Both Music and DC Downloads where the folders shared by Linux DC++. So I moved all the important stuff from these two folders into different folders and deleted them. Now the newly shared folders dont have any problem. Thanx everybody for helpin out. :)

---

### Post by jamesisin on 2010-01-26
This sounds suspiciously like "I closed my eyes and it went away".

---

### Post by criptommy on 2010-01-26
The exe or text files are not being created in the new Downloads and Music folder. So i guess the problem is solved

---

### Post by jamesisin on 2010-01-26
You will want to mark the thread as SOLVED then (in Thread Tools above).

---

### Post by Leppie on 2010-01-26
> **jamesisin said:**
> This sounds suspiciously like "I closed my eyes and it went away".
well, if you can't see it it's not there, right? :P

---

### Post by jamesisin on 2010-01-26
> **Leppie said:**
> well, if you can't see it it's not there, right? :P

Absolutely.  Like the fabled ostrich (because the real ostrich is a bad-asp and wouldn't ever do that).

---

### Post by flabdablet on 2010-01-27
> **criptommy said:**
> The exe or text files are not being created in the new Downloads and Music folder. So i guess the problem is solved

I guess completely different. I guess all it's going to take is for the same Windows box that was originally responsible for foisting this crap on you to connect to the same hub as you at the same time, and back in those files will come, possibly with friends. However, I'm only guessing that because I'm a suspicious old curmudgeon. If you're happy, be happy :)

---

### Post by Leppie on 2010-01-27
> **flabdablet said:**
> I guess completely different. I guess all it's going to take is for the same Windows box that was originally responsible for foisting this crap on you to connect to the same hub as you at the same time, and back in those files will come, possibly with friends. However, I'm only guessing that because I'm a suspicious old curmudgeon. If you're happy, be happy :)
people are too used to the microsoft approach, the root cause will not be taken care of but instead we patch so that the annoying effect doesn't show anymore (but probably still is there).

---

### Post by cascade9 on 2010-01-29
> **flabdablet said:**
> i guess completely different. I guess all it's going to take is for the same windows box that was originally responsible for foisting this crap on you to connect to the same hub as you at the same time, and back in those files will come, possibly with friends. However, i'm only guessing that because i'm a suspicious old curmudgeon. If you're happy, be happy :)

+1. :)

---

