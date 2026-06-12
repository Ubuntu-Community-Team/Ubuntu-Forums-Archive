---
title: "What's wrong with my tar command syntax?"
date: 2009-08-14
forum: General Help
---

### Post by tgeer43 on 2009-08-14
I thought I was following directions well but apparently not.
I created a backup of my system with the following command:
```
cd /
sudo tar -cpvzf mybackup.tgz /
```Note: in the above, I left out the --exclude= options in this post for clarity sake but I did actually exclude the usual directories, ie. /lost+found, /mnt, etc. plus the destination file itself (mybackup.tgz), of course.

No problems so far and I have my backup tarball sitting in the root directory. The problem comes when I try to restore. Here's the command I tried (as well as several variations):
```
cd /
sudo tar -xvpfz --same-owner mybackup.tgz -C /
```The error I'm getting is that the file doesn't exist and I think that the problem is related to the placement of the --same-owner option because I've used tar plenty of times before without incident but never with the --same-owner option. It's imperative that I preserve both the file permissions and ownership. If --same-owner had a single letter equivalent them I'm sure I could just include it with -xvpfz but it doesn't.

Can someone please give me the correct syntax and point out where I've been going wrong if it's not obvious? I'm relegated to running Puppy Linux from a USB flash drive until I get my Ubuntu installation restored.

Many thanks in advance,

tgeer

---

### Post by unutbu on 2009-08-14
When you give the "f" option to tar, it expects the name of the archive immediately after the "f". So if you say 
```

tar -xvpfz
```

Then tar looks for a tar-archive called "z".

I managed to get this command to work:
```

sudo tar --same-owner -C / -xvpzf mybackup.tgz  
```

But given the commands you posted, I think```

cd /
sudo tar --same-owner -xvpzf mybackup.tgz  

```
should work too.

---

### Post by tgeer43 on 2009-08-14
Thanks a bunch unutbu,

I sure did not know about the issue with the -f option and didn't see it mentioned in the tar man page. But that would certainly explain things and why my command to create the tarball (tar -cvpzf mybackup.tgz...) works since the filename DOES come immediately after the -f option. And I also see now why the '-C /' is unnecessary since I'm already in the correct directory.

Again, many thanks. I'll give it a go and post back to mark the thread [SOLVED] assuming that I have no further issues. I pretty sure that between the -p and --same-owner options that I won't have any permission or ownership issues. You see, in addition to creating the backup tarball I had also done a straight file copy of the entire partition to another drive but when I tried copying everything back it was a disaster due to ownership and permission problems. Live and learn...

Sincerely,

tgeer

---

### Post by tgeer43 on 2009-08-20
Worked like a charm. Thanks again unutbu.

tgeer

---

