---
title: "Running LAMP development server as root"
date: 2010-10-08
forum: General Help
---

### Post by cothedo on 2010-10-08
Hello,

I develop websites using the Contao CMS (f.k.a. Typolight). I used to use a WAMP server on XP, which gave root privileges (I think) to Apache, which was needed for Contao (for development only - when I put it online, I used the so-called FTP-hack, which gave the necessary privileges to Contao).
Now, I'd like to develop my websites on Ubuntu and need to run Apache in root (again, development only). Is that wise? If it doesn't give any security issues, how do I do that? I tried to Google the problem, but couldn't find the answer.

Emiel

---

### Post by kidders on 2010-10-09
Hi there,

Running apache as a user with any privileges at all (let alone root privileges!) is not a good idea. Although apache usually *starts* as root, allowing it to retain those privileges while it's running is extremely unsafe, even on machines that are not connected to the internet. I'm not familiar with Contao, but the idea of a CMS developer even suggesting doing so is inconceivable.

Imo, the most permissive environment you should even *consider* is to run apache as a user created solely for that purpose, with no write access to anything outside /var/www. Within /var/www, write access should be limited to the minimum possible number of locations necessary for your CMS to function (eg to allow end users to upload files), and should not include executable code (eg a PHP script). Bending those rules invariably creates security issues, which you should address carefully (eg by limiting the IP addresses apache will serve certain things to, using client certification, etc).

Anyhow, to answer your question, running apache as root involves enabling a configuration option called "DBIG_SECURITY_HOLE" and rebuilding the server.

I hope that helps.

---

### Post by cothedo on 2010-10-11
> **kidders said:**
> Hi there,

Running apache as a user with any privileges at all (let alone root privileges!) is not a good idea. Although apache usually *starts* as root, allowing it to retain those privileges while it's running is extremely unsafe, even on machines that are not connected to the internet. I'm not familiar with Contao, but the idea of a CMS developer even suggesting doing so is inconceivable.

Imo, the most permissive environment you should even *consider* is to run apache as a user created solely for that purpose, with no write access to anything outside /var/www. Within /var/www, write access should be limited to the minimum possible number of locations necessary for your CMS to function (eg to allow end users to upload files), and should not include executable code (eg a PHP script). Bending those rules invariably creates security issues, which you should address carefully (eg by limiting the IP addresses apache will serve certain things to, using client certification, etc).

Anyhow, to answer your question, running apache as root involves enabling a configuration option called "DBIG_SECURITY_HOLE" and rebuilding the server.

I hope that helps.

If there is another solution than running Apache as root, I want to try that first, I think.
With the Contao CMS, there is a little system check tool. It's a PHP script and one of the things it'll do is create a file and a folder on the server. In my case, it is able to create these, but the file and folder are owned by me, or rather, my computername. The check tool suggests the file/folder should be owned by root.
So maybe that's where the confusion arises. I assumed that I must run Apache under root in order to have this file/folder created with root privileges, but maybe there is another way.
When it is not possible to create the file/folder with the proper privileges, one can use the so-called "FTP hack". I use that one the live server. One enters the FTP credentials and that allows Contao to create files/folders with the proper privileges.

So from the above information, do you have any suggestions for a solution?

---

### Post by kidders on 2010-10-11
> **cothedo said:**
> The check tool suggests the file/folder should be owned by root.Why not just chown them?

What's the logic behind the suggestion Contao makes? For example, is it testing whether it can change the ownership of files? Does the file it creates contain configuration settings?

> **cothedo said:**
> When it is not possible to create the file/folder with the proper privileges, one can use the so-called "FTP hack".That type of thing is reasonably common. The idea is to allow a CMS to create files, and give up ownership of them. That said, FTP servers are subject to the same security constraints as any other server ... Allowing root to log in to one would be highly dangerous.

It's hard to offer a good solution without knowing what the file & directory you mentioned are for. Running apache as root is *definitely* not the answer though.

---

### Post by cothedo on 2010-11-08
> Why not just chown them?

Yes, thanks. That did the trick, as explained on this page:
[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")
I didn't actually need to run Apache under root.

---

