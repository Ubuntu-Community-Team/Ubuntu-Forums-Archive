---
title: "Wifi option to view Videos on Android phone"
date: 2012-10-14
forum: General Help
---

### Post by Gordonisnz on 2012-10-14
Hello.

i have videos on my PC (ubuntu).

i have an android phone.

I tried something called EMIT (but couldn't connect / get a PIN number etc..)

i tried Rygel & something called UPnPlay 

when I loaded UPnPlay on my android phone, I can scan / view my files already on my phone (but couldn't see my Videos on my PC).

When I ran Rygel, I got this :-

> 
$ rygel
Rygel-Message: New plugin 'MediaExport' available
MediaExport-Message: 'file:///home/gordon/Music' harvested
MediaExport-Message: 'file:///home/gordon/Videos' harvested
MediaExport-Message: 'file:///home/gordon/Pictures' harvested


Q1. How do i know Rygel is actually working ? (I have some videos in my 'videos' directory)

Q2.  how do i tell my android UPnPlay to find my PC ? It didn't ask for an IP address or password or anything.


Q3. Is there a dummies-guide to installing (something) that will allow me to view my PC videos using my android phone over WIFI?

In the EMIT programme i downloaded a bunch of files (in a contained file/compacted)

but I know how to use the command line to install things - but don't know how to install programmes from a GZ archive. Thanks

---

### Post by jensgeorg on 2012-11-22
> **Gordonisnz said:**
> Hello.

i have videos on my PC (ubuntu).

i have an android phone.

I tried something called EMIT (but couldn't connect / get a PIN number etc..)

i tried Rygel & something called UPnPlay 

when I loaded UPnPlay on my android phone, I can scan / view my files already on my phone (but couldn't see my Videos on my PC).

When I ran Rygel, I got this :-



Q1. How do i know Rygel is actually working ? (I have some videos in my 'videos' directory)

Q2.  how do i tell my android UPnPlay to find my PC ? It didn't ask for an IP address or password or anything.


Q3. Is there a dummies-guide to installing (something) that will allow me to view my PC videos using my android phone over WIFI?

In the EMIT programme i downloaded a bunch of files (in a contained file/compacted)

but I know how to use the command line to install things - but don't know how to install programmes from a GZ archive. Thanks

Please try a different UPnP client on your phone like TwoPlayer or BubbleUPnP. UPnPlay is a) horrible and b) doesn't really like Rygel and this is is not fixable from our side since it doesn't identify itself.

You don't need to tell it anything, that's the "magic" in UPnP, they'll find each other. Just make sure you don't have a firewall on the PC running Rygel.

---

### Post by Gordonisnz on 2012-11-22
> **jensgeorg said:**
> Please try a different UPnP client on your phone like TwoPlayer or BubbleUPnP. UPnPlay is a) horrible and b) doesn't really like Rygel and this is is not fixable from our side since it doesn't identify itself.

You don't need to tell it anything, that's the "magic" in UPnP, they'll find each other. Just make sure you don't have a firewall on the PC running Rygel.

I've got (installed) BubbleUpNp on my Mobile (Samsung GT-56500D ). 

Are there any 'instructions' on how to set it up ? my mobile ph says a 'server' is needed in the settings - however i've googled & can't find out how to set it up.
(I tried [http://192.168.1.86](http://192.168.1.86) etc - I used IFCONFIG) - didn't work.


Do I need to install anything on my PC (1 website i found mentioned "windows" - i'm on Ubuntu - obviously).

I'll look more in the weekend when I have more time.

---

### Post by jensgeorg on 2012-11-23
> **Gordonisnz said:**
> I've got (installed) BubbleUpNp on my Mobile (Samsung GT-56500D ). 

Are there any 'instructions' on how to set it up ? my mobile ph says a 'server' is needed in the settings - however i've googled & can't find out how to set it up.
(I tried [http://192.168.1.86](http://192.168.1.86) etc - I used IFCONFIG) - didn't work.


Do I need to install anything on my PC (1 website i found mentioned "windows" - i'm on Ubuntu - obviously).

I'll look more in the weekend when I have more time.

If I remember correctly your PC should appear there automatically if you run rygel and don't have a firewall running. I don't have an android device available at the moment to check.

There might be a slight issue with the network interfaces depending whether you use network manager or not. If you run rygel from the console with

G_MESSAGES_DEBUG=all rygel -g 5

that should tell us if that's the case.

---

### Post by Statia on 2012-11-23
BubbleUpNp has a server for Linux as well.
I actually have the file on my PC, but haven't installed it yet.

---

