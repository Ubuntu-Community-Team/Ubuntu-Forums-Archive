---
title: "error 21 selected disc does not exist *GRUB*HELP*"
date: 2011-02-16
forum: General Help
---

### Post by fluffier on 2011-02-16
Hi everyone,

I need some help. I have laptop with one hard disk  and several partitions, one of them has Windows XP (but I am unable to  boot it), and another one has Ubuntu (wifiway) (I am able to boot it).

fdisk -l reports (i have omitted some info I believe it is not necessary):

disk /dev/hda: 40.0GB .......

Device Boot          System
/dev/hda1             NTFS
/dev/hda2             W95 Ext´d (LBA)
/dev/hda5             Linux
/dev/hda6             Linux swap

So I have one hard disk with four partitions (I guess)

my menu.lst file is like this: ( I have also omitted some info)

default = 0
timeout = 10
....

#Other bootable partition config begins
  title Windows
  root (hd0,1)
  makeactive
  map (hd0) (hd5)
  map (hd5) (hd0)
  chainloader +1
#Other bootable partition config ends
#Comienzo de la configuracion del grub para wifiway 2.X
title wifiway 2.X
root (hd0,4)
kernel /boot/vmlinuz root=/dev/hda5 ro vga=791
savedefault
#Configuracion del grub para wifiway 2.x terminada


My problem is that I am unable to boot my windows.
I have read some other posts and edited menu.lst in an attempt to solve the problem, in particular I have tried with 

root (hd0,2)
root (hd0,3)
root (hd1,0)

and others I cannot remember, and depending on my editing I get error 12, error 23, etc...

Does anybody know what my menu.lst has to look like in order for me to boot Windows?

Thank you!!!!!

---

### Post by oldfred on 2011-02-16
With old grub legacy your windows is in (hd0,0) and if you only have one drive you do not map. If you have boot flag on the windows partition you probably do not even need the make active.

Not sure if your system will run this, but if you want more info:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by fluffier on 2011-02-16
Wow, thanks for a really fast answer. As of now, for some reason I dont understand, I am unable to boot ubuntu, well I am but in a sort of "safemode" it told me to run a command which I did (fsdsk or something of the sort) and is now saying

node xxxxxxx is in use but has dtime set. fix(y)? yes
node xxxxxxx has imagic flag set. Clear(y)? yes
node xxxxxxx has compression flag set on filesystem without compression support. Clear (y) yes

and others and I have to keep pressing "y" all the time.

So I guess I will have to run a livecd... tomorrow. I am knackered.

Will let you know what happens, thanks again!!!!!!!!!!!!

---

### Post by psusi on 2011-02-16
That is not an Ubuntu generated menu.lst.  What is "wifiway"?  Also you mean fdisk listed **s**da, not hda right?  Hard drives have not shown up as hda in many years.

---

### Post by fluffier on 2011-02-17
Dear Oldfred,

It worked like a charm. You are a star!!!!!!!

@psusi:

[LEFT]Wifiway is a linux livecd designed for [www.seguridadwireless.net]("http://www.seguridadwireless.net/") adapted to the wireless with international support of languages.
It is not based in **debian**, **mandriva**, **fedora** and **slax**, bundle has developed for bundle thanks to the project [[COLOR=#0000ff]linuxfromscratch[/COLOR]]("http://www.linuxfromscratch.org/").[/LEFT]

I posted my question here because I had installed first ubuntu and later wifiway (on top the ubuntu partition, which is what I think f**** GRUB) and there were other questions similar to mine on this forum. I apologize if I did wrong.

---

