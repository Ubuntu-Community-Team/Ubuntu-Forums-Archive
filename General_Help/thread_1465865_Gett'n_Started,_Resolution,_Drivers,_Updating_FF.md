---
title: "Gett'n Started, Resolution, Drivers, Updating FF"
date: 2010-04-29
forum: General Help
---

### Post by luky on 2010-04-29
hi there all ....
Re: Ubuntu 9.10
1st and foremost ...
a big thank you to all for being here!
im **NEW **to the family and the world of Ubuntu & im having a very hard time getting started.
i have been googleing but honestly im very tired now and i have'nt made any progress. :(
i have recently acquired both ....
Ubuntu Pocket Guide-v1-1
Ubuntu Kung Fu
i will be reading through them. 
 
my comp. is an [HP Compaq dc7600 Small Form Factor PC]("http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c00376254&lang=en&cc=us&taskId=101&prodSeriesId=472277&prodTypeId=12454") (Please see attachment for all the specifics that i got in Ubuntu using "sudo lshw")
since i started to play around with Ubuntu last week .....
[COLOR=red]**=**[/COLOR] i_*have not* _been able to fix the screen resolution 
_**[COLOR=red]-[/COLOR]**_ i *_have not_* been able to learn how to update firefox
_[COLOR=red]**-**[/COLOR]_ also if i installed Ubuntu the way described [here w/ (Wubi Installer)]("http://wubi-installer.org/faq.php"), do i need to install another antivirus program for Ubuntu?
 
Regarding the screen Resloution ...
[IMG]http://i489.photobucket.com/albums/rr252/foto-pix/Ubuntu/Screenshot-DisplayPreferences.png[/IMG]
[IMG]http://i489.photobucket.com/albums/rr252/foto-pix/Ubuntu/Screenshot-HardwareDrivers.png[/IMG]

---

### Post by don_xvi on 2010-04-29
grrr
I'm looking myself because 10.04 STILL doesn't correctly detect my max resolution, nor does it seem to offer a simple way to manually input my desired resolution.

Take a note for the future and you can google "x.org monitor configuration line generator"  It gets you to this website that you can enter your desired screen parameters into and it gives you a line to copy & paste into your xorg.conf.  The problem is that I think they did away with that and need to do more searches around here myself to remind myself of how this all works.  Anyways, here's the website:
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

Poke around on how to generate a manual xorg.conf in 9.10.

It's disappointing that this is this still (1) broken and (2) so difficult to override.
I'm sure it's been a release or two now that have had hard times detecting what resolution to set or allow, why not make it easy to tell the system manually?

---

### Post by luky on 2010-04-29
ill have a look at that - its kinda late now - so i gotta call it quits for the night but thanks again.
ps.
if youre more familiar with the forum than me ....
where would one see the attachment that i attached when i created the post ?
i dont see it anywhere.
thanks again

---

