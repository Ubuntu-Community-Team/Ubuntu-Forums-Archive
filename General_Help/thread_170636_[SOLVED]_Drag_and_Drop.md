---
title: "[SOLVED] Drag and Drop"
date: 2006-05-05
forum: General Help
---

### Post by Cariboo1938 on 2006-05-05
I would like to Back-Up daily work, i.e. Office files, some music files , some pictures and so on, to a CD-R/W in the "Drag and Drop " manner, as I always can in Windows OS. There I use Nero Express and InCD to format the read/write CD accordingly. Is there a similar package for Linux systems?
Kindly
Juergen

---

### Post by C0n5ci3n53 on 2006-05-05
I am not sure that I fully understand what you want to do if you are looking for a cd-burner software which is a little like nero and allows drag-and-drop, try K3b. If this is not what you are looking then im sorry :D

---

### Post by deadgobby on 2006-05-05
[QUOTE=Cariboo1938]I would like to Back-Up daily work, i.e. Office files, some music files , some pictures and so on, to a CD-R/W in the "Drag and Drop " manner, as I always can in Windows OS. There I use Nero Express and InCD to format the read/write CD accordingly. Is there a similar package for Linux systems?
Kindly
Juergen[/QUOTE]
 Yes, Juergen you can use the basicly the same method. Install k3b from you synaptic. There is a option to make a data CD. Most likely when you run k3b the first time it wants to up date and should with no problem. Just go through the steps and you'll be burning cd's in no time flat. You can point and click the files you want to burn to disk. See [http://www.k3b.org/](http://www.k3b.org/) for screen shots and other tid bits.
Gobby

---

### Post by bluenova on 2006-05-05
You can drag and drop files into k3b as well.

---

### Post by Buffalo Soldier on 2006-05-05
[QUOTE=Cariboo1938]I would like to Back-Up daily work, i.e. Office files, some music files , some pictures and so on, to a CD-R/W in the "Drag and Drop " manner, as I always can in Windows OS. There I use Nero Express and InCD to format the read/write CD accordingly. Is there a similar package for Linux systems?[/QUOTE]

Using Ubuntu Dapper (still in beta, scheduled to release in June). Here how it is done, quite simple:[list]
[*] At the Top Panel (or taskbar in Windows-speak), clik **Places** -> **CD/DVD Creator**.

[*] Then CD/DVD Creator windows will appear. Just drag-and-drop any files into that windows.

[*] When you're done, just click **Write To Disc**. A small option window will pop up. I just use the default.

[*] Lastly click **Write**.[/list]

Can't remember the exact steps in Ubuntu Breezy, but it should be quite the same.

Attached are the approriate screenshots.

---

### Post by Irony on 2006-05-05
I think Cariboo1938 means can you write to a CD RW disc like you can to a floppy or a zip drive, not a write once (CD R) disc.

Breezy doesn't do RW discs, at least in not in RW fashion, hopefully that'll be solved in Dapper as it limits the external back-up options.

---

### Post by Cariboo1938 on 2006-05-05
[QUOTE=Irony]I think Cariboo1938 means can you write to a CD RW disc like you can to a floppy or a zip drive, not a write once (CD R) disc.

Breezy doesn't do RW discs, at least in not in RW fashion, hopefully that'll be solved in Dapper as it limits the external back-up options.[/QUOTE]

Sorry, that I couldn't express myself clear enough to all of you and....
Thank you Irony,
that exactly is, what I want to do --- handle a CD-R/W as it would be a floppy disk! ---
I try to leave Windows behind, but there, I was used to this kind of using CD-R/W's as a very convenient storage medium.

---

### Post by Cariboo1938 on 2006-05-05
[QUOTE=C0n5ci3n53]I am not sure that I fully understand what you want to do if you are looking for a cd-burner software which is a little like nero and allows drag-and-drop, try K3b. If this is not what you are looking then im sorry :D[/QUOTE]
> Originally Posted by Irony
I think Cariboo1938 means can you write to a CD RW disc like you can to a floppy or a zip drive, not a write once (CD R) disc.
Breezy doesn't do RW discs, at least in not in RW fashion, hopefully that'll be solved in Dapper as it limits the external back-up options.

that exactly is, what I want to do --- handle a CD-R/W as it would be a floppy disk! ---
I try to leave Windows behind, but there, I was used to this kind of using CD-R/W's as a very convenient storage medium.
Sorry, that I couldn't express myself clear enough....:D
Juergen

---

### Post by Cariboo1938 on 2006-05-19
Thank you Buffalo Soldier for the input!
Is it really possible whith Ubuntu Dapper to write a single file/directory to the CD-R/W without erasing the other content of the CD? If I have a blank CD-R/W, has it to be formatted first? 
Juergen :-k

---

### Post by jones_jj on 2006-05-19
Actually from what I've seen with Breezy, if you install Nautilus CD burner package from Synaptic, you will be able to drag and drop files onto a CD or DVD using the Nautalus file browser, just like you could do in XP with windows explorer.  I'm just not sure if it will work with RWs in the floppy fashion of writing and rewriting

---

### Post by aysiu on 2006-05-19
Nautilus in action:
[http://gnomejournal.org/article/6/cddvd-creation-with-nautilus](http://gnomejournal.org/article/6/cddvd-creation-with-nautilus)

---

### Post by mcduck on 2006-05-19
Most burning apps I've tried allow drag&drop, but I don't think there is any packet writing software for linux, at least I've never seen one.

But I never use packet writing anyway, because those CD's aren't guaranteed to work with other systems, and when I write a disk I want to be sure that it works on every machine, not just on my own..

edit: I did some searching with google, and I now believe that UDF disk format is supported, but I still didn't find any app that actually does packet writing with UDF..

[http://en.wikipedia.org/wiki/Universal_Disk_Format]("http://en.wikipedia.org/wiki/Universal_Disk_Format")

edit2: here's a Gentoo HowTo about packet writing: [http://gentoo-wiki.com/HOWTO_Packet_Writing_on_CD-RW]("http://gentoo-wiki.com/HOWTO_Packet_Writing_on_CD-RW")

---

### Post by Cariboo1938 on 2006-05-21
Thank you mcduck, aysiu,
I found the link   [http://gentoo-wiki.com/HOWTO_Packet_Writing_on_CD-RW](http://gentoo-wiki.com/HOWTO_Packet_Writing_on_CD-RW)  
too and the declared goal there is exactly what I was thinking would be cool to have:
 :cool:
> [COLOR="Blue"] 
[SIZE="3"]Goals[/SIZE]
After this, you will be able to write CD-RW as a big floppy disc. 
DVD-RW packet writing is functional as well with this configuration. 
[/COLOR]
Unfortunately I'm not a programmer, otherwise I would try to implement it to k3b or nautilus.
:rolleyes:

---

### Post by Cariboo1938 on 2006-05-24
I found a package named 'udftools'. It is a Debian package in test. Does anybody know how to use this tool for the CD-R/W usage like a large floppy?
](*,)

---

### Post by Cariboo1938 on 2006-05-25
I just found dradul's HOW-To Packet writing posted Feb.17th. Before I try this I have a question: Would it work on any Linux distro or is it specific for Ubuntu?

EDIT:
I wait until this (packet writing) issue is officially solved.....

---

