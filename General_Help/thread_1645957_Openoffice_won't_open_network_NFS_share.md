---
title: "Openoffice won't open network NFS share"
date: 2010-12-15
forum: General Help
---

### Post by NertSkull on 2010-12-15
I have a computer in another room of my house that I share the drive with my primary computer using NFS.

I just mount the network drive as normal in NFS.  But I discovered today that I can't open openoffice files off of the drive.  I have to copy them to the local disk first.  I can open text files, pictures, pdfs.  But .odt files will load the splash screen for open office, but go no further than that.

Anyone know how to fix this?  It's kind of a killer for NFS for me.  I really would like to be able to open documents over the network.

here's the settings I'm using in fstab in case those are wrong

```
192.168.0.3:/media/Data /media/Data nfs rw,hard,intr 0 0
```

---

### Post by NertSkull on 2010-12-18
So after some searching around for a few days I discovered something about NFS and locking files.

In the man page for nfs it talks about mounting with nolock (default is to lock).

So I changed my fstab to this

```
192.168.0.3:/media/Data /media/Data nfs rw,hard,intr,nolock 0 0
```

and now it works.  I can open the openoffice files.

BUT, I cannot figure out what this is doing.  I've read a lot but its not totally making sense to me.

Is this ok?  Is it bad to turn off the "lock"??  I want to make sure that I'm not harming other files in any way, or that I'm not weakening security.

