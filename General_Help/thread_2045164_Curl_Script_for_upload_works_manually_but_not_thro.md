---
title: "Curl Script for upload works manually but not through cron"
date: 2012-08-20
forum: General Help
---

### Post by jimmystubs on 2012-08-20
Hi all!

I have a strange issue I am hoping a Ubuntu guru can shed some light on.

I have a curl script which is run by cron to upload a zip file once a day - this is used as an automated backup and the file is only 30MB in size.

The script is: *'curl -T /home/jmyers/redstone_backups/`date +%y%m%d`/`date +%y%m%d`.zip [ftp://ftp.server.com.au](ftp://ftp.server.com.au) --user username:password'*

When I run the script manually with sh it shows a progress bar and uploads the file completely. When cron runs it the file only uploads 2MB then stops.

The crontab -e is *'50 4 * * * /home/user/dailyoffsitebackup.sh'* which seems to run according to the schedule, but the file uploaded is around 2MB in size.

Any ideas why the output is different when run via cron rather than the output i get if I manually run the script?

Any help is appreciated. Thanks!

---

### Post by thnewguy on 2012-08-20
Is this something that you can reproduce? I mean have you run the script from cron several times and had the same truncated file each time? For that matter are you sure the remote file is really just 2MB in size? Depending on how you are viewing the file its old (partial) size might be cached in your browser/FTP client.

---

### Post by jimmystubs on 2012-08-20
Thanks for your quick reply.

I can confirm the file that ends up on the FTP is indeed 2MB, as I can download it to another machine and confirm the file is not complete.

I can also view this file on the FTP server itself from command-line and confirmed the size. The script has been running for around a week so I have a bunch of examples on the FTP server. They are all exactly 2,297KB in size which seems strange, I confirmed all the source files are 30,616KB in size.

I can replicate this, I just ran it via cron just now and got the same result, then I manually run *'sh dailybackupscript.sh'* and it showed a progress bar and performed as expected, outputting the full 30MB file.

Seems really strange and am abit clueless at this point...

---

### Post by jimmystubs on 2012-08-21
I lie, they do not always end up being the same size. After some more testing they vary from 2.2MB to 2.3MB.

Any ideas as to why this would be happening? If not are there any other simple programs like curl I can try instead.

Cheers

---

### Post by jimmystubs on 2012-08-22
Any ideas?

---

### Post by dragonfly41 on 2012-08-22
Out of curiosity found a few references here ..

