---
title: "Samba V3.5.11 on Desktop 12.04"
date: 2012-06-04
forum: General Help
---

### Post by rubiconza on 2012-06-04
Hi guys

I am trying to share my *series* directory on my Ubuntu 12.04 desktop version with my mates at home.

They are all running Windows 7 Ultimate

My PC and my smb.conf

My PC has an extra drive installed and it is showing under media as Storage

so I have the following "directory"

/media/Storage/series

The ownership looks like this

> drwx------ 1 stefanv stefanv    4096 2012-01-29 11:31 series
As for my config file it looks like this

> 
[global]
    workgroup = workgroup
    netbios name = Babylon
    wins support = yes
    log level = 1
    max log size = 1000
    read only = yes
    security = user
    local master = yes
    preferred master = yes
    os level = 33
    guest ok = No
 
[homes]
    comment = %u's Home Directory
    path = /home/%u
    browsable = no
    read only = no

[Share]
    path = /share
    writable = yes
    browsable = yes
    guest ok = yes

[Series]
    path = /media/Storage/series
    browsable = yes
    guest ok = yes
I have an Ubuntu user called stefanv, I also have a virtual box  running inside my Ubuntu which has Windows 7 Ultimate on it.  The  username for my Windows 7 is also stefanv and the password on the ubuntu  and on the windows is exactly the same.

From my stefanv user on the Windows VM I can see my Samba Server  broadcasting my linux hostname (stefan-pc) instead of my netbios name  which is Babylon.  I can browse to it without suppling a username and  password which I take it is because I am set to user level security and  because both my usernames and passwords on both the machines are the  same.

Only problem I have is that I see my linux hostname and not my netbios name, any ideas why?

That was my first issue, now my second issue

Now I want to share my directories with my mates, but I don't want to  create physical users on my box for them, is there any other way I can  do it so that they just have "read" access to my files but without write  or execute capabilities?

On my Windows 7 VM I created another user called masterofdisaster, but I  didn't create a linux user for him, but sadly he can't even browse to  the server without supplying a username and password.

Any advice would be most welcome

---

### Post by gordintoronto on 2012-06-04
It's just not that complicated.

I assume you have an entry in fstab to mount the other hard drive.

Navigate until you can see the folder you want to share, right-click and select "sharing options." Set the ones you want.

Over the past year, I have tested at least a dozen distros/versions, and I always set up a shared folder. I have never edited a configuration file, I have never used the command line. It has worked 100% of the time.

From Windows 7, click on "computer," then "network" and follow your nose.

---

### Post by rubiconza on 2012-06-05
> **gordintoronto said:**
> It's just not that complicated.

I assume you have an entry in fstab to mount the other hard drive.

Answer: Yes

> Navigate until you can see the folder you want to share, right-click and select "sharing options." Set the ones you want.

Answer: I understand it is the easiest way to do it through the GUI, or using Webmin, but I plan on doing the same thing in the future but on a Server build, on which I will obviously not install X

So I would really love to know WHY:

Why my share name which uses the smb.conf file does not list my computer as Babylon

Why  my shares are accessible to linux users, but not to windows users

> Over the past year, I have tested at least a dozen distros/versions, and I always set up a shared folder. I have never edited a configuration file, I have never used the command line. It has worked 100% of the time.

Answer: The X-factor [sic]


> From Windows 7, click on "computer," then "network" and follow your nose.

Windows machines with usernames which were not created as linux system users can only see the resource (my PC name, not Babylon) but can't even access it, something about permissions

As you can see from my config the permissions is set so that guests can access the Share directory and my Series directory

Any other ideas in the mean while?

I am going to make a backup of my smb.conf file now,  remove the package, re-install the package, make use of the default smb.conf file and see if it works if I only add one of the guest shares.

Figure if I do it like that I can safely assume that my problem lies somewhere in my global options

---

### Post by Morbius1 on 2012-06-05
> As you can see from my config the permissions is set so that guests can access the Share directory and my Series directoryIf your clients are using Windows you have set your share to allow guest access but your server will not allow it because you decided to deviate from the default smb.conf.

Without the following line in the [global] section:
```
map to guest = Bad User
```The server defaults to:
```
map to guest = Never
```It would be better if you restored the original smb.conf and start over again than try to add back all the things that were removed. You also have a lot of share specific options in the [global] section which makes it difficult to figure out what's going on.

The other thing to keep in mind is that samba can match or remove permissions from the shared resource but it can’t add to them so make sure for example that /share has permissions of 777 or else the remote guest will never get write access.

---

### Post by Morbius1 on 2012-06-05
One more thing:
> so I have the following "directory"

/media/Storage/series

The ownership looks like this

     Quote:
                                                 drwx------ 1 stefanv stefanv    4096 2012-01-29 11:31 series                      /media/Storage smells like an ntfs partition based on those permissions so one way around this problem for that share is to change it to this:
> [Series]
path = /media/Storage/series
browsable = yes
[COLOR=Blue]**force user = stefanv**[/COLOR]
guest ok = yes The only person getting access to that directory is stefanv. "force user" will make the remote guest look like you.

---

### Post by rubiconza on 2012-06-05
@Morbius1

Thanks bud, you certainly have a good understanding of the Samba service! 

I am halfway there

I've commented out most of the lines which I think could cause havoc, please tell me if I am wrong

> root@stefan-pc:/# more /etc/samba/smb.conf 
[global]
    workgroup = workgroup
#    netbios name = Babylon
    wins support = yes
    log level = 1
    max log size = 1000
#    read only = yes
    security = user
#    local master = yes
#    preferred master = yes
#    os level = 33
    map to guest = bad user
    guest account = nobody
    create mask = 0644
    directory mask = 0755

[homes]
    comment = %u's Home Directory
    path = /home/%u
     browsable = no
    read only = no
    guest ok = no

[Share]
    path = /share
    writable = yes
    browsable = yes
    

[Series]
    path = /media/Storage/series
    writable = yes
    browsable = yes
    force user = stefanvdw    


I can now browse to the /media/Storage/series, but I can't create a directory

I've tried to chmod the /media/Storage directory to 777 but that didn't take either, I could also not change the ownership.

So it is still:

> drwx------ 1 stefanv stefanv    4096 2012-01-29 11:31 series 			 		

---

### Post by Morbius1 on 2012-06-05
> I can now browse to the /media/Storage/series, but I can't create a directory
Because the only one that can access that folder is stefanv
>  			 				drwx------ 1 **[COLOR=Blue]stefanv[/COLOR]** stefanv    4096 2012-01-29 11:31 series 			 		
And you forced the user to stefanvdw
> [Series]
    path = /media/Storage/series
    writable = yes
    browsable = yes
    force user = **[COLOR=Blue]stefanvdw[/COLOR]**     			 		
And if /media/Storage/series is sitting on an NTFS partition stop trying to do a chmod and chown it's not going to work.

---

### Post by rubiconza on 2012-06-06
> And if /media/Storage/series is sitting on an NTFS partition stop trying to do a chmod and chown it's not going to work.

Well, that solves my problem.  Thank you very much, I will get the data off the HDD and redo the drive in ubuntu

Thanks for all the help Morbius, much appriciated ... now I can move on to buillding a mail server with a web client and try and get spamassasin and ClamAV installed.

Keep well mate

---

