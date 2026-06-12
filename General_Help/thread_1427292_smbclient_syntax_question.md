---
title: "smbclient syntax question"
date: 2010-03-11
forum: General Help
---

### Post by jonnymccullagh on 2010-03-11
I am having problems with smbclient on the command line. When I enter the following in Nautilus or Konqueror it works fine:
```
smb://myADusername@server1.ads.domain.tld/testhome/myADusername
```
but similar on the command line gives me an error:
```
smbclient \\\\server1.ads.domain.tld\\testhome\\myADusername -U 'myADusername%myADpassword'
```
Domain=[ADS] OS=[Windows Server 2003 R2 3790 Service Pack 2] Server=[Windows Server 2003 R2 5.2]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME
So my question is does anyone know if it is possible to log or see the smbclient command issued by nautilus or konqueror so I can use these as a basis for my own command line stuff? 
Thanks in advance,
jonny

---

### Post by 209pcs on 2010-03-11
Although I do not know the answer to the question presented, one possibility may be due to the fact that the directory 'myADusername' is included in the share path.  I just now tested my ability to log in to our server, and it worked fine as long as I did not include a directory in the share path:

```
smbclient \\\\server.domain.tld\\share -U 'domain\myADusername'
```This will prompt you for a password (I was not able to successfully include a password in the command).



Including a directory in the share path
```
smbclient \\\\server.domain.tld\\share\directory -U 'domain\myADusername'
```returns the following message:
```
Enter XXXX\user's password: 
Domain=[XXXX] OS=[Windows X.X] Server=[Windows X LAN Manager]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME

```

---

### Post by jonnymccullagh on 2010-03-12
Thanks for your reply 209pcs, you've helped me work out that what I should have been doing is:
```
smbclient \\\\server1.ads.domain.tld\\testhome -U 'myADusername%myADpassword' -c 'cd myADusername; ls'
```
So this helps me understand how the command line smbclient works I'm on to my next problem of getting the web interface (phpsmbwebclient) to work the same. Thanks.

---

### Post by jonnymccullagh on 2010-03-12
Incidentally the -D parameter can also be used to set the initial directory:
smbclient \\\\server1.ads.domain.tld\\testhome -U 'myADusername%myADpassword' -D 'myADusername' -c 'ls'
Just in case this helps anyone else,
jonny

---

### Post by 209pcs on 2010-03-12
jonnymccullagh,

I tried the example you posted, and when I attempt to include my password, the cursor simply goes down to the next line and displays a ">".  Does the percent sign (%) separate the username and password?


I'm using Ubuntu 9.10 64-bit, smbclient version 3.4.0

---

### Post by jonnymccullagh on 2010-03-12
Yes the % symbol is to separate the username and password (if you do not want to be prompted for a password. 
From the man page:
```
-U|--user=username[%password]
Sets the SMB username or username and password.
If %password is not specified, the user will be prompted.
```
Are you sure you have quoted everything correctly. Usually when I get a > prompt it is because I have an extra apostrophe symbol?
jonny

---

### Post by 209pcs on 2010-03-15
There it is.  I have an apostrophe in my password.

---

