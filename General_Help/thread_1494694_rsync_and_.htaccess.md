---
title: "rsync and .htaccess"
date: 2010-05-27
forum: General Help
---

### Post by computerx138 on 2010-05-27
Good day,

I'll open with: I'm learning linux. My knowledge is spiky so I apologise if I'm asking something really stupid.

I have a .sh script with the following line:
rsync -Lrv --delete --exclude '.*' --include 'public_html/.htaccess' public_html/ root@mydomain:/home/mdt/public_html/

This is to upload and sync a development snapshot from my local development server to my actual webserver (--delete is intentional). This raises two issues:

1. Big deal: It's not uploading my .htaccess file.

2. Not a big deal: Can I easily have it su or run a chown? Obviously I'd prefer the files have the right ownership :D su is an issue because I don't want most of the users to have a shell, but if I must, I must.

I guess I can work around both with extra ssh commands after the rsync, but one thing I've learnt with Linux so far is: There's probably an easier way.

Thanks in advance

---

### Post by ownaginatious on 2010-05-27
Ya, you can send commands directly over ssh like so:

```

ssh root@mydomain 'chown root /home/mdt/public_html/test.txt'

```

Just add that to the script after the sync.

---

### Post by computerx138 on 2010-05-27
Yeah, I've now added a scp and ssh to upload the .htaccess and fix permissions, but this is a script I'd like to deploy over all the sites I develop and manage. Making it faster and more flexible (supporting multiple .htaccess files without extending the script on a per site basis, for example), plus understanding rsync a little better would be nice. Not essential, but nice :)

---

