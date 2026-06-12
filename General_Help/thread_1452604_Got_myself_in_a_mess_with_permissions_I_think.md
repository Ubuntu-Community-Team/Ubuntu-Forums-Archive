---
title: "Got myself in a mess with permissions I think"
date: 2010-04-12
forum: General Help
---

### Post by dchurch24 on 2010-04-12
Hi all,

I have several machines on my home network.

Until recently all was fine, but recently if I try to copy or create a file on my NAS unit I get the error "Permission Denied".

I have one machine where I have created a sym link to my NAS, I am the owner of the folder, and the owner of the link. In desperatation I went to the NAS and did: "chmod -R 777" on the root folder. This has made no difference.

The logged in user on all machines is the same: "dave".

I'm struggling to see why I still get permission denied.

I get this from another machine I have on the network too. I can get around it by doing "sudo cp ...blah", but I want to run a cron job overnight to copy my pictures to the NAS as a backup, and I won't be wanting to type "sudo" every morning at 2am ;-)

ls -l returns this on the folder I am looking to copy to (this is a sym link, the drive is mounted elsewhere):

I am using samba to mount the drive.

```
lrwxrwxrwx 1 dave root   20 2010-04-12 10:55 mybook -> /media/mybook/public
```

Can anyone point me in the right direction please?

---

