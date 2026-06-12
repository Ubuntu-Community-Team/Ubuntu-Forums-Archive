---
title: "Anyone know how to specify username using ftp?"
date: 2011-03-12
forum: General Help
---

### Post by LumbeeNDN on 2011-03-12
Hey guys. I'm using old skool ftp from the terminal. I need to connect with a different user than my local linux user (which ftp defaults to). Can anyone tell me how to specify that from the prompt? Man page says...
```
 user user-name [password] [account]
                 Identify yourself to the remote FTP server.  If the password is not specified and the server requires it, ftp
                 will prompt the user for it (after disabling local echo).  If an account field is not specified, and the FTP
                 server requires it, the user will be prompted for it.  If an account field is specified, an account command
                 will be relayed to the remote server after the login sequence is completed if the remote server did not
                 require it for logging in.  Unless ftp is invoked with “auto-login” disabled, this process is done automati&#8208;
                 cally on initial connection to the FTP server.

```
...tryed all combos at the propt, but not getting any where...

---

### Post by tredegar on 2011-03-12
```
user user-name [password] [account]
                 Identify yourself to the remote FTP server.  If the password is not specified and the server requires it, ftp
                 will prompt the user for it (after disabling local echo).  If an account field is not specified, and the FTP
                 server requires it, the user will be prompted for it.  If an account field is specified, an account command
                 will be relayed to the remote server after the login sequence is completed if the remote server did not require
                 it for logging in.  [COLOR="Red"]Unless ftp is invoked with “auto-login” disabled, this process is done automatically on
                 initial connection to the FTP server.[/COLOR]

```
```
-n    Restrains ftp from attempting “auto-login” upon initial connection.  If auto-login is enabled, ftp will check the
           .netrc (see netrc(5)) file in the user's home directory for an entry describing an account on the remote machine.  If
           no entry exists, ftp will prompt for the remote machine login name (default is the user identity on the local
           machine), and, if necessary, prompt for a password and an account with which to login.

```
So, make sure **.netrc** does not exist, and maybe try **ftp -n host**

[ I don't use **ftp**, because I set up key-based authentication for **ssh** and now use **sftp://username@host** in **nautilus** which works very well.]

---

### Post by LumbeeNDN on 2011-03-12
:rolleyes: Well geez-um...it it was a snake it would have bit me! That did it..thanx!

---

