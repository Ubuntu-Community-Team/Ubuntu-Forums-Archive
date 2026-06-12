---
title: "rsync via ssh permissions issue"
date: 2011-06-25
forum: General Help
---

### Post by maclenin on 2011-06-25
Hello!

I am putting the final touches on an rsync backup script, which I can configure to operate either locally or remotely.

1. local```
rsync -avrP ~/photos /media/usb_backup/
```
2. remote```
rsync -avrP**e** ~/photos server@123.456.7.890:/media/usb_backup/
```

When I run the local script, from my local machine - all ends well. A new directory 'photos' is created under 'usb_backup' and files within the source and target directories are sync'ed.

**However**, when I run the remote script (also from my local machine), I receive the following...```
rsync: Failed to exec ~/photos: Permission denied (13)
```...and rsync terminates.

I can ssh from my local machine to the remote "server" (with public key authentication) and make directories the server's /media/usb_backup/ drive - without issue.

Does the "rsync user" have permission to make directories on the server's /media/usb_backup/ drive?

As an additional experiment, I created a 'photos' directory on the server's /media/usb_backup/ drive (manually, via ssh), ran the remote rsync and received the same "Permission denied" error. Does the "rsync user" need special permission to "exec" a local directory for remote transfer?

Thanks for any guidance!

---

### Post by papibe on 2011-06-25
My guess is that /media is own by root and then you're not able to create the usb_backup directory. Try creating it before hand and assign it read and write permissions to the user 'server'. Alternatively, you can change the /media's permission to 777.

BTW, you're using 'server@123.456.7.890'. That means you're connecting to the server 123.456.7.890 using a user called 'server'. Is that right ?

Regards.

---

### Post by maclenin on 2011-06-25
**papibe:** Thanks for the reply.

Yes. /media @123.456.7.890 is owned by root.
Yes. 'server' is the user.

[B]Differently (but with the above in mind)....
[/B]
client: /home/user/photos
server: /media/usb_backup

**Successful** test: SSH from client to server
1. Accessed server (public key)
2. Accessed /media/usb_backup
3. Created /media/usb_backup/photos

**Unsuccessful** test: RSYNC via SSH from client (/home/user/photos/) to server (/media/usb_backup/photos/)
1. Shouldn't the "ssh process" and "rsync process" bestow similar privileges - as both are invoked by the same client "user" - with the same public key - to gain access to the same server and /media resource?
2. The error message...```
rsync: Failed to exec /home/user/photos: Permission denied (13)
```...seems to imply that the permission issues are associated with trying to open the client directory - /home/user/photos? No?

Thanks for your help!

---

### Post by papibe on 2011-06-25
After a second look...

The option -e is to pass ssh options. Try changing the syntax:
```
$ rsync -avrP -e "ssh -l server" ~/photos 123.456.7.890:/media/usb_backup/
```
Hope it helps.

---

### Post by maclenin on 2011-06-25
That did it! Thanks for the second look!

So, it seems there is the concept of "ssh-user" vs. "rsync-user" - and these must be "individuated" to be certain that procedural privileges are assigned (properly)....

My final "working" iteration is:```
rsync -avrPe "ssh" /home/user/photos server@123.456.7.890:/media/usb_backup/
```

As I have only one client "ssh-user" - it seems "ssh" was enough to guide the process to the "ssh-default" - the same default who was able to successfully access and create the directories via "plain vanilla" ssh, in the first place....

Thanks, again, **papibe**!

---

