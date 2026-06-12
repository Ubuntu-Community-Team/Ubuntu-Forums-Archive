---
title: "WGET Help"
date: 2010-11-10
forum: General Help
---

### Post by MordyT on 2010-11-10
Hello,
I am currently looking for some help with the wget command. I have a linux server with shell access. I also have a windows server with only ftp access. I want to use the following...

```
ftp://username:password@serverip/127.0.0.1 port 1/main/
```Obviously I replace the username/password and server ip. 

So when i FTP into the server, I see the folder 127.0.0.1 port 1 (ok, the ip and port are different, but that doesn't matter). Inside that folder I see main, etc. I wish to download all the files in main. 

So I run the command, and it authenticates correctly and all, but then it errors out...
Here is what I see...

```
Connecting to serverip:21... connected.
Logging in as username... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD not needed.
==> SIZE serverip ... done.
==> PASV ... done.    ==> RETR serverip ...
No such file `serverip'.

--2010-11-10 08:49:12--  http://port/
Resolving port... failed: Name or service not known.
wget: unable to resolve host address `port'
--2010-11-10 08:49:12--  http://1(port number)/main/(specific file)

```What it appears to do is trying to download the folder with the serverip in it. Remember the folder structure is 127.0.0.1 port 1/main and it seems to think the first folder is only 127.0.0.1 without appending the port 1 part....

How would I structure this command properly?

Thanks.

EDIT: I cannot rename any folders...

---

### Post by MordyT on 2010-11-10
Really? This thread got pushed back to page 13 in a mere 16 hours, indicating that this board is very active, yet somehow no one can answer it? This is the second thread I have made that hasn't been answered at all..
While I understand no one is obligated to answer anything, I thought that was what a community was about.

---

### Post by Smart Viking on 2010-11-10
[FONT=monospace]Do you have a directory in your server named [/FONT]"127.0.0.1 port 1"? O.o

```
ftp serverip
get "127.0.0.1 port 1/main/?*"
```

---

### Post by SeijiSensei on 2010-11-10
Try putting the URL in quotes like this:

```

wget 'ftp://username:password@serverip/127.0.0.1 port 1/main/'

```

The bash shell parses a line into fields using the space.  So without the quotes it sees "port" and "1/main/" as separate fields and not as parts of the URL.

Embedded spaces are legal in *nix, but they're a pain to deal with.  I usually use hyphens or underscores when naming directories and files for this reason.

---

### Post by MordyT on 2010-11-10
> **Smart Viking said:**
> [FONT=monospace]Do you have a directory in your server named [/FONT]"127.0.0.1 port 1"? O.o

```
ftp serverip
get "127.0.0.1 port 1/main/?*"
```
Yes I do. It is named exactly like that with the space and all...
> **SeijiSensei said:**
> Try putting the URL in quotes like this:

```

wget 'ftp://username:password@serverip/127.0.0.1 port 1/main/'

```The bash shell parses a line into fields using the space.  So without the quotes it sees "port" and "1/main/" as separate fields and not as parts of the URL.

Embedded spaces are legal in *nix, but they're a pain to deal with.  I usually use hyphens or underscores when naming directories and files for this reason.
Ok, I tried that and it worked! Excellent. 

Last question: I can transfer file by file in that directory, but how would I transfer the whole directory?

EDIT: Would doing a -r before the directory do the trick? Like so:

```

wget -r 'ftp://username:password@serverip/127.0.0.1 port 1/main/'

```

---

