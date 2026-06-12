---
title: "Ubuntu Linux Live 5.04 (Hoary) i386 BETA 4"
date: 2005-02-19
forum: General Help
---

### Post by wsg on 2005-02-19
I have a CD labelled "Ubuntu Linux Live 5.04 (Hoary) i386 BETA 4"...

It boots fine...But I can't locate ANYWHERE on it a TOOL to configure a dial up modem.

Any help??

(I also note that with Firefox page opened, it mentions "Welcome...Warty Warthog Release".  Does that indicate that I've got the wrong CD?)

Thanks...

---

### Post by wsg on 2005-02-22
Really would like to know the answer to this... ](*,) 

Where's the dialup config tool?

Thanks to anyone who might comment...

---

### Post by Smurf on 2005-02-23
There Isn't one, thats why I droped it. I had to do a pppsetup just to find my hardware modem, then after that I could not find a way to dial out! People just told me to download Modem Lights. why? If this is so easy and n00b friendly why jump thru the hoops? But I have to say what I did see I liked and this is the best Gnome I havev ever seen! 8)

---

### Post by wsg on 2005-02-23
Thanks for your reply...

 :roll: It's hard to believe that Ubuntu could omit a dial-up tool... :roll: 

But if that's the way it is, I'll also have to forget it... :-x

---

### Post by GilGalad on 2005-02-23
What about "sudo pppconfig" (should be in the cd) and then "pon" or "poff" to connect, disconnect. 

However the tool I most use for dial out is gnome-ppp (not in the cd but in universe).

---

### Post by wsg on 2005-02-23
> gnome-ppp (not in the cd but in universe). 
Thanks for that tip...

Can you please 'point' me to where I should go to find it?

Thanks from a newbie...

---

### Post by GilGalad on 2005-02-23
Just add 

```

deb http://archive.ubuntu.com/ubuntu/ hoary universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hoary universe multiverse

```

to your /etc/apt/sources.list. Run synaptic, update and search for gnome-ppp. It should be there.

---

### Post by wsg on 2005-02-23
[QUOTE=GilGalad]Just add 

```

deb http://archive.ubuntu.com/ubuntu/ hoary universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hoary universe multiverse

```

to your /etc/apt/sources.list. Run synaptic, update and search for gnome-ppp. It should be there.[/QUOTE]
 Well, GilGalad...I think I goofed by not explaining that I'm running exclusively from the LiveCD with no hard disk drive in my webstation...only USB flash drives.

It has 1GHz processor and 256MB RAM.

I guess my setup won't allow me to add gnome-ppp.

Thank you for your kind help...

---

