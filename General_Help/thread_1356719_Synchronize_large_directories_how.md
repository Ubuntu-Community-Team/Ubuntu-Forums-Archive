---
title: "Synchronize large directories: how?"
date: 2009-12-16
forum: General Help
---

### Post by johann_p on 2009-12-16
How can I best syncronize large directories between my laptop and several desktop machines?

I have used Unison in the past, but unfortunately, unison for nearly all my directories gives me the error:
"Fatal Error - Lost connection with server"
and on the console it shows:

"Fatal error: Trying to transfer too much data in one go.
If this happens during update detection, try to
synchronize smaller pieces of the replica first
using the "path" directive."

I have searched the mailing list and other web sites but there seems to be no solution for this other than manually splitting up the synchronization chunks which is not practical in my case.

So -- are there any other alternatives to unison that can handle larger file areas? Is there any solution to the unison problem?

---

### Post by Jose Catre-Vandis on 2009-12-16
I use a cp command to do this. You will have to do it both ways though if files are changed on both machines. However the cp cpommand I use won't overwrite anything that is the same on the target machine. I use nfs to connect the shares, but this will work over ssh and samba.

```
    cp -urvp /pathto/externaldrive/* /pathto/backup/directory/

What does it all do?

    cp         the copy command

    -u         update only new or changed files with a newer date

    -r          recursive to all sub directories

    -v          verbose, tell me what is happening

    -p          preserve file attributes
```

---

### Post by garryknight on 2009-12-16
I use grsync which is a graphical front-end to rsync. I've found it extremely easy to set up and use, and very reliable after many months of use. Before that I was using a set of bash scripts that called rsync, but selecting the particular backup I want to do from a list is easier than remembering the names of the scripts.

If you're running Gnome, grsync will fit right in, otherwise installing it will pull in a Gnome library or two.

---

### Post by johann_p on 2009-12-16
Thank you for the suggestions - the problem with both approaches, in comparison with unison is that they only work in one direction. So it is not really syncing, more bringing one up-to-date to the other. Unison can determine what is new on either computer and also show which files have conflicts or have been updated on both. 

I'd even be prepared to pay for a decent program that can do this like unison, but without that limitation concerning large directory trees.

---

### Post by garryknight on 2009-12-16
> **johann_p said:**
> the problem with both approaches, in comparison with unison is that they only work in one direction.

I was puzzled when I saw what you'd written as I know I've used grsync in both directions. But on thinking about what Unison does, I realized that you mean that it does both directions **at the same time**. I can see why you'd want this option.

---

### Post by johann_p on 2009-12-16
> **garryknight said:**
> I was puzzled when I saw what you'd written as I know I've used grsync in both directions. But on thinking about what Unison does, I realized that you mean that it does both directions **at the same time**. I can see why you'd want this option.


Yes, exactly ... unless I can always be certain that changes only happened on one computer, having the option of synchronizing in both directions at the same time (and thus also figure out parallel changes or conflicts) makes things much easier (again, especially if many files are involved).

Also, I always did  the synchronization over ssh ... grsync seems to only support locally mounted file systems?

---

### Post by john newbuntu on 2009-12-17
Try synkron ([http://synkron.sourceforge.net/](http://synkron.sourceforge.net/))

---

### Post by johann_p on 2009-12-17
> **john newbuntu said:**
> Try synkron ([http://synkron.sourceforge.net/](http://synkron.sourceforge.net/))

Thank you, that one looks nice and has nice additional features, but unfortunately does not seem to be able to sync to a different machine over ssh.

---

### Post by garryknight on 2009-12-17
> **johann_p said:**
> grsync seems to only support locally mounted file systems?

No, it will work on a network and should even sync across the internet provided that you've got the relevant NAT set up on your router.

I use it on my LAN with, for example:
    Source: /data/
    Destination: netbook:/data/
It will work with any properly defined host named in /etc/hosts or with any dotted quad, e.g. 192.168.1.4:/home/me/Videos

It's worth noting that grsync simply collects arguments for rsync from its input and passes them as-is. I haven't (yet) looked at synkron but I wouldn't be surprised if it also works across networks. Also, just yesterday, I came across another app called [luckybackup]("http://www.ubuntugeek.com/luckybackup-a-powerful-fast-and-reliable-backup-sync-tool.html") which looks very similar to grsync.

Because grsync and luckybackup work in one direction only, they probably better serve the purposes of those of us who want to sync certain directories from our PC to our laptop/netbook before we leave the house/work, then sync the same directories the other way when we get back. If you want to use them on a LAN where more than one machine is on the go during the day then unison, or something like it, is obviously a much better option. Otherwise it means making notes on what's changed where as you go along, and we humans aren't always good at doing that...

---

### Post by johann_p on 2009-12-17
Sorry - I did not realize this, but one can indeed use grsync just like rsync with remote hosts over ssh.

---

### Post by paxmark1 on 2010-01-08
Probably won't help, but you can change your preferences in etc/ssh or ~/.ssh to use a less demanding cipher, like blowfish-cbc or aes-128 (as opposed to des) and then the time to complete very well might be less. Some people do this when using unison vis ssh on arm cpu's or on a nas 

It should go a lot quicker after the first sucessful run and you could then go back to des

If you could somehow for a short period split the directory in half or thirds or whatever and you were sucessful, then you could keep adding more files until you had all files from the chosen directory.  

Another option might be edit your ./unison/default or in your .prf add some ignore's

ignore = Name *.mp3
# ignore all .mp3 files anywhere
ignore = Name .*    # ignores hidden files
ignore = Name l*
ignore = Name m*

to be successful and then sequentially remove ignores as it will have to index less after the first sucess.  

Gotta be a humongous directory

peace mark

---

### Post by johann_p on 2010-01-08
As it turns out, the original unison bug has been fixed .. there was a built in limit somewhere which has been removed.

This bug has been removed in version 2.32.52 which I have manually compiled from source. The version in the Ubuntu repositories still has that bug.

So with my new unison version I am happy again though rsync/grsync is very useful for one-way copying between machines and other situations where only one-way syncing is needed.

---

