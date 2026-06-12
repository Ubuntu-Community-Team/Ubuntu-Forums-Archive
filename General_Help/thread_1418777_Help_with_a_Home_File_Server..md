---
title: "Help with a Home File Server."
date: 2010-03-01
forum: General Help
---

### Post by sam3317 on 2010-03-01
I've tried to set up a home file server using 9.10 Karmic and [http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver)
I've tried to adjust it with help from the posts at the end of Pg. 3 but I just cannot get it to work.

Has anyone got any advice as too what you would need to do different in 9.10 or could you point towards a more suitable tutorial?

---

### Post by johnofwax on 2010-03-01
Hello Sam, and welcome to the Ubuntu forums!
What is it that you're not able to get to work? What adjustments were you trying to make?
I ran into a few hiccups sharing folders across the network with the right-click "Share" menu options, but after using samba instead I haven't had any issues. I've been running shares from 3 HDs on my Ubuntu desktop to the rest of my network (close enough to a file server for me to answer you, I guess) without any issues.
 
If you could be more specific about what's going on, maybe we can figure it out together.
 
Are you not seeing the shares on your computer when accessing it from another PC?
Are you not getting a response from your computer, period?
Are you getting denied access, or the user:pass your typing in isn't working?
Are you running firestarter or another iptables configuration gui ?
Just throw some details into the thread and I'm sure we can figure it out.

---

### Post by sam3317 on 2010-03-01
Well maybe it's something simple so i'll just tell you what's happening. On my windows box the ubuntu server appears in my windows workgroup as
my server name(Samba, Ubuntu)(my server name)
if I double click it takes me to \\my server name with \sdb public hard disk and \printers and faxes. if I then double click \sdb public hard disk my windows box hangs.
It also hangs if I try to map \\my server name\sdb public hard disk as a network drive in my computer.

---

### Post by sam3317 on 2010-03-01
When I try to map \\my server name\sdb public hard disk as a network drive I get an error 
"The mapped network drive could not be created because the following error has occurred:
The specified network name is no longer available."

Oh and thanks for the welcome.

---

### Post by jahst on 2010-03-01
Never had much luck with Samba... and since I don't use Windows for anything anymore, I don't miss messing with it.

There was something I always had to change in a text file.. winbind and hosts.. something like that. Granted I usually went from Ubuntu to Windows... but might want to do some searches for these and see if anything helps out.

I did always find it helped to use IP rather than host name.

\\xxx.xxx.x.xx\sdb

Give that a shot...

Also try pinging the machine.. to see if one machine can even talk to the other.



Otherwise , if you just want to share files between Ubuntu Machines I recommend this post for setting up NFS.

Made my life so much easier .. NFS is super easy and fast to setup.

[http://ubuntuforums.org/showthread.php?t=249889&highlight=NFS]("http://ubuntuforums.org/showthread.php?t=249889&highlight=NFS")

sorry can't help more.

---

### Post by johnofwax on 2010-03-01
Sorry it took so long for me to get back, been a bit busy.
I believe jahst hit the nail on the head. I'd bet money on your firewall being the issue. I was just reading something yesterday about this...
[Samba and Firestarter - The real story]("http://ubuntuforums.org/showthread.php?t=190542")
I actually have the same issue when accessing my shares from my Xbox. I have to turn off my firewall on my desktop (really not a big issue here. 4 PCs and an Xbox behind IPCop, w/ Mac Filtering and WPA on the dd-wrt)  However, to address that issue, I went on a hunt. The above link is what I found. 
Supposedly it only takes 1 line in the iptables ruleset to fix the issue... check out the link.

Also, did requesting the IP instead of the name circumvent the issue?  I haven't tried it yet.

Edit:
With it "Hanging", you may be blocking the connection.
Try using FireStarter to allow connections from your windows box.
Also, I use Samba to do my shares... I tried using the gnome-menu "Sharing" options before, but that didn't really work so well for me. There is also a Samba GUI to make life easier, if you don't want to be bothered with the smb.conf file.  As my boss would say "It just *works*."

---

