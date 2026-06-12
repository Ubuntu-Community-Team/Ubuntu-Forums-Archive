---
title: "about win xp"
date: 2009-12-29
forum: General Help
---

### Post by James Dee on 2009-12-29
Hello,

I want to made image of the windows partition. There are software like ghost norton, image bla bla bla... and procedure is not so complicated but it is not also so easy.
I have one idea to do it from ubuntu, but I'm not sure is it ok.
From ubuntu is possible to see windows partition and all files and directories on this partition. Is this truth?
I can select all files and directories and compress them. The new compress file I can store somewhere on the hard disk or dvd. And if I will have some problems with windows, I can format windows partition with liveCD and uncompress the compress file on the new formated partition.
And this is it? I have fresh clean windows installation on the computer.

---

### Post by RodGer GR on 2009-12-29
I think that the only data you could not just copy this way from a windows installation, would be the windows bootloader from the mbr. But, since you have grub in your mbr, and boot windows using grub, I think that all the needed files can be copied and buckuped the way you described. 

However, this is just an assumption. I'm not sure. If anyone is sure about what would happen, please let us know.

---

### Post by kevinatkins on 2009-12-29
In this situation, I'd be tempted to use 'Partimage Is Not Ghost' (PING) which is similar to Norton Ghost and can be downloaded for free from -

[http://ping.windowsdream.com/](http://ping.windowsdream.com/)

It's not overly difficult to use, although you will need to carefully read the documentation before proceeding.

You are correct that from Ubuntu it is possible to see all the files / directories on the Windows partition, and it might be possible to manually create an image from within Ubuntu, but PING would be easier I think. 

If you use PING, you'll need somewhere to store the image - either a network share, or perhaps a spare partition / location on your existing hard drive.. 

Good luck!

---

### Post by James Dee on 2009-12-29
> **kevinatkins said:**
> In this situation, I'd be tempted to use 'Partimage Is Not Ghost' (PING) which is similar to Norton Ghost and can be downloaded for free from -

[http://ping.windowsdream.com/](http://ping.windowsdream.com/)

It's not overly difficult to use, although you will need to carefully read the documentation before proceeding.

You are correct that from Ubuntu it is possible to see all the files / directories on the Windows partition, and it might be possible to manually create an image from within Ubuntu, but PING would be easier I think. 

If you use PING, you'll need somewhere to store the image - either a network share, or perhaps a spare partition / location on your existing hard drive.. 

Good luck!


i will try with ping.
thnx.

---

### Post by howefield on 2009-12-30
> **James Dee said:**
> I want to made image of the windows partition. There are software like ghost norton, image bla bla bla... and procedure is not so complicated but it is not also so easy.

I'd offer up Clonezilla, very reliable.

Downside being that it is "not so complicated but it is not also so easy" however, by following the defaults and reading what is in front of you, you wouldn't be long in sussing it out.

---