The only thing I can figure out is "lock" was supposed to keep other things from opening the file.  But nothing else ever was opening the file (I only have two computers so I know that I'm the only one trying to open the office files).  So I don't understand how that can be the case.

Anyway, before I implement this as a final solution, can anyone give me more information about locking files?  and what it is I'm doing?

thanks

---

### Post by NertSkull on 2010-12-19
Has no one else really had an issue with this?

I found a few places that said I should edit the /usr/bin/soffice (as root) by commenting out the following lines. 

SAL_ENABLE_FILE_LOCKING=1
export SAL_ENABLE_FILE_LOCKING

Those lines are in there, but they are in there 2 or 3 times.  And commenting them out doesn't do anything.

I think the new version tries to account for this, because these lines are found in a bunch of if statements with other lines.

Anyway, point is commenting those out doesn't work for me even though everything I've read says that is the solution.

Still the only thing I can find is to add the nolock to fstab.  But I don't know if thats the best way to do this.

---

### Post by NertSkull on 2010-12-19
SUCCESS!!!! (no thanks to you people, hahahaha j/k)

Anyway, in case anyone else has the same issues this is what has to be done.  Its probably not the best fix.  And if you have multiple people editing the same open office documents it could be bad, but for my home network it works fine.

So like I said above, a few other forums said remove the sal locking command.  But you can't just do the couple of lines.  You need to do the entire if block that includes sal and star locking.  This is what mine originally looked like

```
sudo nano /usr/bin/soffice
```


```
esac

# adjust environment
if [ -z "$SAL_ENABLE_FILE_LOCKING" ]; then
    case "$FILE_LOCKING" in
       auto)
        home_on_nfs "$@"
        if [ $? = 0 ]; then
           STAR_PROFILE_LOCKING_DISABLED=1
           export STAR_PROFILE_LOCKING_DISABLED
       fi
       file_on_nfs "$@"
       if [ $? = 0 ]; then
           SAL_ENABLE_FILE_LOCKING=0
           export SAL_ENABLE_FILE_LOCKING
           # for safety
           STAR_ENABLE_FILE_LOCKING=0
           export STAR_ENABLE_FILE_LOCKING
       else
            # file locking now enabled by default
           SAL_ENABLE_FILE_LOCKING=1
           export SAL_ENABLE_FILE_LOCKING
       fi
        ;;
       yes)
       SAL_ENABLE_FILE_LOCKING=1
       export SAL_ENABLE_FILE_LOCKING
        ;;
       no)
       SAL_ENABLE_FILE_LOCKING=0
       export SAL_ENABLE_FILE_LOCKING
       # for safety
       STAR_ENABLE_FILE_LOCKING=0
       export STAR_ENABLE_FILE_LOCKING
       STAR_PROFILE_LOCKING_DISABLED=1
       export STAR_PROFILE_LOCKING_DISABLED
    esac
fi

if [ -z "$SAL_NOOPENGL" ]; then
```


and then I edited it to look like the following (just commented everything out)


```
esac

# adjust environment
# I commented out this next block of locking because I couldn't get things to open on my 
# network NFS drives.  Removing this block of coding fixed that (the commented out if part)
#if [ -z "$SAL_ENABLE_FILE_LOCKING" ]; then
#    case "$FILE_LOCKING" in
#       auto)
#        home_on_nfs "$@"
#        if [ $? = 0 ]; then
#           STAR_PROFILE_LOCKING_DISABLED=1
#           export STAR_PROFILE_LOCKING_DISABLED
#       fi
#       file_on_nfs "$@"
#       if [ $? = 0 ]; then
#           SAL_ENABLE_FILE_LOCKING=0
#           export SAL_ENABLE_FILE_LOCKING
#           # for safety
#           STAR_ENABLE_FILE_LOCKING=0
#           export STAR_ENABLE_FILE_LOCKING
#       else
#            # file locking now enabled by default
#           SAL_ENABLE_FILE_LOCKING=1
#           export SAL_ENABLE_FILE_LOCKING
#       fi
#        ;;
#       yes)
#       SAL_ENABLE_FILE_LOCKING=1
#       export SAL_ENABLE_FILE_LOCKING
#        ;;
#       no)
#       SAL_ENABLE_FILE_LOCKING=0
#       export SAL_ENABLE_FILE_LOCKING
#       # for safety
#       STAR_ENABLE_FILE_LOCKING=0
#       export STAR_ENABLE_FILE_LOCKING
#       STAR_PROFILE_LOCKING_DISABLED=1
#       export STAR_PROFILE_LOCKING_DISABLED
#    esac
#fi

if [ -z "$SAL_NOOPENGL" ]; then
```

Now it works GREAT.

Thanks everyone for looking, hopefully that will help someone else if they run into the same issue.  

But now I can mount my drive normally (with locking on, which I also discovered was a better thing) and still open my openoffice files.

For anyone interested in more reading.  I found this fix at the link below.  They have a bit more discussion on what's going on.

[http://forum.qnap.com/viewtopic.php?f=35&t=33959](http://forum.qnap.com/viewtopic.php?f=35&t=33959)

---

### Post by eflester on 2011-03-26
Allow me to express my thanks for your post. I have been wrestling this problem on and off all day, after ignoring it for several weeks. I finally couldn't stand it any more and started looking around. You are quite right about the solution. I also used "nolock," which really isn't a problem on my system since I'm the only user (I have a NAS exporting stuff via NFS to whatever I run in the house), but it does seem that commenting out the lines in soffice is a better solution.

I found some other forums that also suggested commenting out certain lines in soffice, but your post is the first one that directly addresses the file that I see using Ubuntu 10.10 with Open Office 3.2.1. It is indeed necessary to comment out all the lines as you show it. I tried several variations but this is the first one that actually works.

Yes, the problem belongs to Open Office. People grumble about NFS, but it works fine with everything else. And, realistically, what alternative exists? 

Thanks again for your valuable help.

---

### Post by NertSkull on 2011-03-27
Well I'm glad it helped.

Just an FYI for others.  I've since moved to Libre Office, and I encountered the same issues with NFS.  But I did the same thing and it works just as well now as Open Office.

Anyway, glad it worked for you.  Cheers!

---

### Post by toljnima on 2011-05-08
Thanks, NertSkull, for the "fix"

I also moved over to Libreoffice, on Mint. It's a little different than your fix. actually easier.
I did this:
sudo nano /opt/libreoffice/program/soffice

commented out these lines, at the very beginning, they occur only once in the file:

# file locking now enabled by default
# SAL_ENABLE_FILE_LOCKING=1
# export SAL_ENABLE_FILE_LOCKING

opened a odt file and it works like a charm

Hope this helps others also.
Lev väl

---

### Post by jdc.84 on 2011-12-22
Hi,

I tried doing this on Ubuntu 11.10 with libre version: 
LibreOffice 3.4.4 
OOO340m1 (Build:402)

But i can't get the thing to write to my seagate GoFlex network drive.

I definitely commented out all the lines properly, i even logged out and logged back but still i cannot write to the drive, my initial troubles started here on this link: [http://ubuntuforums.org/showthread.php?t=1890841](http://ubuntuforums.org/showthread.php?t=1890841)

---

### Post by Kenno on 2012-04-10
Sorry for the necropost, but for future reference, I'd like to point out that editing /usr/bin/soffice is a bit heavy-handed and may be undone by a software update. The safe way to disable OpenOffice/LibreOffice file locking system-wide in Ubuntu would be to edit /etc/openoffice/soffice.sh and change FILE_LOCKING from "auto" to "no". Sadly, this doesn't actually work because of (presumably) a bug in /usr/bin/soffice , which can be corrected by changing ```
        ;;
        no)
        SAL_ENABLE_FILE_LOCKING=0
        export SAL_ENABLE_FILE_LOCKING
        # for safety
       STAR_ENABLE_FILE_LOCKING=0
        export STAR_ENABLE_FILE_LOCKING
        STAR_PROFILE_LOCKING_DISABLED=1
        export STAR_PROFILE_LOCKING_DISABLED
    esac
fi
```to```
        ;;
        no)
        unset SAL_ENABLE_FILE_LOCKING STAR_ENABLE_FILE_LOCKING
        # for safety
        export STAR_PROFILE_LOCKING_DISABLED=1
    esac
fi
```. I know, now we're editing /usr/bin/soffice anyway, but I hope this is something that can be fixed upstream so that we can get away with only the edit in /etc/openoffice/soffice.sh .

---

### Post by glicioto on 2012-04-30
Hi, I bookmaked this thread because the solution which is given here has allways been necessary at each update of Staroffice. Now I just upgraded the sys to UBUNTU 12.04 LTS and of course I lost the possibility to open office files on my NAS in read/write mode. I came back here to apply the beloved solution, but, trying to apply it, I found out that the soffice file did change. Now the part that we used to comment is not there any more. There is a shortest solution I propose: to comment the following lines that are on top of the file:

# file locking now enabled by default
SAL_ENABLE_FILE_LOCKING=1
export SAL_ENABLE_FILE_LOCKING

Just turn it to:

# file locking now enabled by default
#SAL_ENABLE_FILE_LOCKING=1
#export SAL_ENABLE_FILE_LOCKING

It seems to work. It's easy I hope some other user can confirm the propose workaround.

Ciao

Glicioto

---

