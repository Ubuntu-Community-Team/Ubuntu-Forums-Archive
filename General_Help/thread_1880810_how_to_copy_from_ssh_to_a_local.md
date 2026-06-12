---
title: "how to copy from ssh to a local?"
date: 2011-11-14
forum: General Help
---

### Post by liquidmonkey on 2011-11-14
so i looked up how to copy a file to my local computer (when ssh'ing into another server) BUT its not working.

a little help please :)

i'm at the top of where i ssh'd into and i try

scp [email]username@IPaddress:/filename.pdf[/email] /usr/Downloads

where the first part is the ssh file (just a pdf) and the usr part is my local machine.

it asks me for a password THREE times, then says 'permission denied (publickey, password'

tried that 4 times and no love :(
and if i'm doing it right, shouldn't the pdf name fill itself in after the first few letters and a i pres tab? or is that just a local computer thing?


thanks!

---

### Post by carranty on 2011-11-14
Autocompletion won't work, because you haven't logged into the remote machine until after you've hit the return key.  It would only be able to remote complete if you were logged in already.

Are you sure the password is correct.  It's 'username's password, not yours on your local machine its asking for.

I use yafc, rather than scd, so I'm not sure whether you're command is valid or not.  I'll try it on mine now and get back to you

---

### Post by liquidmonkey on 2011-11-14
well, i actually login in to the remote machine using ssh first, then i try the copy commands.

maybe that is the problem? or? maybe should have mentioned that :(

---

### Post by carranty on 2011-11-14
Ah right.  If you're already logged into the remote machine that command doesn't make any sense.  Its telling the machine to log into itself and then copy a file called filename.pdf from its root directory to its /usr/Downloads directory.

If you start from your local machine and type

scp [EMAIL="username@IPaddress:/filename.pdf"]username@IPaddress:/filename.pdf[/EMAIL] /usr/Downloads

that should work fine, it did with mine. Keep in mind that the username and IP address is that for your REMOTE machine.  Also if filename is in the home directory you should use

scp [EMAIL="username@IPaddress:/filename.pdf"]username@IPaddress:/home/username/filename.pdf[/EMAIL] /usr/Downloads

instead.

scp uses a ssh connection by default, so no there's no need to create an ssh connection first.

---

### Post by carranty on 2011-11-14
If you aren't sure exactly what the filename is, or where it is - as I usually don't, then yafc is a good alternative.  You log in using

*yafc ssh://username@IPaddress*

Then to download a file simply write[I]

get /path/to/remote/file/filename

[/I]and to upload a file use

*put /path/to/local/file/filename*

---

### Post by liquidmonkey on 2011-11-14
ok, that made it much easier.
after a few tries, got it to work.

i'm still not super clear on all the paths but eventual it worked!

thanks!

and just out of curiosity, how could i do it IF i was already logged in with ssh?

---

### Post by carranty on 2011-11-14
> **liquidmonkey said:**
> 
and just out of curiosity, how could i do it IF i was already logged in with ssh?


You can't, assuming you've used a command similar to 

*ssh username@IPaddress*

ssh is a remote login program, not a file transfer program. I suppose, once logged into the remote computer with ssh, you could use a file transfer program such as scp to log back into your local machine, but it'd be a very wierd way of doing things.

---

### Post by liquidmonkey on 2011-11-14
> **carranty said:**
> If you aren't sure exactly what the filename is, or where it is - as I usually don't, then yafc is a good alternative.  You log in using

*yafc ssh://username@IPaddress*

Then to download a file simply write[I]

get /path/to/remote/file/filename

[/I]and to upload a file use

*put /path/to/local/file/filename*


this is a great tip, thanks!

---

### Post by carranty on 2011-11-14
> **liquidmonkey said:**
> this is a great tip, thanks!

Glad to be of help.  You can also navigate in yafc.  Once logged into the remote computer use the *cd *command to navigate your remote machine and *lcd  *to navigate your local one.  In fact any command you can use on the remote machine, you can use on your local one by simply putting a *l *(for local) in front of it.  Any files copied with the *get* command will be placed in your current directory on your local machine. Also, yafc supports autocompletion (by pressing TAB) and so I find it far easier than other file transfer programs.

---

