---
title: "Wget and FTP Automation"
date: 2009-11-19
forum: General Help
---

### Post by thexder31 on 2009-11-19
Just using wget for the first time... doing this:

wget http://ftp.<sitename>:21 --ftp-user=<username>  --ftp-password=<password>

I've tested the site/username/password, and confident I have those right.  

I'm working through a proxy, which is set with the env variable http_proxy (not sure if that even has an impact), but seem to have gotten through all that... a file (index.html) gets downloaded with the contents:

[INDENT]220-Welcome to the Yahoo! Web Hosting FTP server.
220-Need help? Get all details at:
220-http://help.yahoo.com/help/us/webhosting/gftp/
220-
220-No anonymous logins accepted.
220 Yahoo!
530 Please login with USER and PASS.
530 Please login with USER and PASS.
530 Please login with USER and PASS.
530 Please login with USER and PASS.
530 Please login with USER and PASS.
530 Please login with USER and PASS.
530 Please login with USER and PASS.
530 Please login with USER and PASS.
[/INDENT]

This implies to me I've gotten through the firewall, and am talking to yahoo... but just that the username and password are somehow not being conveyed.  

Tried a lot of stuff --user and --password. The above is the best I've gotten.

Any thoughts? The other threads on this topic got me this far... but no further.

---

### Post by Morphine Drip on 2009-11-19
hi man.  i'm not sure on wget...but what i normally use is curl. the syntax i use is:  curl --silent -O [ftp://username](ftp://username)  : password@10.10.10.10/file

  i put spaces around the : because it kept sticking smiley faces in there. got tired of guessing how to escape it to turn it off

---

### Post by thexder31 on 2009-11-20
Thanks Morphine... I'll try that.  (btw, I tried wget outside the firewall, and it works pretty well.  It definitely works as advertised... wondering if there are some special restrictions at the company... ).  

If anyone wants to comment on wget and proxies, and the dumb error I'm getting, we can continue the thread on that path.

Thx!

---

### Post by thexder31 on 2009-11-20
Curl is definitely the way to go with this.

It works great from within the firewall, as it allows the sending of commands before the transfer happens (-Q "<command>") and after the transfer( -Q "-<command>").

curl --verbose -u $username:$password -Q "user <username>@<server>" -Q "pass <password>" -Q "-RMD $directory" ftp://<proxyftpserver>21/

It seems strange to you guys, perhaps.  My company has a bizzaro ftp proxy server you have to login to, from which you can then send commands out to an external ftp server, and do transfers. 

It works well enough, now that I understand feeding of commands back and forth.

If you've read this far in the thread, curl was an excellent suggestion, and the solution for me.

Thanks.

---

