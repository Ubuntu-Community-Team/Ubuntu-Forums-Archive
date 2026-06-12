---
title: "Mirror Selection with apt-get"
date: 2009-12-27
forum: General Help
---

### Post by Mahngiel on 2009-12-27
Thought just crossed my mind...

For most all downloads these days, you are allowed to select a mirror to download your products from - even true for when you download via HTTP from ubuntu (canonical).

So when you use the terminal to 'apt-get', is there only one place these files are held?  Or is it possible to find a closer mirror for a better download?

---

### Post by The Secret on 2009-12-27
Open Software Sources ( System / Administration ) and use the server selection menu to change it.

---

### Post by scrooge_74 on 2009-12-27
in terminal the file is in 

/etc/apt/sources.list

---

### Post by Mahngiel on 2009-12-27
backtrack.

i found sources to edit, but no mirrors.

---

### Post by alphabravoxxx on 2009-12-27
First, find a Ubuntu mirror (I listed them for your convenience):
             *North America*
     
[LIST]
[*][mirrors.kernel.org/ubuntu]("http://mirrors.kernel.org/ubuntu")
[*][ftp.osuosl.org/pub/ubuntu]("http://ftp.osuosl.org/pub/ubuntu")
[*][lug.mtu.edu/ubuntu]("http://lug.mtu.edu/ubuntu")
[*][ubuntu.mirrors.tds.net/ubuntu]("http://ubuntu.mirrors.tds.net/ubuntu")
[*][ubuntu.secs.oakland.edu]("http://ubuntu.secs.oakland.edu")
[*][mirror.mcs.anl.gov/pub/ubuntu]("http://mirror.mcs.anl.gov/pub/ubuntu")
[*][mirrors.cat.pdx.edu/ubuntu]("http://mirror.mcs.anl.gov/pub/ubuntu")
[*][ubuntu.cs.utah.edu/ubuntu]("http://ubuntu.cs.utah.edu/ubuntu")
[*][ftp.ussg.iu.edu/linux/ubuntu]("http://ftp.ussg.iu.edu/linux/ubuntu")
[*][mirrors.xmission.com/ubuntu]("http://mirrors.xmission.com/ubuntu")
[*][mirrors.cs.wmich.edu/ubuntu]("http://mirrors.cs.wmich.edu/ubuntu")
[*][gulus.USherbrooke.ca/pub/distro/ubuntu]("http://gulus.USherbrooke.ca/pub/distro/ubuntu")
[/LIST]
                          *Asia*
     
[LIST]
[*][kr.archive.ubuntu.com/ubuntu]("http://kr.archive.ubuntu.com/ubuntu")
[*][th.archive.ubuntu.com/ubuntu]("http://th.archive.ubuntu.com/ubuntu")
[*][mirror.lupaworld.com/ubuntu]("http://mirror.lupaworld.com/ubuntu")
[*][kambing.vlsm.org/ubuntu]("http://kambing.vlsm.org/ubuntu")
[*][ubuntu.mithril-linux.org/archives]("http://ubuntu.mithril-linux.org/archives")
[*][mirror.in.th/ubuntu]("http://mirror.in.th/ubuntu")
[*][mirror.rootguide.org/ubuntu]("http://mirror.rootguide.org/ubuntu")
[/LIST]
                  *Africa*
     
[LIST]
[*][za.archive.ubuntu.com/ubuntu]("http://za.archive.ubuntu.com/ubuntu")
[/LIST]
             *Europe*
     
[LIST]
[*][cz.archive.ubuntu.com/ubuntu]("http://cz.archive.ubuntu.com/ubuntu")
[*][de.archive.ubuntu.com/ubuntu]("http://de.archive.ubuntu.com/ubuntu")
[*][dk.archive.ubuntu.com/ubuntu]("http://dk.archive.ubuntu.com/ubuntu")
[*][es.archive.ubuntu.com/ubuntu]("http://es.archive.ubuntu.com/ubuntu")
[*][fr.archive.ubuntu.com/ubuntu]("http://fr.archive.ubuntu.com/ubuntu")
[*][ge.archive.ubuntu.com/ubuntu]("http://ge.archive.ubuntu.com/ubuntu")
[*][gr.archive.ubuntu.com/ubuntu]("http://gr.archive.ubuntu.com/ubuntu")
[*][hr.archive.ubuntu.com/ubuntu]("http://hr.archive.ubuntu.com/ubuntu")
[*][mt.archive.ubuntu.com/ubuntu]("http://mt.archive.ubuntu.com/ubuntu")
[*][nl.archive.ubuntu.com/ubuntu]("http://nl.archive.ubuntu.com/ubuntu")
[*][no.archive.ubuntu.com/ubuntu]("http://no.archive.ubuntu.com/ubuntu")
[*][se.archive.ubuntu.com/ubuntu]("http://se.archive.ubuntu.com/ubuntu")
[*][yu.archive.ubuntu.com/ubuntu]("http://yu.archive.ubuntu.com/ubuntu")
[/LIST]
                  *Australia and New Zealand*
     
[LIST]
[*][nz.archive.ubuntu.com/ubuntu]("http://nz.archive.ubuntu.com/ubuntu")
[*][nz2.archive.ubuntu.com/ubuntu]("http://nz2.archive.ubuntu.com/ubuntu")
[*][ftp.iinet.net.au/pub/ubuntu]("http://ftp.iinet.net.au/pub/ubuntu")
[*][mirror.optus.net/ubuntu]("http://mirror.optus.net/ubuntu")
[*][ftp.filearena.net/pub/ubuntu]("http://ftp.filearena.net/pub/ubuntu")
[*][mirror.pacific.net.au/linux/ubuntu]("http://mirror.pacific.net.au/linux/ubuntu")
[/LIST]
           
                 
             Open a terminal window (Applications->Accessories->Terminal on GNOME, Applications->System->Konsole on KDE)

USERNAME@HOSTNAME:~$ sudo nano /etc/apt/sources.list
Password: (enter your password)

You should see something like this (my sources.list file on GNOME), click to enlarge:
[[IMG]http://img684.imageshack.us/img684/1682/18084355.th.png[/IMG]]("http://img684.imageshack.us/i/18084355.png/")

Now, you can change the mirrors (lug.mtu.edu/ubuntu in my example) to different ones, like (example) mirror.optus.net/ubuntu

- AlphaBravo

---

### Post by Mahngiel on 2009-12-27
aaah, i see. my apologies for not understanding in the first place. thanks AlphaBravo for making it barney-style. *kudos*

so i'll just find+replace 'ttp://us.archive.ubuntu.com/ubuntu/' with the mirror i wish.

---

