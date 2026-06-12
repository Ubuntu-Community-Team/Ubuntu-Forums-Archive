---
title: "Deja Dup with S3"
date: 2010-08-21
forum: General Help
---

### Post by RogerD on 2010-08-21
Hi

I'm currently useing Deja Dup to backup 8G of important files onto an external hard disk - it's absolutely fine, simple to use, and file recovery, which I've practised, is straightforward.

For added security I'd now like to start storing files using some form of Internet storage service - Amazon's S3 looks very reasonably priced, and is supposedly well integrated with Deja Dup. However, how one goes about using S3 with Deja Dup is all a bit of a mystery.

I've signed  up with S3, and have received the standard email inviting me to collect my Access Identifiers. When I try to do that, I'm asking to make a choice about the sort of security credentials I need. I've no idea what to choose, and I can't understand the guidance offered by Amazon. It's all utterly bewildering, and I'm rapidly coming to the conclusion that S3 isn't really suitable for a relatively unsophisticated user like me - which is a bit odd, given that  Deja Dup is so brilliantly easy to use, and S3 support is supposedly built-in.

Has anyone managed to use S3 with Deja Dup, and, if so, how to you start?

Roger D

---

### Post by mikix on 2010-08-21
Hello!  I'm the maintainer of Deja Dup, so thanks for the kind words.  Sorry that using S3 is a bit confusing.

First, go to [http://aws.amazon.com/account/](http://aws.amazon.com/account/) and click on "Security Credentials".  Then look at the "Access Keys" section.  You'll want to note your Access Key ID and your Secret Access Key.

Then, open Deja Dup, click Edit->Preferences, and select "Amazon S3" as your backup location.  You'll then see options to enter what your Access Key ID is as well as if you want to put this backup under a particular folder in S3.

When you back up, you will be prompted for your Secret Access Key, which you can choose to have Deja Dup remember if you like.

That's all there should be to it!

---

### Post by RogerD on 2010-08-22
Many thanks for the very helpful response - and the great work on Deja Dup. For some reason my first s3 backup attempt failed, but I tried again a few minutes later, and everything worked fine. 

As a test, I've now successfully save and restored a 1M folder - couldn't be easier.

The S3 documentation has a lot to say about 'buckets', which with Deja Dup I don't seem to meet at all - which is great. However, I seem to remember reading something about 5G being the largest object I could store in a bucket. Currently, all my key files are in a folder of over 8G. Can a store this as a single folder on S3, or do I need to prune it done to under 5G, which, to be honest, would probably be a sensible move, given that 8G will take days to upload.

Roger D

---

### Post by dixon on 2010-08-27
I'm also considering deja-dup + s3 solution, but there's one thing I want to know. How's deja-dup working? I want to backup all my photos - it has something around 40GB. It doesn't grow very fast - 500MB per month. When deja-dup is doing incremental backups does it need to download the whole first 40GB backup? What will be the traffic in case of incremental backups? I'm on DSL connection so the traffic is kind of important for me...

---

### Post by bmullan on 2010-08-28
> **mikix said:**
> Hello!  I'm the maintainer of Deja Dup, so thanks for the kind words.  Sorry that using S3 is a bit confusing.

First, go to [http://aws.amazon.com/account/](http://aws.amazon.com/account/) and click on "Security Credentials".  Then look at the "Access Keys" section.  You'll want to note your Access Key ID and your Secret Access Key.

Then, open Deja Dup, click Edit->Preferences, and select "Amazon S3" as your backup location.  You'll then see options to enter what your Access Key ID is as well as if you want to put this backup under a particular folder in S3.

When you back up, you will be prompted for your Secret Access Key, which you can choose to have Deja Dup remember if you like.

That's all there should be to it!

I've been using AWS S3 for a long time and decided to try deja-dup.

I installed it using on Ubuntu 10.04 (64bit), using the PPA.

I then do the following:

-select Amazon S3
-enter my AWS Access Key
-enter my Amazon "bucket" name for "folder"
-click Connect to Server
-enter the URI of my bucket
-I press Connect

I always get the same error:

**Cannot Connect to Server. You must enter a name for the server.**

I think I am doing the configuration correctly?  Is there a "port" I need to open on my firewall?

---

### Post by bmullan on 2010-08-28
> **bmullan said:**
> I've been using AWS S3 for a long time and decided to try deja-dup.

I installed it using on Ubuntu 10.04 (64bit), using the PPA.

I then do the following:

-select Amazon S3
-enter my AWS Access Key
-enter my Amazon "bucket" name for "folder"
-click Connect to Server
-enter the URI of my bucket
-I press Connect

I always get the same error:

**Cannot Connect to Server. You must enter a name for the server.**

I think I am doing the configuration correctly?  Is there a "port" I need to open on my firewall?

[SOLVED - I think]
As there is little help or documentation with Deja-Dup what little is available is confusing.

If I only click the BACKUP icon select Amazon S3 the ONLY click NEXT (*not* CONNECT) then I can proceed with a Backup.

If you Click on CONNECT to Server... it always fails asking for a server name.   No matter what I enter for a server name URI, ip address etc it always issues the fail to connect message.

I'm not sure why but it would really help me and other's I found researching this problem if there was at least a minimal help file, wiki or something to describe details of when to do what and what to enter where ... whether you are doing a local or remote backup.

---

