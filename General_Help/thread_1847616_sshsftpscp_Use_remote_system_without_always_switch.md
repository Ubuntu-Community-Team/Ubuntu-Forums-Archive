---
title: "ssh/sftp/scp: Use remote system without always switching tools/connections?"
date: 2011-09-21
forum: General Help
---

### Post by Abscissa on 2011-09-21
First of all: I know my way around the command line, at least enough to get by, but I'm far from being any sort of unix expert. I'm a programmer (mostly C-derived languages), and I can do basic shell scripts, but I'm no script-fu wiz.

I have basic familiarity with using ssh (for a secure remote shell), sftp and scp. But I've noticed I typically need to switch between them a lot for various tasks (which also means lots of opening/closing ssh connections to the same remote machine). From what I can tell, this seems to be due to limitations in each of them.

Maybe I'm wrong, but as I understand things:

ssh shell:
	Can do: Pretty much anything you can do at a normal shell.
	Can do: Multiple commands in one session/connection.
	Cannot do: File transfers. 
	Cannot do: "batch" mode (like sftp) that'll bail out at the first error.

sftp:
	Can do: Multiple commands in one session/connection.
	Can do: Transfer files.
	Can do: Delete files and empty dirs.
	Can do: Explore/query the remote filesystem.
	Can do: Batch mode (-b) that'll bail out at the first error.
	Cannot do: Transfer/delete entire non-empty directory trees.

scp:
	Can do: Transfer entire non-empty directory trees.
	Cannot do: Multiple commands in one session/connection.
	Cannot do: Delete things.
	Cannot do: Move/rename things.

So, for example, suppose I want to do all the following, and automate it in a script:

	1. Upload a bunch of misc standalone files to various places (ie, wildcards won't help).
	2. Delete the tree 'foo'.
	3. Upload a new 'foo' tree.
	4. Do some logic, both remote and local.
	5. Some other step that completely depends on the results of #4

As far as I'm aware:
#1 needs to use sftp (could use scp, but that would be wasteful - a new connection for every file?).
#2 needs to be ssh (could use sftp in theory, but that's be a royal PITA).
#3 needs to be scp (again, sftp would be theoretically possible, but a royal pain).
#4 can only be ssh.
#5 could end up needing to be anything. 

So, AFAIK, I can't just simply pass a block of script in batch mode to ssh or sftp. That simple set of tasks involves switching between all those separate programs, and with each making a separate new connection.

Now, I can certainly do all that. But it seems to me I must be missing something.

Is there some better way to do all of this? To do it all in one connection? Or not have to keep switching between the different tools?

---

### Post by scarleo on 2011-09-21
You could perhaps try rsync for file transfer, I use it to transfer files since it's generally faster than scp and it uses either SSH connection or its own rsync daemon. But it's still a new session, not sure why that matters to you. Although only one.

Not sure what you mean by switching tools, as far as I see it it's just different programs to do different stuff, as always. Are you using them in different terminals? If you have possibility to setup ssh server also on client you can run everything through ssh on your server. That would let you not switch terminals and still get same functionality. But you seem to be scripting these commands so again, why does number of connections even matter? Speed?

Maybe I just misunderstood your whole problem, if so I'm sorry.

---

### Post by Lars Noodén on 2011-09-21
> **Abscissa said:**
> 
#1 needs to use sftp (could use scp, but that would be wasteful - a new connection for every file?).

As mentioned you can use rsync for the transfer.  If you do not want to make a new connection each time, you can [multiplex SSH](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Multiplexing) and re-use your connection.

---

### Post by Abscissa on 2011-09-27
> **scarleo said:**
> But it's still a new session, not sure why that matters to you.
...
why does number of connections even matter?

It doesn't really matter all that much, it just seemed oddly clunky and needlessly inefficient.

Well, there is one way in which it matters: I prefer to use a password-protected certificate, so I'd have to re-type the password for every connection that gets made, which obviously works against the whole "automated" thing ;)

Of course, since I posted the OP, I've learned about the "expect" tools, and that could probably be used to automate entering the password. But of course that would defeat the point of using a password-protected certificate.

> **Lars Noodén said:**
> As mentioned you can use rsync for the transfer.  If you do not want to make a new connection each time, you can [multiplex SSH](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Multiplexing) and re-use your connection.

Thanks. That sounds like it could be just what I had in mind.

Although, I've just discovered sshfs ( [http://www.linuxjournal.com/article/8904](http://www.linuxjournal.com/article/8904) ) and it's *freaking awesome* and perfect for my needs. So I think I'm going to go with that.

---

### Post by Lars Noodén on 2011-09-28
[SSHFS](https://help.ubuntu.com/community/SSHFS) is specialized use of SFTP. It does rock and should be mentioned more often than it has been.

---