[https://www.google.com/search?client=ubuntu&channel=fs&q=curl+truncates+zip+file&ie=utf-8&oe=utf-8&gl=uk](https://www.google.com/search?client=ubuntu&channel=fs&q=curl+truncates+zip+file&ie=utf-8&oe=utf-8&gl=uk)

---

### Post by SlugSlug on 2012-08-22
> **jimmystubs said:**
> Hi all!

I have a strange issue I am hoping a Ubuntu guru can shed some light on.

I have a curl script which is run by cron to upload a zip file once a day - this is used as an automated backup and the file is only 30MB in size.

The script is: *'curl -T /home/jmyers/redstone_backups/`date +%y%m%d`/`date +%y%m%d`.zip [ftp://ftp.server.com.au](ftp://ftp.server.com.au) --user username:password'*

When I run the script manually with sh it shows a progress bar and uploads the file completely. When cron runs it the file only uploads 2MB then stops.

The crontab -e is *'*50 4 * * * /home/user/dailyoffsitebackup.sh*'* which seems to run according to the schedule, but the file uploaded is around 2MB in size.

Any ideas why the output is different when run via cron rather than the output i get if I manually run the script?

Any help is appreciated. Thanks!

try edit cron to 
```
50 4 * * * /bin/sh /home/user/dailyoffsitebackup.sh
```

---

### Post by jimmystubs on 2012-08-22
Good idea but no success.

I checked FTP logs and there is indeed an error:

- 426 Connection closed; transfer aborted. Error #10057

I have no idea on this, as i said this script works completely fine if run from CLI manually - the issue only comes into play when running it from cron.

---

### Post by jimmystubs on 2012-08-22
Tried adding the --ftp-pasv to the end but same result. It works when manually run but when cron runs it, it fails after 2mb

---

### Post by SlugSlug on 2012-08-22
maybe edit the script to output to a logfile?

```
curl -T /home/jmyers/redstone_backups/`date +%y%m%d`/`date +%y%m%d`.zip [ftp://ftp.server.com.au](ftp://ftp.server.com.au) --user username:password >/tmp/ftp.log
```

---

### Post by jimmystubs on 2012-08-22
The log file is empty at end of transaction...

Curl was my first choice but perhaps i should look into something else...

Any more ideas welcome

---

### Post by SlugSlug on 2012-08-22
or maybe add a ```
&
```  to the end of the cron line

---

### Post by SlugSlug on 2012-08-22
I'd use rsync if you have ssh access to the ftp server?

---

### Post by spjackson on 2012-08-22
> **jimmystubs said:**
> Tried adding the --ftp-pasv to the end but same result. It works when manually run but when cron runs it, it fails after 2mbHow do you know what size the zip file is at 04:50am? Are you sure that it isn't still being written at that time?

---

### Post by jimmystubs on 2012-08-22
Dare I say on this forum that the FTP server is a microsoft server running bulletproof ftp. This was a pre-existing FTP that I wanted to utilize. I have full access to this server though is there is any setting changes I can look, though its all pretty standard stuff that works in other ways fine (including the manual run of the script).

I am tweaking the cron times to check this real time, and I can see once the file transfer has stopped via ftp console, so yep am sure that it is not still writing...

---

### Post by SlugSlug on 2012-08-22
plain old ftp example here

[http://www.stratigery.com/scripting.ftp.html](http://www.stratigery.com/scripting.ftp.html)

---

### Post by dragonfly41 on 2012-08-22
Did you not find this clue in the simple google search I posted earlier ..

[http://curl.haxx.se/mail/archive-2004-09/0065.html](http://curl.haxx.se/mail/archive-2004-09/0065.html)

What version curl are you using?

Are you trying to upload and overwrite existing files?

---

### Post by jimmystubs on 2012-08-22
I looked at it before as I have done now but still cant find much help there. If there is something obvious I have missed perhaps you could post it here for me & others to find?

curl --version:

[B]curl 7.19.7 (x86_64-pc-linux-gnu) libcurl/7.19.7 OpenSSL/0.9.8k zlib/1.2.3.3 libidn/1.15
Protocols: tftp ftp telnet dict ldap ldaps http file https ftps
Features: GSS-Negotiate IDN IPv6 Largefile NTLM SSL libz[/B]

During the normal operation of this script it will be an overwrite, but for this testing I am clearing the incomplete files each time.

Thanks for your responses dragonfly, its appreciated. I am an inexperienced ubuntu user and am hoping to get this simple script working for my backups soon. Each time I have setup cron jobs I have struggled abit! I will re-read the articles and see if I can make sense of it.

"-a/--append
(FTP) When used in a ftp upload, this will tell curl to append to the target file instead of overwriting it. If the file doesn't exist, it will be created.
If this option is used twice, the second one will disable append mode again."

Reading this in the manual made me think overwriting is fine...

---

### Post by jimmystubs on 2012-08-22
OK, I've added **2>/home/user/ftp.log** to the end of the command and have an error:

curl: (18) Uploaded unaligned file size (14958592 out of 31352138 bytes)

I'm currently researching, will post back if I figure out why

---

### Post by dragonfly41 on 2012-08-22
some have suggested clearing cache on ftp server.

---

### Post by jimmystubs on 2012-08-23
OK no solid answers really. I think the issue may of been due to a choppy internet connection at the time, as it is working properly now.

Sorry I dont have anymore than that, and if I figure a more solid answer I will post back. I have not changed anything on the FTP server, and the only change to the script was to add the error output at the end. Still confused as to why the script worked 100% of the time when manually run, but not when run by cron, perhaps just luck but seems hard to believe. Anyway, thanks for help! :-)

---

