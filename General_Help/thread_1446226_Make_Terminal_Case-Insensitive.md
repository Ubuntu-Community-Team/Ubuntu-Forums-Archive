---
title: "Make Terminal Case-Insensitive"
date: 2010-04-03
forum: General Help
---

### Post by dadgetboy on 2010-04-03
Yo guys!

Is there anyway that I could make Terminal Case-Insensitive. For example,
ApT-geT should equal apt-get, and CD should be the same as cd. I have looked at other threads, and other advice and they pointed me towards making a file named .inputrc in my Home folder with the following text:

```
set completion-ignore-case on
```Needless to say, this tip didn't work; is there anything else I could do/am I doing something wrong?

---

### Post by dcstar on 2010-04-03
> **dadgetboy said:**
> Yo guys!

Is there anyway that I could make Terminal Case-Insensitive. For example,
ApT-geT should equal apt-get, and CD should be the same as cd. I have looked at other threads, and other advice and they pointed me towards making a file named .inputrc in my Home folder with the following text:

```
set completion-ignore-case on
```Needless to say, this tip didn't work; is there anything else I could do/am I doing something wrong?

Linux is a case sensitive OS, it is not DOS.

---

### Post by capscrew on 2010-04-03
> **dadgetboy said:**
> Yo guys!

Is there anyway that I could make Terminal Case-Insensitive. For example,
ApT-geT should equal apt-get, and CD should be the same as cd. I have looked at other threads, and other advice and they pointed me towards making a file named .inputrc in my Home folder with the following text:

```
set completion-ignore-case on
```Needless to say, this tip didn't work; is there anything else I could do/am I doing something wrong?

The file .inputrc is for keyboard input not terminal recognition.  See [**_here _**]("http://robertmarkbramprogrammer.blogspot.com/2008/08/inputrc-for-bash-history-completion.html")for more information.

As ** dcstar **has said, Linux is case sensitive. You are better off learning to use it that way.

---

### Post by srs5694 on 2010-04-03
If you just mistype a few commands in the same way every time, you could set up aliases in your ~/.bashrc file, as in:

```

alias ApT-geT='apt-get'

```

This would be very awkward to do to cover every possible variant, though. A 6-letter command like apt-get has 64 possible case combinations, so you'd need 63 entries to cover all the variants. That's just one command, too.

One other point to consider is that some commands take options that are themselves case-sensitive. The -s and -S options to dpkg, for instance, are entirely different. The only way I can think of to get around that would be to write a script that serves as a front-end to the command. The script would have to juggle options, so that (for instance) dpkg's -s and -S are mapped to two different letters, or one of these short forms would be dropped entirely. To do this for more than one or two commands, this would be a massive undertaking, and the result would be a very non-standard system.

Overall, I concur with the others; learn to live with case sensitivity, except maybe just to set up a few aliases to cover typos that you frequently make. Even that might not be entirely advisable, though, since then you might forget which is the real command and have problems if you need to use another system, or cause problems for others if you should offer advice based on your alias rather than the real command.

---

### Post by Primefalcon on 2010-04-03
Short answer no... Linux is a case sensitive OS

demonstration in point...

Microsoft are using a windows server.... let's jumble the caps a little...

[http://www.microsoft.com/en/us/dEfAUlt.aspx](http://www.microsoft.com/en/us/dEfAUlt.aspx)

as you can see even though we've recapped a few of the littlers in default.aspx

it still finds the file, that's because to windows fIlE.txt is no different from file.txt or FILE.TXT.... Windows simply can't tell the difference...

Let's try Ubuntu.com which is hosted on a Linux server

[http://www.ubuntu.com/products/whatisubuntu/910features/iNdEx.php](http://www.ubuntu.com/products/whatisubuntu/910features/iNdEx.php)

as you see... it can't find the file because iNdEx.php is not index.php, Linux can tell the difference.....

In this case you could use url rewriting so that it redirects you to index.php.... but it comes down to Linux is a case sensitive operating system, while Windows isn't...

and while you could use regex to match you, it's a lot easier in the long run just to accept that Linux is not Windows

---

### Post by dadgetboy on 2010-04-04
Alright thanks guys! I guess I'll just have to accept it (which is no big problem anyhow). Also, thanks for the alias tip in .bashrc :)

I guess this is case closed :D

---

### Post by stoian on 2011-01-01
> **dadgetboy said:**
> Yo guys!

Is there anyway that I could make Terminal Case-Insensitive. For example,
ApT-geT should equal apt-get, and CD should be the same as cd. I have looked at other threads, and other advice and they pointed me towards making a file named .inputrc in my Home folder with the following text:

```
set completion-ignore-case on
```Needless to say, this tip didn't work; is there anything else I could do/am I doing something wrong?

The tip above, or, as described in this post:
```
http://www.cyberciti.biz/faq/bash-shell-setup-filename-tab-completion-case-insensitive/
```
is only for tab completion to be case insensitive in the terminal.

---

