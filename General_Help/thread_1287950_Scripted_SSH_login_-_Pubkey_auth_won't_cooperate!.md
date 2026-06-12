---
title: "Scripted SSH login - Pubkey auth won't cooperate!"
date: 2009-10-10
forum: General Help
---

### Post by jooshbro on 2009-10-10
Hey all,
I'm trying to set up a little system where I can send an email to restart a few different systems that I don't always have SSH access to.  I've read as much as I can find on scripted SSH logins, and have already set up the public/private key pair on my client computer and target server.  I know it's working because whenever I log in manually, I'm not prompted for a password.  But when I try to log in through running a script such as this one:

```
ssh root@myhost.com uname
```

It prompts me for my password.  I've tried using a custom SSH config file (to manually turn off password auth and turn on key auth) with no luck, and I've also unsuccessfully tried ssh-agent (though I'm not sure if I set it up completely correctly, or if it's even what I need).  Thanks for any help you can offer! :)

-Josh

---

### Post by delcypher on 2009-10-10
Firstly run ssh in verbose mode to see what's happening.

```
ssh -v root@myhost.com uname
```

If your private keys aren't in ```
.ssh/identity
 .ssh/id_rsa
 .ssh/id_dsa

```
in your home directory then ssh won't find them.

If you know where your private key is you can load it by running


```
ssh -v -i /path/to/private.key root@myhost.com uname
```

If you want to get ssh-agent working then run the following:
```
eval `ssh-agent -s`
ssh-add
```

This will load ssh-agent so it is available to the current shell (and all sub shells), ssh-add will load the default keys in the .ssh directory. If your private key is somewhere else then run (after you've run eval `ssh-agent -s` )
```
ssh-add /path/to/private.key
```

Everytime a new private key is loaded ssh-add will ask you for the passphrase, you only need to enter it once. After that ssh-agent will take care of the rest.

Now you can run ssh,scp, rsync (with ssh shell) and not need to enter any passwords :)

For more on ssh-agent look at [http://www.securityfocus.com/infocus/1812]("http://www.securityfocus.com/infocus/1812")

Have fun!

---

### Post by jooshbro on 2009-10-11
Wow thank you, I'll give that a shot :P

---

### Post by Lars Noodén on 2009-10-11
When you have that working, you may wish to take it a step further and make a special non-root account with specific keys for that specific activity. Then you can either use ForceCommand in the sshd_config or put a specific line in sudoers allowing that program and only that program to be run and only with specific parameters.  In that way you can avoid root login at all.

---

