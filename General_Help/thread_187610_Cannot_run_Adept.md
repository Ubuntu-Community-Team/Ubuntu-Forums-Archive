---
title: "Cannot run Adept?"
date: 2006-06-03
forum: General Help
---

### Post by King Blah on 2006-06-03
I am trying to run the Adept Update Manager, and whenever I open it I get an error saying the database is locked probably because it is being used by another program. However I have no programs open. How do I fix this?

---

### Post by King Blah on 2006-06-03
I tried entering this random command that someone else tried and it worked:

sudo dpkg --configure -a

No idea what it does, just seems like a load of random letters to me but at least it worked!

---

### Post by King Blah on 2006-06-03
Uh, another problem now:

> There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages. 

I get this error whenever I try downloading/removing or anything in Adept..
Please can someone help! I've tried searching but absolutely nothing people have suggested seems to be helping. I've tried running sudo apt-get upgrade and update but that does absolutely nothing to help. And i can't stand using the command line to install packages either, it's horrible. Please can someone help?!

Edit: I am going to keep editing this post as people will think I am being helped by seeing lots of replies. I tried typing in "sudo apt-get remove" and the following appears:
>  Reading package lists... Done 
Building dependency tree... Done
E: The package vmware-player needs to be reinstalled, but I can't find an archive for it.
Is this causing the problem?

---

### Post by gingermark on 2006-06-03
[QUOTE=King Blah]Uh, another problem now:
I get this error whenever I try downloading/removing or anything in Adept..
Please can someone help! I've tried searching but absolutely nothing people have suggested seems to be helping. I've tried running sudo apt-get upgrade and update but that does absolutely nothing to help. And i can't stand using the command line to install packages either, it's horrible. Please can someone help?![/QUOTE]
Can you post the contents of your sources.list file please (located in /etc/apt),

---

### Post by King Blah on 2006-06-03
Here it is:
> 

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe 
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse 
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe 


---

### Post by dresnu on 2006-06-03
Are you getting this error while trying to upgrade or while installing a particular package?

---

### Post by gingermark on 2006-06-03
It's not a repository problem. Have you been manually downloading and installing individual .deb files willy nilly? Maybe one that are not meant for Ubuntu?

EDIT: And don't keep editing your post, post again instead, otherwise folks won't know when you've read what they post.

---

### Post by King Blah on 2006-06-03
I have not downloaded any individual files at all. I haven't downloaded anything without using adept. I am getting this problem while trying to update/remove/install ANY package.

---

### Post by dresnu on 2006-06-03
So if you try to run these two commands in a console:```
sudo apt-get update
sudo apt-get upgrade
```
you get no errors?

---

### Post by gingermark on 2006-06-03
Sorry mate. I just remembered that I had the same problem on a brand new Dapper RC install of Kubuntu. And I'm sitting here trying to remember how I fixed it!

---

### Post by King Blah on 2006-06-03
If i run apt-get update, here's what I get:
```
Get: 1 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get: 2 http://gb.archive.ubuntu.com dapper Release.gpg [189B]
Get: 3 http://gb.archive.ubuntu.com dapper-updates Release.gpg [189B]
Hit http://security.ubuntu.com dapper-security Release
Hit http://gb.archive.ubuntu.com dapper Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://gb.archive.ubuntu.com dapper-updates Release
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://gb.archive.ubuntu.com dapper/main Packages
Hit http://gb.archive.ubuntu.com dapper/restricted Packages
Hit http://gb.archive.ubuntu.com dapper/main Sources
Hit http://gb.archive.ubuntu.com dapper/restricted Sources
Hit http://gb.archive.ubuntu.com dapper-updates/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://gb.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://gb.archive.ubuntu.com dapper-updates/main Sources
Hit http://gb.archive.ubuntu.com dapper-updates/restricted Sources
Fetched 3B in 0s (8B/s)
Reading package lists... Done
```

And apt-get upgrade:
```
Reading package lists... Done
Building dependency tree... Done
E: The package vmware-player needs to be reinstalled, but I can't find an archive for it.
```

I get that error message, although I said that before in one of my posts before.

---

### Post by gingermark on 2006-06-03
Right, vmware-player is in the multiverse repository, which you don't have enabled by default.

So, in Konsole do
```
kdesu kate /etc/apt/sources.list
```

Then remove the '#' symbols that are in front of any line that begins 'deb'.

Then do a 'sudo apt-get update' or "fetch updates" or whatever it is in Adept, and see if it then works.

---

### Post by dresnu on 2006-06-03
Try this command: ```
sudo dpkg -P vmware-player
``` and then try updating and upgrading again.

EDIT: sorry gingermark for getting in your way, we seem to reply simultaneously :-D

---

### Post by King Blah on 2006-06-03
If i try doing that command gingermark just said, lo and behold another error message:
> X Error: BadDevice, invalid or uninitialized input device 155
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 155
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


PS: It is taking me a long time to reply because my internet is cutting off every 5 minutes, yet another problem with kubuntu. I have to keep restarting my router every 5 minutes, hopefully i'll get this resolved as i have opened another topic about it in networking.

---

### Post by King Blah on 2006-06-03
I get this error if i try sudo dpkg -P vmware-player:
```

dpkg: error processing vmware-player (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 vmware-player

```

---

### Post by King Blah on 2006-06-03
Well, thanks for the help but it looks like this isn't going to be resolved...

---

### Post by King Blah on 2006-06-07
Does no one know the answer to this? I STILL have this problem... I can't download anything through Adept!

Edit: Endless problems! "Add or Remove programs" will also not open, the cursor changes to an hourglass and after about 2 minutes of "loading" it just closes. Everything just seems to be not working, what the hell has happened to this installation? It just seems to muck up constantly, I really need some help. I feel like I am talking to myself!

---

### Post by xtacocorex on 2006-06-07
[QUOTE=King Blah]
X Error: BadDevice, invalid or uninitialized input device 155
Major opcode: 146
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 155
Major opcode: 146
Minor opcode: 3
Resource id: 0x0
Failed to open device[/QUOTE]

That's just something with the X-server. I get that on some programs too, but that's minor, at least IMO. 

When you open Adept, do you have apt-get trying to do something at the same time? If you do, that could be why you were getting the error saying that the database is locked. 

Are all the repos enabled in your sources.list file? 

From what I read in your other thread, you are on wireless. If you can, do this from the command line:
```
sudo apt-get install wifi-radar
```

When it is done installing, run it with:
```
sudo wifi-radar
```
You may get that X error again, but don't worry. The program will scan for wireless networks and then if you click on yours and then click to connect, it'll make a config for it and will automatically set the card up to use that on boot. I did this to stop my wireless card from disconnecting every 15 minutes on my laptop, I think I had misconfigured it in the command line somewhere.

Just remember that the people who are helping out have other obligations and may not get a response to you as fast you may like. It also comes down to how you ask the question. If you search for some of the threads I've started, you'll see that I have a couple that aren't answered by anyone but me, why, because I had very technical questions that no-one had the knowledge base for. I'm not trying to flame, but just asking you to be patient.

---

