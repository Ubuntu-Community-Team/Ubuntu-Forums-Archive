---
title: "uploaded files to /var/www  cannot be viewed by a browser"
date: 2009-06-29
forum: General Help
---

### Post by ceilingcat on 2009-06-29
I am trying to upload some html files to /var/www in ubuntu server 9.04 but I get "permission denied" when I try to view them.

why are the permissions set so low?

---

### Post by mcduck on 2009-06-29
Strict permissions are pretty much the basis of security in Unix/Linux systems. They are the reason why we don't have the kind of virus problem Windows has, and why majority of web servers and supercomputers run Linux or some Unix variant.

Normal user's simply have no business outside their home directory, all system-level stuff belongs to administrators.

You should probably read this: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

..and to solve your actual problem, run "gksudo nautilus" to open the file manager as root, or use command line to move files to /var/www.

In case it's a development/testing server and not in actual production use, I'd recommend creating a web site with it's root located inside your home directory. This would allow you to use the server for development purposes without having to worry about the permissions.

---

### Post by ceilingcat on 2009-06-29
I forgot to mention I am using ubuntu server. However the problem remains.

I want to be on a beach in Tahiti with my laptop, upload a new file to my server in Vladivostok, and be able to view the file in a browser without flying 6,500 miles home to transfer files from my home directory to /var/www and then nip back to the beach.

---

### Post by t0p on 2009-06-29
> **ceilingcat said:**
> I forgot to mention I am using ubuntu server. However the problem remains.

I want to be on a beach in Tahiti with my laptop, upload a new file to my server in Vladivostok, and be able to view the file in a browser without flying 6,500 miles home to transfer files from my home directory to /var/www and then nip back to the beach.

Did you do what mcduck suggested?

If you don't have a gui on the box, prefix **sudo** to your command, like this:

```
sudo cp file.html /var/www/file.html
```

---

### Post by ceilingcat on 2009-06-29
How can I be clearer about my problem, [t0p]("http://ubuntuforums.org/member.php?u=380385")?

I shall restate it.

I am nowhere near my linux box. 

It is in Vladivostok.

I am in Tahiti.

I am using ftp to upload files.

How can the uploaded files be given appropriate permissions when
they are 'put' into /var/www, automatically?

If you know of a way to sudo using ftp please share that knowledge, 
even if you have to kill me afterwards.  I am dying to know.

---

### Post by 3rdalbum on 2009-06-29
How are you sending them, and how are you trying to access them?

If you're sending them through an FTP program and then trying to view them through some web server software, then you will encounter problems as the web server will typically run with the lowest possible permissions. By design.

It's been a while since I've used an FTP client, but I think it's possible to change permissions on files that you upload so they can be readable by anyone.

---

### Post by ceilingcat on 2009-06-29
[3rdalbum]("http://ubuntuforums.org/member.php?u=61044"), thanks for your input.  You are right about the permissions thing, and indeed,
that is what prompted me to start this thread looking for help.

How do I do what you suggest? Google hasn't helped me. There are many suggestions about changing vsftpd.conf, and I reckon I have tried them all.  I have even gone so far as to check that there is only one vsftpd.conf file on my linux box in case I am editing the wrong one.

vstpd.conf has an option for chown_uploads and chown_username, but I have had no success with altering those. It would seem like a scattergun approach anyways.

I am sure the solution is simple!

---

### Post by decoherence on 2009-06-29
Hi Ceilingcat! I just want to confirm a couple of things...

You are able to upload these files to your server's /var/www? As in, you don't get a permissions error then? 

Assuming you can do this successfully, what specific error does the browser give you when you try to access the file? A 403/forbidden error?

What FTP client and server are you using?

Assuming you can upload the files, you should be able to make them readable to the web server afterwards. How you do this depends on what FTP client you're using. I believe the command line client uses the standard chmod/chown/chgrp commands. Something like "chgrp www-data *yourfile*" then "chmod g+r *yourfile*" might do it, but it has been a long time since I used FTP so I could be way off.

Also... when you get back to Vladivostok you might consider ditching FTP for SSH, which can provide the same uploading functionality in a more secure way. FTP should be phased out where possible as it does not encrypt transmission.

---

### Post by ceilingcat on 2009-06-29
Yes, I can upload to /var/www without getting a permissions error.

Yes, I get a 403 forbidden error.

The server is vsftpd.

Here is where you will laugh at me.  My ftp client is the command line XP client. It is 
good enough for transferring files but that is about all.

Filezilla client connects to my server, but it disconnects because of a timeout whilst trying to list the home directory. The filezilla client installation wizard tells me my firewall is all ****** up, so I tried Core FTP as a client, and it worked straight away and didn't care at all about the firewall, so I guess Filezilla is screwed.

So, using Core FTP i can chmod the files once they are uploaded :)

But I would still like to have it 'automatic' .. that my ftp logon details would be enough for  the server to 'intelligently' recognize that anything I put into /var/www should not be restricted.

---

### Post by sirhalos on 2009-06-29
Try chmod 755 to the files inside the folder

---

### Post by ceilingcat on 2009-06-29
Solved!
I knew the answer would be simple.

I took your advice, [decoherence]("http://ubuntuforums.org/member.php?u=156618"), and installed an SSH client, for security reasons, and lo,
I discovered that files uploaded using a secure connection are assigned the correct permissions.

---

