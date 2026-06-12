---
title: "bash script for SSH"
date: 2009-10-23
forum: General Help
---

### Post by vttay03 on 2009-10-23
I often SSH into my main desktop PC from my netbook - I want to write a bash script to do this so that I don't have to type in the whole nine yards at the shell each time.  I'm well aware of how to script the command - my question is how do I incorporate the password response into the script?  For instance if I type in the following:

```

ssh -X -l username XXX.XXX.XXX.XXX

```

It will come back asking me for username's password on that particular machine.  I want to include the response for this in the script - I'm not worried about security and have no worries about just putting the password in plain text in the script.  Any suggestions?

---

### Post by JeSTeR7 on 2009-10-23
I think you may want to look into creating a SSH key for doing passwordless ssh logins.  This is what I followed to enable this [http://www.debian-administration.org/articles/152](http://www.debian-administration.org/articles/152)

---

### Post by thegreenblob on 2009-10-23
I recently did something like this with sshfs. I have my netbook auto mount my music folder on my desktop to the netbook using a script.

I had to use a program called "expect".

```
sudo apt-get install expect
```

And here's my expect script (minus my password of course), I'm sure you can modify it to suit your needs.

```
#!/usr/bin/expect -d
set timeout -1
spawn -ignore HUP /usr/bin/sshfs -f joe@192.168.1.100:/home/joe/Music /home/joe/Music
expect "password:"
send "mypassword\r"
expect "\n"
```

Hope this helps.

---

### Post by vttay03 on 2009-10-23
this looks pretty interesting...i haven't heard of expect before but i'm definitely going to look into it.  thanks.

---

### Post by whitethorn on 2009-10-23
Really the best way to do what you want is.

1) create an alias in your .bashrc  ```
nano ~/.bashrc
```

There should already be a couple in there, just copy the format alias whatever.you.want.to.use.as.a.shortcut='ssh XXX.XXX.XXX -l username -X'

2) then use the guide the one guy meant and setup a password less login.  That way when you type the command (alias)  It'll log to your server automatically.

---

### Post by Giblet5 on 2009-10-23
I second the idea of creating the pair of keys.

That is the most secure. It is the easiest to use.

As for the remainder of your commandline options, put those in ~/.ssh/config as described in ```
man 5 ssh_config
```

That way, the remote system is simply an extension of the one you're on.

---

### Post by vttay03 on 2009-10-25
Thanks guys - I ultimately took your advice and created the keys.  Afterwards, I made aliases as suggested in my .bashrc file to automate the process a bit more.  Thanks for the help...

---

