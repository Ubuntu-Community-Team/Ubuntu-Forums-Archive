---
title: "Amazon S3"
date: 2009-12-09
forum: General Help
---

### Post by Robbyx on 2009-12-09
[http://aws.amazon.com/s3/](http://aws.amazon.com/s3/)

Has anyone experience of using this with say simple backup? I can see that it is possible to use a remote directory (SSH or FTP) in simple backup. It is not obvious if amazon S3 will accept SSH. If not I assume there is another program that will match s3 requirements. 

For backing up a standalone machine this looks like a very cheap approach to high quality backup. I am wondering how I do it in practice.

Robin

---

### Post by Robbyx on 2009-12-10
Any chance of a reply, please?

---

### Post by Steve834 on 2009-12-10
S3 doesn't support ssh or ftp.  It's a low level service for storage used by companies to build on.  For a backup solution in the cloud I would google around for some already made service.

---

### Post by falconindy on 2009-12-10
S3 is cost effective and, in my experience, reliable. As mentioned above, it is extremely low level. The only standardized structure determined by S3 is a bucket. It's up to the backup solution used to create and manage the directories and files. That is to say, one particular backup program is **not** compatible with another.

I researched various methods of backups to S3 buckets -- s3rsync, s3fs, and jungledisk. [Jungledisk]("http://jungledisk.com/") is by far the best option, and contrary to what the website says, is free.

---

### Post by DugieHowsa on 2010-04-03
I had used JetS3t in the past, but wasn't overly impressed with it.

[http://bitbucket.org/jmurty/jets3t/wiki/Home]("http://bitbucket.org/jmurty/jets3t/wiki/Home")

---

### Post by mikaelcrocker on 2012-01-05
I haven't used Jungledisk, but I use s3fs.  I just mounted the s3 bucket as a file system.  Once it's mounted I used fstab so it'll auto-mount when I restart my system.  Once it's auto-mounted just cp stuff over to it...

---

### Post by oldos2er on 2012-01-05
Closed, necromancy.

---

