---
title: "Samba keeps asking for password"
date: 2010-05-03
forum: General Help
---

### Post by Sciamano on 2010-05-03
Hi, I'm having problems with SAMBA after upgrading to Lucid Lynx.

I use samba to access a shared folder on my PC with my xbox (to view videos on my TV using XMBC). It's a closed network so there are no security issues involved, so I don't want to have to insert user/pwd to access the shares.

Everything used to work perfectly, but now after upgrading to Lucid when I try to access the shares, the system asks for the password. What's worse is that it does not work even if I insert a user/pwd combo (correct and set up with smbpasswd -a USERNAME)

Here is my old smb.conf which worked:

```

[SHARES]
path = /home/luca/Shares
comment = /home/luca/Shares
guest ok = yes
writable = yes
public = yes
only guest = yes
guest account = nobody
browsable = yes
```

I've also tried this without success:

```

[SHARES]
path = /home/luca/Shares
comment = /home/luca/Shares
available = yes
writable = yes
browseable = yes
public = yes
```

adding guest ok = yes does not solve.

Also, in the Authentication section of smb.conf, I've tried both:

security = user

and

security = share

but none worked. Keeps asking for password and rejecting entry even though username/pwd are correct.

Any help would be very much appreciated.
Thanks!!

---

### Post by Sciamano on 2010-05-06
Am I the only one who has problems with samba??

---

### Post by John Bean on 2010-05-06
> **Sciamano said:**
> Am I the only one who has problems with samba??

Probably not, but Samba problems seem to have few (if any) simple answers in my (limited) experience of it. If I didn't know better I'd think its a deliberate ploy to discourage contact with Windows machines... :-(

Come on you Samba wizards, prove me wrong and help the OP at the same time ;-)

---

### Post by Morbius1 on 2010-05-06
Sciamano, please post the output of the following commands:

```
net usershare info
testparm -s
```

---

### Post by Sciamano on 2010-05-06
First of all, thanks for helping!

Here are the results of the commands:
```
luca@desktop:~$ net usershare info
[2010/05/06 14:10:20,  0] param/loadparm.c:7472(lp_do_parameter)
  Ignoring unknown parameter "wide symlinks"
[2010/05/06 14:10:20,  0] param/loadparm.c:5745(lp_bool)
  lp_bool(no #in some cases works with yes): value is not boolean!
```


```
luca@desktop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Unknown parameter encountered: "wide symlinks"
Ignoring unknown parameter "wide symlinks"
lp_bool(no #in some cases works with yes): value is not boolean!
WARNING: The "printer admin" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[SHARES]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        obey pam restrictions = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 50
        unix extensions = No
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        comment = Server
        path = /home/luca/SHARES
        invalid users = root
        valid users = nobody, Gast, luca, Administrator, xbox, @users, @lpadmin                                      
        printer admin = @lpadmin
        read only = No
        guest ok = Yes

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No
        browsable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[SHARES]
        comment = /home/luca/Shares
        valid users = luca, xbox
```

---

### Post by Morbius1 on 2010-05-06
First, My apologies. I didn't realize until now that you're using kubuntu.

net userhsare info is "Simple Sharing" or "Nautilus-share" and is a Gnome thing so don't worry about that error.

As for your testparm output and it's warning's I'm debating with myself whether it's best to try to fix your existing smb.conf or just start over.  May I ask where or how this was generated? Did you roll your own or is this the result of some GUI app? You've got a lot of things that don't usually belong in the global section.

And you did say that your original intent was to create a public share that required no username and password to access right?

In the meantime can you confirm whether or not you have a file at this location ( sorry, not that familiar with KDE anymore ): 

/usr/share/samba/smb.conf

I'm in and out of the forum this morning so this may take a while.

---

### Post by Sciamano on 2010-05-06
There is no hurry at all, the important thing is to come to a solution even though it takes a while. Moreover, I'm at work now, so I don't have access to the home PC, where the problem is.
Regarding your questions: I made the smb.conf myself following a few tutorials I've found on the net. It very probably is not "adherent" to the correct syntax, but it has worked perfectly until the upgrade to Lucid, so it did its job :)

