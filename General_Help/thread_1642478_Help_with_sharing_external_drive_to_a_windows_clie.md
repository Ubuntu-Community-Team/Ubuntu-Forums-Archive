---
title: "Help with sharing external drive to a windows client"
date: 2010-12-10
forum: General Help
---

### Post by AmazonasGrun on 2010-12-10
Hello, I'm very very new to Linux.  I'm trying to share a USB external hard drive on my dell laptop running ubuntu 10.10 with a windows client on my home LAN.  I'm able to share folders on the laptop's internal hard drive, but so far I'm not successful with the external drive. I can see the dell laptop from "my network places", but I'm unable to select it to open any of the folders or drives that are shared.  I can get to it by "run  \\IP Address", and then I can see the icons for the folders that are shared on dell hard drive and I can see the icons that I've shared on the external drive.  However, I can only access those that are shared on the dell drive.  When I try to access the shared folders on the external drive, I get a message that tells me that I do not have permissions. 

I've read the following thread:
[http://ubuntuforums.org/showthread.php?t=1376114&highlight=sharing+external+drive&page=3](http://ubuntuforums.org/showthread.php?t=1376114&highlight=sharing+external+drive&page=3)

Here's my usershare info:

jpcapoc@jpcapoc-Inspiron-1000:/media$ net usershare info
[pictures]
path=/home/jpcapoc/Pictures
comment=
usershare_acl=Everyone:F,
guest_ok=y

[my book]
path=/media/My Book
comment=External Drive
usershare_acl=Everyone:F,
guest_ok=y

[pics]
path=/media/My Book/Pics
comment=
usershare_acl=Everyone:F,
guest_ok=y

[documents]
path=/home/jpcapoc/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y

I now am trying to modify the smb.conf file per Morbius1's suggestion.
I found three versions of the smb.conf file in three different directories:

/etc/samba
/usr/share/doc/nautilus-share/examples
/usr/share/samba

In all three, I don't see the section below that Morbius1 is suggesting to be deleted.  They all appear to be "sample" files.

Here's Morbius1's suggestion from the thread referenced above:

"(1) Get rid of the "Classic Samba" share in smb.conf:

 	Quote:
 	 	 		 			 				[SIZE=2][share]
comment = Ubuntu File Server Share
path = /media/SEA_DISC/Petermanfiles
read only = No
create mask = 0755
guest ok = Yes 			 		[/SIZE] 	 	 
[SIZE=2](2) Add **force user = blake** to the [/SIZE][SIZE=2][COLOR=Blue][global][/COLOR][/SIZE][SIZE=2] section of smb.conf[/SIZE]"

Which of these three files should I be editing?

When I open the files with a text editor, it says "read only".  How do I get permission to edit?

Again, I'm an extreme novice.  Help is appreciated!!

Thanks,

John

---

### Post by AmazonasGrun on 2010-12-12
bump   Can anybody help?

---

### Post by luvshines on 2010-12-12
> **AmazonasGrun said:**
> bump   Can anybody help?

You'll have to modify the /etc/samba/smb.conf file.

Also, you'll have to first open it with sudo and then edit, something like```

# Assuming you are using vim editor. From terminal, use this command
sudo vim /etc/samba/smb.conf
```

---

### Post by AmazonasGrun on 2010-12-13
> **luvshines said:**
> You'll have to modify the /etc/samba/smb.conf file.

Also, you'll have to first open it with sudo and then edit, something like```

# Assuming you are using vim editor. From terminal, use this command
sudo vim /etc/samba/smb.conf
```

I'm a novice, I'm not familiar with the vim editor.  I typed "vim man" and here's what I got:

The program 'vim' can be found in the following packages:
 * vim
 * vim-gnome
 * vim-tiny
 * vim-gtk
 * vim-nox
Try: sudo apt-get install <selected package>

I presume this means I don't have the vim editor.  Can I do it with the text editor?  When I open the file with the text editor, it says "read only".

Also, there is no "[share]" section in the /etc/samba/smb.conf file.  Do I just add the line 
force user = jpcapoc
to the global section?

Thanks!

---

### Post by luvshines on 2010-12-13
> **AmazonasGrun said:**
> I'm a novice, I'm not familiar with the vim editor.  I typed "vim man" and here's what I got:

The program 'vim' can be found in the following packages:
 * vim
 * vim-gnome
 * vim-tiny
 * vim-gtk
 * vim-nox
Try: sudo apt-get install <selected package>

I presume this means I don't have the vim editor.  Can I do it with the text editor?  When I open the file with the text editor, it says "read only".

Also, there is no "[share]" section in the /etc/samba/smb.conf file.  Do I just add the line 
force user = jpcapoc
to the global section?

Thanks!

You can use any editor. Just start it from command line with sudo as prefix :) (say sudo gedit, sudo nano etc...)

And for the [share], it's just a notation
Like in your case possible values for [share] will be - [pictures], [documents], [my book], [pics] ...
So you should add 'force user = jpcapoc' under those [share] section whose path is pointing to external NTFS drive paths ( I guess in your case it shud be under [pics] and [my book], ie those having path as /media/...)

---

### Post by AmazonasGrun on 2010-12-13
Thank you luvshines.  It works!  Bonus:  I learned a few things!  :p

---

