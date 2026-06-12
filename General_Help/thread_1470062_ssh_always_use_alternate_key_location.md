---
title: "ssh always use alternate key location?"
date: 2010-05-02
forum: General Help
---

### Post by pwebguy on 2010-05-02
Hello, all. 

I know I can add  the -i to an ssh command to choose an alternate ssh key:

ssh  -i /path/to/private/key user@remote

Is there a way to permanently set the alternate key file location so I can just:

ssh  user@remote

Issue is that this is a dual boot Win and Ubuntu, and I store all my data (keys also) on a separate partition.

Thanks!

---

### Post by krismatth3 on 2010-05-02
Add the following to your /home/name/.bashrc

```

alias ssh='ssh -i /path/to/private/key' 

```Close and reopen the terminal. The command 'ssh' will now behave like you always typed that extra info.

Or, you could consider symlinking your ssh private key to the real thing

```

cd ~/.ssh
ln -s /path/to/private/key name_of_private_key

```

---

### Post by pwebguy on 2010-05-09
Perfect, thank you very much! Should have known it would be something simple and elegant.

Cheers!

---

