---
title: "Sharing files etc"
date: 2011-01-21
forum: General Help
---

### Post by rickhaden on 2011-01-21
Can someone point me towards real beginner issues? For instance, I have a number of drives attached internally and externally to the machine, which under windows I share across the network. Ubuntu is saying that I can't share because I haven't got some programs installed. What are those programs and how do you install such things?

Told you it was basic stuff...I am sure it is easy, but I am a windows man, eager to swap over if I can pick this stuff up...

Rick

---

### Post by chunky bacon! on 2011-01-21
Hi there.  I would imagine it is wanting you to install samba in order to share out folders.

Hope this helps you:

[https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide)

---

### Post by tredegar on 2011-01-21
To allow windows access to your linux filesystem, you need to install and use samba
I don't use samba but I think the following should get it for you:
```
sudo apt-get update
sudo apt-get install samba
```
There are lots of HOWTOs for samba. Here's [one]("http://www.unixmen.com/linux-tutorials/1060-how-to-configure-samba-using-a-graphical-interface-in-ubuntu")

---

### Post by nothingspecial on 2011-01-21
Yeah samba if you want to share to windows, unnecessary if everything is linux.

On a sidenote, I`d hop over to the resolution center and ask for a forum username change or you have a large chance of getting heavily spammed.

---

### Post by rickhaden on 2011-01-21
I gathered the fact that Linux expects the user to know what he is doing...sorry Linux...as for the sharing, when I go to private file sharing, it tells me that I am unable to share because there needs to be programs installed that aren't at present...I have said nothing about what I want to share to or from so how would it know I needed Samba?

Rooky Rick

---

### Post by nothingspecial on 2011-01-21
Rick,

Don`t take my sig personally, it says that at the end of all my posts.

So, what do you want to share?

From what and to what?

linux > windows?

linux > linux?

linux > windows/linux/mac?

---

### Post by Morbius1 on 2011-01-21
> when I go to private file sharingDo you mean Personal File Sharing?

You will need to install the following packages:
```
apache2.2-bin
libapache2-mod-dnssd
```Just so you know and in case anyone asks it sets up a baby apache file server and broadcasts its share using avahi. And it only allows you to share one folder - the "Public" folder in your home directory. Oh, and it has nothing to do with Samba.

---

### Post by rickhaden on 2011-01-21
Thanks for all that...but I am even more confused now...

I am trying to share a whole range of drives to Linux/mac OSX and Windows...and yes I did mean Personal file sharing...it was the only reference to sharing I could find...

Rick

---

### Post by Morbius1 on 2011-01-21
This is one of those instances ( perhaps the only instance ) where the best thing to do is make believe you're sitting in front of a WinXP machine and not a Linux machine:

Open Nautilus ( your Home folder )
Right click on a folder you own, like say ... Documents
Select "Sharing Options"

[COLOR=Blue]*If you don't have samba installed it will ask you if you want to install it. Of course it is not going to call it Samba because that would be too obvious so instead it calls it "Windows Networking" or something like that.*[/COLOR]

Select "Share this folder", "Allow others to create and delete..", "Guest Access".
Select "Create Share"
It will ask you if you want it to modify permissions - you do.

You just created a Samba share ( a specific type of samba share called Usershare ).

---

