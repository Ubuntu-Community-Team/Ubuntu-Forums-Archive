---
title: "How to download files from remote login using wget"
date: 2011-10-26
forum: General Help
---

### Post by melwyn_jn on 2011-10-26
Hi All,
         I was using sftp to download files from a remote login, but the connection wouldn't last long. So I wanted a tool that could resume download even after the link was disconnected. Hence, I decided to go with wget. But the problem is that I don't have the correct syntax of the command. [B]The requirement is to download from a remote machine with a separate login and password.
[/B]
Does anybody know how to do it with wget or if you know about any other tool, please let me know.

Thanks
Melwyn

---

### Post by duke.tim on 2011-10-26
this is copied from the wget man page, It contains the options for user name a password

```
 wget [OPTION]... [URL]...

```

>  --user=user
       --password=password
           Specify the username user and password password for both FTP and
           HTTP file retrieval.  These parameters can be overridden using the
           --ftp-user and --ftp-password options for FTP connections and the
           --http-user and --http-password options for HTTP connections.

       --ask-password
           Prompt for a password for each connection established. Cannot be
           specified when --password is being used, because they are mutually
           exclusive.
 

--http-user=user
       --http-password=password
           Specify the username user and password password on an HTTP server.
           According to the type of the challenge, Wget will encode them using
           either the "basic" (insecure), the "digest", or the Windows "NTLM"
           authentication scheme.

           Another way to specify username and password is in the URL itself.
           Either method reveals your password to anyone who bothers to run
           "ps".  To prevent the passwords from being seen, store them in
           .wgetrc or .netrc, and make sure to protect those files from other
           users with "chmod".  If the passwords are really important, do not
           leave them lying in those files either---edit the files and delete
           them after Wget has started the download.



FTP Options
       --ftp-user=user
       --ftp-password=password
           Specify the username user and password password on an FTP server.
           Without this, or the corresponding startup option, the password
           defaults to -wget@, normally used for anonymous FTP.

           Another way to specify username and password is in the URL itself.
           Either method reveals your password to anyone who bothers to run
           "ps".  To prevent the passwords from being seen, store them in
           .wgetrc or .netrc, and make sure to protect those files from other
           users with "chmod".  If the passwords are really important, do not
           leave them lying in those files either---edit the files and delete
           them after Wget has started the download.


---

### Post by melwyn_jn on 2011-10-28
Hi [duke.tim]("http://ubuntuforums.org/member.php?u=937794"),
    Thanks for your reply, but I already tried looking at the wget man page, and tried various combinations. Didn't seem to find the solution.

---

### Post by MG&amp;TL on 2011-10-28
Where are you tring to get it from? Surely if you're remotely logging in, wget directly won't get it as it needs a password-so use the ftp commands suggested?
So:

wget  --ftp-user <name> --ftp-password <password> <URL>

Or if that won't work for whatever reason, try curl: sudo apt-get install curl

---

### Post by duke.tim on 2011-11-09
How did this turn out?

---