My intent is exactly the one you wrote: to create a public share that requires no username and password to access.
The only extra feature requested is that the share must support symbolic links. This is due to the fact that I often need to add directories to my share, so I've created a shared folder (/home/luca/Shares) in which I add symbolic links to the folders I need to share, that reside on different disks and partitions. 

No problem in writing a new smb.conf from scratch, the important thing is that it works again! :)

I'll check (and report back) about the existence of the file /usr/share/samba/smb.conf as soon as I get back home.

Again, thanks for your time.
Luca

---

### Post by Morbius1 on 2010-05-06
Your mention of symbolic links made me think ( it's rare but it does happen ). There was(is ?) a security problem with samba and symlinks:
[http://www.samba.org/samba/news/symlink_attack.html](http://www.samba.org/samba/news/symlink_attack.html)

The workaround was to add the following to the [global] section of smb.conf:

```
follow symlinks = yes
wide links = yes
unix extensions = no
```In looking at your testparm it appears you have:
> unix extensions = noYou do not have:
> follow symlinks = yesAnd you have a testparm error:
> Unknown parameter encountered: "wide symlinks"
Ignoring unknown parameter "wide symlinks"
It should be:
```
wide links = yes
```Hopefully this is all that's wrong. Let us know.

---

### Post by sites on 2010-05-06
Have you tried the following commands?

sudo smbpasswd -a <username>

sudo smbpasswd -e <username>

---

### Post by Sciamano on 2010-05-06
First of all, I checked the existence of /usr/share/samba/smb.conf and it's right there.

I've corrected the 'wide links' syntax error (+ restarted smbd) but I'm still being asked for username/password :(

I've created and enabled a user called "xbox" but nothing changed. Also don't forget that I want to be able to access shares without the need of authentication.

---

### Post by Sciamano on 2010-05-06
UPDATE: I tried using my "old" [Shares] section and now I can get into the shared folder without the system asking for authentication.
Only problem is the xbox now does not see the symlinks that should lead it to the actual shared folders. :(

BTW, the line "follow symlinks = yes" is right there, I don't know why testparm does not show it.
Here is the part, which is in my global section of smb.conf:
```
# Unix Extensions
# If disabled it should allow symbolic links in shares

follow symlinks = yes
wide links = yes
unix extensions = no #in some cases works with yes
```

Now this is even funnier. Just to see what would happen, I appended the line 'follow symlinks = **yes**' to my [SHARES] section.
Look what testparm says now:
```
[SHARES]
        comment = /home/luca/Shares
        guest only = Yes
        follow symlinks = **No**
```

---

### Post by Morbius1 on 2010-05-06
I just noticed something else. Are you sure this worked before?

You're missing one parameter that allows the creation of a guest user:
```
map to guest = bad user
```It's the only way for a non authenticated remote user to be converted to the default user: ***nobody***

In your original share definition you had "guest account = nobody" which is the default BTW, but without "map to guest" there's no way to get there.

You also have all these valid users which is somewhat confusing:
>         valid users = nobody, Gast, luca, Administrator, xbox, @users, @lpadmin                                      You only have one guest share why are there any valid users. You shouldn't have any users.

---

### Post by Sciamano on 2010-05-06
> **Morbius1 said:**
> I just noticed something else. Are you sure this worked before?
I've been using this smb.conf since Ubuntu Dapper Drake and I've been watching my tv shows on the Xbox since then. :)

> 
You're missing one parameter that allows the creation of a guest user:
```
map to guest = bad user
```It's the only way for a non authenticated remote user to be converted to the default user: ***nobody***

Ok, I will add this, but in what section should it go?
Although, if I may point this out, the problem is not accessing the shares anymore, since it actually seems resolved, but following the symlinks, which do not work anymore :(
**EDIT:** Correction: I can't access the shares anymore. This is pretty strange! And confusing!!

> You also have all these valid users which is somewhat confusing:
You only have one guest share why are there any valid users. You shouldn't have any users.

I guess they were there in the beginning. I only added me (luca) and xbox to try if this way it would work. 
Anyway, how should this line look? Do I delete everything after the = ?

---

### Post by Morbius1 on 2010-05-06
map to guest should be in the global section.

You know, rather than make changes to something that once worked you might want to think about an entirely different approach. Make a backup copy of what you have now and start over with a fresh smb.conf. [B][I]Just a suggestion:
[/I][/B] 
Make a backup of your current smb.conf:
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
```Copy the "reserve" copy to take it's place:
```
sudo cp -a /usr/share/samba/smb.conf /etc/samba/
```There's a mistake in the reserve copy that needs to be corrected:

Look for **encrypt passwords = false** and change it to **true** or **yes**

Add the following symlink corrections to the global section:
```
follow symlinks = yes
wide links = yes
unix extensions = no

```Then add a very simple share:
```
[SHARES]
path = /home/luca/Shares
read only = no
guest ok = yes

```Restart samba:
**sudo service smbd restart**
**sudo service nmbd restart**

[COLOR=Blue]EDIT:[/COLOR] Run **testparm -s** to check for errors

If it doesn't work you can always restore the original.

---

### Post by garvinrick4 on 2010-05-06
gksudo gedit /etc/samba/smb.conf  
 
Find this section in the file:  
 ####### Authentication #######  
 # &#8220;security = user&#8221; is always a good idea. This will require a Unix account  
 # in this server for every user accessing the server. See  
 # /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html 
 # in the samba-doc package for details. 
 #security = user  
 

 Uncomment the security line, and add another line to make it look like this:  
 security = user  
 username map = /etc/samba/smbusers

---

### Post by Sciamano on 2010-05-06
@Morbius1: tried with a "clean" smb.conf but solved only partially (I can access /Shares but don't see the symlinked folders).

@garvinrick4: tried your solution too, but nothing changed. Can access the Shares but it looks empty. :(

---

### Post by pricetech on 2010-05-06
Have you looked at:
[http://www.jonathanmoeller.com/screed/?p=1590](http://www.jonathanmoeller.com/screed/?p=1590)

The only step I needed was to run smbpasswd since everything was installed, but it worked for me.

---

### Post by Sciamano on 2010-05-07
> **pricetech said:**
> Have you looked at:
[http://www.jonathanmoeller.com/screed/?p=1590](http://www.jonathanmoeller.com/screed/?p=1590)

The only step I needed was to run smbpasswd since everything was installed, but it worked for me.

Yes I followed that tutorial too, but it didn't solve my problem. :(
Thanks anyway.

---

### Post by Morbius1 on 2010-05-07
I've reproduced your problem on a freshly installed Ubuntu 10.04 Gnome. I added a share and everything works. Then I added a symlink to that share and the client can access and see everything except the symlinked folder. The "fixes" - follow symlinks, wide links, and unix extensions - did nothing. Searching the web indicated that the "fixes" should have worked so there is some step that you and I are not doing but I don't know what that is at the moment.

I do have a workaround though if you absolutely - positively have to have symlinks work. I will show you how I did mine as an example:

I have two folders in my home directory : Public - that I want to share, and TEMP - that I want to link to Public

I created a Public share that matches yours and like yours it works perfectly. The client user can access the share without a username and password prompt:
> [Public]
path = /home/morbius/Public
read only = no
guest ok = yesFrom here on things get "exotic" :wink:

*** Step 1: Create a TEMPLink directory within Public:***
```
mkdir /home/morbius/Public/TEMPLink
```***STEP 2: Install bindfs:***
```
sudo apt-get install bindfs
```***STEP 3: "Bind" TEMP to TEMPLink in Public in fstab:***

Add the following line to /etc/fstab:
```
bindfs#/home/morbius/TEMP /home/morbius/Public/TEMPLink fuse perms=0777
```This will create a TEMPLink folder in Public that will retain the ownership of the TEMP folder but set permissions to 777 which will allow read write access to guests ( among others ). You could also set it at perms=0755 which will give remote users read only access. It all depends on your requirements.

*** STEP 4: Force fstab to rerun to capture the new fstab entry:***
```
sudo mount -a
```This will work although it's certainly not as easy as creating a symlink.

_ Usage notes:_
(1) Every "bind" in fstab will create a desktop icon which could get a little messy depending on how many you have.
(2) Since it's in fstab it will automatically unmount at shutdown. To force a unmount before shutdown you'll have to issue the following command:
```
sudo umount /home/morbius/Public/TEMPLink
```(3) To make a temporary link without fstab, the sytax in a terminal changes a bit:
```
sudo bindfs -o perms=0777 /home/morbius/TEMP /home/morbius/Public/TEMPLink
```OTHER NOTES:
If you followed the suggested link at: 
[http://www.jonathanmoeller.com/screed/?p=1590](http://www.jonathanmoeller.com/screed/?p=1590)
undo all the changes you made to the share definition. You had a working public share ( other than the symlinks ). There is no need to make it private by adding a "valid users" option. 

In the end though you have to ask yourself what is easier, doing what I've outlined above or simply create another share for TEMP.

[COLOR=Blue]EDIT:[/COLOR] I will continue to try and figure out why the wide links/no unix extensions thing fixes this problem with symlinks for everyone on the web except you and I.

---

### Post by Sciamano on 2010-05-07
Thanks Morbius1, I will try your solution, although in my /home/luca/Shares I have at least 12 symlinked folders (those that don't work) and setting all them up this way looks like a huge task. But I might start with just those few folders I absolutely need, until a proper solution is found.

Regarding the linked tutorial, I've already reverted all the changes it suggests, since they did not work for me.

It's pretty strange that symlinks don't work for you and me, although I find it hard to believe that no one else is experiencing this inconvenience. Maybe guest access (with no credentials given) has been made incompatible with the follow symlinks option?

I don't know. What's sure is that if giving credentials solved this problem, I might as well put up with it, but during all my tries I've never been able to pass beyond the username/password request window, since the system acted like they were wrong.

If you want, and have the time, we can try this way (I'm not sure I made every step correctly, so it might be useful to have your supervision).

Thanks again for your time and help.
Luca

P.S.: you are right, the easier solution probably would be to create a new share for every folder. I might end up doing this, after all.

---

### Post by Morbius1 on 2010-05-07
> P.S.: you are right, the easier solution probably would be to create a new share for every folder. I might end up doing this, after all.Not that I'm trying to make you a convert to Gnome or anything but in Gnome it's easy to create samba shares and it doesn't involve creating shares in smb.conf. It can be done from the file manager in 4 mouse clicks and can be undone in 2. Don't even have to restart samba. ;)

---

### Post by Sciamano on 2010-05-07
> **Morbius1 said:**
> Not that I'm trying to make you a convert to Gnome or anything but in Gnome it's easy to create samba shares and it doesn't involve creating shares in smb.conf. It can be done from the file manager in 4 mouse clicks and can be undone in 2. Don't even have to restart samba. ;)

I know, I use Gnome on my laptop, but I'm bound (=used) to different programs on my desktop (I could never live without KTorrent, Akregator, K3b and KRename, for example, which I barely use on my laptop instead).
I could easily switch back to Gnome but I've never found a good RSS aggregator. Liferea really isn't good enough for me and RSSOwl is made in Java, and it's too heavy for my taste.

Anyway creating shares used to be equally easy in KDE too. Clicking on a folder's properties you could select the options for sharing. I don't know why but since I upgraded to Lucid, this does not work anymore. I'm on another computer now and I can't remember the exact error, but it seems like some program that used to enable this, has been removed (if I give the same command in the terminal I receive the "command not found" error). :confused:

Edit: anyway, shares (and symlinks to folders) should work regardless of the desktop environment one might want to use. I find it pretty annoying that right now I have to go back to my windows partition in order to have those shares seen by my xbox!

---

### Post by Sciamano on 2010-05-08
Now, this is getting very frustrating.

I've moved all the folders I want to share (and I mean physically moved, not linked) to the same hard disk which is /media/Storage). This way, I thought, I can simply share all the disk and I'm set.

So I've added this share to the smb.conf:

[Storage]
path = /media/Storage/
read only = no
guest ok = yes

But I can't access anything this way either.
Browsing the share with Dolphin I get "The file or folder smb://desktop/Storage does not exist."

:confused:

---

### Post by Morbius1 on 2010-05-08
From the Ubuntu Machine post the output of the following command: **smbtree**

---

### Post by Sciamano on 2010-05-08
> **Morbius1 said:**
> From the Ubuntu Machine post the output of the following command: **smbtree**

```
luca@desktop:~$ smbtree
Enter luca's password: 
WORKGROUP
        \\DESKTOP                       desktop server (Samba, Ubuntu)
                \\DESKTOP\Xerox_Phaser_6130N    Xerox_Phaser_6130N
                \\DESKTOP\IPC$                  IPC Service (desktop server (Samba, Ubuntu))
                \\DESKTOP\Storage        
                \\DESKTOP\SHARES         
                \\DESKTOP\print$                Printer Drivers

```

---

### Post by Sciamano on 2010-05-08
BTW, I installed ubuntu-desktop (=Gnome) and when I try to share folders (for example /media/Storage) from Nautilus, I get to this point:

> Nautilus needs to add some permissions to your folder "Anime" in order to share it
The folder "Anime" needs the following extra permissions for sharing to work:
  - read permission by others
  - write permission by others
  - execute permission by others
Do you want Nautilus to add these permissions to the folder automatically?

Cancel / Add permissions automatically

I click on Add permission automatically and I get this error:

> Could not change the permissions of folder "Anime"

There definitely is something wrong here...
Can the problem be that /media/Storage owner and group are root : plugdev? 
The fact is tha /media/Storage is a mounted NTFS hard drive.

Here is the respective line in the fstab (I copied it from a tutorial, because I don't understand well the fstab syntax. Do I need to change anything?):
```
UUID=1AC62C5CC62C3B01 /media/Storage	ntfs defaults,umask=007,gid=46,noatime 0 0
```

---

### Post by Morbius1 on 2010-05-08
>  The fact is tha /media/Storage is a mounted NTFS hard drive.BINGO !

Samba says allow guests. Linux file permissions says "No guests allowed". Nothing overrides linux file permissions.

You've got two choices:

(1) Change the umask in fstab to : **umask=000**

OR

(2) Add the following line to the [Shares] definition in smb.conf:

```
force user = luca
```Then restart samba

---

### Post by Morbius1 on 2010-05-08
Just checking up on things. 

A note on the "force user" line: it's your local login user name. There's no need to create an smbpasswd for "force user". There's really never any need to create an smbpasswd for the server owner.

What "force user" will do is create a mask that will convert all remote users to you - for that share. It doesn't give them total access to your machine, only for that share and only under the constraints of the linux permissions and samba authorizations.

---

### Post by Sciamano on 2010-05-08
**Yesss! It worked!**
Sorry for the delay but I was not home...
Anyway I've quickly tried adding both the umask and the force user tricks and now I can browse the symlinks. Tomorrow I'll revert things and try just one of the two solutions at a time and see which one works best.

Just a consideration: the NTFS drive was an EXT3 drive when I started this quest. I converted to NTFS because I needed to access the data from Windows too, but the various EXT2IFS drivers worked only partially. This is to say that when I upgraded to Lucid, both the fstab and the smb.conf were the same I had in Karmic, when things with samba worked perfectly.
Also, in the fresh installation you tried, you encountered the same problem, and I guess your share was not on an NTFS drive.

Therefore I guess something in samba has been changed, although we ignore what it is.
I'll report back ASAP to report on the two solutions when applied one at a time (it's 1am here now...). In the meanwhile I **thank you very much** for your help!

---

### Post by Sciamano on 2010-05-09
Ok, here's what ve fond out.

The trick is modifying the permissions in the fstab. Once done that, everything works.

{optional}: I added this line to the [global] section of the smb.conf:
> usershare owner only = false
in order to be able to share folders that I can access but that are not owner by me (like all those in the NTFS disk, that I could access through the symlinks in my /home/luca/Shares, but not if I tried to directly share a folder on that disk).

Hope this helps other people who having problems with Samba after upgrading to Lucid.
Thanks a bunch to Morbius1 for the time he dedicated to this problem and for providing the working (and easy) solution.

Luca

---

### Post by mocha on 2010-05-17
This is an issue for anyone running the Mythpretty script with the default parameters and using it to share the links out to a media device such as a Popcorn Hour.  There was a samba security update in Karmic back in April that started these problems.  Anyway, thanks to those that figured out the workarounds.

---

### Post by bartman2589 on 2011-04-03
sort of a necropost I know, but creating shares can be done and undone almost just as easily using the Dolphin  file manager in Kubuntu by right clicking on the folder and choosing 'Properties' and then the 'Share' tab.

---

