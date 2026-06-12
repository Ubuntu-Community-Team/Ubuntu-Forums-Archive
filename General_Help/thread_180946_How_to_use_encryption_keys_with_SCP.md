---
title: "How to use encryption keys with SCP"
date: 2006-05-23
forum: General Help
---

### Post by Mortuis on 2006-05-23
I want to write a script that I can put in the crontab which will scp a file to my uncles server a couple times a day.  My problem is that in order to get into my uncles computer, I need to use the private key he issued my user account.  From a windows computer I am able to successfully use WinSCP to connect to his computer and upload/download files manually, and on linux I am able to successfully use the scp command to move files between computers on my lan (which are only password protected) but I can't figure out how to get the command line scp application on linux to use the key my uncle gave me to get into his machine.  I've been searching google for a couple days now and can find pleanty of documentation on scp, but nothing on how to tell it what key file to use.

Any help would be appreciated.

---

### Post by souki on 2006-05-23
scp -i yourkey.pub ...

---

### Post by Slim Odds on 2006-05-23
[QUOTE=souki]scp -i yourkey.pub ...[/QUOTE]

Or, put copy the contents of yourkey.pub into the authorized_keys file on his machine.

Then you get automatic authorization.

---

### Post by Mortuis on 2006-05-24
[QUOTE=souki]scp -i yourkey.pub ...[/QUOTE]
How did I miss that? I swear I looked at the man pages but there it is. :oops:

Thanks!

---

### Post by Mortuis on 2006-05-24
[QUOTE=Slim Odds]Or, put copy the contents of yourkey.pub into the authorized_keys file on his machine.

Then you get automatic authorization.[/QUOTE]

That'd be a lot easier, however I don't have that file in my system, or at least I get:
john@gabriel:~$ locate authorized_keys
john@gabriel:~$

Would it work to just copy mykey.pub into ~/.ssh and rename it to authorized_keys or is there other information that needs to be in the file?  I'll have to try that later.

---

### Post by Slim Odds on 2006-05-24
[QUOTE=Mortuis]That'd be a lot easier, however I don't have that file in my system, or at least I get:
john@gabriel:~$ locate authorized_keys
john@gabriel:~$

Would it work to just copy mykey.pub into ~/.ssh and rename it to authorized_keys or is there other information that needs to be in the file?  I'll have to try that later.[/QUOTE]

You add the *contents* of **your** public key (id.pub or something like that) to **his** authorized_keys files

I do this when I allow internet access to one of my machines, then I _disable name/password_ based access. This is a **very** secure way to use ssh.

---

### Post by souki on 2006-05-24
[quote=Mortuis]Would it work to just copy mykey.pub into ~/.ssh and rename it to authorized_keys or is there other information that needs to be in the file?  I'll have to try that later.[/quote] 
yes that will be fine,
or you can do this from the client machine (replace id_rsa with your key):
```
cat ~/.ssh/id_rsa.pub | ssh root@the-ssh-server 'cat - >> ~/.ssh/authorized_keys'

``` an other tip, if you're as lazy as me, you can define an alias so you don't have to specify wich key you want to use each time you scp or ssh :

on your client, put this in ~/.ssh/config
```
Host the-alias
        IdentityFile ~/.ssh/id_rsa
        HostName your-host-here
        Port 22
        User root
        Compression no
        Cipher blowfish
        Protocol 2

``` then, you can ssh  without specifying the identity file nor the user id:
```
ssh the-alias
``` 
you can add more alias if you want, and there is a lot of options you can use
for example, you can define tunneling

---

