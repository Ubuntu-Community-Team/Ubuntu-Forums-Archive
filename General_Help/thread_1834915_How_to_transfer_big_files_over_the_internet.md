---
title: "How to transfer big files over the internet?"
date: 2011-08-28
forum: General Help
---

### Post by thunderbirdje on 2011-08-28
Hello everyone,

I would like to receive some big files (several files), in total around @GB from a friend over the internet.

Is there any way to do this secure? Can this done with resuming options because the internet from the sender is not so stable and quite slow (180kb max)?

We both have Ubuntu :):):)

Thank you!

---

### Post by bruno9779 on 2011-08-28
There are many services on the net to do this.

Personally, for a case like this I would create a private .torrent.

If the person that needs to send you the files already uses a torrent client, it should be pretty easy to guide him through the creation of a new torrent, also if he's never done it.

---

### Post by docbop on 2011-08-28
Are you talking about scp or similar tool.  The problem I had with large transfers is the encryption/decryption can almost double the transfer time.  Then if going long distance or over a funky connection then dropped packets and resends add more time.

Try scp and see how your times are, if any issues then probably should checkout one of the many file sharing services on the net.

---

### Post by galvatron408 on 2011-08-28
ahhh, the best tool for you is rsync.

rsync will sync all his file with whatever location you set on your side. it is secure and it can continue syncing files even if your connection was interrupted. 

he has to be running sshd or a rsync daemon but for your purpose sshd is perfectly fine.

---

### Post by papibe on 2011-08-31
> **thunderbirdje said:**
> Is there any way to do this secure?

If you mean 'data integrity', there's no reason to worry about that.

A few ideas:
[LIST]
[*] Synchronization Service:
[LIST]
[*]Dropbox.
[*]Ubuntu One, etc.
[/LIST]
[*]File hosting sites:
[LIST]
[*]Megaupload.
[*]Rapidshare, etc
[/LIST]
[*]Bittorrent.
[*]rsync over ssh.
[/LIST]
I personally use rsync over ssh to share pictures, and family videos with my brother (who is out of the country). If you go this way, you'll need also:

[LIST]
[*]Create a simple script that can take of the concern of a slow or inestable connection. Here you can even use md5sum to check integrity.
[*]Create ssh Public keys for security and easier automation of your script.
[*]Optional: the virtual session manager 'screen'. The easiest way to manage long time execution command line programs.
[/LIST]

Hope it helps,
Regards.

---

### Post by thunderbirdje on 2011-09-01
> **papibe said:**
> If you mean 'data integrity', there's no reason to worry about that.

A few ideas:
[LIST]
[*] Synchronization Service:
[LIST]
[*]Dropbox.
[*]Ubuntu One, etc.
[/LIST]
[*]File hosting sites:
[LIST]
[*]Megaupload.
[*]Rapidshare, etc
[/LIST]
[*]Bittorrent.
[*]rsync over ssh.
[/LIST]
I personally use rsync over ssh to share pictures, and family videos with my brother (who is out of the country). If you go this way, you'll need also:

[LIST]
[*]Create a simple script that can take of the concern of a slow or inestable connection. Here you can even use md5sum to check integrity.
[*]Create ssh Public keys for security and easier automation of your script.
[*]Optional: the virtual session manager 'screen'. The easiest way to manage long time execution command line programs.
[/LIST]

Hope it helps,
Regards.

Thank you all for dropping so many options, much to check out! Welll, I am talking about transferring the files through a secured tunnel so that none can steal them. Openssh tunneling sounds good with rsync :)

I will give it a try!

---

### Post by SeijiSensei on 2011-09-01
If the files are compressible, meaning mostly text rather than pictures or video, use the -z option with rsync to employ on-the-fly compression.  That will speed the transfer.

Don't use this option with already-compressed files like JPEGs though; it will actually slow down the transfer.

---

### Post by holycow131415 on 2011-09-01
Dropbox, it is easy to get 5gbs free, esp if you and a friend will have a shared folder with each other ;)

---

### Post by thunderbirdje on 2011-09-02
I have set up SSH and using rsync now, works as a charm! Will test it to my friend and keep you up to date!

Thanks agaain!

---

### Post by papibe on 2011-09-02
A few tips regarding a slow or instable connection:

**Loop**
If you want to leave things running unattended, you'll need a loop un your script. This would be an skeleton: 
```
!/bin/bash
...
rsync -aP -e ssh yourfriends:source/ local/

# Enter a loop if it didn't finish properly
until [ $? = 0 ]
do
        echo "Connection lost, sleeping 90 seconds."
        echo "-------------------------------------"
        sleep 90

        rsync -aP -e ssh yourfriends:source/ local/
done

# Check md5sum here, if you feel like it.
...

```
**Keep partial transfers**
To make sure you don't start transferring all over again when the connection is lost, use the rsync option --partial. That way, anything already transfered will be kept, so the next time rsync is run it won't start from zero.

**Optional: progress**
When transferring several small to medium files, the option -v is very usefull. However for a few "big" files, I personally find the option --progress much helpful. Note that -P implies --partial and --progress.

Hope it helps,
Good Luck!

---

