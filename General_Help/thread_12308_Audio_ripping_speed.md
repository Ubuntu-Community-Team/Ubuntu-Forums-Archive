---
title: "Audio ripping speed"
date: 2005-01-23
forum: General Help
---

### Post by chombee on 2005-01-23
I finally got SoundJuicer to rip mp3's. I had the feeling that my slow ripping speed was due to ogg encoding, but apparently not. With Ubuntu, on two seperate computers, I get audio ripping speeds of around 1.0x with Ogg or mp3 encoding, and with SoundJuicer or another app such as Grip.

These computers should be able to rip a music cd in under a minute or so, not in one hour! Is there a solution?

Thanks,
Sean

---

### Post by chombee on 2005-01-25
No one? It happens on more than one machine for me, is anyone else experiencing this?

---

### Post by ctt1wbw on 2005-01-25
How did you get it to rip cd's?  I tried and it gave me an error about a codec or something...

---

### Post by chombee on 2005-01-25
Sorry, it just worked with Ogg or FLAC. To get it ripping mp3 I had to download an RPM of gstreamer0.8-lame because apt-get wouldn't install it (one of the dependencies was version xxx-ubuntu and it needed version xxx), and I couldn't get it to build from source either. I converted the RPM to deb with alien. After that ripping just worked. You should post your error message in another thread.

---

### Post by ctt1wbw on 2005-01-25
thanks, I think I will do that.  And as for the alien thing, I might have to wait.  I ain't quite ready for that yet!  :grin:

---

### Post by mudra on 2005-04-21
I have the same problem with GRIP. I cannot get a faster speed than 1.0x for ripping a  CD. On my lower spec PC with a vanilla debian install and slower CD Drive I get much better speeds.

Any help on this would be greatly appreciated.

Mudra

---

### Post by chombee on 2005-04-21
[QUOTE=mudra]I have the same problem with GRIP. I cannot get a faster speed than 1.0x for ripping a  CD. On my lower spec PC with a vanilla debian install and slower CD Drive I get much better speeds.

Any help on this would be greatly appreciated.

Mudra[/QUOTE]
 I have found that changing 'paranoia' to 1 in GConf in Apps->SoundJuicer puts my ripping speed up from < 1.0x to 3.0x-4.0x. With Grip, there are various error checking options for cdparanoia, if I disable all the checking I can get the speed up to 9-10x.

What I want though is a modern GUI like SoundJuicer, GooBox or even KAudioKreator ripping at full speed of around 40x.

I am starting to think that cdparanoia is simply a slow (but focus on high quality, lots of error checking) tool for cd ripping and encoding. What I might need to do is use eg.: lame instead (I think maybe lame encodes but does not rip, so would need to be combined with something else).

Lame should be easy enough to install and use in Grip so I might be able to try it soon, but I'd want a proper modern Gnome app configured to use Lame (or something fast) ideally.

I still cannot confirm, despite asking everywhere, whether this extremely slow ripping is normal Ubuntu behavior (in which case the default CD Ripping setup needs changed) or a problem with the machines I've tried.

---

### Post by doclivingston on 2005-04-21
If your CDs are scratched at all the ripping (using cdparanoia) will take a *long* time. This is because it will re-read the cd several times trying to correct the errors caused by the scratches (which is what cdparanoia is designed to do). The other possibility is that a dodgy CD drive which is returning wrong information about whether the CD sector was read correctly, so cdparanoia has to re-read it to check - although I personally haven't seen any CD drives that do this in the last few years.

If you turn the paranoia level down it will go quicker, but might have sounds glitches, due to misreads of the CD. I normally get around 10x in both grip and sound-juicer on unscratched CDs.

---

