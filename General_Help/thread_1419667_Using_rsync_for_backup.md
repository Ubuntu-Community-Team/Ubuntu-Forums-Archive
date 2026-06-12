---
title: "Using rsync for backup"
date: 2010-03-02
forum: General Help
---

### Post by Scunnered on 2010-03-02
I saw in a magazine reference to using rsync to have identical copies of folders.  This looks like something I could find useful as I have a large number of items in need of safe backup.

I have the folders on an old system on a home network and would like to copy these over to a USB Hard Drive.  

Currently the folders reside on SFTP xxx.xxx.xxx.xxx and I wish to sync them to a USB port on my laptop.  As it would be more than my life is worth to get things wrong I need your kind assistance.

---

### Post by QLee on 2010-03-02
[QUOTE=Scunnered]
I have the folders on an old system on a home network and would like to copy these over to a USB Hard Drive.  

Currently the folders reside on SFTP xxx.xxx.xxx.xxx and I wish to sync them to a USB port on my laptop.  As it would be more than my life is worth to get things wrong I need your kind assistance.[/QUOTE]

There's no need to make it more complicated than necessary (unless one is trying to answer a homework question). Since your source and destination directories are local.

rsync [choose the options you want to use] [source] [destination]

---

### Post by HermanAB on 2010-03-02
Indeed, most 'backup' programs are nothing more than a complicated front end to rsync or unison.  In most cases, it is easier to simply craft your own one liner directly in a desktop launcher, rather than trying to figure out how to use some ridiculously complicated backup manager program.

There are examples in the man page.

However, if you are a sucker for punishment, then look into dervish, rbackup and bacula. ;)

---

### Post by Scunnered on 2010-03-02
Many thanks for your replies.

Can I therefore assume that as both are on the same home network that it will be a case of entering into the terminal :

rsync &#8211;archive &#8211;delete  /SFTP on xxx.xxx.xxx.xxx/home/user name/master folder/sub-folder/ /media/My Passport/folder

I think from what I see that the path to source will be correct but am a little unsure about the path to destination.  I want to put the copy to an existing folder in a Passport USB HD connected to my laptop. I would be connecting from the laptop to both the SFTP and Passport. 

Would what I have shown be correct or should I just attach the Passport to a spare USB connection on the old system and shorten the paths?

Your further assistance will be appreciated.

---

### Post by timZZ on 2010-03-02
Use ```
ssh host 'echo $PATH'
``` to find your remote path.

Be mindful when using spaces within paths.

Here is an example.

```
#!/bin/sh

    export PATH=/usr/local/bin:/usr/bin:/bin

    LIST="rootfs usr data data2"

    for d in $LIST; do
	mount /backup/$d
	rsync -ax --exclude fstab --delete /$d/ /backup/$d/
	umount /backup/$d
    done

    DAY=`date "+%A"`
    
    rsync -a --delete /usr/local/apache /data2/backups/$DAY
    rsync -a --delete /data/solid /data2/backups/$DAY


```

You can modify this code to achieve what you are looking for.

---

### Post by QLee on 2010-03-02
[QUOTE=Scunnered]... should I just attach the Passport to a spare USB connection on the old system and shorten the paths?[/QUOTE]

That's how I would choose to do it, keep it simple. No need to transfer over a network then over a usb connection for local files in my opinion.

---

### Post by Scunnered on 2010-03-02
Again my thanks for your advice.

As no doubt you will have gathered that I am finding my way slowly through the joys of Linux.

I think that I will follow what QLee suggests as it is more of the KISS approach that I understand a bit better.  I will have a look at what timZZ offers as it would appear to if I am reading this right a means of automatically syncing day by day.

As I am taking things one step at a time I will see how I get along with things now before attempting anything more complicated.

Again my sincere thanks for your kind assistance

---

### Post by Scunnered on 2010-03-02
Things are not going as well as I had hoped for.  It appears that I am not correctly understanding things.  The magazine states that using rsync --archive --delete /path/to/source/ /path/to/dest/ 
will ensure that the second directory contains an exact copy of the first.

As I am wishing to have an exact copy of a folder from my home directory copied to a USB hard drive is this the right way to go?

I had eneterd the full path /home/myname/PHOTOBACKUP/2009 Photos and the destination as media/My Passport/ 

I was informed that the path was not right and nothing was transferred.

Where am I going wrong?

---

### Post by QLee on 2010-03-02
[QUOTE=Scunnered]
I had eneterd the full path /home/myname/PHOTOBACKUP/2009 Photos and the destination as media/My Passport/ 

I was informed that the path was not right and nothing was transferred.

Where am I going wrong?[/QUOTE]

Since none of us is looking over your shoulder it isn't easy for us to know. What you wrote doesn't look like an exact error message. However, I'd first ask, is your backup media mounted and is that the correct mount point? "My Passport" looks a lot like a LABEL.

---

### Post by Scunnered on 2010-03-02
**QLee**

As far as I can see when I click on the passport icon on my desktop it displays on the location bar as "**/media/My Passport**" so that was why I entered it as that.

I followed the instructions as written however all that happened was I was told that there was an error and nothing was downloaded.  As the desktop is in a bedroom it is currently shut down to let others sleep.  I will have a go again in the morning and copy the full details from the terminal and post that FYI.

Meanwhile I will post on the magazine forum and see if everything was correctly printed.

---

### Post by Scunnered on 2010-03-03
I am pleased to advise that I have been able to resolve this matter.  I contacted the magazine forum and they provided guidance which worked a treat.

I was instructed that the best way forward was to use auto completion with the <tab> key. 

I took the KISS approach by working with the desktop only and by using auto completion was able to enter the instruction with ease.  I was given the example of  :

Type rsync /h<tab>/my<tab>/Photob<tab>/2009<tab>/<space>/med<tab>/My<tab>/ -avu  

which using auto completion set everything in motion.  This was slightly different to the method advised in the magazine but as it worked OK I shall not worry too much for the moment.

The upshot was that what was taking hours to copy by conventional methods took somewhere in the 10 &#8211; 15 mins range. 

I hope this will assist others should they have the need.

Again my thanks to everyone for their contributions which ably assisted

---

### Post by HermanAB on 2010-03-03
Quotes my friend, quotes...

If there are spaces in your paths, then you have to use quotes.

---

### Post by Scunnered on 2010-03-03
**HermanAB**

There was a space between My Passport (the USB HD) but using the <tab> put a backslash between my and passport and everything worked a treat. I used this to copy a full years output and once my partner has finished picking and choosing what she wishes to keep I intend to use it for everything.

---

