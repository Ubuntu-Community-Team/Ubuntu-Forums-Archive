---
title: "Sharing Automounted Windows Drive - Is this method OK??"
date: 2012-08-27
forum: General Help
---

### Post by 777funk on 2012-08-27
I just automounted my windows drive in Ubuntu 12.04. Works good. Now I have to go to MNT to find the Windows directory. A little inconvenient to find the folder but... so be it. Glad to have it automounted!

But when I went into sharing options I was getting:
> add: cannot share path /media/disk/disk as we are restricted to only sharing directories we own.
    Ask the administrator to add the line "**usershare owner only = False**" 
    to the [global] section of the smb.conf to allow this.[SIZE=3]So... I hit Alt-F2 and added that line to the Global section of the smb.conf file.[/SIZE]

Now I can share whatever I want. BUT is that safe? I'd like to make sure I keep Windows happy too just incase I need it.




[SIZE=1]From[ this thread]("http://ubuntuforums.org/archive/index.php/t-958457.html"), this guy had another way... but it didn't work for me for some reason like what I did. Here's his way:
[/SIZE]> [SIZE=1]Smb.conf is located in /etc/samba. THe easy way is Alt-F2 and type
gksu gedit /etc/samba/smb.conf[/SIZE]The method I used ("**usershare owner only = False**" ) worked great, but I want to make sure it's safe.

---

### Post by Rexilion on 2012-08-27
I think it would allow others to share ***_your_*** home directory and (probably) see it's contents.

I suggest you just change the owner :lolflag:

---

### Post by Mark Phelps on 2012-08-27
From experience, any "sharing" of a Windows NTFS filesystem that involves a partition containing the Vista/Win7 OS files is asking for trouble.  Vista/Win7 use a newer version of NTFS that is really sensitive to filesystem changes from "outside" -- which is exactly what you're doing if you share a folder in that partition and then allow changes to files.

A much "safer" option is to create a sharable Data partition and put all the files you want to share in that.  Since that partition doesn't have OS files, there is no risk over it not being bootable.

---

### Post by Rexilion on 2012-08-27
> **Mark Phelps said:**
> From experience, any "sharing" of a Windows NTFS filesystem that involves a partition containing the Vista/Win7 OS files is asking for trouble.  Vista/Win7 use a newer version of NTFS that is really sensitive to filesystem changes from "outside" -- which is exactly what you're doing if you share a folder in that partition and then allow changes to files.

A much "safer" option is to create a sharable Data partition and put all the files you want to share in that.  Since that partition doesn't have OS files, there is no risk over it not being bootable.

Huh, I thought that Windows XP, Vista and 7 all use NTFS 3.1 so there would be no trouble. Only when another version of Windows finds OS version specific files in a location where the other OS would write to as well.

Could you elaborate on this? I'm curious.

---

### Post by Cheesemill on 2012-08-27
I've come across the situation several times where accessing the Windows system drive from Ubuntu has left Windows in an unbootable state. And not by doing anything silly like deleting system files either, just reading user files has caused this problem for me before.

As Mark Phelps said it's far safer to use a shared NTFS data partition if you want access to files from both OS's.

---

### Post by 777funk on 2012-08-27
> **Cheesemill said:**
> I've come across the situation several times where accessing the Windows system drive from Ubuntu has left Windows in an unbootable state. And not by doing anything silly like deleting system files either, just reading user files has caused this problem for me before.

As Mark Phelps said it's far safer to use a shared NTFS data partition if you want access to files from both OS's.

Sounds like a good idea. So what do I do in GParted to accomplish this without damaging either file system (or my stored files)?

---

### Post by Morbius1 on 2012-08-27
> add: cannot share path /media/disk/disk as we are restricted to only sharing directories we own. Ask the administrator to add the line "**usershare owner only = False**" to the [global] section of the smb.conf to allow this.                                 [SIZE=3]

So... I hit Alt-F2 and added that line to the Global section of the smb.conf file.[/SIZE]

Now I can share whatever I want. BUT is that safe? I'd like to make sure I keep Windows happy too just incase I need it.By default creating Samba shares from nautilus allows any user to share anything [COLOR=Blue]**he owns**[/COLOR] to the rest of the network. When you tried as a normal user to share /media/disk/disk you must have run into a problem that you do not own the mounted ntfs partition. 

There's 3 ways around this problem:

** Change how you are mounting the ntfs partition so that you own it.

** Run Nautilus as root ( gksu nautilus ) since root owns everything.

** Add "**usershare owner only = False**" as you have done to smb.conf.

The only issue with what you have done comes about if you have multiple local login users on that box. You don't want to give UserB the ability to share UserA's folders. If you are the only user then it's not an issue.

---

### Post by Morbius1 on 2012-08-27
> **777funk said:**
> Sounds like a good idea. So what do I do in GParted to accomplish this without damaging either file system (or my stored files)?
Unless I completely misunderstood the original post going into gparted is not necessary. Everyone else is interpreting this to be an ntfs mounted permissions issue.

I interpreted this to be a Samba file sharing issue.

---

### Post by Rexilion on 2012-08-27
@Morbius1, please read the entire thread. Some users have bad experiences sharing a partition formatted with NTFS with a Linux and a Windows system. We are way past the permission restrictions for mount sharing.

@777funk, always back-up first. Then shrink a partition and create a new one in it's space or copy your files to another partition and share them there. The most elegant solution would be to create a seperate 'data' NTFS partition so that Windows is happy too. And then share that NTFS partition as it does not contain system files/important security settings et all.

---

### Post by Morbius1 on 2012-08-27
> **Rexilion said:**
> @Morbius1, please read the entire thread. Some users have bad experiences sharing a partition formatted with NTFS with a Linux and a Windows system. We are way past the permission restrictions for mount sharing.
Is that why no one answered his original question? The one relating to Samba?

---

### Post by Rexilion on 2012-08-27
> **Morbius1 said:**
> Is that why no one answered his original question? The one relating to Samba?

Second post of mine, besides he already answered the question you answered again. People to prevent people from answering :) .

---

### Post by Morbius1 on 2012-08-27
> Second post of mine, besides he already answered the question you answered again. People to prevent people from answering :smile: .     > Huh, I thought that Windows XP, Vista and 7 all use NTFS 3.1 so there  would be no trouble. Only when another version of Windows finds OS  version specific files in a location where the other OS would write to  as well.

Could you elaborate on this? I'm curious.     Ah yes, I can clearly see now how your second post talks about Samba, network file sharing, and whether or not "usershare owner only = False" is safe.

My mistake :p

---

